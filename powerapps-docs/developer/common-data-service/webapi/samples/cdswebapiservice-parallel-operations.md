---
title: Web API CDSWebApiService の並列操作のサンプル (C#) (Common Data Service) | Microsoft Docs
description: このサンプルは、同期要求でタスク並列ライブラリ (TPL) を使用する方法を示しています。
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
ms.openlocfilehash: 8bf51ab169671f95dede5e8b68ca1fcfff8a2a39
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/21/2020
ms.locfileid: "3276707"
---
# <a name="web-api-cdswebapiservice-parallel-operations-sample-c"></a>Web API CDSWebApiService の並列操作のサンプル (C#)

この例は、[System.Threading.Tasks.Parallel.ForEach メソッド](/dotnet/api/system.threading.tasks.parallel.foreach) ループを使用して、CDS で作成する一連のレコードに対してデータの並列処理を有効にする方法を示しています。

このサンプルでは、操作内で CDSWebApiService クラスの同期メソッドを使用します。 CDSWebApiService クラスは、Service Protection API の制限を管理できるため、このコードは、クライアントが予期する一時的な 429 エラーに対して回復性があります。 構成可能な回数再試行します。 

詳細:

- [Web API CDSWebApiService クラス サンプル (C#)](cdswebapiservice.md)
- [サービス保護の API 制限](../../api-limits.md)

このサンプルは、[方法: 単純な Parallel.ForEach ループの書き込み](/dotnet/standard/parallel-programming/how-to-write-a-simple-parallel-foreach-loop) の例に基づいていますが、CDSWebApiService クラスによって提供される同期メソッドを使用して、CDS エンティティで作成および削除操作を実行するように変更されています。

> [!NOTE]
> Fiddler を使用して予想されるサービス保護 API の制限を監視する場合は、作成するレコードの数を約 10,000 に設定する必要があります。 5 分後に表示され始めます。 アプリケーションが失敗を再試行し、すべてのレコードのフローを完了する方法にご注意ください。

## <a name="prerequisites"></a>前提条件

以下は CDSWebApiService C# サンプルの構築および実行に必要です。

- Microsoft Visual Studio 2019。 
- CRUD 操作を実行する特権を用いて Common Data Service にアクセスします。
  
<a name="bkmk_runSample"></a>
  
## <a name="how-to-run-this-sample"></a>このサンプルを実行する方法

1. [Web API CDSWebApiService のサンプル](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/webapi/C%23/CDSWebApiService) に移動して、サンプル リポジトリをクローンもしくはダウンロードし、ローカル フォルダに内容を解凍してください。

1. [CDSWebApiService.sln](https://github.com/microsoft/PowerApps-Samples/blob/master/cds/webapi/C%23/CDSWebApiService/CDSWebApiService.sln) を開きます。

1. **ParallelOperations** プロジェクト選択して、App.config を開きます。これは、このソリューションのすべてのサンプルで使用される共通の [App.config](https://github.com/microsoft/PowerApps-Samples/blob/master/cds/webapi/C%23/CDSWebApiService/App.config) ファイルです。 これを編集すると、このソリューションの任意のサンプルを実行できます。

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

1. **ParallelOperations** プロジェクトがスタートアップ プロジェクトとして設定されていることを確認します。 プロジェクトの名前は、スタートアップ プロジェクトであることを示すために太字にする必要があります。 名前が太字でない場合は、ソリューション エクスプローラーでその名前を右クリックして、**スタートアップ プロジェクトに設定**を選択します。

1. F5 キーを押して、プログラムをデバッグ モードで実行します。

## <a name="code-listing"></a>コード一覧

このサンプルは、CDSWebAPIService プロジェクトに含まれているアセンブリに依存しています。 このクラスが提供するメソッドについては、[Web API CDSWebApiService クラス サンプル (C#)](cdswebapiservice.md) を参照してください。

以下は、Program.cs ファイルのコードです。

```csharp
using Newtonsoft.Json.Linq;
using System;
using System.Collections.Concurrent;
using System.Collections.Generic;
using System.Configuration;
using System.Threading.Tasks;

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

        private static void Main()
        {
            #region Optimize Connection

            //Change max connections from .NET to a remote service default: 2
            System.Net.ServicePointManager.DefaultConnectionLimit = 65000;
            //Bump up the min threads reserved for this app to ramp connections faster - minWorkerThreads defaults to 4, minIOCP defaults to 4
            System.Threading.ThreadPool.SetMinThreads(100, 100);
            //Turn off the Expect 100 to continue message - 'true' will cause the caller to wait until it round-trip confirms a connection to the server
            System.Net.ServicePointManager.Expect100Continue = false;
            //Can decreas overall transmission overhead but can cause delay in data packet arrival
            System.Net.ServicePointManager.UseNagleAlgorithm = false;

            #endregion Optimize Connection

            var parallelOptions = new ParallelOptions() { MaxDegreeOfParallelism = maxDegreeOfParallelism };

            var count = 0;

            //Will be populated with account records to import
            List<JObject> accountsToImport = new List<JObject>();
            //ConcurrentBag is a thread-safe, unordered collection of objects.
            ConcurrentBag<Uri> accountsToDelete = new ConcurrentBag<Uri>();
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

            try
            {
                using (CDSWebApiService svc = new CDSWebApiService(serviceConfig))
                {
                    Console.WriteLine($"Creating {accountsToImport.Count} accounts");
                    var startCreate = DateTime.Now;

                    //Create the accounts in parallel
                    Parallel.ForEach(accountsToImport, parallelOptions, (account) =>

                    {
                        //Add the Uri returned to the ConcurrentBag to delete later
                        accountsToDelete.Add(svc.PostCreate("accounts", account));
                    });

                    //Calculate the duration to complete
                    var secondsToCreate = (DateTime.Now - startCreate).TotalSeconds;

                    Console.WriteLine($"Created {accountsToImport.Count} accounts in  {Math.Round(secondsToCreate)} seconds.");

                    Console.WriteLine($"Deleting {accountsToDelete.Count} accounts");
                    var startDelete = DateTime.Now;

                    //Delete the accounts in parallel
                    Parallel.ForEach(accountsToDelete, parallelOptions, (uri) =>
                    {
                        svc.Delete(uri);
                    });

                    //Calculate the duration to complete
                    var secondsToDelete = (DateTime.Now - startDelete).TotalSeconds;

                    Console.WriteLine($"Deleted {accountsToDelete.Count} accounts in {Math.Round(secondsToDelete)} seconds.");
                    Console.WriteLine("Sample completed. Press any key to exit.");
                    Console.ReadLine();
                }
            }
            catch (Exception)
            {
                throw;
            }
        }
    }
}
```

### <a name="see-also"></a>関連項目

[ Common Data Service Web API を使用する](../overview.md)<br />
[Web API CDSWebApiService クラス サンプル (C#)](cdswebapiservice.md)<br />
[Web API CDSWebApiService の非同期並列操作のサンプル (C#)](cdswebapiservice-async-parallel-operations.md)<br />
[Web API CDSWebApiService の基本操作のサンプル (C#)](cdswebapiservice-basic-operations.md)<br />
[Web API を使用してエンティティを作成する](../create-entity-web-api.md)<br />
[Web API を使用したエンティティの更新と削除](../update-delete-entities-using-web-api.md)