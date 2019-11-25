---
title: LINQ でエンティティ属性を使用して結果を並べ替える (Common Data Service) | Microsoft Docs
description: 検索またはオプション セット (候補リスト) 属性を使用して、LINQ クエリ内の結果の順序を指定する方法を説明します。
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 90b98b99e84a544ae524af6ed56eaa458c351a11
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749110"
---
# <a name="order-results-using-entity-attributes-with-linq"></a>エンティティ属性と LINQ を使用した結果の順序指定

アプリの Common Data Service (Common Data Service) では、検索または OptionSet (候補リスト) 属性を使用して、LINQ クエリ内の結果の順序を指定できます。 このトピックでは、この種類のクエリの例をいくつか示します。  
  
## <a name="using-a-lookup-value-to-order-by"></a>Order By に対する検索値の使用  

次のサンプルは `Order By`  句での検索属性 `PrimaryContactId` の使用を示します。  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
 var query_orderbylookup = from a in svcContext.AccountSet
                           where a.Address1_Name == "Contoso Pharmaceuticals"
                           orderby a.PrimaryContactId
                           select new
                           {
                            a.Name,
                            a.Address1_City
                           };
 foreach (var a in query_orderbylookup)
 {
  System.Console.WriteLine(a.Name + " " + a.Address1_City);
 }
}

```
  
## <a name="using-a-picklist-to-order-by"></a>Order By に対する候補リストの使用  

次のサンプルは、Order By に対する検索値の使用を示します。  
  
```csharp

using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
 var query_orderbypicklist = from c in svcContext.ContactSet
                             where c.LastName != "Parker" &&
                             c.AccountRoleCode != null
                             orderby c.AccountRoleCode, c.FirstName
                             select new
                             {
                              AccountRole = c.FormattedValues["accountrolecode"],
                              c.FirstName,
                              c.LastName
                             };
 foreach (var c in query_orderbypicklist)
 {
  System.Console.WriteLine(c.AccountRole + " " +
   c.FirstName + " " + c.LastName);
 }
}
```
  
### <a name="see-also"></a>関連項目  
 [LINQ (.NET Language-Integrated Query) を使用してクエリを作成する](build-queries-with-linq-net-language-integrated-query.md)   
 [LINQ による大量の結果セットのページング](page-large-result-sets-linq.md)