---
title: 演算子および識別子 | Microsoft Docs
description: Power Apps の演算子および識別子に関する構文と例を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/20/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a38930c24954867d9253b53c2f7cb24b86aed2c1
ms.sourcegitcommit: 4b6f187c9501332f9acca5978fa326621f2980e5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/22/2020
ms.locfileid: "3394049"
---
# <a name="operators-and-identifiers-in-power-apps"></a>Power Apps の演算子と識別子

これらの演算子の一部は、作成者の言語に依存します。  詳細については、[グローバル アプリ](../global-apps.md) に関する記事を参照してください。


|                               記号                                |                        種類​​                         |                                                                                    構文                                                                                    |                                                                                                                           内容                                                                                                                            |
|---------------------------------------------------------------------|-----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                **.**                                |                  プロパティ セレクター                  |                                                               **Slider1.Value<br>Color.Red<br>Acceleration.X**                                                               |                                               [テーブル](../working-with-tables.md)、コントロール、[シグナル](signals.md) または列挙体からプロパティを抽出します。  旧バージョンとの互換性のために **!** を使用することもできます。                                                |
| **.**<br>[[言語依存](../global-apps.md)]  |                  小数点                  |                                                             **1.23**                                                           |                                                                              数値の整数部分と小数部分の区切り記号。 この文字は言語に依存します。                                                                              |
|                               **( )**                               |                     かっこ                     |                                                               **Filter(T, A &lt; 10)**<br><br>**(1 + 2) \* 3**                                                               |                                                                                           優先順位を変更し、式の中の副次式をグループ化する                                                                                           |
|                                **+**                                |                算術演算子                 |                                                                                  **1 + 2**                                                                                   |                                                                                                                             加算                                                                                                                             |
|                                **-**                                |                       &nbsp;                        |                                                                                  **2-1**                                                                                   |                                                                                                                       減算および符号                                                                                                                       |
|                              *                               |                       &nbsp;                        |                                                                                  **2 \* 3**                                                                                  |                                                                                                                          乗算                                                                                                                          |
|                                **/**                                |                       &nbsp;                        |                                                                                  **2 / 3**                                                                                   |                                                                                                   除算 (**[Mod](function-mod.md)** 関数も参照してください)                                                                                                    |
|                                **^**                                |                       &nbsp;                        |                                                                                  **2 ^ 3**                                                                                   |                                                                                          累乗、**[Power](function-numericals.md)** 関数に相当します                                                                                          |
|                                **%**                                |                       &nbsp;                        |                                                                                   **20%**                                                                                    |                                                                                                         百分率 (&quot;\* 1/100&quot; に相当します)                                                                                                          |
|                                **=**                                |                比較演算子                 |                                                                               **Price = 100**                                                                                |                                                                                                                             と等しい                                                                                                                             |
|                              **&gt;**                               |                       &nbsp;                        |                                                                              **Price &gt; 100**                                                                              |                                                                                                                           より大きい                                                                                                                           |
|                              **&gt;=**                              |                       &nbsp;                        |                                                                             **Price &gt;= 100**                                                                              |                                                                                                                     以上である                                                                                                                     |
|                              **&lt;**                               |                       &nbsp;                        |                                                                              **Price &lt; 100**                                                                              |                                                                                                                            より小さい                                                                                                                             |
|                              **&lt;=**                              |                       &nbsp;                        |                                                                             **Price &lt;= 100**                                                                              |                                                                                                                      以下である                                                                                                                       |
|                            **&lt;&gt;**                             |                       &nbsp;                        |                                                                            **Price &lt;&gt; 100**                                                                            |                                                                                                                           と等しくない                                                                                                                           |
|                              **&amp;**                              |            文字列連結演算子            |                                                      **&quot;hello&quot; &amp; &quot; &quot; &amp; &quot;world&quot;**                                                       |                                                                                                             複数の文字列を続けて表示します                                                                                                             |
|                      **&amp;&amp;** または **And**                      |                  論理演算子                  |                                       **Price &lt; 100 &amp;&amp; Slider1.Value = 20**<br>または **Price &lt; 100 And Slider1.Value = 20**                                       |                                                                                         論理積、**[And](function-logicals.md)** 関数に相当します                                                                                          |
|                     **&#124;&#124;** または **Or**                      |                       &nbsp;                        |                                        **Price &lt; 100 &#124;&#124; Slider1.Value = 20** または **Price &lt; 100 Or Slider1.Value = 20**                                        |                                                                                          論理和、**[Or](function-logicals.md)** 関数に相当します                                                                                          |
|                          **!** または **Not**                           |                       &nbsp;                        |                                                              **!(Price &lt; 100)** または **Not (Price &lt; 100)**                                                               |                                                                                           論理否定、**[Not](function-logicals.md)** 関数に相当します                                                                                           |
|                             **exactin**                             |  [メンバーシップ演算子](#in-and-exactin-operators)  |                                                                   **Gallery1.Selected exactin SavedItems**                                                                   |                                                                                       [コレクション](../working-with-data-sources.md#collections) またはテーブルに属しています                                                                                        |
|                             **exactin**                             |                       &nbsp;                        |                                           **&quot;Windows&quot; exactin “Windows オペレーティング システムで Windows を表示するには...”**                                            |                                                                                                                 部分文字列をテストします (大文字小文字を区別します)                                                                                                                  |
|                               **に含まれる**                                |                       &nbsp;                        |                                                                     **Gallery1.Selected in SavedItems**                                                                      |                                                                                                               コレクションまたはテーブルに属しています                                                                                                               |
|                               **に含まれる**                                |                       &nbsp;                        |                                                      **&quot;The&quot; in &quot;The keyboard and the monitor...&quot;**                                                      |                                                                                                                部分文字列をテストします (大文字小文字を区別しません)                                                                                                                 |
|                                **@**                                | [曖昧性除去演算子](#disambiguation-operator) |                                                                           **MyTable[@fieldname]**                                                                            |                                                                                                                       フィールドの曖昧性を除去します                                                                                                                       |
|                                **@**                                |                       &nbsp;                        |                                                                              **[@MyVariable]**                                                                               |                                                                                                                      グローバルの曖昧性を除去します                                                                                                                       |
| **,**<br>[[言語依存](../global-apps.md)]  |                   リスト区切り記号                    | **If( X < 10, "Low", "Good" )**<br>**{ X: 12, Y: 32 }**<br>**[ 1, 2, 3 ]** | 以下の要素を区切ります。 <ul><li>関数呼び出しの引数</li><li>[レコード](../working-with-tables.md#elements-of-a-table) のフィールド</li><li>[テーブル](../working-with-tables.md#inline-value-tables) のレコード</li></ul> この文字は言語に依存します。 |
| **;**<br>[[言語依存](../global-apps.md)] |                  数式のチェーン                   |                                     **Collect(T, A); Navigate(S1, &quot;&quot;)**                                     |                                                                          関数の呼び出しの動作プロパティを区切ります。 このチェーン演算子は言語に依存します。                                                                          |
|                             **セルフ**                              |         [Self 演算子](#self-and-parent-operators)         |                                                                               **Self.Fill**                                                                                |                                                                                                           現在のコントロールのプロパティへのアクセス                                                                                                             |
|                             **親**                              |         [Parent 演算子](#self-and-parent-operators)         |                                                                               **Parent.Fill**                                                                                |                                                                                                           コントロール コンテナーのプロパティにアクセスする                                                                                                            |
|                            **ThisItem**                             |       [ThisItem 演算子](#thisitem-operator)       |                                                                            **ThisItem.FirstName**                                                                            |                                                                                                          ギャラリーまたはフォーム コントロールのフィールドにアクセスする                                                                                                           |

## <a name="in-and-exactin-operators"></a>in 演算子と exactin 演算子
**[in](operators.md#in-and-exactin-operators)** 演算子と **[exactin](operators.md#in-and-exactin-operators)** 演算子を使用して、コレクションやインポートされたテーブルなどの [データ ソース](../working-with-data-sources.md) 内の文字列を検索できます。 **[in](operators.md#in-and-exactin-operators)** 演算子は、大文字小文字を無視して一致する文字列を識別し、**[exactin](operators.md#in-and-exactin-operators)** 演算子は、大文字小文字が一致する文字列のみを識別します。 次に例を示します。

1. **在庫**という名前のコレクションを作成またはインポートし、[ギャラリーでのイメージとテキストの表示](../show-images-text-gallery-sort-filter.md) で説明している最初の手順に従って、それをギャラリーに表示します。
2. ギャラリーの **[Items](../controls/properties-core.md)** プロパティを次の数式に設定します。
   <br>**Filter(Inventory, "E" in ProductName)**

    ギャラリーには、指定した文字が名前に含まれていない唯一の製品である Callisto を除くすべての製品が表示されます。
3. ギャラリーの **[Items](../controls/properties-core.md)** プロパティを次の数式に変更します。
   <br>**Filter(Inventory, "E" exactin ProductName)**

    ギャラリーには、指定した大文字が名前に含まれている唯一の製品である Europa のみが表示されます。

## <a name="thisitem-operator"></a>ThisItem 演算子
**[ギャラリー](../controls/control-gallery.md)**、**[編集フォーム](../controls/control-form-detail.md)**、または **[表示フォーム](../controls/control-form-detail.md)** コントロールをテーブルまたはコレクションにバインドすることによって、テーブルまたはコレクションのデータを表示することができます。  これらのコントロールは、他のカードおよびコントロールのコンテナーです。  コンテナー内のカードまたはコントロールは、**[ThisItem](operators.md#thisitem-operator)** 演算子を通して、バインドされているデータにアクセスできます。   

**[ThisItem](operators.md#thisitem-operator)** 演算子を使用して、外側のコントロール内の各カードまたは各コントロールに表示されるデータの [列](../working-with-tables.md#columns) を指定します。 たとえば、「[Show images and text in a gallery](../show-images-text-gallery-sort-filter.md)」 (イメージとテキストをギャラリーに表示する) の製品ギャラリーでは、この演算子は、製品のデザインを表示するイメージ コントロール、製品名を表示する上のラベル、および在庫数を示す下のラベルを指定しています。

入れ子になっているギャラリーでは、**[ThisItem](operators.md#thisitem-operator)** は、最も内側のギャラリー アイテムを参照します。 内側と外側のギャラリーの行フィールドが競合していないことを前提として、修飾されていないフィールド (列) 名を直接使用することもできます。 この方法によって、内側のギャラリーが外側のギャラリーのアイテムを参照するというルールが有効になります。

## <a name="self-and-parent-operators"></a>Self および Parent 演算子

数式内でコントロールとそのプロパティを参照するには、3 つの方法があります:

| メソッド | 内容 |
|--------|-------------|
| コントロール名別 |  コントロールは、アプリ内のどこからでも、名前で参照することができます。<br><br>例えば、**Label1.Fill** は名前が **Label1** であるコントロールの Fill プロパティを参照します。  | 
| **Self** 演算子 | 数式を作成するときに、同じコントロールの別のプロパティを参照すると便利な場合があります。  名前による絶対参照を使用する代わりに、1 つの*Self* への相対参照を使用する方が簡単で移植性が高くなります。  **Self** 演算子は、現在のコントロールに簡単にアクセスできるようにします。<br><br>例えば、**Self.Fill** は現在のコントロールの塗りつぶしの色を参照します。   |
| **Parent** 演算子 | 一部のコントロールは、**[画面](../controls/control-screen.md)** や **[ギャラリー](../controls/control-gallery.md)** コントロールなど、他のコントロールをホストします。 内部のコントロールのホスティング コントロールは、*親* と呼ばれます。  **Self** 演算子と同様に、**Parent** 演算子は、コンテナー コントロールへの簡単な相対参照を提供します。<br><br>例えば、**Parent.Fill** は、現在のコントロールのコンテナーであるコントロールの fill プロパティを参照します。 |

**Self** と **Parent** は演算子であり、コントロール自体のプロパティではありません。 **Parent.Parent**、**Self.Parent** または **Parent.Self** への参照はサポートされていません。

## <a name="identifier-names"></a>識別子名

変数、データ ソース、列、およびその他のオブジェクトの名前に、[Unicode](https://en.wikipedia.org/wiki/Unicode) を含めることができます。

スペースまたはその他の特殊文字を含む名前は単一引用符で囲みます。  2 つの単一引用符を共に使用して、名前内で 1 つの単一引用符を表します。  特殊文字を含まない名前は、単一引用符は必要ありません。

テーブルで使用される可能性のある列名の例、および数式で表す方法を示します。

| データベースの列名   | 数式の列参照 |
|-----------------------------|-------------------------------|
| SimpleName                  | ```SimpleName``` |
| NameWith123Numbers          | ```NameWith123Numbers``` |
| スペースを含む名前            | ```'Name with spaces'``` |
| 「二重」引用符で囲まれた名前   | ```'Name with "double" quotes'``` |
| 「単一」引用符で囲まれた名前   | ```'Name with ''single'' quotes'``` |
| @ アット マークが付いた名前      | ```'Name with an @ at sign'``` |

二重引用符は、[テキスト文字列を指定する](data-types.md#embedded-text) ために使用されます。  

## <a name="display-names-and-logical-names"></a>表示名および論理名
SharePoint および Common Data Service のような一部のデータ ソースには、同じテーブルまたはデータ列を参照する 2 つの異なる名前があります。

* **論理名** - 一意であることが保証され、作成された後に変更されず、通常はスペースやその他の特殊文字を使用することはできず、異なる言語にローカライズされていない名前。  その結果として、名前は不可解なものになることがあります。  これらの名前は、プロの開発者が使用しています。  例えば、**cra3a_customfield** です。  この名前は、**スキーマ名**、または単に**名前**として参照されることもあります。

* **表示名** - ユーザー フレンドリーで、エンド ユーザーに表示されることを目的とした名前。  この名前は一意ではなく、時間とともに変化することがあり、スペースと任意の Unicode 文字が含まれ、異なる言語にローカライズされる可能性があります。  上記の例に対応して、表示名は単語の間にスペースあある**カスタム フィールド**になることがあります。
 
表示名は理解しやすいので、キャンバス アプリはそれらを選択肢として提案し、論理名は提案しません。  論理名は推奨されませんが、直接入力した場合、使用されます。

たとえば、あなたが**カスタム フィールド**を Common Data Service のエンティティに追加したと仮定します。  論理名はシステムによって割り当てられ、フィールドの作成時にのみ変更できます。  結果は次のようになります。

> [!div class="mx-imgBorder"]  
> ![カスタム フィールドが追加された Accounts エンティティ。表示名「カスタム フィールド」と論理名「cr5e3_customfield」が表示されています](media/operators/customfield_portal.png)

アカウントのフィールドへの参照を作成するとき、これは表示名なので、**カスタム フィールド**固有名の提案が使用されます。  この名前にはスペースが含まれているため、一重引用符を使用する必要があることに注意してください。

> [!div class="mx-imgBorder"]  
> ![表示名「カスタム フィールド」が強調表示された取引先のフィールド名の提案を示す Studio 数式バー](media/operators/customfield_suggest_display.png)

候補を選択した後「カスタム フィールド」が数式バーに表示され、データが取得されます。 

> [!div class="mx-imgBorder"]  
> ![フィールドに対する表示名「カスタム フィールド」の使用を示す Studio 数式バー](media/operators/customfield_display.png)

推奨されませんが、このフィールドには論理名を使用することもできます。  これにより、同じデータが取得されます。  この名前にはスペースや特殊文字が含まれていないため、単一引用符は必要ないことに注意してください。

> [!div class="mx-imgBorder"]  
> ![フィールドに対する論理名 cr5e3_customfield の使用を示す Studio 数式バー](media/operators/customfield_logical.png)

バックグラウンドで、数式に表示される表示名と基になる論理名との間のマッピングが維持されます。  データ ソースとの対話には論理名を使用する必要があるため、このマッピングは、現在の表示名から論理名に自動的に変換するために使用され、ネットワーク トラフィックに表示されます。  たとえば、表示名が変更されたり、また別の言語のメーカーがアプリを編集したりする場合など、このマッピングは新しい表示名に切り替えるため論理名に戻すためにも使用されます。

> [!NOTE] 
> 環境間でアプリを移動する場合、論理名は翻訳されません。  Common Data Service システム エンティティおよびフィールド名について、論理名は環境間で一貫しているため、これは問題にはなりません。  ただし、上記のこの例の **cra3a_customfield** などのカスタム フィールドは異なる環境の接頭辞を持つことがあります (この場合、**cra3a**)。  新しい環境では表示名に対して照合できるため、表示名が推奨されます。 

## <a name="name-disambiguation"></a>名前の曖昧性を除去します
表示名は一意ではないため、同じエンティティ内に同じ表示名が 1 回以上表示されることがあります。  これが発生すると、論理名は競合する名前の 1 つに対してかっこ内の表示名の最後に追加されます。  上記の例に基づき、論理名が **cra3a_customfieldalt** で、同じ**カスタム フィールド**の表示名の 2 番目のフィールドが存在する場合、提案が次のように表示されます。

> [!div class="mx-imgBorder"]  
> ![2 つのバージョンの「カスタム フィールド」の曖昧さを解消するための論理名 cr5e3_customfieldalt の使用を示している Studio の数式バー](media/operators/customfield_suggest_alt.png)

エンティティの名前、オプション セット、およびその他の Common Data Service アイテムなど、名前の競合が発生する他の状況では、名前の曖昧性解消文字列が追加されます。 

## <a name="disambiguation-operator"></a>曖昧性除去演算子
一部の関数では、各レコードの処理中に、テーブルのフィールドにアクセスするための [レコード スコープ](../working-with-tables.md#record-scope) を作成します (**Filter**、**AddColumns**、**Sum** など)。  レコード スコープによって追加されたフィールド名は、アプリの別の場所にある同じ名前を上書きします。  これが発生した場合でも、**@** 曖昧性除去演算子を使用して、レコード スコープの外部の値にアクセスできます。

* 入れ子になったレコード スコープの値にアクセスするには、次のパターンを使用した操作対象のテーブルの名前の **@** 演算子を使います。<br>_Table_**[@**_FieldName_**]**
* データ ソース、コレクション、およびコンテキスト変数などのグローバル値にアクセスするには、**[@**_オブジェクト名_**]** のパターンを使用します (テーブルは指定しません)。

詳細および例については、[レコード スコープ](../working-with-tables.md#record-scope) を参照してください。

