---
title: Validate 関数 | Microsoft Docs
description: Power Apps での Validate 関数の構文と例を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/01/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1524b6f28d0ce5b1ed02fbd02d3c2df52e2b300f
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3304360"
---
# <a name="validate-function-in-power-apps"></a>Power Apps の Validate 関数
**Validate** 関数は、特定の[データ ソース](../working-with-data-sources.md) について、単一の[列](../working-with-tables.md#columns) または[レコード](../working-with-tables.md#records) 全体の値が有効であるかどうかを確認するものです。  

## <a name="description"></a>内容
ユーザーがデータの変更を送信する前に、送信内容の有効性についてその場でフィードバックを返し、ユーザー エクスペリエンスを向上させることができます。

データ ソースでは、レコード内で値が有効になるための要素に関する情報を指定できます。 この情報として指定できる制約には、次に挙げたものをはじめ、さまざまなものがあります。

* 列に値が必要かどうか
* テキストの文字列の長さ
* 数値の範囲
* 日付の範囲

**Validate** 関数は、この情報に基づいて値が有効であるかどうかを判定し、有効でなかった場合にはその内容に合わせたエラー メッセージを返します。 **[DataSourceInfo](function-datasourceinfo.md)** 関数でも、**Validate** 関数が使用する情報を表示できます。

有効性に関して提供される情報の量は、データ ソースによって異なります。まったく情報を提供しないデータ ソースもあります。 **Validate** では、この情報に基づいて値を検証するのみにとどまります。 **Validate** で問題が発見されなかった場合でも、データの変更の適用に失敗する可能性は依然として残っています。 変更の失敗に関する情報を取得するには、**[Errors](function-errors.md)** 関数を使用します。

**Validate** で問題が見つかった場合には、アプリのユーザーに対して表示させることができるエラー メッセージが返されます。 値がすべて有効な場合には、**Validate** は[空白](function-isblank-isempty.md) を返します。 検証に関する情報のない[コレクション](../working-with-data-sources.md#collections) の場合には、値が常に有効になります。

## <a name="syntax"></a>構文
**Validate**( *DataSource*, *Column*, *Value* )

* *DataSource* – 必須。 検証に使用するデータ ソース。
* *Column* – 必須。 検証する列。
* *Value* – 必須。 検証対象として選択した列の値。

**Validate**( *DataSource*, *OriginalRecord*, *Updates* )

* *DataSource* – 必須。 検証に使用するデータ ソース。
* *OriginalRecord* - 必須。  更新内容が検証されるレコード。
* *Updates* - 必須。  元のレコードに適用される変更。

## <a name="examples"></a>例
ここに挙げた例では、**Scores** データ ソースの **Percentage** 列の値が 0 以上 100 以下に収まっている必要があります。 データが検証に合格すると、関数は*空白*を返します。 これに対して、検証に合格しなかった場合には、エラー メッセージが返されます。

### <a name="validate-with-a-single-column"></a>単一の列の検証

| 計算式 | 内容 | 結果 |
| --- | --- | --- |
| **Validate( Scores, Percentage, 10 )** |**10** が **Scores** データ ソースの **Percentage** 列の値として有効であるかどうかを確認します。 |*空白* |
| **Validate( Scores, Percentage, 120 )** |**120** が **Scores** データ ソースの **Percentage** 列の値として有効であるかどうかを確認します。 |"Values must be between 0 and 100." |

### <a name="validate-with-a-complete-record"></a>レコード全体の検証

| 計算式 | 内容 | 結果 |
| --- | --- | --- |
| **Validate( Scores, EditRecord, Gallery.Updates )** |**Score** データ ソースのすべての列の値が有効かどうかを確認します。 この例では、**Percentage** 列の値は **10** です。 |*空白* |
| **Validate( Scores, EditRecord, Gallery.Updates )** | **Score** データ ソースのすべての列の値が有効かどうかを確認します。 この例では、**Percentage** 列の値は **120** です。 |"Values must be between 0 and 100." |

