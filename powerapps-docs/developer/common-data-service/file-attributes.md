---
title: ファイル属性 (Common Data Service) | Microsoft Docs
description: アプリケーション内にファイル データを保存するファイル属性、サポートされている属性、データの取得、およびファイル データのアップロードについて説明します。
ms.custom: ''
ms.date: 05/08/2020
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: phecke
ms.author: pehecke
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 20f7614ebf0764b5c0b94f7bdef0ef935a421aaa
ms.sourcegitcommit: 241075714595a3544833040a6a16bc3def87ffcc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/28/2020
ms.locfileid: "3407934"
---
# <a name="file-attributes"></a>ファイル属性

ファイル属性は、指定した最大サイズまでファイル データを格納するために使用されます。 カスタム、またはカスタマイズ可能なエンティティは、ゼロ以上のファイル属性に加えて、各メモに 0 から 1 の添付ファイル付きのメモ (注釈) コレクションを持つことができます。 ファイル属性の <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.SchemaName> は `EntityFile` です。

Web API (REST) | .NET API (SOAP)
------- | -------
[FileAttributeMetadata](/dynamics365/customer-engagement/web-api/fileattributemetadata) | <xref:Microsoft.Xrm.Sdk.Metadata.FileAttributeMetadata>

許可されないファイルの種類については、 **ブロックする添付ファイルの拡張子の設定** 設定の [システム設定全般タブ](/power-platform/admin/system-settings-dialog-box-general-tab) を参照してください。

> [!IMPORTANT]
> いくつかの制限は、 Common Data Service のファイルおよび拡張イメージ データ型を使用するときに適用されます。 顧客管理キー (CMK) がテナントで有効になっている場合、テナントの組織は、ファイル、イメージ、IoTデータ型を使用できません。 除外されたデータ型を含むソリューションはインストールされません。 これらのデータ型を使用するには、顧客が CMK をオプトアウトする必要があります。<p/>
> ファイル属性は、<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy.SdkClientVersion> 9.0.45.329 以降および Web API バージョン 9.1 以降でサポートされています。


<!--File data is not passed to plug-ins for performance reasons. You must retrieve the file data in plug-in code using an explicit retrieve call. -->
  
<a name="BKMK_SupportingAttributes"></a>   
## <a name="supporting-attributes"></a>属性のサポート  
ファイル属性がエンティティに追加されると、一部の追加の属性がそれをサポートするために作成されます。
  
### <a name="maxsizeinkb-attribute"></a>MaxSizeInKB 属性

 この値は、属性に含めることができるファイル データの最大サイズ (KB) を表します。 この値を、特定のアプリケーションに適した最小の使用可能データ サイズに設定してください。 許容サイズ制限と既定値に対する <xref:Microsoft.Xrm.Sdk.Metadata.FileAttributeMetadata.MaxSizeInKB> のプロパティを参照してください。
 
 > [!NOTE]
 > MaxSizeInKB は、ファイル属性がエンティティに追加されるときに設定されます。 設定後は変更するできません。
  
<a name="BKMK_RetrievingFiles"></a>

## <a name="retrieve-file-data"></a>ファイル データ の取得
ファイル属性のデータを取得するには、次の API を使用します。

Web API (REST) | .NET API (SOAP)
------- | -------
 なし  | <xref:Microsoft.Crm.Sdk.Messages.InitializeFileBlocksDownloadRequest>、<br/><xref:Microsoft.Crm.Sdk.Messages.InitializeAttachmentBlocksDownloadRequest>、<br/><xref:Microsoft.Crm.Sdk.Messages.InitializeAnnotationBlocksDownloadRequest>
GET /api/data/v9.1/\<entity-type(id)\>/\<file-attribute-name\>/$value   | <xref:Microsoft.Crm.Sdk.Messages.DownloadBlockRequest>

Webサービス エンドポイントからのファイル データ転送は、単一のサービス コールで最大16 MBデータに制限されています。 その量を超えるファイル データは、4 MB以下のデータ ブロック (チャンク) に分割する必要があり、各ブロックはすべてのファイル データが受信されるまで、個別の API 呼び出しで受信されます。 ダウンロードしたデータ ブロックを結合して、ブロックを受信したのと同じ順序でデータ ブロックを結合して完全なデータ ファイルを形成するのは、ユーザーの責任です。

<xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest> と <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest> のようなメッセージを使用して、ファイル属性データをダウンロードすることはできません。

### <a name="example-rest-download-with-chunking"></a>例: チャンクを使用した REST ダウンロード

**要求**
```http
GET [Organization URI]/api/data/v9.1/accounts(id)/myfileattribute/$value
Headers:
Range: 0-1023/8192
```

**応答**
```http
206 Partial Content

Body:
byte[]

Response Headers:
Content-Disposition: attachment; filename="sample.txt"
x-ms-file-name: "sample.txt"
x-ms-file-size: 8192
Location: api/data/v9.1/accounts(id)/myfileattribute?FileContinuationToken
```

チャンクは、リクエストの `Range` ヘッダー の存在に基づいて決定されます。 範囲ヘッダー値の形式は: startByte-endByte/total バイトです。 `Range` ヘッダーが含まれない場合、完全なファイルは 1 回のリクエストで (最大 16 MB) ダウンロードされます。 チャンクの場合、 `Location` 応答ヘッダーは、クエリ可能なパラメーター `FileContinuationToken` を含みます。 次の GET 要求で保存先ヘッダー値を使用して、順序内の次のデータ ブロックを取得します。

### <a name="example-net-c-code-for-download-with-chunking"></a>例: チャンクを使用してダウンロードするための .NET C# コード

```csharp
static async Task ChunkedDownloadAsync(
            Uri urlPrefix,
            string customEntitySetName,
            string entityId,
            string entityFileOrAttributeAttributeLogicalName,
            string fileRootPath,
            string downloadFileName,
            string token)
        {
            var url = new Uri(urlPrefix, $"{customEntitySetName}({entityId})/{entityFileOrAttributeAttributeLogicalName}/$value?size=full");
            var increment = 4194304;
            var from = 0;
            var fileSize = 0;
            byte[] downloaded = null;
            do
            {
                using (var request = new HttpRequestMessage(HttpMethod.Get, url))
                {
                    request.Headers.Range = new System.Net.Http.Headers.RangeHeaderValue(from, from + increment - 1);
                    request.Headers.Authorization = new System.Net.Http.Headers.AuthenticationHeaderValue("Bearer", token);
                    using (var response = await Client.SendAsync(request))
                    {
                        if (downloaded == null)
                        {
                            fileSize = int.Parse(response.Headers.GetValues("x-ms-file-size").First());
                            downloaded = new byte[fileSize];
                        }

                        var responseContent = await response.Content.ReadAsByteArrayAsync();
                        responseContent.CopyTo(downloaded, from);
                    }
                }

                from += increment;
            } while (from < fileSize);

            await File.WriteAllBytesAsync(Path.Combine(fileRootPath, downloadFileName), downloaded);
        }
```

<a name="BKMK_UploadingFiles"></a>

## <a name="upload-file-data"></a>ファイル データ のアップロード  
ファイル属性のデータをアップロードするために、次の API を使用します。

Web API (REST) | .NET API (SOAP)
------- | -------
なし   | <xref:Microsoft.Crm.Sdk.Messages.InitializeFileBlocksUploadRequest>、<br/><xref:Microsoft.Crm.Sdk.Messages.InitializeAttachmentBlocksUploadRequest>、<br/><xref:Microsoft.Crm.Sdk.Messages.InitializeAnnotationBlocksUploadRequest>
PATCH /api/data/v9.1/\<entity-type(id)\>/\<file-attribute-name\>   | <xref:Microsoft.Crm.Sdk.Messages.UploadBlockRequest>
なし   | <xref:Microsoft.Crm.Sdk.Messages.CommitFileBlocksUploadRequest>、<br/><xref:Microsoft.Crm.Sdk.Messages.CommitAttachmentBlocksUploadRequest>、<br/><xref:Microsoft.Crm.Sdk.Messages.CommitAnnotationBlocksUploadRequest>

[ファイル データ の取得](#retrieve-file-data) で前述したように、16 MB 以下のデータ ファイルのアップロードは、1 回の API 呼び出しで実行できますが、16 MB を超えるアップロードには、ファイル データを 4 MB 以下のデータ ブロックに分割する必要があります。 データ ブロックの完全なセットをアップロードし、コミット 要求を送信すると、Web サービスは、データ ブロックがアップロードされたのと同じ順序で、ブロックを Azure Blob Storage の単一データ ファイルに自動的に結合します。

<xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> と <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest> のようなメッセージを使用して、ファイル属性データをアップロードすることはできません。

### <a name="example-rest-upload-with-chunking-first-request"></a>例: REST チャンクを使用してアップロード (最初の要求)

**要求**
```http
PATCH [Organization URI]/api/data/v9.1/accounts(id)/myfileattribute 

Headers: 
x-ms-transfer-mode: chunked 
x-ms-file-name: sample.png
```
**応答**
```http
200 OK 

Response Headers: 
x-ms-chunk-size: 4096 
Accept-Ranges: bytes 
Location: api/data/v9.1/accounts(id)/myfileattribute?FileContinuationToken 
```

### <a name="example-rest-upload-with-chunking-next-request"></a>例: REST チャンクを使用してアップロード (次の要求)
**要求**
```http
PATCH [Organization URI]/api/data/v9.1/accounts(id)/myfileattribute?FileContinuationToken 

Headers: 
Content-Range: 0-4095/8192 
Content-Type: application/octet-stream
x-ms-file-name: sample.png

Body:
byte[]
```

**応答**
```http
206 Partial Content
```

### <a name="example-net-c-code-for-upload-with-chunking"></a>例: チャンクを使用してアップロードするための .NET C# コード

```csharp
static async Task ChunkedUploadAsync(
            Uri urlPrefix,
            string customEntitySetName,
            string entityId,
            string entityFileOrAttributeAttributeLogicalName,
            string fileRootPath,
            string uploadFileName,
            string accessToken)
        {
            var filePath = Path.Combine(fileRootPath, uploadFileName);
            var fileBytes = await File.ReadAllBytesAsync(filePath);
            var url = new Uri(urlPrefix, $"{customEntitySetName}({entityId})/{entityFileOrAttributeAttributeLogicalName}");

            var chunkSize = 0;
            using (var request = new HttpRequestMessage(HttpMethod.Patch, url))
            {
                request.Headers.Add("x-ms-transfer-mode", "chunked");
                request.Headers.Authorization = new System.Net.Http.Headers.AuthenticationHeaderValue("Bearer", accessToken);
                request.Headers.Add("x-ms-file-name", uploadFileName);
                using (var response = await Client.SendAsync(request))
                {
                    response.EnsureSuccessStatusCode();
                    url = response.Headers.Location;
                    chunkSize = int.Parse(response.Headers.GetValues("x-ms-chunk-size").First());
                }
            }

            for (var offset = 0; offset < fileBytes.Length; offset += chunkSize)
            {
                var count = (offset + chunkSize) > fileBytes.Length ? fileBytes.Length % chunkSize : chunkSize;
                using (var content = new ByteArrayContent(fileBytes, offset, count))
                using (var request = new HttpRequestMessage(HttpMethod.Patch, url))
                {
                    content.Headers.Add("Content-Type", "application/octet-stream");
                    content.Headers.ContentRange = new System.Net.Http.Headers.ContentRangeHeaderValue(offset, offset + (count - 1), fileBytes.Length);
                    request.Headers.Add("x-ms-file-name", uploadFileName);
                    request.Headers.Authorization = new System.Net.Http.Headers.AuthenticationHeaderValue("Bearer", accessToken);
                    request.Content = content;
                    using (var response = await Client.SendAsync(request))
                    {
                        response.EnsureSuccessStatusCode();
                    }
                }
            }
        }
```
 
<a name="BKMK_DeletingFiles"></a>

## <a name="delete-file-data"></a>ファイル データの削除  
ストレージからファイル属性データを削除するには、次のAPIを使用します。

Web API (REST) | .NET API (SOAP)
------- | -------
DELETE /api/data/v9.1/\<entity-type(id)\>/\<attribute-name\> | <xref:Microsoft.Crm.Sdk.Messages.DeleteFileRequest>

### <a name="see-also"></a>関連項目
[イメージ属性](image-attributes.md)
