---
title: リボン定義 (モデル駆動型アプリ) をエクポートする | MicrosoftDocs
description: リボン定義のエクスポートについて学習します。
ms.custom: ''
ms.date: 04/30/2020
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: nkrb
ms.author: nabuthuk
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 2b0ca0fb153813a0ed5b48e9df8344d3b6741057
ms.sourcegitcommit: c6906775005aec98973b1f5c3dbe5924aff6d26e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2020
ms.locfileid: "3341364"
---
# <a name="export-ribbon-definitions"></a>リボン定義のエクスポート

既定の RibbonXml に対する変更を効率的に定義するには、リボンを定義する RibbonXml データを参照できる必要があります。  
  
## <a name="access-the-ribbon-definitions-for-your-organization"></a>組織のリボン定義へのアクセス  

組織のリボンが変更されたときに、カスタマイズされたリボン要素を扱う予定がある場合には現在の定義をエクスポートする必要があります。 エクスポートには、[リボン xml をエクスポートする](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ExportRibbonDefinitions)のサンプルを使用します。  
  
## <a name="access-the-default-ribbon-data"></a>既定のリボン データへのアクセス  

 モデル駆動型アプリの既定のリボン定義は、[Microsoft ダウンロード: ExportedRibbonXml.zip](https://download.microsoft.com/download/C/2/A/C2A79C47-DD2D-4938-A595-092CAFF32D6B/ExportedRibbonXml.zip) からダウンロードできます。 
  
 applicationRibbon.xml ファイルには、コア アプリケーション リボンの定義が含まれています。  
  
 残りのファイルには、エンティティ テンプレートとは異なるリボン定義を持つエンティティによって使用される定義が含まれます。 各ファイルの名前は、エンティティの名前に従って付けられています (論理エンティティ名 + Ribbon.xml)。  
  
 これらのファイルは、[サンプル: リボン定義のエクスポート](sample-export-ribbon-definitions.md) を使用する次の 2 つのメッセージの出力を表します。  
  
 <xref:Microsoft.Crm.Sdk.Messages.RetrieveApplicationRibbonRequest>  
 このメッセージは、エンティティ テンプレートを含むコア アプリケーション リボンを取得します。  
  
 <xref:Microsoft.Crm.Sdk.Messages.RetrieveEntityRibbonRequest>  
 このメッセージは、特定のエンティティで使用されるリボン定義を取得します。  
  
### <a name="decompress-the-ribbon-data"></a>リボン データを解凍する  

 リボン データは、圧縮ファイルとしてエクスポートされます。 このファイルを XML に解凍するには、[System.IO.Packaging.ZipPackage](https://msdn.microsoft.com/library/system.io.packaging.zippackage.aspx) クラスを使用する必要があります。 次の例は、SDK サンプルの中でファイルを解凍するために使用されるヘルパー メソッドです。  

 ``` C# 
/// <summary>
/// A helper method that decompresses the Ribbon data returned
/// </summary>
/// <param name="data">The compressed ribbon data</param>
/// <returns></returns>
public byte[] unzipRibbon(byte[] data)
{
 System.IO.Packaging.ZipPackage package = null;
 MemoryStream memStream = null;

 memStream = new MemoryStream();
 memStream.Write(data, 0, data.Length);
 package = (ZipPackage)ZipPackage.Open(memStream, FileMode.Open);

 ZipPackagePart part = (ZipPackagePart)package.GetPart(new Uri("/RibbonXml.xml", UriKind.Relative));
 using (Stream strm = part.GetStream())
 {
  long len = strm.Length;
  byte[] buff = new byte[len];
  strm.Read(buff, 0, (int)len);
  return buff;
 }
}

```

### <a name="retrieve-the-application-ribbon-data"></a>アプリケーション リボン データを取得する  

 アプリケーション リボンは、次の例に示すように、<xref:Microsoft.Crm.Sdk.Messages.RetrieveApplicationRibbonRequest> を使用して取得できます。  

 ```C# 
 //Retrieve the Application Ribbon
var appribReq = new RetrieveApplicationRibbonRequest();
var appribResp = (RetrieveApplicationRibbonResponse)service.Execute(appribReq);

System.String applicationRibbonPath = Path.GetFullPath(exportFolder + "\\applicationRibbon.xml");
File.WriteAllBytes(applicationRibbonPath, unzipRibbon(appribResp.CompressedApplicationRibbonXml)); 
```
  
### <a name="retrieve-entity-ribbons"></a>エンティティ リボンを取得する  

 エンティティのリボン定義を取得するには、<xref:Microsoft.Crm.Sdk.Messages.RetrieveEntityRibbonRequest> のパラメーターとしてエンティティの名前を指定するだけです。  
  
 リボンをサポートするすべてのエンティティのリボン定義を取得するには、エンティティ リボン テンプレートとは異なるリボン定義を持つシステム エンティティの一覧が必要です。 以下のサンプルは、リボン定義を持つすべてのシステム エンティティの配列を示します。  

 ```C# 
 //This array contains all of the system entities that use the ribbon.
public System.String[] entitiesWithRibbons = {"account",
"activitymimeattachment",
"activitypointer",
"appointment",
"bulkoperation",
"calendar",
"campaign",
"campaignactivity",
"campaignresponse",
"competitor",
"connection",
"contact",
"contract",
"contractdetail",
"convertrule",
"convertruleitem",
"customeraddress",
"discount",
"discounttype",
"email",
"emailserverprofile",
"entitlement",
"entitlementchannel",
"entitlementtemplate",
"entitlementtemplatechannel",
"fax",
"goal",
"goalrollupquery",
"importfile",
"incident",
"invoice",
"invoicedetail",
"kbarticle",
"kbarticlecomment",
"lead",
"letter",
"list",
"listmember",
"mailbox",
"metric",
"opportunity",
"opportunityproduct",
"partnerapplication",
"phonecall",
"postfollow",
"pricelevel",
"product",
"productpricelevel",
"queue",
"queueitem",
"quote",
"quotedetail",
"recurringappointmentmaster",
"report",
"rollupfield",
"routingrule",
"routingruleitem",
"salesliterature",
"salesliteratureitem",
"salesorder",
"salesorderdetail",
"service",
"serviceappointment",
"sharepointdocument",
"sharepointdocumentlocation",
"sharepointsite",
"site",
"sla",
"slaitem",
"socialactivity",
"socialprofile",
"systemuser",
"task",
"team",
"teamtemplate",
"territory",
"uom",
"uomschedule",
"userquery"};
 ```
  
以下のサンプルは、一連のエンティティのリボン定義の取得方法を示します。 

```csharp
//Retrieve system Entity Ribbons
var entRibReq = new RetrieveEntityRibbonRequest() { RibbonLocationFilter = RibbonLocationFilters.All };
foreach (System.String entityName in entitiesWithRibbons)
{
 entRibReq.EntityName = entityName;
 var entRibResp = (RetrieveEntityRibbonResponse)service.Execute(entRibReq);

 System.String entityRibbonPath = Path.GetFullPath(exportFolder + "\\" + entityName + "Ribbon.xml");
 File.WriteAllBytes(entityRibbonPath, unzipRibbon(entRibResp.CompressedEntityXml));
 //Write the path where the file has been saved.
 Console.WriteLine(entityRibbonPath);
} 
``` 
ユーザー定義エンティティも、リボンのカスタマイズをサポートします。 ユーザー定義エンティティの一覧を取得するには、<xref:Microsoft.Xrm.Sdk.Messages.RetrieveAllEntitiesRequest> を使用してユーザー定義エンティティの名前を取得します。 以下のサンプルは、すべてのユーザー定義エンティティのリボン定義の取得方法を示します。  

```csharp 
//Check for custom entities
 var raer = new RetrieveAllEntitiesRequest() { EntityFilters = EntityFilters.Entity };
 var resp = (RetrieveAllEntitiesResponse)service.Execute(raer);
 foreach (EntityMetadata em in resp.EntityMetadata)
 {
  if (em.IsCustomEntity == true && em.IsIntersect == false)
  {
   entRibReq.EntityName = em.LogicalName;
   var entRibResp = (RetrieveEntityRibbonResponse)service.Execute(entRibReq);
   System.String entityRibbonPath = Path.GetFullPath(exportFolder + "\\" + em.LogicalName + "Ribbon.xml");
   File.WriteAllBytes(entityRibbonPath, unzipRibbon(entRibResp.CompressedEntityXml));
   //Write the path where the file has been saved.
   Console.WriteLine(entityRibbonPath);
  }
 } 
``` 

## <a name="troubleshoot-ribbon-issues"></a>リボンの問題のトラブルシューティング

リボン コマンド バー ボタンで問題が発生している場合は、次の[トラブルシューティング ガイド](https://support.microsoft.com/help/4552163)を使用して問題を見つけ解決してください。

### <a name="see-also"></a>関連項目  
 [リボンのカスタマイズ](customize-commands-ribbon.md)   
 [バーまたはリボンの表示](command-bar-ribbon-presentation.md)   
 [エクスポート、編集の準備、およびリボンのインポート](export-prepare-edit-import-ribbon.md)
