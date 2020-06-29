---
title: First、FirstN、Last、および LastN 関数 | Microsoft Docs
description: Power Apps での First、FirstN、Last、および LastN 関数の構文と例を含む参照情報
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
ms.openlocfilehash: 490bc00deb41cdc58919cf5f42302ef46dd405f7
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3305211"
---
# <a name="first-firstn-last-and-lastn-functions-in-power-apps"></a>Power Apps での First、FirstN、Last、および LastN 関数
テーブルの最初または最後の[レコード](../working-with-tables.md#records) のセットを返します。

## <a name="description"></a>内容
**First** 関数は、[テーブル](../working-with-tables.md) の最初のレコードを返します。

**FirstN** 関数は、テーブルの最初のレコードのセットを返します。2 番目の引数は返されるレコードの数を指定します。

**Last** 関数は、テーブルの最後のレコードを返します。

**LastN** 関数は、テーブルの最後のレコードのセットを返します。2 番目の引数は返されるレコードの数を指定します。

**First** および **Last** は 1 つのレコードを返します。  **FirstN** および **LastN** は、1 つのレコードのみを指定した場合でも、テーブルを返します。

[!INCLUDE [delegation-no](../../../includes/delegation-no.md)]

## <a name="syntax"></a>構文
**First**( *Table* )<br>**Last**( *Table* )

* *Table* - 必須。 操作の対象となるテーブル。

**FirstN**( *Table* [, *NumberOfRecords* ] )<br>**LastN**( *Table* [, *NumberOfRecords* ] )

* *Table* - 必須。 操作の対象となるテーブル。
* *NumberOfRecords* - オプション。  返されるレコードの数。 この引数を指定しない場合は、関数は 1 つのレコードを返します。

## <a name="examples"></a>例
この関数は、**Employees** という名前のテーブルから最初のレコードを返します。<br>
**First(Employees)**

この関数は、**Employees** という名前のテーブルから最後の 15 レコードを返します。<br>
**LastN(Employees, 15)**

