---
title: Power Apps で MR の図形表示コンポーネントを使用する (プレビュー)
description: Power Apps で拡張現実機能を使用して、現実世界での事前定義されたデジタル 3D 図形を表示します。
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
ms.openlocfilehash: 8497663a4ebebd744e44ce9b89c819c2c34d56a0
ms.sourcegitcommit: 5e195cb09ab43d31c854efdc4e7e8dc9f1955ca4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "3418697"
---
# <a name="create-and-view-predefined-3d-shapes-in-mixed-reality-preview"></a>Mixed Reality で事前定義された 3D 図形を作成および表示する (プレビュー)

[!INCLUDE [cc-beta-prerelease-disclaimer.md](../../includes/cc-beta-prerelease-disclaimer.md)]

アプリの **MR の図形表示** コンポーネントを使用して、シンプルな立方体が指定されたスペースに収まるかをユーザーが確認できるようにします。 ユーザーは、提供される特定のオブジェクトがどのようにスペースに収まるかを確認するために、これを実行する可能性があります。 オブジェクトの 3D モデルがある場合は、代わりに [**MR で表示**コンポーネント](mixed-reality-component-view-mr.md) を使用できます。

コンポーネントは、アプリにボタンを作成します。 アプリのユーザーがボタンをクリックすると、キューブがデバイスのライブ カメラ フィードにオーバーレイされます。 Power Apps でコンポーネントを編集するとき、キューブのディメンションを設定します。

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vvwR]

コンポーネントを使用するには、使用する [各アプリの Mixed Reality (MR) 機能を有効にする](mixed-reality-overview.md#enable-the-mixed-reality-features-for-each-app) 必要があります。

[MR コンポーネントを使用するための前提条件の確認](mixed-reality-overview.md#prerequisites) も必ず実行してください。

> [!TIP]
> MR コンポーネントは、フラット テクスチャ サーフェスの明るい環境で最適に動作します。 追跡を確立するときは、追跡するサーフェスにデバイスを向け、広い腕の動きでデバイスを右から左にゆっくりとパンします。 追跡に失敗した場合は、終了して MR ビューを入力し、追跡をリセットして再試行してください。

## <a name="use-the-component"></a>コンポーネントを使用する

他の任意のボタン コントロールまたはコンポーネントの場合と同じように、コンポーネントをアプリに挿入します。

[Power Apps Studio](https://create.powerapps.com) で編集用にアプリを開いて:

1. **挿入**タブを開きます。
2. **Mixed reality** を展開します。
3. コンポーネントの **MR の図形表示**を選択して、アプリ スクリーンの中央に配置するか、またはスクリーンの任意の場所にドラッグおよびドロップします。

   ![MR の図形表示を選択](./media/augmented-view-shape/augmented-view-shape.png "MR の図形表示を選択")

いくつかのプロパティを使用してコンポーネントを変更できます。

### <a name="properties"></a>プロパティ​​

次のプロパティは、**プロパティ**と**詳細**タブのコンポーネントの **MR の図形表示**ウィンドウにあります。

![MR ペインのコンポーネントの図形表示のプロパティ](./media/augmented-view-shape/augmented-view-shape-properties.png "MR ペインのコンポーネントの図形表示のプロパティ")

一部のプロパティは、**MR の図形表示**ウィンドウの**詳細**タブでのみ使用できることに注意してください。

プロパティ | 内容 | 種類​​ | Location
- | - | - | -
テキスト | ボタンのラベル。 | 文字列 | プロパティ (**詳細**にもあります)
表示の種類 | ボタンにアイコン、テキスト、またはその両方が表示されるかどうか。 | ドロップダウン セレクション | プロパティ (**詳細**にもあります)
形状の幅 | キューブの幅。 | Integer | **プロパティ** (**詳細**にもあります)
形状の高さ | キューブの高さ。 | Integer | **プロパティ** (**詳細**にもあります)
図形の深さ | キューブの 3 次元の深さ。 | Integer | **プロパティ** (**詳細**にもあります)
測定単位 | 幅、高さ、深さフィールドに使用される測定単位。 | ドロップダウン セレクション | **プロパティ** (**詳細**にもあります)
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
- **[Mixed Reality で表示](mixed-reality-component-view-mr.md)** コンポーネントを使用して、現実世界の画像と 3D コンテンツを表示します。
- **[Mixed Reality で測定](mixed-reality-component-measure-distance.md)** コンポーネントを使用して、距離、面積、体積を測定します。
