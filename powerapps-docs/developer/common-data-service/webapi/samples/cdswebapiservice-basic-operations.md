---
title: Web API CDSWebApiService の基本操作のサンプル (C#) (Common Data Service) | Microsoft Docs
description: このサンプルによって、CDSWebAPIService クラスでの Common Data Service Web API を使用して、基本的な CRUD (Create、Retrieve、Update、および Delete) の実行方法および Common Data Service のエンティティ インスタンス上での関連付けおよび関連付け解除の操作の実行方法を示します
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
ms.openlocfilehash: 8d1af1a70073b95a32e908e91b82f4afe397c0dc
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/21/2020
ms.locfileid: "3276711"
---
# <a name="web-api-cdswebapiservice-basic-operations-sample-c"></a>Web API CDSWebApiService の基本操作のサンプル (C#)

このサンプルによって、Common Data Service Web API を使用して基本的な CRUD (Create、Retrieve、Update、および Delete) の実行方法および Common Data Service エンティティ インスタンス上での関連付けおよび関連付け解除の操作の実行方法を示します。  
  
> [!NOTE]
> この Common Data Service 操作のサンプルの実装とコンソール出力は [Web API の基本操作のサンプル](../web-api-basic-operations-sample.md) で詳しく説明されています。またコモン C# の構成の使用は [Web API のサンプル (C#)](../web-api-samples-csharp.md) で説明されています。 

## <a name="prerequisites"></a>前提条件

以下は CDSWebApiService C# サンプルの構築および実行に必要です。

- Microsoft Visual Studio 2019。 
- CRUD 操作を実行する特権を用いて Common Data Service にアクセスします。
  
<a name="bkmk_runSample"></a>
  
## <a name="how-to-run-this-sample"></a>このサンプルを実行する方法

1. [Web API CDSWebApiService のサンプル](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/webapi/C%23/CDSWebApiService) に移動して、サンプル リポジトリをクローンもしくはダウンロードし、ローカル フォルダに内容を解凍してください。

1. [CDSWebApiService.sln](https://github.com/microsoft/PowerApps-Samples/blob/master/cds/webapi/C%23/CDSWebApiService/CDSWebApiService.sln) を開きます。

1. **BasicOperations** プロジェクト選択して、App.config を開きます。これは、このソリューションのすべてのサンプルで使用される共通の [App.config](https://github.com/microsoft/PowerApps-Samples/blob/master/cds/webapi/C%23/CDSWebApiService/App.config) ファイルです。 これを編集すると、このソリューションの任意のサンプルを実行できます。

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

1. **BasicOperations** プロジェクトがスタートアップ プロジェクトとして設定されていることを確認します。 プロジェクトの名前は、スタートアップ プロジェクトであることを示すために太字にする必要があります。 名前が太字でない場合は、ソリューション エクスプローラーでその名前を右クリックして、**スタートアップ プロジェクトに設定**を選択します。

1. F5 キーを押して、プログラムをデバッグ モードで実行します。

## <a name="code-listing"></a>コード一覧

このサンプルは、CDSWebAPIService プロジェクトに含まれているアセンブリに依存しています。 このクラスが提供するメソッドについては、[Web API CDSWebApiService クラス サンプル (C#)](cdswebapiservice.md) を参照してください。

以下は、Program.cs ファイルのコードです。 

```csharp
using Newtonsoft.Json.Linq;
using System;
using System.Collections.Generic;
using System.Configuration;

namespace PowerApps.Samples
{
    internal class Program
    {
        //Get configuration data from App.config connectionStrings
        private static readonly string connectionString = ConfigurationManager.ConnectionStrings["Connect"].ConnectionString;

        private static readonly ServiceConfig config = new ServiceConfig(connectionString);

        private static void Main()
        {
            //List of Uris for records created in this sample
            List<Uri> entityUris = new List<Uri>();
            bool deleteCreatedRecords = true;

            try
            {
                using (CDSWebApiService svc = new CDSWebApiService(config))
                {
                    Console.WriteLine("--Starting Basic Operations--");

                    #region Section 1: Basic Create and Update operations

                    Console.WriteLine("--Section 1 started--");
                    //Create a contact
                    var contact1 = new JObject
                        {
                            { "firstname", "Rafel" },
                            { "lastname", "Shillo" }
                        };
                    Uri contact1Uri = svc.PostCreate("contacts", contact1);
                    Console.WriteLine($"Contact '{contact1["firstname"]} " +
                        $"{contact1["lastname"]}' created.");
                    entityUris.Add(contact1Uri); //To delete later
                    Console.WriteLine($"Contact URI: {contact1Uri}");

                    //Update a contact
                    JObject contact1Add = new JObject
                    {
                        { "annualincome", 80000 },
                        { "jobtitle", "Junior Developer" }
                    };
                    svc.Patch(contact1Uri, contact1Add);
                    Console.WriteLine(
                    $"Contact '{contact1["firstname"]} {contact1["lastname"]}' " +
                    $"updated with jobtitle and annual income");

                    //Retrieve a contact
                    var retrievedcontact1 = svc.Get(contact1Uri.ToString() +
                        "?$select=fullname,annualincome,jobtitle,description");
                    Console.WriteLine($"Contact '{retrievedcontact1["fullname"]}' retrieved: \n" +
                    $"\tAnnual income: {retrievedcontact1["annualincome"]}\n" +
                    $"\tJob title: {retrievedcontact1["jobtitle"]} \n" +
                    //description is initialized empty.
                    $"\tDescription: {retrievedcontact1["description"]}.");

                    //Modify specific properties and then update entity instance.
                    JObject contact1Update = new JObject
                        {
                            { "jobtitle", "Senior Developer" },
                            { "annualincome", 95000 },
                            { "description", "Assignment to-be-determined" }
                        };
                    svc.Patch(contact1Uri, contact1Update);

                    Console.WriteLine($"Contact '{retrievedcontact1["fullname"]}' updated:\n" +
                    $"\tJob title: {contact1Update["jobtitle"]}\n" +
                    $"\tAnnual income: {contact1Update["annualincome"]}\n" +
                    $"\tDescription: {contact1Update["description"]}\n");

                    // Change just one property
                    string telephone1 = "555-0105";
                    svc.Put(contact1Uri, "telephone1", telephone1);
                    Console.WriteLine($"Contact '{retrievedcontact1["fullname"]}' " +
                        $"phone number updated.");

                    //Now retrieve just the single property.
                    var telephone1Value = svc.Get($"{contact1Uri}/telephone1");
                    Console.WriteLine($"Contact's telephone # is: {telephone1Value["value"]}.");

                    #endregion Section 1: Basic Create and Update operations

                    #region Section 2: Create record associated to another

                    /// <summary>
                    /// Demonstrates creation of entity instance and simultaneous association to another,
                    ///  existing entity.
                    /// </summary>
                    ///

                    Console.WriteLine("\n--Section 2 started--");

                    //Create a new account and associate with existing contact in one operation.
                    var account1 = new JObject
                    {
                        { "name", "Contoso Ltd" },
                        { "telephone1", "555-5555" },
                        { "primarycontactid@odata.bind", contact1Uri }
                    };
                    var account1Uri = svc.PostCreate("accounts", account1);
                    entityUris.Add(account1Uri); //To delete later
                    Console.WriteLine($"Account '{account1["name"]}' created.");
                    Console.WriteLine($"Account URI: {account1Uri}");
                    //Retrieve account name and primary contact info
                    JObject retrievedAccount1 = svc.Get($"{account1Uri}?$select=name," +
                        $"&$expand=primarycontactid($select=fullname,jobtitle,annualincome)") as JObject;

                    Console.WriteLine($"Account '{retrievedAccount1["name"]}' has primary contact " +
                        $"'{retrievedAccount1["primarycontactid"]["fullname"]}':");
                    Console.WriteLine($"\tJob title: {retrievedAccount1["primarycontactid"]["jobtitle"]} \n" +
                        $"\tAnnual income: {retrievedAccount1["primarycontactid"]["annualincome"]}");

                    #endregion Section 2: Create record associated to another

                    #region Section 3: Create related entities

                    /// <summary>
                    /// Demonstrates creation of entity instance and related entities in a single operation.
                    /// </summary>
                    ///
                    Console.WriteLine("\n--Section 3 started--");
                    //Create the following entries in one operation: an account, its
                    // associated primary contact, and open tasks for that contact.  These
                    // entity types have the following relationships:
                    //    Accounts
                    //       |---[Primary] Contact (N-to-1)
                    //              |---Tasks (1-to-N)

                    //Build the Account object inside-out, starting with most nested type(s)
                    JArray tasks = new JArray();
                    JObject task1 = new JObject
                    {
                        { "subject", "Sign invoice" },
                        { "description", "Invoice #12321" },
                        { "scheduledend", DateTimeOffset.Parse("4/19/2019") }
                    };
                    tasks.Add(task1);
                    JObject task2 = new JObject
                    {
                        { "subject", "Setup new display" },
                        { "description", "Theme is - Spring is in the air" },
                        { "scheduledstart", DateTimeOffset.Parse("4/20/2019") }
                    };
                    tasks.Add(task2);
                    JObject task3 = new JObject
                    {
                        { "subject", "Conduct training" },
                        { "description", "Train team on making our new blended coffee" },
                        { "scheduledstart", DateTimeOffset.Parse("6/1/2019") }
                    };
                    tasks.Add(task3);

                    JObject contact2 = new JObject
                    {
                        { "firstname", "Susie" },
                        { "lastname", "Curtis" },
                        { "jobtitle", "Coffee Master" },
                        { "annualincome", 48000 },
                        //Add related tasks using corresponding navigation property
                        { "Contact_Tasks", tasks }
                    };

                    JObject account2 = new JObject
                    {
                        { "name", "Fourth Coffee" },
                        //Add related contacts using corresponding navigation property
                        { "primarycontactid", contact2 }
                    };

                    //Create the account and related records
                    Uri account2Uri = svc.PostCreate("accounts", account2);
                    Console.WriteLine($"Account '{account2["name"]}  created.");
                    entityUris.Add(account2Uri); //To delete later
                    Console.WriteLine($"Contact URI: {account2Uri}");

                    //Retrieve account, primary contact info, and assigned tasks for contact.
                    //CDS only supports querying-by-expansion one level deep, so first query
                    // account-primary contact.
                    var retrievedAccount2 = svc.Get($"{account2Uri}?$select=name," +
                        $"&$expand=primarycontactid($select=fullname,jobtitle,annualincome)");

                    Console.WriteLine($"Account '{retrievedAccount2["name"]}' " +
                        $"has primary contact '{retrievedAccount2["primarycontactid"]["fullname"]}':");

                    Console.WriteLine($"\tJob title: {retrievedAccount2["primarycontactid"]["jobtitle"]} \n" +
                        $"\tAnnual income: {retrievedAccount2["primarycontactid"]["annualincome"]}");

                    //Next retrieve same contact and its assigned tasks.
                    //Don't have a saved URI for contact 'Susie Curtis', so create one
                    // from base address and entity ID.
                    Uri contact2Uri = new Uri($"{svc.BaseAddress}contacts({retrievedAccount2["primarycontactid"]["contactid"]})");
                    //Retrieve the contact
                    var retrievedcontact2 = svc.Get($"{contact2Uri}?$select=fullname," +
                        $"&$expand=Contact_Tasks($select=subject,description,scheduledstart,scheduledend)");

                    Console.WriteLine($"Contact '{retrievedcontact2["fullname"]}' has the following assigned tasks:");
                    foreach (JToken tk in retrievedcontact2["Contact_Tasks"])
                    {
                        Console.WriteLine(
                            $"Subject: {tk["subject"]}, \n" +
                            $"\tDescription: {tk["description"]}\n" +
                            $"\tStart: {tk["scheduledstart"].Value<DateTime>().ToString("d")}\n" +
                            $"\tEnd: {tk["scheduledend"].Value<DateTime>().ToString("d")}\n");
                    }

                    #endregion Section 3: Create related entities

                    #region Section 4: Associate and Disassociate entities

                    /// <summary>
                    /// Demonstrates associating and disassociating of existing entity instances.
                    /// </summary>
                    Console.WriteLine("\n--Section 4 started--");
                    //Add 'Rafel Shillo' to the contact list of 'Fourth Coffee',
                    // a 1-to-N relationship.
                    JObject rel1 = new JObject
                    {
                        { "@odata.id", contact1Uri }
                    }; //relationship object for msg content
                    Uri navUri1 = new Uri($"{account2Uri}/contact_customer_accounts/$ref");
                    //Create relationship
                    svc.Post(navUri1.ToString(), rel1);
                    Console.WriteLine($"Contact '{retrievedcontact1["fullname"]}' " +
                        $"associated to account '{account2["name"]}'.");

                    //Retrieve and output all contacts for account 'Fourth Coffee'.
                    var retrievedContactList1 = svc.Get($"{account2Uri}/contact_customer_accounts?" +
                        $"$select=fullname,jobtitle");

                    Console.WriteLine($"Contact list for account '{retrievedAccount2["name"]}':");

                    foreach (JToken ct in retrievedContactList1["value"])
                    {
                        Console.WriteLine($"\tName: {ct["fullname"]}, Job title: {ct["jobtitle"]}");
                    }

                    //Dissociate the contact from the account.  For a collection-valued
                    // navigation property, must append URI of referenced entity.
                    Uri dis1Uri = new Uri($"{navUri1}?$id={contact1Uri}");
                    //Equivalently, could have dissociated from the other end of the
                    // relationship, using the single-valued navigation ref, located in
                    // the contact 'Peter Cambel'.  This dissociation URI has a simpler form:
                    // [Org URI]/api/data/v9.1/contacts([contactid#])/parentcustomerid_account/$ref

                    svc.Delete(dis1Uri);
                    //'Rafel Shillo' was removed from the the contact list of 'Fourth Coffee'

                    //Associate an opportunity to a competitor, an N-to-N relationship.
                    //First, create the required entity instances.
                    JObject comp1 = new JObject
                    {
                        { "name", "Adventure Works" },
                        {
                            "strengths",
                            "Strong promoter of private tours for multi-day outdoor adventures"
                        }
                    };
                    Uri comp1Uri = svc.PostCreate("competitors", comp1);
                    entityUris.Add(comp1Uri); //To delete later

                    JObject oppor1 = new JObject
                    {
                        ["name"] = "River rafting adventure",
                        ["description"] = "Sales team on a river-rafting offsite and team building"
                    };
                    Uri oppor1Uri = svc.PostCreate("opportunities", oppor1);
                    entityUris.Add(oppor1Uri); //To delete later

                    //Associate opportunity to competitor via opportunitycompetitors_association.
                    // navigation property.
                    JObject rel2 = new JObject
                    {
                        { "@odata.id", comp1Uri }
                    };
                    Uri navUri2 = new Uri($"{oppor1Uri}/opportunitycompetitors_association/$ref");

                    svc.Post(navUri2.ToString(), rel2);
                    Console.WriteLine($"Opportunity '{oppor1["name"]}' associated with competitor '{comp1["name"]}'.");

                    //Retrieve all opportunities for competitor 'Adventure Works'.
                    var retrievedOpporList1 = svc.Get($"{comp1Uri}?$select=name,&$expand=opportunitycompetitors_association($select=name,description)");

                    Console.WriteLine($"Competitor '{retrievedOpporList1["name"]}' has the following opportunities:");
                    foreach (JToken op in
                        retrievedOpporList1["opportunitycompetitors_association"])
                    {
                        Console.WriteLine($"\tName: {op["name"]}, \n" +
                            $"\tDescription: {op["description"]}");
                    }

                    //Dissociate opportunity from competitor.
                    svc.Delete(new Uri($"{navUri2}?$id={comp1Uri}"));
                    // 'River rafting adventure' opportunity disassociated with 'Adventure Works' competitor

                    #endregion Section 4: Associate and Disassociate entities

                    #region Section 5: Delete sample entities

                    Console.WriteLine("\n--Section 5 started--");
                    //Delete all the created sample entities.  Note that explicit deletion is not required
                    // for contact tasks because these are automatically cascade-deleted with owner.

                    if (!deleteCreatedRecords)
                    {
                        Console.Write("\nDo you want these entity records deleted? (y/n) [y]: ");
                        String answer = Console.ReadLine();
                        answer = answer.Trim();
                        if (!(answer.StartsWith("y") || answer.StartsWith("Y") || answer == string.Empty))
                        { entityUris.Clear(); }
                        else
                        {
                            Console.WriteLine("\nDeleting created records.");
                        }
                    }
                    else
                    {
                        Console.WriteLine("\nDeleting created records.");
                    }

                    foreach (Uri entityUrl in entityUris)
                    {
                        svc.Delete(entityUrl);
                    }

                    #endregion Section 5: Delete sample entities

                    Console.WriteLine("--Basic Operations Completed--");
                    Console.WriteLine("Press any key to close");
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
[Web API を使用してエンティティを作成する](../create-entity-web-api.md)<br />
[Web API を使用したエンティティの更新と削除](../update-delete-entities-using-web-api.md)<br />
[Web API を使用してエンティティを取得する](../retrieve-entity-using-web-api.md)<br />
[Web API を使用したエンティティの更新と削除](../update-delete-entities-using-web-api.md)<br />
[Web API のサンプル](../web-api-samples.md)<br />
[Web API 基本操作のサンプル](../web-api-basic-operations-sample.md)
[Web API クエリ データのサンプル (C#)](query-data-csharp.md)<br />
[Web API 条件付き演算サンプル (C#)](conditional-operations-csharp.md)<br />
[Web API 機能およびアクションのサンプル (C#)](functions-actions-csharp.md)