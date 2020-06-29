---
title: '画面コントロール: リファレンス | Microsoft Docs'
description: プロパティとサンプルを含む、画面コントロールに関する情報
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 09/14/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ac06720b1d7037cab540c91ab8a42f6c269b0edb
ms.sourcegitcommit: 6acc6ac7cc1749e9681d5e55c96613033835d294
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "3309075"
---
# <a name="screen-control-in-power-apps"></a>Power Apps での画面コントロール

アプリ内で 1 つまたは複数の他のコントロールを含む UI 要素。

## <a name="description"></a>内容

ほとんどのアプリには、**[ラベル](control-text-box.md)** コントロール、**[ボタン](control-button.md)** コントロール、およびデータを表示したりナビゲーションをサポートするその他のコントロールを含む複数の**画面**コントロールがあります。 画面の追加、画面の並べ替え、ナビゲーションの構成方法についての詳細は、[画面の追加](../add-screen-context-variables.md) を確認してください。

## <a name="key-properties"></a>主要なプロパティ

**[BackgroundImage](properties-visual.md)** – 画面の背景に表示される画像ファイルの名前。

**[塗りつぶし](properties-color-border.md)** – コントロールの背景色。

## <a name="additional-properties"></a>追加のプロパティ

**高さ** - 画面の高さ。 アプリに応答性 ([**全体表示**](../set-aspect-ratio-portrait-landscape.md#change-screen-size-and-orientation) が**オフ**である) があり、アプリが実行しているデバイスがこのプロパティより短い場合、画面を垂直方向にスクロールできます。

**[ImagePosition](properties-visual.md)** – 画面またはコントロールのサイズが画像と異なる場合の、画面またはコントロール内の画像の位置 (**画面いっぱい**、**自動調整**、**拡大**、**タイル表示**、または**中央に表示**)。

**LoadingSpinner** (**なし**、**コントロール**または**データ**) - なしの場合、スピナーは表示されません。 コントロール時 | データは、画面レベルのすべての子コントロールが表示されるまでスピナーを示します。 **注意。入れ子になったコントロールは考慮されません。**

**LoadingSpinnerColor** - スピナーを読み込む塗りつぶしの色。

**名前** - 画面の名前。

**OnHidden** – ユーザーが画面から移動するときのアプリの動作。

**OnVisible** – ユーザーが画面に移動するときのアプリの動作。  このプロパティを使用して、画面で使用される変数とプリロード データを設定します。  [**App.OnStart**](../functions/object-app.md#onstart-property) プロパティを使用して、アプリ起動時に一度設定します。

**向き** - 画面の向き。 **幅**が**高さ**より大きい場合、向きは **Layout.Horizontal** になります; それ以外の場合は、**Layout.Vertical** になります。

**サイズ** - 画面のサイズを分類する正の整数。 分類は、画面の**幅**プロパティを [**App.SizeBreakpoints**](../functions/signals.md) プロパティの値と比較することによって決まります。 **ScreenSize** タイプは、整数 1 〜 4 に対応する 4 つの値 (**小**、**中**、**大**、および**特大**) から構成されます。

**幅** - 画面の幅。 アプリに応答性 ([**全体表示**](../set-aspect-ratio-portrait-landscape.md#change-screen-size-and-orientation) が**オフ**である) があり、アプリが実行しているデバイスがこのプロパティより狭い場合、画面を水平方向にスクロールできます。

## <a name="related-functions"></a>関連する関数

[**Distinct**( *DataSource*, *ColumnName* )](../functions/function-distinct.md)

## <a name="example"></a>例

1. **[ラジオ](control-radio.md)** コントロールを追加し、**ScreenFills** という名前を付け、**[項目](properties-core.md)** プロパティを次の値に設定します:

    `["Red", "Green"]`

    [コントロールの追加、名前付け、構成](../add-configure-controls.md) についてはこちらをご覧ください。

1. 既定の**画面**コントロールに**ソース**という名前を付け、別の**画面**コントロールを追加して、**対象**という名前を付けます。

1. **ソース**に、**[図形](control-shapes-icons.md)** コントロール (矢印など) を追加し、その **[OnSelect](properties-core.md)** プロパティを次の数式に設定します:

    `Navigate(Target, ScreenTransition.Fade)`

    **[移動](../functions/function-navigate.md)** 関数または [その他の関数](../formula-reference.md) については各関連記事を参照してください。

1. **対象**に、**[図形](control-shapes-icons.md)** コントロール (矢印など) を追加し、その **[OnSelect](properties-core.md)** プロパティを次の数式に設定します:

    `Navigate(Source, ScreenTransition.Fade)`

1. **対象**の **[塗りつぶし](properties-color-border.md)** プロパティを次の数式に設定します:

    `If("Red" in ScreenFills.Selected.Value, RGBA(255, 0, 0, 1), RGBA(54, 176, 75, 1))`

1. **ソース**画面を選択してから、Alt キーを押しながら、**[ラジオ](control-radio.md)** コントロールのいずれかのオプションを選択し、次に **[図形](control-shapes-icons.md)** コントロールを選択します。

    **対象**が、選択した色で表示されます。

1. **対象**で、**[図形](control-shapes-icons.md)** コントロールを選択して、**ソース**に戻ります。

1. (オプション) **[ラジオ](control-radio.md)** コントロールの他のオプションを選択してから、**[図形](control-shapes-icons.md)** コントロールを選択して**対象**が他の色で表示されることを確認します。

1. (オプション) 左側のナビゲーション バーの**対象**にカーソルを合わせて画面を並べ替え、表示される省略記号を選択してから、**上へ移動**を選択します。

    ユーザーがアプリを開くときに、**対象**が最初に表示されます。

## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン

### <a name="color-contrast"></a>色のコントラスト

**画面**がテキストの実質的な背景である場合、次の間には適切な色のコントラストが必要です:

- **[塗りつぶし](properties-color-border.md)** とテキスト
- **[BackgroundImage](properties-visual.md)** とテキスト (該当する場合)

たとえば、**画面**に **[ラベル](control-text-box.md)** が含まれ、ラベルの塗りつぶしが透明な場合、画面の **[塗りつぶし](properties-color-border.md)** は実質的にはラベルの背景色になります。

テキストに加えて、**[評価](control-rating.md)** コントロールの星画像のような重要なグラフィック オブジェクトとの色のコントラストを確認することを検討してください。

### <a name="screen-reader-support"></a>スクリーン リーダー サポート

- 各**画面**にはわかりやすい名前を付ける必要があります。 画面名は、他のコントロールと同様に、コントロール ウィンドウのツリー ビューまたはプロパティ ウィンドウのヘッダーで表示および編集できます。

    > [!NOTE]
  > 新しい**画面**が読み込まれると、スクリーン リーダーでその名前が通知されます。
