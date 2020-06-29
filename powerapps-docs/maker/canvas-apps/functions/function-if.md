---
title: If および Switch 関数 | Microsoft Docs
description: Power Apps での If および Switch 関数の構文と例を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/24/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 07924ea46dd0914fbeaf5d0fef24bb3cdc543d6c
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3305073"
---
# <a name="if-and-switch-functions-in-power-apps"></a>Power Apps での If および Switch 関数
セット内の条件が true かどうか (**If**)、または数式の結果がセット内の任意の値に一致するかどうか (**Switch**)を指定し、次に結果を返す、またはアクションを実行します。

## <a name="description"></a>内容
**If** 関数は、**true** の結果が見つかるまで、1 つ以上の条件をテストします。 そのような結果が見つかった場合は、対応する値が返されます。 そのような結果が見つからない場合は、既定値が返されます。 いずれの場合も、返される値は、表示する文字列、評価する数式、または別のフォームの結果となります。

**Switch** 関数は、数式を評価し、結果が指定したシーケンス内の任意の値に一致するかどうかを指定します。 一致が見つかった場合は、対応する値が返されます。 一致が見つからない場合は、既定値が返されます。 いずれの場合も、返される値は、表示する文字列、評価する数式、または別のフォームの結果となります。

**If** および **Switch** はよく似ていますが、状況に合わせて最適な関数を使用する必要があります。

* 1 つの条件を評価するには、**If** を使用します。 この関数の最も一般的な構文は、**If**( *Condition*, *ThenResult*, *DefaultResult* ) で、一般的な “if … を提供します  then … else …” 他のプログラミング ツールで見られるパターン。
* 複数の無関係な条件を評価するには、**If** を使用します。 Power Apps では (Microsoft Excel とは異なり)、**If** の数式を入れ子にすることなく、複数の条件を指定できます。
* 複数の可能な一致に対して1 つの条件を評価するには、**Switch** を使用します。 この場合 **If** を使用することもできますが、それぞれの一致する可能性がある数式を繰り返す必要があります。

これらの関数は両方とも、2 つ以上のアクション間で分岐するために、[動作の数式](../working-with-formulas-in-depth.md) で使用できます。 アクションをトリガーする分岐は 1 つだけです。 条件および一致が順番に評価され、条件が **true** または一致が見つかった場合は停止します。

どの条件も **true**ではなく、どの一致も見つからない、および既定の結果を指定しない場合は、*空白*が返されます。

## <a name="syntax"></a>構文
**If**( *Condition*, *ThenResult* [, *DefaultResult* ] )<br>**If**( *Condition1*, *ThenResult1* [, *Condition2*, *ThenResult2*, ... [ , *DefaultResult* ] ] )

* *Condition(s)* - 必須。 **true** をテストする数式。 これらの数式には、一般的に、比較[演算子](operators.md) (**<**、**>**、**=** など)、および **[IsBlank](function-isblank-isempty.md)**、**[IsEmpty](function-isblank-isempty.md)** などのテスト関数が含まれています。
* *ThenResult(s)* - 必須。 **true** と評価される条件に対して返される対応する値。
* *DefaultResult* - オプション。 **true** と評価される条件がない場合に返される値。  この引数を指定しない場合は、*空白*が返されます。

**Switch**( *Formula*, *Match1*, *Result1* [, *Match2*, *Result2*, ... [, *DefaultResult* ] ] )

* *Formula* - 必須。 一致を評価する数式。  この数式は、1 回だけ評価されます。
* *Match(s)* - 必須。 *Formula* の結果と比較する値。  完全一致が見つかった場合、対応する *Result* が返されます。
* *Result(s)* - 必須。 完全一致が見つかった場合に返される対応する値。
* *DefaultResult* - オプション。 完全一致が見つからない場合は、この値が返されます。 この引数を指定しない場合は、*空白*が返されます。

## <a name="examples"></a>例
### <a name="values-in-formulas"></a>数式の値
次の例では、**Slider** コントロール (**Slider1** という名前) に **25** の値が設定されています。

| 計算式 | 内容 | 結果 |
| --- | --- | --- |
| **If( Slider1.Value&nbsp;=&nbsp;25, "Result1" )** |条件は **true** で、対応する結果が返されます。 |"Result1" |
| **If( Slider1.Value&nbsp;=&nbsp;25, "Result1", "Result2" )** |条件は **true** で、対応する結果が返されます。 |"Result1" |
| **If( Slider1.Value&nbsp;>&nbsp;1000, "Result1" )** |条件は **false** で、*DefaultResult* が指定されていません。 |*空白* |
| **If( Slider1.Value&nbsp;>&nbsp;1000, "Result1", "Result2" )** |条件は **false** で、*DefaultResult* が指定され、それが返されます。 |"Result2" |
| **If( Slider1.Value&nbsp;=&nbsp;25, "Result1", Slider1.Value&nbsp;>&nbsp;0, "Result2" )** |1 つ目の条件は **true** で、対応する結果が返されます。 2 つ目の条件も **true** ですが、**true** と評価される条件よりも後に引数リストに表示されるため、評価されません。 |"Result1" |
| **If( IsBlank(&nbsp;Slider1.Value&nbsp;), "Result1", IsNumeric(&nbsp;Slider1.Value&nbsp;), "Result2" )** |スライダーが *空白* ではないため、1 つ目の条件は **false** です。 スライダーの値は数値であるため、2 つ目の条件は **true** になり、対応する結果が返されます。 |"Result2" |
| **If( Slider1.Value&nbsp;>&nbsp;1000, "Result1", Slider1.Value&nbsp;>&nbsp;50, "Result2", "Result3")** |1 つ目と 2 つ目の条件の両方とも **false** であり、*DefaultResult* が指定されて返されます。 |"Result3" |
| **Switch( Slider1.Value, 25, "Result1" )** |スライダーの値は、チェックされる 1 つ目の値と一致し、対応する結果が返されます。 |"Result1" |
| **Switch( Slider1.Value, 20, "Result1", 25, "Result2", 30, "Result3" )** |スライダーの値は、チェックされる 2 つ目の値と一致し、対応する結果が返されます。 |"Result2" |
| **Switch( Slider1.Value, 20, "Result1", 10, "Result2", 0, "Result3", "DefaultResult" )** |スライダーの値は、チェックされるどの値とも一致しません。  *DefaultResult* が指定されているので、返されます。 |"DefaultResult" |

### <a name="branching-in-behavior-formulas"></a>動作の数式の分岐
次の例では、**FirstName** という名前の**[テキスト入力](../controls/control-text-input.md)** コントロールに "John" の値が入力されています。

| 計算式 | 内容 | 結果 |
| --- | --- | --- |
| **If( ! IsBlank( FirstName.Text ), Navigate(&nbsp;Screen1, ScreenTransition.None ) )** |条件は **true** なので、**[Navigate](function-navigate.md)** 関数が実行されます。 **[IsBlank](function-isblank-isempty.md)** 関数を使用して、必要なフォーム フィールドが入力されたかどうかをテストすることができます。  **FirstName** が[空白](function-isblank-isempty.md) だった場合、この数式は無効になります。 |**True**<br><br>表示が **Screen1** に変更されます。 |
| **If( IsBlank( FirstName.Text ), Navigate(&nbsp;Screen1, ScreenTransition.None ), Back() )** |**!** なし 演算子、条件は **false** で、**[Navigate](function-navigate.md)** 関数は実行されません。 **[Back](function-navigate.md)** 関数が *DefaultResult* として指定され、実行します。 |**True**<br><br>表示は、前に表示されていたスクリーンに戻ります。 |
| **Switch( FirstName.Text, "Carlos", Navigate(&nbsp;Screen1, ScreenTransition.None ), "Kirstin", Navigate( Screen2, ScreenTransition.None ), "John", Navigate( Screen3, ScreenTransition.None ) )** |**FirstName.Text** の値は "Carlos"、"Kirstin"、および "John" というその順序で比較されます。 "John" との一致が見つかり、アプリは **Screen3** に移動します。 |**True**<br><br>表示が **Screen3** に変更されます。 |

### <a name="step-by-step"></a>手順
1. **[テキスト入力](../controls/control-text-input.md)** コントロールを追加し、既定でその名前が付いていない場合は、**Text1** という名前を付けます。
2. **Text1** に **30** と入力します。
3. **Label** コントロールを追加し、その **[Text](../controls/properties-core.md)** プロパティを次の数式に設定します。<br>
   **If( Value(Text1.Text) < 20, "Order MANY more!", Value(Text1.Text) < 40, "Order more!", Text1.Text )**
   
    **Label** コントロールに**受注必要!** と表示されます **Text1** の値が 20 より大きく 40 より小さいためです。
4. **Text1** に **15** と入力します。
   
    **Label** コントロールに**受注多数必要!** と表示されます **Text1** の値が 20 より小さいためです。
5. **Text1** に **50** と入力します。
   
    **ラベル** コントロールは、入力した値が 40 を超えているため表示されます。

