---
title: 'チェック ボックス コントロール: リファレンス | Microsoft Docs'
description: プロパティとサンプルを含む、チェック ボックス コントロールに関する情報
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
ms.openlocfilehash: 7bb993de28435478c65e061e959b2fa8945e73d1
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3306154"
---
# <a name="check-box-control-in-power-apps"></a>Power Apps でのチェック ボックス コントロール
値を **true** または **false** に設定するためにユーザーがオンまたはオフにできるコントロール。

## <a name="description"></a>内容
ユーザーは、何十年もの間 GUI で使用されてきた、この使い慣れたコントロールを使用してブール値を指定できます。

## <a name="key-properties"></a>主要なプロパティ
**[Default](properties-core.md)** – ユーザーが変更する前のコントロールの初期値です。

**[テキスト](properties-core.md)** – コントロールに表示されるテキスト、またはユーザーがコントロールに入力するテキスト。

**[Value](properties-core.md)** – 入力コントロールの値です。

## <a name="additional-properties"></a>追加のプロパティ
**[BorderColor](properties-color-border.md)** – コントロールの境界線の色。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線が**実線**、**破線**、**点線**、または**なし**かどうか。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さ。

**CheckboxBackgroundFill** – チェックボックス コントロール内のチェックマークを囲むボックスの背景色。

**CheckboxBorderColor** – チェックボックス コントロール内のチェックマークを囲む境界線の色。

**CheckboxSize** – チェック ボックス コントロール内のチェックマークを囲むボックスの幅と高さ。

**CheckmarkFill** – チェック ボックス コントロール内のチェックマークの色。

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

**[HoverBorderColor](properties-color-border.md)** – ユーザーがコントロール上にマウス ポインターを重ねているときのコントロールの境界線の色。

**[HoverColor](properties-color-border.md)** – ユーザーがコントロールにマウス ポインターを重ねているときのコントロール内のテキストの色。

**[HoverFill](properties-color-border.md)** – ユーザーがコントロールにマウス ポインターを重ねているときのコントロールの背景色。

**[斜体](properties-text.md)** – コントロール内のテキストを斜体にするかどうか。

**OnCheck** – チェックボックスまたはトグルの値が **true** に変わったときの、アプリの反応を指定します。

**[OnSelect](properties-core.md)** – ユーザーがコントロールをタップまたはクリックする場合のアプリの反応方法。

**OnUncheck** – チェック ボックスまたはトグルの値が **false** に変わったときの、アプリの反応を指定します。

**[PaddingBottom](properties-size-location.md)** – コントロール内のテキストとそのコントロールの下端間の距離。

**[PaddingLeft](properties-size-location.md)** – コントロール内のテキストとそのコントロールの左端間の距離。

**[PaddingRight](properties-size-location.md)** – コントロール内のテキストとそのコントロールの右端間の距離。

**[PaddingTop](properties-size-location.md)** – コントロール内のテキストとそのコントロールの上端間の距離。

**[PressedBorderColor](properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロールの境界線の色。

**[PressedColor](properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロール内のテキストの色。

**[PressedFill](properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロールの背景色。

**[Reset](properties-core.md)** – コントロールを既定値に戻すかどうかを指定します。

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
[**If**( *Condition*, *Result* )](../functions/function-if.md)

## <a name="example"></a>例
1. **チェック ボックス** コントロールを追加して **chkReserve** という名前を付け、その **[テキスト](properties-core.md)** プロパティを**今すぐ予約する**を表示するよう設定します。
   
    [コントロールの追加、名前付け、構成](../add-configure-controls.md) についてはこちらをご覧ください。
2. **[日付の選択](control-date-picker.md)** コントロールを追加し、その **[表示](properties-core.md)** プロパティを次の数式に設定します:
   <br>**If(chkReserve.Value = true, true)**
   
    **[If](../functions/function-if.md)** 関数または [その他の関数](../formula-reference.md) の詳細については各関連記事を参照してください。
3. F5 キーを押して、**chkReserve** をクリックまたはタップしてその **[値](properties-core.md)** プロパティを **true** に設定してから、もう一度 **chkReserve** をクリックまたはタップしてその **[値](properties-core.md)** プロパティを **false** に設定します。
   
    **[日付の選択](control-date-picker.md)** コントロールは、**chkReserve** の **[値](properties-core.md)** プロパティが **true** のときは表示されますが、**false** のときは表示されません。
4. 既定のワークスペースに戻るには、Esc キーを押します。


## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
### <a name="color-contrast"></a>色のコントラスト
次の間には適切な色のコントラストが必要です:
* **CheckmarkFill** と **CheckboxBackgroundFill**
* **CheckboxBackgroundFill** と **[塗りつぶし](properties-color-border.md)**
* **CheckboxBackgroundFill** と **[PressedFill](properties-color-border.md)**
* **CheckboxBackgroundFill** と **[HoverFill](properties-color-border.md)**

これは、[標準の色のコントラスト要件](../accessible-apps-color.md) に追加されるものです。

### <a name="screen-reader-support"></a>スクリーン リーダー サポート
* **[Text](properties-core.md)** を指定する必要があります。

### <a name="keyboard-support"></a>キーボードのサポート
* **[TabIndex](properties-accessibility.md)** を 0 以上にして、キーボード ユーザーがそこに移動できるようにする必要があります。
* フォーカス インジケーターは明確に表示する必要があります。 これを実現するには **[FocusedBorderColor](properties-color-border.md)** および **[FocusedBorderThickness](properties-color-border.md)** を使用します。
 
