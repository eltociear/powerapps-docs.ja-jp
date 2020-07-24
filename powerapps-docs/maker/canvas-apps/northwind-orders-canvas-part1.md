---
title: キャンバス アプリで受注ギャラリーを作成する | Microsoft Docs
description: キャンバス アプリで受注ギャラリーを作成して、Northwind Traders のデータを管理する
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/06/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 25dacb85b49e931ebc8de90a819ed3cebe5aab9a
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3307373"
---
# <a name="create-an-order-gallery-in-a-canvas-app"></a>キャンバス アプリで受注ギャラリーを作成する

詳細な手順に従って、Northwind Traders データベースの架空のデータを管理するため、キャンバス アプリで受注ギャラリーを作成します。 このトピックは、Common Data Service のリレーショナル データでビジネス アプリを構築する方法を説明するシリーズの一部です。 最良の結果を得るには、これらのトピックを次の順序で調べてください:

1. 受注ギャラリーを作成する (**このトピック**)。
1. [概要フォームを作成する](northwind-orders-canvas-part2.md)。
1. [詳細ギャラリーを作成する](northwind-orders-canvas-part3.md)。

> [!div class="mx-imgBorder"]
> ![画面領域の定義](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="prerequisites"></a>前提条件

- [Northwind Traders のデータベースとアプリをインストールする](northwind-install.md)。
- Northwind Traders の [キャンバス アプリの概要](northwind-orders-canvas-overview.md) をお読みください。

## <a name="create-a-blank-app"></a>空白のアプリを作成する

1. [Power Apps にサインイン](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) してから、空白のタブレット アプリを作成します。

    > [!div class="mx-imgBorder"]
    > ![空白タイルからのキャンバス アプリ](media/northwind-orders-canvas-part1/start-01.png)

1. アプリに任意の名前を付けてから、**作成**を選択します。

    > [!div class="mx-imgBorder"]
    > ![空白ダイアログ ボックスからのキャンバス アプリ](media/northwind-orders-canvas-part1/start-02.png)

    アプリにデータ ソースとコントロールを追加できるよう、Power Apps Studio を開きます:

    > [!div class="mx-imgBorder"]
    > ![Power Apps Studio](media/northwind-orders-canvas-part1/start-03.png)

## <a name="add-the-data"></a>データを追加する

1. **ビュー** タブで、**データソース**を選択します:

    > [!div class="mx-imgBorder"]
    > ![ビュー、データ ソースを選択し、データ ソースを追加する](media/northwind-orders-canvas-part1/datasource-01.png)

1. 検索ボックスに**受注**と入力します:

    > [!div class="mx-imgBorder"]
    > ![接続の一覧](media/northwind-orders-canvas-part1/datasource-02.png)

1. アプリで使用する**受注**データ ソースを選択します:

    > [!div class="mx-imgBorder"]
    > ![エンティティの一覧](media/northwind-orders-canvas-part1/datasource-03.png)

    **受注**エンティティには、さまざまなタイプのフィールドが多く含まれます:

    > [!div class="mx-imgBorder"]
    > ![受注エンティティのフィールドの一覧](media/northwind-orders-canvas-part1/datasource-05.png)

    各フィールドには**表示名**と**名前**があり、論理名と呼ばれることもあります。 どちらの名前も同じものを指します。 一般に、アプリを構築するときに表示名を使用しますが、手順で説明したように、場合によってはより暗号化された**名前**が必要になります。

1. 次に画面とコントロールを操作するので、Power Apps Studio で 3 つの積み上げた正方形アイコンを押すことにより、左側にある**ツリー ビュー**に戻ります。 シリンダー アイコンを押して、いつでも**データ ソース**に戻ることができます。

## <a name="create-the-order-gallery"></a>受注ギャラリーを作成する

1. **挿入**タブで、**ギャラリー** > **縦方向 (空)** を選択して [**Gallery**](controls/control-gallery.md) コントロールに追加すると、受注が表示されます。

    > [!div class="mx-imgBorder"]
    > ![挿入、ギャラリー、空の垂直](media/northwind-orders-canvas-part1/orders-01.png)

    コントロールがキャンバスに配置され、フライアウト ダイアログが表示され、どのデータ ソースに接続するかを尋ねます。  


    > [!div class="mx-imgBorder"]
    > ![ギャラリーの Items プロパティを設定する](media/northwind-orders-canvas-part1/orders-02.png)

1. ここで**受注**に直接接続できますが、代わりにギャラリーの並べ替え順をコントロールします。  フライアウト ダイアログを無視し、数式バーでギャラリーの **Items** プロパティを次の式に設定します:

    ```powerapps-dot
    Sort( Orders, 'Order Number', Descending )
    ```

    [**Sort**](functions/function-sort.md) 関数は一覧を並べ替えて、最も新しい受注 (注文番号が最も大きい) が最初に表示されるようにします。

    > [!div class="mx-imgBorder"]
    > ![ギャラリーの Items プロパティを設定する](media/northwind-orders-canvas-part1/orders-02b.png)

1. しばらくすると、結果ビューが数式バーの下に表示されます。  左側の矢印をプルダウンして、式の結果を確認します。  右にスクロールして**受注番号**列を確認し、希望どおりに (最大から最小) 並べ替えられるようにします。  

    > [!div class="mx-imgBorder"]
    > ![ギャラリーの Items プロパティを設定する](media/northwind-orders-canvas-part1/orders-02c.png)

1. 右端の**プロパティ** タブで、**レイアウト**の一覧を開きます:

    > [!div class="mx-imgBorder"]
    > ![レイアウト オプションの一覧](media/northwind-orders-canvas-part1/orders-03.png)

1. オプションの一覧から、**タイトルとサブタイトル**を選択します:

    > [!div class="mx-imgBorder"]
    > ![レイアウトを選択する](media/northwind-orders-canvas-part1/orders-04.png)

    2 つの [**Label**](controls/control-text-box.md) コントロールがギャラリーのテンプレートに追加されます。 既定では、これらのコントロールは 2 つの**受注**エンティティの列に表示され、次に変更を加えます。 ギャラリーのテンプレートは、エンティティの各レコードに対して垂直に複製されます。

1. 右端にある**プロパティ** タブで、(**フィールド**の隣にある) **編集**を選択します。

    > [!div class="mx-imgBorder"]
    > ![レイアウトを選択する](media/northwind-orders-canvas-part1/orders-04b.png)

1. **データ** ウィンドウで、**Title1** を選択 (またはギャラリーのテンプレートで上部のラベルを選択) します。

1. 数式バーで、ラベルの **Text** プロパティを次の数式に設定します:

    ```powerapps-dot
    "Order " & ThisItem.'Order Number'
    ```

    > [!div class="mx-imgBorder"]
    > ![タイトル ラベルの Text プロパティを設定する](media/northwind-orders-canvas-part1/orders-06.png)

    受注番号は、各ギャラリー項目の上部に表示されます。 ギャラリー テンプレートで、**ThisItem** は**受注**エンティティのすべてのフィールドへのアクセスを許可します。

1. **データ** ウィンドウで、**Subtitle1** を選択 (またはギャラリーのテンプレートで下部のラベルを選択) します:

    > [!div class="mx-imgBorder"]
    > ![サブタイトル ラベルを選択する](media/northwind-orders-canvas-part1/orders-07.png)

1. 数式バーで、ラベルの **Text** プロパティを次の数式に設定します:

    ```powerapps-dot
    ThisItem.Customer.Company
    ```

    > [!div class="mx-imgBorder"]
    > ![サブタイトル ラベルの Text プロパティを設定する](media/northwind-orders-canvas-part1/orders-08.png)

    この数式を入力すると、一時的に赤い波線のエラーが表示される場合があります。 数式バーの外側で任意のものを選択してカーソルを数式バーに戻すと、エラーが解消されます。 エラーが続く場合、または値が表示されない場合は、**ビュー**タブを選択し、**データ ソース**を選択してから、データソース名の右側にある省略記号 (...) を選択することにより**受注**エンティティを更新します。

    **ThisItem.Customer** を指定した場合、**受注**および**顧客**エンティティ間の多対一の関連付けを活用し、各受注に関連付けられている顧客レコードを取得しています。 顧客レコードから、表示する**会社**列でデータを抽出します。

    **顧客**エンティティを含む、**注文**エンティティから他のエンティティへのすべての関連付けを表示できます:

    > [!div class="mx-imgBorder"]
    > ![関連付けの一覧](media/northwind-orders-canvas-part1/orders-09.png)

1. 右上隅の閉じるアイコン (x) を選択して、**データ** ウィンドウを閉じます。

## <a name="show-each-orders-status"></a>各受注の状態を表示する

この手順では、ギャラリーにラベル用のスペースを追加し、データに基づいて各受注の状態を異なる色で表示するように構成します。

1. ギャラリーのテンプレートで、最初のラベル **Title1** の幅を削減します:

    > [!div class="mx-imgBorder"]
    > ![ギャラリーのテンプレートでの Title1](media/northwind-orders-canvas-part1/status-01.png)

1. 前の手順を 2 番目のラベル **Subtitle1**で繰り返します:

    > [!div class="mx-imgBorder"]
    > ![ギャラリーのテンプレートでの Subtitle1](media/northwind-orders-canvas-part1/status-02.png)

1. ギャラリー テンプレート (またはテンプレートのコントロール) を選択した状態で、**挿入**タブで**ラベル**を選択します:

    > [!div class="mx-imgBorder"]
    > ![ラベルの追加](media/northwind-orders-canvas-part1/status-03.png)

1. 新しいラベルを **Title1** ラベルの右側に移動します:

    > [!div class="mx-imgBorder"]
    > ![ラベルの移動とサイズ変更](media/northwind-orders-canvas-part1/status-04.png)

1. 新しいラベルの **Text** プロパティを次の式に設定します:

    ```powerapps-dot
    ThisItem.'Order Status'
    ```

    > [!div class="mx-imgBorder"]
    > ![Text プロパティの設定](media/northwind-orders-canvas-part1/status-05.png)

    **受注**エンティティで、**受注の状態**フィールドは**受注の状態**オプション セットからの値を保持します。 オプション セットは、他のプログラミング ツールの列挙に似ています。 オプションの各セットはデータベースで定義されるため、ユーザーはセット内のオプションのみを指定できます。 **受注の状態**オプション セットもローカルではなくグローバルであるため、他のエンティティで使用できます:

    > [!div class="mx-imgBorder"]
    > ![受注の状態オプション セット](media/northwind-orders-canvas-part1/status-06.png)

    セットの各オプションには、ラベルに表示することで表示される名前があります。 これらの名前はローカライズでき、英語のユーザーが **Apple** を、フランスのユーザーが **Pomme** を、またはスペイン語のユーザーが **Manzana** を選択するかどうかにかかわらず、アプリは同じオプションを認識します。 このため、このトピックが後で示すように、オプションのハードコードされた文字列に依存する数式を作成することはできません。

    数式では、**受注の状態**にスペースが含まれているため、単一引用符で囲む必要があります。 ただし、その名前は Power Apps での**顧客**または**会社**などの他の名前と同じ方法で機能します。

1. **ホーム** タブで、状態ラベルのフォント サイズを 20 ポイントに増やし、テキストを右揃えにします:

    > [!div class="mx-imgBorder"]
    > ![フォント サイズと配置を変更する](media/northwind-orders-canvas-part1/status-07.png)

1. 数式バーで、状態ラベルの **Color** プロパティを次の数式に設定します:

    ```powerapps-dot
    Switch( ThisItem.'Order Status',
        'Orders Status'.Closed, Green,
        'Orders Status'.New, Black,
        'Orders Status'.Invoiced, Blue,
        'Orders Status'.Shipped, Purple
    )
    ```

    > [!div class="mx-imgBorder"]
    > ![状態ラベルの Color プロパティを設定する](media/northwind-orders-canvas-part1/status-08.png)

    Power Apps では、オプション名がローカライズされている場合、このような数式では不適切な結果を生成される可能性があるため、セット内の各オプションのハードコードされた文字列に依存する数式を作成できません。 代わりに、**Switch** 関数は、ユーザーの設定に基づいて、ラベルに表示される文字列に基づく色を決定します。

    この数式を使用すると、前の図に示すように、異なる状態値が異なる色で表示されます。

## <a name="display-each-orders-total"></a>各受注の合計を表示する

1. ギャラリーの最初の項目を選択します。これはギャラリーのテンプレートです:

    > [!div class="mx-imgBorder"]
    > ![ギャラリー テンプレートを選択する](media/northwind-orders-canvas-part1/aggregate-01.png)

1. **挿入**タブで、**ラベル**を選択して別のラベルに追加します:

    > [!div class="mx-imgBorder"]
    > ![ラベルの追加](media/northwind-orders-canvas-part1/aggregate-02.png)

1. 状態ラベルの下に表示されるように、新しいラベルを移動します:

    > [!div class="mx-imgBorder"]
    > ![新しいラベルをサイズ変更して移動する](media/northwind-orders-canvas-part1/aggregate-03.png)

1. 数式バーで、新しいラベルの **Text** プロパティを次の数式に設定します:

    ```powerapps-dot
    Text( Sum( ThisItem.'Order Details', Quantity * 'Unit Price' ), "[$-en-US]$ #,###.00" )
    ```

    > [!div class="mx-imgBorder"]
    > ![受注の合計コストを計算する数式](media/northwind-orders-canvas-part1/aggregate-04.png)

    この数式では、[**Sum**](functions/function-aggregates.md) 関数は、**受注**エンティティの各レコードに関連付けられている**受注明細**エンティティのレコードを一対多の関連付けを通して合計します。 これらの品目が各受注を構成し、同じ一対多の関係を使用して、画面の右下領域にある品目を表示および編集します。

    Common Data Service では、複雑な集計関数 (たとえば、乗算の合計) の委任をサポートしていないため、この数式は青い下線および [委任の警告](delegation-overview.md) を表示します。 この例では 500 品目を超える受注がないため、この情報は無視できます。 別のアプリで必要な場合は、**アプリの設定**でその制限を増やすことができます。

    この数式の [**Text**](functions/function-text.md) 関数では、通貨記号を追加し、結果を千単位の桁区切りおよび小数点区切り記号で書式設定します。 記述されているように、数式には米国英語の言語タグ (**[$-en-US]**) およびドル記号 (**$**) が含まれます。 言語タグを削除すると、言語設定に基づいてタグが置き換えられ、ラベルにはそのタグに適した形式が表示されます。 ドル記号を残すと、ラベルにはユーザーの設定に基づいて適切な通貨記号が表示されます。 ただし、ドル記号を必要に応じて置き換えることで、異なる記号を強制的に表示できます。

1. **ホーム** タブで、最新ラベルのフォント サイズを 20 ポイントに変更し、テキストを右揃えにします:

    > [!div class="mx-imgBorder"]
    > ![フォント サイズとラベルの配置を変更する](media/northwind-orders-canvas-part1/aggregate-05.png)

1. ギャラリーを画面の左端に移動し、ギャラリーの幅を狭めてスペースを詰めます。

1. 画面とほぼ同じ高さになるようにギャラリーの高さを増やしますが、上部にタイトル バー用に少し余裕を残します。タイトル バーは、次のトピックの最初に追加します:

    > [!div class="mx-imgBorder"]
    > ![ギャラリーを移動してサイズ変更する](media/northwind-orders-canvas-part1/aggregate-06.png)

## <a name="summary"></a>概要

要約すると、次の要素を含む受注ギャラリーを追加して、単一画面のキャンバス アプリの構築を開始しました:

- 受注番号表示する式: `"Orders " & ThisItem.OrderNumber`
- 多対一の関連付けのフィールド: `ThisItem.Customer.Company`
- セットのオプションの名前を表示するラベル: `ThisItem.'Order Status'`
- ラベルに表示されるセット内のオプションに基づいて形式を変更するラベル: `Switch( ThisItem.'Order Status', 'Orders Status'.Closed, Green, ...`
- 一対多の関連付けに対する複雑な集計関数: `Sum( ThisItem.'Order Details', Quantity * 'Unit Price' )`

## <a name="next-topic"></a>次のトピック

次のトピックでは、[**Edit form**](controls/control-form-detail.md) コントロールを追加して、先ほど作成したギャラリーでユーザーが選択した順序の概要を表示および編集します。

> [!div class="nextstepaction"]
> [概要フォームを作成する](northwind-orders-canvas-part2.md)
