---
title: Web API CDSWebApiService の非同期並列操作のサンプル (C#) (Common Data Service) | Microsoft Docs
description: このサンプルは、非同期要求でタスク並列ライブラリ (TPL) データフロー コンポーネントを使用する方法を示しています。
ms.custom: ''
ms.date: 04/20/2020
ms.service: powerapps
applies_to:
- Dynamics 365 (online)
author: JimDaly
ms.author: pehecke
ms.reviewer: pehecke
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3a0ac308195bbdb2c13e769c9ccac80c79902f20
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/21/2020
ms.locfileid: "3276710"
---
# <a name="web-api-cdswebapiservice-async-parallel-operations-sample-c"></a>Web API CDSWebApiService の非同期並列操作のサンプル (C#)

このサンプルは、非同期要求でタスク並列ライブラリ (TPL) データフロー コンポーネント [データフロー (タスク並列ライブラリ)](/dotnet/standard/parallel-programming/dataflow-task-parallel-library) を使用する方法を示しています。

TPL は、アプリケーションに並列処理と同時実行を追加する機能を提供します。 これらの機能は、CDS 内でデータを追加または更新する操作を実行するときにスループットを最大化するための重要な要素です。

このサンプルでは、非同期操作内で CDSWebApiService クラスの非同期メソッドを使用します。 CDSWebApiService クラスは、Service Protection API の制限を管理できるため、このコードは、クライアントが予期する一時的な 429 エラーに対して回復性があります。 構成可能な回数再試行します。 詳しくは：[サービス保護APIの制限](../../api-limits.md)を参照してください。

このサンプルでは、作成する構成可能な数のアカウントレコードを単に作成し、それを順に削除します。 このサンプルでは、データフロー コンポーネントを使用してレコードを処理し、作成操作の結果をこれらのレコードを削除する次のフェーズに変換します。 このデータ フローの性質上、以前に作成したレコードの削除操作は、作成するすべてのレコードが完了する前に開始されます。

## <a name="prerequisites"></a>前提条件

以下は CDSWebApiService C# サンプルの構築および実行に必要です。

- Microsoft Visual Studio 2019。 
- CRUD 操作を実行する特権を用いて Common Data Service にアクセスします。
  
<a name="bkmk_runSample"></a>
  
## <a name="how-to-run-this-sample"></a>このサンプルを実行する方法

1. [Web API CDSWebApiService のサンプル](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/webapi/C%23/CDSWebApiService) に移動して、サンプル リポジトリをクローンもしくはダウンロードし、ローカル フォルダに内容を解凍してください。

1. [CDSWebApiService.sln](https://github.com/microsoft/PowerApps-Samples/blob/master/cds/webapi/C%23/CDSWebApiService/CDSWebApiService.sln) を開きます。

1. **AsyncParallelOperations** プロジェクト選択して、App.config を開きます。これは、このソリューションのすべてのサンプルで使用される共通の [App.config](https://github.com/microsoft/PowerApps-Samples/blob/master/cds/webapi/C%23/CDSWebApiService/App.config) ファイルです。 これを編集すると、このソリューションの任意のサンプルを実行できます。

1. 接続する CDS インスタンスと資格情報を設定する編集するには、`Url`、`UserPrincipalName`、および`Password` の値を編集する必要があります。

    ```xml
        <add name="Connect"
            connectionString="Url=https://yourorg.api.crm.dynamics.com;
            Authority=null;
            ClientId=51f81489-12ee-4a9e-aaae-a2591f45987d;
            RedirectUrl=app://58145B91-0C36-4500-8554-080854F2AC97;
            UserPrincipalName=you@yourorg.onmicrosoft.com;
            Password=y0urp455w0rd;
            CallerObjectId=null;
            Version=9.1;
            MaxRetries=3;
            TimeoutInSeconds=180;
            "/>
    ```

1. **AsyncParallelOperations** プロジェクトがスタートアップ プロジェクトとして設定されていることを確認します。 プロジェクトの名前は、スタートアップ プロジェクトであることを示すために太字にする必要があります。 名前が太字でない場合は、ソリューション エクスプローラーでその名前を右クリックして、**スタートアップ プロジェクトに設定**を選択します。

1. F5 キーを押して、プログラムをデバッグ モードで実行します。

## <a name="code-listing"></a>コード一覧

このサンプルは、CDSWebAPIService プロジェクトに含まれているアセンブリに依存しています。 このクラスが提供するメソッドについては、[Web API CDSWebApiService クラス サンプル (C#)](cdswebapiservice.md) を参照してください。

以下は、Program.cs ファイルのコードです。

```csharp
using Newtonsoft.Json.Linq;
using System;
using System.Collections.Generic;
using System.Configuration;
using System.Threading.Tasks;
using System.Threading.Tasks.Dataflow;

namespace PowerApps.Samples
{
    internal class Program
    {
        //Get configuration data from App.config connectionStrings
        private static readonly string connectionString = ConfigurationManager.ConnectionStrings["Connect"].ConnectionString;

        private static readonly ServiceConfig serviceConfig = new ServiceConfig(connectionString);

        //Controls the max degree of parallelism
        private static readonly int maxDegreeOfParallelism = 10;

        //How many records to create with this sample.
        private static readonly int numberOfRecords = 100;

        private static async Task Main()
        {
            #region Optimize Connection

            //Change max connections from .NET to a remote service default: 2
            System.Net.ServicePointManager.DefaultConnectionLimit = 65000;
            //Bump up the min threads reserved for this app to ramp connections faster - minWorkerThreads defaults to 4, minIOCP defaults to 4
            System.Threading.ThreadPool.SetMinThreads(100, 100);
            //Turn off the Expect 100 to continue message - 'true' will cause the caller to wait until it round-trip confirms a connection to the server
            System.Net.ServicePointManager.Expect100Continue = false;
            //Can decrease overall transmission overhead but can cause delay in data packet arrival
            System.Net.ServicePointManager.UseNagleAlgorithm = false;

            #endregion Optimize Connection

            var executionDataflowBlockOptions = new ExecutionDataflowBlockOptions
            {
                MaxDegreeOfParallelism = maxDegreeOfParallelism
            };

            var count = 0;
            double secondsToComplete;

            //Will be populated with account records to import
            List<JObject> accountsToImport = new List<JObject>();

            Console.WriteLine($"Preparing to create {numberOfRecords} acccount records using Web API.");

            //Add account records to the list to import
            while (count < numberOfRecords)
            {
                var account = new JObject
                {
                    ["name"] = $"Account {count}"
                };
                accountsToImport.Add(account);
                count++;
            }

            using (var svc = new CDSWebApiService(serviceConfig))
            {
                secondsToComplete = await ProcessData(svc, accountsToImport, executionDataflowBlockOptions);
            }

            Console.WriteLine($"Created and deleted {accountsToImport.Count} accounts in  {Math.Round(secondsToComplete)} seconds.");

            Console.WriteLine("Sample completed. Press any key to exit.");
            Console.ReadLine();
        }

        private static async Task<double> ProcessData(CDSWebApiService svc, List<JObject> accountsToImport,
            ExecutionDataflowBlockOptions executionDataflowBlockOptions)
        {
            var createAccounts = new TransformBlock<JObject, Uri>(
                async a =>
                {
                    return await svc.PostCreateAsync("accounts", a);
                },
                    executionDataflowBlockOptions
                );

            var deleteAccounts = new ActionBlock<Uri>(
                async u =>
                {
                    await svc.DeleteAsync(u);
                },
                executionDataflowBlockOptions
              );

            createAccounts.LinkTo(deleteAccounts, new DataflowLinkOptions { PropagateCompletion = true });

            var start = DateTime.Now;

            accountsToImport.ForEach(a => createAccounts.SendAsync(a));
            createAccounts.Complete();
            await deleteAccounts.Completion;

            //Calculate the duration to complete
            return (DateTime.Now - start).TotalSeconds;
        }
    }
}
```

### <a name="see-also"></a>関連項目

[ Common Data Service Web API を使用する](../overview.md)<br />
[Web API CDSWebApiService クラス サンプル (C#)](cdswebapiservice.md)<br />
[Web API CDSWebApiService の基本操作のサンプル (C#)](cdswebapiservice-basic-operations.md)<br />
[Web API CDSWebApiService の並列操作のサンプル (C#)](cdswebapiservice-parallel-operations.md)<br />
[Web API を使用してエンティティを作成する](../create-entity-web-api.md)<br />
[Web API を使用したエンティティの更新と削除](../update-delete-entities-using-web-api.md)
