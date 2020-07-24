---
title: キャンバス アプリで概要フォームを作成する | Microsoft Docs
description: キャンバス アプリで概要フォームを作成して、Northwind Traders のデータを管理する
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
ms.openlocfilehash: 6f49057e55ea52dac98c92109752a05276eec831
ms.sourcegitcommit: 32542f1d17fee757dcdaf9c247f4051f59b86434
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "3303946"
---
# <a name="create-a-summary-form-in-a-canvas-app"></a>キャンバス アプリで概要フォームを作成する

詳細な手順に従って、Northwind Traders データベースの架空のデータを管理するため、キャンバス アプリで概要フォームを作成します。 このトピックは、Common Data Service のリレーショナル データでビジネス アプリを構築する方法を説明するシリーズの一部です。 最良の結果を得るには、これらのトピックを次の順序で調べてください:

1. [受注ギャラリーの作成](northwind-orders-canvas-part1.md)。
2. 概要フォームを作成します (**このトピック**)。
3. [詳細ギャラリーを作成する](northwind-orders-canvas-part3.md)。

> [!div class="mx-imgBorder"]
> ![画面領域の定義](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="prerequisites"></a>前提条件

1. [Northwind Traders のデータベースとアプリをインストールする](northwind-install.md)。
1. Northwind Traders の [キャンバス アプリの概要](northwind-orders-canvas-overview.md) を確認します。
1. 自身で [受注ギャラリーを作成する](northwind-orders-canvas-part1.md) か、またはすでにそのギャラリーが含まれる **Northwind Orders (キャンバス) - パート 2 の開始**アプリを開きます。

## <a name="add-a-title-bar"></a>タイトル バーを追加する

アプリの上部全体にタイトル バーを作成します。ここには、このトピックの終わりまでにアクション ボタンが保持されます。

1. **ツリー ビュー** ウィンドウで、**Screen1** を選択して、誤ってコントロールを受注ギャラリーに追加しないようにします:

    > [!div class="mx-imgBorder"]
    > ![ツリー ビュー ウィンドウで Screen1 を選択する](media/northwind-orders-canvas-part2/titlebar-01.png)

1. **挿入**タブで、**ラベル**を選択して [**Label**](controls/control-text-box.md) コントロールに挿入します:

    > [!div class="mx-imgBorder"]
    > ![ラベルを挿入する](media/northwind-orders-canvas-part2/titlebar-02.png)

    新しいラベルは、ギャラリーの上部に一度だけ表示されます。 ギャラリーの各項目に表示される場合、ラベルの最初のインスタンスを削除し、(前の手順で説明したように) 画面が選択されていることを確認してから、ラベルを再挿入します。

1. 新しいラベルを移動しサイズ変更して、画面上部に広げます:

    > [!div class="mx-imgBorder"]
    > ![ラベルを移動してサイズ変更する](media/northwind-orders-canvas-part2/titlebar-03.png)

1. ラベルのテキストをダブルクリックしてから、**Northwind Orders** と入力します。

    代替策として、同じ結果を達成するために数式バーで **Text** プロパティを変更します:

    > [!div class="mx-imgBorder"]
    > ![タイトル バーのテキストを変更する](media/northwind-orders-canvas-part2/titlebar-04.png)

1. **ホーム** タブで、ラベルの書式を設定します:
    - フォント サイズを 24 ポイントに増やします。
    - テキストを太字にします。
    - テキストを白くします。
    - テキストを中央揃えにします。
    - 濃い青色の塗りつぶしを背景に追加します。

    > [!div class="mx-imgBorder"]
    > ![ホーム タブの書式設定オプション](media/northwind-orders-canvas-part2/titlebar-05.png)

## <a name="add-an-edit-form-control"></a>Edit form コントロールを追加する

このセクションでは、ユーザーがギャラリーで選択する任意の受注の概要を表示するコントロールを追加します。

1. **挿入**タブで、[**Edit form**](controls/control-form-detail.md) コントロールを挿入します:

    > [!div class="mx-imgBorder"]
    > ![Edit form コントロールを追加する](media/northwind-orders-canvas-part2/form-01.png)

    既定では、フォームは左上隅に表示されますが、他のコントロールでは見つけにくい場合があります:

    > [!div class="mx-imgBorder"]
    > ![既定の場所での Edit form コントロール](media/northwind-orders-canvas-part2/form-02.png)

1. フォームを移動しサイズ変更して、タイトル バー下の画面の右上隅をカバーします:

    > [!div class="mx-imgBorder"]
    > ![Edit form コントロールを移動しサイズ変更する](media/northwind-orders-canvas-part2/form-03.png)

1. **プロパティ** ウィンドウで、**データ ソース** ドロップ ダウンを選択します。

    > [!div class="mx-imgBorder"]
    > ![Edit form コントロールの DataSource プロパティを設定する](media/northwind-orders-canvas-part2/form-04a.png)

1. **受注**データ ソースを選択します。

    > [!div class="mx-imgBorder"]
    > ![Edit form コントロールの DataSource プロパティを設定する](media/northwind-orders-canvas-part2/form-04.png)

## <a name="add-and-arrange-fields"></a>フィールドを追加および配置する

1. 右端にある**プロパティ** タブで、**フィールドの編集**を選択して**フィールド** ウィンドウを開きます。

    > [!div class="mx-imgBorder"]
    > ![フィールド ウィンドウを開く](media/northwind-orders-canvas-part2/form-05.png)

1. **フィールド** ウィンドウが空でない場合は、すでに挿入されているフィールドを削除します。  

    > [!div class="mx-imgBorder"]
    > ![フィールド ウィンドウを開く](media/northwind-orders-canvas-part2/form-06a.png)

1. フィールドの一覧が空になった後、**フィールドの追加**を選択してから、**顧客**および**従業員**フィールドのチェック ボックスをオンにします。

    > [!div class="mx-imgBorder"]
    > ![顧客および従業員フィールドを Edit form コントロールに追加する](media/northwind-orders-canvas-part2/form-06b.png)

1. これらのフィールドが表示されるまで下にスクロールしてから、チェック ボックスをオンにします:

    - **メモ**
    - **注文日**
    - **受注番号**
    - **受注状態**
    - **支払日**

    > [!div class="mx-imgBorder"]
    > ![Edit form コントロールに更に 5 つのフィールドを追加する](media/northwind-orders-canvas-part2/form-06c.png)

    > [!div class="mx-imgBorder"]
    > ![Edit form コントロールに更に 5 つのフィールドを追加する](media/northwind-orders-canvas-part2/form-06d.png)

1. **フィールド** ウィンドウの下部に、**追加**を選択してから、**フィールド** ウィンドウを閉じます。

    フォームには 7 つのフィールドが表示されますが、順序が異なる場合があります:

    > [!div class="mx-imgBorder"]
    > ![Edit form コントロールに 7 つのフィールドが表示される](media/northwind-orders-canvas-part2/form-08.png)

    > [!NOTE]
    > 任意のフィールドに赤いエラー アイコンが表示される場合、データがソースから取得されたときに問題が発生した可能性があります。 エラーを解決するには、データを更新します:
    >
    > 1. **ビュー** タブで、**データ ソース**を選択します。
    > 1. **データ** ウィンドウで、**データ ソース**を選択します。
    > 1. **受注**の隣で、省略記号 (...) を選択し、**更新**を選択してから、**データ** ウィンドウを閉じます。
    >
    > 顧客名または従業員名のコンボ ボックスにまだエラーが表示される場合は、各ボックスの**主要テキスト**および **SearchField**を選択してから**データ** ウィンドウを開くことにより確認します。 顧客ボックスの場合、両方のフィールドを **nwind_company** に設定する必要があります。 従業員ボックスの場合、両方のフィールドを **nwind_lastname** に設定する必要があります。

1. フォームを選択した状態で、右端にある**プロパティ** タブでフォームの列数を 3 から 12 に変更します。

    この手順により、フィールドを配置するときに柔軟性が加わります:

    > [!div class="mx-imgBorder"]
    > ![次に Edit form コントロールで列数を変更する](media/northwind-orders-canvas-part2/form-08b.png)

    多くの UI デザインは、1、2、3、4、6、および 12 コントロールの行に均等に対応できるため、12 列のレイアウトに依存しています。 このトピックでは、1、2、または 4 コントロールを含む行を作成します。

1. 他の任意のコントロールと同じように、ハンドルをドラッグしてフィールドを移動およびサイズ変更し、各行に次のデータ カードが指定された順序で含まれるようにします:

    - 最初の行: **受注番号**、**受注状態**、**注文日**、および**支払日**
    - 2 行目: **顧客**および**従業員**
    - 3 行目: **メモ**

    > [!NOTE]
    > 配置する前に**メモ**、**顧客**、および**従業員**データ カードの幅を広げやすくなります。

    > [!div class="mx-imgBorder"]
    > ![フィールドを移動しサイズ変更する](media/northwind-orders-canvas-part2/form-rearrange.gif)

    フォームにフィールドを配置する方法の詳細: [キャンバス アプリのデータ フォーム レイアウトについて](working-with-form-layout.md)。

## <a name="hide-time-controls"></a>時間コントロールを非表示にする

この例では、細分性のそのレベルがユーザーの注意をそらすため、日付フィールドの時間部分は必要ありません。 それらを削除すると、それらのコントロールに依存して日付値を更新したり、データ カード内の別のコントロールの位置を決定したりする数式で問題が発生する可能性があります。 代わりに、時間コントロールを **Visible** プロパティに設定して非表示にします。

1. **ツリー ビュー** ウィンドウで、**注文日**データ カードを選択します。

    カードの名前は異なる場合がありますが、カードには**注文日**が含まれています。

1. Shift キーを押しながら、**注文日**データ カードで時間、分、およびコロン区切りのコントロールを選択します。

    > [!div class="mx-imgBorder"]
    > ![注文日カードで時間コントロールを選択する](media/northwind-orders-canvas-part2/form-09.png)

1. コントロールの **Visible** プロパティを **false** に設定します。

    選択したすべてのコントロールがフォームから消えます:

    > [!div class="mx-imgBorder"]
    > ![Visible プロパティを false に設定します。](media/northwind-orders-canvas-part2/form-10.png)

1. [**Date picker**](controls/control-date-picker.md) コントロールをサイズ変更して、完了日を表示します:

    > [!div class="mx-imgBorder"]
    > ![Date picker コントロールをサイズ変更する](media/northwind-orders-canvas-part2/form-11.png)

    次に、**支払日**フィールドで最後のいくつかの手順を繰り返します。

1. **ツリー ビュー** ウィンドウで、**支払日**データ カードの時間コントロールを選択します:

    > [!div class="mx-imgBorder"]
    > ![支払日カードの時間コントロールを選択する](media/northwind-orders-canvas-part2/form-12.png)

1. 選択したコントロールの **Visible** プロパティを **false** に設定します:

    > [!div class="mx-imgBorder"]
    > ![Visible プロパティを false に設定します。](media/northwind-orders-canvas-part2/form-13.png)

1. **支払日**カードで日付の選択をサイズ変更します:

    > [!div class="mx-imgBorder"]
    > ![Date picker コントロールをサイズ変更する](media/northwind-orders-canvas-part2/form-14.png)

## <a name="connect-the-order-gallery"></a>受注ギャラリーを接続する

1. **ツリー ビュー** ウィンドウで、フォームを折りたたんで受注ギャラリーの名前を見つけやすくしてから、必要に応じて **Gallery1** に名前変更します。

1. 概要フォームの **Item** プロパティを次の式に設定します:

    ```powerapps-dot
    Gallery1.Selected
    ```

    > [!div class="mx-imgBorder"]
    > ![フォームの Item プロパティを設定する](media/northwind-orders-canvas-part2/form-15.png)

    フォームには、アプリ ユーザーが一覧で選択する順序の概要が表示されます。

    > [!div class="mx-imgBorder"]
    > ![一覧で受注を選択して、フォームにその概要を表示する](media/northwind-orders-canvas-part2/form-select.gif)

## <a name="replace-a-data-card"></a>データ カードを置き換える

**受注番号**は、Common Data Service がレコードを作成するときに自動的に割り当てられる識別子です。 このフィールドには既定で [**Text input**](controls/control-text-input.md) コントロールがありますが、ユーザーがこのフィールドを編集できないようにラベルに置き換えます。

1. フォームを選択し、右端にある**プロパティ** タブで**フィールドの編集**を選択してから、**受注番号**フィールドを選択します:

    > [!div class="mx-imgBorder"]
    > ![受注番号フィールドを選択する](media/northwind-orders-canvas-part2/alt-01.png)

1. **コントロールの種類**の一覧を開きます:

    > [!div class="mx-imgBorder"]
    > ![**コントロールの種類**の一覧を開く](media/northwind-orders-canvas-part2/alt-02.png)

1. **テキストの表示**データ カードを選択します:

    > [!div class="mx-imgBorder"]
    > ![**テキストの表示**データ カードを選択する](media/northwind-orders-canvas-part2/alt-02b.png)

1. **フィールド** ウィンドウを閉じます。

    ユーザーは受注番号を変更できなくなりました:

    > [!div class="mx-imgBorder"]
    > ![受注番号が読み取り専用](media/northwind-orders-canvas-part2/alt-03.png)

1. **ホーム** タブで、受注番号のフォント サイズを 20 ポイントに変更して、フィールドを見つけやすくします:

    > [!div class="mx-imgBorder"]
    > ![受注番号のフォント サイズを変更する](media/northwind-orders-canvas-part2/alt-04.png)

## <a name="use-a-many-to-one-relationship"></a>多対一の関連付けを使用する

**受注**エンティティには**従業員**エンティティとの多対一の関係付けがあります: 各従業員は多くの受注を作成できますが、各受注は 1 人の従業員にのみ割り当てることができます。 ユーザーが [**Combo box**](controls/control-combo-box.md) コントロールで従業員を選択するとき、その **Selected** プロパティでは、**従業員**エンティティからの従業員のレコード全体が提供されます。 この結果、[**Image**](controls/control-image.md) コントロールを構成して、ユーザーがコンボ ボックスで選択する従業員の写真を表示できます。

1. **従業員**データカードを選択します:

    > [!div class="mx-imgBorder"]
    > ![従業員データカードを選択する](media/northwind-orders-canvas-part2/employee-01.png)

1. 右端にある**詳細設定**タブで、データ カードをロック解除して、以前は読み取り専用であった数式を編集できるようにします:

    > [!div class="mx-imgBorder"]
    > ![従業員データカードをロック解除する](media/northwind-orders-canvas-part2/employee-02.png)

1. データ カードで、コンボ ボックスの幅を小さくして、従業員写真用のスペースを確保します:

    > [!div class="mx-imgBorder"]
    > ![コンボ ボックス コントロールをサイズ変更する](media/northwind-orders-canvas-part2/employee-03b.png)

1. **挿入**タブで、**メディア** > **画像**を選択します:

    > [!div class="mx-imgBorder"]
    > ![画像の挿入](media/northwind-orders-canvas-part2/employee-04.png)

    画像がデータ カードに表示され、画像が収まるように拡張されます:

    > [!div class="mx-imgBorder"]
    > ![Image コントロール付きの従業員データ カード](media/northwind-orders-canvas-part2/employee-05.png)

1. 画像をサイズ変更し、コンボ ボックスの右側に移動します:

    > [!div class="mx-imgBorder"]
    > ![画像コントロールを移動してサイズ変更する](media/northwind-orders-canvas-part2/employee-06.png)

1. 画像の **Image**プロパティをこの式に設定し、必要に応じて DataCardValue の末尾の数値を置き換えます:

    ```powerapps-dot
    DataCardValue7.Selected.Picture
    ```

    > [!div class="mx-imgBorder"]
    > ![画像の Image プロパティを設定する](media/northwind-orders-canvas-part2/employee-07.png)

    選択した従業員の写真が表示されます。

1. Alt キーを押しながら、コンボ ボックスで異なる従業員を選択して、写真も変化することを確認します。

    > [!div class="mx-imgBorder"]
    > ![従業員を選択してその従業員の写真を表示する](media/northwind-orders-canvas-part2/employee-select.gif)

## <a name="add-a-save-icon"></a>保存​​アイコンを追加する

1. **ツリー ビュー** ウィンドウで、**Screen1** を選択してから、**挿入** > **アイコン** > **確認**を選択します:

    > [!div class="mx-imgBorder"]
    > ![チェック マーク アイコンの挿入](media/northwind-orders-canvas-part2/save-01.png)

    既定では、[**確認**](controls/control-shapes-icons.md) アイコンは左上隅に表示されますが、他のコントロールでは見つけにくい場合があります:

    > [!div class="mx-imgBorder"]
    > ![既定の場所にあるアイコン](media/northwind-orders-canvas-part2/save-02.png)

1. **ホーム** タブで、アイコンの **Color** プロパティを白に変更し、アイコンをサイズ変更して、タイトル バーの右端に移動します:

    > [!div class="mx-imgBorder"]
    > ![保存アイコンの色、サイズ、場所を構成する](media/northwind-orders-canvas-part2/save-03.png)

1. **ツリー ビュー** ウィンドウで、フォームの名前が **Form1** であることを確認してから、アイコンの **OnSelect** プロパティをこの式に設定します:

    ```powerapps-dot
    SubmitForm( Form1 )
    ```

    > [!div class="mx-imgBorder"]
    > ![保存アイコンの OnSelect プロパティを設定する](media/northwind-orders-canvas-part2/save-04.png)

    ユーザーがアイコンを選択すると、[**SubmitForm**](functions/function-form.md) 関数は、フォーム内の変更された値を収集し、それらをデータ ソースに送信します。 データが送信されると点が画面の上部を移動し、プロセスの終了後に受注ギャラリーに変更が反映されます。

1. アイコンの **DisplayMode** プロパティを次の式に設定します:

    ```powerapps-dot
    If( Form1.Unsaved, DisplayMode.Edit, DisplayMode.Disabled )
    ```

    > [!div class="mx-imgBorder"]
    > ![アイコンの DisplayMode プロパティを設定する](media/northwind-orders-canvas-part2/save-05.png)

    フォームのすべての変更が保存されている場合、アイコンは無効になり、次に設定する **DisabledColor** に表示されます。

1. アイコンの **DisabledColor** プロパティを次の値に設定します:

    ```powerapps-dot
    Gray
    ```

    > [!div class="mx-imgBorder"]
    > ![アイコンの DisabledColor プロパティを設定する](media/northwind-orders-canvas-part2/save-06.png)

    ユーザーは、確認アイコンを選択することにより、受注への変更を保存できます。これにより、ユーザーが別の変更を加えるまで無効になりグレー表示されます:

    > [!div class="mx-imgBorder"]
    > ![変更を保存中](media/northwind-orders-canvas-part2/save-submit.gif)

## <a name="add-a-cancel-icon"></a>キャンセル アイコンを追加する

1. **挿入**タブで、**アイコン** > **キャンセル**を選択します:

    > [!div class="mx-imgBorder"]
    > ![キャンセル アイコンを追加する](media/northwind-orders-canvas-part2/save-07.png)

    既定では、アイコンは左上隅に表示されますが、他のコントロールでは見つけにくい場合があります:

    > [!div class="mx-imgBorder"]
    > ![既定の場所にあるキャンセル アイコン](media/northwind-orders-canvas-part2/save-08.png)

1. **ホーム** タブで、アイコンの **Color** プロパティを白に変更し、アイコンをサイズ変更して、確認アイコンの左端に移動します:

    > [!div class="mx-imgBorder"]
    > ![キャンセル アイコンの色、サイズ、場所を変更する](media/northwind-orders-canvas-part2/save-09.png)

1. キャンセル アイコンの **OnSelect** プロパティを次の式に設定します:

    ```powerapps-dot
    ResetForm( Form1 )
    ```

    > [!div class="mx-imgBorder"]
    > ![キャンセル アイコンの OnSelect プロパティを設定する](media/northwind-orders-canvas-part2/save-10.png)

    [**ResetForm**](functions/function-form.md) 関数ではフォーム内のすべての変更を破棄し、元の状態に戻します。

1. キャンセル アイコンの **DisplayMode** プロパティを次の式に設定します:

    ```powerapps-dot
    If( Form1.Unsaved Or Form1.Mode = FormMode.New, DisplayMode.Edit, DisplayMode.Disabled )
    ```

    > [!div class="mx-imgBorder"]
    > ![キャンセル アイコンの DisplayMode プロパティを設定する](media/northwind-orders-canvas-part2/save-11.png)

    この式は、確認アイコンの式とは少し異なります。 すべての変更が保存されている、またはフォームが**新規**モードである場合、キャンセル アイコンは無効になります。このモードは次に有効になります。 その場合、**ResetForm** は新しいレコードを破棄します。

1. キャンセル アイコンの **DisabledColor** プロパティを次の値に設定します:

    ```powerapps-dot
    Gray
    ```

    > [!div class="mx-imgBorder"]
    > ![キャンセル アイコンの DisabledColor プロパティを設定する](media/northwind-orders-canvas-part2/save-12.png)

    ユーザーは受注への変更をキャンセルできます。すべての変更が保存されている場合は、確認アイコンとキャンセル アイコンは無効になりグレー表示になります。

    > [!div class="mx-imgBorder"]
    > ![変更を保存およびキャンセル中](media/northwind-orders-canvas-part2/save-cancel.gif)

## <a name="add-an-add-icon"></a>追加アイコンを追加する

1. **挿入**タブで、**アイコン** > **追加**を選択します。

    > [!div class="mx-imgBorder"]
    > ![追加アイコンを挿入する](media/northwind-orders-canvas-part2/save-13.png)

    既定では、**追加**アイコンは左上隅に表示されますが、他のコントロールでは見つけにくい場合があります:

    > [!div class="mx-imgBorder"]
    > ![既定の場所にある追加アイコン](media/northwind-orders-canvas-part2/save-14.png)

1. **ホーム** タブで、追加アイコンの **Color** プロパティを白に変更し、アイコンをサイズ変更して、キャンセル アイコンの左端に移動します:

    > [!div class="mx-imgBorder"]
    > ![追加アイコンの色、サイズ、場所を変更する](media/northwind-orders-canvas-part2/save-15.png)

1. 追加アイコンの **OnSelect** プロパティを次の式に設定します:

    ```powerapps-dot
    NewForm( Form1 )
    ```

    > [!div class="mx-imgBorder"]
    > ![追加アイコンの OnSelect プロパティを設定する](media/northwind-orders-canvas-part2/save-15b.png)

    [**NewForm**](functions/function-form.md) 関数ではフォームに空のレコードが表示されます。  

1. 追加アイコンの **DisplayMode** プロパティを次の式に設定します:

    ```powerapps-dot
    If( Form1.Unsaved Or Form1.Mode = FormMode.New, DisplayMode.Disabled, DisplayMode.Edit )
    ```

    > [!div class="mx-imgBorder"]
    > ![追加アイコンの DisplayMode プロパティを設定する](media/northwind-orders-canvas-part2/save-16.png)

    次の条件下で、式は追加アイコンを無効にします:

    - ユーザーは変更を加えますが、変更の保存またはキャンセルは行いません。これは、確認アイコンとキャンセル アイコンとは逆の動作です。
    - ユーザーは追加アイコンを選択しますが、変更は加えません。

1. 追加アイコンの **DisabledColor** プロパティを次の値に設定します:

    ```powerapps-dot
    Gray
    ```

    > [!div class="mx-imgBorder"]
    > ![追加アイコンの DisabledColor プロパティを設定する](media/northwind-orders-canvas-part2/save-17.png)

    変更を加えない場合、または加えた任意の変更を保存またはキャンセルする場合に、ユーザーは受注を作成できます。 (ユーザーがこのアイコンを選択する場合、1 つ以上の変更を加えてからそれらの変更を保存またはキャンセルするまで、アイコンを再度選択することはできません):

    > [!div class="mx-imgBorder"]
    > ![受注を作成します](media/northwind-orders-canvas-part2/save-new.gif)

> [!NOTE]
> 受注を作成して保存する場合、受注ギャラリーで下にスクロールして、新しい受注を表示する必要があります。 まだ受注明細を追加していないため、合計金額が表示されません。

## <a name="add-a-trash-icon"></a>ごみ箱アイコンを追加する

1. **挿入**タブで、**アイコン** > **ごみ箱**を選択します。

    > [!div class="mx-imgBorder"]
    > ![ごみ箱アイコンを挿入する](media/northwind-orders-canvas-part2/save-18.png)

    既定では、**ゴミ箱**アイコンは左上隅に表示されますが、他のコントロールでは見つけにくい場合があります:

    > [!div class="mx-imgBorder"]
    > ![ゴミ箱アイコンの既定の場所](media/northwind-orders-canvas-part2/save-19.png)

1. **ホーム** タブで、ゴミ箱アイコンの **Color** プロパティを白に変更し、アイコンをサイズ変更して、追加アイコンの左端に移動します:

    > [!div class="mx-imgBorder"]
    > ![ゴミ箱アイコンの色、サイズ、場所を変更する](media/northwind-orders-canvas-part2/save-20.png)

1. ゴミ箱アイコンの **OnSelect** プロパティを次の式に設定します:

    ```powerapps-dot
    Remove( Orders, Gallery1.Selected )
    ```

    > [!div class="mx-imgBorder"]
    > ![ゴミ箱アイコンの OnSelect プロパティを設定する](media/northwind-orders-canvas-part2/save-21.png)

    [**Remove**](functions/function-remove-removeif.md) 関数では、データ ソースからのレコードを削除します。 この数式では、関数は受注ギャラリーで選択されたレコードを削除します。 フォームにはレコードの詳細が表示されるため、ごみ箱アイコンは (受注ギャラリーではなく) 概要フォームの近くに表示されます。これにより、ユーザーは数式が削除するレコードをより簡単に識別できます。

1. ゴミ箱アイコンの **DisplayMode** プロパティを次の式に設定します:

    ```powerapps-dot
    If( Form1.Mode = FormMode.New, DisplayMode.Disabled, DisplayMode.Edit )
    ```

    > [!div class="mx-imgBorder"]
    > ![ゴミ箱アイコンの DisplayMode プロパティを設定する](media/northwind-orders-canvas-part2/save-22.png)

    ユーザーがレコードを作成している場合、この式はゴミ箱アイコンを無効にします。 ユーザーがレコードを保存するまで、**Remove** 関数には削除するレコードがありません。

1. ゴミ箱アイコンの **DisabledColor** プロパティを次の値に設定します:

    ```powerapps-dot
    Gray
    ```

    > [!div class="mx-imgBorder"]
    > ![ゴミ箱アイコンの DisabledColor プロパティを設定する](media/northwind-orders-canvas-part2/save-23.png)

    ユーザーは受注を削除できます。

    > [!div class="mx-imgBorder"]
    > ![受注の削除中](media/northwind-orders-canvas-part2/save-delete.gif)

## <a name="summary"></a>概要

要約すると、ユーザーは各受注の概要を表示および編集できるフォームを追加し、次の要素を使用しました:

- **受注**エンティティからのデータを表示するフォーム: **Form1.DataSource =**`Orders`
- フォームと受注ギャラリーの間の接続: **Form1.Item =**`Gallery1.Selected`
- **受注番号**フィールドの代替コントロール: **テキストの表示**
- **従業員**データ カードで従業員の写真を表示する多対一の関連付け: `DataCardValue1.Selected.Picture`
- 受注への変更を保存するアイコン: `SubmitForm( Form1 )`
- 受注への変更をキャンセルするアイコン: `ResetForm( Form1 )`
- 受注を作成するアイコン: `NewForm( Form1 )`
- 受注を削除するアイコン: `Remove( Orders, Gallery1.Selected )`

## <a name="next-step"></a>次のステップ

次のトピックでは、別のギャラリーを追加して各受注の製品を表示します。[**Patch**](functions/function-patch.md) 関数を使用してこれらの詳細を変更します。

> [!div class="nextstepaction"]
> [ 詳細ギャラリーを作成する](northwind-orders-canvas-part3.md)
