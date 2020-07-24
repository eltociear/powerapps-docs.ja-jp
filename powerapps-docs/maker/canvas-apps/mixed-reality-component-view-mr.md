---
title: Power Apps で MR コンポーネントのビューを使用する (プレビュー)
description: Power Apps で拡張現実機能を使用して、現実世界の 3D モデルと 2D 画像を表示します。
author: iaanw
manager: shellyha
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 5/4/2020
ms.author: iawilt
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 5b6445ef8a604085ad139f89972bddb83c1ff71c
ms.sourcegitcommit: eda1684352baa7cb0f95119362177f3934a7bd4d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/28/2020
ms.locfileid: "3409662"
---
# <a name="view-3d-content-or-images-in-the-real-word-preview"></a>実際の言葉で 3D コンテンツまたは画像を表示する (プレビュー)

[!INCLUDE [cc-beta-prerelease-disclaimer.md](../../includes/cc-beta-prerelease-disclaimer.md)]

アプリの **MR で表示**コンポーネントを使用して、特定のアイテムが指定されたスペースにどのように収まるかをユーザーが確認できるようにします。

コンポーネントは、アプリにボタンを作成します。 アプリ ユーザーがボタンをクリックすると、選択した 3D モデル (.glb ファイル形式) または画像 (.jpg または .png ファイル形式) がデバイスのライブ カメラ フィードにオーバーレイされます。

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vvwR]



> [!IMPORTANT]
> 3D コンテンツは .glb ファイル形式である必要があります。  
> さまざまな 3D 形式から [既存の 3D モデルを .glb ファイル形式に変換](/dynamics365/mixed-reality/import-tool/) できます。

コンポーネントを使用するには、使用する [各アプリの Mixed Reality (MR) 機能を有効にする](mixed-reality-overview.md#enable-the-mixed-reality-features-for-each-app) 必要があります。

[MR コンポーネントを使用するための前提条件の確認](mixed-reality-overview.md#prerequisites) も必ず実行してください。

> [!TIP]
> MR コンポーネントは、フラット テクスチャ サーフェスの明るい環境で最適に動作します。 追跡を確立するときは、追跡するサーフェスにデバイスを向け、広い腕の動きでデバイスを右から左にゆっくりとパンします。 追跡に失敗した場合は、終了して MR ビューを入力し、追跡をリセットして再試行してください。

## <a name="use-the-component"></a>コンポーネントを使用する

他の任意のボタン コントロールまたはコンポーネントの場合と同じように、コンポーネントをアプリに挿入します。

[Power Apps Studio](https://create.powerapps.com) で編集用にアプリを開いて:

1. **挿入**タブを開きます。
2. **Mixed reality** を展開します。
3. コンポーネントの **MR で表示**を選択して、アプリ スクリーンの中央に配置するか、またはスクリーンの任意の場所にドラッグおよびドロップします。

   ![MR コンポーネントのビューをアプリに挿入する](./media/augmented-view-mr/augmented-view-mr.png "MR コンポーネントのビューをアプリに挿入する")

いくつかのプロパティを使用してコンポーネントを変更できます。

### <a name="properties"></a>プロパティ​​

次のプロパティは、**プロパティ**と**詳細**タブでコンポーネントの **MR で表示**ウィンドウにあります。

![MR ペインのビューのプロパティ](./media/augmented-view-mr/augmented-view-mr-properties.png "MR ペインのビューのプロパティ")

一部のプロパティは、**MR で表示**ウィンドウの**詳細**タブの**詳細オプション**でのみ使用できることに注意してください。

プロパティ | 内容 | 種類​​ | 場所
- | - | - | -
テキスト | ボタンのラベル | 文字列 | プロパティ (**詳細**にもあります)
表示の種類 | ボタンにアイコン、テキスト、またはその両方が表示されるかどうか。 | ドロップダウン セレクション | プロパティ (**詳細**にもあります)
ソース | 表示する .glb ファイルを識別するデータ ソース。 **MR で表示**コンポーネントは次からのモデルの読み込みをサポートします:<br/><ul><li>一般にアクセス可能な、CORS 準拠の URL。</li><li>Base64 エンコードされた URI。</li><li>データ コネクタを介してアクセスされる添付ファイルまたはメディア コンテンツ。</li></ul><br/>詳細については、**3D で表示**コンポーネントの [3D コンテンツの格納場所を定義する](mixed-reality-component-view-3d.md#define-where-the-3d-content-is-stored) を参照してください。 | 適用なし | **プロパティ** (**詳細**にもあります)
オブジェクトの幅 | 表示される画像または 3D コンテンツの幅。 | Integer | **プロパティ** (**詳細**にもあります)
オブジェクトの高さ | 表示される画像または 3D コンテンツの高さ。 | Integer | **プロパティ** (**詳細**にもあります)
オブジェクトの深さ | 3D コンテンツの 3 次元の深さ。 | Integer | **プロパティ** (**詳細**にもあります)
出荷単位 | オブジェクトの幅、高さ、深さフィールドに使用される単位。 | ドロップダウン セレクション | **プロパティ** (**詳細**にもあります)
写真 | Mixed Reality セッション中にキャプチャされた写真。 | | 該当なし (出力プロパティのみ)

### <a name="additional-properties"></a>追加のプロパティ

**[BorderColor](./controls/properties-color-border.md)** – コントロールの境界線の色。

**[BorderStyle](./controls/properties-color-border.md)** – コントロールの境界線が**実線**、**破線**、**点線**、または**なし**かどうか。

**[BorderThickness](./controls/properties-color-border.md)** – コントロールの境界線の太さ。

**[Color](./controls/properties-color-border.md)** – コントロールのテキストの色。

**[DisplayMode](./controls/properties-core.md)** – コントロールがユーザー入力を許可するか (**編集**)、データのみを表示するか (**表示**)、または無効にするか (**無効**) どうか。

**[DisabledBorderColor](./controls/properties-color-border.md)** – コントロールの **[DisplayMode](./controls/properties-core.md)** プロパティが**無効**に設定されている場合のコントロールの境界線の色。

**[DisabledColor](./controls/properties-color-border.md)** – コントロールの **[DisplayMode](./controls/properties-core.md)** プロパティが**無効**に設定されている場合のコントロール内のテキストの色。

**[DisabledFill](./controls/properties-color-border.md)** – コントロールの **[DisplayMode](./controls/properties-core.md)** プロパティが**無効**に設定されている場合のコントロールの背景色。

**[FillColor](./controls/properties-color-border.md)** – コントロールの背景色。

**[Font](./controls/properties-text.md)** – テキストを表示するフォントのファミリーの名前。

**[FontStyle](./controls/properties-text.md)** - コンポーネント内のテキストのスタイル: **なし**、**取り消し線**、**下線**、または **イタリック**。

**[FontSize](./controls/properties-text.md)** – コントロールに表示されるテキストのフォント サイズ。

**[FontWeight](./controls/properties-text.md)** – コントロール内のテキストの太さ: **太字**、**中太**、**標準**、または**細字**。

**[Height](./controls/properties-size-location.md)** – コントロールの上端と下端間の距離。

**[HoverBorderColor](./controls/properties-color-border.md)** – ユーザーがコントロールにマウス ポインターを重ねているときのコントロールの境界線の色。

**[HoverColor](./controls/properties-color-border.md)** – ユーザーがコントロールにマウス ポインターを重ねているときのコントロール内のテキストの色。

**[HoverFill](./controls/properties-color-border.md)** – ユーザーがコントロールにマウス ポインターを重ねているときのコントロールの背景色。

**[PaddingBottom](./controls/properties-size-location.md)** – コントロール内のテキストとそのコントロールの下端間の距離。

**[PaddingLeft](./controls/properties-size-location.md)** – コントロール内のテキストとそのコントロールの左端間の距離。

**[PaddingRight](./controls/properties-size-location.md)** – コントロール内のテキストとそのコントロールの右端間の距離。

**[PaddingTop](./controls/properties-size-location.md)** – コントロール内のテキストとそのコントロールの上端間の距離。

**[PressedBorderColor](./controls/properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロールの境界線の色。

**[PressedColor](./controls/properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロール内のテキストの色。

**[PressedFill](./controls/properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロールの背景色。

**[TabIndex](./controls/properties-accessibility.md)** – キーボード ナビゲーションの順序。

**[TextAlignment](./controls/properties-text.md)** - テキストの配置: **中央揃え**、**左揃え**、**右揃え**、または両端揃え。

**[Tooltip](./controls/properties-core.md)** – ユーザーがコントロールにカーソルを置くときに表示される説明テキスト。

**[VerticalAlign](./controls/properties-text.md)** – コントロールの垂直方向の中心に対するコントロール上でのテキストの位置: **中央**、**上部**、または **下部**。

**[Visible](./controls/properties-core.md)** – コントロールが表示されるか非表示になるか。

**[Width](./controls/properties-size-location.md)** – コントロールの左端と右端間の距離。

**[X](./controls/properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離。

**[Y](./controls/properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離。

## <a name="other-mixed-reality-controls"></a>他の Mixed Reality コントロール

- **[3D で表示](mixed-reality-component-view-3d.md)** コンポーネントを使用して 3D コンテンツを表示します。
- **[Mixed Reality で測定](mixed-reality-component-measure-distance.md)** コンポーネントを使用して、距離、面積、体積を測定します。
- **[Mixed Reality で図形表示](mixed-reality-component-view-shape.md)** コンポーネントを使用して、事前定義された 3D 形状を作成して表示します
