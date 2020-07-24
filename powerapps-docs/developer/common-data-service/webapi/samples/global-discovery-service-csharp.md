---
title: グローバル探索サービス サンプル (C#) (Common Data Service) | Microsoft Docs
description: このサンプルは、OData v4 RESTful API を使用してグローバル探索サービスにアクセスする方法を示しています
ms.custom: ''
ms.date: 4/16/2020
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
ms.reviewer: pehecke
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 86bda5aad070aadf68c587032c8a796b96d75eee
ms.sourcegitcommit: 223c3d19ec4fbe43fcc7a16b76423c00f8602ecd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "3266411"
---
# <a name="global-discovery-service-sample-c"></a>グローバル検索サービスのサンプル (C#)

このサンプルは、OData v4 RESTful API を使用してグローバル探索にアクセスする方法を示しています。

## <a name="how-to-run-this-sample"></a>このサンプルを実行する方法

このサンプルは、Github 上に用意されています [https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/webapi/C%23/GlobalDiscovery](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/webapi/C%23/GlobalDiscovery)。

## <a name="what-this-sample-does"></a>このサンプルの概要

このサンプルは、指定されたユーザー資格情報に対して、利用可能な Common Data Service インスタンスを返します。

## <a name="how-this-sample-works"></a>このサンプルがどのように動作するか

このサンプルは、App.config ファイル内の資格情報を使用し、接続文字列内で構成された URL は使用しません。 代わりに、ユーザー資格情報およびクライアント ID だけを使用します。

### <a name="demonstrates"></a>説明

このサンプルは、HttpClient を使用して ADAL を使用した認証を行い、探索サービスを呼び出してユーザーが接続できる利用可能なインスタンスに関する情報を返します。

サンプルは、次のように `GetInstances` メソッドおよび `Instance` クラスに依存しています。

```csharp
/// <summary>
/// Uses the global discovery service to return environment instances
/// </summary>
/// <param name="username">The user name</param>
/// <param name="password">The password</param>
/// <returns>A list of Instances</returns>
static List<Instance> GetInstances(string username, string password)
{

    string GlobalDiscoUrl = "https://globaldisco.crm.dynamics.com/";
    HttpClient client = new HttpClient();
    client.DefaultRequestHeaders.Authorization = 
        new AuthenticationHeaderValue("Bearer", GetAccessToken(username, password, 
        new Uri("https://disco.crm.dynamics.com/api/discovery/")));
    client.Timeout = new TimeSpan(0, 2, 0);
    client.BaseAddress = new Uri(GlobalDiscoUrl);

    HttpResponseMessage response = 
        client.GetAsync("api/discovery/v2.0/Instances", HttpCompletionOption.ResponseHeadersRead).Result;

    if (response.IsSuccessStatusCode)
    {
        //Get the response content and parse it.
        string result = response.Content.ReadAsStringAsync().Result;
        JObject body = JObject.Parse(result);
        JArray values = (JArray)body.GetValue("value");

        if (!values.HasValues)
        {
            return new List<Instance>();
        }

        return JsonConvert.DeserializeObject<List<Instance>>(values.ToString());
    }
    else
    {
        throw new Exception(response.ReasonPhrase);
    }
}
```


```csharp
/// <summary>
  /// Object returned from the Discovery Service.
  /// </summary>
  class Instance
  {
    public string Id { get; set; }
    public string UniqueName { get; set; }
    public string UrlName { get; set; }
    public string FriendlyName { get; set; }
    public int State { get; set; }
    public string Version { get; set; }
    public string Url { get; set; }
    public string ApiUrl { get; set; }
    public DateTime LastUpdated { get; set; }
  }
```

                                                                                                                    '''