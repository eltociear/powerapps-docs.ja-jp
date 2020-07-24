---
title: 'ラベル コントロール: リファレンス | Microsoft Docs'
description: 各種プロパティとサンプルを含むラベル コントロールに関する情報
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
ms.openlocfilehash: 66de4ee34cf52f3c351fe3f9c624596e5dd1211d
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/13/2020
ms.locfileid: "3308385"
---
# <a name="label-control-in-canvas-apps"></a>キャンバス アプリのラベル コントロール

テキスト、数値、日付、または通貨などのデータを表示するボックスです。

## <a name="description"></a>内容

ラベルには、入力した内容がそのまま表示されるリテラル文字列として、またはテキスト文字列に評価される数式として指定したデータが表示されます。 ラベルは通常、他のコントロール (画面を識別するためのバナーなど) の外側に、別のコントロール (評価コントロール、オーディオ コントロールなど) を識別するラベルとして、またはギャラリー内の項目に関する特定の種類の情報を示すために表示されます。

## <a name="key-properties"></a>主要なプロパティ

**[AutoHeight](properties-core.md)** – ラベルにすべてのテキストが表示されるように高さを自動的に調整する場合は true に設定します。 割り当てた高さでテキストを一部削除する場合は false に設定します。

**[色](properties-color-border.md)** – コントロールのテキストの色。

**[フォント](properties-text.md)** – テキストを表示するフォントのファミリーの名前。

**[テキスト](properties-core.md)** – コントロールに表示されるテキスト、またはユーザーがコントロールに入力するテキスト。

**[DelayOutput](properties-core.md)** – テキスト入力時に操作を遅延させる場合は true に設定します。

## <a name="additional-properties"></a>追加のプロパティ

**[配置](properties-text.md)** – コントロールの水平方向の中心に対するテキストの位置。

**AutoHeight** – **[Text](properties-core.md)** プロパティの内容がコントロールで一度に表示できる文字数を超えている場合に、自動的に **[Height](properties-size-location.md)** プロパティを大きくするかどうかを指定します。

**[BorderColor](properties-color-border.md)** – コントロールの境界線の色。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線が**実線**、**破線**、**点線**、または**なし**かどうか。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さ。

**[DisplayMode](properties-core.md)** – コントロールがユーザー入力を許可するか (**編集**)、データのみを表示するか (**表示**)、または無効にするか (**無効**) どうか。

**[DisabledBorderColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロールの境界線の色。

**[DisabledColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロール内のテキストの色。

**[DisabledFill](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロールの背景色。

**[塗りつぶし](properties-color-border.md)** – コントロールの背景色。

**[FocusedBorderColor](properties-color-border.md)** – コントロールがフォーカスされているときのコントロールの境界線の色。

**[FocusedBorderThickness](properties-color-border.md)** – コントロールがフォーカスされているときのコントロールの境界線の太さ。

**[FontWeight](properties-text.md)** – コントロール内のテキストの太さ: **太字**、**中太**、**標準**、または**細字**。

**[高さ](properties-size-location.md)** – コントロールの上端と下端間の距離。

**[HoverBorderColor](properties-color-border.md)** – ユーザーがコントロール上にマウス ポインターを重ねているときのコントロールの境界線の色。

**[HoverColor](properties-color-border.md)** – ユーザーがコントロールにマウス ポインターを重ねているときのコントロール内のテキストの色。

**[HoverFill](properties-color-border.md)** – ユーザーがコントロールにマウス ポインターを重ねているときのコントロールの背景色。

**[斜体](properties-text.md)** – コントロール内のテキストを斜体にするかどうか。

**[LineHeight](properties-text.md)** – たとえば、テキストの行間またはリスト内の項目間などの距離です。

**[Live](properties-accessibility.md)** – スクリーン リーダーがラベルの **Text** プロパティの値の変更を知らせる方法。

* **オフ**に設定した場合、スクリーン リーダーは変更を知らせません。
* **Polite** に設定した場合、スクリーン リーダーは、スクリーン リーダーが話している間に生じた変更を知らせる前に話し終えます。
* **Assertive** に設定した場合、スクリーン リーダーは、スクリーン リーダーが話している間に生じた変更すべてを知らせるために中断します。

**[OnSelect](properties-core.md)** – ユーザーがコントロールをタップまたはクリックする場合のアプリの反応方法。

**Overflow** – ラベルの **Wrap** プロパティが **true** に設定され、**[Text](properties-core.md)** プロパティの値がコントロールで一度に表示できる文字数を超えている場合に、ラベルにスクロール バーを表示するかどうかを指定します。

**[PaddingBottom](properties-size-location.md)** – コントロール内のテキストとそのコントロールの下端間の距離。

**[PaddingLeft](properties-size-location.md)** – コントロール内のテキストとそのコントロールの左端間の距離。

**[PaddingRight](properties-size-location.md)** – コントロール内のテキストとそのコントロールの右端間の距離。

**[PaddingTop](properties-size-location.md)** – コントロール内のテキストとそのコントロールの上端間の距離。

**[PressedBorderColor](properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロールの境界線の色。

**[PressedColor](properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロール内のテキストの色。

**[PressedFill](properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロールの背景色。

**Role** - 見出し 1 など、ラベル テキストのセマンティック ロール。 ラベルのスタイルは変更しませんが、出力をスクリーン リーダーの解釈のために意味的に修整します。

**[サイズ](properties-text.md)** – コントロールに表示されるテキストのフォント サイズ。

**[Strikethrough](properties-text.md)** – コントロールに表示されるテキストに取り消し線を付けるかどうか。

**[TabIndex](properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序。

**[ツールヒント](properties-core.md)** – ユーザーがコントロールにカーソルを置くときに表示される説明テキスト。

**[下線](properties-text.md)** – コントロールに表示されるテキストの下に線を引くかどうか。

**[VerticalAlign](properties-text.md)** – コントロールの垂直方向の中心に対するコントロール上でのテキストの位置。

**[表示](properties-core.md)** – コントロールが表示されるか非表示になるか。

**[幅](properties-size-location.md)** – コントロールの左端と右端間の距離。

**Wrap** – 長すぎてラベルに収まらないテキストを次の行に折り返すかどうかを指定します。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離。

## <a name="related-functions"></a>関連する関数

[**Text**( *Number*, "*FormatCodes*" )](../functions/function-text.md)

## <a name="examples"></a>例

### <a name="show-a-literal-string"></a>リテラル文字列を表示する

* ラベルを追加し、その **[Text](properties-core.md)** プロパティを **"Hello, world"** (二重引用符を含む) に設定します。
  
    [コントロールの追加および構成](../add-configure-controls.md) についてはこちらをご覧ください。

### <a name="show-the-result-of-a-formula"></a>数式の結果を表示する

* ラベルを追加し、その **[Text](properties-core.md)** プロパティを次のような数式に設定します。<br>
  **Today()**
  
    > [!NOTE]
  > 数式を指定する場合、その数式の引数がリテラル文字列でない限り、引用符は使用しないでください。 この場合、数式ではなく、引数を二重引用符で囲みます。
  
    **[Today](../functions/function-now-today-istoday.md)** 関数または [その他の関数](../formula-reference.md) については各関連記事を参照してください。

### <a name="show-data-in-a-gallery"></a>ギャラリーにデータを表示する

この手順では、**CityPopulations** というコレクションを作成し、ヨーロッパのさまざまな都市の人口に関するデータを格納します。 次に、そのデータを 3 つのラベルを含むギャラリーに表示し、各ラベルに表示するデータの種類を指定します。

1. ボタンを追加し、**[OnSelect](properties-core.md)** プロパティを次の数式に設定します。<br>
   **ClearCollect(CityPopulations, {City:"London", Country:"United Kingdom", Population:8615000}, {City:"Berlin", Country:"Germany", Population:3562000}, {City:"Madrid", Country:"Spain", Population:3165000}, {City:"Rome", Country:"Italy", Population:2874000}, {City:"Paris", Country:"France", Population:2273000}, {City:"Hamburg", Country:"Germany", Population:1760000}, {City:"Barcelona", Country:"Spain", Population:1602000}, {City:"Munich", Country:"Germany", Population:1494000}, {City:"Milan", Country:"Italy", Population:1344000})**
2. F5 キーを押し、ボタンを選択して Esc キーを押します。
3. テキスト ギャラリーを追加し、その **[Items](properties-core.md)** プロパティを **CityPopulations** に設定します。

    ギャラリーを選択すると、右側のウィンドウにそのギャラリー用のオプションが表示されます。
4. **Gallery1** ウィンドウで、上部の一覧を **Population** に、中央の一覧を **City** に、下部の一覧を **Country** にそれぞれ設定します。

## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン

名前とは異なり、**ラベル** コントロールを別のコントロールのラベルとして使用する必要はありません。 任意のテキストを表示するために使用できます。

**ラベル**は、**[OnSelect](properties-core.md)** 動作を指定することにより、ボタンまたはリンクとして使用できます。 この方法で使用する場合、ボタンと同様にアクセシビリティの考慮事項があります。

### <a name="color-contrast"></a>色のコントラスト

次の間には適切な色のコントラストが必要です:

* **[Color](properties-color-border.md)** と **[Fill](properties-color-border.md)**
* その他の [標準の色のコントラスト要件](../accessible-apps-color.md) が適用されます (ボタンまたはリンクとして使用する場合)

### <a name="screen-reader-support"></a>スクリーン リーダーのサポート

* **[Text](properties-core.md)** を指定する必要があります。
* スクリーン リーダーが **Text** プロパティの値への変更を知らせる必要がある場合、**[Live](properties-accessibility.md)** は **Polite** または **Assertive** に設定する必要があります。

  > [!NOTE]
  > **[TabIndex](properties-accessibility.md)** が 0 以上の場合、スクリーン リーダーは**ラベル**をボタンとして扱います。

### <a name="low-vision-support"></a>弱視のサポート

* **ラベル**をリンクとして使用する場合、リンクのように見えるようにします。
  * **[Underline](properties-text.md)** を **true** に設定します
  * **[HoverColor](properties-color-border.md)** は **[Color](properties-color-border.md)** と異なる色にします

### <a name="keyboard-support"></a>キーボードのサポート

* テキストをボタンまたはリンクとして使用する場合は、**[TabIndex](properties-accessibility.md)** を 0 以上にする必要があります。 こうすることで、キーボード ユーザーがそこに移動できるようになります。
* テキストをボタンまたはリンクとして使用する場合は、フォーカス インジケーターを明確に表示する必要があります。 これを実現するには **[FocusedBorderColor](properties-color-border.md)** および **[FocusedBorderThickness](properties-color-border.md)** を使用します。
