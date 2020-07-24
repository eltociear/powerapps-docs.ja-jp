---
title: DataSourceInfo 関数 | Microsoft Docs
description: Power Apps での DataSourceInfo 関数の構文と例を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/11/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 559549a1221ed5e6d5c683a5a3cbaf0f2e9960ed
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3305418"
---
# <a name="datasourceinfo-function-in-power-apps"></a>Power Apps での DataSourceInfo 関数
[データ ソース](../working-with-data-sources.md) に関する情報を提供します。

## <a name="overview"></a>概要
データ ソースは、ユーザー エクスペリエンスを最適化するために貴重な情報を提供できます。

**[Patch](function-patch.md)** 関数を使用する前に、[列](../working-with-tables.md#columns) レベルの情報を使用して、ユーザー入力を検証し、ユーザーに即時フィードバックを提供することができます。 **[Validate](function-validate.md)** 関数はこの同じ情報を使用します。

データ ソース レベルで情報を使用して、たとえば、[レコード](../working-with-tables.md#records) を編集および作成するためのアクセス許可を持たないユーザーに対して、**編集**および**新規作成**ボタンを無効または非表示にすることができます。

データ ソースは提供する情報の量によって異なり、まったく提供しないものもあります。  [コレクション](../working-with-data-sources.md#collections) は情報を提供しません。 情報が提供されない場合は、既定が使用されるか、もしくは*空白*が返されます。

## <a name="description"></a>内容
### <a name="column-information"></a>列の情報
**DataSourceInfo** を使用すると、データ ソースの特定の列に関する情報を取得できます。  

| 情報の引数 | 結果の種類 | 内容 |
| --- | --- | --- |
| **DataSourceInfo.DisplayName** |文字列 |列の表示名。 表示名が定義されていない場合は、列名を返します。 |
| **DataSourceInfo.MaxLength** |番号 |列が保持できる最大文字数。 文字列が含まれている列にのみ適用されます。 最大数が設定されていない場合は、*空白*を返します。 |
| **DataSourceInfo.MaxValue** |番号 |列が保持できる最大数値。 数値が含まれている列にのみ適用されます。 最大数が設定されていない場合は、*空白*を返します。 |
| **DataSourceInfo.MinValue** |番号 |列が保持できる最小数値。 数値が含まれている列にのみ適用されます。 最小値が設定されていない場合は、*空白*を返します。 |
| **DataSourceInfo.Required** |Boolean |値はこの列に必要ですか? データ ソースによって設定されていない場合は、**false** を返します。 |

3 番目の引数は、文字列としての列の名前です。  たとえば、**人物**コレクションの **電話**の列は、二重引用符を含む **"Phone"** として渡されます。

### <a name="data-source-information"></a>データ ソースの情報
**DataSourceInfo** を使用すると、データ ソース全体に関する情報を取得することもできます。  

| 情報の引数 | 結果の種類 | 内容 |
| --- | --- | --- |
| **DataSourceInfo.AllowedValues** |Boolean |このデータ ソースに対してユーザーに付与できるアクセス許可の種類は何ですか? データ ソースによって設定されていない場合は、*空白*を返します。 |
| **DataSourceInfo.CreatePermission** |Boolean |現在のユーザーは、このデータ ソースでレコードを作成するアクセス許可を持っていますか? データ ソースによって設定されていない場合は、**true** を返します。 |
| **DataSourceInfo.DeletePermission** |Boolean |現在のユーザーは、このデータ ソースでレコードを削除するアクセス許可を持っていますか? データ ソースによって設定されていない場合は、**true** を返します。 |
| **DataSourceInfo.EditPermission** |Boolean |現在のユーザーは、このデータ ソースでレコードを編集するアクセス許可を持っていますか? データ ソースによって設定されていない場合は、**true** を返します。 |
| **DataSourceInfo.ReadPermission** |Boolean |現在のユーザーは、このデータ ソースでレコードを読み取りするアクセス許可を持っていますか?: データ ソースによって設定されていない場合は、**true** を返します。 |

## <a name="syntax"></a>構文
**DataSourceInfo**( *DataSource*, *Information*, *ColumnName* )

* *DataSource* – 必須。 使用するデータ ソース。
* *情報* – 必須。 取得する情報の種類。
* *ColumnName* – オプション。 列レベルの情報の場合は、列名を文字列として指定します。 **電話**の列は、二重引用符を含む **"電話"** として渡されます。 データ ソース レベルの情報に関しては、*ColumnName* 引数を使用することはできません。
  
    > [!NOTE]
  > 名前にスペースが使われている SharePoint と Excel のデータ ソースの場合、各スペースを **"\_x0020\_"** として指定します。 たとえば、**"Column Name"** を **"Column_x0020_Name"** として指定します。

## <a name="examples"></a>例
このセクションの例は、**IceCream** という名前のデータ ソースを使用します。

![](media/function-datasourceinfo/icecream.png)

このデータ ソースは、次の情報も提供します。

* **数量**の表示名は "手持ち在庫数量" です。
* **Flavor** の最大長は 30 文字です。
* **Flavor** 列には値を含める必要があります。 **数量** 列は必須ではありません。
* 最小**数量**は 0 です。
* 最大**数量**は 100 です。
* 現在のユーザーは、**IceCream** データ ソースのレコードの読み取りおよび編集を行うことができますが、レコードを作成および削除することはできません。

| 計算式 | 内容 | 結果 |
| --- | --- | --- |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.DisplayName,&nbsp;"Quantity"&nbsp;)** |**IceCream** データ ソースの**数量**列の表示名を返します。 |"手持ち在庫数量" |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.MaxLength,&nbsp;"Flavor"&nbsp;)** |**IceCream** データ ソースの **Flavor** 列の文字列の最大長を返します。 |30 |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.Required,&nbsp;"Flavor"&nbsp;)** |**IceCream** データ ソースの **Flavor** 列は必須ですか? |**True** |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.Required,&nbsp;"Quantity"&nbsp;)** |**IceCream** データ ソースの**数量**列は必須ですか? |**false** |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.MaxValue,&nbsp;"Quantity"&nbsp;)** |**IceCream** データ ソースの**数量**列の最大数値を返します。 |100 |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.MinValue,&nbsp;"Quantity"&nbsp;)** |**IceCream** データ ソースの**数量**列の最小数値を返します。 |0 |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.ReadPermission)** |現在のユーザーは **IceCream** データ ソースのレコードを読み取ることができますか? |**True** |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.EditPermission)** |現在のユーザーは **IceCream** データ ソースのレコードを編集できますか? |**True** |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.CreatePermission)** |現在のユーザーは **IceCream** データ ソースのレコードを作成できますか? |**false** |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.DeletePermission)** |現在のユーザーは **IceCream** データ ソースのレコードを削除できますか? |**false** |

