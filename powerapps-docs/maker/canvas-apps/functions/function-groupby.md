---
title: GroupBy および Ungroup 関数 | Microsoft Docs
description: Power Apps での GroupBy および Ungroup 関数の構文と例を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/26/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 47a71ab36d67cd3b6862b7d3fe6503b9053108c8
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3305119"
---
# <a name="groupby-and-ungroup-functions-in-power-apps"></a>Power Apps での GroupBy および Ungroup 関数
[テーブル](../working-with-tables.md) の[レコード](../working-with-tables.md#records) のグループ化とグループ化解除を行います。

## <a name="description"></a>内容
**GroupBy** 関数は、1 つ以上の[列](../working-with-tables.md#columns) の値に基づいてレコードを一緒にグループ化したテーブルを返します。 同じグループのレコードは単一のレコードに配置され、残りの列の入れ子になったテーブルを保持する列が追加されます。   

**Ungroup** 関数は、**GroupBy** プロセスを逆にします。 この関数は、一緒にグループ化されていたレコードをそれぞれのレコードに分割してテーブルを返します。

**GroupBy** を使用してレコードをグループ化し、返されたテーブルを変更し、次に **Ungroup** を使用して変更されたテーブルのレコードのグループ化を解除することができます。 たとえば、次の方法でレコードのグループを削除できます。

* **GroupBy** 関数を使用します。
* **[Filter](function-filter-lookup.md)** 関数を使用して、レコードのグループ全体を削除します。
* **Ungroup** 関数を使用します。  

グループ化に基づいて結果を集計することもできます。

* **GroupBy** 関数を使用します。
* **[Sum](function-aggregates.md)**、**[Average](function-aggregates.md)**、およびその他の集計関数とともに **[AddColumns](function-table-shaping.md)** 関数を使用して、グループ テーブルの集計である新しい列を追加します。
* **[DropColumns](function-table-shaping.md)** 関数を使用してグループ テーブルをドロップします。

**Ungroup** は、**GroupBy** に供給されたレコードの元の順序を維持しようとします。  これは常にできるとは限りません (たとえば、元のテーブルに*空白*レコードが含まれている場合です)。

テーブルは、文字列や数値と同じように、Power Apps の値です。 関数の引数としてテーブルを指定し、関数はテーブルを返すことができます。 **GroupBy** および **Ungroup** はテーブルを変更せず、代わりに、テーブルを引数として受け取り、別のテーブルを返します。 詳細については、[テーブルの使用](../working-with-tables.md) に関するページを参照してください。

## <a name="syntax"></a>構文
**GroupBy**( *Table*, *ColumnName1* [, *ColumnName2*, ... ], *GroupColumnName* )

* *Table* - 必須。 グループ化するテーブル。
* *ColumnName(s)* - 必須。  レコードをグループ化する*テーブル*内の列名。  これらの列は、結果のテーブルの列になります。
* *GroupColumnName* - 必須。  *ColumnName(s)* にないレコード データの記憶域の列名。
  
    > [!NOTE]
  > 名前にスペースが使われている SharePoint と Excel のデータ ソースの場合、各スペースを **"\_x0020\_"** として指定します。 たとえば、**"Column Name"** を **"Column_x0020_Name"** として指定します。

**Ungroup**( *Table*, *GroupColumnName* )

* *Table* - 必須。 グループ化を解除するテーブル。
* *GroupColumnName* - 必須。 **GroupBy** 関数を用いたレコード データの設定を含む列。
  
    > [!NOTE]
  > 名前にスペースが使われている SharePoint と Excel のデータ ソースの場合、各スペースを **"\_x0020\_"** として指定します。 たとえば、**"Column Name"** を **"Column_x0020_Name"** として指定します。

## <a name="examples"></a>例
### <a name="create-a-collection"></a>コレクションの作成
1. ボタンを追加し、その **[Text](../controls/properties-core.md)** プロパティを設定し、ボタンに**オリジナル**と表示されるようにします。
2. **オリジナル**ボタンの **[OnSelect](../controls/properties-core.md)** プロパティを次の数式に設定します。

```powerapps-dot   
ClearCollect( CityPopulations, 
    { City: "London",    Country: "United Kingdom", Population: 8615000}, 
    { City: "Berlin",    Country: "Germany",        Population: 3562000}, 
    { City: "Madrid",    Country: "Spain",          Population: 3165000}, 
    { City: "Rome",      Country: "Italy",          Population: 2874000}, 
    { City: "Paris",     Country: "France",         Population: 2273000}, 
    { City: "Hamburg",   Country: "Germany",        Population: 1760000}, 
    { City: "Barcelona", Country: "Spain",          Population: 1602000}, 
    { City: "Munich",    Country: "Germany",        Population: 1494000}, 
    { City: "Milan",     Country: "Italy",          Population: 1344000}
)
```

3. Alt キーを押しながら、**オリジナル**ボタンを選択します。
   
    次のデータが含まれた **CityPopulations** という名前の[コレクション](../working-with-data-sources.md#collections) が作成されました。
   
    ![](media/function-groupby/cities.png)
4. このコレクションを表示するには、**ファイル** メニューの**コレクション**を選択し、次に **CityPopulations** コレクションを選択します。  コレクション内の最初の 5 つのレコードが表示されます。
   
    ![](media/function-groupby/citypopulations-collection.png)

### <a name="group-records"></a>レコードのグループ化
1. 他のボタンを追加し、その **[Text](../controls/properties-core.md)** プロパティを **"グループ"** に設定します。
2. このボタンの **[OnSelect](../controls/properties-core.md)** プロパティを次の数式に設定します。
   
    **ClearCollect( CitiesByCountry, GroupBy( CityPopulations, "Country", "Cities" ) )**
3. Alt キーを押しながら、**グループ** ボタンを選択します。
   
    前のコレクションのレコードが、**国**列によってグループ化されている **CitiesByCountry** という名前のコレクションが作成されました。
   
    ![](media/function-groupby/cities-grouped.png)
4. このコレクションに含まれている最初の 5 つのレコードを表示するには、**ファイル** メニューの**コレクション**を選択します。
   
    ![](media/function-groupby/citiesbycountry-collection.png)
5. 国の市区町村の人口を表示するには、その国 (例: ドイツ) の**市区町村**列内のテーブル アイコンを選択します。
   
    ![](media/function-groupby/population-germany.png)

### <a name="filter-and-ungroup-records"></a>レコードのフィルターおよびグループ化解除
1. 他のボタンを追加し、その **[Text](../controls/properties-core.md)** プロパティを設定し、ボタンが **"フィルター"** と表示されるようにします。
2. このボタンの **[OnSelect](../controls/properties-core.md)** プロパティを次の数式に設定します。
   
    **ClearCollect( CitiesByCountryFiltered, Filter( CitiesByCountry, "e" in Country ) )**
3. Alt キーを押しながら、追加したボタンを選択します。
   
    名前に "e" を持つ (つまり、スペインまたはイタリアではない) これらの国のみを含む、**CitiesByCountryFiltered** という名前の 3 つ目のコレクションが作成されました。
   
    ![](media/function-groupby/cities-grouped-hase.png)
4. もう 1 つボタンを追加し、その **[Text](../controls/properties-core.md)** プロパティを設定し、ボタンが **"グループ化の解除"** と表示されるようにします。
5. このボタンの **[OnSelect](../controls/properties-core.md)** プロパティを次の数式に設定します。
   
    **ClearCollect( CityPopulationsUngrouped, Ungroup( CitiesByCountryFiltered, "Cities" ) )**
   
    結果は次のようになります。
   
    ![](media/function-groupby/cities-hase.png)

### <a name="aggregate-results"></a>結果の集計
このほか、グループ化したテーブルでは結果を集計することができます。  この例では、各国の主な市区町村の人口を合計します。

1. 他のボタンを追加し、その **[Text](../controls/properties-core.md)** プロパティを設定し、**"合計"** と表示されるようにします。
2. **"合計"** ボタンの **[OnSelect](../controls/properties-core.md)** プロパティを次の数式に設定します。
   
    **ClearCollect( CityPopulationsSum, AddColumns( CitiesByCountry, "Sum of City Populations", Sum( Cities, Population ) ) )**
   
    結果は次のようになります。
   
    ![](media/function-groupby/cities-sum.png)
   
    **[AddColumns](function-table-shaping.md)** では、ベースである **CitiesByCountry** コレクションで始まり、新しい列である**市区町村人口の合計**が追加されます。  この列の値では、数式 **Sum( Cities, Population )** に基づいて、行単位で計算されます。  **AddColumns** は、各行に**市区町村**列 (テーブル) の値を提供し、**[合計](function-aggregates.md)** は、このサブ テーブルの各行に**人口**を追加します。

    これで、必要な合計が得られたので、**[DropColumns](function-table-shaping.md)** を使用してサブ テーブルを削除できます。
  
3. 他のボタンを追加し、**"SumOnly"** と表示されるように、その **[Text](../controls/properties-core.md)** プロパティを設定します。
4. **"SumOnly"** ボタンの **[OnSelect](../controls/properties-core.md)** プロパティを次の数式に設定します。

    **ClearCollect( CityPopulationsSumOnly, DropColumns( CityPopulationsSum, "Cities" ) )**
   
    結果は次のようになります。
   
    ![](media/function-groupby/cities-sum-drop-cities.png)
   
    このテーブルのグループ化を解除する必要がなかったことに注意してください。

