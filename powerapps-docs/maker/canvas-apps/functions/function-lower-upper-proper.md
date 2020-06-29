---
title: Lower、Upper および Proper 関数 | Microsoft Docs
description: Power Apps の Lower、Upper および Proper 関数の構文と例を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 115b5e51f816778d763481999f8f487a1d64037a
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3304935"
---
# <a name="lower-upper-and-proper-functions-in-power-apps"></a>Power Apps の Lower、Upper および Proper 関数
テキストの文字列中の文字をすべて小文字、大文字または適切な文字に変換します。

## <a name="description"></a>内容
**Lower**、**Upper**、および **Proper** 関数は、文字列中の文字の大文字小文字を変換します。

* **Lower** は、すべての大文字を小文字に変換します。
* **Upper** は、すべての小文字を大文字に変換します。
* **Proper** は、各単語の最初の文字が小文字であれば大文字に変換します。また、その他の大文字は小文字に変換します。

これら 3 つの関数では、アルファベットでない文字は無視されます。

単一の文字列を渡した場合、その戻り値は文字列の変換されたバージョンです。  文字列が含まれた単一列[テーブル](../working-with-tables.md)を渡すと、変換された文字列の単一列テーブルが戻り値として返されます。 複数列テーブルがある場合は、[テーブルの使用](../working-with-tables.md) に関するページの説明に従って、そのテーブルを単一列テーブルにすることができます。

## <a name="syntax"></a>構文
**Lower**( *String* )<br>**Upper**( *String* )<br>**Proper**( *String* )

* *String* - 必須。 変換する文字列。

**Lower**( *SingleColumnTable* )<br>**Upper**( *SingleColumnTable* )<br>**Proper**( *SingleColumnTable* )

* *SingleColumnTable* - 必須。 変換する文字列の単一列テーブル。

## <a name="examples"></a>例
### <a name="single-string"></a>単一の文字列
このセクションの例では、**Author** という名前のテキスト入力コントロールを[データ ソース](../working-with-data-sources.md) として使用します。 このコントロールには、文字列 "E が含まれます。 E. CummINGS".

| 計算式 | 内容 | 結果 |
| --- | --- | --- |
| **Lower (&nbsp;Author.Text&nbsp;)** |文字列中のすべての大文字を小文字に変換します。 |"e. e. cummings" |
| **Upper (&nbsp;Author.Text&nbsp;)** |文字列中のすべての小文字を大文字に変換します。 |"E. E. CUMMINGS" |
| **Proper (&nbsp;Author.Text&nbsp;)** |各単語の最初の文字が小文字であれば大文字に変換します。また、その他の大文字の文字を小文字に変換します。 |"E. E. Cummings" |

### <a name="single-column-table"></a>単一列テーブル
このセクションの例では、次のデータが含まれている **People** データ ソースの **住所**[列](../working-with-tables.md#columns) から文字列を変換します。

![](media/function-lower-upper-proper/people-table.png)

それぞれの数式は、変換済みの文字列を含む単一列テーブルを返します。

| 計算式 | 内容 | 結果 |
| --- | --- | --- |
| **Lower( ShowColumns(&nbsp;People,&nbsp;"Address"&nbsp;) )** |小文字の文字をすべて大文字に変換します。 |<style> img { 最大幅: なし; } </style> ![](media/function-lower-upper-proper/people-table-lower.png) |
| **Upper( ShowColumns(&nbsp;People,&nbsp;"Address"&nbsp;) )** |小文字の文字をすべて大文字に変換します。 |![](media/function-lower-upper-proper/people-table-upper.png) |
| **Proper( ShowColumns(&nbsp;People,&nbsp;"Address"&nbsp;) )** |単語の最初の文字が小文字であれば大文字に変換します。また、その他の文字が大文字であれば小文字に変換します。 |![](media/function-lower-upper-proper/people-table-proper.png) |

### <a name="step-by-step-example"></a>手順の例
1. **[テキスト入力](../controls/control-text-input.md)** コントロールを追加し、**ソース**という名前を付けます。
2. ラベルを追加し、その **[Text](../controls/properties-core.md)** プロパティを次の関数に設定します:<br>**Proper(Source.Text)**
3. F5 キーを押し、**WE ARE THE BEST!** と入力します **ソース** ボックスに。<br>ラベルは **We Are The Best!** と表示します

