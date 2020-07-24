---
title: Web API を使用してエンティティ レコードをマージする (Common Data Service)| Microsoft Docs
description: マージのバインドされていないアクションを使用して 2 つのエンティティ レコードをマージする方法を参照します
ms.custom: ''
ms.date: 06/04/2020
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
caps.latest.revision: 21
author: JimDaly
ms.author: jdaly
ms.reviewer: pehecke
manager: annbe
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: feb07265210fedcc170d0b9afc55bbe7d9a73ea2
ms.sourcegitcommit: dab754a07a4d4aa7a361a70173009c37fc80b0ed
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2020
ms.locfileid: "3433662"
---
# <a name="merge-entity-records-using-the-web-api"></a>Web API を使用してエンティティ レコードをマージする 

重複するレコードを見つけた場合は、[マージ アクション](/dynamics365/customer-engagement/web-api/merge) を使用して 1 つに統合できます。

> [!NOTE]
> 次のエンティティの種類のみをマージできます:
> - [account](/dynamics365/customer-engagement/web-api/account)
> - [contact](/dynamics365/customer-engagement/web-api/contact)
> - [インシデント](/dynamics365/customer-engagement/web-api/incident)
> - [lead](/dynamics365/customer-engagement/web-api/lead)


## <a name="merge-action"></a>"マージ" アクション
マージは、4 つのパラメーターを受け入れるバインドされていないアクションです:


|件名  |種類​​  |内容  |
|---------|---------|---------|
|`Target`|[crmbaseentity ](/dynamics365/customer-engagement/web-api/crmbaseentity)|マージ操作のターゲット。|
|`Subordinate`|[crmbaseentity ](/dynamics365/customer-engagement/web-api/crmbaseentity)|データのマージ元のエンティティ レコード。|
|`UpdateContent`|[crmbaseentity ](/dynamics365/customer-engagement/web-api/crmbaseentity)|マージ操作中に設定される追加のエンティティ属性。|
|`PerformParentingChecks`|Boolean|2 つのエンティティ レコードの親情報が異なるかどうかを確認するかどうかを示します。|

すべてのパラメーターが必要です。

POST 要求を使用してエンティティをマージするデータを送信します。 この例では、マージ後に残るレコードの `accountnumber` プロパティを更新するときに、2 つの取引先企業エンティティ レコードをマージします。

**要求**

```http
POST [Organization URI]/api/data/v9.0/Merge HTTP/1.1
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0
Accept: application/json

{
  "Target": {
    "name": "Account 1",
    "accountid": "bb8055c0-aea6-ea11-a812-000d3a55d474",
    "@odata.type": "Microsoft.Dynamics.CRM.account"
  },
  "Subordinate": {
    "name": "Account 2",
    "accountid": "c38055c0-aea6-ea11-a812-000d3a55d474",
    "@odata.type": "Microsoft.Dynamics.CRM.account"
  },
  "UpdateContent": {
    "accountnumber": "1234",
    "@odata.type": "Microsoft.Dynamics.CRM.account"
  },
  "PerformParentingChecks": false
}
```

> [!IMPORTANT]
> `Target`、`Subordinate`、`UpdateContent` プロパティ タイプはパラメータによって明示的に定義されていないため、`@odata.type` コメントを含めてタイプを指定する必要があります。

**回答** 

```http
HTTP/1.1 204 No Content
OData-Version: 4.0
```


### <a name="see-also"></a>関連項目

[重複レコードの統合](../../../user/merge-duplicate-records.md)<br />
<xref:Microsoft.Crm.Sdk.Messages.MergeRequest>