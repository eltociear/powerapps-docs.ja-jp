---
title: Average、Max、Min、StdevP、Sum、および VarP 関数 | Microsoft Docs
description: 構文と例を含む Power Apps の Average、Max、Min、StdevP、Sum、および VarP 関数の参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 08/15/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 7ff5e8440295f97268127cdc8a2d5646d5b676fa
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3305556"
---
# <a name="average-max-min-stdevp-sum-and-varp-functions-in-power-apps"></a>Power Apps の Average、Max、Min、StdevP、Sum、および VarP 関数
一連の数値をまとめる集計関数。

## <a name="description"></a>内容
**Average** 関数は、引数の平均または算術平均を算出します。

**Max** 関数は、最大値を割り出します。

**Min** 関数は、最小値を割り出します。

**Sum** 関数は、引数の合計を計算します。

**StdevP** 関数は、引数の標準偏差を算出します。

**VarP** 関数は、引数の差異を算出します。

これらの関数には、次の形式で値を指定できます。

* 個々の引数。 たとえば、**Sum( 1, 2, 3 )** は 6 を返します。
* [テーブル](../working-with-tables.md)とそのテーブルを操作する数式。  各[レコード](../working-with-tables.md#records)について、数式の値の集計が計算されます。  

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

これらの関数は数値に対してのみ動作します。 文字列やレコードなど、他の種類の値は無視されます。 文字列を数値に変換するには、**[Value](function-value.md)** 関数を使用します。

**Average**、**Max**、**Min**、および **Sum** 関数が、[これらの関数の委任をサポートするデータ ソース](../delegation-list.md)に使用される場合は、関数を委任できます。  ただし、**StdevP** と **VarP** は、どのデータ ソースにも委任できません。  委任がサポートされていない場合、データの最初の部分だけが取得され、関数はローカルに適用されます。  結果は完全なストーリーを表さない場合があります。  作成時に表示される委任の警告は、この制限が存在し、可能であれば委任可能な代替物に切り替えるよう提案されるときに表示されます。 詳しくは、「[委任の概要](../delegation-overview.md)」を参照してください。

## <a name="syntax"></a>構文
**Average**( *NumericalFormula1*, [ *NumericalFormula2*, ... ] )<br>**Max**( *NumericalFormula1*, [ *NumericalFormula2*, ... ] )<br>**Min**( *NumericalFormula1*, [ *NumericalFormula2*, ... ] )<br>**Sum**( *NumericalFormula1*, [ *NumericalFormula2*, ... ] )<br>**StdevP**( *NumericalFormula1*, [ *NumericalFormula2*, ... ] )<br>**VarP**( *NumericalFormula1*, [ *NumericalFormula2*, ... ] )

* *NumericalFormula(s)* - 必須。  操作の対象となる数値。

**Average**( *Table*, *NumericalFormula* )<br>**Max**( *Table*, *NumericalFormula* )<br>**Min**( *Table*, *NumericalFormula* )<br>**Sum**( *Table*, *NumericalFormula* )<br>**StdevP**( *Table*, *NumericalFormula* )<br>**VarP**( *Table*, *NumericalFormula* )

* *Table* - 必須。  操作の対象となるテーブル。
* *NumericalFormula* - 必須。 各レコードについて評価する数式。 この数式の結果が集計に使用されます。 数式では、テーブルの列を使用できます。

## <a name="examples"></a>例
### <a name="step-by-step"></a>手順
**Sales** という名前の[データ ソース](../working-with-data-sources.md)に **CostPerUnit** 列と **UnitsSold** 列が含まれており、ラベルの **[Text](../controls/properties-core.md)** プロパティを次の関数に設定するとします。<br>
**Sum(Sales, CostPerUnit *UnitsSold)**

ラベルには、各レコードのこれらの列の値を乗算し、すべてのレコードの結果を加算した合計売上が表示されます。<br>![販売数と出荷単位あたりのコストから合計売上を計算する](./media/function-aggregates/total-sales.png)

別の例として、**Slider1**、**Slider2**、**Slider3** という名前のスライダーがあり、**[Text](../controls/properties-core.md)** プロパティを持つラベルを次の数式に設定したとします。<br>
**Sum(Slider1.Value, Slider2.Value, Slider3.Value)**

ラベルには、スライダーで設定されたすべての値の合計が表示されます。

