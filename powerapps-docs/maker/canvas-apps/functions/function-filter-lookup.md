---
title: Filter、Search、および LookUp 関数 | Microsoft Docs
description: Power Apps での Filter および LookUp 関数の構文と例を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 02/05/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8941352930e9978da6062f81fcf1e1ddb7700529
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3305257"
---
# <a name="filter-search-and-lookup-functions-in-power-apps"></a>Power Apps での Filter、Search、および LookUp 関数
[テーブル](../working-with-tables.md) で、1 つ以上の[レコード](../working-with-tables.md#records) を検索します。

## <a name="description"></a>内容
**Filter** 関数は、数式を満たすテーブルでのレコードを検索します。  **Filter** を使用して 1 つ以上の条件に一致する一連のレコードを検索し、そうしないレコードを破棄します。

**LookUp** 関数は、数式を満たすテーブルでの最初のレコードを検索します。  **LookUp** を使用して 1 つ以上の条件に一致する単一レコードを検索します。

どちらの場合も、数式はテーブルの各レコードに対して評価されます。  結果が *true* であるレコードは、結果に含まれます。  標準的な数式の [演算子](operators.md)に加えて、サブストリング照合には **[in](operators.md#in-and-exactin-operators)** および **[exactin](operators.md#in-and-exactin-operators)** 演算子を使用できます。

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

**Search** 関数は、いずれかの列に文字列を含むテーブルのレコードを検索します。 この文字列は、列内のどこにでも現れることがあり、たとえば、"昌" または "平"を検索すると、"昌平" を含む列で一致が検出されます。 検索では大文字と小文字を区別しません。 **Filter** および **LookUp** とは異なり、**Search** 関数は、数式の代わりに一致する単一文字列を使用します。

**Filter** および **Search** は、元のテーブルと同じ列を含むテーブルと条件に一致するレコードを返します。 **LookUp** は、レコードを単一の値に減らす数式を適用した後に、最初に見つかったレコードのみを返します。 レコードが見つからない場合、**Filter** および **Search** は[空](function-isblank-isempty.md) のテーブルを返し、**LookUp** は*空白*を返します。  

[テーブル](../working-with-tables.md) は、文字列や数値と同じように、Power Apps 内での値です。 関数に渡して、関数から返すことができます。  **Filter**、 **Search**、および **LookUp** はテーブルを変更しません。 代わりに、引数としてテーブルを受け取り、そこからテーブル、レコード、または単一の値を返します。 詳細については、[テーブルの使用](../working-with-tables.md) に関するページを参照してください。

[!INCLUDE [delegation](../../../includes/delegation.md)]

## <a name="syntax"></a>構文
**Filter**( *Table*, *Formula1* [, *Formula2*, ... ] )

* *Table* - 必須。 検索するテーブル。
* *Formula(s)* - 必須。 テーブルの各レコードが評価される数式。 関数は、結果が **true** のすべてのレコードを返します。 テーブル内の列を参照することができます。 複数の数式を指定した場合、すべての数式の結果は **[And](function-logicals.md)** 関数を使用して組み合わせられます。

**Search**( *Table*, *SearchString*, *Column1* [, *Column2*, ... ] )

* *Table* - 必須。 検索するテーブル。
* *SearchString* - 必須。 検索のための文字列。 *空白*または空の文字列の場合は、すべてのレコードが返されます。
* *Column(s)* - 必須。 検索する *Table* 内の列の名前。 検索する列には、テキストが含まれている必要があります。 列の名前は、文字列であり、および二重引用符で囲まれている必要があります。 ただし、列の名前は静的である必要があり、数式では計算できません。 *SearchString* が、これらの列のいずれかのデータ内で部分一致として見つかった場合、レコード全体が返されます。

> [!NOTE]
> 名前にスペースが使われている SharePoint と Excel のデータ ソースの場合、各スペースを **"\_x0020\_"** として指定します。 たとえば、**"Column Name"** を **"Column_x0020_Name"** として指定します。

**LookUp**( *Table*, *Formula* [, *ReductionFormula* ] )

* *Table* - 必須。 検索するテーブル。 UI で、構文が関数ボックスの上に*ソース*として表示されます。
* *Formula* - 必須。
  テーブルの各レコードが評価される数式。 関数は結果が **true** の最初のレコードを返します。 テーブル内の列を参照することができます。 UI で、構文が関数ボックスの上に*条件*として表示されます。
* *ReductionFormula* - オプション。 この数式は、検出されたレコードに対して評価し、次にレコードを単一の値に減らします。 テーブル内の列を参照することができます。 このパラメーターを使用しない場合、関数はテーブルからレコード全体を返します。 UI で、構文が関数ボックスの上に*結果*として表示されます。

## <a name="examples"></a>例
次の例では、**IceCream** [データ ソース](../working-with-data-sources.md) を使用します。

![](media/function-filter-lookup/icecream.png)

| 計算式 | 内容 | 結果 |
| --- | --- | --- |
| **Filter( IceCream, OnOrder > 0 )** |**OnOrder** が 0 より大きいレコードを返します。 |<style> img {最大幅: なし;} </style> ![](media/function-filter-lookup/icecream-onorder.png) |
| **Filter( IceCream, Quantity + OnOrder > 225 )** |**数量**および **OnOrder** 列の合計が 225 より大きいレコードを返します。 |![](media/function-filter-lookup/icecream-overstock.png) |
| **Filter( IceCream, "chocolate" in Lower( Flavor ) )** |大文字または小文字に関係なく、**Flavor** の名前に "chocolate" という単語が表示されるレコードを返します。 |![](media/function-filter-lookup/icecream-chocolate.png) |
| **Filter( IceCream, Quantity < 10 && OnOrder < 20 )** |**数量**が 10 未満および **OnOrder** が 20 未満のレコードを返します。  これらの条件に一致するレコードがないため、空のテーブルが返されます。 |![](media/function-filter-lookup/icecream-empty.png) |
| **Search( IceCream, "choc", "Flavor" )** |大文字または小文字に関係なく、**Flavor** の名前に "choc" という文字列が表示されるレコードを返します。 |![](media/function-filter-lookup/icecream-chocolate.png) |
| **Search( IceCream, "", "Flavor" )** |検索語句が空であるため、すべてのレコードが返されます。 |![](media/function-filter-lookup/icecream.png) |
| **LookUp( IceCream, Flavor = "Chocolate", Quantity )** |**Flavor** が "chocolate" に等しいレコードを検索し、その中でそれは 1 つあります。  見つかった最初のレコードについて、そのレコードの**数量**を返します。 |100 |
| **LookUp( IceCream, Quantity > 150, Quantity + OnOrder )** |**Quantity** が 100 を超えるレコードを検索し、その中でそれは複数あります。  見つかった最初のレコード 、"Vanilla" の **Flavor** に関して、**数量**および **OnOrder** 列の合計を返します。 |250 |
| **LookUp( IceCream, Flavor = "Pistachio", OnOrder )** |**Flavor** が "Pistachio" に等しいレコードを検索し、その中にそれは存在しません。  見つからなかったため、**Lookup** は *空白* を返します。 |*空白* |
| **LookUp( IceCream, Flavor = "Vanilla" )** |**Flavor** が "Vanilla" に等しいレコードを検索し、その中でそれは 1 つあります。  換算公式が指定されなかったため、レコード全体が返されます。 |{ Flavor: "Vanilla", Quantity: 200, OnOrder: 75 } |

### <a name="search-user-experience"></a>検索のユーザー エクスペリエンス
多くのアプリでは、検索ボックスに 1 つ以上の文字を入力して、大きなデータ セット内のレコードの一覧をフィルター処理することができます。 入力すると、一覧には、検索条件に一致するレコードのみが表示されます。

このトピックの残りの部分にある例では、次のデータを含む**顧客**という名前のリストを検索した結果を表示しています。

![](media/function-filter-lookup/customers.png)

このデータ ソースをコレクションとして作成するには、**[ボタン](../controls/control-button.md)** コントロールを作成し、その **OnSelect** プロパティを次の数式に設定します。

**ClearCollect( Customers, Table( { Name: "Fred Garcia", Company: "Northwind Traders" }, { Name: "Cole Miller", Company: "Contoso" }, { Name: "Glenda Johnson", Company: "Contoso" }, { Name: "Mike Collins", Company: "Adventure Works" }, { Name: "Colleen Jones", Company: "Adventure Works" } ) )**

この例に示すように、画面下部にある[**ギャラリー コントロール**](../controls/control-gallery.md)にレコードの一覧を表示できます。 画面の上部には、ユーザーが関心のあるレコードを指定できるように、**SearchInput** という名前の[**テキスト入力**](../controls/control-text-input.md) コントロールを追加できます。

![](media/function-filter-lookup/customers-ux-unfiltered.png)

ユーザーが **SearchInput** に文字を入力すると、ギャラリーの結果は自動的にフィルター処理されます。 この場合、ギャラリーは、(会社の名前ではなく) 顧客の名前が **SearchInput** の文字シーケンスで始まるレコードを表示するように構成されています。 ユーザーが検索ボックスに **co** と入力する場合、ギャラリーには次の結果が表示されます。

![](media/function-filter-lookup/customers-ux-startswith-co.png)

**Name** 列に基づいてフィルター処理するには、ギャラリー コントロールの **Items** プロパティを次の数式のいずれかに設定します。

| 計算式 | 内容 | 結果 |
| --- | --- | --- |
| **Filter( Customers, StartsWith( Name, SearchInput.Text ) )** |**Customers** データ ソースで、検索文字列が **Name** 列の先頭に出現するレコードをフィルター処理します。 このテストでは、大文字と小文字が区別されません。 ユーザーが検索ボックスに **co** と入力した場合、ギャラリーには、**Colleen Jones** と **Cole Miller** が表示されます。 ギャラリーに **Mike Collins** が表示されないのは、そのレコードの **Name** 列の先頭に検索文字列がないためです。 |<style> img {最大幅: なし} </style> ![](media/function-filter-lookup/customers-name-co-startswith.png) |
| **Filter( Customers, SearchInput.Text in Name )** |**Customers** データ ソースで、検索文字列が **Name** 列のどこかに出現するレコードをフィルター処理します。 このテストでは、大文字と小文字が区別されません。 ユーザーが検索ボックスに **co** と入力した場合、ギャラリーには、**Colleen Jones**、**Cole Miller**、 そして **Mike Collins** が表示されます。これは、検索文字列が、これらすべてのレコードの **Name** 列のどこかに出現しているためです。 |<style> img {最大幅: なし} </style> ![](media/function-filter-lookup/customers-name-co-contains.png) |
| **Search( Customers, SearchInput.Text, "Name" )** |**in** 演算子を使用した場合と同様、**Search** 関数は、各レコードの **Name** 列内で一致を検索します。 列名を二重引用符で囲む必要があることに注意してください。 |<style> img {最大幅: なし} </style> ![](media/function-filter-lookup/customers-name-co-contains.png) |

**Name** 列だけでなく **Company** 列を含めるように検索範囲を広げることができます。

| 計算式 | 内容 | 結果 |
| --- | --- | --- |
| **Filter( Customers, StartsWith( Name, SearchInput.Text ) &#124;&#124; StartsWith( Company, SearchInput.Text ) )** |**Customers** データ ソースで、**Name** 列または **Company** 列の先頭に検索文字列 (たとえば、**co**) があるレコードをフィルター処理します。  どちらか一方の **StartsWith** 関数が *true* の場合、[**&#124;&#124;** 演算子](operators.md) は *true* になります。 |<style> img {最大幅: なし} </style> ![](media/function-filter-lookup/customers-all-co-startswith.png) |
| **Filter( Customers, SearchInput.Text in Name &#124;&#124; SearchInput.Text in Company )** |**Customers** データ ソースで、**Name** 列または **Company** 列の中に検索文字列 (たとえば、**co**) が含まれているレコードをフィルター処理します。 |<style> img {最大幅: なし} </style> ![](media/function-filter-lookup/customers-all-co-contains.png) |
| **Search( Customers, SearchInput.Text, "Name", "Company" )** |**in** 演算子を使用した場合と同様、**Search** 関数は、**Customers** データ ソースで、**Name** 列または **Company** 列の中に検索文字列 (たとえば、**co**) が含まれているレコードを検索します。 複数の列と複数の **in** 演算子を指定する場合は、**Filter** よりも **Search** 関数の方が読み書きが簡単です。 列の名前を二重引用符で囲む必要があることに注意してください。 |<style> img {最大幅: なし} </style> ![](media/function-filter-lookup/customers-all-co-contains.png) |

