---
title: '評価コントロール: リファレンス | Microsoft Docs'
description: プロパティとサンプルを含む、評価コントロールに関する情報
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
ms.openlocfilehash: a5e91f8ff3b760e173ac01b32a68c7f60a488014
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3305970"
---
# <a name="rating-control-in-power-apps"></a>Power Apps での評価コントロール
ユーザーが 1 から指定する最大数までの値を示すことができるコントロール。

## <a name="description"></a>内容
たとえば、このコントロールでは、ユーザーが何かをどの程度気に入ったかを特定数の星を選択して示すことができます。

## <a name="key-properties"></a>主要なプロパティ
**[Default](properties-core.md)** – ユーザーが変更する前のコントロールの初期値です。

**Max** – ユーザーがスライダーまたは評価を設定できる最大値です。

## <a name="additional-properties"></a>追加のプロパティ
**[AccessibleLabel](properties-accessibility.md)** – スクリーン リーダー用のラベル。

**[BorderColor](properties-color-border.md)** – コントロールの境界線の色。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線が**実線**、**破線**、**点線**、または**なし**かどうか。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さ。

**[DisplayMode](properties-core.md)** – コントロールがユーザー入力を許可するか (**編集**)、データのみを表示するか (**表示**)、または無効にするか (**無効**) どうか。

**[塗りつぶし](properties-color-border.md)** – コントロールの背景色。

**[FocusedBorderColor](properties-color-border.md)** – コントロールがフォーカスされているときのコントロールの境界線の色。

**[FocusedBorderThickness](properties-color-border.md)** – コントロールがフォーカスされているときのコントロールの境界線の太さ。

**[高さ](properties-size-location.md)** – コントロールの上端と下端間の距離。

**[OnChange](properties-core.md)** – ユーザーが (たとえば、スライダーを調整するなどして) コントロールの値を変更した場合のアプリの反応を指定します。

**[OnSelect](properties-core.md)** – ユーザーがコントロールをタップまたはクリックする場合のアプリの反応方法。

**RatingFill** – 評価コントロールの星の色。

**ReadOnly** – ユーザーがスライダーまたは評価コントロールの値を変更できるかどうかを指定します。

**[Reset](properties-core.md)** – コントロールを既定値に戻すかどうかを指定します。

**ShowValue** – ユーザーがスライダーまたは評価の値を変更するか、ポインタをコントロールに合わせたときにその値を表示するかどうかを指定します。

**[TabIndex](properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序。

**[ツールヒント](properties-core.md)** – ユーザーがコントロールにカーソルを置くときに表示される説明テキスト。

**[表示](properties-core.md)** – コントロールが表示されるか非表示になるか。

**[幅](properties-size-location.md)** – コントロールの左端と右端間の距離。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離。

## <a name="related-functions"></a>関連する関数
[**Average**( *Value1*, *Value2,* ... )](../functions/function-aggregates.md)

## <a name="example"></a>例
1. **評価**コントロールを追加して **Quantitative** という名前を付けます。
   
    [コントロールの追加、名前付け、構成](../add-configure-controls.md) についてはこちらをご覧ください。
2. **[テキスト入力](control-text-input.md)** コントロールを追加し、**質的**という名前を付け、**評価**コントロールの下に移動します。
3. **[テキスト入力](control-text-input.md)** コントロールの **[既定](properties-core.md)** プロパティを **""** に設定し、その **HintText** を次の数式に設定します:
   <br>**If(Quantitative.Value > 3, "何が特に気に入りましたか?", "何かご意見がおありですか?")**
   
    **[If](../functions/function-if.md)** 関数または [その他の関数](../formula-reference.md) の詳細については各関連記事を参照してください。
4. F5 キーを押してから、**評価**コントロールの 4 または 5 つの星をクリックまたはタップします。
   
    **[テキスト入力](control-text-input.md)** コントロールのヒント テキストが、高評価を反映して変更されます。
5. **量的**で 4 つより少ない星をクリックまたはタップします。
   
    **[テキスト入力](control-text-input.md)** コントロールのヒント テキストが、低評価を反映して変更されます。
6. 既定のワークスペースに戻るには、Esc キーを押します。


## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
### <a name="color-contrast"></a>色のコントラスト
次の間には適切な色のコントラストが必要です:
* **RatingFill** と **[塗りつぶし](properties-color-border.md)**

これは、[標準の色のコントラスト要件](../accessible-apps-color.md) に追加されるものです。

### <a name="screen-reader-support"></a>スクリーン リーダー サポート
* **[AccessibleLabel](properties-accessibility.md)** が存在する必要があります。

    > [!NOTE]
  > スクリーン リーダーは、**評価**コントロールをラジオ ボタンとして扱います。

### <a name="keyboard-support"></a>キーボードのサポート
* **[TabIndex](properties-accessibility.md)** を 0 以上にして、キーボード ユーザーがそこに移動できるようにする必要があります。
* フォーカス インジケーターは明確に表示する必要があります。 これを実現するには **[FocusedBorderColor](properties-color-border.md)** および **[FocusedBorderThickness](properties-color-border.md)** を使用します。
* 星が多すぎる場合は、別のコントロールの使用を検討してください。 キーボードを使用した移動は面倒な場合があり、タッチ スクリーンで正確に選択するのは難しい可能性があります。

    > [!NOTE]
  > ラジオ ボタンに対するのと同じキーボード操作を**評価**に対して使用できます。
