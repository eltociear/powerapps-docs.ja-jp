---
title: Revert 関数 | Microsoft Docs
description: Power Apps での Revert 関数の構文と例を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/21/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: efaffeac79c104d517d8e7da5b2e324fcac3eecb
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3304659"
---
# <a name="revert-function-in-power-apps"></a>Power Apps の Revert 関数
[データ ソース](../working-with-data-sources.md) の [レコード](../working-with-tables.md#records) を更新し、エラーをクリアします。

## <a name="description"></a>内容
**Revert** 関数は、データ ソース全体またはそのデータ ソース内の 1 つのレコードを更新します。 他のユーザーが加えた変更が表示されます。

元に戻されたレコードについて、**Revert** は **[Errors](function-errors.md)** 関数から返されたすべてのエラーを [テーブル](../working-with-tables.md) からクリアします。

**[Patch](function-patch.md)** またはその他のデータ操作の後に **[Errors](function-errors.md)** 関数で競合がレポートされた場合は、競合するバージョンのあるレコードを **Revert** で元に戻したうえで、変更を再適用してください。

**Revert** には、戻り値はありません。 [動作の数式](../working-with-formulas-in-depth.md) 内でのみ使用できます。

## <a name="syntax"></a>構文
**Revert**( *DataSource* [, *Record* ] )

* *DataSource* – 必須。 元に戻す対象のデータ ソース。
* *Record* - オプション。  元に戻す対象のレコード。  レコードを指定しない場合、データ ソース全体が元に戻されます。

## <a name="example"></a>例
この例では、**IceCream** という名前のデータ ソースを元に戻します。このデータ ソースは次のテーブルのデータから始まります。

![](media/function-revert/icecream.png)

別のデバイスのユーザーが、**Strawberry** レコードの **Quantity** プロパティを **400** に変更します。  この変更を知らないまま、自分がほぼ同時に同じレコードの同じプロパティを **500** に変更したとします。

**[Patch](function-patch.md)** 関数を使用して、レコードを更新します。<br>
**Patch( IceCream, First( Filter( IceCream, Flavor = "Strawberry" ) ), { Quantity: 500 } )**

**[Errors](function-errors.md)** テーブルを確認すると、エラーが表示されています。

| レコード | [列](../working-with-tables.md#columns) | メッセージ | エラー |
| --- | --- | --- | --- |
| **{ ID: 1, Flavor: "Strawberry", Quantity: 300 }** |*空白* |**変更しようとしているレコードは別のユーザーによって変更されています。レコードを元に戻して、もう一度やり直してください。** |**ErrorKind.Conflict** |

**Error** 列に基づき、**Reload** ボタンの **[OnSelect](../controls/properties-core.md)** プロパティは、次の数式に設定されます。<br>
**Revert( IceCream, First( Filter( IceCream, Flavor = "Strawberry" ) ) )**

**Reload** ボタンを選択すると、**[Errors](function-errors.md)** テーブルが [空](function-isblank-isempty.md) になり、**Strawberry** の新しい値が読み込まれます。

![](media/function-revert/icecream-after.png)

この既に行われた変更の上から変更を再適用すると、競合が解決されるので、変更が成功します。

![](media/function-revert/icecream-success.png)

