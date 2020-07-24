---
title: 'トグル コントロール: リファレンス | Microsoft Docs'
description: 各種プロパティとサンプルを含むトグル コントロールに関する情報です
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
ms.openlocfilehash: 17bceb06af2c460eb122f1bab0dc382b00838ee5
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3305901"
---
# <a name="toggle-control-in-power-apps"></a>Power Apps のトグル コントロール
ユーザーがハンドルを動かすことでオンまたはオフにできるコントロールです。

## <a name="description"></a>内容
トグルは最近の GUI 向けのデザインですが、動作はチェック ボックスと同じです。

## <a name="key-properties"></a>主要なプロパティ
**[Default](properties-core.md)** – ユーザーが変更する前のコントロールの初期値です。

**[Value](properties-core.md)** – 入力コントロールの値です。

## <a name="additional-properties"></a>追加のプロパティ
**[AccessibleLabel](properties-accessibility.md)** – スクリーン リーダー用のラベル。

**[BorderColor](properties-color-border.md)** – コントロールの境界線の色。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線が**実線**、**破線**、**点線**、または**なし**かどうか。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さ。

**[DisplayMode](properties-core.md)** – コントロールがユーザー入力を許可するか (**編集**)、データのみを表示するか (**表示**)、または無効にするか (**無効**) どうか。

**[DisabledBorderColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロールの境界線の色。

**FalseFill** – トグルが無効な場合の、トグルの塗りつぶしの色です。

**FalseHoverFill** – トグルが無効な場合の、トグルのポイント時の塗りつぶしの色です。

**FalseText** – トグルが無効な場合に表示されるテキストです。

**[塗りつぶし](properties-color-border.md)** – コントロールの背景色。

**[FocusedBorderColor](properties-color-border.md)** – コントロールがフォーカスされているときのコントロールの境界線の色。

**[FocusedBorderThickness](properties-color-border.md)** – コントロールがフォーカスされているときのコントロールの境界線の太さ。

**HandleFill** – トグル ハンドルの塗りつぶしの色。

**[高さ](properties-size-location.md)** – コントロールの上端と下端間の距離。

**[HoverBorderColor](properties-color-border.md)** – ユーザーがコントロール上にマウス ポインターを重ねているときのコントロールの境界線の色。

**[OnChange](properties-core.md)** – ユーザーが (たとえば、スライダーを調整するなどして) コントロールの値を変更した場合のアプリの反応を指定します。

**OnCheck** – チェックボックスまたはトグルの値が **true** に変わったときの、アプリの反応を指定します。

**[OnSelect](properties-core.md)** – ユーザーがコントロールをタップまたはクリックする場合のアプリの反応方法。

**OnUncheck** – チェック ボックスまたはトグルの値が **false** に変わったときの、アプリの反応を指定します。

**[PressedBorderColor](properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロールの境界線の色。

**RailFill** – 値が **false** の場合のトグル コントロール内の四角形の背景色、またはスライダー コントロールのハンドルの右側の線の色です。

**RailHoverFill** – 値が **false** の場合に、トグル コントロールまたはスライダーをポイントしたときの、トグル コントロール内の四角形の背景色、またはスライダー コントロールのハンドルの右側の線の色です。

**[Reset](properties-core.md)** – コントロールを既定値に戻すかどうかを指定します。

**ShowLabel** – テキスト ラベルをトグル コントロールの横に表示するかどうかを指定します。

**[TabIndex](properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序。

**TextPosition** – ラベルをトグル コントロールの右側と左側のどちらにするかを指定します。

**[ツールヒント](properties-core.md)** – ユーザーがコントロールにカーソルを置くときに表示される説明テキスト。

**TrueFill** – トグルが有効な場合の、トグルの塗りつぶしの色です。

**TrueHoverFill** – トグルが有効な場合の、トグルのポイント時の塗りつぶしの色です。

**TrueText** – トグルが有効な場合に表示されるテキストです。

**ValueFill** – 値が **true** の場合の、トグル コントロール内の四角形の背景色、またはスライダー コントロールのハンドルの左側の線の色です。

**ValueHoverFill** – 値が **true** の場合に、トグル コントロールまたはスライダーにポインターを合わせたときの、トグル コントロール内の四角形の背景色、またはスライダー コントロールのハンドルの左側の線の色です。

**[表示](properties-core.md)** – コントロールが表示されるか非表示になるか。

**[幅](properties-size-location.md)** – コントロールの左端と右端間の距離。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離。

## <a name="related-functions"></a>関連する関数
[**If**( *Condition*, *Result* )](../functions/function-if.md)

## <a name="example"></a>例
1. トグルを追加し、名前を **MemberDiscount** にします。

    [コントロールの追加、名前付け、構成](../add-configure-controls.md) についてはこちらをご覧ください。
2. ラベルを追加し、その **[Text](properties-core.md)** プロパティを次の数式に設定します。
   <br>**If(MemberDiscount.Value = true, "Price: $75", "Price: $100")**

    **[If](../functions/function-if.md)** 関数または [その他の関数](../formula-reference.md) の詳細については各関連記事を参照してください。
3. F5 キーを押し、**MemberDiscount** の値を変更します。

    **MemberDiscount** がオンかオフかに応じて、ラベルに異なる価格が表示されます。
4. 既定のワークスペースに戻るには、Esc キーを押します。


## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
### <a name="color-contrast"></a>色のコントラスト
次の間には適切な色のコントラストが必要です:
* **HandleFill** および **FalseFill**
* **HandleFill** および **FalseHoverFill**
* **HandleFill** および **TrueFill**
* **HandleFill** および **TrueHoverFill**
* **Fill** およびコントロールの外側の色
* **FalseHoverFill** およびコントロールの外側の色
* **TrueFill** およびコントロールの外側の色
* **TrueHoverFill** およびコントロールの外側の色

これは、[標準の色のコントラスト要件](../accessible-apps-color.md) に追加されるものです。

### <a name="screen-reader-support"></a>スクリーン リーダー サポート
* **[AccessibleLabel](properties-accessibility.md)** が存在する必要があります。
* **FalseText** を指定する必要があります。
* **TrueText** を指定する必要があります。

### <a name="low-vision-support"></a>弱視のサポート
* ユーザーがトグル値をすばやく判断できるように、**ShowLabel** を **true** に設定することを検討してください。

### <a name="keyboard-support"></a>キーボードのサポート
* **[TabIndex](properties-accessibility.md)** を 0 以上にして、キーボード ユーザーがそこに移動できるようにする必要があります。
* フォーカス インジケーターは明確に表示する必要があります。 これを実現するには **[FocusedBorderColor](properties-color-border.md)** および **[FocusedBorderThickness](properties-color-border.md)** を使用します。
