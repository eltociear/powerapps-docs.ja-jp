---
title: Revert 関数 | Microsoft Docs
description: 構文と例を含む PowerApps の Revert 関数の参照情報
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
ms.openlocfilehash: dbf1c623b18bc244e62fd962625f1d7cde35f1e4
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992448"
---
# <a name="revert-function-in-powerapps"></a>PowerApps の Revert 関数
[データ ソース](../working-with-data-sources.md)の[レコード](../working-with-tables.md#records)を更新し、エラーをクリアします。

## <a name="description"></a>説明
**Revert** 関数は、データ ソース全体またはそのデータ ソース内の 1 つのレコードを更新します。 他のユーザーが加えた変更が表示されます。

元に戻されたレコードについては、**Revert** は **[Errors](function-errors.md)** 関数から返されたすべてのエラーを[テーブル](../working-with-tables.md)からクリアします。

**[Patch](function-patch.md)** またはその他のデータ操作の後に **[Errors](function-errors.md)** 関数で競合がレポートされた場合は、競合するバージョンのあるレコードを **Revert** で元に戻したうえで、変更を再適用してください。

**Revert** には、戻り値はありません。 [動作の数式](../working-with-formulas-in-depth.md)内でのみ使用できます。

## <a name="syntax"></a>構文
**Revert**( *DataSource* [, *Record* ] )

* *DataSource* – 必須。 元に戻す対象のデータ ソース。
* *Record* - 省略可能。  元に戻す対象のレコード。  レコードを指定しない場合、データ ソース全体が元に戻されます。

## <a name="example"></a>例
この例では、**IceCream** という名前のデータ ソースを元に戻します。このデータ ソースは次のテーブルのデータから始まります。

![](media/function-revert/icecream.png)

別のデバイスのユーザーが、**Strawberry** レコードの **Quantity** プロパティを **400** に変更します。  この変更を知らないまま、自分がほぼ同時に同じレコードの同じプロパティを **500** に変更したとします。

**[Patch](function-patch.md)** 関数を使用して、レコードを更新します。<br>
**Patch (IceCream、First (Filter (IceCream, フレーバー = "Strawberry"))、{Quantity:500})**

**[Errors](function-errors.md)** テーブルを確認すると、エラーが表示されています。

| レコード | [列](../working-with-tables.md#columns) | メッセージ | エラー |
| --- | --- | --- | --- |
| **{ID:1、フレーバー:"Strawberry"、Quantity:300}** |"*空白*" |**"変更しようとしているレコードは別のユーザーにより変更されています。レコードを元に戻してからやり直してください。"** |**ErrorKind.Conflict** |

**Error** 列に基づいて、**Reload** ボタンの **[OnSelect](../controls/properties-core.md)** プロパティは、次の数式に設定されます。<br>
**Revert( IceCream, First( Filter( IceCream, Flavor = "Strawberry" ) ) )**

**Reload** ボタンを選択すると、 **[Errors](function-errors.md)** テーブルが[空](function-isblank-isempty.md)になり、**Strawberry** の新しい値が読み込まれます。

![](media/function-revert/icecream-after.png)

この既に行われた変更の上から変更を再適用すると、競合が解決されるので、変更が成功します。

![](media/function-revert/icecream-success.png)

