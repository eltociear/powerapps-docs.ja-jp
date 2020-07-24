---
title: Refresh 関数 | Microsoft Docs
description: Power Apps での Refresh 関数の構文と例を含む参照情報
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
ms.openlocfilehash: 8376d21117c286a540ca8b873c7e91b07d53d607
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3304774"
---
# <a name="refresh-function-in-power-apps"></a>Power Apps の Refresh 関数
[データ ソース](../working-with-data-sources.md) の [レコード](../working-with-tables.md#records) を更新します。

## <a name="description"></a>内容
**Refresh** 関数は、データ ソースの新しいコピーを取得します。  他のユーザーが加えた変更が表示されます。

**Refresh** には戻り値が存在せず、[動作の数式](../working-with-formulas-in-depth.md) 内でのみ使用できます。

## <a name="syntax"></a>構文
**Refresh**( *DataSource* )

* *DataSource* – 必須。 更新するデータ ソース。

## <a name="example"></a>例
この例では、次のデータから始まる、**IceCream** という名前のデータ ソースを更新します。

![](media/function-refresh/icecream.png)

別のデバイスのユーザーが、**Strawberry** レコードの **Quantity** を **400** に変更します。  この計算式が実行されるまで、この変更は表示されません。

**Refresh( IceCream )**

その数式が実行された後、**IceCream** データ ソースにバインドされたギャラリーに、更新後の **Strawberry** の値が表示されます。

![](media/function-refresh/icecream-after.png)

