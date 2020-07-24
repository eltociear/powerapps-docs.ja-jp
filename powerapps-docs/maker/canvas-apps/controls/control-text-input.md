---
title: 'テキスト入力コントロール: リファレンス | Microsoft Docs'
description: プロパティとサンプルを含むテキスト入力コントロールに関する情報
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/22/2019
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1322fd34f4e3a59a62a414fc0e2e7ccca48fc99f
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/13/2020
ms.locfileid: "3308362"
---
# <a name="text-input-control-in-power-apps"></a>Power Apps のテキスト入力コントロール
ユーザーがテキスト、数値、およびその他のデータを入力できるボックス。

## <a name="description"></a>内容
ユーザーは、テキスト入力コントロールに入力してデータを指定できます。 アプリの構成方法に応じて、そのデータをデータ ソースに追加したり、一時的な値を計算するために使用したり、また他の方法で組み込んだりすることができます。

## <a name="key-properties"></a>主要なプロパティ
**[Default](properties-core.md)** – ユーザーが変更する前のコントロールの初期値です。

**[テキスト](properties-core.md)** – コントロールに表示されるテキスト、またはユーザーがコントロールに入力するテキスト。

## <a name="additional-properties"></a>追加のプロパティ
**[AccessibleLabel](properties-accessibility.md)** – スクリーン リーダー用のラベル。

**[配置](properties-text.md)** – コントロールの水平方向の中心に対するテキストの位置。

**[BorderColor](properties-color-border.md)** – コントロールの境界線の色。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線が**実線**、**破線**、**点線**、または**なし**かどうか。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さ。

**Clear** – テキスト入力コントロールに、ユーザーがタップまたはクリックして、そのコントロールの内容をクリアできる「X」を表示するかどうかを指定します。

**[色](properties-color-border.md)** – コントロールのテキストの色。

**DelayOutput** – true に設定した場合、1/2 秒の遅延の後、ユーザー入力が登録されます。  負荷のかかる操作をユーザーがテキストの入力を完了するまで遅らせる場合 (つまり、入力が他の数式で使用される際にフィルタ処理する場合) に便利です。

**[DisplayMode](properties-core.md)** – コントロールがユーザー入力を許可するか (**編集**)、データのみを表示するか (**表示**)、または無効にするか (**無効**) どうか。

**[DisabledBorderColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロールの境界線の色。

**[DisabledColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロール内のテキストの色。

**[DisabledFill](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロールの背景色。

**EnableSpellCheck** – テキスト入力コントロールがブラウザーのスペル チェック機能を使用するかどうかを指定します。 Power Apps for Windows はこのプロパティをサポートしていません。

**[塗りつぶし](properties-color-border.md)** – コントロールの背景色。

**[FocusedBorderColor](properties-color-border.md)** – コントロールがフォーカスされているときのコントロールの境界線の色。

**[FocusedBorderThickness](properties-color-border.md)** – コントロールがフォーカスされているときのコントロールの境界線の太さ。

**[フォント](properties-text.md)** – テキストを表示するフォントのファミリーの名前。

**[FontWeight](properties-text.md)** – コントロール内のテキストの太さ: **太字**、**中太**、**標準**、または**細字**。

**Format** – ユーザー入力を数字のみに制限するか、またはすべてのテキストを許可するかを指定します。

**[高さ](properties-size-location.md)** – コントロールの上端と下端間の距離。

**HintText** – テキスト入力コントロールが空の場合に表示される薄いグレーのテキストです。

**[HoverBorderColor](properties-color-border.md)** – ユーザーがコントロール上にマウス ポインターを重ねているときのコントロールの境界線の色。

**[HoverColor](properties-color-border.md)** – ユーザーがコントロールにマウス ポインターを重ねているときのコントロール内のテキストの色。

**[HoverFill](properties-color-border.md)** – ユーザーがコントロールにマウス ポインターを重ねているときのコントロールの背景色。

**[斜体](properties-text.md)** – コントロール内のテキストを斜体にするかどうか。

**[LineHeight](properties-text.md)** – たとえば、テキストの行間またはリスト内の項目間などの距離です。

**MaxLength** – ユーザーがテキスト入力コントロールに入力できる文字数です。

**Mode** – コントロールのモードは、**SingleLine**、**MultiLine**、または **Password** です。

**[OnChange](properties-core.md)** – ユーザーが (たとえば、スライダーを調整するなどして) コントロールの値を変更した場合のアプリの反応を指定します。

**[OnSelect](properties-core.md)** – ユーザーがコントロールをタップまたはクリックする場合のアプリの反応方法。

**[PaddingBottom](properties-size-location.md)** – コントロール内のテキストとそのコントロールの下端間の距離。

**[PaddingLeft](properties-size-location.md)** – コントロール内のテキストとそのコントロールの左端間の距離。

**[PaddingRight](properties-size-location.md)** – コントロール内のテキストとそのコントロールの右端間の距離。

**[PaddingTop](properties-size-location.md)** – コントロール内のテキストとそのコントロールの上端間の距離。

**[PressedBorderColor](properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロールの境界線の色。

**[PressedColor](properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロール内のテキストの色。

**[PressedFill](properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロールの背景色。

**[RadiusBottomLeft](properties-size-location.md)** – コントロールの左下隅を丸める度合い。

**[RadiusBottomRight](properties-size-location.md)** – コントロールの右下隅を丸める度合い。

**[RadiusTopLeft](properties-size-location.md)** – コントロールの左上隅を丸める度合い。

**[RadiusTopRight](properties-size-location.md)** – コントロールの右上隅を丸める度合い。

**[Reset](properties-core.md)** – コントロールを既定値に戻すかどうかを指定します。

**[サイズ](properties-text.md)** – コントロールに表示されるテキストのフォント サイズ。

**[Strikethrough](properties-text.md)** – コントロールに表示されるテキストに取り消し線を付けるかどうか。

**[TabIndex](properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序。

**[ツールヒント](properties-core.md)** – ユーザーがコントロールにカーソルを置くときに表示される説明テキスト。

**[下線](properties-text.md)** – コントロールに表示されるテキストの下に線を引くかどうか。

**VirtualKeyboardMode** – アプリ ユーザーのタッチ スクリーンに表示される仮想キーボードのタイプで、テキストまたは数値。 既定値は **Format** プロパティにより決定されます。 デバイスのサポートはそれぞれ異なります。 iOS を実行しているデバイスは、バージョン 12.2 以降が必要です。 Android の推奨バージョンは 9.0 で、数字キーボードの機能は Android デバイスによって異なります。 Windows 10 はこのプロパティをサポートしていません。  

**[表示](properties-core.md)** – コントロールが表示されるか非表示になるか。

**[幅](properties-size-location.md)** – コントロールの左端と右端間の距離。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離。

## <a name="related-functions"></a>関連する関数
[**DateTimeValue**( *String* )](../functions/function-datevalue-timevalue.md)

## <a name="examples"></a>例
### <a name="collect-data"></a>データを収集する
1. 2 つのテキスト入力コントロールを追加し、それらに **inputFirst** と **inputLast** という名前を付けます。
   
    [コントロールの追加、名前付け、構成](../add-configure-controls.md) についてはこちらをご覧ください。
2. ボタンを追加し、その **[Text](properties-core.md)** プロパティを **Add** に設定し、その**[OnSelect](properties-core.md)** プロパティを次の式に設定します。<br>
   **Collect(Names, {FirstName:inputFirst.Text, LastName:inputLast.Text})**
   
    **[Collect](../functions/function-clear-collect-clearcollect.md)** 関数または [その他の関数](../formula-reference.md) については、各関連記事を参照してください。
3. 縦/垂直方向にテキスト ギャラリーを追加し、その **[Items](properties-core.md)** プロパティを **Names** に設定し、**Subtitle1** の **[Text](properties-core.md)** プロパティを **ThisItem.FirstName** に設定します。
4. (任意) テンプレート ギャラリーで、下部の **Body1** というラベルを削除し、ギャラリーの **[TemplateSize](control-gallery.md)** プロパティを **80** に設定します。
5. F5 キーを押して、**inputFirst** と **inputLast** に文字列を入力して、**追加**ボタンをクリックまたはタップします。
6. (任意) 他の名前をコレクションに追加し、Esc キーを押して、既定のワークスペースに戻ります。

### <a name="prompt-for-a-password"></a>パスワードの入力を求める

1. テキスト入力コントロールを追加し、それに **inputPassword** という名前を付けて、その **Mode** プロパティを **Password** に設定します。

1. ラベルを追加し、その **[Text](properties-core.md)** プロパティを次の数式に設定します。<br>
   **If(inputPassword.Text = "P@ssw0rd", "Access granted", "Access denied")**

    **[If](../functions/function-if.md)** 関数または [その他の関数](../formula-reference.md) の詳細については各関連記事を参照してください。

1. F5 キーを押し、**inputPassword** に **P@ssw0rd** と入力します。

    パスワードの入力が完了すると、ラベルの **Access denied** の表示が停止し、**Access granted** の表示が開始します。

1. 既定のワークスペースに戻るには、Esc キーを押します。

1. (任意) 矢印などのコントロールを追加し、それを別の画面に移動するように構成し、ユーザーがパスワードを入力した後にのみ表示するようにします。

1. (任意) ボタンを追加し、その **[Text](properties-core.md)** プロパティに **Sign in** と表示されるように設定した後、タイマーを追加し、ユーザーが間違ったパスワードを入力して **Sign in** ボタンをクリックまたはタップした場合に、一定の時間テキスト入力コントロールを無効にします。


## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
### <a name="color-contrast"></a>色のコントラスト
* [標準の色のコントラスト要件](../accessible-apps-color.md) が適用されます。

### <a name="screen-reader-support"></a>スクリーン リーダー サポート
* **[AccessibleLabel](properties-accessibility.md)** が存在する必要があります。

### <a name="keyboard-support"></a>キーボードのサポート
* **[TabIndex](properties-accessibility.md)** を 0 以上にして、キーボード ユーザーがそこに移動できるようにする必要があります。
* フォーカス インジケーターは明確に表示する必要があります。 これを実現するには **[FocusedBorderColor](properties-color-border.md)** および **[FocusedBorderThickness](properties-color-border.md)** を使用します。
 
