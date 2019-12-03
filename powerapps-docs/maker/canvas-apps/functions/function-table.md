---
title: Table 関数 | Microsoft Docs
description: 構文と例を含む Power Apps の Table 関数の参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm tapanm
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 900277f62d35ad36fc914e6ca83a1d03e621bafe
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74729933"
---
# <a name="table-function-in-power-apps"></a>Power Apps の Table 関数
一時[テーブル](../working-with-tables.md)を作成します。

## <a name="description"></a>Description
**Table** 関数は、[レコード](../working-with-tables.md#records)の引数リストからテーブルを作成します。

テーブルの[列](../working-with-tables.md#columns)は、すべての引数レコードのすべてのプロパティの集合になります。 レコードに値が含まれていない列には、"*空白*" の値が追加されます。

テーブルは、文字列や数値と同じように、Power Apps の値です。 テーブルは関数の引数として指定できるほか、関数から結果として返すことができます。 **Table** は、永続テーブルは作成しません。 その代わりに、引数で構成された一時テーブルを返します。  この一時テーブルは、別の関数の引数として指定できるほか、ギャラリーで視覚化したり、別のテーブルに埋め込んだりもできます。  詳細については、[テーブルの使用](../working-with-tables.md)に関するページを参照してください。

**[ value1, value2, ... ]** という構文を使って、単一列テーブルを作成することもできます。

## <a name="syntax"></a>構文
**Table**( *Record1* [, *Record2*, ... ] )

* *Record(s)* - 必須。 テーブルに追加するレコード。

## <a name="examples"></a>例
* リスト ボックスの **[Items](../controls/properties-core.md)** プロパティを次の数式に設定します。
  <br>**Table({Color:"red"}, {Color:"green"}, {Color:"blue"})**
  
    リスト ボックスには、オプションとしてそれぞれの色が表示されます。
* テキスト ギャラリーを追加し、その **[Items](../controls/properties-core.md)** プロパティをこの関数に設定します。<br>
  **Table({Item:"Violin123", Location:"France", Owner:"Fabrikam"}, {Item:"Violin456", Location:"Chile"})**
  
    ギャラリーには 2 つのレコードが表示されます。どちらにも、項目の場所と名前が含まれます。 所有者の名前が含まれるのは、1 つのレコードのみです。

