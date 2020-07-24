---
title: キャンバス アプリのテーブルについて | Microsoft Docs
description: Power Apps でのキャンバス アプリのテーブル、列、およびレコードの操作に関する参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/23/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 777dd5452af8662569e2e51452142a1bbce3f619
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/13/2020
ms.locfileid: "3308799"
---
# <a name="understand-canvas-app-tables-and-records-in-power-apps"></a>Power Apps でのキャンバス アプリのテーブルとレコードについて

Power Apps では、データがレコードとテーブルに格納された Microsoft Excel、SharePoint、SQL Server、その他のいくつかのソースの情報にアクセスするキャンバス アプリを作成できます。 この種類のデータを効率的に操作できるように、これらの構造の基になる概念を確認しておきましょう。

* レコードには、個人、場所、または物に関する 1 つ以上の情報カテゴリが含まれます。 たとえば、1 つのレコードに、単一の顧客の名前、電子メール アドレス、電話番号が含まれます。 他のツールでは、レコードを "行"や "項目" として参照します。
* テーブルは、同じ情報カテゴリを含む 1 つまたは複数のレコードを保持します。 たとえば、1 つのテーブルに 50 人の顧客の名前、電子メール アドレス、電話番号が含まれます。

アプリでは、[数式](working-with-formulas.md)を使用してレコードとテーブルを作成、更新、操作します。 おそらく、拡張テーブルである外部の[データ ソース](working-with-data-sources.md)へのデータの読み取りおよび書き込みをします。 さらに、1 つまたは複数の内部テーブルを作成する場合があります。これは、[コレクション](working-with-data-sources.md#collections)と呼ばれます。

Excel の式が引数として 1 つまたは複数のセルの参照を受け取るのと同様に、引数としてテーブルの名前を受け取るさまざまな式を作成できます。 Power Apps の一部の式では、指定された他の引数を反映するテーブルが返されます。 たとえば、次のような数式を作成できます:

* **[Patch](functions/function-patch.md)** 関数に対する複数の引数の 1 つとしてそのテーブルを指定することで、テーブル内のレコードを更新します
* **[AddColumns](functions/function-table-shaping.md)** 関数、**[DropColumns](functions/function-table-shaping.md)** 関数、または **[RenameColumns](functions/function-table-shaping.md)** 関数の引数としてそのテーブルを指定することで、テーブル内の列を追加、削除、名前変更します。 これらの関数のいずれも、元のテーブルを変更することはありません。 代わりに、指定する他の引数に基づいて、関数は別のテーブルを返します。

## <a name="elements-of-a-table"></a>テーブルの要素
![](media/working-with-tables/elements-of-a-table.png)

### <a name="records"></a>レコード​​
各レコードには、人、場所、物についての少なくとも 1 つの情報カテゴリが含まれています。 上の例では、各製品 (**チョコレート**、**パン**、**水**) のレコードと、各情報カテゴリ (**価格**、**手持ち在庫数量**、**注文数量**) の列が示されています。

数式では、テーブルのコンテキストの外側で、中かっこを使用してレコード自体を参照できます。 たとえば、このレコード **{ 名前: "ストロベリー"、価格: 7.99 }** はテーブルに関連付けられていません。 この例では、**名前**や**価格**などのフィールド名が二重引用符で囲まれていないことに注意してください。

### <a name="fields"></a>フィールド
フィールドは、レコード内の個々の情報です。 この種のフィールドは特定のレコードの列の値として視覚化できます。

コントロールの場合と同様、レコードの **.** [演算子](functions/operators.md)を使用してレコードのフィールドを参照します。  たとえば、**First(Products).Name** は、**製品**テーブル内の 1 つ目のレコードに対する**名前**フィールドを返します。

**[GroupBy](functions/function-groupby.md)** 関数の例が示すように、フィールドに別のレコードやテーブルを含めることができます。 必要なだけ多くのレベルのレコードとテーブルを入れ子にできます。

### <a name="columns"></a>列
列は、テーブル内の 1 つまたは複数のレコードの同じフィールドを参照します。 上の例では、各製品に価格フィールドがあり、その価格はすべての製品で同じ列にあります。  上のテーブルでは、上部に横に並んだ 4 つの列があります。

* **名前**
* **価格**
* **手持ち在庫数量**
* **注文数量**

列の名前には、その列のフィールドが反映されます。

列内のすべての値は、同じデータ型です。 上の例で、 「手持ち在庫数量」 列には常に数値が含まれ、1 つのレコードだけ 「12 ユニット」 のような文字列を含むことはできません。  任意のフィールドの値も*空白*になる場合があります。  

他のツールでは、列が "フィールド" と呼ばれたこともあります。

> [!NOTE]
> SharePoint および名前にスペースが使われている列を含む Excel のデータ ソースの場合、Power Apps はスペースを **"\_x0020\_"** に置き換えます。 たとえば、SharePoint の **"列名"** または Excel は、データレイアウトまたは数式で表示すると、Power Apps では **"Column_x0020_Name"** として表示されます。

### <a name="table"></a>Table
テーブルは 1 つ以上のレコードで構成され、各レコードには複数のフィールドであり、レコード間で名前が一貫しています。

データ ソースやコレクションに格納されている任意のテーブルには名前があり、テーブルを参照したり、引数として受け取る関数に渡すために使用します。  テーブルを関数や数式の結果にすることもできます。

次の例に示すように、**[Table](functions/function-table.md)** 関数を使用して、一連のレコードを中かっこで表すことにより、数式をテーブルで表すことができます。

`Table( { Value: "Strawberry" }, { Value: "Vanilla" } )`

角かっこを使用して、単一の列テーブルを定義することもできます。  上記を書き込む同等の方法:

`[ "Strawberry", "Vanilla" ]`

## <a name="table-formulas"></a>テーブルの数式
Excel と Power Apps では、似た方法で数式を使用してテキストの数値と文字列を操作します:

* Excel では、セル **A1** に **42** などの値を入力してから、別のセルに **A1+2** などの数式を入力して、**44** の値が表示されます。
* Power Apps では、**Slider1** の **[Default](controls/properties-core.md)** プロパティを **42** に、ラベルの **[Text](controls/properties-core.md)** プロパティを **Slider1.Value + 2** に設定して、**44** の値を表示します。

どちらの場合も、引数の値 (たとえば、セル **A1** の数値や **Slider1** の値) を変更すると、計算された値が自動的に変更されます。

同様に、数式を使用して、テーブルやレコード内のデータにアクセスし、操作することができます。 **カタログ** テーブルの**価格**列内の最小値を表示する **Min(Catalog, Price)** など、テーブルの名前を一部の数式の引数として使用します。 **RenameColumns(Catalog, "Price", "Cost")** など、テーブル全体を戻り値として提供する他の数式もあります。これは、**カタログ** テーブルからのすべてのレコードを返しますが、**価格**列の名前を**コスト**に変更します。

数値の場合と同様、テーブルやレコードを含む数式は、基になるテーブルやレコードが変更されると自動的に再計算されます。 **カタログ** テーブルにある製品のコストが以前の最小値よりも小さくなった場合、**[Min](functions/function-aggregates.md)** 数式の戻り値がそれに合わせて自動的に変更されます。

単純な例をいくつか見ていきましょう。

1. 電話用の空のアプリを作成し、他のコントロールを含む垂直方向の **[Gallery](controls/control-gallery.md)** コントロールを追加します。

    既定では、画面には **CustomGallerySample** という名前のテーブルからのプレースホルダー テキストが表示されます。 画面の **[ギャラリー](controls/control-gallery.md)** コントロールの **[Items](controls/properties-core.md)** プロパティは自動的にそのテーブルに設定されます。

    ![](media/working-with-tables/gallery-items.png)

    > [!NOTE]
    > 一部のコントロールは、例示の目的で再配置され、拡大されました。

2. **[Items](controls/properties-core.md)** プロパティをテーブルの名前に設定する代わりに、次の例のように、テーブルの名前を引数として含む数式に設定します:

    `Sort(CustomGallerySample, SampleHeading, Descending)`

    この数式では **[Sort](functions/function-sort.md)** 関数が組み込まれています。これはテーブルの名前を最初の引数として、そのテーブル内の列の名前を 2 つ目の引数として受け取ります。 また、省略可能な 3 つ目の引数もサポートしており、データを降順で並べ替えるように指定します。

    ![](media/working-with-tables/gallery-items-sort.png)

3. 次の例のように、**[Items](controls/properties-core.md)** プロパティを、前の手順から数式を引数として受け取り、テーブルを返す数式に設定します。

    `FirstN(Sort(CustomGallerySample, SampleHeading, Descending), 2)`

    この数式では、**[FirstN](functions/function-first-last.md)** 関数を使用して、テーブルの特定の数のレコードを表示します。 **[Sort](functions/function-sort.md)** 関数を **[FirstN](functions/function-first-last.md)** への 1 つ目の引数として使用し、数値 (この場合、**2**) を 2 つ目の引数として使用します。これにより表示するレコードの数を指定します。

    数式全体は、**CustomGallerySample** テーブルの最初の 2 つのレコードを含むテーブルを返し、**SampleHeading** 列で降順に並べ替えられます。

    ![](media/working-with-tables/gallery-items-sort-firstn.png)

## <a name="table-functions-and-control-properties"></a>Table 関数とコントロール プロパティ

**Lower** 関数について検討しましょう。 変数 **welcome** がテキスト文字列 **"Hello, World"** を含む場合、数式 **Lower( welcome )** は **"hello, world"** を返します。  この関数は、まったくその変数の値を変更しません。 **Lower** は入力の処理と出力の生成のみを実行する、純粋な関数です。 それ以外の機能はなく、副作用もありません。 Excel のすべての関数と Power Apps のほとんどの関数は純粋な関数であり、ワークブックまたはアプリを自動的に再計算できます。

Power Apps は、同じ方法でテーブルを操作する一連の関数を提供します。 これらの関数は、テーブルを入力として受け取り、データのテーブル全体をフィルタ―処理、並べ替え、変換、削減、および要約します。 実際には、**Lower** 関数や、通常は単一の値を受け取る他の多くの関数も、単一列テーブルを入力として受け取ります。

* **[Sort](functions/function-sort.md)**、**[Filter](functions/function-filter-lookup.md)** - レコードを並べ替えたりフィルター処理します。
* **[FirstN](functions/function-first-last.md)**、**[LastN](functions/function-first-last.md)** - テーブルの最初の N または最後の N レコードを返します。
* **[Abs](functions/function-numericals.md)**、**[Sqrt](functions/function-numericals.md)**、**[Round](functions/function-round.md)**、**[RoundUp](functions/function-round.md)**、**[RoundDown](functions/function-round.md)** - 単一列テーブルの各レコードに対する算術演算で、結果は単一列テーブルになります。
* **[Left](functions/function-left-mid-right.md)**、 **[Mid](functions/function-left-mid-right.md)**、 **[Right](functions/function-left-mid-right.md)**、**[Replace](functions/function-replace-substitute.md)**、 **[Substitute](functions/function-replace-substitute.md)**、 **[Trim](functions/function-trim.md)**、 **[Lower](functions/function-lower-upper-proper.md)**、 **[Upper](functions/function-lower-upper-proper.md)**、 **[Proper](functions/function-lower-upper-proper.md)** - 単一列テーブルの各レコードに対する文字列操作で、文字列の単一列テーブルになります。
* **[Len](functions/function-len.md)** - 文字列の列の場合、各文字列の長さを含む単一列テーブルを返します。
* **[Concatenate](functions/function-concatenate.md)** - 文字列の複数の列を連結し、文字列の単一列テーブルになります。
* **[AddColumns](functions/function-table-shaping.md)**、**[DropColumns](functions/function-table-shaping.md)**、**[RenameColumns](functions/function-table-shaping.md)**、**[ShowColumns](functions/function-table-shaping.md)** - テーブルの列操作で、異なる列を持つ新しいテーブルになります。
* **[Distinct](functions/function-distinct.md)** - 重複したレコードを削除します。
* **[Shuffle](functions/function-shuffle.md)** - レコードをランダムな順序でシャッフルします。
* **[HashTags](functions/function-hashtags.md)** - 文字列でハッシュタグを検索します。
* **[Errors](functions/function-errors.md)** - データ ソースを使用する場合にエラー情報を提供します。

これらの関数の多くは、単一列テーブルを入力として受け取ります。 テーブル全体に列が 1 つしかない場合は、名前で指定できます。 テーブルに複数の列がある場合は、*Table.Column* 構文を使用してそれらの列の 1 つを指定できます。 例えば、**Products.Name** は、**製品**テーブルからの**名前**値のみの単一列テーブルを返します。

**[AddColumns](functions/function-table-shaping.md)**、**[RenameColumns](functions/function-table-shaping.md)**、**[ShowColumns](functions/function-table-shaping.md)**、または **[DropColumns](functions/function-table-shaping.md)** 関数を使用して、必要に応じてテーブルを完全に再整形できます。 この場合も、これらの関数は出力のみを変更し、ソースは変更しません。

コントロールのプロパティはテーブルにもなります:

* **Items** - ギャラリー、リスト ボックス、およびコンボ ボックスに適用します。 このプロパティは、ギャラリーまたはリストが表示するテーブルを定義します。
* **SelectedItems** - リスト ボックスおよびコンボ ボックスに適用します。 **SelectMultiple** が有効になっている場合、このプロパティはユーザーが選択した項目のテーブルを定義します。

## <a name="behavioral-formulas"></a>動作の数式

その他の関数はデータを変更するために特別に設計されており、副作用があります。 これらの関数は純粋ではないため、慎重に構築する必要があり、アプリでの値の自動再計算には使用できません。 これらの関数は、[動作の数式](working-with-formulas-in-depth.md)内でのみ使用できます。

* **[Collect](functions/function-clear-collect-clearcollect.md)**、**[Clear](functions/function-clear-collect-clearcollect.md)**、**[ClearCollect](functions/function-clear-collect-clearcollect.md)** - コレクションを作成し、クリアし、それにデータを追加します。
* **[Patch](functions/function-patch.md)** - レコードの 1 つ以上のフィールドを変更します。
* **[Update](functions/function-update-updateif.md)**、**[UpdateIf](functions/function-update-updateif.md)** - 指定する 1 つ以上の条件に一致するレコードを更新します。
* **[Remove](functions/function-remove-removeif.md)**、**[RemoveIf](functions/function-remove-removeif.md)** - 指定する 1 つ以上の条件に一致するレコードを削除します。

## <a name="record-formulas"></a>レコードの数式

個々のレコード用にデータを計算したり、個々のレコードを引数として受け取り、戻り値として返したりする数式も構築できます。 上記のギャラリーの例に戻り、**Gallery1.Selected** プロパティを使用して、ギャラリーでユーザーが選択する何らかのレコードからの情報を表示しましょう。

1. [**ボタン**](controls/control-button.md)を追加し、その **[OnSelect](controls/properties-core.md)** プロパティを次の数式に設定します:<br>
    **Collect( SelectedRecord, Gallery1.Selected )**

2. Alt キーを押しながら、ボタンを選択します。

3. **ファイル** メニューで、**コレクション**を選択します。

    ![](media/working-with-tables/selected-collection.png)

この数式は、ギャラリーで現在選択されているレコードからのデータだけでなく、そのギャラリーの各コントロールも含むレコードを返します。 たとえば、レコードには、元のテーブルの **SampleText** 列に対応する **SampleText** 列と、その列からのデータを表示するラベルを示す **Subtitle1** 列の両方が含まれます。 **Subtitle1** 列のテーブル アイコンを選択して、そのデータの詳細情報を確認します。

> [!NOTE]
> このトピックで指定する以外の要素を追加した場合、**Subtitle1** 列には **Subtitle2** または類似する名前が付けられる場合があります。

レコードを選択したので、**.** 演算子を使用してレコードから個々のフィールドを抽出できるようになります。

1. **[Label](controls/control-text-box.md)** コントロールを追加してから、ギャラリーとボタンの下に移動します。

1. ラベルの **[Text](controls/properties-core.md)** プロパティを次の数式に設定します:<br>
    **"Selected: " & Gallery1.Selected.SampleHeading**

    ![](media/working-with-tables/gallery-selected.png)

レコードである **Selected** プロパティを受け取り、そこから **SampleHeading** プロパティを抽出しました。

関連する名前付き値に対する汎用的コンテナーとしてレコードを使用することもできます。

* **[UpdateContext](functions/function-updatecontext.md)** 関数や **[Navigate](functions/function-navigate.md)** 関数を中心に数式を構築する場合は、レコードを使用して、更新する[コンテキスト変数](working-with-variables.md#use-a-context-variable)を収集できます。
* **[Edit form](controls/control-form-detail.md)** コントロールで **[Updates](controls/control-form-detail.md)** プロパティを使用して、ユーザーがフォームで加えた変更を収集します。
* **[Patch](functions/function-patch.md)** 関数を使用して、データ ソースを更新してレコードを結合します。

このような場合、レコードはテーブルの一部ではありませんでした。

## <a name="record-functions-and-control-properties"></a>レコード関数とコントロール プロパティ
レコードを返す関数:

* **[FirstN](functions/function-first-last.md)**、**[LastN](functions/function-first-last.md)** - 最初または最後のレコードまたはテーブルのレコードを返します。
* **[Lookup](functions/function-filter-lookup.md)** - 1 つ以上の条件に一致するテーブルからの最初のレコードを返します。
* **[Patch](functions/function-patch.md)** - データ ソースを更新するか、レコードを統合します。
* **[Defaults](functions/function-defaults.md)** - データ ソースの既定値を返します。

レコードを返すプロパティ:

* **Selected** - ギャラリーおよびリスト ボックスに適用します。 現在選択されているレコードを返します。
* **Updates** - ギャラリーに適用します。  ユーザーがデータ入力フォームで加えるすべての変更が 1 つにまとめられます。
* **[Update](functions/function-update-updateif.md)** - テキスト入力コントロールやスライダーなどの入力コントロールに適用します。 ギャラリーの個々のプロパティを 1 つにまとめて設定します。

## <a name="record-scope"></a>レコードのスコープ

一部の関数は、テーブルのすべてのレコード間で個別に数式を評価することにより動作します。 数式の結果は、さまざまな方法で使用されます:

* **AddColumns** - 数式は追加されるフィールドの値を提供します。
* **Average**、**Max**、**Min**、**Sum**、**StdevP**、**VarP** - 数式は集計する値を指定します。
* **Filter**、**Lookup** - 数式はレコードを出力に含めるかどうかを決定します。
* **Concat** - 数式は一緒に連結する文字列を決定します。
* **Distinct** - 数式は重複したレコードを識別するのに使用される 1 つの値を返します。
* **ForAll** - 数式は任意の値を返すことができ、副作用が生じる可能性もあります。
* **Sort** - 数式はレコードを並べ替えるための値を提供します。
* **With** - 数式は任意の値を返すことができ、副作用が生じる可能性もあります。

これらの数式内で、処理するレコードのフィールドを参照できます。 これらの関数ごとに、数式を評価するための "レコードのスコープ" が作成されます。この範囲にあるレコードのフィールドがは最上位の識別子として使用できます。 また、アプリ全体からのコントロール プロパティやその他の値を参照することもできます。

たとえば、**製品**のテーブルを見てみましょう:

![](media/working-with-tables/requested.png)

この例のテーブルをアプリに作成するには、ボタンを挿入して、**OnSelect** プロパティをこの数式に追加してから、ボタンを選択します (Power Apps Studio で Alt キーを押しながらボタンをクリックします):

```powerapps-dot
Set( Products,
    Table(
        { Product: "Widget",    'Quantity Requested': 6,  'Quantity Available': 3 },
        { Product: "Gadget",    'Quantity Requested': 10, 'Quantity Available': 20 },
        { Product: "Gizmo",     'Quantity Requested': 4,  'Quantity Available': 11 },
        { Product: "Apparatus", 'Quantity Requested': 7,  'Quantity Available': 6 }
    )
)
```

これらの製品のいずれかに、利用可能な数より多くの要求があったかどうかを判断するには:

`Filter( Products, 'Quantity Requested' > 'Quantity Available' )`

**Filter** への最初の引数は操作するレコードのテーブルで、2 つ目の引数は数式です。  **Filter** は、各レコードのフィールドが利用可能なこの数式を評価するためのレコード スコープを作成します。この場合は、**製品**、**要求された数量**、**在庫数量**です。  比較の結果によって、関数の結果に各レコードを含めるかどうかが決定されます:

![](media/working-with-tables/needed.png)

この例に追加して、各製品の受注量を計算できます:

```powerapps-dot
AddColumns( 
    Filter( Products, 'Quantity Requested' > 'Quantity Available' ), 
    "Quantity To Order", 'Quantity Requested' - 'Quantity Available'
)
```

ここでは、計算された列が結果に追加されます。 **AddColumns** には、要求された数量と在庫数量間の差の計算に使用するレコード スコープがあります。

![](media/working-with-tables/toorder.png)

最後に、結果テーブルを必要な列だけに減らすことができます。

```powerapps-dot
ShowColumns(
    AddColumns(
        Filter( Products, 'Quantity Requested' > 'Quantity Available' ),
        "Quantity To Order", 'Quantity Requested' - 'Quantity Available'
    ),
    "Product",
    "Quantity To Order"
)
```

![](media/working-with-tables/toorderonly.png)

上記では、二重引用符 (") を使用している箇所と単一引用符 (') を使用している箇所があることに注意してください。  単一引用符はフィールドやテーブルなどのオブジェクトの値を参照する際に使用します。オブジェクトの名前にはスペースが含まれます。  二重引用符は、オブジェクトの値を参照するのではなく、特に **AddColumns** の場合のように、オブジェクトがまだ存在しない状況でそれについて話している場合に使用されます。

## <a name="disambiguation"></a>曖昧性の除去

レコード スコープによって追加されたフィールド名は、アプリの別の場所にある同じ名前を上書きします。  これが発生した場合でも、[**@** 曖昧性除去](functions/operators.md)演算子を使用して、レコード スコープの外部からの値にアクセスできます:

* 入れ子になったレコード スコープの値にアクセスするには、次のパターンを使用した操作対象のテーブルの名前の **@** 演算子を使います。<br>_Table_**[@**_FieldName_**]**
* データ ソース、コレクション、およびコンテキスト変数などのグローバル値にアクセスするには、**[@**_オブジェクト名_**]** のパターンを使用します (テーブルは指定しません)。

操作対象のテーブルが、**Filter(** _Table_**,** ... **)** のような式である場合、曖昧性除去演算子は使用できません。  最も内側のレコード スコープのみが、曖昧性除去演算子を使用せずに、このテーブル式からのフィールドにアクセスできます。

たとえば、コレクション **X** があると仮定します:

![](media/working-with-tables/X.png)

このコレクションは、**ClearCollect( X, \[1, 2\] )** を使用して作成できます。

別のコレクション **Y**:

![](media/working-with-tables/Y.png)

**ClearCollect( Y, ["A", "B"] )** を使用してこのコレクションを作成できます。

さらに、**Value** という名前のコンテキスト変数を次の数式を使用して定義します: **UpdateContext( {Value: "!"} )**

これらを 1 つにまとめてみましょう。 このコンテキストでは、次の数式を使用します:

```powerapps-dot
Ungroup(
    ForAll( X,
        ForAll( Y,
            Y[@Value] & Text( X[@Value] ) & [@Value]
        )
    ),
    "Value"
)
```

次のテーブルが生成されます:

![](media/working-with-tables/XY.png)

数式を詳しく見てみましょう。  最も外側の **ForAll** 関数では **X** のレコード スコープが定義されます。これにより、処理の際に各レコードの**値**フィールドにアクセスできます。  単に**値**という単語か **X[@Value]** を使用してアクセスできます。

最も内側の **ForAll** 関数は **Y** の別のレコード スコープを定義します。このテーブルには定義された**値**フィールドもあるため、ここで**値**を使用すると **Y** のレコードのフィールドが参照され、**X** のフィールドは参照されなくなります。ここで、**X** の**値**フィールドにアクセスするには、曖昧性除去演算子を使用した長いバージョンを使用する必要があります。

**Y** は最も内側のレコード スコープのため、このテーブルのフィールドにアクセスする際に曖昧性除去は必要ありません。同じ結果になるこの数式を使用できます:

```powerapps-dot
Ungroup(
    ForAll( X,
        ForAll( Y,
            Value & Text( X[@Value] ) & [@Value]
        )
    ),
    "Value"
)
```

すべての **ForAll** レコード スコープはグローバル スコープを上書きします。 定義した **Value** コンテキスト変数は、曖昧性除去演算子がなければ名前で参照することができません。 この値にアクセスするには、**[@Value]** を使用します。

**Ungroup** は、入れ子になった **ForAll** 関数が入れ子になった結果テーブルとなるため、結果をフラット化します。

## <a name="single-column-tables"></a>単一列テーブル

テーブルからの単一列を操作するには、この例のように **ShowColumns** 関数を使用します:

```powerapps-dot
ShowColumns( Products, "Product" )
```

この数式は、この単一列テーブルを生成します:

![](media/working-with-tables/single-column.png)

より短い代替策に関しては、*Table.Column* を指定し、*テーブル*からの*列*の単一列のテーブルを抽出します。 たとえば、この数式は **ShowColumns** を使用した場合と全く同じ結果を生成します。

```powerapps-dot
Products.Product
```

## <a name="inline-records"></a>インライン レコード

名前付きフィールド値を含む中かっこを使用して、レコードを表します。  たとえば、次の数式を使用して、このトピックの冒頭に出てきたテーブル内の最初のレコードを表すことができます:

`{ Name: "Chocolate", Price: 3.95, 'Quantity on Hand': 12, 'Quantity on Order': 10 }`

次の例に示すように、数式を他の数式に埋め込むこともできます:

`{ Name: First(Products).Name, Price: First(Products).Price * 1.095 }`

次の例に示すように、中かっこを入れ子にすると、レコードを入れ子にすることができます。

`{ 'Quantity': { 'OnHand': ThisItem.QuantOnHand, 'OnOrder': ThisItem.QuantOnOrder } }`

空白やコロンなどの特殊文字が含まれる各列名を、単一引用符で囲みます。  列名内で単一引用符を使用するには、二重にします。

**価格**列の値にはドル記号などの通貨記号が含まれていない点に注意してください。 この書式は、値が表示される際に適用されます。  

## <a name="inline-tables"></a>インライン テーブル
**[Table](functions/function-table.md)** 関数と一連のレコードを使用して、テーブルを作成します。 このトピックの冒頭で出てきたテーブルを、次の数式で表すことができます:

```powerapps-dot
Table( 
    { Name: "Chocolate", Price: 3.95, 'Quantity on Hand': 12, 'Quantity on Order': 10 },
    { Name: "Bread", Price: 4.95, 'Quantity on Hand': 34, 'Quantity on Order': 0 },
    { Name: "Water", Price: 4.95, 'Quantity on Hand': 10, 'Quantity on Order': 0 } 
)
```

また、テーブルを入れ子にすることができます:

```powerapps-dot
Table( 
    { Name: "Chocolate", 
      'Quantity History': Table( { Quarter: "Q1", OnHand: 10, OnOrder: 10 },
                                 { Quarter: "Q2", OnHand: 18, OnOrder: 0 } ) 
    }
)
```

## <a name="inline-value-tables"></a>インライン値テーブル
値を角かっこで指定することにより、単一列テーブルを作成できます。 結果のテーブルには、**値**という名前の単一列があります。

例えば、`[ 1, 2, 3, 4 ]` は `Table( { Value: 1 }, { Value: 2 }, { Value: 3 }, { Value: 4 } )` に相当し、次のテーブルを返します:

![](media/working-with-tables/inline-table.png)

