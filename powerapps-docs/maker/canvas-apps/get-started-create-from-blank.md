---
title: Excel データを基にして最初からキャンバス アプリを作成する | Microsoft Docs
description: このチュートリアルでは、2 つのスクリーンのキャンバス アプリを作成して、ユーザーが Excel ファイル内のレコードを作成、編集、および削除できるようにします。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 12/05/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 01bb3037e6223d41fd7da044b49a51abc57762de
ms.sourcegitcommit: d194d2fa009ca7bfcbe95e5f31473832a130e0a6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "3307488"
---
# <a name="create-a-canvas-app-from-scratch-based-on-excel-data"></a>Excel データを基にして最初からキャンバス アプリを作成する

Excel データを基にしてテーブルとして書式設定された独自のキャンバス アプリを最初から作成した後、必要に応じて、他のソースからデータを追加します。 このチュートリアルの手順では、2 つのスクリーンのアプリを作成します。 1 つは、一連のレコードをユーザーが閲覧するためのスクリーンです。 もう 1 つは、ユーザーがレコードを作成したり、レコードのフィールドを更新したり、レコード全体を削除したりするためのスクリーンです。 この方法は、[基本的なアプリを Excel から作成する](get-started-create-from-data.md) よりも時間がかかりますが、経験豊富なアプリ作成者は自分のニーズに合わせて最適なアプリを構築できます。

## <a name="prerequisites"></a>前提条件

このチュートリアルの手順に厳密に従うには、最初に次のサンプル データを使って Excel ファイルを作成します。

1. このデータをコピーし、Excel ファイルに貼り付けます。

    | StartDay | StartTime | Volunteer | バックアップ |
    | --- | --- | --- | --- |
    | 土曜日 |10am-noon |Vasquez |Kumashiro |
    | 土曜日 |noon-2pm |Ice |Singhal |
    | 土曜日 |2pm-4pm |Myk |Mueller |
    | 日曜日 |10am-noon |Li |Adams |
    | 日曜日 | noon-2pm |Singh |Morgan |
    | 日曜日 | 2pm-4pm |Batye |Nguyen |

2. そのデータを **Schedule** という名前のテーブルとして書式設定し、Power Apps が情報を解析できるようにします。

    詳細については、「[Excel でテーブルを書式設定する](how-to-excel-tips.md)」をご覧ください。

3. ファイルを **eventsignup.xls** という名前で保存してから、ファイルを閉じ、OneDrive などの[クラウド ストレージ アカウント](connections/cloud-storage-blob-connections.md) にアップロードします。

> [!IMPORTANT]
> 独自の Excel ファイルを使って、このチュートリアルの一般的な概念だけを確認できます。 ただし、Excel ファイル内のデータは、テーブルとして書式設定されている必要があります。 詳細については、「[Excel でテーブルを書式設定する](how-to-excel-tips.md)」をご覧ください。

## <a name="open-a-blank-app"></a>空のアプリを開く

1. [Power Apps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインします。

1. **自分のアプリを作成する**で、**キャンバス アプリを一から作成**を選択します。

    > [!div class="mx-imgBorder"]
    >![空白のキャンバス アプリを作成する](./media/get-started-create-from-blank/blank-app.png)

1. アプリに名前を指定し、**電話**を選択し、**作成**を選択します。

    携帯電話や他のデバイス (タブレット PC など) 用のアプリを最初から設計できます。 このトピックでは、携帯電話用のアプリの設計について説明します。

    > [!div class="mx-imgBorder"]
    >![アプリの名前と形式を指定する](./media/get-started-create-from-blank/excel-demo.png)

    Power Apps Studio で、携帯電話用の空のアプリが作成されます。

1. **Power Apps Studio へようこそ**のダイアログ ボックスが開いたら、**スキップ**を選択します。

## <a name="connect-to-data"></a>データに接続する

1. 画面の中央で**データに接続**を選択します。

1. **データ** ウィンドウで、クラウド ストレージ アカウントへの接続が表示される場合は、それを選択します。 それ以外の場合は、次の手順で接続を追加します。

    1. **新しい接続**を選択して、お使いのクラウド ストレージ アカウントのタイルを選択してから、**作成**を選択します。
    2. メッセージが表示されたら、そのアカウントの資格情報を指定します。

1. **Excel ファイルの選択**で、**eventsignup** の最初の何文字かを入力するか貼り付けて、一覧をフィルター処理し、アップロードしたファイルを選択します。

1. **テーブルの選択**で、**Schedule** のチェックボックスをオンにしてから、**接続**を選択します。

1. **データ** ウィンドウの右上隅の閉じるアイコン (X) を選択してそれを閉じます。

## <a name="create-the-view-screen"></a>表示スクリーンを作成する

1. **ホーム** タブで、**新しいスクリーン**の横にある下向き矢印を選んで画面の種類の一覧を開き、**リスト**を選択します。

    スクリーンが追加され、いくつかの既定のコントロールが表示されます (検索ボックスや **[Gallery](controls/control-gallery.md)** コントロールなど)。 ギャラリーは、検索ボックスの下の画面全体に広がる領域になります。

1. 新しいスクリーン上部の **[Label](controls/control-text-box.md)** コントロールを選び、**[Title]** を **View records** に置き換えます。

     ![タイトル バーの変更](./media/get-started-create-from-blank/change-title-bar.png)

1. 左のナビゲーション バーで、**BrowseGallery1** を選択します。

    ギャラリーの周囲にハンドルの付いた選択ボックスが表示されます。

    ![リスト画面を追加する](./media/get-started-create-from-blank/select-gallery.png)

1. 右側のウィンドウの **プロパティ** タブで **レイアウト** メニューの下向き矢印を選択します。

    ![レイアウト メニューを開く](./media/get-started-create-from-blank/select-layout.png)

1. **タイトル、サブタイトル、本文** を選択します。

1. 数式バーの **CustomGallerySample** を **Schedule** に置き換え、**SampleText** の両インスタンスを **Volunteer** に置き換えます。

1. 数式バーの右端で下向き矢印を選択し、**テキストの書式設定**を選択します。

    数式が、この例と一致します。

    ```powerapps-dot
    SortByColumns(
        Search(
            Schedule,
            TextSearchBox1.Text,
            "Volunteer"
        ),
        "Volunteer",
        If(
            SortDescending1,
            SortOrder.Descending,
            SortOrder.Ascending
        )
    )
    ```

1. 右側のウィンドウの**プロパティ** タブで、**フィールド** ラベルの横にある**編集**を選択します。

1. **Title2** ボックスで **Volunteer** を選択し、**Subtitle2** ボックスでは **StartDay** を選択し、**Body1** ボックスでは **StartTime** を選択します。

1. **データ** ウィンドウの右上隅の閉じるアイコン (X) を選択してそれを閉じます。

ユーザーは、この数式の **SortByColumns** 関数と **Search** 関数に基づいて、ボランティア名でギャラリーを並べ替えたりフィルター処理したりできます。

- ユーザーが検索ボックスに文字を入力すると、**Volunteer** フィールドにその文字が含まれるレコードだけがギャラリーに表示されます。
- ユーザーが (タイトル バーの更新ボタンとプラス ボタンの間の) 並べ替えボタンを選ぶと、ギャラリーのレコードは **Volunteer** フィールドの値に基づいて (ユーザーがボタンを選んだ回数に応じて) 昇順または降順に並べ替えられます。

これらの関数とその他の関数の詳細については、[数式のリファレンス](formula-reference.md)を参照してください。

## <a name="create-the-change-screen"></a>変更スクリーンを作成する

1. **ホーム** タブで**新しいスクリーン**の横の下向き矢印を選択し、**フォーム**を選択します。

1. 左のナビゲーション バーで **EditForm1** を選択します。

1. 右側のウィンドウの **プロパティ** タブで**データ ソース**の横の下向き矢印を選択し、表示されたリストで**スケジュール**を選択します。

1. 先ほど指定したデータ ソースの下の**フィールドの編集**を選択します。

1. **フィールド** ウィンドウで**フィールドの追加**を選択し、各フィールドのチェック ボックスをオンにしてから、**追加**を選択します。

1. 各フィールドの名前の横の矢印を選択して折りたたみ、**Volunteer** フィールドを上にドラッグし、フィールドのリストの上部にそれが表示されるようにします。

     ![フィールドの順序を変更する](./media/get-started-create-from-blank/reorder-fields.png)

1. **フィールド** ウィンドウの右上隅の閉じるアイコン (X) を選択してそれを閉じます。

1. フォームを選び、次の式を数式バーに入力するか貼り付けて、その **Item** プロパティに設定します。

    `BrowseGallery1.Selected`

1. スクリーン上部の **[Label](controls/control-text-box.md)** コントロールを選び、**[Title]** を **Change records** に置き換えます。

    ![タイトル バーの変更](./media/get-started-create-from-blank/change-title-bar2.png)

## <a name="delete-and-rename-screens"></a>スクリーンの削除と名前の変更

1. 左のナビゲーション バーで、**Screen1** の省略記号 (...) を選択して、**削除**を選択します。

    ![スクリーンの削除](./media/get-started-create-from-blank/delete-screen.png)

1. **Screen2** の省略記号 (...) を選択して、**名前の変更**を選択してから、**ViewScreen** と入力するか貼り付けます。

1. **Screen3** の省略記号 (...) を選択して**名前の変更**を選択してから、**ChangeScreen** と入力するか貼り付けます。

## <a name="configure-icons-on-the-view-screen"></a>表示スクリーンのアイコンを構成する

1. **ViewScreen** の上部で、円形の矢印アイコンを選択します。

    ![レコードの追加](./media/get-started-create-from-blank/refresh-icon.png)

1. そのアイコンの **OnSelect** プロパティに次の数式を設定します。

    `Refresh(Schedule)`

    ユーザーがこのアイコンを選ぶと、**Schedule** からのデータが Excel ファイルから更新されます。

    この関数とその他の関数について詳しくは、「[数式のリファレンス](formula-reference.md)」を参照してください。

1. **ViewScreen** の右上隅で、プラス アイコンを選びます。

    ![レコードの追加](./media/get-started-create-from-blank/add-record.png)

1. そのアイコンの **OnSelect** プロパティに次の数式を設定します。

    `NewForm(EditForm1);Navigate(ChangeScreen,ScreenTransition.None)`

    このアイコンをユーザーが選択すると、各フィールドが空の状態で **ChangeScreen** が表示され、ユーザーはレコードをさらに簡単に作成できます。

1. ギャラリーの最初のレコードの右向き矢印を選択します。

    ![矢印を選択する](./media/get-started-create-from-blank/select-arrow.png)

1. 矢印の **OnSelect** プロパティに次の数式を設定します。

    `EditForm(EditForm1); Navigate(ChangeScreen, ScreenTransition.None)`

    ユーザーがこのアイコンを選択すると、**ChangeScreen** の各フィールドに選択したレコードのデータが表示され、ユーザーはさらに簡単にレコードを編集または削除できます。

## <a name="configure-icons-on-the-change-screen"></a>変更スクリーンのアイコンを構成する

1. **ChangeScreen** で、左上隅の "X" アイコンを選択します。

    ![キャンセル アイコン](./media/get-started-create-from-blank/cancel-icon.png)

1. そのアイコンの **OnSelect** プロパティに次の数式を設定します。

    `ResetForm(EditForm1);Navigate(ViewScreen, ScreenTransition.None)`

    ユーザーがこのアイコンを選択すると、ユーザーがこのスクリーンで行ったすべての変更が破棄されて、表示スクリーンが開きます。

1. 右上隅にあるチェックマーク アイコンを選択します。

    ![チェックマーク アイコン](./media/get-started-create-from-blank/checkmark-icon.png)

1. チェックマークの **OnSelect** プロパティに次の数式を設定します。

    `SubmitForm(EditForm1); Navigate(ViewScreen, ScreenTransition.None)`

    ユーザーがこのアイコンを選択すると、ユーザーがこのスクリーンで行ったすべての変更が保存されて、表示スクリーンが開きます。

1. **挿入**タブで**アイコン**を選択し、**ごみ箱**アイコンを選択します。

1. 新しいアイコンの **Color** プロパティを **White** に設定し、新しいアイコンをチェックマーク アイコンの隣に移動します。

    ![ごみ箱アイコン](./media/get-started-create-from-blank/trash-icon.png)

1. ごみ箱アイコンの **Visible** プロパティに次の数式を設定します。

    `EditForm1.Mode = FormMode.Edit`

    このアイコンは、フォームが**新規**モードではなく、**編集**モードのときのみ表示されます。

1. ごみ箱アイコンの **OnSelect** プロパティに次の数式を設定します。

    `Remove(Schedule, BrowseGallery1.Selected); Navigate(ViewScreen, ScreenTransition.None)`

    ユーザーがこのアイコンを選択すると、選択したレコードがデータ ソースから削除され、表示スクリーンが開きます。

## <a name="test-the-app"></a>アプリをテストする

1. **ViewScreen** を選択してから、F5 キーを押して (または右上隅の**プレビュー** アイコンを選んで) プレビューを開きます。

    ![プレビュー モードを開く](./media/get-started-create-from-blank/open-preview.png)

1. 検索ボックスに文字を 1 つ以上入力するか貼り付けて、ボランティア名に基づいてリストをフィルター処理します。

1. ボランティア名に基づいてデータを昇順または降順で表示するために、並べ替えアイコンを 1 回以上選択します。

1. レコードを追加します。

1. 追加したレコードを更新してから、変更を保存します。

1. 追加したレコードを更新してから、変更を取り消します。

1. 追加したレコードを削除します。

1. Esc キーを押して (または右上隅の閉じるアイコンを選んで)、プレビュー モードを閉じます。

## <a name="next-steps"></a>次の手順

- 他のデバイスから実行できるように、Ctrl-S キーを押してアプリをクラウドに保存します。
- 他のユーザーが実行できるように[アプリを共有](share-app.md) します。
- 標準フォームを作らずにデータを管理できる、**Patch** などの[関数](working-with-formulas.md) について説明します。
- [ソリューションにこのアプリをリンク](add-app-solution.md)することにより、たとえば、別の環境に 展開したり、AppSource に公開することができます。
