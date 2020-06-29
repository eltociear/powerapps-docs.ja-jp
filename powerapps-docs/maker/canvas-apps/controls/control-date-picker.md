---
title: '日付の選択コントロール: リファレンス | Microsoft Docs'
description: プロパティとサンプルを含む、日付の選択コントロールに関する情報
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/10/2020
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 4d241eb8ce8ec9f6d0fa17ac802aeddbd142de25
ms.sourcegitcommit: af653cd30f5879fea97a594d458d355fe18f4834
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/11/2020
ms.locfileid: "3309236"
---
# <a name="date-picker-control-in-power-apps"></a>Power Apps での日付の選択コントロール
ユーザーがクリックまたはタップして日付を指定できるコントロール。

## <a name="description"></a>内容
**[テキスト入力](control-text-input.md)** コ ントロールの代わりに**日付の選択**コントロールを追加すると、ユーザーが適切な形式で日付を指定しやすくなります。

## <a name="key-properties"></a>主要なプロパティ
**DefaultDate** – ユーザーが変更しない限りの日付コントロールの初期値。

**SelectedDate** – 日付コントロールで現在選択されている日付。  この日付はローカル時間で表されます。

**形式** – コントロールで日付が表示され、ユーザーが日付を指定するテキスト形式。 このプロパティを **ShortDate** (既定) または **LongDate** に設定して、このコントロールの**言語**プロパティに基づいて日付を書式設定できます。 また、言語に関係なく同じ形式を使用する場合は、このプロパティを **yyyy/mm/dd** などの式に設定できます。 たとえば、次のようなものです。

* ユーザーが 2017 年の最終日をクリックまたはタップする場合、コントロールには **12/31/2017** と表示され、**形式**プロパティは **ShortDate** に、**言語**プロパティは **en-us** に設定されます。
* ユーザーが 2017 年の最終日をクリックまたはタップする場合、コントロールには **dimanche 31 decembre 2017** と表示され、**形式**プロパティは **LongDate** に、**言語**プロパティは **fr-fr** に設定されます。

**言語** – 月の名前を含む、日付の書式を設定するために使用される言語を指定します。 このプロパティが指定されていない場合、ユーザーのデバイスの設定で言語が決まります。 サポートされる値には、"EN-us" および "FR" が含まれます。

## <a name="additional-properties"></a>追加のプロパティ
**[AccessibleLabel](properties-accessibility.md)** – スクリーン リーダー用のラベル。

**[BorderColor](properties-color-border.md)** – コントロールの境界線の色。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線が**実線**、**破線**、**点線**、または**なし**かどうか。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さ。

**[色](properties-color-border.md)** – コントロールのテキストの色。

**DateTimeZone** – 日付を **UTC** またはユーザーの**ローカル**時間で表示するかどうか。

**[DisplayMode](properties-core.md)** – コントロールがユーザー入力を許可するか (編集)、データのみを表示するか (表示)、または無効にするか (無効) どうか。

**[DisabledBorderColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロールの境界線の色。

**[DisabledColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロール内のテキストの色。

**[DisabledFill](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロールの背景色。

**EndYear** – ユーザーが日付の選択コントロールの値を設定できる最新の年。

**[塗りつぶし](properties-color-border.md)** – コントロールの背景色。

**[FocusedBorderColor](properties-color-border.md)** – コントロールがフォーカスされているときのコントロールの境界線の色。

**[FocusedBorderThickness](properties-color-border.md)** – コントロールがフォーカスされているときのコントロールの境界線の太さ。

**[フォント](properties-text.md)** – テキストを表示するフォントのファミリーの名前。

**[FontWeight](properties-text.md)** – コントロール内のテキストの太さ: **太字**、**中太**、**標準**、または**細字**。

**[高さ](properties-size-location.md)** – コントロールの上端と下端間の距離。

**IconFill** – 日付の選択アイコンの前景色。

**IconBackground** – 日付の選択アイコンの背景色。

**InputTextPlaceholder** – 日付が入力されていない場合に表示される説明テキスト。

**IsEditable** – 日付の選択テキストを編集できるかどうか。 false の場合、日付はカレンダーを使用してのみ変更できます。

**[斜体](properties-text.md)** – コントロール内のテキストを斜体にするかどうか。

**[OnSelect](properties-core.md)** – ユーザーがコントロールをタップまたはクリックする場合のアプリの反応方法。

**[OnChange](properties-core.md)** – ユーザーがコントロールの値を変更するときのアプリの反応方法。 

**OnChange** および **OnSelect** 間の違い: OnSelect および OnChange では、ユーザーの*クリック*によって変更が発生する場合に、同じユーザー アクションでトリガーされます。この場合、OnSelect は OnChange の**前**にトリガーします。

**[PaddingBottom](properties-size-location.md)** – コントロール内のテキストとそのコントロールの下端間の距離。

**[PaddingLeft](properties-size-location.md)** – コントロール内のテキストとそのコントロールの左端間の距離。

**[PaddingRight](properties-size-location.md)** – コントロール内のテキストとそのコントロールの右端間の距離。

**[PaddingTop](properties-size-location.md)** – コントロール内のテキストとそのコントロールの上端間の距離。

**[サイズ](properties-text.md)** – コントロールに表示されるテキストのフォント サイズ。

**StartOfWeek** – 日付の選択コントロールの最初の日列に表示する曜日。

**StartYear** – ユーザーが日付の選択コントロールの値を設定できる最初の年。

**[TabIndex](properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序。

**[表示](properties-core.md)** – コントロールが表示されるか非表示になるか。

**[幅](properties-size-location.md)** – コントロールの左端と右端間の距離。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離。

## <a name="related-functions"></a>関連する関数
**[年](../functions/function-datetime-parts.md)**( *DateTimeValue* )

## <a name="example"></a>例
1. **日付の選択**コントロールを追加して、**期限**という名前を付けます。

    [コントロールの追加、名前付け、構成](../add-configure-controls.md) についてはこちらをご覧ください。
2. **[ラベル](control-text-box.md)** コントロールを追加し、その **[テキスト](properties-core.md)** プロパティを次の数式に設定します:
   <br>**DateDiff(今日()、Deadline.SelectedDate) & "残り日数!"**

    **[DateDiff](../functions/function-dateadd-datediff.md)** 関数または [その他の関数](../formula-reference.md) については各関連記事を参照してください。
3. F5 キーを押して、**期限**の日付を選択してから、**OK** をクリックまたはタップします。

    **[ラベル](control-text-box.md)** コントロールでは、当日から選択した日付までの日数が表示されます。
4. 既定のワークスペースに戻るには、Esc キーを押します。


## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
### <a name="color-contrast"></a>色のコントラスト
* [標準の色のコントラスト要件](../accessible-apps-color.md) が適用されます。

### <a name="screen-reader-support"></a>スクリーン リーダー サポート
* **[AccessibleLabel](properties-accessibility.md)** が存在する必要があります。

### <a name="keyboard-support"></a>キーボードのサポート
* **[TabIndex](properties-accessibility.md)** を 0 以上にして、キーボード ユーザーがそこに移動できるようにする必要があります。
* フォーカス インジケーターは明確に表示する必要があります。 これを実現するには **[FocusedBorderColor](properties-color-border.md)** および **[FocusedBorderThickness](properties-color-border.md)** を使用します。

> [!TIP]
> カレンダーが開いているときに、**Page up** キーと **Page down** キーを押して月の間を移動し、**Shift+Page up** キーと **Shift+Page down** キーを押して年の間を移動します。
