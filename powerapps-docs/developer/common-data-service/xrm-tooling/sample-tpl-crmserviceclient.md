---
title: 'サンプル: CrmServiceClient (Common Data Service) を使用したタスク並列ライブラリ | Microsoft Docs'
description: タスク並列ライブラリ (TPL) は、アプリケーションに並列処理と同時実行を追加するプロセスを簡略化することで、開発者の生産性を高めます。 このサンプルは、CrmServiceClient でこれを使用する方法を示します
ms.custom: ''
ms.date: 04/20/2020
ms.reviewer: pehecke
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: samples
applies_to:
- Dynamics 365 (online)
author: JimDaly
ms.author: nabuthuk
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 20aeaaf471e99e2201de90ceb1dbc13985baf7a4
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/21/2020
ms.locfileid: "3276709"
---
# <a name="sample-task-parallel-library-with-crmserviceclient"></a>サンプル: CrmServiceClient を使用したタスク並列ライブラリ

タスク並列ライブラリ (TPL) は、アプリケーションに並列処理と同時実行を追加するプロセスを簡略化することで、開発者の生産性を高めます。

並列処理と同時実行を追加すると、短期間に多数の CDS 操作を実行する必要があるアプリケーションのスループット総数を大幅に改善できます。

サンプルをダウンロードします: [CrmServiceClient を使用したタスク並列ライブラリのサンプル](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/Xrm%20Tooling/TPLCrmServiceClient)

## <a name="how-to-run-the-sample"></a>サンプルを実行する方法

1. サンプルをダウンロードまたは抽出し、ローカル コピーを持てるようにします。  
2. `TPLCrmServiceClient.sln` ファイルを Visual Studio で開きます。  
3. **F5** キーを押して、プログラムをコンパイルして実行します。  

## <a name="demonstrates"></a>説明

[Microsoft.Xrm.Tooling.Connector.CrmServiceClient クラス](/dotnet/api/microsoft.xrm.tooling.connector.crmserviceclient) には CDS サービス保護制限によってスローされた一時的なエラーの処理が含まれます。そのため TPL と CrmServiceClient の組み合わせは、これらの制限により拒否された要求を再試行することにより、サービス保護制限エラーへの回復性を持ちながら、スループットを最適化できるアプリケーションを作成するのに役立ちます。

詳しくは：[サービス保護APIの制限](../api-limits.md)を参照してください。

[CrmServiceClient.Clone メソッド](/dotnet/api/microsoft.xrm.tooling.connector.crmserviceclient.clone) は、TPL が複数のスレッドでクライアントを使用できるようにします。

この簡単なサンプルは、[System.Threading.Tasks.Parallel.ForEach メソッド](/dotnet/api/system.threading.tasks.parallel.foreach) を使用して、アカウント エンティティ レコードの数を生成します。

次に、その手法を再度使用して、作成されたエンティティを削除します。

**メモ**:
> 既定では、このサンプルは 10 レコードのみを作成します。これはサービス保護 API 制限エラーにヒットするには不十分です。 `numberOfRecords` 変数値を 10000 に上げると、Fiddler を使用して、一部の要求が拒否され再試行される方法に注意できます。

このサンプルは、Azure アフィニティ Cookie を無効にするよう構成されていません。これは、スループットを改善するための別の推奨事項です。 これを有効にするには、以下をアプリケーションの App.config に追加します:

```xml
  <appSettings>
    <add key="PreferConnectionAffinity"
         value="false" />
  </appSettings>
```

## <a name="code-listing"></a>コード一覧

このサンプルのコードは、同じ部分クラスの異なる部分を定義する 2 つのファイルに分割されています。

SampleProgram.cs にはこのコードが含まれています:

```csharp
using Microsoft.Xrm.Sdk;
using Microsoft.Xrm.Tooling.Connector;
using System;
using System.Collections.Generic;
using System.Linq;

namespace PowerApps.Samples
{
    public partial class SampleProgram
    {
        // Limit on the max degree of parallelism
        private static int maxDegreeOfParallelism = 10;

        //How many records to create with this sample.
        private static readonly int numberOfRecords = 10;

        [STAThread] // Added to support UX
        private static void Main()
        {
            CrmServiceClient service = null;

            try
            {
                service = SampleHelpers.Connect("Connect");
                if (service.IsReady)
                {
                    #region Sample Code

                    #region Set up

                    SetUpSample(service);

                    #endregion Set up

                    #region Demonstrate

                    #region Optimize Connection settings

                    //Change max connections from .NET to a remote service default: 2
                    System.Net.ServicePointManager.DefaultConnectionLimit = 65000;
                    //Bump up the min threads reserved for this app to ramp connections faster - minWorkerThreads defaults to 4, minIOCP defaults to 4
                    System.Threading.ThreadPool.SetMinThreads(100, 100);
                    //Turn off the Expect 100 to continue message - 'true' will cause the caller to wait until it round-trip confirms a connection to the server
                    System.Net.ServicePointManager.Expect100Continue = false;
                    //Can decreas overall transmission overhead but can cause delay in data packet arrival
                    System.Net.ServicePointManager.UseNagleAlgorithm = false;

                    #endregion Optimize Connection settings

                    // Generate a list of account entities to create.

                    var accountsToImport = new List<Entity>();
                    var count = 0;
                    Console.WriteLine($"Preparing to create {numberOfRecords} acccount records");
                    while (count < numberOfRecords)
                    {
                        var account = new Entity("account");
                        account["name"] = $"Account {count}";
                        accountsToImport.Add(account);
                        count++;
                    }

                    try
                    {
                        Console.WriteLine($"Creating {accountsToImport.Count} accounts");

                        var startCreate = DateTime.Now;

                        //Import the list of accounts
                        var createdAccounts = CreateEntities(service, accountsToImport);

                        var secondsToCreate = (DateTime.Now - startCreate).TotalSeconds;

                        Console.WriteLine($"Created {accountsToImport.Count} accounts in  {Math.Round(secondsToCreate)} seconds.");

                        Console.WriteLine($"Deleting {createdAccounts.Count} accounts");
                        var startDelete = DateTime.Now;

                        //Delete the list of accounts created
                        DeleteEntities(service, createdAccounts.ToList());

                        var secondsToDelete = (DateTime.Now - startDelete).TotalSeconds;

                        Console.WriteLine($"Deleted {createdAccounts.Count} accounts in {Math.Round(secondsToDelete)} seconds.");
                    }
                    catch (AggregateException)
                    {
                        // Handle exceptions
                    }

                    Console.WriteLine("Done.");
                    Console.ReadLine();
                }

                #endregion Demonstrate

                #endregion Sample Code

                else
                {
                    const string UNABLE_TO_LOGIN_ERROR = "Unable to Login to Common Data Service";
                    if (service.LastCrmError.Equals(UNABLE_TO_LOGIN_ERROR))
                    {
                        Console.WriteLine("Check the connection string values in cds/App.config.");
                        throw new Exception(service.LastCrmError);
                    }
                    else
                    {
                        throw service.LastCrmException;
                    }
                }
            }
            catch (Exception ex)
            {
                SampleHelpers.HandleException(ex);
            }
            finally
            {
                if (service != null)
                    service.Dispose();

                Console.WriteLine("Press <Enter> to exit.");
                Console.ReadLine();
            }
        }
    }
}
```

SampleMethods.cs には、コードで使用する 2 つの静的メソッド (`CreateEntities` および `DeleteEntities`) の定義が含まれます:


```csharp
/// <summary>
/// Creates entities in parallel
/// </summary>
/// <param name="svc">The CrmServiceClient instance to use</param>
/// <param name="entities">A List of entities to create.</param>
/// <returns></returns>
private static ConcurrentBag<EntityReference> CreateEntities(CrmServiceClient svc, List<Entity> entities)
{
    var createdEntityReferences = new ConcurrentBag<EntityReference>();

    Parallel.ForEach(entities,
        new ParallelOptions() { MaxDegreeOfParallelism = maxDegreeOfParallelism },
        () =>
        {
            //Clone the CrmServiceClient for each thread
            return svc.Clone();
        },
        (entity, loopState, index, threadLocalSvc) =>
        {
            // In each thread, create entities and add them to the ConcurrentBag
            // as EntityReferences
            createdEntityReferences.Add(
                new EntityReference(
                    entity.LogicalName,
                    threadLocalSvc.Create(entity)
                    )
                );

            return threadLocalSvc;
        },
        (threadLocalSvc) =>
        {
            //Dispose the cloned CrmServiceClient instance
            if (threadLocalSvc != null)
            {
                threadLocalSvc.Dispose();
            }
        });

    //Return the ConcurrentBag of EntityReferences
    return createdEntityReferences;
}

/// <summary>
/// Deletes a list of entity references
/// </summary>
/// <param name="svc">The CrmServiceClient instance to use</param>
/// <param name="entityReferences">A List of entity references to delete.</param>
private static void DeleteEntities(CrmServiceClient svc, List<EntityReference> entityReferences)
{
    Parallel.ForEach(entityReferences,
        new ParallelOptions() { MaxDegreeOfParallelism = maxDegreeOfParallelism },
        () =>
        {
            //Clone the CrmServiceClient for each thread
            return svc.Clone();
        },
        (er, loopState, index, threadLocalSvc) =>
        {
            // In each thread, delete the entities
            threadLocalSvc.Delete(er.LogicalName, er.Id);

            return threadLocalSvc;
        },
        (threadLocalSvc) =>
        {
            //Dispose the cloned CrmServiceClient instance
            if (threadLocalSvc != null)
            {
                threadLocalSvc.Dispose();
            }
        });
}
```

### <a name="more-information"></a>詳細

[タスク並列ライブラリ (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)