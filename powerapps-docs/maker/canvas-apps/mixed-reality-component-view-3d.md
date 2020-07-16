---
title: Power Apps で 3D コンポーネントのビューを使用 (プレビュー)
description: Power Apps で 3D モデルを表示します。
author: iaanw
manager: shellyha
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 5/22/2020
ms.author: iawilt
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e0f5df20dd7797e47ffc86bff9d5efd110b626a8
ms.sourcegitcommit: eda1684352baa7cb0f95119362177f3934a7bd4d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/28/2020
ms.locfileid: "3409838"
---
# <a name="view-3d-content-in-canvas-apps-preview"></a>キャンバス アプリで 3D コンテンツを表示 (プレビュー)

[!INCLUDE [cc-beta-prerelease-disclaimer.md](../../includes/cc-beta-prerelease-disclaimer.md)]

キャンバス アプリに 3D コンテンツを追加します。 **3D で表示**コンポーネントを使い、シンプルなジェスチャーでモデルを回転および拡大します。

単一の 3D モデルを表示、またはユーザーに [**Gallery** コントロールに接続することで](#define-where-the-3d-content-is-stored) ギャラリーから選択させることができます。

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vyoW]

> [!IMPORTANT]
> 3D コンテンツは .glb ファイル形式である必要があります。  
> さまざまな 3D 形式から [既存の 3D モデルを .glb ファイル形式に変換](/dynamics365/mixed-reality/import-tool/) できます。

コンポーネントを使用するには、使用する [各アプリの Mixed Reality (MR) 機能を有効にする](mixed-reality-overview.md#enable-the-mixed-reality-features-for-each-app) 必要があります。

[MR コンポーネントを使用するための前提条件の確認](mixed-reality-overview.md#prerequisites) も必ず実行してください。

## <a name="use-the-component"></a>コンポーネントを使用する

他の任意のコントロールまたはコンポーネントの場合と同じように、コンポーネントをアプリに挿入します。

[Power Apps Studio](https://create.powerapps.com) で編集用にアプリを開いて:

1. **挿入**タブを開きます。
2. **メディア**を拡大します。
3. コンポーネントの **3D で表示**を選択して、アプリ スクリーンの中央に配置するか、またはスクリーンの任意の場所にドラッグおよびドロップします。

いくつかのプロパティを使用してコンポーネントを変更できます。

### <a name="properties"></a>プロパティ​​

次のプロパティは、**プロパティ**と**詳細**タブのコンポーネントの **3D で表示**ウィンドウにあります。

![3D ペインのコンポーネントのビューのプロパティ](./media/augmented-3d/augmented-3d-viewer-controls.png "3D ペインのコンポーネントのビューのプロパティ")

一部のプロパティは、**3D で表示**ウィンドウの**詳細**タブでのみ使用できます。

プロパティ | 内容 | 種類​​ | 場所
- | - | - | -
ソース | 表示する .glb ファイルを識別するデータ ソース。 **3D で表示**コンポーネントは次からのモデルの読み込みをサポートします:<br/><ul><li>一般にアクセス可能な、CORS 準拠の URL</li><li>Base64 エンコードされた URI</li><li>データ コネクタを介してアクセスされる添付ファイルまたはメディア コンテンツ</li> | 適用なし | **プロパティ** (**詳細**の **Src** としても)
背景の塗りつぶし | コンポーネントの背景色を設定します | カラー ピッカー | **プロパティ** (RGBA または HTML 16 進数のカラーコードを受け入れる **BackgroundFill** としても**詳細**に含まれる)

### <a name="additional-properties"></a>追加のプロパティ

**[DisplayMode](./controls/properties-core.md)** – コントロールがユーザー入力を許可するか (**編集**)、データのみを表示するか (**表示**)、または無効にするか (**無効**) どうか。

**[Height](./controls/properties-size-location.md)** – コントロールの上端と下端間の距離。

**[TabIndex](./controls/properties-accessibility.md)** – キーボード ナビゲーションの順序。

**[Visible](./controls/properties-core.md)** – コントロールが表示されるか非表示になるか。

**[Width](./controls/properties-size-location.md)** – コントロールの左端と右端間の距離。

**[X](./controls/properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離。

**[Y](./controls/properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離。

## <a name="define-where-the-3d-content-is-stored"></a>3D コンテキストが保存されている場所を定義

.glb ファイルへのダイレクト URL、base64 エンコード URI、または添付ファイルやメディア コンテンツとして、3D コンテンツ用のソースを設定できます。

### <a name="load-models-from-a-url"></a>URL からモデルを読み込む

**Source** プロパティは、3D モデル ファイル (.glb) を指す URL にすることが可能です。

制限付きのクロス オリジン リソース共有 (CORS) 設定のあるサーバーにファイルが存在する場合、使用しているアプリで 3D モデルを表示できません。 この問題を解決するには、ホストするサーバーが *powerapps.com* からのクロス オリジン要求を許可する必要があります。

次のサービスを使用して、CORS 準拠の URL をホストおよび取得できます。

**Dropbox を使用するには**

1. 通常どおりにファイルを Dropbox にアップロードします。
1. **共有**ボタンを選択します。
1. 公開ダウンロード リンクを生成します。 たとえば、*https://www.dropbox.com/s/rANdoMGeneR4tedLink/my-file.glb?dl=0* などとします。
1. URL の **www** を **dl** に置き換え、最後に **?dl=0** を削除します。 これで、ダイレクト アクセス URL ができました。 たとえば、*https://dl.dropbox.com/s/rANdoMGeneR4tedLink/my-file.glb* などとします。

**GitHub を使用するには**

1. 使用している Git リポジトリが **公開** に設定されていることを確認します。
1. 使用しているファイルへ移動します。 たとえば、*https://github.com/microsoft/experimental-pcf-control-assets/blob/master/robot_arm.glb* などとします。
1. **/blob/** を削除します。
1. **https://github.com** を **https://raw.githubusercontent.com** に置き換えます。 これで、ファイルに直接アクセスできます。 たとえば、*https://raw.githubusercontent.com/microsoft/experimental-pcf-control-assets/master/robot_arm.glb* などとします。

### <a name="loading-base64-encoded-models"></a>base64 エンコード モデルの読み込み

**ソース** プロパティは、フォーマット *data:base64,\<base64-encoded content\>* にある base64 エンコード 3D モデル データの URI にすることが可能です。

以下は、使用しているモデルの base64 エンコード URI を作成できる 2 つの一般的な方法です。

**Power Automate を使用するには**

Power Automate では、dataUri(base64(*file content*)) 式を使い、ファイルを base64 に変換できます。 たとえば、.glb ファイルを SharePoint ドキュメント ライブラリに保存する場合、3D でビューを使用して、次のように Power Apps に読み込むことができます:

1. **SharePoint ドキュメント ライブラリ** および **SharePoint リスト**を作成します。 リストには、タイプ**複数行のテキスト**の列が必要です。
1. **ドキュメント ライブラリ**から、**新しいファイルが SharePoint に追加されたとき、カスタム アクションを完了する**テンプレートを使い、新しいフローを作成します。
1. 新しいステップを **SharePoint からファイル コンテンツを入手**に追加し、**ファイル識別子**を**識別子**に設定します。
1. 新しいステップを **SharePoint からアイテムを作成**に追加し、**リスト名**を以前作成した SharePoint に設定し、URI として以下の式を使い**題名**を複数行のテキスト列に追加します。  
    `concat('data:base64,', Last(split(dataUri(base64(body('Get_file_content'))), ',')))`  

    ![SharePoint でファイルを変換する](./media/augmented-3d/augmented-3d-convert-flow.png "SharePoint でファイルを変換する")

.glb ファイルを**ドキュメント ライブラリ**に追加すると、base64 エンコード データ URI に変換されます。これは、リストをアクセスするための SharePoint データ コネクタを使用して、**3D で表示**コンポーネントの **Source** プロパティに設定できます。

**Common Data Service を使用するには**

Common Data Service の [メモ エンティティ](/powerapps/developer/common-data-service/annotation-note-entity) は、どの添付ファイルでも **ドキュメント** フィールドの base64 に変換します。

### <a name="loading-models-as-attachments-or-media-content"></a>添付ファイルまたはメディア コンテンツとしてモデルの読み込み

添付ファイルまたはメディア コンテンツとしてモデルを読み込むことは、Power Apps に関連付けられたバイナリ記憶域を通じて起動します。 データ コネクタがバイナリ記憶域を使用しているかどうかを確認するには、ラベルを追加し、**Text**プロパティをデータ ソースに設定します。 ラベルが `appres://` で始まる場合は、そのデータ ソースは **3D で表示** コンポーネントで起動します。

**SharePoint リストを使用するには**

1. SharePoint リストを作成します。
1. 作成されたリストで、**+ 追加** 列を選択し、**列の表示/非表示** を選択します。
1. **添付ファイル** が選択されていることを確認し、上部にある **適用** を押します。
1. リストで新しいアイテムを作成し、**添付ファイルの追加** を押します。
1. 使用している 3D モデル (.glb ファイル) を選択します。
1. アプリに含める 3D モデルごとに、リストに新しいアイテムを作成します。
1. キャンバス アプリで、ギャラリーを追加します。
1. ギャラリー データ ソースを以前に作成した SharePoint リストに設定します。
1. **3D で表示** のコントロールを追加し、**詳細** タブで **Src** プロパティ を **First(Gallery1.Selected.Attachments).Value** に設定します。

**Excel Online を使用するには**

1. .glb ファイルも保存した OneDrive で、Excel Online ワークブックを作成します。

    ![OneDrive を使い .glb ファイルを共有する](./media/augmented-3d/augmented-3d-onedrive-list.png "OneDrive を使い .glb ファイルを共有する")

1. ワークブックで、**3DModel [画像]** および**名前**というタイトルの列を持つテーブルを作成します。
1. 各 .glb ファイルの行を追加し、**3DModel [画像]** 列の .glb ファイルに相対ファイル パスを挿入します。

    ![Excel Online を使い .glb ファイルを共有する](./media/augmented-3d/augmented-3d-excel-list.png "Excel Online を使い .glb ファイルを共有する")

1. キャンバスに基づいたアプリで、**ギャラリー**を追加します。
1. ギャラリー データ ソースを Excel Online ワークブックに設定します。
1. **3D で表示** コンポーネントの **詳細** プロパティ タブで、**Src** プロパティを **Gallery1.Selected.3DModel** に設定します。

## <a name="known-constraints"></a>既の制約

- Power Apps のセキュリティ アーキテクチャは、HTTP ではなく HTTPS リンクを必要とします。
- ドキュメントをホストするサーバーは、認証を必要するのではなく、[CORS 準拠](https://en.wikipedia.org/wiki/Cross-origin_resource_sharing) を必要とします。

## <a name="other-mixed-reality-components"></a>他の Mixed Reality コンポーネント

- **[Mixed Reality で表示](mixed-reality-component-view-mr.md)** コンポーネントを使用して、現実世界の 3D コンテンツと画像を表示します。
- **[Mixed Reality で測定](mixed-reality-component-measure-distance.md)** コンポーネントを使用して、距離、面積、体積を測定します。
- **[Mixed Reality で図形表示](mixed-reality-component-view-shape.md)** コンポーネントを使用して、事前定義された 3D 形状を作成して表示します
