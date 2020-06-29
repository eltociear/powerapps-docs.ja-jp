---
title: Left、Mid、および Right 関数| Microsoft Docs
description: Power Apps で Left、Mid、および Right 関数の構文と例を含む参照情報
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
ms.sourcegitcommit: 80120b59d440bb7a3ddca93cd51154607f749f6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "3307925"
---
# <a name="left-mid-and-right-functions-in-power-apps"></a>Power Apps の Left、Mid、および Right 関数
テキストの文字列の左、中央、または右部分を抽出します。

## <a name="description"></a>内容
**Left**、**Mid**、および **Right** 関数は、文字列の一部を返します。

* **Left** は、文字列の先頭の文字を返します。
* **Mid** は、文字列の中央の文字を返します。
* **Right** は、文字列の末尾の文字を返します。

単一の文字列を引数として指定した場合、関数は文字列の要求した部分を返します。 文字列が含まれている単一列[テーブル](../working-with-tables.md) を指定した場合、関数は、それらの文字列の要求した部分の単一列テーブルを返します。 複数列テーブルを指定する場合は、[テーブルの使用](../working-with-tables.md) が説明しているように、単一列テーブルにすることができます。

開始位置がが負または文字列の末尾よりも後ろにある場合、**Mid** は*空白*を返します。  文字列の長さは、**[Len](function-len.md)** 関数を使用して確認することができます。 文字列が含むまれるより多くの文字を要求する場合、関数はできるだけ多くの文字を返します。

## <a name="syntax"></a>構文
**Left**( *String*, *NumberOfCharacters* )<br>**Mid**( *String*, *StartingPosition* [, *NumberOfCharacters* ] )<br>**Right**( *String*, *NumberOfCharacters* )

* *String* - 必須。 結果の抽出元の文字列。
* *StartingPosition* - 必須 (**Mid** のみ)。  開始位置。  文字列の先頭文字の位置は 1 です。
* *NumberOfCharacters* - 必須 (**Left** および **Right** のみ)。  返す文字の数。  **Mid** 関数で省略した場合は、関数は開始位置から文字列の末尾までを返します。

**Left** ( *SingleColumnTable*、 *NumberOfCharacters* )<br>**Mid** ( *SingleColumnTable*、 *StartingPosition* [、 *NumberOfCharacters* ] )<br>**Right** ( *SingleColumnTable*、 *NumberOfCharacters* )

* *SingleColumnTable* - 必須。 結果の抽出元となる文字列の単一列テーブル。
* *StartingPosition* - 必須 (**Mid** のみ)。  開始位置。  文字列の先頭文字の位置は 1 です。
* *NumberOfCharacters* - 必須 (**Left** および **Right** のみ)。  返す文字の数。  **Mid** 関数で省略した場合は、関数は開始位置から文字列の末尾までを返します。

## <a name="examples"></a>例
### <a name="single-string"></a>単一の文字列
このセクションの例では、テキスト入力コントロールを[データ ソース](../working-with-data-sources.md) として使用します。 コントロールは **Author** という名前がつけられ、文字列 "E を含みます。 E. Cummings".

| 計算式 | 内容 | 結果 |
| --- | --- | --- |
| **Left( Author.Text, 5 )** |文字列の先頭から最大 5 文字を抽出します。 |"E. E." |
| **Mid( Author.Text, 7, 4 )** |文字列から、7 番目の文字で始まる最大 4 文字を抽出します。 |「Cumm」 |
| **Mid( Author.Text, 7 )** |文字列から、7 番目の文字で始まるすべての文字を抽出します。 |「Cummings」 |
| **Right( Author.Text, 5 )** |文字列の末尾から最大 5 文字を抽出します。 |「mings」 |

### <a name="single-column-table"></a>単一列テーブル
このセクションの各例では、**ユーザー**という名前がつけられたこのデータ ソースの**住所**[列](../working-with-tables.md#columns) から文字列が抽出し、その結果を含む単一列テーブルが返されます:

![](media/function-left-mid-right/people-table.png)

| 計算式 | 内容 | 結果 |
| --- | --- | --- |
| **Left( ShowColumns(&nbsp;People,&nbsp;"Address"&nbsp;), 8 )** |各文字列の先頭の 8 文字を抽出します。 |<style> img { 最大幅: なし } </style> ![](media/function-left-mid-right/people-table-left.png) |
| **Mid( ShowColumns(&nbsp;People,&nbsp;"Address"&nbsp;), 5, 7 )** |5 番目の文字で始まる、各文字列の中央の 7 文字を抽出します。 |![](media/function-left-mid-right/people-table-mid.png) |
| **Right( ShowColumns(&nbsp;People,&nbsp;"Address"&nbsp;), 7 )** |各文字列の最後の 7 文字を抽出します。 |![](media/function-left-mid-right/people-table-right.png) |

### <a name="step-by-step-example"></a>手順の例
1. **在庫**という名前の[コレクション](../working-with-data-sources.md#collections) をインポートまたは作成し、[ギャラリーでのイメージとテキストの表示](../show-images-text-gallery-sort-filter.md) で説明している最初の手順に従って、それをギャラリーに表示します。
2. ギャラリーにある下のラベルの**[Text](../controls/properties-core.md)** プロパティを、次の関数に設定します:
   
    **Right(ThisItem.ProductName, 3)**
   
    ラベルは、各製品名の最後の 3 文字を表示します。

