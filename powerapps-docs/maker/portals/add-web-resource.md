---
title: フォームに Azure Storage Web リソースを追加 | MicrosoftDocs
description: Azure Storage に添付ファイルをアップロードできるようフォームに Azure Storage Web リソースを追加する手順。
author: gitanjalisingh33msft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 05/27/2020
ms.author: gisingh
ms.reviewer: tapanm
ms.openlocfilehash: 0758244f614be79e738eb4fbd3ac9988f54080c0
ms.sourcegitcommit: c12260f372ad2cc48d3146be570d2088c9ef1d86
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2020
ms.locfileid: "3493437"
---
# <a name="add-the-azure-storage-web-resource-to-a-form"></a>フォームに Azure Storage Web リソースを追加する

Common Data Service に直接ではなく Azure Storage にアップロードした添付ファイルは、Common Data Service のメモを使用して管理できます。

特定のフォームからの添付ファイルを Azure Storage にアップロードできるようにするには、Web リソースをそのフォームに追加し、[組織に Azure Storage を構成する](enable-azure-storage.md) 必要があります。

> [!NOTE]
> この例では、フォームは潜在顧客エンティティの潜在顧客フォームに追加されます。 既存のフォームを編集する場合は注意なさるようお勧めします。

ポータルを使用してファイル (たとえば attachments.zip) を Azure Storage にアップロードする場合、それはエンティティ上のメモと添付ファイルのプレースホルダーで表されます。

![フォームの添付ファイル](media/notes-attachment-lead-form.png "フォームの添付ファイルのプレースホルダー")

添付ファイルは、attachment.zip.txt という名前になりました。 既定では、Common Data Service に Azure ファイルの概念がないので、代わりにこのプレースホルダー .txt ファイルは Common Data Service に保存されます。 プレースホルダー ファイルの Azure Storage コンテキストが、そのファイルについての詳細を示します。
```
{
 Name: attachment.zip,
 Type: application/x-zip-compressed,
 Size: 24890882,
 "Url": "https://accountname.blob.core.windows.net/storage/81a9a9491c36e51182760026833bcf82/attachment.zip"
}
```

Azure に保存されているファイルを表示したり操作したりするには、Web リソースの adx.annotations.html をそのフォームに追加する必要があります。 前提条件として、ユーザーに adx_setting への読み取りアクセス権があることを確認します。 それ以外の場合は、Web リソースは適切に表示されません。

1. 関連するフォームのフォーム エディターで、**挿入**タブの **Web リソース**を選択します。

2. **Web リソース**ボックスで、**adx_annotations/adx.annotations.html** を選択します。

3. リソースの名前とラベルを入力します。

4. **カスタム パラメーター (データ)** ボックスで、**azureEnabled=true** と入力します。 <br>このように Azure サポートを有効にせずに Web リソースを使用することもできますが、その場合は既定のコントロールとほぼ全く同様に機能します。</br>

5. **形式**タブで、必要に応じた形式ルールを選択します。 **境界の表示**チェック ボックスをオフにすることをお勧めします。

6. **OK** を選択してリソースを保存します。

7. 必要に応じて、既存のメモ コントロールを削除できます。 または、既定で非表示になるようマークされているタブまたはセクションに移動することができます。

8. フォームを保存してから、その変更を公開します。

   ![Web リソースの追加](media/add-web-resource.png "Web リソースの追加")

新しいコントロールがページに表示されるようになり、添付ファイルを Azure Storage で管理できるようになります。

![フォームの Azure ファイル添付](media/azure-file-attachment-lead-form.png "フォームの Azure ファイル添付")

このファイルが Azure Storage に保存されていることを示すために、ペーパークリップ アイコンはクラウド アイコンに置き換えられています。 引き続き添付ファイルを Common Data Service に保存することもでき、それらのファイルはペーパークリップ アイコンで示されます。

> [!NOTE]
> 以下のように、クロス オリジンのリソース共有 (CORS) ルールをあなたの Azure Storage アカウントに追加する必要があります。それ以外の場合は、クラウド アイコンではなく通常の添付アイコンが表示されます。
> - **許可されているオリジン**: ドメインの指定。 例:`https://contoso.crm.dynamics.com`  <br> 許可されているオリジンに末尾の `/` がないことを確認してください。 たとえば、`https://contoso.crm.dynamics.com/` は正しくありません。
> - **許可されている動詞**: GET, PUT, DELETE, HEAD, POST
> - **許可されているヘッダー**: オリジン ドメインが CORS 要求で指定できる要求ヘッダーを指定。 例えば、x-ms-meta-data\*、x-ms-meta-target\*。 このシナリオでは、* を指定する必要があります。それ以外の場合は、Web リソースは適切に表示されません。
> - **公開されたヘッダー**: CORS 要求への応答で送信され、ブラウザが要求発行者に公開する応答ヘッダーを指定。 例 - \*or x-ms-meta-\*。 このシナリオでは、* を指定する必要があります。それ以外の場合は、Web リソースは適切に表示されません。
> - **最大期日経過日数 (秒)**: ブラウザがプリフライト OPTIONS 要求をキャッシュする最大時間を指定。 例えば、200 です。
> 
> [!include[More information](../../includes/proc-more-information.md)] [Azure Storage サービスの CORS サポート](https://docs.microsoft.com/rest/api/storageservices/cross-origin-resource-sharing--cors--support-for-the-azure-storage-services)。

添付ファイルが画像の場合、保存先が Common Data Service であっても Azure Storage であっても、コントロールはその画像をサムネイルとして表示します。

> [!NOTE]
> サムネイル機能は、サイズが 1 MB 以下の画像に制限されています。

![メモのサムネイル](media/notes-thumbnail.png "メモのサムネイル")

### <a name="processes-for-azure-blob-storage"></a>Azure Blob Storage のプロセス

添付ファイルを Azure Storage にアップロードするには、2 つのプロセスが必要です。**Azure Blob Storage の URL** と **AzureBlobStorageEnabled** です。

![Blob Storage のプロセス](media/blob-storage-processes.png "Blob Storage のプロセス")

移行中に、プロセスが非アクティブになる場合があります。 これにより、Web リソースを追加する手順に従って、添付ファイルが Azure Storage ではなく Common Data Service にアップロードされる可能性があります。 添付ファイルを Azure Storage にアップロードするために、これら 2 つのプロセスがアクティブ化されていることを確認してください。

## <a name="cors-protocol-support"></a>CORS プロトコル サポート

[クロス オリジン リソース共有 (CORS)](https://www.w3.org/TR/cors/) プロトコルは、反応が別のドメイン内で共有できるかどうかを表す一連のヘッダーで構成されます。
次のサイト設定は CORS を構成するのに使用されます。

| サイト設定 | 要求ヘッダー | 説明 |
|-|-|-|
| HTTP/Access-Control-Allow-Credentials | Access-Control-Allow-Credentials | このヘッダーの唯一の有効な値は true です (文字と小文字が区別されます)。 資格情報を必要としなくなった場合、(値を false に設定するよりもむしろ) このヘッダー全体を省略します。 
| HTTP/Access-Control-Allow-Headers | Access-Control-Allow-Headers | サポートされた HTTP 要求ヘッダーのコンマ区切りの一覧。
| HTTP/Access-Control-Allow-Methods | Access-Control-Allow-Methods | GET、POST、OPTIONS などの、許可された HTTP 要求メソッドのコンマ区切りの一覧。
| HTTP/Access-Control-Allow-Origin | Access-Control-Allow-Origin | Dynamics 365 インスタンスの URL (https://contoso.crm.dynamics.com など)。 URI がリソースにアクセスできるようにするには、\* を使用します。                 |
|  HTTP/Access-Control-Expose-Headers | Access-Control-Expose-Headers | リソースが使用するまたは公開できる簡単な応答ヘッダー以外の、HTTP ヘッダー名のコンマ区切りの一覧。
| HTTP/Access-Control-Max-Age | Access-Control-Max-Age |  結果がキャッシュされる最大秒数。
| HTTP/Content-Security-Policy | Content-Security-Policy | 特定のページに対してユーザーエージェントが読み込みことができるリソースを制御します。
| HTTP/Content-Security-Policy-Report-Only | Content-Security-Policy-Report-Only | Web開発者は、ポリシーの効果を監視するだけであり、ポリシーの効果を強制することはできません。 これらの違反レポートは、HTTP POST リクエストを介して指定された URI に送信される JSON ドキュメントで構成されます。
| HTTP/X-Frame-Options | X-Frame-Options | ブラウザが、*\<frame\>*、*\<iframe\>*、*\<embed\>*、*\<object\>* でページをレンダリングできるようにするかどうかを示します。
| HTTP/X-Content-Type-Options | X-Content-Type-Options | *Content-Type* で、MIME スニッフィングを無効にし、ブラウザで指定したタイプを使用するように強制します。
