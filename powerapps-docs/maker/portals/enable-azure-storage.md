---
title: ポータル用の Azure Storage を有効化 | MicrosoftDocs
description: ポータル用 Azure Storage を有効にして、Azure より大きなファイル ストレージ機能を利用できるようにする手順
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/11/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 0d9b49857528cf0e55fa2ad3dfcaae2aa88b77c0
ms.sourcegitcommit: 01fefd7a06bf5d6509acd0bb54ea6479208cbbc8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/19/2019
ms.locfileid: "2815994"
---
# <a name="enable-azure-storage"></a>Azure Storage の有効化

ポータルの Azure 記憶域の統合は、 Azure のより大きいファイル ストレージ機能を利用できるようにし、既定の添付ファイルとして同じインターフェイスを使用し、同じユーザー エクスペリエンスを提供します。 この機能は、Web ファイル、エンティティ フォーム、および Web フォーム用にサポートされています。

展開モデルとして**リソース マネージャー**でストレージ アカウントを作成する必要があります。 [!include[More information](../../includes/proc-more-information.md)] [Azure Storage アカウントの作成](https://docs.microsoft.com/azure/storage/storage-create-storage-account#create-a-storage-account)。

ストレージ アカウントの実行後に、ポータルは、ストレージ アカウントを検索する方法をアプリケーションに伝える特定のグローバル設定を必要とします。 ポータル管理アプリで、 **設定** > **新規** へと移動し、 **FileStorage/CloudStorageAccount** と呼ばれる新しい設定を追加します。

> [!NOTE]
> ファイル アップロードの最大サイズは 125 MB です。

FileStorage/CloudStorageAccount の値を検索するには、[!include[Azure portal](../../includes/pn-azure-portal.md)]から接続文字列を取得する必要があります。

1. [!include[Azure portal](../../includes/pn-azure-portal.md)]にサインインします。

2. ストレージ アカウントに移動します。

3. **アクセス キー**を選択します。

    ![Azure ポータルから接続文字列の値を検索](media/key-azure-storage.png "Azure ポータルから接続文字列の値を検索")

4. 結果のパネルで、**接続文字列**というラベルのフィールドを検索します。 値をコピーする必要があるフィールドの隣で**コピー**アイコンを選択し、その値を新しい設定に貼り付けます。

    ![主要な接続文字列の値](media/primary-connection-string-azure-storage.png "主要な接続文字列の値")

    ![クラウド ストレージ アカウントのポータル設定](media/portal-site-setting-cloud-storage-account.png "クラウド ストレージ アカウントのポータル設定")

## <a name="specify-the-storage-container"></a>ストレージ コンテナーを指定します。

ストレージ アカウントに Azure BLOB コンテナーがすでにない場合は、 [!include[Azure portal](../../includes/pn-azure-portal.md)] を使用して追加する必要があります。

[ポータル管理アプリ](configure/configure-portal.md)で、 **設定** > **新規** に移動し、値としてコンテナーの名前を使用して、 **FileStorage/CloudStorageContainerName** と呼ばれる新しい設定を追加します。

![クラウド ストレージ コンテナーのポータル設定](media/portal-site-setting-cloud-storage-container.png "クラウド ストレージ コンテナーのポータル設定")

## <a name="add-cors-rule"></a>CORS ルールの追加

以下のように、クロス オリジンのリソース共有 (CORS) ルールをあなたの Azure Storage アカウントに追加する必要があります。それ以外の場合は、クラウド アイコンではなく通常の添付アイコンが表示されます:

- **許可されているオリジン**: ドメインの指定。 たとえば、`http://contoso.crm.dynamics.com` などとします。
- **許可されている動詞**: GET, PUT, DELETE, HEAD, POST
- **許可されているヘッダー**: オリジン ドメインが CORS 要求で指定できる要求ヘッダーを指定。 例えば、x-ms-meta-data\*、x-ms-meta-target\*。 
- **公開されたヘッダー**: CORS 要求への応答で送信され、ブラウザが要求発行者に公開する応答ヘッダーを指定。 例えば、x-ms-meta-\*。
- **最大期日経過日数 (秒)**: ブラウザがプリフライト OPTIONS 要求をキャッシュする最大時間を指定。 例えば、200 です。
 
[!include[More information:](../../includes/proc-more-information.md)] [Azure Storage サービスの CORS サポート](https://docs.microsoft.com/rest/api/storageservices/cross-origin-resource-sharing--cors--support-for-the-azure-storage-services)

## <a name="add-site-settings"></a>サイト設定の追加

**ポータル** > **サイト設定**から以下のサイト設定を追加します。 [!include[More information:](../../includes/proc-more-information.md)] [ポータル サイト設定の管理](configure/configure-site-settings.md#manage-portal-site-settings)。

|Name|Value|
|-----|-----|
|WebFiles/CloudStorageAccount|FileStorage/CloudStorageAccount で提供されているのと同じ接続文字列を提供します。|
|WebFiles/StorageLocation|AzureBlobStorage|
|||

ポータルで子ファイルを作成して、Azure Blob アドレス URL の完全修飾名 (コンテナーとともに) に言及することができるようになりました。 これらの設定によってポータルは、Azure Storage への Files のアップロードおよびそこからのダウンロードを開始する準備が整います。 ただし、[Azure Storage への添付ファイルのアップロードを有効にする Web リソースの追加](add-web-resource.md)したり、[エンティティ フォーム](configure-notes.md#notes-configuration-for-entity-forms) および [Web フォーム](configure-notes.md#notes-configuration-for-web-forms) を使用するのに構成するまでは、この機能をフルに活用することはできません。

### <a name="see-also"></a>関連項目

[Web リソースの追加](add-web-resource.md)

[メモを構成する](configure-notes.md)
