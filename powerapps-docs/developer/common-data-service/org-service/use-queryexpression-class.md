---
title: QueryExpression クラスの使用 (Common Data Service) | Microsoft Docs
description: QueryExpression クラスを使用して、IOrganizationService.QueryBase) メソッドまたは RetrieveMultipleRequest メッセージで使用する複雑なクエリを作成します。
ms.custom: ''
ms.date: 04/17/2020
ms.reviewer: pehecke
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
ms.openlocfilehash: 0b405e76323300522e01956ea3eacbe7b2596f50
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/21/2020
ms.locfileid: "3275783"
---
# <a name="use-the-queryexpression-class"></a>QueryExpression クラスの使用

Common Data Service では、<xref:Microsoft.Xrm.Sdk.Query.QueryExpression> クラスを使用して、<xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*> メソッドまたは <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest> メッセージによってクエリの結果セットを絞り込むことができます。 <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> に対するクエリ パラメーターは、<xref:Microsoft.Xrm.Sdk.Query.ConditionExpression>、<xref:Microsoft.Xrm.Sdk.Query.ColumnSet>、および <xref:Microsoft.Xrm.Sdk.Query.FilterExpression> の各クラスを使用して設定できます。  
  
 <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> クラスを使用すると、複雑なクエリを作成できます。 <xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute> クラスは、指定した値と属性が一致するエンティティを簡単に検索できるように設計されています。  
  
<a name="record_count"></a>   
## <a name="record-count"></a>レコードのカウント  
 クエリで返るレコードの数を調べるには、クエリを実行する前に <xref:Microsoft.Xrm.Sdk.Query.PagingInfo.ReturnTotalRecordCount> プロパティを true に設定します。 これを行うと、<xref:Microsoft.Xrm.Sdk.EntityCollection.TotalRecordCount> が設定されます。 それ以外の場合、この値は -1 になります。  
  
## <a name="example"></a>例  
 次のサンプルは、<xref:Microsoft.Xrm.Sdk.Query.QueryExpression> クラスの使用方法を示します。  
  
```csharp  
//  Query using ConditionExpression and FilterExpression  
ConditionExpression condition1 = new ConditionExpression();  
condition1.AttributeName = "lastname";  
condition1.Operator = ConditionOperator.Equal;  
condition1.Values.Add("Brown");              
  
FilterExpression filter1 = new FilterExpression();  
filter1.Conditions.Add(condition1);  
  
QueryExpression query = new QueryExpression("contact");  
query.ColumnSet.AddColumns("firstname", "lastname");  
query.Criteria.AddFilter(filter1);  
  
EntityCollection result1 = _serviceProxy.RetrieveMultiple(query);  
Console.WriteLine();Console.WriteLine("Query using Query Expression with ConditionExpression and FilterExpression");  
Console.WriteLine("---------------------------------------");  
foreach (var a in result1.Entities)  
{  
    Console.WriteLine("Name: " + a.Attributes["firstname"] + " " + a.Attributes["lastname"]);  
}  
Console.WriteLine("---------------------------------------");  
```  
## <a name="use-sql-hints-in-a-query"></a>クエリ内の SQL ヒントを使用

<xref:Microsoft.Xrm.Sdk.Query.QueryExpression> クラスでは <xref:Microsoft.Xrm.Sdk.Query.QueryExpression.QueryHints> という名前のプロパティが含まれています。 このプロパティを以下に示すサポートされている文字列値のいずれかに設定することにより、クエリの実行に影響する生成された SQL テキストのヒントを提供できます。

|QueryHint 値 | SQL クエリ オプションとヒント |
|---------|---------|
|OptimizeForUnknown | 不明の最適化|
|ForceOrder | 強制注文 |
|再コンパイル | 再コンパイル |
|DisableRowGoal | ヒントを使用 ('Disable_Optimizer_RowGoal') |
|EnableOptimizerHotfixes | ヒントを使用 ('ENABLE_QUERY_OPTIMIZER_HOTFIXES') |
|LoopJoin | ループ結合 |
|MergeJoin | マージ結合 |
|HashJoin | ハッシュ結合 |
|NO_PERFORMANCE_SPOOL | NO_PERFORMANCE_SPOOL |
|MaxRecursion | MAXRECURSION 番号 |

詳細: [ヒント (Transact-SQL) - クエリ](https://docs.microsoft.com/sql/t-sql/queries/hints-transact-sql-query)

### <a name="see-also"></a>関連項目  
 [QueryExpression でクエリを作成する](build-queries-with-queryexpression.md)   
 [ColumnSet クラスの使用](use-the-columnset-class.md)   
 [ConditionExpression クラスの使用](use-conditionexpression-class.md)   
 [FilterExpression クラスの使用](use-filterexpression-class.md)   
 <xref:Microsoft.Xrm.Sdk.Query.QueryExpression>