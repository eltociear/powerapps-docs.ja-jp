---
title: Distinct 関数 | Microsoft Docs
description: Power Apps での Distinct 関数の構文と例を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 09/14/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b77cdf452250fc30e1b8c61867f82e5f109fff49
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3305326"
---
# <a name="distinct-function-in-power-apps"></a>Power Apps での Distinct 関数
[テーブル](../working-with-tables.md) の[レコード](../working-with-tables.md#records) を要約し、重複を削除します。

## <a name="description"></a>内容
**Distinct** 関数は、テーブルの各レコードにわたって数式を評価し、重複する値が削除された結果の 1 列のテーブルを返します。  列の名前は、**結果**です。  

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

[!INCLUDE [delegation-no-one](../../../includes/delegation-no-one.md)]

## <a name="syntax"></a>構文
**Distinct**( *Table*, *Formula* )

* *Table* - 必須。  全体を評価するテーブル。
* *Formula* - 必須。  各レコードについて評価する数式。

## <a name="example"></a>例

1. [**Button**](../controls/control-button.md) コントロールを挿入し、**OnSelect** プロパティに次の数式を設定します。

    ```powerapps-dot
    ClearCollect( CityPopulations,
        { City: "London",    Country: "United Kingdom", Population: 8615000 },
        { City: "Berlin",    Country: "Germany",        Population: 3562000 },
        { City: "Madrid",    Country: "Spain",          Population: 3165000 },
        { City: "Hamburg",   Country: "Germany",        Population: 1760000 },
        { City: "Barcelona", Country: "Spain",          Population: 1602000 },
        { City: "Munich",    Country: "Germany",        Population: 1494000 }
    );
    ```

1. Alt キーを押しながら、ボタンを選択します。

    数式が評価され、数式バーで **CityPopulations** を選択して表示される **CityPopulations** が作成されます。

    > [!div class="mx-imgBorder"]
    > ![結果ビューに表示される CityPopulations コレクション](media/function-distinct/citypopulations-create.png)

1. [**データ テーブル**](../controls/control-data-table.md) コントロールを挿入し、その **Items** プロパティを次の数式に設定します。

    ```powerapps-dot
    Distinct( CityPopulations, Country )
    ```

    数式の全体を選択すると、この数式の結果が数式バーに表示されます。

    > [!div class="mx-imgBorder"]
    > ![結果ビューに表示される Distinct 関数からの出力](media/function-distinct/citypopulations-distinct.png)

1. データ テーブルのプロパティ ペインで、**フィールドの編集**リンクを使用し、**結果**列を追加します。

    > [!div class="mx-imgBorder"]
    > ![データ テーブルに表示される Distinct 関数からの出力](media/function-distinct/citypopulations-datatable.png)

1. [**Label**](../controls/control-text-box.md) コントロールを挿入し、その **Text** プロパティを次の数式に設定します。

    ```powerapps-dot
    First( Sort( Distinct( CityPopulations, Country ), Result ) ).Result
    ```

    この数式は、[**Sort**](function-sort.md) 関数を使用して **Distinct** からの結果を並べ替え、[**First**](function-first-last.md) 関数を使用して結果テーブルから最初のレコードを取り出し、**結果**フィールドを解凍して国名のみを取得します。

    > [!div class="mx-imgBorder"]
    > ![最初の国を名前で表示する Distinct 関数からの出力](media/function-distinct/citypopulations-first.png)

     
