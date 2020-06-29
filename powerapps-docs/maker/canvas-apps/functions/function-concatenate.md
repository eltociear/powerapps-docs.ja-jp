---
title: Concat および Concatenate 関数 | Microsoft Docs
description: Power Apps での Concat および Concatenate 関数の構文と例を含む参照情報
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
ms.openlocfilehash: 01bf9b2ea165fd24a06725f4f09427bd05c3fe14
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3305464"
---
# <a name="concat-and-concatenate-functions-in-power-apps"></a>Power Apps での Concat および Concatenate 関数

テキストの個々の文字列と[テーブル](../working-with-tables.md) 内の文字列を連結します。

## <a name="description"></a>内容

**Concatenate** 関数は、個々の文字列の組み合わせおよび文字列の単一列テーブルを連結します。 個々の文字列を用いてこの関数を使用する場合、**&** [演算子](operators.md) を使用するのと同等になります。

**Concat** 関数は、テーブルのすべての[レコード](../working-with-tables.md#records) にまたがって適用される数式の結果を連結し、単一の文字列にします。 この関数は、**[Sum](function-aggregates.md)** 関数が数値に対して行うのと同じように、テーブルの文字列を要約するために使用します。

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

文字列を部分文字列テーブルに分割するには、[**Split**](function-split.md) または [**MatchAll**](function-ismatch.md) 関数を使用します。

## <a name="syntax"></a>構文

**Concat**( *Table*, *Formula* )

- *Table* - 必須。  操作の対象となるテーブル。
- *Formula* - 必須。  テーブルのレコードにまたがって適用する数式。

**Concatenate**( *String1* [, *String2*, ...] )

- *文字列* - 必須。  個々の文字列の組み合わせまたは文字列の単一列テーブル。

## <a name="examples"></a>例

このセクションの例は、次のグローバル変数を使用します:

- **FirstName** = "Jane"
- **LastName** = "Doe"
- **製品** = ![2 つの列および 4 つの行のテーブル](media/function-concatenate/products.png)

アプリでこれらのグローバル変数を作成するには、[**Button**](../controls/control-button.md) コントロールを挿入し、**OnSelect** プロパティを次の数式に設定します:

```powerapps-dot
Set( FirstName, "Jane" ); Set( LastName, "Doe" );
Set( Products,
    Table(
        { Name: "Violin", Type: "String" },
        { Name: "Cello", Type: "String" },
        { Name: "Trumpet", Type: "Wind" }
    )
)
```

(Alt キーを押しながらクリックして) ボタンを選択します。

### <a name="concatenate-function-and-the--operator"></a>Concatenate 関数および & 演算子

これらの例では、[**Label**](../controls/control-text-box.md) コントロールの **Text** プロパティを、次のテーブルの最初の列の数式に設定します。

| 計算式 | 内容 | 結果 |
|---------|-------------|--------|
| **Concatenate(&nbsp;LastName,&nbsp;",&nbsp;",&nbsp;FirstName&nbsp;)** | **LastName** の値、文字列である **", "** (コンマの後にスペースが続く)、および **FirstName** の値を連結します。 | "Doe,&nbsp;Jane" |
| **LastName&nbsp;&&nbsp;",&nbsp;"&nbsp;&&nbsp;FirstName** | 関数の代わりに **&** 演算子を使用していることを除き、前の例と同じです。 | "Doe,&nbsp;Jane" |
| **Concatenate(&nbsp;FirstName,&nbsp;"&nbsp;",&nbsp;LastName&nbsp;)** | **FirstName** の値、文字列である **" "** (単一のスペース)、および **LastName** の値を連結します。 | "Jane&nbsp;Doe" |
| **FirstName&nbsp;&&nbsp;"&nbsp;"&nbsp;&&nbsp;LastName** | 前の例と同じで、関数の代わりに **&** 演算子を使用しています。 | "Jane&nbsp;Doe" |

### <a name="concatenate-with-a-single-column-table"></a>単一列テーブルと連結

この例では、空白で、垂直の [**Gallery**](../controls/control-gallery.md) コントロールを追加し、その **Items** プロパティを次のテーブルの数式に設定し、次にギャラリー テンプレートにラベルを追加します。

| 計算式 | 内容 | 結果 |
|---------|-------------|--------|
| **Concatenate( "Name:&nbsp;",&nbsp;Products.Name, ",&nbsp;Type:&nbsp;",&nbsp;Products.Type )** | **製品**テーブルの各レコードで、文字列である **Name**、製品の名前、文字列である **Type** および製品の種類を連結します。  | ![製品のテーブル](media/function-concatenate/single-column.png) |

### <a name="concat-function"></a>Concat 関数

これらの例では、ラベルの **Text** プロパティを次のテーブルの最初の列の数式に設定します。

| 計算式 | 内容 | 結果 |
|---------|-------------|--------|
| **Concat( Products, Name & ", " )** | **製品**の各レコードに対して式である **Name & ", "** が評価され、結果を単一の文字列に連結します。  | "Violin、&nbsp;Cello、&nbsp;Trumpet、&nbsp;" |
| **Concat( Filter(&nbsp;Products,&nbsp;Type&nbsp;=&nbsp;"String"&nbsp;), Name & ", " )** | フィルターである **Type = "String"** を満たす**製品**の各レコードに対して式である **Name & ", "** が評価され、結果を単一の文字列に連結します。   | "Violin、&nbsp;Cello、&nbsp;" |

### <a name="trimming-the-end"></a>末尾のトリミング

最後の 2 つの例では、結果の最後に追加の ", " が含まれています。 関数は、最後のレコードを含むテーブル内のすべてレコードの**名前**の値に、コンマおよびスペースを追加します。

場合によっては、これらの余分な文字は重要ではありません。 たとえば、結果をラベルに表示した場合、シングルスペースの区切り記号は表示されません。 これらの余分な文字を削除する場合は、[**Left**](function-left-mid-right.md) もしくは [**Match**](function-ismatch.md) 関数を使用します。

これらの例では、ラベルの **Text** プロパティを次のテーブルの最初の列の数式に設定します。

| 計算式 | 内容 | 結果 |
|---------|-------------|--------|
| **Left( Concat(&nbsp;Products,&nbsp;Name&nbsp;&&nbsp;",&nbsp;"&nbsp;), Len(&nbsp;Concat(&nbsp;Products,&nbsp;Name&nbsp;&&nbsp;",&nbsp;"&nbsp;)&nbsp;)&nbsp;-&nbsp;2 )** | **Concat** の結果を返しますが、余分な区切り記号を形成する最後 2 文字は削除されます。 | "Violin、&nbsp;Cello、&nbsp;Trumpet" |
| **Match( Concat(&nbsp;Products,&nbsp;Name&nbsp;&&nbsp;",&nbsp;"&nbsp;), "^(?&lt;trim&gt;.*),&nbsp;$" ).trim** | **Concat** の文字をテキスト文字列 (^) の先頭から末尾 ($) に返しますが、末尾に不要なコンマおよびスペースは含まれません。 | "Violin、&nbsp;Cello、&nbsp;Trumpet" |

### <a name="split-and-matchall"></a>Split および MatchAll

区切り記号で **Concat** を使用した場合、**Split** および **MatchAll** 関数を組み合わせることにより操作を逆にできます。

これらの例では、空白で、垂直のギャラリーを追加し、その **Items** プロパティを次のテーブルの数式に設定し、次にギャラリー テンプレートにラベルを追加します。

| 計算式 | 内容 | 結果 |
|---------|-------------|--------|
| **Split( Concat(&nbsp;Products,&nbsp;Name&nbsp;&&nbsp;",&nbsp;"&nbsp;), ", " )** | 区切り記号 **", "** でテキスト文字列を分割します。 文字列はコンマおよびスペースで終わるため、結果の最後の行は空の文字列です。  | ![Table](media/function-concatenate/split.png) |
| **MatchAll( Concat(&nbsp;Products,&nbsp;Name&nbsp;&&nbsp;",&nbsp;"&nbsp;), "[^\s,]+" ).FullMatch** | スペースまたはコンマではない文字に基づいてテキスト文字列を分割します。 この数式は、文字列の末尾にある余分なコンマおよびスペースを削除します。 | ![Table](media/function-concatenate/matchall.png)