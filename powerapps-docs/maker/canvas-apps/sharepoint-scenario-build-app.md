---
title: プロジェクトを管理するキャンバス アプリを作成する | Microsoft Docs
description: このタスクでは、キャンバス アプリを最初から構築します。 ユーザーはこのアプリを使用してプロジェクトの管理者を割り当てたり、プロジェクトの詳細な情報を更新したりできます。
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 04/30/2020
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 2cb9e1be1deade618521a299d115d4011cfeb8a9
ms.sourcegitcommit: 597849e2942c88a5c54953eeb8f14c8c81ac0ae2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "3326155"
---
# <a name="create-a-canvas-app-to-manage-projects"></a>プロジェクトを管理するキャンバス アプリを作成する
> [!NOTE]
> この記事は、Power Apps、Power Automate、および Power BI と SharePoint Online の使用に関するチュートリアル シリーズの一部です。 シリーズ全般に関することや、関連するファイルのダウンロードの詳細について、[シリーズの概要](sharepoint-scenario-intro.md) を必ずご覧ください。

このタスクでは、キャンバス アプリを最初から構築します。 ユーザーはこのアプリを使用してプロジェクトの管理者を割り当てたり、プロジェクトの詳細な情報を更新したりできます。 最初のアプリで見たのと同じコントロールと数式がいくつか表示されますが、今回はそのときよりも多くの機能を自分で作成します。 プロセスはより複雑ですが、より多くのことが学べますので、学習して損しません。

> [!TIP]
> このシナリオの[ダウンロード パッケージ](https://aka.ms/o4ia0f) には、このアプリの完成版 (project-details-app.msapp) が含まれています。

## <a name="quick-review-of-power-apps-studio"></a>Power Apps Studio の復習
Power Apps Studio は 3 つのウィンドウと 1 つのリボンで構成されているため、PowerPoint でスライド デッキを作成するのと同じような感覚でアプリを作成できます。

1. 左側のナビゲーション バー。アプリのすべてのスクリーンとコントロールの階層ビューが表示され、スクリーンのサムネイルも表示されます
2. 中央のウィンドウ。作業しているアプリのスクリーンが含まれます
3. 右側のウィンドウ。レイアウトやデータ ソースなどのオプションを設定します
4. プロパティ ドロップダウン リスト。数式を適用するプロパティを選択します
5. 数式バー。アプリの動作を定義する数式を (Excel のように) 追加します
6. リボン。コントロールを追加し、デザイン要素をカスタマイズします

![Power Apps Studio](./media/sharepoint-scenario-build-app/04-00-00-powerapps-studio.png)

## <a name="step-1-create-screens"></a>手順 1: スクリーンを作成する
復習はほどほどにして、さっそくアプリの作成を開始しましょう。

### <a name="create-and-save-the-app"></a>アプリの作成と保存
1. Power Apps Studio で、**新規**をクリックまたはタップして、**空のアプリ**で、**電話レイアウト**をクリックまたはタップします。
   
    ![空のアプリ - 電話レイアウト](./media/sharepoint-scenario-build-app/04-01-01-blank-phone-app.png)
2. **ファイル**をクリックまたはタップして、**アプリの設定** タブを開きます。「プロジェクト管理アプリ」という名前を入力します。
   
    ![アプリ名](./media/sharepoint-scenario-build-app/04-01-02-app-name.png)
3. **名前を付けて保存**をクリックまたはタップして、アプリの保存先がクラウドであることを確認したら、右下隅にある**保存**をクリックします。
   
    ![クラウドに保存](./media/sharepoint-scenario-build-app/04-01-03-save-to-cloud.png)

4. チェックマーク アイコンを ![アプリに戻るアイコン](./media/sharepoint-scenario-build-app/icon-back-to-app.png) をクリックまたはタップしてアプリに戻ります。

### <a name="add-four-screens-to-the-app"></a>アプリに 4 つのスクリーンを追加する
この手順では、アプリに 4 つの空のスクリーンを作成します。 スクリーンの目的に応じて、スクリーンのレイアウトが異なります。 後の手順で、これらの画面に内容を追加します。

| **スクリーン** | **目的** |
| --- | --- |
| **SelectTask** |開始スクリーン。他のスクリーンに移動します |
| **AssignManager** |承認されたプロジェクトに管理者を割り当てます |
| **ViewProjects** |プロジェクトの一覧と概要情報を表示します |
| **UpdateDetails** |プロジェクトの詳細を表示したり、更新したりします |

1. **ホーム** タブで、**新しいスクリーン**、**スクロール可能なスクリーン**の順にクリックまたはタップします。
   
    ![スクロール可能なスクリーン](./media/sharepoint-scenario-build-app/04-01-03a-scrollable-screen.png)
2. スクリーンの名前を **SelectTask** に変更します。
   
    ![スクリーンの名前変更](./media/sharepoint-scenario-build-app/04-01-04-rename-screen.png)
3. 追加のスクリーンを作成し、名前を変更します。
   
   1. **新しいスクリーン**、**スクロール可能なスクリーン**の順にクリックまたはタップします。 スクリーンの名前を **AssignManager** に変更します。
   2. **新しいスクリーン**、**リスト スクリーン**の順にクリックまたはタップします。 スクリーンの名前を **ViewProjects** に変更します。
   3. **新しいスクリーン**、**フォーム スクリーン**の順にクリックまたはタップします。 スクリーンの名前を **UpdateDetails** に変更します。
4. **Screen1** の横にある省略記号 (**. . .**) を選択し、**削除**をクリックまたはタップします。
   
    ![スクリーンの削除](./media/sharepoint-scenario-build-app/04-01-04a-delete-screen.png)

アプリは次のイメージのようになります。

![アプリのすべてのスクリーン](./media/sharepoint-scenario-build-app/04-01-05-all-screens.png)

## <a name="step-2-connect-to-a-sharepoint-list"></a>手順 2: SharePoint リストに接続する
この手順では、**プロジェクトの詳細** SharePoint リストに接続します。 このアプリでは 1 つのリストを使用するだけですが、アプリを拡張するときは両方に簡単に接続できます。

1. 左側のナビゲーション バーで、**SelectTask** スクリーンをクリックまたはタップします。
2. 右側のウィンドウで、**データ ソースの追加**をクリックまたはタップします。
   
    ![データに接続する](./media/sharepoint-scenario-build-app/04-02-01-connect.png)
3. **新しい接続**をクリックまたはタップします。
   
    ![新しいつながり](./media/sharepoint-scenario-build-app/04-02-02-new-connection.png)
4. **SharePoint**をクリックまたはタップします。
   
    ![SharePoint 接続](./media/sharepoint-scenario-build-app/04-02-03-sharepoint-connection.png)
5. **直接接続 (クラウド サービス)** を選択して、**作成**をクリックまたはタップします。
   
    ![直接接続 (クラウド サービス)](./media/sharepoint-scenario-build-app/04-02-03a-sharepoint-cloud.png)
6. SharePoint の URL を入力し、**移動**をクリックまたはタップします。
   
    ![接続用の SharePoint URL](./media/sharepoint-scenario-build-app/04-02-04-sharepoint-url.png)
7. **プロジェクトの詳細**リストを選択し、**接続**をクリックまたはタップします。
   
    ![プロジェクトの詳細リストの選択](./media/sharepoint-scenario-build-app/04-02-05-sharepoint-lists.png)
   
    右側のウィンドウにある**データ ソース**タブに、作成した接続が表示されます。
   
    ![データ ソース タブ](./media/sharepoint-scenario-build-app/04-02-06-data-sources.png)

## <a name="step-3-build-the-selecttask-screen"></a>手順 3: SelectTask スクリーンを作成する
この手順では、Power Apps のコントロール、数式、書式設定オプションを使用して、アプリの他のスクリーンに移動する方法を説明します。

### <a name="update-the-title-and-insert-introductory-text"></a>タイトルを更新して導入テキストを挿入する
1. 左側のナビゲーション バーで、**SelectTask** スクリーンを選択します。
2. 中央のウィンドウで既定の **[タイトル]** を選択して、数式バーで **Text** プロパティを "Contoso Project Management" に更新します。
   
    ![数式バーの Text プロパティ](./media/sharepoint-scenario-build-app/04-03-02-text-property.png)
3. **挿入**タブで、**ラベル**をクリックまたはタップし、上部のバナーの下にラベルをドラッグします。
   
    ![ラベルの追加](./media/sharepoint-scenario-build-app/04-03-03-text-default.png)
4. 数式バーで、ラベルに次のプロパティを設定します。
   
   * **Color** プロパティ = **DarkGray**

   * **Size** プロパティ = **18**

   * **Text** プロパティ = "**続行するにはクリックまたはタップしてください ..."**
     
     ![ラベルのテキストの更新](./media/sharepoint-scenario-build-app/04-03-04-text-updated.png)

### <a name="add-two-navigation-buttons"></a>2 つのナビゲーション ボタンを追加する
1. **挿入**タブで、**ボタン**をクリックまたはタップし、ラベルの下にボタンをドラッグします。
   
    ![\[Add\] (追加) ボタン](./media/sharepoint-scenario-build-app/04-03-05-button-default.png)
2. 数式バーで、ボタンに次のプロパティを設定します。
   
   * **OnSelect** プロパティ = **Navigate(AssignManager, Fade)**。 アプリを実行してこのボタンをクリックすると、アプリの 2 番目のスクリーンに移動する際にフェードしてスクリーンが切り替わります。

   * **Text** プロパティ = **"管理者の割り当て"**

3. テキストに合わせてボタンのサイズを変更します。
   
    ![ボタンのテキストの更新](./media/sharepoint-scenario-build-app/04-03-06-button-updated.png)
4. 次のプロパティを持つ別のボタンを挿入します。
   
   * **OnSelect** プロパティ = **Navigate(ViewProjects, Fade)**。

   * **Text** プロパティ = **"詳細の更新"**
     
     ![ボタンのテキストの更新](./media/sharepoint-scenario-build-app/04-03-08-buttons-final.png)
     
     > [!NOTE]
     > ボタンのラベルは**詳細の更新**ですが、最初に **ViewProjects** スクリーンに移動して、更新するプロジェクトを選択します。

### <a name="run-the-app"></a>アプリの実行
アプリはまだ完成していませんが、必要に応じて実行することができます。

1. **SelectTask** スクリーンをクリックまたはタップします (アプリは常に Power Apps Studio のプレビュー モードで選択したスクリーンから開始します)。

2. チェックマーク アイコンを ![アプリの実行アイコン](./media/sharepoint-scenario-build-app/icon-run-arrow.png) をクリックまたはタップし、アプリを実行します。

3. ボタンのいずれか 1 つをクリックまたはタップして別のスクリーンに移動します。

4. チェックマーク アイコンを ![アプリ プレビューを閉じるアイコン](./media/sharepoint-scenario-build-app/icon-close-preview.png) をクリックまたはタップしてアプリを閉じます。

## <a name="step-4-build-the-assignmanager-screen"></a>手順 4: AssignManager スクリーンを作成する
この手順では、承認後にまだ管理者が割り当てられていないプロジェクトを、ギャラリーを使用してすべて表示します。 他のコントロールを追加することで、管理者を割り当てられるようになります。

> [!NOTE]
>  プロジェクトのすべてのフィールド (管理者フィールドも含む) を編集できるページをあとでアプリ内に作成しますが、このようなスクリーンも作成したほうが出来栄えが良くなります。

1. ここまでに行った変更を保存します。

2. 左側のナビゲーション バーで、**AssignManager** スクリーンをクリックまたはタップします。

### <a name="update-the-title-and-insert-introductory-text"></a>タイトルを更新して導入テキストを挿入する

1. **[タイトル]** を**管理者の割り当て**に変更します。

2. 次のプロパティをラベルに追加します。
   
   * **Color** プロパティ = **DarkGray**

   * **Size** プロパティ = **18**

   * **Text** プロパティ = "**プロジェクトを選択して、管理者を割り当てる"**
     
     ![管理者の割り当てのレイアウト](./media/sharepoint-scenario-build-app/04-04-01-layout.png)

### <a name="add-a-back-arrow-to-return-to-the-selecttask-screen"></a>SelectTask スクリーンに戻るための戻る矢印を追加する

1. スクリーンの上部に表示される青色のバーをクリックまたはタップします。

2. **挿入**タブで、**アイコン**、**左**の順にクリックまたはタップします。
   
    ![左矢印の挿入](./media/sharepoint-scenario-build-app/04-04-02-icon-left.png)

3. 青色のバーの左側に矢印を移動し、次のプロパティを設定します。
   
   * **Color** プロパティ = **White**

   * **Height** プロパティ = **40**

   * **OnSelect** プロパティ = **Navigate(SelectTask, Fade)**

   * **Width** プロパティ = **40**
     
     ![戻るボタンの追加](./media/sharepoint-scenario-build-app/04-04-03-left-arrow.png)

### <a name="add-and-modify-a-gallery"></a>ギャラリーを追加して変更する

1. **挿入**タブで、**ギャラリー**、**縦**の順にクリックまたはタップします。
   
    ![縦方向のギャラリーの追加](./media/sharepoint-scenario-build-app/04-04-04-gallery.png)

2. 右側のウィンドウにある**レイアウト**メニューから、**タイトル、サブタイトル、本文**を選択します。 
   
    ![ギャラリー レイアウトの変更](./media/sharepoint-scenario-build-app/04-04-04a-gallery-layout.png)
   
    ギャラリーに適切なレイアウトが作成されましたが、既定のサンプル テキストが表示されたままです。 次にこれを修正します。
   
    ![既定のテキストが表示されているギャラリー](./media/sharepoint-scenario-build-app/04-04-05-gallery-default.png)

3. ギャラリーに次のプロパティを設定します。
   
   * **BorderThickness** プロパティ = **1**

   * **BorderStyle** プロパティ = **Dotted**

   * **Items** プロパティ = **Filter('Project Details', PMAssigned="Unassigned")** 管理者が割り当てられていないプロジェクトのみがギャラリーに表示されます。
     
     ![リストからのテキストが表示されているギャラリー](./media/sharepoint-scenario-build-app/04-04-06-gallery-updated.png)

4. 右側のウィンドウで、次の一覧と一致するようにフィールドを更新します。
   
   * **ApprovedDate**

   * **状況**

   * **タイトル**
     
     ![ギャラリー フィールド](./media/sharepoint-scenario-build-app/04-04-07-gallery-fields.png)

5. 必要に応じて、ギャラリー内のラベルのサイズを変更し、最初のギャラリー アイテムから矢印を削除します (このギャラリー内から別の場所に移動する必要はありません)。
   
    ![矢印アイコンの削除](./media/sharepoint-scenario-build-app/04-04-07a-remove-arrow.png)
   
    スクリーンは次のように表示されます。
   
    ![書式設定されたギャラリー](./media/sharepoint-scenario-build-app/04-04-07b-gallery-size-text.png)

### <a name="change-the-color-of-an-item-if-its-selected"></a>選択された場合のアイテムの色を変更する

1. ギャラリーを選択し、**TemplateFill** プロパティを **If (ThisItem.IsSelected=true, Orange, White)** に設定します。

2. ギャラリー内のアイテムを選択します。 スクリーンは次のように表示されます。
   
    ![選択したアイテムが表示されているギャラリー](./media/sharepoint-scenario-build-app/04-04-08-gallery-selected.png)

### <a name="add-a-label-text-input-and-ok-button-to-submit-manager-assignments"></a>管理者の割り当てを送信するための、ラベル、テキスト入力、OK ボタンを追加する

1. 作業していたギャラリーの外側をクリックまたはタップします。

2. **挿入**タブで、**ラベル**をクリックまたはタップします。 ギャラリーの下のラベルを左側にドラッグします。 ラベルに次のプロパティを設定します。
   
   * **Size** プロパティ = **20**

   * **Text** プロパティ = **"管理者:"**
   
   ![管理者ラベルの追加](./media/sharepoint-scenario-build-app/04-04-09-controls-text.png)

3. **挿入**タブで、**テキスト**、**テキスト入力**の順にクリックまたはタップします。 ギャラリーの下のテキスト入力を中央にドラッグします。 ドロップダウンに次のプロパティを設定します。
   
   * **Default** プロパティ = **""**

   * **Height** プロパティ = **60**

   * **Size** プロパティ = **20**

   * **Width** プロパティ = **250**
   
   ![テキスト入力を追加する](./media/sharepoint-scenario-build-app/04-04-10-controls-text-box.png)

4. **挿入**タブで、**ボタン**をクリックまたはタップします。 ギャラリーの下のボタンを右側にドラッグします。 ボタンに次のプロパティを設定します。
   
   * **Height** プロパティ = **60**

   * **OnSelect** プロパティ = **Patch('Project Details', LookUp('Project Details', ID = Gallery1.Selected.ID), {PMAssigned: TextInput1.Text})**. 詳細については、「[数式の詳細](#formula-deep-dive)」をご覧ください。

   * この数式で、**プロジェクトの詳細**リストを更新し、PMAssigned フィールドの値を設定します。

   * **Size** プロパティ = **20**

   * **Text** プロパティ = **"OK"**

   * **Width** プロパティ = **80**
   
   ![OK ボタンの追加](./media/sharepoint-scenario-build-app/04-04-11-controls-button.png)

完成したスクリーンは次のように表示されます。

![管理者の割り当て完成画面](./media/sharepoint-scenario-build-app/04-04-12-complete.png)

## <a name="step-5-build-the-viewprojects-screen"></a>手順 5: ViewProjects スクリーンを作成する
この手順では、**ViewProjects** スクリーンでギャラリーのプロパティを変更します。 このギャラリーで**プロジェクトの詳細**リストのアイテムが表示されます。 この画面でアイテムを選択し、**UpdateDetails** スクリーンで詳細を編集します。

1. 左側のナビゲーション バーで、**ViewProjects** スクリーンをクリックまたはタップします。

2. **[タイトル]** を **「プロジェクトの表示」** に変更します。

3. 左側のナビゲーション バーで、**ViewProjects** の下にある **BrowserGallery1** をクリックまたはタップします。

4. 右側のウィンドウにある**レイアウト**メニューから、**タイトル、サブタイトル、本文**を選択します。 
   
    ![ギャラリー レイアウトの変更](./media/sharepoint-scenario-build-app/04-04-04a-gallery-layout.png)
   
    ギャラリーに適切なレイアウトが作成され、既定のサンプル テキストが表示されています。
   
    ![既定のテキストが表示されているギャラリー](./media/sharepoint-scenario-build-app/04-04-04b-gallery-default.png)

5. 更新ボタン ![更新アイコン](./media/sharepoint-scenario-build-app/icon-refresh.png) を選択し、その **OnSelect** プロパティを **Refresh('Project Details')** に設定します。

6. 新しいアイテム ボタン![新規アイコンの追加](./media/sharepoint-scenario-build-app/icon-add-item.png) を選択し、その **OnSelect** プロパティを **NewForm(EditForm1); Navigate(UpdateDetails, ScreenTransition.None)** に設定します。

### <a name="add-a-back-arrow-to-return-to-the-selecttask-screen"></a>SelectTask スクリーンに戻るための戻る矢印を追加する

1. 左側のナビゲーション バーで、**AssignManager** スクリーンをクリックまたはタップします。

2. ここに追加した戻る矢印を選択し、コピーします。

3. 矢印を **ViewProjects** スクリーンに貼り付けて、更新ボタンの左側に配置します。 
   
    ![戻るボタン](./media/sharepoint-scenario-build-app/04-05-04-left-arrow-v.png)
   
    **Navigate(SelectTask, Fade)** の **OnSelect** プロパティも含め、プロパティのすべてが付随します。

### <a name="change-the-data-source-for-the-browsegallery1-gallery"></a>BrowseGallery1 ギャラリーのデータ ソースを変更する

1. **BrowseGallery1** ギャラリーを選択し、ギャラリーの **Items** プロパティを **SortByColumns(Filter('Project Details', StartsWith(Title, TextSearchBox1.Text)), "Title", If(SortDescending1, Descending, Ascending))** に設定します。
   
    これにより、ギャラリーのデータ ソースが**プロジェクトの詳細**リストに設定され、その **タイトル** フィールドを使用して検索や並べ替えが行われるようになります。

2. 最初のギャラリー アイテムで ![詳細矢印アイコン](./media/sharepoint-scenario-build-app/icon-details-arrow.png) を選択し、**OnSelect** プロパティを **Navigate(UpdateDetails, None)** に設定します。
   
    ![ プロジェクトの表示ギャラリー - 最初の選択済みのアイテム](./media/sharepoint-scenario-build-app/04-05-05b-gallery-arrow-v.png)

3. 右側のウィンドウで、次の一覧と一致するようにフィールドを更新します。
   
   * **状況**

   * **PMAssigned**

   * **タイトル**
     
     ![ギャラリー フィールド](./media/sharepoint-scenario-build-app/04-05-06-gallery-fields.png)
     
     完成したスクリーンは次のように表示されます。
     
     ![完成したプロジェクトの表示スクリーン](./media/sharepoint-scenario-build-app/04-05-07-viewprojects-final.png)

## <a name="step-6-build-the-updatedetails-screen"></a>手順 6: UpdateDetails スクリーンを作成する
この手順では、**UpdateDetails** スクリーンの編集フォームをデータ ソースに接続し、いくつかのプロパティとフィールドを変更します。 このスクリーンで、**プロジェクトの表示**スクリーンで選択したプロジェクトの詳細を編集します。

1. 左側のナビゲーション バーで、**UpdateDetails** スクリーンをクリックまたはタップします。

2. **[タイトル]** を **"詳細の更新"** に変更します。

3. 左側のナビゲーション バーで、**UpdateDetails** の下にある **EditForm1** をクリックまたはタップします。

4. フォームに次のプロパティを設定します。
   
   * **DataSource** プロパティ = **'Project Details'**

   * **Item** プロパティ = **BrowseGallery1.Selected**

5. フォームを選択したまま、右側のウィンドウで、次の順番で表示されるフィールドのチェックボックスをクリックまたはタップします。
   
   * **タイトル**

   * **PMAssigned**

   * **状況**

   * **ProjectedStartDate**

   * **ProjectedEndDate**

   * **ProjectedDays**

   * **ActualDays**
     
     ![フォーム フィールドの編集](./media/sharepoint-scenario-build-app/04-06-03-edit-fields.png)
6. キャンセル ボタン ![キャンセル アイコン](./media/sharepoint-scenario-build-app/icon-cancel.png) を選択し、その **OnSelect** プロパティを **ResetForm(EditForm1); Back()** に設定します。

7. 保存ボタン ![チェック マーク保存アイコン](./media/sharepoint-scenario-build-app/icon-check-mark.png) を選択し、**OnSelect** の数式が **SubmitForm(EditForm1)** になっていることを確認します。 編集フォーム コントロールを使用するため、以前使用した **Patch()** ではなく **Submit()** を使用できます。

完成したスクリーンは次のように表示されます (フィールドが空白の場合は、必ず**プロジェクトの表示**スクリーンでアイテムを選択してください)。

![完成した詳細の更新スクリーン](./media/sharepoint-scenario-build-app/04-06-06-edit-final.png)

## <a name="step-7-run-the-app"></a>手順 7: アプリを実行する
アプリが完成したので、実行して動作を確認します。 SharePoint サイトにアプリへのリンクを追加します。 アプリをブラウザで実行することはできるが、他のユーザーが実行できるようにアプリを共有する必要がある場合もあります。 詳細については、「[アプリの共有](share-app.md)」をご覧ください。

### <a name="add-a-link-to-the-app"></a>アプリへのリンクを追加する
1. Office 365 アプリ起動ツールで、**PowerApps** をクリックまたはタップします。
   
    ![Office 365 アプリ起動ツールの Power Apps](./media/sharepoint-scenario-build-app/04-07-02a-waffle.png)

2. Power Apps で、**プロジェクト管理アプリ**の省略記号 (**. . .**) を選択して**開く**をクリックまたはタップします。
   
    ![プロジェクト管理アプリの選択](./media/sharepoint-scenario-build-app/04-07-02b-select-app.png)

3. ブラウザーでアプリのアドレス (URL) をコピーします。
   
    ![アプリ の URL をコピー](./media/sharepoint-scenario-build-app/04-07-02ba-copy-url.png)

4. SharePoint で、**リンクの編集**をクリックまたはタップします。
   
    ![SharePoint サイトのリンクを編集する](./media/sharepoint-scenario-build-app/04-07-02c-edit-links.png)

5. **(+) リンク**をクリックまたはタップします。
   
    ![SharePoint サイトへのアプリ リンクを追加する](./media/sharepoint-scenario-build-app/04-07-02d-add-link.png)

6. 「プロジェクト管理アプリ」と入力して、アプリのアドレスを貼り付けます。
   
    ![リンクのプロパティの編集](./media/sharepoint-scenario-build-app/04-07-02e-link-dialog.png)

7. **OK**、**保存**の順にクリックまたはタップします。
   
    ![リンクの変更の保存](./media/sharepoint-scenario-build-app/04-07-02f-save.png)

### <a name="assign-a-manager-to-a-project"></a>プロジェクトに管理者を割り当てる
SharePoint サイトでアプリの準備ができたので、続いてプロジェクト承認者のロールに基づき、管理者が割り当てられていないプロジェクトを探し、プロジェクトの 1 つに管理者を割り当てます。 次に、プロジェクト管理者のロールに基づき、自分たちに割り当てられているプロジェクトに関する情報を追加します。

1. 最初に、SharePoint の**プロジェクトの詳細**リストを見てみましょう。 2 つのプロジェクトで、**PMAssigned** 列の値が **Unassigned** になっています。 アプリ内でこれらを確認します。
   
    ![SharePoint リスト内の未割り当てプロジェクト](./media/sharepoint-scenario-build-app/04-07-01-unassigned.png)

2. 作成したアプリへのリンクをクリックまたはタップします。

3. 最初の画面で、**管理者の割り当て**をクリックまたはタップします。
   
    ![アプリの概要スクリーン](./media/sharepoint-scenario-build-app/04-07-03-intro-screen.png)

4. **管理者の割り当て**画面で、リストに 2 つの未割り当てプロジェクトが表示されています。 **新しい BI ソフトウェア** プロジェクトを選択します。
   
    ![アイテムが選択されたギャラリー](./media/sharepoint-scenario-build-app/04-07-04-selected.png)

5. **管理者**のテキスト入力欄に、「Joni Sherman」と入力して **OK** をクリックします。
   
    変更がリストに反映されてギャラリーが更新されると、残りの未割り当てプロジェクトのみが表示されます。
   
    ![プロジェクトへの管理者の割り当て](./media/sharepoint-scenario-build-app/04-07-05-updated.png)

6. SharePoint リストに戻り、ページを更新します。 プロジェクトのエントリが更新されてプロジェクト管理者名が表示されます。
   
    ![SharePoint リストに割り当てられたプロジェクト管理者](./media/sharepoint-scenario-build-app/04-07-07-assigned.png)

### <a name="update-details-for-the-project"></a>プロジェクトの詳細の更新

1. ![戻るアイコン](./media/sharepoint-scenario-build-app/icon-back.png) をクリックまたはタップして最初のスクリーンに戻り、**詳細の更新**をクリックまたはタップします。
   
   ![アプリの概要スクリーン](./media/sharepoint-scenario-build-app/04-07-08-intro-screen.png)

2. **プロジェクトの表示**スクリーンで、検索ボックスに「新規」と入力します。
   
   ![アプリのギャラリー内で検索](./media/sharepoint-scenario-build-app/04-07-09-search-new.png)

3. **新しい BI ソフトウェア** アイテムの![詳細矢印アイコン](./media/sharepoint-scenario-build-app/icon-details-arrow.png) をクリックします。
   
   ![選択したギャラリー アイテム](./media/sharepoint-scenario-build-app/04-07-10-select-project.png)

4. **詳細の更新**スクリーンで、次の値を設定します。
   
   * **ProjectedStartDate** フィールド = "3/6/2017"

   * **ProjectedEndDate** フィールド = "3/24/2017"

   * **ProjectedDays** フィールド = "15"
   
   ![アイテムの詳細の更新](./media/sharepoint-scenario-build-app/04-07-11-update.png)

5. チェックマーク アイコンを ![クリックまたはタップして、](./media/sharepoint-scenario-build-app/icon-check-mark.png) をクリックまたはタップして、SharePoint リストに変更を適用します。

6. アプリを閉じて、リストに戻ります。 プロジェクトのエントリが更新されて変更日時が表示されます。
   
    ![更新された SharePoint リスト](./media/sharepoint-scenario-build-app/04-07-11-updated-list.png)

## <a name="formula-deep-dive"></a>数式の詳細
このセクションは、Power Apps の数式に関する 2 つ目の省略可能なセクションです。 最初の詳細では、Power Apps が生成し、3 画面アプリ内のブラウズ ギャラリーで使用される数式の 1 つを確認しました。 この詳細では、2 つ目のアプリの **AssignManager** スクリーンで使用する数式を確認します。 数式は次のとおりです。

**Patch( 'Project Details', LookUp( 'Project Details', ID = Gallery1.Selected.ID ), {PMAssigned: TextInput1.Text} )**

この数式について説明します。 ギャラリーでアイテムを選択して **OK** ボタンをクリックすると、この数式は**プロジェクトの詳細**リストを更新し、**PMAssigned** 列にテキスト入力で指定した値を設定します。 この数式は、次の関数を使用します。

* [**Patch** 関数](functions/function-patch.md) は、データ ソースの 1 つ以上のレコードを変更します。

* [**LookUp** 関数](functions/function-filter-lookup.md) は、数式を満たすテーブルでの最初のレコードを検索します。

これらの関数を数式に組み込むと、次のようになります。

1. **OK** ボタンをクリックすると、**Patch** 関数が呼び出されて、**プロジェクトの詳細**リストを更新します。

2. **Patch** 関数内で、**LookUp** 関数は**プロジェクトの詳細**リストのどの行を更新するのかを特定します。 選択したギャラリー アイテムの ID とリスト内の ID を比較することで特定します。 たとえば、ID を 12 とすると、**新しい BI ソフトウェア**のエントリが更新されます。

3. **Patch** 関数は正しい ID を取得すると、**PMAssigned** フィールドを更新して **TextInput1.Text** 内の値に設定します。

## <a name="next-steps"></a>次の手順
このチュートリアル シリーズの次の手順では、[プロジェクトを分析する Power BI レポートを作成](sharepoint-scenario-build-report.md) します。

