---
title: 'ラジオ コントロール: リファレンス | Microsoft Docs'
description: プロパティとサンプルを含む、ラジオ コントロールに関する情報
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 07/06/2018
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 09e8e12a2a6bc94fcc7e3fb2482ff89b058c369f
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3305993"
---
# <a name="radio-control-in-power-apps"></a>Power Apps でのラジオ コントロール

ユーザーが一度に 1 つだけ選択できる、複数のオプションを表示する入力コントロール。

## <a name="description"></a>内容

HTML の標準的な入力コントロールである**ラジオ** コントロールは、いくつかの相互に排他的なオプションでのみ使用するのが最適です。

このコントロールには、水平または垂直レイアウトがあります。

## <a name="key-properties"></a>主要なプロパティ

**[既定](properties-core.md)** – ユーザーが変更する前のコントロールの値。

**[項目](properties-core.md)** – ギャラリー、リスト、グラフなどのコントロールに表示されるデータのソース。

**レイアウト** – オプションが垂直または水平にレイアウトされるかどうか。

**[Value](properties-core.md)** – 入力コントロールの値です。

**選択済** – 選択された項目を表すデータ レコード。

## <a name="all-properties"></a>すべてのプロパティ

**[配置](properties-text.md)** – コントロールの水平方向の中心に対するテキストの位置。

**[BorderColor](properties-color-border.md)** – コントロールの境界線の色。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線が**実線**、**破線**、**点線**、または**なし**かどうか。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さ。

**[色](properties-color-border.md)** – コントロールのテキストの色。

**[DisplayMode](properties-core.md)** – コントロールがユーザー入力を許可するか (**編集**)、データのみを表示するか (**表示**)、または無効にするか (**無効**) どうか。

**[DisabledBorderColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロールの境界線の色。

**[DisabledColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロール内のテキストの色。

**[DisabledFill](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロールの背景色。

**[塗りつぶし](properties-color-border.md)** – コントロールの背景色。

**[FocusedBorderColor](properties-color-border.md)** – コントロールがフォーカスされているときのコントロールの境界線の色。

**[FocusedBorderThickness](properties-color-border.md)** – コントロールがフォーカスされているときのコントロールの境界線の太さ。

**[フォント](properties-text.md)** – テキストを表示するフォントのファミリーの名前。

**[FontWeight](properties-text.md)** – コントロール内のテキストの太さ: **太字**、**中太**、**標準**、または**細字**。

**[高さ](properties-size-location.md)** – コントロールの上端と下端間の距離。

**[HoverColor](properties-color-border.md)** – ユーザーがコントロールにマウス ポインターを重ねているときのコントロール内のテキストの色。

**[HoverFill](properties-color-border.md)** – ユーザーがコントロールにマウス ポインターを重ねているときのコントロールの背景色。

**[斜体](properties-text.md)** – コントロール内のテキストを斜体にするかどうか。

**[LineHeight](properties-text.md)** – たとえば、テキストの行間またはリスト内の項目間などの距離です。

**[OnChange](properties-core.md)** – ユーザーが (たとえば、スライダーを調整するなどして) コントロールの値を変更した場合のアプリの反応を指定します。

**[OnSelect](properties-core.md)** – ユーザーがコントロールをタップまたはクリックする場合のアプリの反応方法。

**[PaddingBottom](properties-size-location.md)** – コントロール内のテキストとそのコントロールの下端間の距離。

**[PaddingLeft](properties-size-location.md)** – コントロール内のテキストとそのコントロールの左端間の距離。

**[PaddingRight](properties-size-location.md)** – コントロール内のテキストとそのコントロールの右端間の距離。

**[PaddingTop](properties-size-location.md)** – コントロール内のテキストとそのコントロールの上端間の距離。

**[PressedColor](properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロール内のテキストの色。

**[PressedFill](properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロールの背景色。

**RadioBackgroundFill** – ラジオボタン コントロールの円の背景色。

**RadioBorderColor** – ラジオボタン コントロールに含まれる各オプションの円の色。

**RadioSelectionFill** – ラジオボタン コントロールで選択されたオプションの円の内側に表示される色。

**RadioSize** – ラジオボタン コントロールの円の直径。

**[Reset](properties-core.md)** – コントロールを既定値に戻すかどうかを指定します。

**SelectedText (非推奨)** – 選択した項目を表す文字列値。

**[サイズ](properties-text.md)** – コントロールに表示されるテキストのフォント サイズ。

**[Strikethrough](properties-text.md)** – コントロールに表示されるテキストに取り消し線を付けるかどうか。

**[TabIndex](properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序。

**[ツールヒント](properties-core.md)** – ユーザーがコントロールにカーソルを置くときに表示される説明テキスト。

**[下線](properties-text.md)** – コントロールに表示されるテキストの下に線を引くかどうか。

**[表示](properties-core.md)** – コントロールが表示されるか非表示になるか。

**[幅](properties-size-location.md)** – コントロールの左端と右端間の距離。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離。

## <a name="related-functions"></a>関連する関数

[**Distinct**( *DataSource*, *ColumnName* )](../functions/function-distinct.md)

## <a name="example"></a>例

1. **ラジオ** コントロールを追加して**価格設定**という名前を付け、**[項目](properties-core.md)** プロパティを次の数式に設定します:

    **["標準", "プレミアム"]**

    [コントロールの追加、名前付け、構成](../add-configure-controls.md) についてはこちらをご覧ください。

2. **[ラベル](control-text-box.md)** コントロールを追加し、**ラジオ** コントロールの下に移動させ、**[ラベル](control-text-box.md)** コントロールの **[テキスト](properties-core.md)** プロパティを次の数式に設定します:

    **If("プレミアム" in Pricing.Selected.Value, "$200/日", "$150/日")**

    **[If](../functions/function-if.md)** 関数または [その他の関数](../formula-reference.md) の詳細については各関連記事を参照してください。

3. Alt キーを押したまま、**ラジオ** コントロールのいずれかのオプションを選択します。

    **[ラベル](control-text-box.md)** コントロールでは、選択内容に合ったテキストが表示されます。

4. (オプション) Alt キーを押しながら他のオプションを選択して、適切なテキストが表示されることを確認します。

## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン

### <a name="color-contrast"></a>色のコントラスト

[標準の色のコントラスト要件](../accessible-apps-color.md) に加えて、次の間で色のコントラストが適切になるようにします:

* **RadioSelectionFill** と **RadioBackgroundFill**
* **RadioBackgroundFill** と **[塗りつぶし](properties-color-border.md)**

### <a name="screen-reader-support"></a>スクリーン リーダーのサポート

* すべてのオプションに **[値](properties-core.md)** があることを確認します。
* **ラジオ** コントロールの直前に **[ラベル](control-text-box.md)** を追加して、見出しとして提供することを検討してください。

### <a name="keyboard-support"></a>キーボードのサポート

* キーボード ユーザーが移動できるように、**[TabIndex](properties-accessibility.md)** プロパティを 0 以上に設定します。
* フォーカス インジケーターがはっきり見えるように、**[FocusedBorderColor](properties-color-border.md)** および **[FocusedBorderThickness](properties-color-border.md)** プロパティを設定します。
