---
title: Power Apps で MR コンポーネントのメジャーを使用 (プレビュー)
description: Power Apps の拡張現実機能で、距離をデジタルで測定し、現実世界のエリアと形状を作成します。
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
ms.openlocfilehash: b640d20546dfd599d7f6834997021b5b661539f9
ms.sourcegitcommit: eda1684352baa7cb0f95119362177f3934a7bd4d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/28/2020
ms.locfileid: "3409861"
---
# <a name="take-measurements-in-mixed-reality-preview"></a>Mixed Reality で測定を行う (プレビュー)

[!INCLUDE [cc-beta-prerelease-disclaimer.md](../../includes/cc-beta-prerelease-disclaimer.md)]

使用しているアプリの **MR でメジャー**コンポーネントを使用して、ユーザーが距離、面積、体積を測定できるようにします。 測定時には、特定サイズのオブジェクトがスペース内にどのように収まるかを確認するために、使用可能な 2 次元および 3 次元のポリゴンを作成します。

コンポーネントは、アプリにボタンを作成します。 アプリのユーザーがボタンをクリックすると、デバイスのライブ カメラ フィードが表示されます。 アプリのユーザーは、開始点を特定してから、測定する個々の点を特定できます。 測定されたセグメントの距離は、ライブ カメラ フィードに直接表示されます。

アプリ内で、コンポーネントがどのように機能するかの例を次のビデオに表示します:


> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vyoW]


ユーザーがコンポーネントを終了すると、取得された測定値が **Measurements** および **MeasurementsDetailed** プロパティを保管または保存できるようにします。

Mixed Reality のエクスペリエンス中に撮影されたスクリーンショットは、アプリ内で表示するための **Photos** プロパティに保存されます。

コンポーネントを使用するには、使用する [各アプリの Mixed Reality 機能を有効にする](mixed-reality-overview.md#enable-the-mixed-reality-features-for-each-app) 必要があります。

また、[Mixed Reality コンポーネントを使用するための前提条件も確認してください](mixed-reality-overview.md#prerequisites)。

> [!TIP]
> Mixed Reality コンポーネントは、フラット テクスチャ サーフェスの明るい環境で最適に動作します。 追跡を確立するときは、追跡するサーフェスにデバイスを向け、広い腕の動きでデバイスを右から左にゆっくりとパンします。 追跡が失敗した場合は、終了して Mixed Reality ビューに移動し、追跡をリセットして再試行してください。

## <a name="use-the-component"></a>コンポーネントを使用する

他のボタン コンポーネントの場合と同じように、コンポーネントをアプリに挿入します。

[Power Apps Studio](https://create.powerapps.com) で編集用にアプリを開いて:

1. **挿入**タブを開きます。
2. **Mixed reality** を展開します。
3. コンポーネント **MR でメジャー**を選択して、アプリ スクリーンの中央に配置するか、またはスクリーンの任意の場所にドラッグおよびドロップします。

   > [!div class="mx-imgBorder"]
   > ![MR でメジャーを選択](./media/augmented-measure/augmented-measure.png "MR でメジャーを選択")

いくつかのプロパティを使用してコンポーネントを変更できます。

> [!NOTE]
> 3D コンテンツは .glb ファイル形式である必要があります。 さまざまな 3D 形式から [既存の 3D モデルを .glb ファイル形式に変換](/dynamics365/mixed-reality/import-tool/) できます。


### <a name="properties"></a>プロパティ​​

次のプロパティは、**プロパティ**と**詳細**タブのコンポーネントの **MR でメジャー**ウィンドウにあります。

> [!div class="mx-imgBorder"]
> ![MR でメジャー ペイン](./media/augmented-measure/augmented-measure-properties.png "MR でメジャー ペイン")

一部のプロパティは、**MR でメジャー**ウィンドウの**詳細**タブの**より多くのオプション**でのみ使用できることに注意してください。

プロパティ | 内容 | 種類​​ | 場所
- | - | - | -
テキスト | ボタンのラベル | 文字列 | **プロパティ** (**詳細**にもあります)
表示の種類 | ボタンにアイコン、テキスト、またはその両方が表示されるかどうか | ドロップダウン セレクション | **プロパティ** (**詳細**にもあります)
測定単位 | どの測定値を表示して返すべきか | ドロップダウン セレクション | **プロパティ** (**詳細**にもあります)
測定の種類 | ユーザーが作成できる測定のタイプ、点から点の距離、完全な領域、または 3 次元値 (領域と高さまたは深さ) のいずれか。 | ドロップダウン セレクション | **プロパティ** (**詳細**にもあります)
測定 | 以下で構成される、測定されたセグメントを含むテーブル: <ul><li>長さ - セグメントの長さを表す数値</li><li>単位 - この測定の単位を表示する文字列</li></ul> | 文字列 | 該当なし (出力プロパティのみ)
MeasurementsDetailed | 以下から構成される、測定された体積と面積を表示するテーブル:<ul><li>単位 - この測定の基本単位を表示する文字列</li><li>高さ - キャプチャされた体積の高さを表す数値、または完成した体積または 2D 領域でない場合は 0</li><li>PathLength - パスの合計の長さを表す数値</li><li>セグメント - 次のプロパティで指定された測定オブジェクトのすべてのセグメントを表示するテーブル:<ul><li>距離 - 指定された測定単位の特定セグメントの合計距離を表す数値 (たとえば、.52)</li><li>方向 - 正規化されたセグメントの方向を説明するベクトル</li><li>X - ワールド スペースでセグメントの X 方向を指定する数値 (たとえば、0.5)</li><li>Y - ワールド スペースで測定の Y 方向を指定する数値 (通常 0)</li><li>Z - ワールド スペースで測定の Z 方向を指定する数値 (たとえば、0.5)</li></ul></li></li> | | 該当なし (出力プロパティのみ)
写真 | Mixed Reality セッション中にキャプチャされた写真 | | 該当なし (出力プロパティのみ)

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

**[FontWeight](./controls/properties-text.md)** – コントロール内のテキストの太さ: **太字**、**中太字**、**標準**、または **細字**

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

**[TextAlignment](./controls/properties-text.md)** - テキストの配置: **中央揃え**、**左揃え**、**右揃え**、または **両端揃え**

**[Tooltip](./controls/properties-core.md)** – ユーザーがコントロールにカーソルを置くときに表示される説明テキスト。

**[VerticalAlign](./controls/properties-text.md)** – コントロールの垂直方向の中心に対するコントロール上でのテキストの位置: **中央**、**上部**、または**下部**

**[Visible](./controls/properties-core.md)** – コントロールが表示されるか非表示になるか。

**[Width](./controls/properties-size-location.md)** – コントロールの左端と右端間の距離。

**[X](./controls/properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離。

**[Y](./controls/properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離。

## <a name="other-mixed-reality-components"></a>他の Mixed Reality コンポーネント

- **[3D で表示](mixed-reality-component-view-3d.md)** コンポーネントを使用して 3D コンテンツを表示します。
- **[Mixed Reality で表示](mixed-reality-component-view-mr.md)** コンポーネントを使用して、現実世界の画像と 3D コンテンツを表示します。
- **[Mixed Reality で図形表示](mixed-reality-component-view-shape.md)** コンポーネントを使用して、事前定義された 3D 形状を作成して表示します
