---
title: Left 関数、Mid 関数、Right 関数 | Microsoft Docs
description: 構文と例を含む、Power Apps の左、中、右の関数の参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 02/07/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 2a8f89dff09d34d7492f325f54f73c4c736adc24
ms.sourcegitcommit: ee1960fe32136a621e653d6ff2f13d87017830a2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77145416"
---
# <a name="left-mid-and-right-functions-in-power-apps"></a>Power Apps の Left、Mid、Right の各関数
テキストの文字列から左側部分、中間部分、または右側部分を抽出します。

## <a name="description"></a>説明
**Left** 関数、**Mid** 関数、**Right** 関数は、文字列の一部を返します。

* **Left** 関数は、文字列の先頭部分の文字を返します。
* **Mid** 関数は、文字列の中間部分の文字を返します。
* **Right** 関数は、文字列の末尾部分の文字を返します。

1 つの文字列を引数として指定した場合、上記の関数は文字列の要求された部分を返します。 文字列が含まれている単一列[テーブル](../working-with-tables.md)を指定した場合、この関数は、それらの文字列の要求された部分を単一列テーブルとして返します。 複数列テーブルを指定する場合は、[テーブルの使用](../working-with-tables.md)に関するページの説明に従って、そのテーブルを単一列テーブルにすることができます。

起点が負であったり、文字列の末尾よりも後ろであったりすると、**Mid** は "*空*" を返します。  文字列の長さは、 **[Len](function-len.md)** 関数を使用して確認することができます。 要求された文字の数が文字列の文字数よりも多い場合、関数はできるだけ多くの文字を返します。

## <a name="syntax"></a>構文
**Left**( *String*, *NumberOfCharacters* )<br>**Mid**( *String*, *StartingPosition* [, *numberofcharacters* ])<br>**Right**( *String*, *NumberOfCharacters* )

* *String* - 必須。 結果の抽出元となる文字列。
* *StartingPosition* - 必須 (**Mid** のみ)。  起点。  文字列の先頭にある文字の位置が 1 になります。
* *Numberofcharacters* -必須 (**左**および**右**のみ)。  返す文字数。  **Mid**関数で省略した場合、関数は、開始位置から文字列の末尾までの部分を返します。

**Left**( *SingleColumnTable*, *NumberOfCharacters* )<br>**Mid**( *SingleColumnTable*、 *StartingPosition* [、 *numberofcharacters* ])<br>**Right**( *SingleColumnTable*, *NumberOfCharacters* )

* *SingleColumnTable* - 必須。 結果の抽出元となる文字列が含まれている単一列テーブル。
* *StartingPosition* - 必須 (**Mid** のみ)。  起点。  文字列の先頭にある文字の位置が 1 になります。
* *Numberofcharacters* -必須 (**左**および**右**のみ)。  返す文字数。  **Mid**関数で省略した場合、関数は、開始位置から文字列の末尾までの部分を返します。

## <a name="examples"></a>使用例
### <a name="single-string"></a>単一の文字列
このセクションの例では、テキスト入力コントロールを[データ ソース](../working-with-data-sources.md)として使用します。 **Author** という名前のこのコントロールには、文字列 "E. E. Cummings" が含まれています。

| [数式] | 説明 | 結果 |
| --- | --- | --- |
| **Left( Author.Text, 5 )** |文字列の先頭の 5 文字を抽出します。 |"E. E." |
| **Mid( Author.Text, 7, 4 )** |7 番目の文字を起点として、文字列から 4 つの文字を抽出します。 |"Cumm" |
| **Mid (執筆者、7)** |文字列から7番目の文字で始まるすべての文字を抽出します。 |"Cummings" |
| **Right( Author.Text, 5 )** |文字列の末尾の 5 文字を抽出します。 |"mings" |

### <a name="single-column-table"></a>単一列テーブル
このセクションの各例では、このデータソースの**Address** [列](../working-with-tables.md#columns)から**People**という名前の文字列を抽出し、結果を含む単一列テーブルを返します。

![](media/function-left-mid-right/people-table.png)

| [数式] | 説明 | 結果 |
| --- | --- | --- |
| **Left( ShowColumns(&nbsp;People,&nbsp;"Address"&nbsp;), 8 )** |各文字列の先頭の 8 文字を抽出します。 |<style>img {max width: none}</style> ![](media/function-left-mid-right/people-table-left.png) |
| **Mid( ShowColumns(&nbsp;People,&nbsp;"Address"&nbsp;), 5, 7 )** |5 番目の文字を起点として、各文字列中の 7 文字を抽出します。 |![](media/function-left-mid-right/people-table-mid.png) |
| **Right( ShowColumns(&nbsp;People,&nbsp;"Address"&nbsp;), 7 )** |各文字列の末尾の 7 文字を抽出します。 |![](media/function-left-mid-right/people-table-right.png) |

### <a name="step-by-step-example"></a>ステップバイステップの例
1. [Inventory](../working-with-data-sources.md#collections) という名前の**コレクション**をインポートするか作成し、[ギャラリーでのイメージとテキストの表示](../show-images-text-gallery-sort-filter.md)に関する記事の最初の手順に従って、それをギャラリーに表示します。
2. ギャラリー内にある下のラベルの **[Text](../controls/properties-core.md)** プロパティに、次の関数を設定します。
   
    **Right(ThisItem.ProductName, 3)**
   
    ラベルには、各製品名の末尾の 3 文字が表示されます。

