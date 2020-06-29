---
title: ForAll 関数 | Microsoft Docs
description: Power Apps での ForEach 関数の構文と例を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 08/15/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9bca1ffe29adb7a7eac55a89040b4ffa486fdc1d
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3305188"
---
# <a name="forall-function-in-power-apps"></a>Power Apps での ForAll 関数
値を計算し、[テーブル](../working-with-tables.md) のすべての[レコード](../working-with-tables.md#records) にアクションを実行します。

## <a name="description"></a>内容
**ForAll** 関数は、テーブルのすべてのレコードの数式を評価します。  数式は、値を計算したり、操作 (データの変更や接続の操作など) を実行したりできます。  [**With** 関数](function-with.md) を使用して、単一レコードの数式を評価します。

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

### <a name="return-value"></a>戻り値
各数式の評価結果は、入力テーブルと同じ順序でテーブルに返されます。

数式の結果が単一の値の場合は、結果のテーブルは単一列テーブルになります。  数式の結果がレコードの場合、結果のテーブルには、結果のレコードと同じ列を持つレコードが含まれます。  

数式の結果が*空白*値の場合、レコードがその入力レコードの結果テーブルに存在していません。  この場合、結果テーブルのレコードはソース テーブルよりも少なくなります。

### <a name="taking-action"></a>アクションの実行
数式には、**[Patch](function-patch.md)** および **[Collect](function-clear-collect-clearcollect.md)** 関数を用いてデータ ソースのレコードの変更など、アクションを実行する関数を含めることができます。  数式は、接続に対してメソッドを呼び出すこともできます。  [**;** 演算子](operators.md) を使用して、複数のアクションをレコードごとに実行できます。 **ForAll** 関数の対象となるテーブルを変更することはできません。

数式を記述する場合、レコードは任意の順序で、可能な場合は並行して、処理できることに注意してください。  テーブルの最初のレコードが最後のレコードの後に処理される場合があります。  順序の依存関係を避けるように注意してください。  したがって、**[UpdateContext](function-updatecontext.md)**、**[Clear](function-clear-collect-clearcollect.md)**、および **[ClearCollect](function-clear-collect-clearcollect.md)** 関数は、効果の影響を受けやすい変数を保持するために簡単に使用できるため、 **ForAll** 関数で使用することはできません。  **[Collect](function-clear-collect-clearcollect.md)** を使用することはできますが、レコードが追加される順序は定義されていません。

**Collect**、**Remove**、および **Update** を含むデータ ソースを変更する複数の関数は、変更されたデータ ソースを戻り値として返します。  これらの戻り値は大きく、**ForAll** テーブルのすべてのレコードに対して返された場合、かなりのリソースを使用する可能性があります。  また、**ForAll** が並行して動作でき、および結果の取得からこれらの関数の副作用を切り離す場合があるので、これらの戻り値が予想どおりのものではないこともあります。  幸いにも、データ変更関数によくありますが、**ForAll** からの戻り値が実際に使用されていない場合、戻り値は作成されず、リソースまたは順序の懸念はありません。  ただし、**ForAll** の結果およびデータ ソースを返す関数のいずれかを使用している場合、結果の構造方法について十分検討し、最初は小さいデータ セットで試してください。  

### <a name="alternatives"></a>代替手段
Power Apps の多くの関数は、単一列テーブルを使用して一度に複数の値を処理することができます。  たとえば、**Len** 関数はテキスト値のテーブルを処理して、**ForAll** の場合と同じように長さのテーブルを返すことができます。  これにより、多くの場合 **ForAll** を使用する必要がなくなり、より効率的、およびより読み取りやすくなります。

別の考慮事項は、**ForAll** が委任可能ではないのに対して、**Filter** などの他の関数は可能であることです。  

### <a name="delegation"></a>委任
[!INCLUDE [delegation-no-one](../../../includes/delegation-no-one.md)]

## <a name="syntax"></a>構文
**ForAll**( *Table*, *Formula* )

* *Table* - 必須。 操作されるテーブル。
* *Formula* - 必須。  *Table* のすべてのレコードに関して評価する数式。

## <a name="examples"></a>例
### <a name="calculations"></a>計算
次の例では、**平方**[データ ソース](../working-with-data-sources.md) を使用します。

![](media/function-forall/squares.png)

このデータ ソースをコレクションとして作成するには、**Button** コントロールの **OnSelect** プロパティを次の数式に設定し、プレビュー モードを開き、次にボタンをクリックまたはタップします。

`ClearCollect( Squares, [ "1", "4", "9" ] )`

| 計算式 | 内容 | 結果 |
| --- | --- | --- |
| **ForAll(&nbsp;Squares, Sqrt(&nbsp;Value&nbsp;)&nbsp;)**<br><br>**Sqrt(&nbsp;Squares&nbsp;)** |入力テーブルのすべてのレコードについて、**値**列の平方根を計算します。  **Sqrt** 関数は単一列テーブルでも使用できるので、**ForAll** を使用しないでこの例を実行することができます。 |<style> img { max-width: none } </style> ![](media/function-forall/sqrt.png) |
| **ForAll(&nbsp;Squares, Power(&nbsp;Value,&nbsp;3&nbsp;)&nbsp;)** |入力テーブルのすべてのレコードについて、**値**列を三乗します。  **Power** 関数は、単一列テーブルをサポートしていません。 したがって、この場合は、**ForAll** を使用する必要があります。 |<style> img {最大幅: なし} </style> ![](media/function-forall/power3.png) |

### <a name="using-a-connection"></a>接続の使用
次の例では、**Expressions** [データ ソース](../working-with-data-sources.md) を使用します。

![](media/function-forall/translate.png)

このデータ ソースをコレクションとして作成するには、**Button** コントロールの **OnSelect** プロパティを次の数式に設定し、プレビュー モードを開き、次にボタンをクリックまたはタップします。

`ClearCollect( Expressions, [ "Hello", "Good morning", "Thank you", "Goodbye" ] )`

この例では、[Microsoft Translator](../connections/connection-microsoft-translator.md) 接続も使用します。  アプリにこの接続を追加するには、[接続を管理する](../add-manage-connections.md) 方法に関するトピックを参照してください。

| 計算式 | 内容 | 結果 |
| --- | --- | --- |
| **ForAll( Expressions, MicrosoftTranslator.Translate( Value, "es" ) )** |Expressions テーブルのすべてのレコードについて、**Value** 列の内容をスペイン語 (省略形 "es") に翻訳します。 |<style> img {最大幅: なし} </style> ![](media/function-forall/translate-es.png) |
| **ForAll( Expressions, MicrosoftTranslator.Translate( Value, "fr" ) )** |Expressions テーブルのすべてのレコードについて、**Value** 列の内容をフランス語 (省略形 "es") に翻訳します。 |<style> img {最大幅: なし} </style> ![](media/function-forall/translate-fr.png) |

### <a name="copying-a-table"></a>テーブルのコピー
場合によっては、データをフィルター処理、整形、並べ替え、および操作する必要があります。  Power Apps では、**Filter**、**AddColumns**、および **Sort** など、これを実行するためのいくつかの関数が提供されています。  Power Apps では、各テーブルを値として扱い、簡単に使用できるようにします。      

さらに、後で使用できるように、この結果のコピーを作成することが可能です。  または、データ ソースから別の場所に情報を移動することも可能です。  Power Apps では、データをコピーするため **Collect** 関数 を提供しています。

ただし、コピーを作成する前に、本当に必要かどうかを十分検討してください。  要求に応じて、数式を使用して基になるデータ ソースのフィルター処理および整形を行うことにより、多くの状況に対処することができます。 コピーの作成のいくつかの欠点を次に示します。

* 同じ情報のコピーが 2 つあるということは、そのうち一方が同期されなくなる可能性があることを意味します。  
* コピーの作成では、多くのコンピューター メモリ、ネットワーク帯域幅、および/または時間が消費される可能性があります。  
* ほとんどのデータ ソースでは、コピーを委任できず、移動できるデータ量を制限します。      

次の例では、**製品**[データ ソース](../working-with-data-sources.md) を使用しています。

![](media/function-forall/prod.png)

このデータ ソースをコレクションとして作成するには、**Button** コントロールの **OnSelect** プロパティを次の数式に設定し、プレビュー モードを開き、次にボタンをクリックまたはタップします。

```powerapps-dot
ClearCollect( Products, 
    Table( 
        { Product: "Widget",    'Quantity Requested': 6,  'Quantity Available': 3 }, 
        { Product: "Gadget",    'Quantity Requested': 10, 'Quantity Available': 20 },
        { Product: "Gizmo",     'Quantity Requested': 4,  'Quantity Available': 11 },
        { Product: "Apparatus", 'Quantity Requested': 7,  'Quantity Available': 6 } 
    )
)
```

目標は、利用可能よりも多く要求され、そのため注文をする必要があるアイテムのみを含む派生テーブルを使用することです。

![](media/function-forall/prod-order.png)  

このタスクは、すべてがさまざまな長所と短所があって同じ結果を生み出すいくつかの異なる方法で実行できます。

#### <a name="table-shaping-on-demand"></a>要求に応じたテーブルの整形
そのコピーを作成しないでください!  必要であればどこでも次の数式を使用できます。

```powerapps-dot
// Table shaping on demand, no need for a copy of the result
ShowColumns( 
    AddColumns( 
        Filter( Products, 'Quantity Requested' > 'Quantity Available' ), 
        "Quantity To Order", 'Quantity Requested' - 'Quantity Available' 
    ), 
    "Product", 
    "Quantity To Order"
)
```

[レコード スコープ](../working-with-tables.md#record-scope) は、各レコードの **'Quantity Requested'** および **'Quantity Available'** フィールドを使用して、それぞれ、比較および減算操作を実行する **Filter** および **AddColumns** 関数によって作成されます。

この例では、**Filter** 関数を委任できます。  たとえそれが多数のテーブルのうちのわずか少数のレコードであっても、条件を満たすすべての製品を見つけることができるので、これは重要です。  現時点では、**ShowColumns** および **AddColumns** は委任できないため、注文する必要がある製品の実際の数は制限されます。  この結果のサイズが常に比較的小さいことを分かっている場合、この方法で問題ありません。

および、コピーを作成しなかったため、管理するまたは古くなる情報の追加のコピーはありません。  

#### <a name="forall-on-demand"></a>要求に応じた ForAll
別の方法として、**ForAll** 関数を使用して、テーブル整形関数を置き換えます。

```powerapps-dot
ForAll( Products, 
    If( 'Quantity Requested' > 'Quantity Available', 
        { 
            Product: Product, 
            'Quantity To Order': 'Quantity Requested' - 'Quantity Available' 
        } 
    ) 
)
```

この数式は、一部のユーザーにとって読み取りおよび書き込みが容易な可能性があります。

**ForAll** のどんな部分も委任できません。  **製品**テーブルの最初の部分のみが評価されますが、このテーブルが非常に大きい場合は問題になることがあります。  前の例で、**Filter** は委任することができたので、大規模なデータ セットではよりよく機能する可能性があります。

#### <a name="collect-the-result"></a>結果の収集
場合によっては、データのコピーが必要な場合があります。  データ ソースから別の場所に情報を移動することが必要になる場合もあります。  この例では、ベンダーのシステムで **NewOrder** テーブルによって注文を行います。  高速なユーザー対話のために、ローカル コピーをキャッシュして、サーバーの待機時間が発生しないようにすることが必要な場合があります。

前の 2 つの例と同じテーブル整形を使用しますが、結果をコレクションに取り込みます。

```powerapps-dot
ClearCollect( NewOrder, 
    ShowColumns( 
        AddColumns( 
            Filter( Products, 'Quantity Requested' > 'Quantity Available' ), 
            "Quantity To Order", 'Quantity Requested' - 'Quantity Available' 
        ), 
        "Product", 
        "Quantity To Order"
    )
)
```

```powerapps-dot
ClearCollect( NewOrder, 
    ForAll( Products, 
        If( 'Quantity Requested' > 'Quantity Available', 
            { 
                Product: Product, 
                'Quantity To Order': 'Quantity Requested' - 'Quantity Available' 
            } 
        } 
    )
)
```

**ClearCollect** および **Collect** は委任できません。  そのため、この方法で移動できるデータの量は制限されます。

#### <a name="collect-within-forall"></a>ForAll 内での収集
最後に、**ForAll** 内で直接 **Collect** を実行できます。

```powerapps-dot
Clear( ProductsToOrder ); 
ForAll( Products, 
    If( 'Quantity Requested' > 'Quantity Available', 
        Collect( NewOrder,  
            { 
                Product: Product, 
                'Quantity To Order': 'Quantity Requested' - 'Quantity Available' 
            } 
        )
    )
)
```

やはり、この時点では **ForAll** 関数は委任できません。  **製品**テーブルが大きい場合、**ForAll** は最初のレコードのセットのみを参照して、注文が必要な一部の製品を見逃す可能性があります。  ただし、小さいままであることが分かっているテーブルの場合は、この方法で十分です。

**ForAll** の結果を取り込んでいないことに注意してください。  その中から行なわれた **Collect** 関数の呼び出しは、すべてのレコードに対して **NewOrder** データ ソースを返し、取り込んだ場合は大量のデータに達することがあります。  

