---
title: Abs、Exp、Ln、Power および Sqrt 関数 | Microsoft Docs
description: Power Apps での Abs、Sqrt およびその他の関数の構文と例を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 09/13/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 925297a8e1a3f4c454cb8bbb09f75a87419cf5cb
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3304820"
---
# <a name="abs-exp-ln-power-and-sqrt-functions-in-power-apps"></a>Power Apps の Abs、Exp、Ln、Power および Sqrt 関数
絶対値、自然対数、平方根、および *e* または任意の数の指定した累乗の結果を計算します。

## <a name="description"></a>内容
**Abs** 関数は引数の負以外の値を返します。 数値が負の場合は、**Abs** は相当する正の値を返します。

**Exp** 関数は *e* の引数の累乗を返します。  超越数 *e* は 2.7182818... で始まります

**Ln** 関数は引数の自然対数 (ベース *e*) を返します。

**Power** 関数は数値の累乗を返します。  [**^** 演算子](operators.md) を使用するのに相当します。

**Sqrt** 関数はそれ自体を乗じた場合に、引数と等しい数値を返します。

単一の数値を渡す場合、戻り値は呼び出される関数に基づく単一の結果です。  複数の数値を含んだ単一列[テーブル](../working-with-tables.md) を渡すと、戻り値は複数の結果を含んだ単一列テーブルとなり、引数のテーブル内のレコードごとに 1 つの結果が返されます。 複数列テーブルがある場合は、[テーブルの使用](../working-with-tables.md) に関するページの説明に従って、そのテーブルを単一列テーブルにすることができます。  

引数が、未定義の値の場合は、結果は*空白*です。  このことは、たとえば、負の数値の平方根および対数などで発生する場合があります。

## <a name="syntax"></a>構文
**Abs**( *Number* )<br>**Exp**( *Number* )<br>**Ln**( *Number* )<br>**Sqrt**( *Number* )

* *Number* - 必須。 演算する数値。

**Power**( *Base*、*Exponent* )

* *Base* - 必須。 累乗する Base の数値。
* *Exponent* - 必須。 ベースの数値を累乗する指数。

**Abs**( *SingleColumnTable* )<br>**Exp**( *SingleColumnTable* )<br>**Ln**( *SingleColumnTable* )<br>**Sqrt**( *SingleColumnTable* )

* *SingleColumnTable* - 必須。 演算する複数の数値を含む単一列テーブル。

## <a name="examples"></a>例
### <a name="single-number"></a>単一の数値

| 計算式 | 内容 | 結果 |
| --- | --- | --- |
| **Abs( -55 )** |負の記号のない数値を返します。 |55 |
| **Exp( 2 )** |*e* の 2 乗、または *e* \* *e* を返します。 |7.389056... |
| **Ln( 100 )** |数値 100 の自然対数 (ベース *e*) を返します。 |4.605170... |
| **Power( 5, 3 )** |5 の 3 乗、または 5 \* 5 \* 5 を返します。 |125 |
| **Sqrt( 9 )** |それ自体を乗じた結果が 9 になる数値を返します。 |3 |

### <a name="single-column-table"></a>単一列テーブル
このセクションの例では、**ValueTable** という名前のついた[データ ソース](../working-with-data-sources.md)を使用し、次のデータを含みます:

![](media/function-numericals/values.png)

| 計算式 | 内容 | 結果 |
| --- | --- | --- |
| **Abs(&nbsp;ValueTable&nbsp;)** |テーブル内の各数値の絶対値を返します。 |<style> img { 最大幅: なし } </style> ![](media/function-numericals/values-abs.png) |
| **Exp(&nbsp;ValueTable&nbsp;)** |テーブル内の各数値で *e* を累乗した値を返します。 |<style> img { 最大幅: なし } </style> ![](media/function-numericals/values-exp.png) |
| **Ln(&nbsp;ValueTable&nbsp;)** |テーブルの各数値の自然対数を返します。 |<style> img { 最大幅: なし } </style> ![](media/function-numericals/values-ln.png) |
| **Sqrt(&nbsp;ValueTable&nbsp;)** |テーブルの各数値の平方根を返します |![](media/function-numericals/values-sqrt.png) |

### <a name="step-by-step-example"></a>手順の例
1. **[テキスト入力](../controls/control-text-input.md)** コントロールを追加し、**ソース**という名前を付けます。
2. **Label** コントロールを追加し、その **[Text](../controls/properties-core.md)** プロパティを次の数式に設定します。
   <br>
   **Sqrt( Value( Source.Text ) )**
3. **Source** に数値を入力し、**Label** コントロールに入力した数値の平方根が表示されることを確認します。

