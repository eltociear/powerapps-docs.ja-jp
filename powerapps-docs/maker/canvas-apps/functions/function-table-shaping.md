---
title: AddColumns、DropColumns、RenameColumns、および ShowColumns 関数 | Microsoft Docs
description: 構文と例を含む PowerApps の AddColumns、DropColumns、RenameColumns、および ShowColumns 関数の参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/04/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 55e38d2be5f43e1b13fc1894f88aac26a26bd57e
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2019
ms.locfileid: "74678214"
---
# <a name="addcolumns-dropcolumns-renamecolumns-and-showcolumns-functions-in-powerapps"></a>PowerApps の AddColumns、DropColumns、RenameColumns、および ShowColumns 関数
[列](../working-with-tables.md#columns)の追加、削除、名前の変更、選択により、[テーブル](../working-with-tables.md)の表示を調整します。

## <a name="overview"></a>概要
これらの関数は、列を調整することでテーブルの表示を調整します。

* 複数の列を持つテーブルを単一列にし、 **[Lower](function-lower-upper-proper.md)** や **[Abs](function-numericals.md)** といった単一列関数で使用できるようにします。  
* 計算列をテーブルに追加します (たとえば、**Quantity** を **Unit Price** で乗算した結果を示す **Total Price** 列)。
* ユーザーに表示するため、または数式で使用するために、列の名前をよりわかりやすく変更します。

テーブルは、文字列や数値と同じように、Power Apps の値です。  テーブルは数式内で引数として指定できるほか、関数から結果として返すことができます。

> [!NOTE]
> このトピックで説明する関数は、元のテーブルを変更しません。 代わりに、そのテーブルを引数として受け取り、変換が適用された新しいテーブルを返します。 詳細については、[テーブルの使用](../working-with-tables.md)に関するページを参照してください。  

これらの関数を使用しても、[データ ソース](../working-with-data-sources.md)の列は変更できません。 そのデータは、ソースで変更する必要があります。 **[Collect](function-clear-collect-clearcollect.md)** 関数を使用して、[コレクション](../working-with-data-sources.md#collections)に列を追加できます。 詳細については、[データ ソースの使用](../working-with-data-sources.md)に関するページを参照してください。  

## <a name="description"></a>Description
**AddColumns** 関数は、テーブルに列を追加し、数式でその列内の値を定義します。 既存の列は変更されません。

数式はテーブルの各レコードについて評価されます。
[!INCLUDE [record-scope](../../../includes/record-scope.md)]

**DropColumns** 関数は、テーブルから列を除外します。  その他すべての列は変更されません。 **DropColumns** は列を除外し、**ShowColumns** は列を表示します。

**RenameColumns** 関数を使用して、テーブルの 1 つ以上の列の名前を変更します。この操作は、テーブルに含まれる列の名前 (置換対象の古い名前) と、テーブルに含まれない列の名前 (使用する新しい名前) を指定する、引数のペアを少なくとも 1 つ指定することで実行します。 以前の名前はテーブルに既に存在している必要があり、新しい名前は存在していてはなりません。 各列名は、古い列名または新しい列名のいずれかとして、引数リストに一度だけ表示できます。 列の名前を既存の列名に変更するには、まず **DropColumns** を使用して既存の列を削除するか、または 1 つの **RenameColumns** 関数を別の関数内に入れ子にすることで既存の列名を変更します。

**ShowColumns** 関数は、テーブルの列を表示し、その他すべての列を削除します。 **ShowColumns** を使用して、複数列テーブルから単一列テーブルを作成できます。  **ShowColumns** は列を表示し、**DropColumns** は列を除外します。  

これらすべての関数の結果は、変換が適用された新しいテーブルになります。 元のテーブルは変更されません。 数式を含む既存のテーブルを変更することはできません。 SharePoint、Common Data Service、SQL Server、およびその他のデータソースは、多くの場合、スキーマと呼ばれるリスト、エンティティ、およびテーブルの列を変更するためのツールを提供します。 このトピックの関数は、元のを変更せずに入力テーブルを変換し、さらに使用できるように出力テーブルに変換するだけです。

これらの関数の引数は、委任をサポートしています。 たとえば、関連レコードをプルする引数として使用される**フィルター**関数は、 **' [dbo]. [AllListings] '** データソースには、100万行が含まれています:

```powerapps-dot
AddColumns( RealEstateAgents, 
    "Listings",  
    Filter(  '[dbo].[AllListings]', ListingAgentName = AgentName ) 
)
```

ただし、これらの関数の出力には、[非委任レコードの制限](../delegation-overview.md#non-delegable-limits)が適用されます。  この例では、 **Realestateagents**データソースに501以上のレコードがある場合でも、500レコードだけが返されます。

この方法で**Addcolumns**を使用する場合、**フィルター**は、 **realestateagents**の最初の各レコードに対して、データソースを個別に呼び出す必要があります。これにより、多数のネットワーク chatter が発生します。 **[Dbo]. [AllListings**は十分に小さく、頻繁に変更されないため、 [**OnStart**](signals.md#app)で**Collect**関数を呼び出して、アプリの起動時にデータソースをキャッシュすることができます。 別の方法として、ユーザーが要求したときにのみ関連レコードをプルするようにアプリを再構築することもできます。  

## <a name="syntax"></a>構文
**AddColumns**( *Table*, *ColumnName1*, *Formula1* [, *ColumnName2*, *Formula2*, ... ] )

* *Table* - 必須。  操作の対象となるテーブル。
* *ColumnName(s)* - 必須。 追加する列の名前。  この引数には、文字列を指定する必要があります (たとえば、二重引用符を含む **"Name"** など)。
* *Formula(s)* - 必須。  各レコードについて評価する数式。 結果は、対応する新しい列の値として追加されます。 この数式では、テーブルの他の列を参照できます。

**DropColumns**( *Table*, *ColumnName1* [, *ColumnName2*, ... ] )

* *Table* - 必須。  操作の対象となるテーブル。
* *ColumnName(s)* - 必須。 削除する列の名前。 この引数には、文字列を指定する必要があります (たとえば、二重引用符を含む **"Name"** など)。

**RenameColumns**( *Table*, *OldColumnName1*, *NewColumnName1* [, *OldColumnName2*, *NewColumnName2*,...])

* *Table* - 必須。  操作の対象となるテーブル。
* *OldColumnName* - 必須。 元のテーブルから名前を変更する列の名前。 この要素は、引数のペアの先頭に (または、数式に複数のペアが含まれている場合は、各引数の先頭に) 表示されます。 この名前は、文字列である必要があります (たとえば、二重引用符を含む **"Name"** など)。
* *NewColumnName* - 必須。 置換後の名前。 この要素は、引数のペアの末尾に (または、数式に複数のペアが含まれている場合は、各引数のペアの末尾に) 表示されます。 この引数には、文字列を指定する必要があります (たとえば、二重引用符を含む **"Customer Name"** など)。

**ShowColumns**( *Table*, *ColumnName1* [, *ColumnName2*, ... ] )

* *Table* - 必須。  操作の対象となるテーブル。
* *ColumnName(s)* - 必須。 表示する列の名前。 この引数には、文字列を指定する必要があります (たとえば、二重引用符を含む **"Name"** など)。

## <a name="examples"></a>例
このセクションの例では、次のテーブルにデータが含まれている **IceCreamSales** データ ソースを使用します。

![](media/function-table-shaping/icecream.png)

これらの例ではいずれも、**IceCreamSales** データ ソースは変更されません。 各関数は、データ ソースの値をテーブルに変換し、その値を結果として返します。

| 数式 | Description | 結果 |
| --- | --- | --- |
| **AddColumns( IceCreamSales, "Revenue", UnitPrice * QuantitySold )** |結果に **Revenue** 列を追加します。  各レコードで **UnitPrice * QuantitySold** が評価され、その結果が新しい列に配置されます。 |<style> img { max-width: none; } </style> ![](media/function-table-shaping/icecream-add-revenue.png) |
| **DropColumns( IceCreamSales, "UnitPrice" )** |結果から **UnitPrice** 列を除外します。 この関数は列の除外に使用し、**ShowColumns** は列の表示に使用します。 |![](media/function-table-shaping/icecream-drop-price.png) |
| **ShowColumns( IceCreamSales, "Flavor" )** |結果に **Flavor** 列のみを表示します。 この関数は列の表示に使用し、**DropColumns** は列の除外に使用します。 |![](media/function-table-shaping/icecream-select-flavor.png) |
| **RenameColumns( IceCreamSales, "UnitPrice", "Price")** |結果の**UnitPrice**列の名前を変更します。 |![](media/function-table-shaping/icecream-rename-price.png) |
| **RenameColumns( IceCreamSales, "UnitPrice", "Price", "QuantitySold", "Number")** |結果内の **UnitPrice** 列と **QuantitySold** 列の名前を変更します。 |![](media/function-table-shaping/icecream-rename-price-quant.png) |
| **DropColumns(<br>RenameColumns(<br>AddColumns( IceCreamSales, "Revenue",<br>UnitPrice * QuantitySold ),<br>"UnitPrice", "Price" ),<br>"Quantity" )** |次のテーブル変換を、数式の内側から順に実行します。 <ol><li>**UnitPrice * Quantity** のレコードごとの計算に基づいて、**Revenue** 列を追加します。<li>**UnitPrice** という名前を **Price** に変更します。<li>**Quantity** 列を除外します。</ol>  この順番は重要なので、注意してください。 たとえば、名前を変更した後は、**UnitPrice** を使用した計算ができません。 |![](media/function-table-shaping/icecream-all-transforms.png) |

### <a name="step-by-step"></a>ステップ バイ ステップ

このトピックで既に説明した例をいくつか試してみましょう。  

1. **[ボタン](../controls/control-button.md)** コントロールを追加し、その**onselect**プロパティを次の数式に設定して、コレクションを作成します。

    ```powerapps-dot
    ClearCollect( IceCreamSales, 
        Table(
            { Flavor: "Strawberry", UnitPrice: 1.99, QuantitySold: 20 }, 
            { Flavor: "Chocolate", UnitPrice: 2.99, QuantitySold: 45 },
            { Flavor: "Vanilla", UnitPrice: 1.50, QuantitySold: 35 }
        )
    )
    ```

1. Alt キーを押したまま、ボタンを選択して数式を実行します。

1. 2番目の**ボタン**コントロールを追加し、その**onselect**プロパティを次の数式に設定して、実行します。

    ```powerapps-dot
    ClearCollect( FirstExample, 
        AddColumns( IceCreamSales, "Revenue", UnitPrice * QuantitySold )
    ) 
    ```
1. **[ファイル]** メニューの **[コレクション]** をクリックし、 **[IceCreamSales]** を選択してそのコレクションを表示します。
 
    この図に示すように、2番目の数式はこのコレクションを変更しませんでした。 **Addcolumns**関数は、読み取り専用の引数として**IceCreamSales**を使用しています。関数は、その引数が参照するテーブルを変更しませんでした。
    
    ![収益列を含まないアイスクリーム販売コレクションの3つのレコードを表示するコレクションビューアー](media/function-table-shaping/ice-cream-sales-collection.png)

1. **[Firstexample]** を選択します。

    この図に示すように、2番目の数式は追加された列を含む新しいテーブルを返しました。 **Clearcollect**関数は、 **firstexample**コレクションの新しいテーブルをキャプチャし、ソースを変更せずに関数を介してフローした元のテーブルに追加します。

    ![新しい収益列を含む最初のサンプルコレクションの3つのレコードを表示するコレクションビューアー](media/function-table-shaping/first-example-collection.png)
