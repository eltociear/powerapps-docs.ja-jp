---
title: キャンバス アプリで詳細ギャラリーを作成する | Microsoft Docs
description: キャンバス アプリで詳細ギャラリーを作成して、Northwind Traders のデータを管理する
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
ms.openlocfilehash: 7e29674e689ff77599bb49c58e7b0edbc028b6be
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2019
ms.locfileid: "3303992"
---
# <a name="create-a-detail-gallery-in-a-canvas-app"></a>キャンバス アプリで詳細ギャラリーを作成する

詳細な手順に従って、Northwind Traders データベースの架空のデータを管理するため、キャンバス アプリで詳細ギャラリーを作成します。 このトピックは、Common Data Service のリレーショナル データでビジネス アプリを構築する方法を説明するシリーズの一部です。 最良の結果を得るには、これらのトピックを次の順序で調べてください:

1. [受注ギャラリーの作成](northwind-orders-canvas-part1.md)。
1. [概要フォームを作成する](northwind-orders-canvas-part2.md)。
1. 詳細ギャラリーを作成する (**このトピック**)。

> [!div class="mx-imgBorder"]
> ![画面領域の定義](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="prerequisites"></a>前提条件

このトピックで前述したように、このトピックを開始する前にデータベースをインストールする必要があります。 次に、受注ギャラリーと概要フォームを作成するか、または **Northwind Orders (キャンバス) - パート 3 の開始**アプリを開く必要があります。アプリには既にそのギャラリーとフォームが含まれています。

## <a name="create-another-title-bar"></a>別のタイトル バーを作成する

1. 画面の上部で、タイトル バーとして機能する [**Label**](controls/control-text-box.md) コントロールを選択し、Ctrl-C キーを押してコピーしてから、Ctrl-V キーを押して貼り付けます。

    > [!div class="mx-imgBorder"]
    > ![タイトル バーをコピーして貼り付ける](media/northwind-orders-canvas-part3/details-01.png)

1. コピーをサイズ変更して移動し、概要フォームのすぐ下に表示されるようにします。

1. 次のいずれかの方法でコピーからテキストを削除します:

    - テキストをダブルクリックして選択し、削除キーを押します。
    - ラベルの **Text** プロパティを空の文字列 (**""**) に設定します。

    > [!div class="mx-imgBorder"]
    > ![タイトル バー コピーからのテキストを削除する](media/northwind-orders-canvas-part3/details-02.png)

## <a name="add-a-gallery"></a>ギャラリーを追加する

1. [**Gallery**](controls/control-gallery.md) コントロールを**縦方向 (空)** レイアウトに挿入します:

    > [!div class="mx-imgBorder"]
    > ![空で垂直のギャラリーを追加する](media/northwind-orders-canvas-part3/details-03.png)

    受注明細を表示する新しいギャラリーが左上隅に表示されます:

    > [!div class="mx-imgBorder"]
    > ![受注明細ギャラリーの既定の場所](media/northwind-orders-canvas-part3/details-04.png)

1. フライアウト データ ソース ダイアログを閉じてから、詳細ギャラリーをサイズ変更して、右下隅の新しいタイトル バーの下に移動します。

    > [!div class="mx-imgBorder"]
    > ![受注明細ギャラリーの変更後の場所](media/northwind-orders-canvas-part3/details-05.png)

1. 詳細ギャラリーの **Items** プロパティを次の数式に設定します:

    ```powerapps-dot
    Gallery1.Selected.'Order Details'
    ```

    > [!div class="mx-imgBorder"]
    > ![詳細ギャラリーの Items プロパティを設定する](media/northwind-orders-canvas-part3/details-06.png)

    エラーが表示された場合は、受注ギャラリーに **Gallery1** (左端の**ツリー ビュー** ウィンドウにある) という名前が付けられていることを確認します。 そのギャラリーに別の名前がある場合は、**Gallery1** に名前変更します。

    2 つのギャラリーをリンクしました。 ユーザーが受注ギャラリーで受注を選択すると、その選択により**受注**エンティティのレコードを識別します。 その受注に 1 つ以上の品目が含まれている場合、**受注**エンティティのレコードは、**受注明細**エンティティの 1 つ以上のレコード、にリンクされ、それらのレコードからのデータが詳細ギャラリーに表示されます。 この動作は、**受注**および**受注明細**エンティティ間で作成された一対多の関連付けを反映しています。 指定した式は、ドット表記を使用してその関連付けを "移動" します:

    > [!div class="mx-imgBorder"]
    > ![受注エンティティおよび受注明細エンティティ間の一対多の関連付け](media/northwind-orders-canvas-part3/schema-orders-rel.png)

## <a name="show-product-names"></a>製品名を表示する

1. 詳細ギャラリーで、**挿入タブから項目を追加**してギャラリー テンプレートを選択します:

    > [!div class="mx-imgBorder"]
    > ![詳細ギャラリーのテンプレートを選択する](media/northwind-orders-canvas-part3/details-07.png)

    ギャラリー自体ではなく、ギャラリー テンプレートを選択したことを確認してください。 境界ボックスはギャラリーの境界の少し内側にあり、おそらくギャラリーの高さよりも短いはずです。 このテンプレートにコントロールを挿入すると、ギャラリー内の項目ごとにコントロールが繰り返されます。

1. **挿入**タブで、詳細ギャラリーにラベルを挿入します。

    ラベルはギャラリー内に表示される必要があります。表示されない場合は、やり直してください。ただしラベルを挿入する前に、ギャラリーのテンプレートを選択していることを確認してください。

    > [!div class="mx-imgBorder"]
    > ![詳細ギャラリーにラベルを追加する](media/northwind-orders-canvas-part3/details-08.png)

1. 新しいラベルの **Text** プロパティを次の式に設定します:

    ```powerapps-dot
    ThisItem.Product.'Product Name'
    ```

    テキストが表示されない場合は、受注ギャラリーの下部にある**受注 0901** の矢印を選択します。

1. フルテキストが表示されるようにラベルをサイズ変更します:

    > [!div class="mx-imgBorder"]
    > ![受注明細の製品名を表示する](media/northwind-orders-canvas-part3/details-09.png)

    この式は**受注明細**エンティティ内のレコードから移動します。 レコードは、**ThisItem** で多対一の関連付けを通して**受注製品**エンティティに保持されます:

    > [!div class="mx-imgBorder"]
    > ![受注明細エンティティおよび受注製品エンティティ間の多対一の関連付け](media/northwind-orders-canvas-part3/schema-orderdetails-rel.png)

    **製品名**フィールド (および使用しようとしている他のフィールド) が抽出されます:

    > [!div class="mx-imgBorder"]
    > ![受注製品エンティティのフィールド](media/northwind-orders-canvas-part3/schema-products-fields.png)

## <a name="show-product-images"></a>製品画像を表示する

1. **挿入**タブで、[**Image**](controls/control-image.md) コントロールを詳細ギャラリーに挿入します:

    > [!div class="mx-imgBorder"]
    > ![画像コントロールの挿入](media/northwind-orders-canvas-part3/details-10.png)

1. 画像とラベルをサイズ変更し、並ぶように移動します。

    > [!TIP]
    > コントロールのサイズと位置をより細かく制御するには、Alt キーを押さずにサイズ変更または移動を開始し、Alt キーを押しながらコントロールのサイズ変更または移動を続けます:

    > [!div class="mx-imgBorder"]
    > ![画像コントロールの移動](media/northwind-orders-canvas-part3/details-11.png)

1. 画像の **Image** プロパティを次の式に設定します:

    ```powerapps-dot
    ThisItem.Product.Picture
    ```

    この場合も、式はこの受注明細に関連付けられている製品を参照し、表示する**画像**フィールドを抽出します。

    > [!div class="mx-imgBorder"]
    > ![製品画像を表示する](media/northwind-orders-canvas-part3/details-12.png)

1. 複数の**受注明細**レコードが一度に表示されるよう、ギャラリーのテンプレートの高さを縮めます:

    > [!div class="mx-imgBorder"]
    > ![ギャラリーのテンプレートを短くする](media/northwind-orders-canvas-part3/details-13.png)

## <a name="show-product-quantity-and-cost"></a>製品の数量とコストを表示する

1. **挿入**タブで、別のラベルを詳細ギャラリーに挿入してから、新しいラベルをサイズ変更して製品情報の右側に移動します。

1. 新しいラベルの **Text** プロパティを次の式に設定します:

    ```powerapps-dot
    ThisItem.Quantity
    ```

    この式は、情報を**受注明細**エンティティから直接取得します (関連付けは必須ではない)。

    > [!div class="mx-imgBorder"]
    > ![製品数量を表示する](media/northwind-orders-canvas-part3/details-13b.png) 

1. **ホーム** タブで、このコントロールの配置を**右**に変更します:

    > [!div class="mx-imgBorder"]
    > ![配置を変更する](media/northwind-orders-canvas-part3/details-14.png)

1. **挿入**タブで、別のラベルを詳細ギャラリーに挿入してから、ラベルをサイズ変更して数量ラベルの右側に移動します。

1. 新しいラベルの **Text** プロパティを次の式に設定します:

    ```powerapps-dot
    Text( ThisItem.'Unit Price', "[$-en-US]$ #,###.00" )
    ```

    言語タグ (**[$-en-US]**) が含まれない場合は、言語と地域に基づいて追加されます。 別の言語タグを使用する場合は、右角かっこ (**]**) 直後の **$** を削除してから、その位置に独自の通貨記号を追加します。

    > [!div class="mx-imgBorder"]
    > ![単価を表示する](media/northwind-orders-canvas-part3/details-15.png)

1. **ホーム** タブで、このコントロールの配置を**右**に変更します:

    > [!div class="mx-imgBorder"]
    > ![配置を変更する](media/northwind-orders-canvas-part3/details-16.png)

1. **挿入**タブで、別のラベル コントロールを詳細ギャラリーに挿入してから、新しいラベルをサイズ変更して単価の右側に移動します。

1. 新しいラベルの **Text** プロパティを次の式に設定します:

    ```powerapps-dot
    Text( ThisItem.Quantity * ThisItem.'Unit Price', "[$-en-US]$ #,###.00" )
    ```

    この場合も、言語タグ (**[$-en-US]**) が含まれない場合は、言語と地域に基づいて追加されます。 タグが異なる場合は、右角かっこ (**]**) 直後の **$** の代わりに独自の通貨記号を使用します。

    > [!div class="mx-imgBorder"]
    > ![拡張価格を表示する](media/northwind-orders-canvas-part3/details-17.png)

1. **ホーム** タブで、このコントロールの配置を**右**に変更します:

    > [!div class="mx-imgBorder"]
    > ![配置を変更する](media/northwind-orders-canvas-part3/details-18.png)

    これで、コントロールを詳細ギャラリーに追加できました。

1. **ツリー ビュー** ウィンドウで、**Screen1** を選択して詳細ギャラリーが選択されていないことを確認します。

## <a name="add-text-to-the-new-title-bar"></a>新しいタイトル バーにテキストを追加する

1. **挿入**タブで、画面に別のラベルを挿入します:

    > [!div class="mx-imgBorder"]
    > ![ラベルを挿入する](media/northwind-orders-canvas-part3/details-19.png)

1. 2 番目のタイトル バーの製品の画像の上にある新しいラベルをサイズ変更し移動してから、**ホーム** タブでテキストの色を白に変更します。

1. ラベルのテキストをダブルクリックしてから、**製品**と入力します:

    > [!div class="mx-imgBorder"]
    > ![ラベル テキストを製品に変更する](media/northwind-orders-canvas-part3/details-20.png)

1. 製品ラベルをコピーし貼り付けてから、コピーをサイズ変更して数量列の上に移動します。

1. 新しいラベルのテキストをダブルクリックしてから、**数量**と入力します:

    > [!div class="mx-imgBorder"]
    > ![ラベル テキストを数量に変更する](media/northwind-orders-canvas-part3/details-21.png)

1. 数量ラベルをコピーし貼り付けてから、コピーをサイズ変更して単価列の上に移動します。

1. 新しいラベルのテキストをダブルクリックしてから、**単価**と入力します:

    > [!div class="mx-imgBorder"]
    > ![ラベル テキストを単価に変更する](media/northwind-orders-canvas-part3/details-22.png)

1. 単価ラベルをコピーし貼り付けてから、コピーをサイズ変更して拡張価格列の上に移動します。

1. 新しいラベルのテキストをダブルクリックしてから、**拡張済**と入力します:

    > [!div class="mx-imgBorder"]
    > ![ラベル テキストを拡張済に変更する](media/northwind-orders-canvas-part3/details-23.png)

## <a name="display-order-totals"></a>受注合計を表示する

1. 詳細ギャラリーの高さを縮めて、画面の下部に受注合計のスペースを確保します:

    > [!div class="mx-imgBorder"]
    > ![受注明細ギャラリーを短くする](media/northwind-orders-canvas-part3/sum-01.png)

1. 画面中央のタイトル バーをコピーし貼り付けてから、コピーを画面の下部に移動します:

    > [!div class="mx-imgBorder"]
    > ![タイトル バーをコピーし、コピーを下端に移動する](media/northwind-orders-canvas-part3/sum-02.png)

1. 中央のタイトル バーから製品ラベルをコピーし貼り付けてから、コピーをタイトル バーの下部、**数量**列の左側に移動します。

1. 新しいラベルのテキストをダブルクリックしてから、次のテキストを入力します:<br>**受注合計:**

    > [!div class="mx-imgBorder"]
    > ![受注合計のラベルを追加する](media/northwind-orders-canvas-part3/sum-03.png)

1. 受注合計ラベルをコピーし貼り付けてから、コピーをサイズ変更して受注合計ラベルの右側に移動します。

1. 新しいラベルの **Text** プロパティを次の式に設定します:

    ```powerapps-dot
    Sum( Gallery1.Selected.'Order Details', Quantity )
    ```

    この式は委任警告を表示しますが、500 以上の製品が含まれる単一の受注がないため、これは無視できます。

1. **ホーム** タブで、新しいラベルのテキスト配置を**右**に設定します:

    > [!div class="mx-imgBorder"]
    > ![配置を変更する](media/northwind-orders-canvas-part3/sum-04.png)

1. このラベル コントロールをコピーし貼り付けてから、コピーをサイズ変更して**拡張済**列の下に移動します。

1. コピーの **Text** プロパティを次の式に設定します:

    ```powerapps-dot
    Text( Sum( Gallery1.Selected.'Order Details', Quantity * 'Unit Price' ), "[$-en-US]$ #,###.00" )
    ```

    この式は委任警告を表示しますが、500 以上の製品が含まれる単一の受注がないため、これは無視できます。

    > [!div class="mx-imgBorder"]
    > ![受注合計金額を表示する](media/northwind-orders-canvas-part3/sum-05.png)

## <a name="add-space-for-new-details"></a>新しい明細用のスペースを追加する

任意のギャラリーで、データは表示できますが、更新したりレコードを追加することはできません。 詳細ギャラリーの下に、ユーザーが**受注明細**エンティティでレコードを構成できる領域を追加し、そのレコードを受注に挿入します。

1. 詳細ギャラリーの高さを十分に縮めて、そのギャラリーの下にある単一品目の編集スペースを確保します。

    このスペースで、ユーザーが受注明細を追加できるようにコントロールを追加します。

    > [!div class="mx-imgBorder"]
    > ![詳細ギャラリーを短くする](media/northwind-orders-canvas-part3/add-details-01.png)

1. **挿入**タブで、ラベルを挿入してから、サイズを変更して詳細ギャラリーの下に移動します。

    > [!div class="mx-imgBorder"]
    > ![ラベルを挿入する](media/northwind-orders-canvas-part3/add-details-02.png)

1. 新しいラベルのテキストをダブルクリックしてから、削除キーを押します。

1. **ホーム** タブで、新しいラベルの**塗りつぶし**の色を **LightBlue** に設定します:

    > [!div class="mx-imgBorder"]
    > ![ラベルの塗りつぶしを淡い青色に変更する](media/northwind-orders-canvas-part3/add-details-03.png)

## <a name="select-a-product"></a>製品を選択する

1. **挿入**タブで、**コントロール** > **Combo box** を選択します:

    > [!div class="mx-imgBorder"]
    > ![コンボ ボックスを挿入する](media/northwind-orders-canvas-part3/add-details-08.png)

    [**Combo box**](controls/control-combo-box.md) コントロールは左上隅に表示されます。

1. フライアウト ダイアログで、**受注製品**データ ソースを選択します:

    > [!div class="mx-imgBorder"]
    > ![コンボ ボックスの Items プロパティを設定する](media/northwind-orders-canvas-part3/add-details-09.png)

1. コンボ ボックスの**プロパティ** タブで、**編集** (**フィールド**の横にある) を選択して**データ** ウィンドウを開きます。  **主要テキスト**および **SearchField** が **nwind_productname** に設定されていることを確認します。

    この場合**データ** ウィンドウがまだ表示名をサポートしていないため、論理名を指定します。

    > [!div class="mx-imgBorder"]
    > ![コンボ ボックスの主要テキストを設定する](media/northwind-orders-canvas-part3/add-details-10.png)

1. **データ** ウィンドウを閉じます。

1. 右端にある**プロパティ** タブで、下にスクロールし、**複数の選択を許可**をオフにし、**検索を許可**がオンになっていることを確認します:

    > [!div class="mx-imgBorder"]
    > ![複数選択を無効にして検索を有効にする](media/northwind-orders-canvas-part3/add-details-12.png)

1. コンボ ボックスをサイズ変更し、詳細ギャラリーの製品名列のすぐ下の淡い青色の領域に移動します:

    > [!div class="mx-imgBorder"]
    > ![コンボ ボックスを移動する](media/northwind-orders-canvas-part3/add-details-13.png)

    このコンボ ボックスでは、ユーザーはアプリが作成する**受注明細**の**製品**エンティティでレコードを指定します。

1. Alt キーを押しながら、コンボ ボックスの下矢印を選択します。

    > [!TIP]
    > Alt キーを押したままにして、プレビュー モードを開かずに Power Apps Studio でコントロールを操作できます。

1. 表示される製品の一覧で、製品を選択します:

    > [!div class="mx-imgBorder"]
    > ![コンボ ボックスで製品を選択する](media/northwind-orders-canvas-part3/add-details-14.png)

## <a name="add-a-product-image"></a>製品画像を追加する

1. **挿入**タブで、**メディア** > **画像**を選択します:

    > [!div class="mx-imgBorder"]
    > ![画像コントロールの挿入](media/northwind-orders-canvas-part3/add-details-15.png)

    [**Image**](controls/control-image.md) コントロールは左上隅に表示されます:

    > [!div class="mx-imgBorder"]
    > ![画像コントロールの既定の場所](media/northwind-orders-canvas-part3/add-details-16.png)

1. 画像をサイズ変更して、他の製品画像の下の淡い青色の領域およびコンボ ボックスの横に移動します。

1. 画像の **Image** プロパティを以下に設定します:

    ```powerapps-dot
    ComboBox1.Selected.Picture
    ```

    > [!div class="mx-imgBorder"]
    > ![画像の画像プロパティを設定する](media/northwind-orders-canvas-part3/add-details-17.png)

    概要フォームで従業員の写真を表示するのに使用したのと同じ方法を使用しています。 コンボ ボックスの **Selected** プロパティは、**画像**フィールドを含む、ユーザーが選択する製品のレコード全体を返します。

## <a name="add-a-quantity-box"></a>数量ボックスを追加する

1. **挿入**タブで、**テキスト** > **テキスト入力**を選択します:

    > [!div class="mx-imgBorder"]
    > ![テキスト入力ボックスを追加する](media/northwind-orders-canvas-part3/add-details-18.png)

    [**Text input**](controls/control-text-input.md) コントロールは左上隅に表示されます:

    > [!div class="mx-imgBorder"]
    > ![テキスト入力ボックスの既定の場所](media/northwind-orders-canvas-part3/add-details-19.png)

1. テキスト入力ボックスをサイズ変更し、コンボ ボックスの右側、詳細ギャラリーの数量列の下に移動します:

    > [!div class="mx-imgBorder"]
    > ![テキスト入力ボックスをサイズ変更し移動する](media/northwind-orders-canvas-part3/add-details-20.png)

    このテキスト入力ボックスを使用して、ユーザーは**受注明細**レコードの**数量**フィールドを指定します。

1. このコントロールの **Default** プロパティを **""** に設定します:

    > [!div class="mx-imgBorder"]
    > ![テキスト入力ボックスの **Default** プロパティを設定する](media/northwind-orders-canvas-part3/add-details-21.png)

1. **ホーム** タブで、このコントロールのテキスト配置を**右**に設定します:

    > [!div class="mx-imgBorder"]
    > ![配置を変更する](media/northwind-orders-canvas-part3/add-details-22.png)

## <a name="show-the-unit-and-extended-prices"></a>単位と拡張価格を表示する

1. **挿入**タブで、**Label** コントロールを挿入します。

    ラベルは画面の左上隅に表示されます:

    > [!div class="mx-imgBorder"]
    > ![ラベルを挿入する](media/northwind-orders-canvas-part3/add-details-23.png)

1. ラベルをサイズ変更してテキスト入力コントロールの右側に移動し、ラベルの **Text** プロパティをこの式に設定します:

    ```powerapps-dot
    Text( ComboBox1.Selected.'List Price', "[$-en-US]$ #,###.00" )
    ```

    > [!div class="mx-imgBorder"]
    > ![ラベルの Text プロパティを設定する](media/northwind-orders-canvas-part3/add-details-24.png)

    このコントロールでは、**受注製品**エンティティからの**定価**を表示します。 この値により、**受注明細**レコードの**単価**フィールドが決定されます。

    > [!NOTE]
    > このシナリオでは、値は読み取り専用ですが、他のシナリオでは、アプリ ユーザーが値を変更する必要があります。 その場合は、**Text input** コントロールを使用し、その**Default** プロパティを**定価**に設定します。

1. **ホーム** タブで、定価ラベルのテキスト配置を**右**に設定します:

    > [!div class="mx-imgBorder"]
    > ![配置を変更する](media/northwind-orders-canvas-part3/add-details-25.png)

1. 定価ラベルをコピーし貼り付けてから、コピーをサイズ変更して定価ラベルの右側に移動します。

1. 新しいラベルの **Text** プロパティを次の式に設定します:

    ```powerapps-dot
    Text( Value(TextInput1.Text) * ComboBox1.Selected.'List Price', "[$-en-US]$ #,###.00" )
    ```

    > [!div class="mx-imgBorder"]
    > ![新しいラベルの Text プロパティを設定する](media/northwind-orders-canvas-part3/add-details-27.png)

    このコントロールでは、アプリ ユーザーが指定した数量およびアプリ ユーザーが選択した製品の定価に基づいて、拡張価格が表示されます。 これは、アプリユーザー向けの情報です。

1. 数量のテキスト入力コントロールをダブルクリックしてから、数値を入力します。

    **拡張済**価格ラベルが再計算され、新しい値が表示されます:

    > [!div class="mx-imgBorder"]
    > ![数量を指定して、拡張価格を表示する](media/northwind-orders-canvas-part3/add-details-28.png)

## <a name="add-an-add-icon"></a>追加アイコンを追加する

1. **挿入**タブで、**アイコン** > **追加**を選択します:

    > [!div class="mx-imgBorder"]
    > ![追加アイコンを挿入する](media/northwind-orders-canvas-part3/add-details-29.png)

    アイコンは画面の左上隅に表示されます。

    > [!div class="mx-imgBorder"]
    > ![追加アイコンの既定の場所](media/northwind-orders-canvas-part3/add-details-30.png)

1. このアイコンをサイズ変更して淡い青色の領域の右端に移動してから、アイコンの **OnSelect** プロパティをこの式に設定します:

    ```powerapps-dot
    Patch( 'Order Details',
        Defaults('Order Details'),
        {
            Order: Gallery1.Selected,
            Product: ComboBox1.Selected,
            Quantity: Value(TextInput1.Text),
            'Unit Price': ComboBox1.Selected.'List Price'
        }
    );
    Refresh( Orders );
    Reset( ComboBox1 );
    Reset( TextInput1 )
    ```

    > [!div class="mx-imgBorder"]
    > ![アイコンの OnSelect プロパティを設定する](media/northwind-orders-canvas-part3/add-details-31.png)

    一般に、[**Patch**](functions/function-patch.md) 関数はレコードを更新して作成します。この数式の特定の引数により、関数が実行する正確な変更が決まります。

    - 最初の引数は、関数がレコードを更新または作成するデータ ソース (この場合、**受注明細**エンティティ) を指定します。
    - 2 番目の引数は、3 番目の引数で指定されていない限り、**受注明細**エンティティの既定値でレコードを作成する関数を指定します。
    - 3 番目の引数は、新しいレコードの 4 つの列にユーザーからの値が含まれることを指定します。

      - **受注**列には、ユーザーが受注ギャラリーで選択した受注の番号が含まれます。
      - **製品**列には、製品を表示するコンボ ボックスでユーザーが選択した製品の名前が含まれます。
      - **数量**列には、ユーザーがテキスト入力ボックスで指定した値が含まれます。
      - **単価**列には、ユーザーがこの受注明細に対して選択した製品の定価が含まれます。

    > [!NOTE]
    > アプリ ユーザーが製品を表示するコンボ ボックスで選択する製品に対して、任意の列 (**受注製品**エンティティで) からのデータを使用する数式を構築できます。 ユーザーが**受注製品**エンティティでレコードを選択すると、製品名がそのコンボ ボックスに表示されるだけでなく、製品の単価もラベルに表示されます。 キャンバス アプリの各検索値は、主キーだけでなく、レコード全体を参照します。

    **Refresh** 関数は、**受注明細**エンティティに先ほど追加したレコードを**受注**エンティティが反映していることを保証します。 **Reset** 関数は、製品、数量、および単価のデータをクリアして、ユーザーが同じ受注に対して別の受注明細をより簡単に作成できるようにします。

1. F5 キーを押してから、**追加**アイコンを選択します。

    受注には、指定した情報が反映されます:

    > [!div class="mx-imgBorder"]
    > ![受注明細を追加するアニメーション](media/northwind-orders-canvas-part3/add-details.gif)

1. (オプション) 受注に別の項目を追加します。

1. Esc キーを押してプレビュー モードを閉じます。

## <a name="remove-an-order-detail"></a>受注明細を削除する

1. 画面の中央で、詳細ギャラリーのテンプレートを選択します:

    > [!div class="mx-imgBorder"]
    > ![ギャラリー テンプレートを選択する](media/northwind-orders-canvas-part3/remove-details-01.png)

1. **挿入**タブで、**アイコン** > **ごみ箱**を選択します:

    > [!div class="mx-imgBorder"]
    > ![ごみ箱アイコンを挿入する](media/northwind-orders-canvas-part3/remove-details-02.png)

    ゴミ箱アイコンはギャラリー テンプレートの左上隅に表示されます。

    > [!div class="mx-imgBorder"]
    > ![アイコンの既定の場所](media/northwind-orders-canvas-part3/remove-details-03.png)

1. ゴミ箱アイコンをサイズ変更して詳細ギャラリー テンプレートの右側に移動してから、アイコンの **OnSelect** プロパティをこの式に設定します:

    ```powerapps-dot
    Remove( 'Order Details', ThisItem ); Refresh( Orders )
    ```

    > [!div class="mx-imgBorder"]
    > ![アイコンの OnSelect プロパティを設定する](media/northwind-orders-canvas-part3/remove-details-04.png)

    現時点で、関連付けからレコードを直接削除することはできないため、[**Remove**](functions/function-remove-removeif.md) 関数が関連するエンティティから直接レコードを削除します。 **ThisItem** では、ゴミ箱アイコンが表示される詳細ギャラリーの同じレコードから取得した、削除するレコードを指定します。

    この場合も、操作ではキャッシュされたデータが使用されるため、**Refresh** 関数は、**受注**エンティティにアプリが関連エンティティの 1つを変更したことを通知します。

1. F5 キーを押してプレビュー モードを開いてから、受注から削除する各**受注明細**レコードの横にあるゴミ箱アイコンを選択します。

1. 受注からのさまざまな受注明細を追加および削除してみてください:

    > [!div class="mx-imgBorder"]
    > ![受注明細を追加および削除するアニメーション](media/northwind-orders-canvas-part3/remove-details.gif)

## <a name="in-conclusion"></a>まとめ

要約すると、別のギャラリーを追加して受注明細を表示し、アプリで受注明細の追加と削除を制御しました。 以下の要素を使用しました:

- 一対多の関連付けを介して受注ギャラリーにリンクされた 2 番目のギャラリー コントロール: **Gallery2.Items** = `Gallery1.Selected.'Order Details'`
- **受注明細**エンティティから**受注製品**エンティティへの多対一の関連付け: `ThisItem.Product.'Product Name'` および `ThisItem.Product.Picture`
- 製品の一覧を取得する **Choices** 関数: `Choices( 'Order Details'.Product' )`
- 完全な多対一の関連レコードとしてのコンボ ボックスの **Selected** プロパティ: `ComboBox1.Selected.Picture` および `ComboBox1.Selected.'List Price'`
- **受注明細**レコードを作成する **Patch**関数: `Patch( 'Order Details', Defaults( 'Order Details' ), ... )`
- **受注明細**レコードを削除する **Remove**関数: `Remove( 'Order Details', ThisItem )`

この一連のトピックでは、教育目的で Common Data Service の関連付けおよびキャンバス アプリのオプション セットを使用する方法について簡単に説明しました。 アプリを運用版にリリースする前に、フィールドの検証、エラー処理、およびその他の多くの要素を検討する必要があります。
