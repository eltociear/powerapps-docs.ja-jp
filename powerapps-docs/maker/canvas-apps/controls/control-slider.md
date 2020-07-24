---
title: 'スライダー コントロール: リファレンス | Microsoft Docs'
description: 各種プロパティとサンプルを含むスライダー コントロールに関する情報
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
ms.openlocfilehash: 6cabcfe58841a5d507ec31b6279cc9a00922850f
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/13/2020
ms.locfileid: "3308408"
---
# <a name="slider-control-in-power-apps"></a>Power Apps のスライダー コントロール
ハンドルをドラッグすることによりユーザーが値を指定できるコントロールです。

## <a name="description"></a>内容
ユーザーは、選択した方向に基づいて、スライダーのハンドルを左右または上下にドラッグして、指定された最小値と最大値の間の値を指定できます。

## <a name="key-properties"></a>主要なプロパティ
**[Default](properties-core.md)** – ユーザーが変更する前のコントロールの初期値です。

**Max** – ユーザーがスライダーまたは評価を設定できる最大値です。

**Min** – ユーザーがスライダーを設定できる最小値です。

**[Value](properties-core.md)** – 入力コントロールの値です。

## <a name="additional-properties"></a>追加のプロパティ
**[AccessibleLabel](properties-accessibility.md)** – スクリーン リーダー用のラベル。

**[BorderColor](properties-color-border.md)** – コントロールの境界線の色。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線が**実線**、**破線**、**点線**、または**なし**かどうか。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さ。

**[DisplayMode](properties-core.md)** – コントロールがユーザー入力を許可するか (**編集**)、データのみを表示するか (**表示**)、または無効にするか (**無効**) どうか。

**[DisabledBorderColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロールの境界線の色。

**[FocusedBorderColor](properties-color-border.md)** – コントロールがフォーカスされているときのコントロールの境界線の色。

**[FocusedBorderThickness](properties-color-border.md)** – コントロールがフォーカスされているときのコントロールの境界線の太さ。

**HandleActiveFill** – ユーザーが値を変更しているときのスライダーのハンドルの色です。

**HandleFill** – トグルまたはスライダー コントロールのハンドル (位置が変わる要素) の色です。

**HandleHoverFill** – スライダーのハンドルにユーザーがマウス ポインターを重ねているときのハンドルの色です。

**HandleSize** – ハンドルの直径。

**[高さ](properties-size-location.md)** – コントロールの上端と下端間の距離。

**[HoverBorderColor](properties-color-border.md)** – ユーザーがコントロール上にマウス ポインターを重ねているときのコントロールの境界線の色。

**Layout** – ユーザーがギャラリーをスクロールしたりスライダーを調整したりする方向です。上下 (**Vertical**) または左右 (**Horizontal**) から選択します。

**[OnChange](properties-core.md)** – ユーザーが (たとえば、スライダーを調整するなどして) コントロールの値を変更した場合のアプリの反応を指定します。

**[OnSelect](properties-core.md)** – ユーザーがコントロールをタップまたはクリックする場合のアプリの反応方法。

**[PressedBorderColor](properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロールの境界線の色。

**RailFill** – 値が **false** の場合のトグル コントロール内の四角形の背景色、またはスライダー コントロールのハンドルの右側の線の色です。

**RailHoverFill** – 値が **false** の場合に、トグル コントロールまたはスライダーをポイントしたときの、トグル コントロール内の四角形の背景色、またはスライダー コントロールのハンドルの右側の線の色です。

**ReadOnly** – ユーザーがスライダーまたは評価コントロールの値を変更できるかどうかを指定します。

**[Reset](properties-core.md)** – コントロールを既定値に戻すかどうかを指定します。

**ShowValue** – ユーザーがスライダーまたは評価の値を変更するか、ポインタをコントロールに合わせたときにその値を表示するかどうかを指定します。

**[TabIndex](properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序。

**[ツールヒント](properties-core.md)** – ユーザーがコントロールにカーソルを置くときに表示される説明テキスト。

**ValueFill** – 値が **true** の場合の、トグル コントロール内の四角形の背景色、またはスライダー コントロールのハンドルの左側の線の色です。

**ValueHoverFill** – 値が **true** の場合に、トグル コントロールまたはスライダーにポインターを合わせたときの、トグル コントロール内の四角形の背景色、またはスライダー コントロールのハンドルの左側の線の色です。

**[表示](properties-core.md)** – コントロールが表示されるか非表示になるか。

**[幅](properties-size-location.md)** – コントロールの左端と右端間の距離。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離。

## <a name="related-functions"></a>関連する関数
[**Sum**( *Value1*, *Value2* )](../functions/function-aggregates.md)

## <a name="example"></a>例
1. ボタンを追加し、**[OnSelect](properties-core.md)** プロパティを次の数式に設定します。
   <br>**ClearCollect(CityPopulations, {City:"London", Country:"United Kingdom", Population:8615000}, {City:"Berlin", Country:"Germany", Population:3562000}, {City:"Madrid", Country:"Spain", Population:3165000}, {City:"Rome", Country:"Italy", Population:2874000}, {City:"Paris", Country:"France", Population:2273000}, {City:"Hamburg", Country:"Germany", Population:1760000}, {City:"Barcelona", Country:"Spain", Population:1602000}, {City:"Munich", Country:"Germany", Population:1494000}, {City:"Milan", Country:"Italy", Population:1344000})**
   
    [コントロールの追加、名前付け、構成](../add-configure-controls.md) についてはこちらをご覧ください。
   
    **[ClearCollect](../functions/function-clear-collect-clearcollect.md)** 関数または [その他の関数](../formula-reference.md) については各関連記事を参照してください。
2. F5 キーを押し、ボタンを選択して Esc キーを押します。
3. スライダーを追加し、ボタンの下に移動させて、スライダーに **MinPopulation** と名前を付けます。
4. スライダーの **Max** プロパティを **5000000**、**Min** プロパティを **1000000** に設定します。
5. テキスト ギャラリーを垂直方向 (縦向き) で追加して、スライダーの下に移動し、ギャラリーの **[Items](properties-core.md)** プロパティを次の数式に設定します。<br>
   **Filter(CityPopulations, Population > MinPopulation)**
6. ギャラリーの最初の項目で、上のラベルの **[Text](properties-core.md)** プロパティを **ThisItem.City** に、下のラベルの **[Text](properties-core.md)** プロパティを次の数式に設定します。<br> **Text(ThisItem.Population, "##,###")**
7. F5 キーを押して、**MinPopulation** を調整し、指定した値よりも人口が多い都市のみを表示します。
8. 既定のワークスペースに戻るには、Esc キーを押します。


## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
### <a name="color-contrast"></a>色のコントラスト
次の間には適切な色のコントラストが必要です:
* **ValueFill** および **RailFill**
* **ValueHoverFill** および **RailHoverFill**
* **[FocusedBorderColor](properties-color-border.md)** およびコントロールの外側の色
* **ValueFill** および背景色
* **RailFill** および背景色
* **ValueHoverFill** および背景色
* **RailHoverFill** および背景色

### <a name="screen-reader-support"></a>スクリーン リーダー サポート
* **[AccessibleLabel](properties-accessibility.md)** が存在する必要があります。

### <a name="keyboard-support"></a>キーボードのサポート
* **[TabIndex](properties-accessibility.md)** を 0 以上にして、キーボード ユーザーがそこに移動できるようにする必要があります。
* フォーカス インジケーターは明確に表示する必要があります。 これを実現するには **[FocusedBorderColor](properties-color-border.md)** および **[FocusedBorderThickness](properties-color-border.md)** を使用します。
* キーボードと対話するときに、スライダーの値を表示する必要があります。 これは、次のいずれかの方法で実現できます。
    * **ShowValue** を **true** に設定します。
    * **[ラベル](control-text-box.md)** をスライダーに隣接するように追加します。 スライダーの **[Text](properties-core.md)** にラベルの **[Text](properties-core.md)** を設定します。
