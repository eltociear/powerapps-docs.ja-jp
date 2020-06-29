---
title: Acos、Acot、Asin、Atan、Atan2、Cos、Cot、Degrees、Pi、Radians、Sin、Tan 関数 | Microsoft Docs
description: Power Apps での Abs および Sqrt 関数の構文と例を含む参照情報
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
ms.openlocfilehash: 8ff8b68dce51ce985c391de569e4be7a5a8fabb4
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3304429"
---
# <a name="acos-acot-asin-atan-atan2-cos-cot-degrees-pi-radians-sin-and-tan-functions-in-power-apps"></a>Power Apps での Acos、Acot、Asin、Atan、Atan2、Cos、Cot、Degrees、Pi、Radians、Sin、Tan 関数 
三角関数の値を計算します。

## <a name="description"></a>内容
### <a name="primary-functions"></a>主要な関数
**Cos** 関数は、ラジアン単位で指定された角度の引数のコサインを返します。

**Cot** 関数は、ラジアン単位で指定された角度の引数のコタンジェントを返します。

**Sin** 関数は、ラジアン単位で指定された角度の引数のサインを返します。

**Tan** 関数は、ラジアン単位で指定された角度の引数のタンジェントを返します。

### <a name="inverse-functions"></a>逆関数
**Acos** 関数は、引数のアークコサイン (逆余弦) の値を返します。 アークコサインとは、コサインの値を引数として得られる角度です。  戻り値としての角度は、ラジアンを使って 0 から &pi; までの範囲で表されます。

**Acot** 関数は、引数のアークコタンジェント (逆余接) の主値を返します。  戻り値としての角度は、ラジアンを使って 0 から &pi; までの範囲で表されます。

**Asin** 関数は、引数のアークサイン (逆正弦) の値を返します。 アークサインとは、サインの値を引数として得られる角度です。  戻り値としての角度は、ラジアンを使って -&pi;/2 から &pi;/2 までの範囲で表されます。

**Atan** 関数は、引数のアークタンジェント (逆正接) の値を返します。 アークタンジェントとは、タンジェントの値を引数として得られる角度です。 戻り値としての角度は、ラジアンを使って -&pi;/2 から &pi;/2 までの範囲で表されます。

**Atan2** 関数は、指定された *x* 座標と *y* 座標を引数としてそのアークタンジェント (逆正接) の値を返します。 アークタンジェントとは、*x* 軸と、原点 (0, 0) と座標 (*x*, *y*) の 2 点を通る直線が形成する角度を表すものです。 角度は、ラジアンを使って -&pi; から &pi; までの範囲で表されます。ただし、-&pi; は除きます。  結果が正の値であれば *x* 軸から反時計回りの方向に形成する角度、負の値であれば時計回りの方向に形成する角度を表します。  **Atan2(&nbsp;*a*,&nbsp;*b*&nbsp;)** と **Atan(&nbsp;*b*/*a*&nbsp;)** は同じ結果になりますが、**Atan2** 関数の方は ***a*** を 0 にすることができるという点で違いがあります。

### <a name="helper-functions"></a>Helper 関数
**Degrees** 関数は、ラジアンを度数法で示した角度に変換します。  ラジアンの &pi; は、度数法の 180 度と同じことを表します。

**Pi** 関数は、3.141592... と永遠に続く超越数 &pi; を返します。

**Radians** 関数は、度数法を使った角度をラジアン値に変換します。  

### <a name="notes"></a>メモ​​
ここに挙げた関数に数値を 1 つだけ渡した場合には、戻り値が 1 つだけ返されます。  複数の数値を含んだ単一列[テーブル](../working-with-tables.md) を渡すと、戻り値は複数の結果を含んだ単一列テーブルとなり、引数のテーブル内のレコードごとに 1 つの結果が返されます。 複数列テーブルがある場合は、[テーブルの使用](../working-with-tables.md) に関するページの説明に従って、そのテーブルを単一列テーブルにすることができます。  

引数が、未定義の値の場合は、結果は*空白*です。  これは、対応範囲外の引数を指定して逆関数を使用した場合などに発生します。

## <a name="syntax"></a>構文
### <a name="primary-functions"></a>主要な関数
**Cos**( *Radians* )<br>**Cot**( *Radians* )<br>**Sin**( *Radians* )<br>**Tan**( *Radians* )

* *Radians* - 必須。 演算の対象となる角度。

**Cos**( *SingleColumnTable* )<br>**Cot**( *SingleColumnTable* )<br>**Sin**( *SingleColumnTable* )<br>**Tan**( *SingleColumnTable* )

* *SingleColumnTable* - 必須。 演算の対象となる角度が複数含まれる単一列テーブル。

### <a name="inverse-functions"></a>逆関数
**Acos**( *Number* )<br>**Acot**( *Number* )<br>**Asin**( *Number* )<br>**Atan**( *Number* )

* *Number* - 必須。 演算する数値。

**Acos**( *SingleColumnTable* )<br>**Acot**( *SingleColumnTable* )<br>**Asin**( *SingleColumnTable* )<br>**Atan**( *SingleColumnTable* )

* *SingleColumnTable* - 必須。 演算する複数の数値を含む単一列テーブル。

**Atan2**( *X*, *Y* )

* *X* - 必須。  *X* 軸の座標。
* *Y* - 必須。  *Y* 軸の座標。

### <a name="helper-functions"></a>Helper 関数
**Degrees**( *Radians* )

* *Radians* - 必須。  ラジアン値を度数法に変換した角度 。

**Pi**()

**Degrees**( *Radians* )

* *Degrees* - 必須。  ラジアン値に変換する角度 (度数法の数値を指定します)。

## <a name="examples"></a>例
### <a name="single-number"></a>単一の数値

| 計算式 | 内容 | 結果 |
| --- | --- | --- |
| **Cos(&nbsp;1.047197&nbsp;)** |ラジアン値 1.047197 (60 度) のコサインを返します。 |0.5 |
| **Cot(&nbsp;Pi()/4&nbsp;)** |ラジアン値 0.785398... (45 度) のコタンジェントを返します。 |1 |
| **Sin(&nbsp;Pi()/2&nbsp;)** |ラジアン値 1.570796... (90 度) のサインを返します。 |1 |
| **Tan(&nbsp;Radians(60)&nbsp;)** |ラジアン値 1.047197... (60 度) のタンジェントを返します。 |1.732050... |
| **Acos(&nbsp;0.5&nbsp;)** |0.5 のアークコサインをラジアン単位で返します。 |1.047197... |
| **Acot(&nbsp;1&nbsp;)** |1 のアークコタンジェントをラジアン単位で返します。 |0.785398... |
| **Asin(&nbsp;1&nbsp;)** |1 のアークサインをラジアン単位で返します。 |1.570796... |
| **Atan(&nbsp;1.732050&nbsp;)** |1.732050 のアークコタンジェントをラジアン単位で返します。 |1.047197... |
| **Atan2(&nbsp;5,&nbsp;3&nbsp;)** |*x* 軸と、原点 (0, 0) と座標 (5, 3) の 2 点を通る直線が形成する角度 (約 31 度) のアークタンジェントを返します。 |0.540419... |
| **Atan2(&nbsp;4,&nbsp;4&nbsp;)** |*x* 軸と、原点 (0, 0) と座標 (4, 4) の 2 点を通る直線が形成する角度 (ラジアン値 &pi;/4、45 度) のアークタンジェントを返します。 |0.785398... |
| **Degrees(&nbsp;1.047197&nbsp;)** |1.047197 度について、対応するラジアン値を返します。 |60 |
| **Pi()** |超越数 &pi; を返します。 |3.141592... |
| **Radians(&nbsp;15&nbsp;)** |15 度について、対応するラジアン値を返します。 |0.261799... |

### <a name="single-column-table"></a>単一列テーブル
このセクションの例では、名前が **ValueTable** で、次のデータを含む[データ ソース](../working-with-data-sources.md) を使用します。  このテーブルの最後のレコードは、ラジアン値では &pi;/2、度数法では 90 度を表すものです。

![](media/function-trig/values.png)

| 計算式 | 内容 | 結果 |
| --- | --- | --- |
| **Cos(&nbsp;ValueTable&nbsp;)** |テーブルの各数値のコサインを返します。 |<style> img { max-width: none } </style> ![](media/function-trig/values-cos.png) |
| **Cot(&nbsp;ValueTable&nbsp;)** |テーブルの各数値のコタンジェントを返します。 |<style> img { max-width: none } </style> ![](media/function-trig/values-cot.png) |
| **Sin(&nbsp;ValueTable&nbsp;)** |テーブルの各数値のサインを返します。 |<style> img { max-width: none } </style> ![](media/function-trig/values-sin.png) |
| **Tan(&nbsp;ValueTable&nbsp;)** |テーブルの各数値のタンジェントを返します。 |<style> img { max-width: none } </style> ![](media/function-trig/values-tan.png) |
| **Acos(&nbsp;ValueTable&nbsp;)** |テーブルの各数値のアークコサインを返します。 |<style> img { max-width: none } </style> ![](media/function-trig/values-acos.png) |
| **Acot(&nbsp;ValueTable&nbsp;)** |テーブルの各数値のアークコタンジェントを返します。 |<style> img { max-width: none } </style> ![](media/function-trig/values-acot.png) |
| **Asin(&nbsp;ValueTable&nbsp;)** |テーブルの各数値のアークサインを返します。 |<style> img { max-width: none } </style> ![](media/function-trig/values-asin.png) |
| **Atan(&nbsp;ValueTable&nbsp;)** |テーブルの各数値のアークタンジェントを返します。 |<style> img { max-width: none } </style> ![](media/function-trig/values-atan.png) |
| **Degrees(&nbsp;ValueTable&nbsp;)** |テーブルの各数値を度数法で示した角度と仮定して、対応するラジアン値を返します。 |<style> img { max-width: none } </style> ![](media/function-trig/values-degrees.png) |
| **Radians(&nbsp;ValueTable&nbsp;)** |テーブルの各数値を度数法で示した角度と仮定して、対応するラジアン値を返します。 |<style> img { max-width: none } </style> ![](media/function-trig/values-radians.png) |

