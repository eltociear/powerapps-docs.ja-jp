---
title: クエリで関連エンティティ レコードを取得する (Common Data Service)| Microsoft Docs
description: ナビゲーション プロパティの拡張によって関連エンティティを取得できる方法についてお読みください。
ms.custom: ''
ms.date: 06/27/2020
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: 3D8FB9AF-3663-437A-988E-CBAE9579F167
caps.latest.revision: 78
author: JimDaly
ms.author: phecke
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: b6326523b63b3974da96a373ed6f8f2a7a63c2e3
ms.sourcegitcommit: c31f1d0385945d6265290c3eb6e49646ffbe4e18
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2020
ms.locfileid: "3517385"
---
# <a name="retrieve-related-entity-records-with-a-query"></a>クエリで関連エンティティを取得する

ナビゲーション プロパティの `$expand` システム クエリ オプションを使用して、関連エンティティからどのデータが返されるかをコントロールします。 ナビゲーション プロパティには次の 2 種類があります。  
  
- *単一値* ナビゲーション プロパティは、多対 1 関係をサポートし、別のエンティティに対する参照が設定できるような検索属性に対応します。  
  
- *コレクション値* ナビゲーション プロパティは 1 対多または多対多の関連付けに対応します。  
  
ナビゲーション プロパティ名のみを含める場合、関連レコードのすべてのプロパティが表示されます。 ナビゲーション プロパティ名の後にかっこで示される、`$select` システム クエリ オプションを使用して、関連レコードに対して返されるプロパティを制限できます。 これは、単一値とコレクション値のナビゲーション プロパティの両方で使用します。  

> [!NOTE]
>  - クエリ内の `$expand` オプションは 10 個までに制限されています。 これはパフォーマンスを保護するためです。 各 `$expand` オプションは、パフォーマンスに影響を与える可能性のある結合を作成します。 
>  - エンティティ インスタンスの関連エンティティを取得するには、「[ナビゲーション プロパティの拡張による関連エンティティの取得](retrieve-entity-using-web-api.md#bkmk_expandRelated)」を参照してください。 
> - コレクション値ナビゲーション プロパティを展開するクエリは、最新の変更を反映しないそれらのプロパティのキャッシュされたデータを返す場合があります。 ブラウザのキャッシュを上書きするには、`If-None-Match` ヘッダーと値 `null` を使用することをお勧めします。 詳細については、「[HTTP ヘッダー](compose-http-requests-handle-errors.md#bkmk_headers)」を参照してください。
> 

<a bkmk="bkmk_retrieverelatedentityexpandsinglenavprop"></a>

## <a name="retrieve-related-entity-records-by-expanding-single-valued-navigation-properties"></a>単一値のナビゲーション プロパティの拡張によって関連エンティティを取得する

以下の例は、すべての取引先企業レコードの取引先担当者を取得する方法を示します。 関連する取引先担当者レコードの場合、取引先担当者 ID およびフルネームのみを取得します。  
  
**要求**  

```http 
GET [Organization URI]/api/data/v9.1/accounts?$select=name
&$expand=primarycontactid($select=contactid,fullname) HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```  
  
**応答** 
 
```http 
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
  
{  
   "@odata.context":"[Organization URI]/api/data/v9.1/$metadata#accounts(name,primarycontactid,primarycontactid(contactid,fullname))",
   "value":[  
      {  
         "@odata.etag":"W/\"513475\"",
         "name":"Fourth Coffee (sample)",
         "accountid":"36dbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "contactid":"9cdbf27c-8efb-e511-80d2-00155db07c77",
            "fullname":"Yvonne McKay (sample)"
         }
      },
      {  
         "@odata.etag":"W/\"513477\"",
         "name":"Litware, Inc. (sample)",
         "accountid":"38dbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "contactid":"9edbf27c-8efb-e511-80d2-00155db07c77",
            "fullname":"Susanna Stubberod (sample)"
         }
      }
   ]
}
```  

エンティティ セットの関連エンティティを返す代わりに、`$ref` オプションを使用して単一値ナビゲーション プロパティを展開することにより、関連エンティティへの参照 (リンク) を返すこともできます。 次の例では、すべての取引先企業の取引先担当者レコードに対するリンクを返します。  
  
 **要求**

```http  
GET [Organization URI]/api/data/v9.1/accounts?$select=name
&$expand=primarycontactid/$ref HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```  
  
 **回答**
 
```http 
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
  
{  
   "@odata.context":"[Organization URI]/api/data/v9.1/$metadata#accounts(name,primarycontactid)",
   "value":[  
      {  
         "@odata.etag":"W/\"513475\"",
         "name":"Fourth Coffee (sample)",
         "_primarycontactid_value":"9cdbf27c-8efb-e511-80d2-00155db07c77",
         "accountid":"36dbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "@odata.id":"[Organization URI]/api/data/v9.1/contacts(9cdbf27c-8efb-e511-80d2-00155db07c77)"
         }
      },
      {  
         "@odata.etag":"W/\"513477\"",
         "name":"Litware, Inc. (sample)",
         "_primarycontactid_value":"9edbf27c-8efb-e511-80d2-00155db07c77",
         "accountid":"38dbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "@odata.id":"[Organization URI]/api/data/v9.1/contacts(9edbf27c-8efb-e511-80d2-00155db07c77)"
         }
      }
   ]
}  
```

## <a name="multi-level-expand-of-single-valued-navigation-properties"></a>単一値ナビゲーション プロパティの複数レベルの展開

`$expand` オプションを別の `$expand` オプション内に入れ子にすることで、単一値ナビゲーション プロパティを複数のレベルに展開することができます。

> [!NOTE]
> 入れ子になった `$expand` オプションの深さに制限はありませんが、クエリ内の合計 10 個の `$expand` オプションの組み合わせ制限は適用されます。


次のクエリは、`task` レコードを返し、関連する `contact`、`contact` に関連する `account`、そして最後に `account` レコードを作成した `systemuser` を展開します。

**要求**

```http
GET [Organization URI]/api/data/v9.1/tasks?$select=subject
&$expand=regardingobjectid_contact_task($select=fullname;
 $expand=parentcustomerid_account($select=name;
  $expand=createdby($select=fullname))) HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```

**回答**

```http
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  

{
    "@odata.context": "[Organization URI]/api/data/v9.1/$metadata#tasks(subject,regardingobjectid_contact_task(fullname,parentcustomerid_account(name,createdby(fullname))))",
    "value":
  [
     {
        "@odata.etag": "W/\"28876997\"",
        "subject": "Task 1 for Susanna Stubberod",
        "activityid": "834814f9-b0b8-ea11-a812-000d3a122b89",
        "regardingobjectid_contact_task": {
            "fullname": "Susanna Stubberod (sample)",
            "contactid": "824814f9-b0b8-ea11-a812-000d3a122b89",
            "parentcustomerid_account": {
                "name": "Contoso, Ltd. (sample)",
                "accountid": "7a4814f9-b0b8-ea11-a812-000d3a122b89",
                "createdby": {
                    "fullname": "Nancy Anderson",
                    "systemuserid": "4026be43-6b69-e111-8f65-78e7d1620f5e",
                    "ownerid": "4026be43-6b69-e111-8f65-78e7d1620f5e"
                }
            }
        }
    },
    {
        "@odata.etag": "W/\"28877001\"",
        "subject": "Task 2 for Susanna Stubberod",
        "activityid": "844814f9-b0b8-ea11-a812-000d3a122b89",
        "regardingobjectid_contact_task": {
            "fullname": "Susanna Stubberod (sample)",
            "contactid": "824814f9-b0b8-ea11-a812-000d3a122b89",
            "parentcustomerid_account": {
                "name": "Contoso, Ltd. (sample)",
                "accountid": "7a4814f9-b0b8-ea11-a812-000d3a122b89",
                "createdby": {
                    "fullname": "Nancy Anderson",
                    "systemuserid": "4026be43-6b69-e111-8f65-78e7d1620f5e",
                    "ownerid": "4026be43-6b69-e111-8f65-78e7d1620f5e"
                }
            }
        }
     }
  ]
}
```

<a bkmk="bkmk_retrieverelatedentityexpandcollectionnavprop"></a>

## <a name="retrieve-related-entities-by-expanding-collection-valued-navigation-properties"></a>コレクション値ナビゲーション プロパティの拡張による関連エンティティの取得

コレクション値ナビゲーション パラメーターを拡張してエンティティ セットの関連エンティティを取得すると、`@odata.nextLink` プロパティが関連エンティティに返されます。 `@odata.nextLink` プロパティの値を新しい `GET` 要求と共に使用して、必要なデータを返す必要があります。  

次の例は、上位 2 件の取引先企業レコードに割り当てられたタスクを取得します。  
  
**要求**

```http 
GET [Organization URI]/api/data/v9.1/accounts?$top=2
&$select=name
&$expand=Account_Tasks($select=subject,scheduledstart) HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```  
  
**回答** 
 
```http 
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
  
{  
   "@odata.context":"[Organization URI]/api/data/v9.1/$metadata#accounts(name,Account_Tasks,Account_Tasks(subject,scheduledstart))",
   "value":[  
      {  
         "@odata.etag":"W/\"513475\"",
         "name":"Fourth Coffee (sample)",
         "accountid":"36dbf27c-8efb-e511-80d2-00155db07c77",
         "Account_Tasks":[],
         "Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.1/accounts(36dbf27c-8efb-e511-80d2-00155db07c77)/Account_Tasks?$select%20=%20subject,%20scheduledstart"
      },
      {  
         "@odata.etag":"W/\"513477\"",
         "name":"Litware, Inc. (sample)",
         "accountid":"38dbf27c-8efb-e511-80d2-00155db07c77",
         "Account_Tasks":[],
         "Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.1/accounts(38dbf27c-8efb-e511-80d2-00155db07c77)/Account_Tasks?$select%20=%20subject,%20scheduledstart"
      }
   ]
}
 
```  

<a bkmk="bkmk_retrieverelatedentitysingleandcollectionnavprop"></a>
  
## <a name="retrieve-related-entities-by-expanding-both-single-valued-and-collection-valued-navigation-properties"></a>単一値とコレクション値の両方のナビゲーション プロパティを拡張して、関連するエンティティを取得します

次の例では、単一値とコレクション値の両方のナビゲーション プロパティを使用して、エンティティセットの関連エンティティを拡張する方法を示します。 既に説明しているように、コレクション値ナビゲーション プロパティを拡張してエンティティ セットの関連エンティティを取得すると、関連エンティティの `@odata.nextLink` プロパティが返されます。 `@odata.nextLink` プロパティの値を新しい `GET` 要求と共に使用して、必要なデータを返す必要があります。  
  
この例では、上位 2 件の取引先企業に割り当てられた取引先担当者およびタスクを取得します。  
  
**要求**

```http 
GET [Organization URI]/api/data/v9.1/accounts?$top=2
&$select=name
&$expand=primarycontactid($select=contactid,fullname),
Account_Tasks($select=subject,scheduledstart)  HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```  
  
**回答**  

```http 
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
  
{  
   "@odata.context":"[Organization URI]/api/data/v9.1/$metadata#accounts(name,primarycontactid,Account_Tasks,primarycontactid(contactid,fullname),Account_Tasks(subject,scheduledstart))",
   "value":
   [  
      {  
         "@odata.etag":"W/\"550614\"",
         "name":"Fourth Coffee (sample)",
         "accountid":"5b9648c3-68f7-e511-80d3-00155db53318",
         "primarycontactid":{  
            "contactid":"c19648c3-68f7-e511-80d3-00155db53318",
            "fullname":"Yvonne McKay (sample)"
         },
         "Account_Tasks":[],
         "Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.1/accounts(5b9648c3-68f7-e511-80d3-00155db53318)/Account_Tasks?$select%20=%20subject,%20scheduledstart"
      },
      {  
         "@odata.etag":"W/\"550615\"",
         "name":"Litware, Inc. (sample)",
         "accountid":"5d9648c3-68f7-e511-80d3-00155db53318",
         "primarycontactid":{  
            "contactid":"c39648c3-68f7-e511-80d3-00155db53318",
            "fullname":"Susanna Stubberod (sample)"
         },
         "Account_Tasks":[],
         "Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.1/accounts(5d9648c3-68f7-e511-80d3-00155db53318)/Account_Tasks?$select%20=%20subject,%20scheduledstart"
      }
   ]
}
```

## <a name="filter-collection-values-based-on-data-in-related-entities"></a>関連エンティティのデータに基づいてコレクション値をフィルターする

Web APIでは、 `any` と `all` の2つのラムダ演算子を使用して、コレクションのブール式を評価することができます。 詳細については次を参照してください: [ラムダ演算子を使用する](query-data-web-api.md#bkmk_LambdaOperators)

## <a name="see-also"></a>関連項目

[Web API を使用したクエリ データ](query-data-web-api.md)<br />
[Web API を使用して演算を実行する](perform-operations-web-api.md)<br />
[HTTP 要求の作成とエラーの処理](compose-http-requests-handle-errors.md)<br />
[Web API を使用してエンティティを作成する](create-entity-web-api.md)<br />
[Web API を使用してエンティティを取得する](retrieve-entity-using-web-api.md)<br />
[Web API を使用したエンティティの更新と削除](update-delete-entities-using-web-api.md)<br />
[Web API を使用したエンティティの関連付けと関連付け解除](associate-disassociate-entities-using-web-api.md)
