---
title: Blank、Coalesce、IsBlank、および IsEmpty 関数 | Microsoft Docs
description: Power Apps での Blank、Coalesce、IsBlank、および IsEmpty 関数の構文と例を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.component: canvas
ms.date: 08/27/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 59314375b68a73e4c46bd3274a3fefc994465b4d
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3305027"
---
# <a name="blank-coalesce-isblank-and-isempty-functions-in-power-apps"></a>Power Apps での Blank、Coalesce、IsBlank、および IsEmpty 関数
値が空白であるかどうか、または [テーブル](../working-with-tables.md) に [レコード](../working-with-tables.md#records) が含まれていないかどうかをテストし、*空白*の値を作成する方法を提供します。

## <a name="overview"></a>概要
*空白*は、"値がない" または "不明な値" のプレースホルダーです  たとえば、ユーザーが選択を行なっていない場合、**[コンボ ボックス](../controls/control-combo-box.md)** コントロールの **Selected** プロパティは*空白*です。 多くのデータ ソースは、Power Apps で*空白*として表される NULL 値 を保存し、返すことができます。

Power Apps のプロパティまたは計算された値はいずれも、*空白*にすることができます。  たとえば、ブール値には通常、**true** または **false** という 2 つの値のいずれかがあります。  しかし、これら 2 つに加えて、状態が確定してないことを示す*空白*にもすることができます。  ワークシート セル は内容を含まない空白として開始しますが、(とりわけ) **TRUE** または **FALSE** の値を保持することができる Microsoft Excel に似ています。 どの時点でも、セルの内容は消去でき、*空白*状態に返すことができます。

*空の文字列*は文字を含まない文字列を意味します。  [**Len** 関数](function-len.md) はこのような文字列のゼロを返し、`""` の間に何もない 2 つの二重引用符として数式に書き込むことができます。  一部のコントロールおよびデータ ソースは、空の文字列を使用して "値なし" の条件を示します。  アプリの作成を簡素化するために、**IsBlank** および **Coalesce** 関数は*空白*値または空の文字列の両方をテストします。    

**IsEmpty** 関数のコンテキストでは、*空*はレコードを含まないテーブルに固有です。 テーブルの構造はそのままで、[列](../working-with-tables.md#columns) の名前を付けて完了している場合がありますが、テーブルにはデータがありません。 テーブルは空として開始され、レコードを取り入れるともう空ではなくなり、次にレコードを削除して再度空にすることができます。

> [!NOTE]
> 切り替えの期間にいます。  これまでは、*空白*を使用してエラーをレポートし、エラーから有効な "値なし" を区別することができませんでした。  このため、現時点で、*空白*値の格納は、ローカル コレクションでのみサポートされています。  ファイル メニュー、アプリの設定、詳細の設定、実験機能の "数式レベルのエラー管理" 実験機能をオンにすると*空白*値を他のデータ ソースに格納できます。  この機能を完了し、およびエラーからの*空白*値の適切な分離を完了することに積極的に取り組んでいます。

## <a name="description"></a>内容
**Blank** 関数は、*空白*値を返します。 これを使用して、これらの値をサポートするデータ ソースに NULL 値を格納し、フィールドから値を効果的に削除します。

**IsBlank** 関数は、*空白*値または空の文字列をテストします。  値が存在しない場合に一部のデータ ソースおよびコントロールが空の文字列を使用するため、テストには、アプリの作成を簡素化する空の文字列が含まれます。  特に*空白*値をテストするには **IsBlank** の代わりに `if( Value = Blank(), ...` を使用します。

**Coalesce** 関数はその引数を順番に評価し、*空白*または空の文字列ではない最初の値を返します。  この関数を使用して、*空白*値または空の文字列を別の値に置換えますが、*空白*でない、および空でない文字列の値は変更しない状態にしておきます。  すべての引数が*空白*または空の文字列の場合、関数は*空白*を返し、**Coalesce** が空の文字列を*空白*値に変換する適切な方法であるようにします。  **Coalesce** のすべての引数は同じ種類である必要があり、たとえば、数値とテキスト文字列を組み合わせることはできません。  

`Coalesce( value1, value2 )` は、`If( Not IsBlank( value1 ), value1, Not IsBlank( value2 ), value2 )` のより簡潔な同等物であり、**value1** および **value2** が 2 回評価される必要はありません。  ここにあるように "その他" の数式がない場合 、[**If** 関数](function-if.md) は*空白*を返します。

**IsEmpty** 関数は、テーブルにレコードが含まれているかどうかをテストします。 これは、**[CountRows](function-table-counts.md)** 関数を使用してゼロを確認するのと同等です。 **IsEmpty** と **[Errors](function-errors.md)** 関数を組み合わせることにより、データ ソース エラーを検査できます。

**IsBlank** および **IsEmpty** 両方の戻り値は、ブール値である **true** または **false** です。

## <a name="syntax"></a>構文
**Blank**()

**Coalesce**( *Value1* [, *Value2*, ... ] )

* *Value(s)* – 必須。 テストする値。  各値は、*空白*でない、および空の文字列でない値が見つかるまで、順番に評価されます。  このポイント以降の値は評価されません。  

**IsBlank**( *Value* )

* *Value* – 必須。 *空白*値または空の文字列をテストをする値。

**IsEmpty**( *Table* )

* *Table* - 必須。 レコードをテストするテーブル。

## <a name="examples"></a>例
### <a name="blank"></a>Blank
> [!NOTE]
> 現時点で、次の例はローカル コレクションでのみ機能します。  ファイル メニュー、アプリの設定、詳細の設定、実験機能の "数式レベルのエラー管理" 実験機能をオンにすると*空白*値を他のデータ ソースに格納できます。  この機能を完了し、およびエラーからの*空白*値の分離を完了することに積極的に取り組んでいます。

1. アプリを最初から作成し、**Button** コントロールを追加します。
2. ボタンの **[OnSelect](../controls/properties-core.md)** プロパティを次の数式に設定します。

    ```powerapps-dot
    ClearCollect( Cities, { Name: "Seattle", Weather: "Rainy" } )
    ```
3. アプリをプレビューし、追加したボタンをクリックまたはタップして、プレビューを閉じます。  
4. **ファイル** メニューで**コレクション**をクリックまたはタップします。

     **市区町村**コレクションが表示され、"シアトル" および "雨" の 1 つのレコードが表示されます。

    ![雨の天気とシアトルを表示するコレクション](./media/function-isblank-isempty/seattle-rainy.png)
5. 後ろ向きの矢印をクリックまたはタップして、既定のワークスペースに戻ります。
6. **Label** コントロールを追加し、その **Text** プロパティを次の数式に設定します。

    ```powerapps-dot
    IsBlank( First( Cities ).Weather )
    ```

    **天気** フィールドに値 ("雨") が含まれているため、ラベルには **false** と表示されます。
7. 2 つ目のボタンを追加し、その **OnSelect** プロパティを次の数式に設定します。

    ```powerapps-dot
    Patch( Cities, First( Cities ), { Weather: Blank() } )
    ```
8. アプリをプレビューし、追加したボタンをクリックまたはタップして、プレビューを閉じます。  

    **市区町村**の最初のレコードの**天気**フィールドは*空白*に置き換えられ、以前あった "雨" は削除されます。

    ![空白の天気のフィールドとシアトルを表示しているコレクション](./media/function-isblank-isempty/seattle-blank.png)

    **天気**フィールドには値が含まれていないため、ラベルには **true** と表示されます。

### <a name="coalesce"></a>Coalesce

| 計算式 | 内容 | 結果 |
| --- | --- | --- |
| **Coalesce(&nbsp;Blank(),&nbsp;1&nbsp;)** |常に*空白*値を返す **Blank** 関数から戻り値をテストします。 最初の引数が*空白*であるため、*空白*でない値および空でない文字列が見つかるまで、評価は次の引数で続行されます。 |**1** |
| **Coalesce( "", 2 )** |空の文字列である最初の引数をテストします。 最初の引数が空の引数であるため、*空白*でない値および空でない文字列が見つかるまで、評価は次の引数で続行されます。 |**2** |
| **Coalesce( Blank(), "", Blank(), "", 3, 4 )** |**Coalesce** は、引数リストの先頭で開始し、*空白*でない値および空でない文字列が見つかるまで、各引数を次々に評価します。  この場合は、最初の 4 つの引数はすべて*空白*または空の文字列を返すため、評価は 5 番目の引数に続きます。 5 番目の引数は*空白*でないおよび空でない文字列なので、評価はここで停止します。 5 番目の引数の値が返され、6 番目の引数は評価されません。 |**3** |
| **Coalesce( "" )** | 空の文字列である最初の引数をテストします。 最初の引数が空の文字列であり、これ以上引数がないため、関数は*空白*を返します。   |*空白* |

### <a name="isblank"></a>IsBlank
1. アプリを最初から作成し、テキスト入力コントロールを追加して **FirstName** という名前を付けます。
2. ラベルを追加し、その **[Text](../controls/properties-core.md)** プロパティを次の数式に設定します。

    ```powerapps-dot
    If( IsBlank( FirstName.Text ), "First Name is a required field." )
    ```

    既定では、テキスト入力コントロールの **[Text](../controls/properties-core.md)** プロパティは **"テキスト入力"** に設定されています。 プロパティには値が含まれており、空白ではないため、ラベルにはメッセージが表示されません。
3. テキスト入力コントロールから、スペースを含めたすべての文字を削除します。

    **[Text](../controls/properties-core.md)** プロパティには文字が含まれなくなったため、空の文字列であり **IsBlank( FirstName.Text )** は **true** になります。 必須フィールドのメッセージが表示されます。

他のツールを使用して検証を実行する方法については、**[Validate](function-validate.md)** 関数および [データ ソースの操作](../working-with-data-sources.md) を参照してください。  

その他の例:

| 計算式 | 内容 | 結果 |
| --- | --- | --- |
| **IsBlank(&nbsp;Blank()&nbsp;)** |常に*空白*値を返す **Blank** 関数から戻り値をテストします。 |**True** |
| **IsBlank( "" )** |文字が含まれていない文字列。 |**True** |
| **IsBlank( "Hello" )** |1 つ以上の文字が含まれている文字列。 |**false** |
| **IsBlank( *AnyCollection* )** |レコードが含まれていなくても、[コレクション](../working-with-data-sources.md#collections) が存在するため、空白ではありません。 空のコレクションを検査するには、代わりに **IsEmpty** を使用します。 |**false** |
| **IsBlank( Mid( "Hello", 17, 2 ) )** |**[Mid](function-left-mid-right.md)** の開始文字は文字列の末尾よりも後ろにあります。  結果は、空の文字列です。 |**True** |
| **IsBlank( If( false, false ) )** |*ElseResult* がない **[If](function-if.md)** 関数。  条件が常に **false** になるため、この **[If](function-if.md)** は常に*空白*を返します。 |**True** |

### <a name="isempty"></a>IsEmpty
1. アプリを最初から作成し、**Button** コントロールを追加します。
2. ボタンの **[OnSelect](../controls/properties-core.md)** プロパティを次の数式に設定します。

    **Collect( IceCream, { Flavor: "Strawberry", Quantity: 300 }, { Flavor: "Chocolate", Quantity: 100 } )**
3. アプリをプレビューし、追加したボタンをクリックまたはタップして、プレビューを閉じます。  

    **IceCream** という名前のコレクションが作成され次のデータが含まれます。

    ![](media/function-isblank-isempty/icecream-strawberry-chocolate.png)

    このコレクションに 2 つのレコードは含まれ、空ではありません。 **IsEmpty( IceCream )** は **false** を返し、および **CountRows( IceCream )** は **2** を返します。
4. 2 つ目のボタンを追加し、その **[OnSelect](../controls/properties-core.md)** プロパティを次の数式に設定します。

    **Clear( IceCream )**
5. アプリをプレビューし、2 つ目のボタンをクリックまたはタップして、次にプレビューを閉じます。  

    これで、コレクションは空になりました。

    ![](media/function-isblank-isempty/icecream-clear.png)

    **[Clear](function-clear-collect-clearcollect.md)** 関数はコレクションからすべてのレコードを削除し、その場合は空のコレクションになります。 **IsEmpty( IceCream )** は **true** を返し、および **CountRows( IceCream )** は **0** を返します。

以下の例のように、**IsEmpty** を使用して、計算されたテーブルが空かどうかをテストすることもできます。

| 計算式 | 内容 | 結果 |
| --- | --- | --- |
| **IsEmpty( [&nbsp;1,&nbsp;2,&nbsp;3 ] )** |単一列テーブルに 3 つのレコードが含まれており、したがって、空ではありません。 |**false** |
| **IsEmpty( [&nbsp;] )** |単一列テーブルにはレコードが含まれず、空です。 |**True** |
| **IsEmpty( Filter( [&nbsp;1,&nbsp;2,&nbsp;3&nbsp;], Value > 5 ) )** |単一列テーブルに 5 より大きい値が含まれていません。  フィルターからの結果にはレコードが含まれておらず、空です。 |**True** |

