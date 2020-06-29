---
title: 'ボタン コントロール: リファレンス | Microsoft Docs'
description: プロパティとサンプルを含む、ボタン コントロールに関する情報
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 10/25/2016
ms.author: chmoncay
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 02d5f59f16b68ce7f140857591b86a5cd8e54cd5
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3306200"
---
# <a name="button-control-in-power-apps"></a>Power Apps でのボタン コントロール
ユーザーがクリックまたはタップしてアプリを操作できるコントロール。

## <a name="description"></a>内容
ユーザーがコントロールをクリックまたはタップするときに 1 つ以上の数式を実行するように、**ボタン** コントロールの **[OnSelect](properties-core.md)** プロパティを構成します。

## <a name="key-properties"></a>主要なプロパティ
**[OnSelect](properties-core.md)** – ユーザーがコントロールをタップまたはクリックする場合のアプリの反応方法。

**[テキスト](properties-core.md)** – コントロールに表示されるテキスト、またはユーザーがコントロールに入力するテキスト。

## <a name="additional-properties"></a>追加のプロパティ
**[配置](properties-text.md)** – コントロールの水平方向の中心に対するテキストの位置。

**AutoDisableOnSelect** – **OnSelect** 動作の実行時にコントロールを自動で無効化します。

**[BorderColor](properties-color-border.md)** – コントロールの境界線の色。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線が**実線**、**破線**、**点線**、または**なし**かどうか。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さ。

**[色](properties-color-border.md)** – コントロールのテキストの色。

**[DisplayMode](properties-core.md)** – コントロールがユーザー入力を許可するか (**編集**)、データのみを表示するか (**表示**)、または無効にするか (**無効**) どうか。

**[DisabledBorderColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロールの境界線の色。

**[DisabledColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロール内のテキストの色。

**[DisabledFill](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロールの背景色。

**[FocusedBorderColor](properties-color-border.md)** – コントロールがフォーカスされているときのコントロールの境界線の色。

**[FocusedBorderThickness](properties-color-border.md)** – コントロールがフォーカスされているときのコントロールの境界線の太さ。

**[塗りつぶし](properties-color-border.md)** – コントロールの背景色。

**[フォント](properties-text.md)** – テキストを表示するフォントのファミリーの名前。

**[FontWeight](properties-text.md)** – コントロール内のテキストの太さ: **太字**、**中太**、**標準**、または**細字**。

**[高さ](properties-size-location.md)** – コントロールの上端と下端間の距離。

**[HoverBorderColor](properties-color-border.md)** – ユーザーがコントロール上にマウス ポインターを重ねているときのコントロールの境界線の色。

**[HoverColor](properties-color-border.md)** – ユーザーがコントロールにマウス ポインターを重ねているときのコントロール内のテキストの色。

**[HoverFill](properties-color-border.md)** – ユーザーがコントロールにマウス ポインターを重ねているときのコントロールの背景色。

**[斜体](properties-text.md)** – コントロール内のテキストを斜体にするかどうか。

**[PaddingBottom](properties-size-location.md)** – コントロール内のテキストとそのコントロールの下端間の距離。

**[PaddingLeft](properties-size-location.md)** – コントロール内のテキストとそのコントロールの左端間の距離。

**[PaddingRight](properties-size-location.md)** – コントロール内のテキストとそのコントロールの右端間の距離。

**[PaddingTop](properties-size-location.md)** – コントロール内のテキストとそのコントロールの上端間の距離。

**押された状態** – コントロールが押されている間は  *true* 、それ以外の場合は *false*。

**[PressedBorderColor](properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロールの境界線の色。

**[PressedColor](properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロール内のテキストの色。

**[PressedFill](properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロールの背景色。

**[RadiusBottomLeft](properties-size-location.md)** – コントロールの左下隅を丸める度合い。

**[RadiusBottomRight](properties-size-location.md)** – コントロールの右下隅を丸める度合い。

**[RadiusTopLeft](properties-size-location.md)** – コントロールの左上隅を丸める度合い。

**[RadiusTopRight](properties-size-location.md)** – コントロールの右上隅を丸める度合い。

**[サイズ](properties-text.md)** – コントロールに表示されるテキストのフォント サイズ。

**[Strikethrough](properties-text.md)** – コントロールに表示されるテキストに取り消し線を付けるかどうか。

**[TabIndex](properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序。

**[ツールヒント](properties-core.md)** – ユーザーがコントロールにカーソルを置くときに表示される説明テキスト。

**[下線](properties-text.md)** – コントロールに表示されるテキストの下に線を引くかどうか。

**[VerticalAlign](properties-text.md)** – コントロールの垂直方向の中心に対するコントロール上でのテキストの位置。

**[表示](properties-core.md)** – コントロールが表示されるか非表示になるか。

**[幅](properties-size-location.md)** – コントロールの左端と右端間の距離。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離。

## <a name="related-functions"></a>関連する関数
**[Navigate( *ScreenName* 、 *ScreenTransitionValue* )](../functions/function-navigate.md)**

## <a name="examples"></a>例
### <a name="add-a-basic-formula-to-a-button"></a>ボタンに基本的な数式を追加する
1. **[テキスト入力](control-text-input.md)** コントロールを追加し、**ソース**という名前を付けます。
   
    [コントロールの追加、名前付け、構成](../add-configure-controls.md) についてはこちらをご覧ください。
2. **ボタン** コントロールを追加し、**[テキスト](properties-core.md)** プロパティを "追加" に設定し、その **[OnSelect](properties-core.md)** プロパティをこの式に設定します:<br>
   **UpdateContext({合計:合計 + 値(Source.Text)})**
   
    **[UpdateContext](../functions/function-updatecontext.md)** 関数または [その他の関数](../formula-reference.md) に関する詳細情報を希望しますか?
3. **[ラベル](control-text-box.md)** コントロールを追加し、**[テキスト](properties-core.md)** プロパティを**合計**に設定してから、**F5** キーを押します。
4. **ソース**から既定のテキストをクリアし、数値を入力してから、**追加**をクリックまたはタップします。
   
    **[ラベル](control-text-box.md)** コントロールには、入力した数値が表示されます。
5. **ソース**から数値をクリアし、別の数値を入力してから、**追加**をクリックまたはタップします。
   
    **[ラベル](control-text-box.md)** コントロールには、入力した 2 つの数値の合計が表示されます。
6. (オプション) 前の手順を何回も繰り返します。
7. Esc キーを押して (または右上隅の閉じるアイコンをクリックまたはタップして)、既定のワークスペースに戻ります。

### <a name="configure-a-button-with-multiple-formulas"></a>複数の数式を使用してボタンを構成する
エントリ間の**テキスト入力**コントロールをクリアする数式を追加します。

1. **ソース**の **[HintText](control-text-input.md)** プロパティを "数字を入力" に設定します。
2. **追加**の **[OnSelect](properties-core.md)** プロパティを次の数式に設定します:
   
    **UpdateContext({合計:合計 + 値(Source.Text)});<br>UpdateContext({ClearInput: ""})**
   
    > [!NOTE]
   > 複数の数式はセミコロン “**;**“ で区切ります。
3. **ソース**の **[既定](properties-core.md)** プロパティを **ClearInput** に設定します。
4. **F5** キーを押してから、複数の数値を一緒に追加してアプリをテストします。

### <a name="add-another-button-to-reset-the-total"></a>合計をリセットする別のボタンを追加する
計算間の合計をクリアする 2 番目のボタンを追加します。

1. 別の**ボタン** コントロールを追加し、**[テキスト](properties-core.md)** プロパティを "クリア" に設定して、**[OnSelect](properties-core.md)** プロパティを次の数式に設定します:
   
    **UpdateContext({Total:0})**
2. **F5** キーを押し、複数の数値を一緒に追加してから、**クリア**をクリックまたはタップして合計をリセットします。

### <a name="change-a-buttons-appearance"></a>ボタンの外観を変更する
#### <a name="change-a-buttons-shape"></a>ボタンの図形を変更する
既定では、Power Apps では、角の丸い四角形の**ボタン** コントロールが作成されます。 **[高さ](properties-size-location.md)**、**[幅](properties-size-location.md)**、**[半径](properties-size-location.md)** の各プロパティを設定することにより、**ボタン** コントロールの図形に基本的な変更を加えることができます。

> [!NOTE]
> [アイコンと図形](control-shapes-icons.md) にはさまざまなデザインが用意されており、**ボタン** コントロールで実行できるのと同じ基本的な機能のいくつかを実行できます。 ただし、**[アイコンと図形](control-shapes-icons.md)** には **[テキスト](properties-core.md)** プロパティはありません。

1. **ボタン** コントロールを追加し、**[高さ](properties-size-location.md)** および **[幅](properties-size-location.md)** プロパティを **300** に設定して、大きな正方形のボタンを作成します。
2. **[RadiusTopLeft](properties-size-location.md)**、**[RadiusTopRight](properties-size-location.md)**、**[RadiusBottomLeft](properties-size-location.md)**、**[RadiusBottomRight](properties-size-location.md)** の各プロパティを変更して、四隅の曲率の量を調整します。 異なるいくつかの図形の例を次に示します。それぞれ 300 x 300 の正方形のボタンを基にしています:
   
   * 4 つすべての **[半径](properties-size-location.md)** の値を **150** に設定して円を作成します。
   * **[RadiusTopLeft](properties-size-location.md)** および **[RadiusBottomRight](properties-size-location.md)** の値を **300** に設定して、葉の形をした**ボタン**を作成します。
   * **[RadiusTopLeft](properties-size-location.md)** および **[RadiusTopRight](properties-size-location.md)** の値を **300** に設定し、**[RadiusBottomLeft](properties-size-location.md)** および **[RadiusBottomRight](properties-size-location.md)** の値を **100** に設定して、タブの形をしたボタンを作成します。

#### <a name="change-a-buttons-color-when-you-hover-over-it"></a>カーソルを置いたときのボタンの色を変更する
既定では、**ボタン** コントロールの塗りつぶしの色は、マウスでカーソルを置くと 20% 暗くなります。 **[HoverFill](properties-color-border.md)** プロパティを変更することで、この動作を調節できます。そのためには **[ColorFade](../functions/function-colors.md)** 関数を使用します。 **[ColorFade](../functions/function-colors.md)** 数式を正の比率に設定すると、ボタンにカーソルを置いたときの色が薄くなります。一方、負の比率に設定すると色が濃くなります。

* 作成したいずれかのボタンの **[HoverFill](properties-color-border.md)** プロパティで **[ColorFade](../functions/function-colors.md)** の比率を変更し、その効果を確認します。

**[HoverFill](properties-color-border.md)** プロパティを、**[ColorFade](../functions/function-colors.md)** 関数の代わりに、**[ColorValue](../functions/function-colors.md)** 関数を含む数式 **ColorValue("Red")** などに設定して**ボタン** コントロールの色を指定することもできます。

> [!NOTE]
> 色の値は、名前か 16 進値のいずれかの CSS 色定義で指定できます。

* 作成したいずれかのボタンで、**[ColorFade](../functions/function-colors.md)** 関数を **[ColorValue](../functions/function-colors.md)** 関数に置き換え、効果を確認します。


## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
### <a name="color-contrast"></a>色のコントラスト
* [標準の色のコントラスト要件](../accessible-apps-color.md) が適用されます。

### <a name="screen-reader-support"></a>スクリーン リーダー サポート
* **[Text](properties-core.md)** を指定する必要があります。

### <a name="keyboard-support"></a>キーボードのサポート
* **[TabIndex](properties-accessibility.md)** を 0 以上にして、キーボード ユーザーがそこに移動できるようにする必要があります。
* フォーカス インジケーターは明確に表示する必要があります。 これを実現するには **[FocusedBorderColor](properties-color-border.md)** および **[FocusedBorderThickness](properties-color-border.md)** を使用します。
 
