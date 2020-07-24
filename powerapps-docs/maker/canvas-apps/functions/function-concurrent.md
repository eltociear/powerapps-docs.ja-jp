---
title: Concurrent 関数 | Microsoft Docs
description: Power Apps での Concurrent 関数の構文を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/26/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e6e2aa2e46625d14a197dc43206bcaac4f31efe1
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3305441"
---
# <a name="concurrent-function-in-power-apps"></a>Power Apps での Concurrent 関数
複数の数式を相互に同時に評価します。

## <a name="description"></a>内容
**Concurrent** 関数では、同時に複数の数式を評価します。 通常、複数の数式は [**;**](operators.md) 演算子と一緒にチェーンすることにより評価され、各々を順次に順番に評価します。 アプリが操作を同時に実行する場合、ユーザーは同じ結果を待機する時間がより少なくなります。

アプリの [**OnStart**](../controls/control-screen.md) プロパティで、**コンカレント**を使用して、アプリがデータを読み込むときのパフォーマンスを向上させます。 前の呼び出しが完了するまで、データ呼び出しが開始されない場合、アプリはすべての要求時間の合計を待機する必要があります。 データ呼び出しが同時に開始される場合、アプリは最長の要求時間だけ待機する必要があります。 Web ブラウザーは、多くの場合、データ操作を同時に実行することによってパフォーマンスを向上させます。

**Concurrent** 関数内の数式の評価の開始および終了の順序は予測できません。 **Concurrent** 関数内の数式は同じ **Concurrent** 関数内の別の数式への依存関係を含めることはできず、それを実行した場合 Power Apps がエラーを表示します。 **Concurrent** 関数が開始する前に完了するため、内部から、**Concurrent** 関数の外部の数式に安全に依存関係を持つことができます。 **Concurrent** 関数の後の数式は、内部の数式に安全に相互関係を持つことができ、これらは、**Concurrent** 関数が終了する前にすべて完了し、チェーン内の次の数式に移動します (**;** 演算子を使用する場合)。 副作用がある関数またはサービス メソッドを呼び出す場合は、微妙な順序の依存関係に注意してください。

数式を、**コンカレント**の引数内で **;** 演算子を使用して連鎖できます。 たとえば、**Concurrent( Set( a, 1 ); Set( b, a+1 ), Set( x, 2 ); Set( y, x+2 ) )** は **Set( a, 1 ); Set( b, a+1 )** を **Set( x, 2 ); Set( y, x+2 )** と同時に評価します。 この場合、数式内の依存関係は問題がなく、**a** は **b** の前に設定され、**x** は **y** の前に設定されます。

アプリが実行されているデバイスまたはブラウザーによっては、実際には少数の数式しか同時に評価されない可能性があります。 **コンカレント**は使用可能な機能を使用し、すべての数式が評価されるまで完了しません。

**数式レベルのエラー管理**を (詳細設定で) 有効にする場合、引数の順序で最初に発生したエラーは**コンカレント**から返され、それ以外の場合は、*空白*が返されます。 すべての数式が成功する場合、*true* が返されます。 1 つの数式が失敗した場合、その数式の残りの部分は停止しますが、他の数式は評価を続行します。

**コンカレント**は、[動作の数式](../working-with-formulas-in-depth.md) でのみ使用できます。

## <a name="syntax"></a>構文
**Concurrent**( *Formula1*, *Formula2* [, ...] )

* *Formula(s)* - 必須。 同時に評価する数式。 少なくとも 2 つの数式を指定する必要があります。

## <a name="examples"></a>例

#### <a name="loading-data-faster"></a>データの読み込みをより迅速にする

1. アプリを作成し、Common Data Service、SQL Server、または SharePoint から 4 つのデータ ソースを追加します。 

    この例では、[SQL Azure のサンプル Adventure Works データベース](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-portal) から 4 つのテーブルを使用します。 データベースを作成したら、完全修飾サーバー名 (たとえば、srvname.database.windows.net) を使用して Power Apps から接続します。

    ![Azure で Adventure Works データベースに接続する](media/function-concurrent/connect-database.png)

2. **[Button](../controls/control-button.md)** コントロールを追加し、その **OnSelect** プロパティを次の数式に設定します。

    ```powerapps-dot
    ClearCollect( Product, '[SalesLT].[Product]' );
    ClearCollect( Customer, '[SalesLT].[Customer]' );
    ClearCollect( SalesOrderDetail, '[SalesLT].[SalesOrderDetail]' ); 
    ClearCollect( SalesOrderHeader, '[SalesLT].[SalesOrderHeader]' )
    ```

3. [Microsoft Edge](https://docs.microsoft.com/microsoft-edge/devtools-guide/network) または [Google Chrome](https://developers.google.com/web/tools/chrome-devtools/network-performance/) で、アプリが実行されている間にネットワーク トラフィックを監視する開発者ツールをオンにします。

1. (オプション) ネットワーク調整をオンにして、この比較の効果を強調します。

4. Alt キーを押しながら、ボタンを選択し、次にネットワーク トラフィックを監視します。

    ツールには、次の例のように、順番に実行された 4 つの要求を示します。  実際の時間は大幅に異なるため、削除されています。  グラフには、各呼び出しが最後の完了後に開始されることを示しています。

    ![4 つのネットワーク要求の時間グラフ、それぞれが最後の完了後に開始され、時間帯全体をカバーしている](media/function-concurrent/chained-network.png)

5. アプリを保存し、閉じて、再度開きます。

    Power Apps はデータをキャッシュするので、ボタンを再度選択しても必ずしも 4 つの新しい要求が発生するわけではありません。 パフォーマンスをテストするたびに、アプリを閉じて再度開きます。 ネットワーク調整がオンになっている場合、別のテストの準備が終わるまでオフにしておくことができます。

1. 2 番目の **[Button](../controls/control-button.md)** コントロールを追加し、**OnSelect** プロパティを次の数式に設定します。

    ```powerapps-dot
    Concurrent( 
        ClearCollect( Product, '[SalesLT].[Product]' ), 
        ClearCollect( Customer, '[SalesLT].[Customer]' ),
        ClearCollect( SalesOrderDetail, '[SalesLT].[SalesOrderDetail]' ),
        ClearCollect( SalesOrderHeader, '[SalesLT].[SalesOrderHeader]' )
    )
    ```

    最初のボタンに同じ **ClearCollect** 呼び出しを追加しましたが、今回は **Concurrent** 関数で囲まれ、コンマで区切られていることに注意してください。

2. ブラウザーでネットワーク監視をクリアにします。

1. ネットワーク調整を以前に使用していた場合は、再度オンにします。

3. Alt キーを押しながら、2 番目のボタンを選択し、次にネットワーク トラフィックを確認します。

    ツールには、次の例のように、同時に実行された 4 つの要求を示します。  この場合も、実際の時間は大幅に異なるため、削除されています。  グラフには、すべての呼び出しがほぼ同時に開始され、および前の呼び出しが終了するまで待機していないことを示しています。

    ![4 つのネットワーク要求の時間グラフ、4 のすべてが同時に開始し、時間帯の半分程度をカバーしている](media/function-concurrent/concurrent-network.png)

    これらのグラフは、同じスケールに基づいています。 **コンカレント**を使用して、これらの操作を完了するのにかかった合計時間を半減させることができます。 

5. アプリを保存し、閉じて、再度開きます。

#### <a name="race-condition"></a>競合状態

1. [Microsoft Translator](../connections/connection-microsoft-translator.md) サービスへの接続をアプリに追加します。

2. [**テキスト入力**](../controls/control-text-input.md) コントロールを追加し、別の名前になっている場合は、**TextInput1** という名前に変更します。

3. **Button** コントロールを追加し、その **OnSelect** プロパティを次の数式に設定します。

    ```powerapps-dot
    Set( StartTime, Value( Now() ) );
    Concurrent(
        Set( FRTrans, MicrosoftTranslator.Translate( TextInput1.Text, "fr" ) ); 
            Set( FRTransTime, Value( Now() ) ),
        Set( DETrans, MicrosoftTranslator.Translate( TextInput1.Text, "de" ) ); 
            Set( DETransTime, Value( Now() ) )
    );
    Collect( Results,
        { 
            Input: TextInput1.Text,
            French: FRTrans, FrenchTime: FRTransTime - StartTime, 
            German: DETrans, GermanTime: DETransTime - StartTime, 
            FrenchFaster: FRTransTime < DETransTime
        }
    )
    ```

4. [**データ テーブル**](../controls/control-data-table.md) コントロールを追加し、その **Items** プロパティを**結果**に設定します。

1. 右側ペインの**プロパティ** タブで、**フィールドの編集**を選択して**フィールド** ペインを開きます。

1. フィールドの一覧で、各フィールドのチェック ボックスを選択して、データ テーブルにすべて表示します。

1. (オプション) **入力**フィールドを一覧の上部にドラッグし、**FrenchFaster** フィールドを一覧の下部にドラッグします。

    ![結果コレクションのフィールドの一覧](media/function-concurrent/field-list.png) 

6. **テキスト入力** コントロールで、翻訳する語句を入力または貼り付けます。

7. Alt キーを押しながら、ボタンを複数回選択して、テーブルを塗りつぶします。

    時間はミリ秒単位で表示されます。
  
    ![文字列 "Hello World" をフランス語およびドイツ語に翻訳した結果が含まれるデータ テーブルの表示。 フランス語翻訳がドイツ語よりも速い場合があり、逆の場合もあります。](media/function-concurrent/race-condition.png) 

    場合によっては、フランス語翻訳はドイツ語よりも速い場合があり、その逆もあります。 両方が同時に開始されますが、ネットワークの待機時間およびサーバー側の処理などの、さまざまな理由で一方が他方の前に返されます。

    アプリが最初に終了する翻訳に依存している場合、[競合状態](https://en.wikipedia.org/wiki/Race_condition) が発生します。 しかし、Power Apps では検出できるほとんどのタイミング依存関係にフラグを付けます。
