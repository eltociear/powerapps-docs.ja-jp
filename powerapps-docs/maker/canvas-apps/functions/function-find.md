---
title: Find 関数 | Microsoft Docs
description: 構文と例を含む Power Apps の Find 関数の参照情報
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
ms.openlocfilehash: 62254bf46836ffc8ed5fa5b7685561b611db49a7
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730976"
---
# <a name="find-function-in-power-apps"></a>Power Apps の Find 関数
テキストの文字列を別の文字列内で検索します (存在する場合)。

## <a name="description"></a>Description
**Find** 関数は、文字列を別の文字列内で検索します。大文字と小文字は区別されます。 大文字と小文字を区別しない場合は、最初に引数に対して **[Lower](function-lower-upper-proper.md)** 関数を使用します。

**Find** は、見つかった文字列の開始位置を返します。  位置 1 は、文字列の先頭の文字です。 **Find** は、検索先の文字列に検索対象の文字列が含まれていない場合、"*空白*" を返します。

## <a name="syntax"></a>構文
**Find**( *FindString*, *WithinString* [, *StartingPosition* ] )

* *FindString* - 必須。  検索する文字列。
* *WithinString* - 必須。  検索先の文字列。
* *StartingPosition* - 省略可能。  検索の開始位置。  位置 1 は、先頭の文字です。

