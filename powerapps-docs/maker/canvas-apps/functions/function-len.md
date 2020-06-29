---
title: Len 関数 | Microsoft Docs
description: Power Apps でのLen 関数の構文と例を含む参照情報
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
ms.openlocfilehash: 07b706d9cc0a61e204669646734cdcaf7fc50946
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3304958"
---
# <a name="len-function-in-power-apps"></a>Power Apps の Len 関数
テキストの文字列の長さを返します。

## <a name="description"></a>内容
単一の文字列を引数として指定した場合、戻り値は数値としての長さです。  文字列が含まれている単一列[テーブル](../working-with-tables.md) を指定した場合、戻り値は、各文字列の長さを含む単一列テーブルになります。 複数列テーブルがある場合は、[テーブルの使用](../working-with-tables.md) に関するページの説明に従って、そのテーブルを単一列テーブルにすることができます。

[空白](function-isblank-isempty.md) の文字列を指定した場合、**Len** は 0 を返します。

## <a name="syntax"></a>構文
**Len** ( *文字列* )

* *String* - 必須。 測定する文字列。

**Len** ( *SingleColumnTable* )

* *SingleColumnTable* - 必須。 測定する文字列の単一列テーブル。

## <a name="examples"></a>例
### <a name="single-string"></a>単一の文字列
このセクションの例では、[データ ソース](../working-with-data-sources.md) は **Author** という名前のテキスト入力コントロールで、文字列 "E を含みます。 E. Cummings".

| 計算式 | 内容 | 結果 |
| --- | --- | --- |
| **Len( Author.Text )** |**Author** コントロール内の文字列の長さを測定します。 |14 |
| **Len( "" )** |空の文字列の長さを測定します。 |0 |

### <a name="single-column-table"></a>単一列テーブル
このセクションの最初の例では、データ ソースは **People** という名前がつけられ、次のデータを含みます:

![](media/function-len/people-table.png)

| 計算式 | 内容 | 結果 |
| --- | --- | --- |
| **Len( ShowColumns(&nbsp;People,&nbsp;"Address"&nbsp;) )** |**People** テーブルの**住所**[列](../working-with-tables.md#columns) 内:<br><ul><li>各文字列の長さを測定します。</li><li>各文字列の長さを含む単一列テーブルを返します。</li> |<style> img { 最大幅: なし } </style> ![](media/function-len/people-table-len.png) |
| **Len( [ "Hello", "to the", "World", "" ] )** |インライン テーブルの**[Value](function-value.md)** 列内:<br><ul><li>各文字列の長さを測定します。</li><li>各文字列の長さを含む単一列テーブルを返します。</li> |![](media/function-len/people-table-len-inline.png) |

