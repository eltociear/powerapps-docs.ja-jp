---
title: XRMツールを使用して Common Data Serviceでアクションを実行する| MicrosoftDocs
description: CrmServiceClient クラスのオブジェクトは、Dynamics 365 データの作成、取得、更新、および削除の操作を実行するために使用できます。
ms.custom: ''
ms.date: 03/20/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: 72e9238d-e0fb-453b-b1ab-3a15ffb19838
caps.latest.revision: 13
ms.author: nabuthuk
manager: kvivek
author: Nkrb
search.audienceType:
- developer
search.app:
- D365CE
ms.openlocfilehash: ff161483f631fbd1673f36465041c5e0dbc0ac8c
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749063"
---
# <a name="use-xrm-tooling-to-execute-a-web-request-against-web-api"></a>XRM ツールキットを使用して Web API に対する Web 要求を実行する

<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient> クラス オブジェクトは、データの作成、更新、取得、または削除などの操作を Dynamics 365 データで実行するために使用します。

これからは <!--<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.ExecuteCrmWebRequest>--> XRM Web API に対する Web 要求を実行するメソッド。

次のコード サンプルは、メソッドを使用して Web 要求を実行できる方法を示しています。 <!--<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.ExecuteCrmWebRequest>-->  メソッド。 

>[!NOTE]
> このメソッドは、認証の種類が `OAuth` または `Certificate` として指定されている場合にのみ適用されます。

## <a name="create-a-record"></a>レコードの作成

次のコード サンプルは、メソッドを使用して、レコードを作成する方法を示しています。 <!--<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.ExecuteCrmWebRequest>-->  メソッド。 この例では、取引先企業を作成してから、応答オブジェクトに ID を表示します。  

```csharp
 Dictionary<string, List<string>> ODataHeaders = new Dictionary<string, List<string>>() {
        { "Accept", new List<string>() { "application/json" } },
        {"OData-MaxVersion", new List<string>(){"4.0"}},
        {"OData-Version", new List<string>(){"4.0"}}
      };

using (CrmServiceClient svc = new CrmServiceClient(conn))
 {
    if (svc.IsReady)
    {
      HttpResponseMessage response = svc.ExecuteCrmWebRequest(HttpMethod.Get, "accounts?$select=name", "{ \"name\":\"Test Account\"}", ODataHeaders, "application/json");

    if (response.IsSuccessStatusCode)
     {
        var accountUri = response.Headers.GetValues("OData-EntityId").FirstOrDefault();
        Console.WriteLine("Account URI: {0}", accountUri);
       }
    else
     {
       Console.WriteLine(response.ReasonPhrase);
        }

  }
    else
      {
        Console.WriteLine(svc.LastCrmError);
           }
}
```