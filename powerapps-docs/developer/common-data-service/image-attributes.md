---
title: イメージ属性 (Common Data Service) | Microsoft Docs
description: イメージ データを保存するイメージ属性、サポートされている属性、イメージ データの取得、およびイメージ データのアップロードについて説明します。
ms.custom: ''
ms.date: 04/27/2020
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: ad995909d93573992b3d999de86b57cb305be4ee
ms.sourcegitcommit: 241075714595a3544833040a6a16bc3def87ffcc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/28/2020
ms.locfileid: "3407938"
---
# <a name="image-attributes"></a>イメージ属性

特定のシステム エンティティとすべてのユーザー定義エンティティがイメージをサポートしています。 イメージをサポートしているエンティティは、サムネイルとフルサイズのプライマリ イメージのどちらも含めることができます。 サムネイル イメージは、エンティティ フォームのデータを表示するとき、Web アプリケーションで表示できます。 エンティティ インスタンスには複数イメージ属性がありますが、プライマリ イメージは 1 つだけです。 ただし、その属性の [IsPrimaryImage](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.metadata.imageattributemetadata.isprimaryimage?view=dynamics-general-ce-9#Microsoft_Xrm_Sdk_Metadata_ImageAttributeMetadata_IsPrimaryImage) を `true` に設定することにより、プライマリ イメージをある画像から別の画像に変更することができます。 各のフルサイズ イメージの属性は、30 MBに制限されています。 エンティティ イメージ属性の <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.SchemaName> は、 `EntityImage` です。 詳細: [エンティティ イメージ](/dynamics365/customer-engagement/developer/introduction-entities#entity-images)。

サムネイル画像と画像のメタデータは、画像全体を取得するために必要な情報を含む Common Data Service に格納されます。 フル画像は、Azure Blob のファイル ストレージに保存され、データ ストレージの消費を削減します。

Web API (REST) | .NET API (SOAP) 
------- | -------
[ImageAttributeMetadata](/dynamics365/customer-engagement/web-api/imageattributemetadata) | <xref:Microsoft.Xrm.Sdk.Metadata.ImageAttributeMetadata>
IsPrimaryImage、MaxHeight、MaxWidth | [IsPrimaryImage](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.metadata.imageattributemetadata.isprimaryimage?view=dynamics-general-ce-9#Microsoft_Xrm_Sdk_Metadata_ImageAttributeMetadata_IsPrimaryImage)、 [MaxHeight](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.metadata.imageattributemetadata.maxheight?view=dynamics-general-ce-9)、 [MaxWidth](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.metadata.imageattributemetadata.maxwidth?view=dynamics-general-ce-9)

イメージ属性に加え、ユーザー定義エンティティは、ファイル データを格納できるゼロ以上のファイル属性をサポートします。 これらのファイル 属性は、イメージ 属性より大量のデータを持つことができます。 詳細については [ファイル属性](file-attributes.md) を参照してください。

> [!NOTE]
> 1 つのエンティティー インスタンスに複数のイメージ属性を格納する機能、Azure BLOB の画像データの格納、30 MB の最大画像サイズ、およびファイル属性は、<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy.SdkClientVersion> 9.0.45.329 以降、および Web API バージョン 9.1 以降でサポートされています。

<a name="BKMK_SupportingAttributes"></a>   
## <a name="supporting-attributes"></a>属性のサポート  
 イメージ属性がエンティティに追加されると、一部の追加の属性がそれをサポートするために作成されます。  
  
### <a name="entityimage_timestamp-attribute"></a>EntityImage_Timestamp 属性  
 属性の種類名: `BigIntType`  
  
 値は、イメージが最後に更新されときに表され、イメージの最新版がクライアントでダウンロードされ、キャッシュされることが確実にできるように使用されます。  
  
### <a name="entityimage_url-attribute"></a>EntityImage_URL 属性  
 属性の種類名: `StringType`  
  
 クライアントでエンティティ イメージを表示する絶対 URL。  
  
 この URL はこのように構成されます:  
  
```http  
{0}/image/download.aspx?entity={1}&attribute={2}&id={3}&timestamp={4}
```  
  
- 0 : 組織 URL  
  
- 1 : エンティティの論理名  
  
- 2 : 属性の論理名  
  
- 3: EntityImageId の値。  
  
- 4: EntityImage_Timestamp の値  
  
  たとえば、次のようになります。   
  `https://myorg.crm.dynamics.com/image/download.aspx?attribute=entityimage&entity=contact&id={ECB6D3DF-4A04-E311-AFE0-00155D9C3020}&timestamp=635120312218444444`  
  
### <a name="entityimageid"></a>EntityImageId  
 属性の種類名: `UniqueIdentifierType`  
  
 イメージの一意の識別子  

### <a name="maxsizeinkb-attribute"></a>MaxSizeInKB 属性

 この値は、属性に含めることができるイメージ データの最大サイズ (KB) を表します。 この値を、特定のアプリケーションに適した最小の使用可能データ サイズに設定してください。 許容サイズ制限と既定値に対する <xref:Microsoft.Xrm.Sdk.Metadata.ImageAttributeMetadata.MaxSizeInKB> のプロパティを参照してください。
 
 > [!NOTE]
 > MaxSizeInKB は、イメージ属性がエンティティに追加されるときに設定されます。 設定後は変更するできません。

### <a name="canstorefullimage-attribute"></a>CanStoreFullImage 属性

 この値は、イメージ属性が完全なイメージを保存できるかどうか示します。 <xref:Microsoft.Xrm.Sdk.Metadata.ImageAttributeMetadata.CanStoreFullImage> プロパティを参照してください。

<a name="BKMK_RetrievingImages"></a>   
## <a name="retrieve-image-data"></a>イメージ データを取得する  

サムネイルのイメージ属性データをダウンロードするには、次の API を使用します。

Web API (REST) | .NET API (SOAP)
------- | -------
GET /api/data/v9.1/\<entity-type(id)\>/\<image-attribute-name\>/$value   | <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest> または <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest>

 > [!NOTE]
> <xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*> または <xref:Microsoft.Xrm.Sdk.IOrganizationService.Retrieve*> を使用すると、 <xref:Microsoft.Xrm.Sdk.Query.ColumnSet>.`AllColumns` の場合は `EntityImage` は含まれません。 プロパティは、 `true` に設定されます。 この属性のデータの潜在的なサイズのために、この属性を返すためには、明示的に要求する必要があります。

Webサービス エンドポイントからのイメージ データ転送は、単一のサービス コールで最大16 MB データに制限されています。 その量を超えるイメージ データは、4 MB以下のデータ ブロック (チャンク) に分割する必要があり、各ブロックはすべてのイメージ データが受信されるまで、個別の API 呼び出しで受信されます。 ダウンロードしたデータ ブロックを結合して、ブロックを受信したのと同じ順序でデータ ブロックを結合して完全なイメージを形成するのは、ユーザーの責任です。

 チャンクに関する詳細: [ファイル属性](file-attributes.md)。

完全なイメージ属性データをダウンロードするには、次の API を使用します。

Web API (REST) | .NET API (SOAP)
------- | -------
 なし  | <xref:Microsoft.Crm.Sdk.Messages.InitializeFileBlocksDownloadRequest>
GET /api/data/v9.1/\<entity-type(id)\>/\<image-attribute-name\>/$value?size=full   | <xref:Microsoft.Crm.Sdk.Messages.DownloadBlockRequest>

この場合、イメージ属性のダウンロードでは、ファイル属性のメッセージ要求を使用することに注意してください。 

### <a name="example-rest-thumbnail-download"></a>例: REST サムネイルのダウンロード

**要求**
```http
GET [Organization URI]/api/data/v9.1/accounts(b9ccec62-f266-e911-8196-000d3a6de638)/myentityimage/$value

Headers:
Content-Type: application/octet-stream
```

**応答**
```http
204 No Content

Body:
byte[]
```

### <a name="example-rest-full-image-download-16mb"></a>例: REST 完全なイメージのダウンロード (<=16MB)

**要求**
```http
GET [Organization URI]/api/data/v9.1/accounts(C0864F1C-0B71-E911-8196-000D3A6D09B3)/myentityimage/$value?size=full

Headers:
Content-Type: application/octet-stream
```
**応答**
```http
204 No Content

Body:
byte[]

Response Headers:
x-ms-file-name: "sample.png"
x-ms-file-size: 12345
```

上記の例では、クエリ文字列のパラメーター `size=full` が、完全なイメージをダウンロードすることを示します。 ファイル名とサイズは、応答ヘッダーで提供されます。

### <a name="example-rest-full-image-download-16mb"></a>例: REST 完全なイメージのダウンロード (>16MB)

**要求**
```http
GET [Organization URI]/api/data/v9.1/accounts(C0864F1C-0B71-E911-8196-000D3A6D09B3)/myentityimage/$value?size=full

Header:
Range: bytes=0-1023/8192
```
**応答**
```http
206 Partial Content

Body:
byte[]

Response Headers:
x-ms-file-name: "sample.png"
x-ms-file-size: 8192
Location: api/data/v9.1/accounts(id)/myentityimage?FileContinuationToken
```
上記の例では、 **範囲** ヘッダーは、合計 8192 バイトのイメージに対して 1024 バイトの最初のチャンクにしたダウンロードを示します。
  
<a name="BKMK_UploadingImages"></a>   
## <a name="upload-image-data"></a>イメージ データをアップロードする  
 イメージを更新するには、イメージ ファイルのコンテンツを含むバイト配列にイメージ属性の値を設定します。 サムネイル イメージは、保存前にデータのサイズを小さくするために、Web サービスによって 144x144 ピクセルの四角形に切り取られ、サイズ変更されます。 サイズの縮小は、次のルールに従います:
  
- 少なくとも 1 つの側面が 144 ピクセルより大きいイメージは中心で 144x144 に切り取られます。  
  
- 両側が144未満のイメージは最小のサイドに正方形に切り取られます。  
  
  次の表に2つの例を示します。  
  
|次の日付より前|After|  
|------------|-----------|  
|![サイズ変更前の画像](media/crm-itpro-cust-imagebeforeresize.png "サイズ変更前の画像")<br /><br /> 300x428|![サイズ変更後の画像](media/crm-itpro-cust-imageafterresize.jpg "サイズ変更後の画像")<br /><br /> 144x144|  
|![2 番目のイメージ サイズ変更の例](media/crm-itpro-cust-imagebeforeresizeexample2.png "2 番目のイメージ サイズ変更の例")<br /><br /> 91x130|![2 番目のサイズ変更の例](media/crm-itpro-cust-imageafterresizeexample2.jpg "2 番目のサイズ変更の例")<br /><br /> 91x91|

サイズが 16 MB 以下のイメージ データをアップロードするには、次のAPIを使用します。

Web API (REST) | .NET API (SOAP)
------- | -------
PUT or PATCH /api/data/v9.1/\<entity-type(id)\>/\<image-attribute-name\>   | <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> または <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest>

Webサービス エンドポイントからのイメージ データ転送は、単一のサービス コールで最大16 MB データに制限されています。 その量を超えるイメージ データは、4 MB以下のデータ ブロック (チャンク) に分割する必要があり、各ブロックはすべてのイメージ データが受信されるまで、個別の API 呼び出しでアップロードされます。 イメージ データを最大 4 MB のブロックに分割し、正しい順序でアップロードするのはユーザーの責任です。

 チャンクに関する詳細: [ファイル属性](file-attributes.md)。

サイズが 16 MB を超えるイメージ データをアップロードするには、次のAPIを使用します。

Web API (REST) | .NET API (SOAP)
------- | -------
なし   | <xref:Microsoft.Crm.Sdk.Messages.InitializeFileBlocksUploadRequest>
PATCH /api/data/v9.1/\<entity-type(id)\>/\<image-attribute-name\>   | <xref:Microsoft.Crm.Sdk.Messages.UploadBlockRequest>
なし   | <xref:Microsoft.Crm.Sdk.Messages.CommitFileBlocksUploadRequest>

イメージ データをチャンクする場合は、サイズが 16 MB 以下のイメージ 属性 (作成/更新メッセージ要求の代わりに) に対して、初期化/アップロード/コミットのブロック メッセージ要求を使用することもできます。

### <a name="example-rest-full-image-upload-16mb"></a>例: REST 完全なイメージのアップロード (<=16MB)

**要求**
```http
PUT [Organization URI]/api/data/v9.1/accounts(C0864F1C-0B71-E911-8196-000D3A6D09B3)/myentityimage

Header:
Content-Type: application/octet-stream
x-ms-file-name: sample.png

Body:
byte[]
```
アップロードが完了したら、サムネイル イメージは、Webサービスによって自動的に生成されます。 

### <a name="example-rest-upload-with-chunking-first-request"></a>例: REST チャンクを使用してアップロード (最初の要求)

**要求**
```http
PATCH [Organization URI]/api/data/v9.1/accounts(id)/myentityimage

Headers:
x-ms-transfer-mode: chunked
x-ms-file-name: sample.png
```

**応答**
```http
Response:
200 OK

Response Headers:
x-ms-chunk-size: 4096
Accept-Ranges: bytes 
Location: api/data/v9.1/accounts(id)/myentityimage?FileContinuationToken
```
上記の例で `x-ms-transfer-mode: chunked` ヘッダーは、チャンク アップロードを示します。
 
### <a name="example-rest-upload-with-chunking-next-request"></a>例: REST チャンクを使用してアップロード (次の要求)

**要求**
```http
PATCH [Organization URI]/api/data/v9.1/accounts(id)/myentityimage?FileContinuationToken

Headers:
Content-Range: bytes 0-4095/8192
Content-Type: application/octet-stream
x-ms-file-name: sample.png

Body:
byte[]
```

**応答**
```http
204 No Content
```
上記要求では、データの次のブロックがアップロードがされます。 すべてのイメージ データが、Web サービスによって受け取られた後、サムネイル イメージが Web サービスによって自動的に作成されます。

### <a name="see-also"></a>関連項目  
[ファイル属性](file-attributes.md)  
[Dynamics 365 のエンティティの概要](/dynamics365/customer-engagement/developer/introduction-entities)   
[Dynamics 365 のエンティティ属性の概要](/dynamics365/customer-engagement/developer/introduction-entity-attributes)   
[サンプル: エンティティ イメージを設定および取得する](/dynamics365/customerengagement/on-premises/developer/sample-set-retrieve-entity-images)
