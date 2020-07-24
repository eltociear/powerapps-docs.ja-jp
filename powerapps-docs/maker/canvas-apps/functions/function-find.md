---
title: Find 関数 | Microsoft Docs
description: Power Apps での Find 関数の構文と例を含む参照情報
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
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3305234"
---
# <a name="find-function-in-power-apps"></a>Power Apps での Find 関数
テキストの文字列が存在する場合、別の文字列内で検索します。

## <a name="description"></a>内容
**Find** 関数では、文字列を別の文字列内で検索し、大文字と小文字を区別します。 大文字と小文字を無視するには、まず引数に **[Lower](function-lower-upper-proper.md)** 関数を使用します。

**Find** は、見つかった文字列の開始位置を返します。  位置は 1 は文字列の先頭文字です。 **Find** は、検索している文字列に検索対象の文字列が含まれていない場合、*空白*を返します。

## <a name="syntax"></a>構文
**Find**( *FindString*, *WithinString* [, *StartingPosition* ] )

* *FindString* - 必須。  検索する文字列。
* *WithinString* - 必須。  検索対象の文字列。
* *StartingPosition* - オプション。  検索を始める開始位置。  位置 1 は、先頭文字です。

