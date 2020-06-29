---
title: Defaults 関数 | Microsoft Docs
description: Power Apps での Defaults 関数の構文と例を含む参照情報
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
ms.openlocfilehash: ad3d8198d73a698abb771aef7230c12b48ff0f56
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3305349"
---
# <a name="defaults-function-in-power-apps"></a>Power Apps での Defaults 関数
[データ ソース](../working-with-data-sources.md) の既定値を返します。  

## <a name="description"></a>内容
**Defaults** 関数を使用して、データ入力フォームを事前設定し、入力を容易にします。

この関数は、データ ソースの既定値を含む[レコード](../working-with-tables.md#records) を返します。  データ ソース内の[列](../working-with-tables.md#columns) に既定値がない場合、そのプロパティは存在しません。

データ ソースは提供する既定の情報の量によって異なり、まったく提供しないものもあります。  既定値をサポートしない[コレクション](../working-with-data-sources.md#collections) または別のデータ ソースを操作する場合、**Defaults** 関数は、[空](function-isblank-isempty.md) レコードを返します。

**Defaults** 関数を **[Patch](function-patch.md)** 関数と組み合わせて、[レコードを作成します](../working-with-data-sources.md)。

## <a name="syntax"></a>構文
**Defaults**( *DataSource* )

* *DataSource* – 必須。 既定値を設定するためのデータ ソース。

## <a name="examples"></a>例

| 計算式 | 内容 | 結果 |
| --- | --- | --- |
| **Defaults(&nbsp;Scores&nbsp;)** |**Scores** データ ソースの既定値を返します。 |**{ スコア: 0 }** |

