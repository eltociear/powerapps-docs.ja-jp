---
title: '画像の追加コントロール: リファレンス | Microsoft Docs'
description: プロパティとサンプルを含む、画像の追加コントロールに関する情報
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 04/17/2020
ms.author: chmoncay
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: fabde7df7a4c9f8c459b9abba1f2d0814909f886
ms.sourcegitcommit: 81d6996e870b55797372429d66f9b56a7200d154
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2020
ms.locfileid: "3309397"
---
# <a name="add-picture-control-in-power-apps"></a>Power Apps での画像の追加コントロール
写真を撮影したり、ローカル デバイスから画像を読み込みます。

## <a name="description"></a>内容
このコントロールを使用すると、ユーザーは写真を撮影したり、デバイスから画像ファイルをアップロードしたり、このコンテンツでデータ ソースを更新したりできます。 モバイル デバイスでは、ユーザーにはデバイスの選択ダイアログが表示され、ユーザーは写真を撮影するか既存の画像を使用するかを選択できます。

このコントロールは、**画像**および**画像の追加ボタン**の 2 つのコントロールを含むグループ化されたコントロールです。 **画像**コントロールには、アップロードされた画像、または画像がアップロードされていない場合はプレースホルダーが表示されます。 **画像の追加ボタン**は、画像をアップロードするように求めます。

**Image** プロパティについては、[イメージ コントロールのリファレンス](control-image.md) を参照してください。

## <a name="add-picture-button-properties"></a>画像ボタンのプロパティの追加
**[AccessibleLabel](properties-accessibility.md)** – スクリーン リーダー用のラベル。 画像追加の目的を説明する必要があります。

**[配置](properties-text.md)** – コントロールの水平方向の中心に対するテキストの位置。

**[BorderColor](properties-color-border.md)** – コントロールの境界線の色。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線が**実線**、**破線**、**点線**、または**なし**かどうか。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さ。

**ChangePictureText** – 画像がアップロードされたときにボタンに表示されるテキスト。

**[色](properties-color-border.md)** – コントロールのテキストの色。

**[DisabledBorderColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロールの境界線の色。

**[DisabledColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロール内のテキストの色。

**[DisabledFill](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロールの背景色。

**[DisplayMode](properties-core.md)** – コントロールがユーザー入力を許可するか (**編集**)、データのみを表示するか (**表示**)、または無効にするか (**無効**) どうか。

**エラー** - 画像のアップロードで問題が発生した場合、このプロパティには該当するエラー文字列が含まれます。

**[塗りつぶし](properties-color-border.md)** – コントロールの背景色。

**[FocusedBorderColor](properties-color-border.md)** – コントロールがフォーカスされているときのコントロールの境界線の色。

**[FocusedBorderThickness](properties-color-border.md)** – コントロールがフォーカスされているときのコントロールの境界線の太さ。

**[フォント](properties-text.md)** – テキストを表示するフォントのファミリーの名前。

**[FontWeight](properties-text.md)** – コントロール内のテキストの太さ: **太字**、**中太**、**標準**、または**細字**。

**[高さ](properties-size-location.md)** – コントロールの上端と下端間の距離。

**[HoverBorderColor](properties-color-border.md)** – ユーザーがコントロール上にマウス ポインターを重ねているときのコントロールの境界線の色。

**[HoverColor](properties-color-border.md)** – ユーザーがコントロールにマウス ポインターを重ねているときのコントロール内のテキストの色。

**[HoverFill](properties-color-border.md)** – ユーザーがコントロールにマウス ポインターを重ねているときのコントロールの背景色。

**[斜体](properties-text.md)** – コントロール内のテキストを斜体にするかどうか。

**Media** – オーディオまたはビデオ コントロールが再生するクリップの ID です。

**[OnChange](properties-core.md)** – ユーザーが (たとえば、スライダーを調整するなどして) コントロールの値を変更した場合のアプリの反応を指定します。

**[OnSelect](properties-core.md)** – ユーザーがコントロールをタップまたはクリックする場合のアプリの反応方法。

**[パディング](properties-size-location.md)** – インポートまたはエクスポート ボタンのテキストと、そのボタンの端との間の距離。

**[PressedBorderColor](properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロールの境界線の色。

**[PressedColor](properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロール内のテキストの色。

**[PressedFill](properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロールの背景色。

**[Reset](properties-core.md)** – コントロールを既定値に戻すかどうかを指定します。

**[サイズ](properties-text.md)** – コントロールに表示されるテキストのフォント サイズ。

**[Strikethrough](properties-text.md)** – コントロールに表示されるテキストに取り消し線を付けるかどうか。

**[TabIndex](properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序。

**[テキスト](properties-core.md)** – イメージがアップロードされていないときにボタンに表示されるテキスト。

**[ツールヒント](properties-core.md)** – ユーザーがコントロールにカーソルを置くときに表示される説明テキスト。

**[下線](properties-text.md)** – コントロールに表示されるテキストの下に線を引くかどうか。

**UseMobileCamera** – 利用可能な場合に、モバイル カメラを直接使用するかどうか。

**[VerticalAlign](properties-text.md)** – コントロールの垂直方向の中心に対するコントロール上でのテキストの位置。

**[表示](properties-core.md)** – コントロールが表示されるか非表示になるか。

**[幅](properties-size-location.md)** – コントロールの左端と右端間の距離。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離。

## <a name="related-functions"></a>関連する関数
[**Patch**( *DataSource*、*BaseRecord*、*ChangeRecord* )](../functions/function-patch.md)

## <a name="examples"></a>例
### <a name="add-images-to-an-image-gallery-control"></a>画像ギャラリー コントロールへの画像の追加
1. **画像の追加**コントロールを追加してから、それをトリプルクリックします。
   
    [コントロールの追加、名前付け、構成](../add-configure-controls.md) についてはこちらをご覧ください。
1. **開く**ダイアログ ボックスで、画像ファイルをクリックまたはタップしてから、**開く**をクリックまたはタップします。
1. **[ボタン](control-button.md)** コントロールを追加して、**画像の追加**コントロールの下に移動し、**[ボタン](control-button.md)** コントロールの **[OnSelect](properties-core.md)** プロパティを次の数式に設定します:<br>
   **Collect(MyPix, AddMediaButton1.Media)**
   
    **[Collect](../functions/function-clear-collect-clearcollect.md)** 関数または [その他の関数](../formula-reference.md) については、各関連記事を参照してください。
1. **垂直ギャラリー** コントロールを追加し、その **[項目](properties-core.md)** プロパティを **MyPix** に設定します。
1. ギャラリーで **[画像](control-image.md)** コントロールを選択して、**画像**プロパティを **ThisItem.Value** に設定します。
1. F5 キーを押してから、**[ボタン](control-button.md)** コントロールをクリックまたはタップします。
   
    **画像の追加**コントロールからの画像が**垂直ギャラリー** コントロールに表示されます。 画像の縦横比が**垂直ギャラリー** コントロール内の **[画像](control-image.md)** コントロールと同じでない場合は、**[画像](control-image.md)** コントロールの **[ImagePosition](properties-visual.md)** プロパティを**自動調整**に設定します。
1. **画像の追加**コントロールをクリックまたはタップし、別の画像ファイルをクリックまたはタップし、**開く**をクリックまたはタップしてから、追加した**[ボタン](control-button.md)** コントロールをクリックまたはタップします。
   
    2 番目の画像が**画像ギャラリー** コントロールに表示されます。
1. (オプション) 前の手順を何回も繰り返してから、Esc キーを押して既定のワークスペースに戻ります。

**[SaveData](../functions/function-savedata-loaddata.md)** 関数を使用して画像をローカルに保存するか、**[パッチ](../functions/function-patch.md)** 関数を使用してデータ ソースを更新します。


## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
**[ボタン](control-button.md)** および**[画像](control-image.md)** と同じガイドラインが適用されます。 さらに次の点について考慮してください:

### <a name="color-contrast"></a>色のコントラスト
* **画像の追加ボタン**には、テキストと背景の間に適切なコントラストが必要です。 アップロードされる画像にはさまざまな色が存在する可能性があるので、**画像の追加ボタン**で不透明な**[塗りつぶし](properties-color-border.md)** を使用して一貫したコントラストにします。

### <a name="screen-reader-support"></a>スクリーン リーダー サポート
* **画像の追加ボタン**には、ユーザーに画像の追加または変更を求める**テキスト**および **ChangePictureText** が必要です。

### <a name="keyboard-support"></a>キーボードのサポート
* **画像の追加ボタン**では、**[TabIndex](properties-accessibility.md)** を 0 以上にして、キーボード ユーザーがそこに移動できるようにする必要があります。
* **画像の追加ボタン**には、明確に判別できるフォーカス インジケーターが必要です。 これを実現するには **[FocusedBorderColor](properties-color-border.md)** および **[FocusedBorderThickness](properties-color-border.md)** を使用します。
 
