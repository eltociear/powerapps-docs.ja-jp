---
title: '図形コントロールとアイコン コントロール: リファレンス | Microsoft Docs'
description: プロパティとサンプルを含む、図形コントロールとアイコン コントロールに関する情報
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/25/2016
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f46199d0265cf042ebae5dd27ae308fad7eca8e6
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3305924"
---
# <a name="shape-controls-and-icon-controls-in-power-apps"></a>Power Apps での図形コントロールとアイコン コントロール
外観と動作のプロパティを構成できるグラフィック。

## <a name="description"></a>内容
これらのコントロールには矢印、幾何学的図形、アクション アイコン、記号が含まれており、塗りつぶし、サイズ、位置などのプロパティを構成できます。 また、**[OnSelect](properties-core.md)** プロパティを構成すると、ユーザーがコントロールを選択した場合にアプリが反応するようにできます。

## <a name="key-properties-icons-and-shapes"></a>主要なプロパティ (アイコンと図形)
**[塗りつぶし](properties-color-border.md)** – コントロールの背景色。

**[OnSelect](properties-core.md)** – ユーザーがコントロールを選択する場合のアプリの反応方法。

## <a name="key-properties-icons-only"></a>主要なプロパティ (アイコンのみ)

**アイコン** - 表示するアイコンのタイプ (たとえば、**ArrowDown** または **ShoppingCart**)。 

**回転** - アイコンを回転させる度数。 

**色** - 名前または RGBA 値によるアイコンの色。

## <a name="additional-properties"></a>追加のプロパティ
**[AccessibleLabel](properties-accessibility.md)** – スクリーン リーダー用のラベル。

**[DisplayMode](properties-core.md)** – コントロールがユーザー入力を許可するか (**編集**)、データのみを表示するか (**表示**)、または無効にするか (**無効**) どうか。

**[FocusedBorderColor](properties-color-border.md)** – コントロールがフォーカスされているときのコントロールの境界線の色。

**[FocusedBorderThickness](properties-color-border.md)** – コントロールがフォーカスされているときのコントロールの境界線の太さ。

**[高さ](properties-size-location.md)** – コントロールの上端と下端間の距離。

**[HoverFill](properties-color-border.md)** – ユーザーがコントロールにマウス ポインターを重ねているときのコントロールの背景色。

**[PressedBorderColor](properties-color-border.md)** – ユーザーがコントロールを選択するときのコントロールの境界線の色。

**[PressedFill](properties-color-border.md)** – ユーザーがコントロールを選択するときのコントロールの背景色。

**[TabIndex](properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序。

**[表示](properties-core.md)** – コントロールが表示されるか非表示になるか。

**[幅](properties-size-location.md)** – コントロールの左端と右端間の距離。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離。

## <a name="related-functions"></a>関連する関数

[**Navigate**( *ScreenName*, *ScreenTransition* )](../functions/function-navigate.md)

## <a name="example"></a>例

1. 既定の **[画面](control-screen.md)** コントロールに**対象**という名前を付け、**[ラベル](control-text-box.md)** コントロールを追加し、**対象**を表示するように **[テキスト](properties-core.md)** プロパティを設定します。

    [コントロールの追加および構成](../add-configure-controls.md) についてはこちらをご覧ください。

1. **[画面](control-screen.md)** コントロールを追加し、**ソース**という名前を付けます。

1. **ソース**に **図形**コントロールを追加し、**[OnSelect](properties-core.md)** プロパティに次の数式を設定します:

  `Navigate(Target, ScreenTransition.Fade)`
  
1. F5 キーを押してから、**図形**コントロールを選択します。

    **対象**画面が表示されます。

1. (オプション) Esc キーを押して既定のワークスペースに戻り、**対象**に**図形**コントロールを追加し、**図形**コントロールの **[OnSelect](properties-core.md)** プロパティに次の数式を設定します:

  `Navigate(Source, ScreenTransition.Fade)`

## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン

### <a name="color-contrast"></a>色のコントラスト

以下は、ボタンとして使用されるグラフィックに、または単なる装飾用ではないグラフィックにのみ適用されます。

アイコン用:
- **[Color](properties-color-border.md)** と **[Fill](properties-color-border.md)**
- その他の [標準色のコントラスト要件](../accessible-apps-color.md) が適用されます (ボタンとして使用される場合)

境界線のある図形の場合:
- **[BorderColor](properties-color-border.md)** とコントロールの外側の色
- **[FocusedBorderColor](properties-color-border.md)** とコントロールの外側の色 (ボタンとして使用される場合)

境界線のない図形の場合:
- **[塗りつぶし](properties-color-border.md)** とコントロールの外側の色
- **[PressedFill](properties-color-border.md)** とコントロールの外側の色 (ボタンとして使用される場合)
- **[HoverFill](properties-color-border.md)** とコントロールの外側の色 (ボタンとして使用される場合)

### <a name="screen-reader-support"></a>スクリーン リーダーのサポート
- グラフィックがボタンとして使用されるか、または単なる装飾用ではない場合は、**[AccessibleLabel](properties-accessibility.md)** が空でない文字列として設定される必要があります。

- グラフィックが不要な情報を提供する、または純粋に装飾用である場合は、**[AccessibleLabel](properties-accessibility.md)** を空または空の文字列 **""** にする必要があります。 この値により、スクリーン リーダーでグラフィックが無視されます。

たとえば、**設定**アイコンの **[AccessibleLabel](properties-accessibility.md)** プロパティを**設定**に設定する場合があります。 このアイコンは、ボタンとしては使用されません。 **[ラベル](control-text-box.md)** の横にあり、**設定**であることを示しています。 スクリーン リーダーは、アイコンとラベルの両方を**設定**として読み込み、これは不必要に冗長なものです。 この場合、アイコンに **[AccessibleLabel](properties-accessibility.md)** は必要ありません。

> [!IMPORTANT]
> **[AccessibleLabel](properties-accessibility.md)** が空の文字列に設定され、その **[ TabIndex](properties-accessibility.md)** が 0 以上の場合、スクリーン リーダーはアイコンや図形を**ボタン**として読み込みます。 このようなアイコンや図形はボタンとしてレンダリングされます。 

### <a name="keyboard-support"></a>キーボードのサポート
- グラフィックをボタンとして使用する場合は、**[TabIndex](properties-accessibility.md)** を 0 以上にする必要があります。 この値をアイコンまたは図形に設定すると、キーボード ユーザーはそこに移動できます。

- グラフィックをボタンとして使用する場合は、明確に判別できるフォーカス インジケーターが必要です。 この結果を実現するには **[FocusedBorderColor](properties-color-border.md)** および **[FocusedBorderThickness](properties-color-border.md)** を使用します。

    > [!NOTE]
    > **[TabIndex](properties-accessibility.md)** が 0 以上の場合、アイコンまたは図形はボタンとしてレンダリングされます。 外観に変更はありませんが、スクリーン リーダーは画像をボタンとして正しく識別します。 **[TabIndex](properties-accessibility.md)** が 0 未満の場合、アイコンまたは図形は画像として識別されます。
