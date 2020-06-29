---
title: And、Or、および Not 関数 | Microsoft Docs
description: Power Apps での And、Or、および Not 関数の構文と例を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/23/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1dae72a288c93b624d232402e32fe0e82cbaaead
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3304912"
---
# <a name="and-or-and-not-functions-in-power-apps"></a>Power Apps の And、Or、および Not 関数

比較とテストの結果を操作するためによく使用される、ブール値の論理関数。

## <a name="description"></a>内容

**And** 関数は、すべての引数が **true** の場合に **true** を返します。

**Or** 関数は、引数のいずれかが **true** の場合に **true** を返します。

**Not** 関数は、引数が **false** の場合は **true** を、引数が **true** の場合は **false** を返します。

これらの関数は、Excel と同じように機能します。 Visual Basic または JavaScript 構文を使用して、同じ操作を実行するには、[演算子](operators.md) を使用することもできます:

| 関数の表記 | Visual Basic 演算子表記 | JavaScript 演算子表記 |
| -------------|------------|--------|
| **And ( x, y )** | **x と y** | **x && y** |
| **Or ( x, y )** | **x または y** | **x &#124;&#124; y** |
| **Not ( x )** | **x 以外** | **! x** |

これらの関数は論理値と機能します。 数または文字列をこれらの関数に直接渡すことはできません; その代わり、比較またはテストする必要があります。 たとえば、この論理式は **x** が **1** より大きい場合、**x > 1** はブール値を **true** と評価します。 **x** が **1** 未満の場合、数式は **false** と評価します。

## <a name="syntax"></a>構文

**And**( *LogicalFormula1*, *LogicalFormula2* [, *LogicalFormula3*, ... ] )<br>
**Or**( *LogicalFormula1*, *LogicalFormula2* [, *LogicalFormula3*, ... ] )<br>
**Not**( *LogicalFormula* )

- *LogicalFormula(s)* - 必須。  評価および操作の論理式。

## <a name="examples"></a>例

このセクションの例は、次のグローバル変数を使用します:

- **a** = *false*
- **b** = *true*
- **x** = 10
- **y** = 100
- **s** = 「Hello World」

アプリでこれらのグローバル変数を作成するには、[**Button**](../controls/control-button.md) コントロールを挿入し、**OnSelect** プロパティを次の数式に設定します:

```powerapps-dot
Set( a, false ); Set( b, true ); Set( x, 10 ); Set( y, 100 ); Set( s, "Hello World" )
```

(Altキーを押しながらクリックして) ボタンを選択し、[**Label**](../controls/control-text-box.md) コントロールの **Text** プロパティを次のテーブルの最初の列の数式に設定します。

| 計算式 | 内容 | 結果 |
|---------|-------------|--------|
| **And( a, b )** | **a** および **b** の値をテストします。  引数の 1 つは *false*なので、関数は *false* を返します。 | *false* |
| **a および b** | 前の例と同じように、Visual Basic 表記を使用ています。 | *false* |
| **a && b** | 前の例と同じように、 JavaScript 表記を使用しています。 | *false* |
| **または ( a, b )** | **a** および **b** の値をテストします。 引数の 1 つは *true*なので、関数は *true* を返します。 | *True* |
| **a または b** | 前の例と同じように、Visual Basic 表記を使用ています。 | *True* |
| **a &#124;&#124; b** | 前の例と同じように、 JavaScript 表記を使用しています。 | *True* |
| **Not ( a )** | **a** の値をテストします。 引数は *false* なので、関数は反対の結果を返します。 | *True* |
| **Not a** | 前の例と同じように、Visual Basic 表記を使用ています。 | *True* |
| **! a** | 前の例と同じように、 JavaScript 表記を使用しています。 | *True* |
| **Len (&nbsp;s&nbsp;)&nbsp;<&nbsp;20 および &nbsp;Not&nbsp;IsBlank (&nbsp;s&nbsp;)** | **s** の長さが 20 未満かどうか、また、**空白**値でないかどうかテストします。 長さが 20 未満で、値が空白ではありません。 したがって、結果は *true* です。 | *True* |
| **または (&nbsp;Len (&nbsp;s&nbsp;) &nbsp;<&nbsp;10、x&nbsp;<&nbsp;100、 y&nbsp;<&nbsp;100&nbsp;)** | **s** の長さが 10 未満かどうか、**x** が 100 未満かどうか、**y** が 100 未満かどうかテストします。 最初および 3 番目の引数は false ですが、2 番目は true です。 したがって、関数は *true* を返します。 | *True* |
| **Not IsBlank (&nbsp;s&nbsp;)** | **s** は *false* を返す*空白*かどうかをテストします。 **Not** はこの結果の反対である *true* を返します。 | *True* |