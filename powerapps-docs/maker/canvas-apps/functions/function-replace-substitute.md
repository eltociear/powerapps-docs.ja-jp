---
title: Replace および Substitute 関数 | Microsoft Docs
description: 構文を含む Power Apps の Replace および Substitute 関数の参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/02/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d58d215e4c075ce6948aa442e7fd74e250ea8d1e
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3304728"
---
# <a name="replace-and-substitute-functions-in-power-apps"></a>Power Apps の Replace および Substitute 関数
テキストの文字列の一部を別の文字列に置換します。

## <a name="description"></a>内容
**Replace** 関数は、開始位置と長さによって、置換するテキストを識別します。  

**Substitute** 関数は、文字列を照合することで、置換するテキストを識別します。 複数の一致が見つかった場合、それらすべてを置き換えるか、または置き換えるものを指定できます。

1 つの文字列を渡すと、変更された文字列が戻り値として返されます。 文字列を含む単一列 [テーブル](../working-with-tables.md) を渡すと、変更された文字列の単一列テーブルが戻り値として返されます。 複数列テーブルがある場合は、[テーブルの使用](../working-with-tables.md) に関するページの説明に従って、そのテーブルを単一列テーブルにすることができます。

## <a name="syntax"></a>構文
**Replace**( *String*, *StartingPosition*, *NumberOfCharacters*, *NewString* )

* *String* - 必須。 操作の対象となる文字列。
* *StartingPosition* - 必須。 置換を開始する文字の位置。 *String* の最初の文字の位置は 1 です。
* *NumberOfCharacters* - 必須。 *String* で置換する文字の数。
* *NewString* - 必須。 置換後の文字列。 この引数の文字数は、*NumberOfCharacters* 引数とは異なっていてもかまいません。

**Substitute**( *String*, *OldString*, *NewString* [, *InstanceNumber* ] )

* *String* - 必須。 操作の対象となる文字列。
* *OldString* - 必須。 置換の対象となる文字列。
* *NewString* - 必須。 置換後の文字列。 *OldString* と *NewString* の長さは異なっていてもかまいません。
* *InstanceNumber* - 省略可能。 *String* に複数のインスタンスが含まれている場合、この引数を使用して *OldString* のどのインスタンスを置換するか指定します。 この引数を指定しない場合、すべてのインスタンスが置き換えられます。

**Replace**( *SingleColumnTable*, *StartingPosition*, *NumberOfCharacters*, *NewString* )

* *SingleColumnTable* - 必須。 操作対象となる複数の文字列の単一列テーブル。
* *StartingPosition* - 必須。 置換を開始する文字の位置。  テーブル内の各文字列の最初の文字の位置は 1 です。
* *NumberOfCharacters* - 必須。 各文字列で置換する文字の数。
* *NewString* - 必須。  置換後の文字列。 この引数の文字数は、*NumberOfCharacters* 引数とは異なっていてもかまいません。

**Substitute**( *SingleColumnTable*, *OldString*, *NewString* [, *InstanceNumber* ] )

* *SingleColumnTable* - 必須。 操作対象となる複数の文字列の単一列テーブル。
* *OldString* - 必須。  置換の対象となる文字列。
* *NewString* - 必須。  置換後の文字列。 *OldString* と *NewString* の長さは異なっていてもかまいません。
* *InstanceNumber* - 省略可能。 *String* に複数のインスタンスが含まれている場合、この引数を使用して *OldString* のどのインスタンスを置換するか指定します。 この引数を指定しない場合、すべてのインスタンスが置き換えられます。

## <a name="examples"></a>例

| 計算式 | 内容 | 結果 |
|---------|-------------|--------|
| **Replace( "abcdefghijk",&nbsp;6,&nbsp;5,&nbsp;"*" )** | 「abcdefghijk」の 5 つの文字を、6 番目の文字 (「f」) で始まる単一の「*」文字に置き換えます。 | 「abcde*k」 |
| **Replace(&nbsp;"2019",&nbsp;3,&nbsp;2,&nbsp;"20"&nbsp;)** | 「2019」の最後の 2 文字を「20」に置き換えます。 | 「2020」 |
| **Replace(&nbsp;"123456",&nbsp;1,&nbsp;3,&nbsp;"_"&nbsp;)** | 「123456」の最初の 3 つの文字を単一の「_」文字に置き換えます。 | 「_456」 | 
| **Substitute(&nbsp;"Sales&nbsp;Data",&nbsp;"Sales",&nbsp;"Cost"&nbsp;)** | 文字列「Cost」を「Sales」に置換します。 | 「Cost Data」 | 
| **Substitute( "Quarter&nbsp;1,&nbsp;2018", "1", "2", 1 )** | 4 番目の引数 (*InstanceNumber*) に 1 が指定されているので、最初の「1」のインスタンスのみを「2」に置換します。 |  「2018 年第 2 四半期」 |
| **Substitute( "Quarter&nbsp;1,&nbsp;2011", "1", "2", 3 )** | 4 番目の引数 (*InstanceNumber*) に 3 が指定されているので、3 番目の「1」のインスタンスのみを「2」に置換します。 | 「2012 年第 1 四半期」 |
| **Substitute( "Quarter&nbsp;1,&nbsp;2011", "1", "2" )** | 4 番目の引数 (*InstanceNumber*) が指定されていないので、「1」のすべてのインスタンスは「2」に置換されます。 | 「2022 年第 2 四半期」 |
| **Replace(<br>[&nbsp;"Quarter&nbsp;1,&nbsp;2018",<br>"Quarter&nbsp;2,&nbsp;2011",<br>"Quarter&nbsp;4,&nbsp;2019" ],<br>9,  1, "3" )** | 単一列テーブルの各レコード内で 9 番目の文字を「3」に置き換えます。 | [&nbsp;"Quarter&nbsp;3,&nbsp;2018",<br>"Quarter&nbsp;3,&nbsp;2011",<br>"Quarter&nbsp;3,&nbsp;2019"&nbsp;] |
| **Substitute( <br>[&nbsp;"Qtr&nbsp;1,&nbsp;2018",<br>"Quarter&nbsp;1,&nbsp;2011",<br>"Q1,&nbsp;2019"&nbsp;],<br>"1", "3", 1 )** | 4 番目の引数 (*InstanceNumber*) に 1 の値が指定されている場合、単一列テーブルの各レコード内で「1」の最初のインスタンスのみが「3」に置き換えられます。 | [&nbsp;"Qtr&nbsp;3,&nbsp;2018",<br>"Quarter&nbsp;3,&nbsp;2011",<br>"Q3,&nbsp;2019"&nbsp;] |
| **Substitute( <br>[&nbsp;"Qtr&nbsp;1,&nbsp;2018",<br>"Quarter&nbsp;1,&nbsp;2011",<br>"Q1,&nbsp;2019"&nbsp;],<br>"1", "3" )** | 4 番目の引数 (*InstanceNumber*) が指定されていない場合、単一列テーブルの各レコード内で「1」のすべてのインスタンスが「3」に置換されます。 | [&nbsp;"Qtr&nbsp;3,&nbsp;2038",<br>"Quarter&nbsp;3,&nbsp;2033",<br>"Q3,&nbsp;2039"&nbsp;] |  
 


