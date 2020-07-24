---
title: Count、CountA、CountIf、および CountRows 関数 | Microsoft Docs
description: Power Apps での Count、CountA、CountIf、および CountRows 関数の構文と例を含む参照情報
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
ms.openlocfilehash: a0c9d7d96b4ca6ce75993586de5a39fd33906f3b
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3304521"
---
# <a name="count-counta-countif-and-countrows-functions-in-power-apps"></a>Power Apps の Count、CountA、CountIf、および CountRows 関数
[テーブル](../working-with-tables.md) のすべての[レコード](../working-with-tables.md#records) をカウントするか、条件を満たすすべてのレコードをカウントします。

## <a name="description"></a>内容
**Count** 関数は、単一列テーブルのレコードのうち、数値が含まれるレコード数をカウントします。

**CountA** 関数は、単一列テーブルのレコードのうち、*空白*でないレコード数をカウントします。 この関数では、[空](function-isblank-isempty.md) のテキスト ("") もカウントされます。

**CountIf** 関数は、テーブルのレコードのうち、論理式で **true** になるレコード数をカウントします。  数式では、テーブルの[列](../working-with-tables.md#columns) を参照できます。

**CountRows** 関数は、テーブルのレコード数をカウントします。

これらの各関数は数値を返します。

[!INCLUDE [delegation-no](../../../includes/delegation-no.md)]

## <a name="syntax"></a>構文
**Count**( *SingleColumnTable* )<br>
**CountA**( *SingleColumnTable* )

* *SingleColumnTable* - 必須。  カウントするレコードの列。  

**CountIf**( *Table*, *LogicalFormula* )

* *Table* - 必須。  カウントするレコードのテーブル。
* *LogicalFormula* - 必須。  テーブルの各レコードについて評価する数式。  この数式に対して **true** を返すレコードがカウントされます。  数式では、テーブルの列を参照できます。

**CountRows**( *Table* )

* *Table* - 必須。  カウントするレコードのテーブル。

## <a name="example"></a>例
1. [ギャラリーでイメージとテキストを表示する](../show-images-text-gallery-sort-filter.md) 方法に関するページの最初の手順に従って、**Inventory** という名前の[コレクション](../working-with-data-sources.md#collections) をインポートするか作成します。
2. ラベルを追加し、その **[Text](../controls/properties-core.md)** プロパティを次の数式に設定します。
   
    **CountIf(Inventory, UnitsInStock < 30)**
   
    2 つの製品 (Ganymede と Callisto) の在庫数が 30 未満なので、ラベルに **2** と表示されます。
3. 別のラベルを追加し、その **[Text](../controls/properties-core.md)** プロパティを次の計算式に設定します。
   
    **CountA(Inventory.UnitsInStock)**
   
    ラベルに **5** と表示されます。これは、**UnitsInStock** 列の空でないセルの数です。
4. 別のラベルを追加し、その **[Text](../controls/properties-core.md)** プロパティを次の計算式に設定します。
   
    **CountRows(Inventory)**
   
    コレクションには 5 つの行が含まれているため、ラベルに **5** と表示されます。

