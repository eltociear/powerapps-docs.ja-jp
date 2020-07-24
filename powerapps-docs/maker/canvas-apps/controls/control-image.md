---
title: '画像コントロール: リファレンス | Microsoft Docs'
description: プロパティとサンプルを含む、画像コントロールに関する情報
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
ms.openlocfilehash: 0610e1cfabde8bd62e083ca1cff65825c28918e4
ms.sourcegitcommit: c0508e233a03ac4846c04d5caae79eccca3e2843
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/15/2020
ms.locfileid: "3309282"
---
# <a name="image-control-in-power-apps"></a>Power Apps での画像コントロール
たとえば、ローカル ファイルまたはデータ ソースからの画像を表示するコントロール。

## <a name="description"></a>内容
アプリに**画像**コントロールを 1 つまたは複数追加すると、データ セットに含まれていない個々の画像を表示したり、データ ソースのレコードからの画像を組み込むことができます。

## <a name="key-properties"></a>主要なプロパティ
**[画像](properties-visual.md)** – 画像、オーディオ、マイクのコントロールに表示される画像の名前。

## <a name="additional-properties"></a>追加のプロパティ
**[AccessibleLabel](properties-accessibility.md)** – スクリーン リーダー用のラベル。

**ApplyEXIFOrientation** – 画像とともに埋め込まれた EXIF のデータで指定された向きを、自動的に適用するかどうか。

**AutoDisableOnSelect** – OnSelect の動作の実行時にコントロールを自動で無効化するかどうかを指定します。

**[BorderColor](properties-color-border.md)** – コントロールの境界線の色。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線が**実線**、**破線**、**点線**、または**なし**かどうか。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さ。

**CalculateOriginalDimensions** – **OriginalHeight** および **OriginalWidth** プロパティを有効にします。

**[DisplayMode](properties-core.md)** – コントロールがユーザー入力を許可するか (**編集**)、データのみを表示するか (**表示**)、または無効にするか (**無効**) どうか。

**[DisabledBorderColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロールの境界線の色。

**[DisabledFill](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロールの背景色。

**[塗りつぶし](properties-color-border.md)** – コントロールの背景色。

**FlipHorizontal** – 画像を表示する前に水平方向に反転するかどうか。

**FlipVertical** – 画像を表示する前に垂直方向に反転するかどうか。

**[FocusedBorderColor](properties-color-border.md)** – コントロールがフォーカスされているときのコントロールの境界線の色。

**[FocusedBorderThickness](properties-color-border.md)** – コントロールがフォーカスされているときのコントロールの境界線の太さ。

**[高さ](properties-size-location.md)** – コントロールの上端と下端間の距離。

**[HoverBorderColor](properties-color-border.md)** – ユーザーがコントロール上にマウス ポインターを重ねているときのコントロールの境界線の色。

**[HoverFill](properties-color-border.md)** – ユーザーがコントロールにマウス ポインターを重ねているときのコントロールの背景色。

**[ImagePosition](properties-visual.md)** – 画面またはコントロールのサイズが画像と異なる場合の、画面またはコントロール内の画像の位置 (**画面いっぱい**、**自動調整**、**拡大**、**タイル表示**、または**中央に表示**)。

**ImageRotation** – 画像を表示する前に回転させる方法。  値には、なし、時計回り (CW) に 90 度、反時計回り (CCW) に 90 度、時計回りに 180 度を設定できます。

**[OnSelect](properties-core.md)** – ユーザーがコントロールをタップまたはクリックする場合のアプリの反応方法。

**OriginalHeight** – 画像の元の高さで、**CalculateOriginalDimensions** プロパティで有効にします。

**OriginalWidth** – 画像の元の幅で、**CalculateOriginalDimensions** プロパティで有効にします。

**[PaddingBottom](properties-size-location.md)** – コントロール内のテキストとそのコントロールの下端間の距離。

**[PaddingLeft](properties-size-location.md)** – コントロール内のテキストとそのコントロールの左端間の距離。

**[PaddingRight](properties-size-location.md)** – コントロール内のテキストとそのコントロールの右端間の距離。

**[PaddingTop](properties-size-location.md)** – コントロール内のテキストとそのコントロールの上端間の距離。

**[PressedBorderColor](properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロールの境界線の色。

**[PressedFill](properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロールの背景色。

**[RadiusBottomLeft](properties-size-location.md)** – コントロールの左下隅を丸める度合い。

**[RadiusBottomRight](properties-size-location.md)** – コントロールの右下隅を丸める度合い。

**[RadiusTopLeft](properties-size-location.md)** – コントロールの左上隅を丸める度合い。

**[RadiusTopRight](properties-size-location.md)** – コントロールの右上隅を丸める度合い。

**[TabIndex](properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序。

**[ツールヒント](properties-core.md)** – ユーザーがコントロールにカーソルを置くときに表示される説明テキスト。

**透明性** – 画像の背後にあるコントロールを表示し続ける度合い。 10 進値の範囲は 0〜1 です。  0 は不透明、0.5 は半透明、1 は透明です。 

**[表示](properties-core.md)** – コントロールが表示されるか非表示になるか。

**[幅](properties-size-location.md)** – コントロールの左端と右端間の距離。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離。

## <a name="related-functions"></a>関連する関数
[**Remove**( *DataSource*, ThisItem )](../functions/function-remove-removeif.md)

## <a name="examples"></a>例
### <a name="show-an-image-from-a-local-file"></a>ローカル ファイルからの画像を表示する
1. **ファイル** メニューで、**メディア**をクリックまたはタップしてから、**参照**をクリックまたはタップします。
2. 追加する画像ファイルをクリックまたはタップし、**開く**をクリックまたはタップしてから、Esc キーを押して既定のワークスペースに戻ります。
3. **画像**コントロールを追加し、**画像**プロパティを追加したファイルの名前に設定します。

    [コントロールの追加および構成](../add-configure-controls.md) についてはこちらをご覧ください。

    指定した画像が**画像**コントロールに表示されます。

### <a name="show-a-set-of-images-from-a-data-source"></a>データ ソースからの一連の画像を表示する
1. この [Excel ファイル](https://pwrappssamples.blob.core.windows.net/samples/FlooringEstimates.xlsx) をダウンロードして、ローカル デバイスに保存します。
2. Power Apps Studio で、アプリを作成するか開いてから、右側のウィンドウで**データ ソースの追加**をクリックまたはタップします。

    右側のウィンドウに**データ ソースの追加**が表示されない場合、左側のナビゲーション バーの画面をクリックまたはタップします。
3. **静的データをアプリに追加**をクリックまたはタップして、ダウンロードした Excel ファイルをクリックまたはタップしてから、**開く**をクリックまたはタップします。
4. **床材の見積もり**チェック ボックスをオンにしてから、**接続**をクリックまたはタップします。
5. **ギャラリー** コントロールを画像に追加し、**[項目](properties-core.md)** プロパティを **FlooringEstimates** に設定します。

    [コントロールの追加および構成](../add-configure-controls.md) についてはこちらをご覧ください。

    **ギャラリー** コントロールには、ダウンロードした Excel ファイルのリンクに基づくカーペット、硬木、およびタイル製品の画像が表示されます。


## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
### <a name="color-contrast"></a>色のコントラスト
* グラフィックがボタンとして使用される場合、[標準色のコントラスト要件](../accessible-apps-color.md) が適用されます。
* 純粋な装飾でない画像の場合、画像内のコントラストの問題を確認することを検討してください。

### <a name="screen-reader-support"></a>スクリーン リーダー サポート
* グラフィックがボタンとして使用されるか、または単なる装飾用ではない場合は、**[AccessibleLabel](properties-accessibility.md)** が存在する必要があります。
* グラフィックが純粋に装飾用である場合は、**[AccessibleLabel](properties-accessibility.md)** を空または空の文字列 **""** にする必要があります。 これにより、スクリーン リーダーでグラフィックが無視されます。
* グラフィックが不要な情報を提供する場合は、**[AccessibleLabel](properties-accessibility.md)** を空または空の文字列 **""** にすることができます。
  * たとえば、**[AccessibleLabel](properties-accessibility.md)** が**設定**に設定された歯車の**画像**があるとします。 このイメージは、ボタンとしては使用されません。 **[ラベル](control-text-box.md)** の横にあり、**設定**であることを示しています。 スクリーン リーダーは、画像を**設定**として読み取り、ラベルをもう一度**設定**として読み取ります。 これは不必要に冗長なものです。 この場合、**画像**に **[AccessibleLabel](properties-accessibility.md)** は必要ありません。

    > [!IMPORTANT]
    > スクリーン リーダーは、**[AccessibleLabel](properties-accessibility.md)** が空の場合でも、**[TabIndex](properties-accessibility.md)** が 0 以上の**画像**を常に読み取ります。 これはボタンとしてレンダリングされるためです。 **[AccessibleLabel](properties-accessibility.md)** が指定されていない場合、スクリーン リーダーは単純にグラフィックを**ボタン**として読み取ります。

### <a name="keyboard-support"></a>キーボードのサポート
* グラフィックをボタンとして使用する場合は、**[TabIndex](properties-accessibility.md)** を 0 以上にする必要があります。 こうすることで、キーボード ユーザーがそこに移動できるようになります。
* グラフィックをボタンとして使用する場合は、明確に判別できるフォーカス インジケーターが必要です。 これを実現するには **[FocusedBorderColor](properties-color-border.md)** および **[FocusedBorderThickness](properties-color-border.md)** を使用します。

    > [!NOTE]
  > **[TabIndex](properties-accessibility.md)** が 0 以上の場合、**画像**はボタンとしてレンダリングされます。 外観は変更はありませんが、スクリーン リーダーは画像をボタンとして正しく識別します。 **[TabIndex](properties-accessibility.md)** が 0 未満の場合、**画像**は画像として識別されます。
