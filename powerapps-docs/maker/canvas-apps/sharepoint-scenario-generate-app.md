---
title: プロジェクトの申請を処理するキャンバス アプリを生成する | Microsoft Docs
description: このタスクでは、3 つの画面を備えた基本的なキャンバス アプリを SharePoint リストから直接生成します。
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 06/12/2017
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: cbf5fdaf3ae6cbba2f89124316ac6d23455a712c
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3306959"
---
# <a name="generate-a-canvas-app-to-handle-project-requests"></a>プロジェクトの申請を処理するキャンバス アプリを生成する
> [!NOTE]
> この記事は、Power Apps、Power Automate、および Power BI と SharePoint Online の使用に関するチュートリアル シリーズの一部です。 シリーズ全般に関することや、関連するファイルのダウンロードの詳細について、[シリーズの概要](sharepoint-scenario-intro.md) を必ずご覧ください。

SharePoint リストの用意ができたため、最初のアプリを作成し、カスタマイズできます。 Power Apps は SharePoint に統合されているため、基本の *3 画面アプリ*をリストから直接、簡単に生成できます。 このアプリを使用すると、各リスト アイテムの概要と詳細情報を表示し、既存のリスト アイテムを更新し、新規リスト アイテムを作成できます。 リストから直接アプリを作成すると、アプリがそのリストの*ビュー*として表示されます。 その後、そのアプリをブラウザーや携帯電話で実行できます。

> [!TIP]
> このシナリオ用の[ダウンロード パッケージ](https://aka.ms/o4ia0f) には、このアプリの完成版 (project-requests-app.msapp) が含まれています。

## <a name="step-1-generate-an-app-from-a-sharepoint-list"></a>手順 1: SharePoint リストからアプリを生成する

1. 作成した**プロジェクトの申請**リストで、**PowerApps**、**アプリの作成**の順にクリックまたはタップします。
   
    ![アプリの作成](./media/sharepoint-scenario-generate-app/02-01-01-create-app.png)

2. アプリに「プロジェクトの申請アプリ」のような名前を指定し、**作成**をクリックまたはタップします。 アプリの準備が整うと、Power Apps Studio でそのアプリが開きます。
   
    ![アプリの名前を指定する](./media/sharepoint-scenario-generate-app/02-01-02-create-app-name.png)

## <a name="step-2-review-the-app-in-power-apps-studio"></a>手順 2: Power Apps Studio でのアプリのレビュー

1. Power Apps Studio では、既定では左側のナビゲーション バーに、スクリーンの階層ビューとアプリのコントロールが表示されます。
   
    ![階層ビューが表示された Power Apps Studio](./media/sharepoint-scenario-generate-app/02-02-01-studio-screens-hierarchy.png)

2. サムネイル アイコンをクリックまたはタップしてビューを切り替えます。
   
    ![Power Apps Studio ビュー セレクター](./media/sharepoint-scenario-generate-app/02-02-02-studio-view-selector.png)

3. 各スクリーンをクリックまたはタップしてスクリーンを中央のウィンドウに表示します。 スクリーンは 3 つあります。
   
    (a). **参照**スクリーンでは、リストから収集されたデータを参照、並べ替え、およびフィルター処理できます。
    
    (b). **詳細**スクリーンでは、アイテムの詳細を表示できます。
    
    (c). **編集/作成**スクリーンでは、既存のアイテムを編集したり、新規のアイテムを作成したりできます。
      
      ![サムネイル表示された Power Apps Studio](./media/sharepoint-scenario-generate-app/02-02-03-studio-screens-thumbnails.png)

## <a name="step-3-customize-the-apps-browse-screen"></a>手順 3: アプリの参照スクリーンをカスタマイズする

1. 参照スクリーンをクリックまたはタップします。
   
    このスクリーンには*ギャラリー*を含む*レイアウト*が配置され、リスト アイテムのほか、検索バーや並べ替えボタンなどの他の*コントロール*も表示されます。

2. 1 つ目を除く任意のレコードをクリックまたはタップして **BrowseGallery1** ギャラリーを選択します。
   
    ![ギャラリーを参照する](./media/sharepoint-scenario-generate-app/02-03-01-browse-gallery.png)

3. 右側のウィンドウで、**プロパティ**から**プロジェクトの申請**をクリックまたはタップします。 

4. 次のリストと一致するフィールドを更新します。
   
   * **RequestDate**

   * **Requestor**

   * **タイトル**

     ![ギャラリー フィールド](./media/sharepoint-scenario-generate-app/02-03-02-gallery-fields.png)

5. **BrowseGallery1** を選択したまま、**Items** プロパティを選択します。
   
    ![Items プロパティ](./media/sharepoint-scenario-generate-app/02-03-03-items.png)

6. 数式を **SortByColumns(Filter('Project Requests', StartsWith(Title, TextSearchBox1.Text)), "Title", If(SortDescending1, Descending, Ascending))** のように変更します。
   
    ![数式バー](./media/sharepoint-scenario-generate-app/02-03-04-formula.png)
   
    これにより、Power Apps での既定ではなく、**タイトル** フィールドを基に、並べ替えおよび検索を行うことができます。 詳細については、「[数式の詳細](#formula-deep-dive)」を参照してださい。

6. **ファイル**、**保存**の順にクリックまたはタップします。 ![アプリに戻るアイコン](./media/sharepoint-scenario-generate-app/icon-back-to-app.png) をクリックまたはタップして、アプリに戻ります。

## <a name="step-4-review-the-apps-details-screen-and-edit-screen"></a>手順 4: アプリの詳細スクリーンを確認し、スクリーンを編集する
1. 詳細スクリーンをクリックまたはタップします。
   
    このスクリーンには*表示フォーム*を含む別のレイアウトが配置され、そこにギャラリーで選択したアイテムの詳細が表示されます。 また、アイテムを編集および削除するためのコントロールと、参照スクリーンに戻るためのコントロールも表示されます。
   
    ![詳細表示フォーム](./media/sharepoint-scenario-generate-app/02-04-01-details.png)

4. 編集スクリーンをクリックまたはタップします。
   
    このスクリーンには、選択したアイテムを編集したり、新規アイテムを作成したりするための*編集フォーム*が表示されます (参照スクリーンから直接このスクリーンに移動した場合)。 編集内容を保存または破棄するためのコントロールがあります。

    ![編集フォーム](./media/sharepoint-scenario-generate-app/02-04-03-edit.png)

## <a name="step-5-run-the-app-from-the-list"></a>手順 5: リストからアプリを実行する

1. **プロジェクトの申請**リストで、**すべてのアイテム**、**プロジェクトの申請アプリ**の順にクリックまたはタップします。
   
    ![プロジェクトの申請アプリを表示する](./media/sharepoint-scenario-generate-app/02-05-01-view-app.png)
2. **開く**をクリックすると、新しいブラウザー タブでアプリが開きます。
   
    ![プロジェクトの申請アプリを開く](./media/sharepoint-scenario-generate-app/02-05-02-open-app.png)

3. アプリで ![詳細に移動アイコン](./media/sharepoint-scenario-generate-app/icon-details-arrow.png) をクリックまたはタップし、参照ギャラリーの最初の項目を表示します。
   
    ![最初のギャラリー アイテム](./media/sharepoint-scenario-generate-app/02-05-04-first-item.png)

4. チェックマーク アイコンを ![鉛筆の編集アイコン](./media/sharepoint-scenario-generate-app/icon-pencil.png) をクリックまたはタップし、アイテムを編集します。

5. 最後の語の「グループ」を「チーム」に変更して**説明**フィールドを更新し、![チェック マーク アイコン](./media/sharepoint-scenario-generate-app/icon-check-mark.png) をクリックまたはタップします
   
   ![説明フィールドを更新する](./media/sharepoint-scenario-generate-app/02-05-07-edit.png)

6. ブラウザー タブを閉じます。

7. **プロジェクトの申請**リストに戻り、**プロジェクトの申請アプリ**、**すべてのアイテム**の順にクリックまたはタップします。
   
   ![すべてのアイテムを表示する](./media/sharepoint-scenario-generate-app/02-05-08-view-all.png)
8. アプリから行った変更を確認します。
   
    ![編集内容を確認する](./media/sharepoint-scenario-generate-app/02-05-09-verify-edit.png)

これは非常に単純なアプリで、基本的なカスタマイズをいくつか行っただけですが、興味深いものをすばやく構築できます。 次のタスクに移りますが、必要に応じて、アプリについてさらに深く考察し、コントロールと数式がどのように連携してアプリの動作を制御するかを確認してください。

## <a name="formula-deep-dive"></a>数式の詳細
このセクションは省略可能ですが、数式の使用方法を深く理解するのに役立ちます。 このタスクの手順 3 では、**BrowseGallery1** の **Items** プロパティの数式を変更しました。 具体的には、Power Apps の既定フィールドではなく**タイトル** フィールドを使用するように、並び替えと検索を変更しました。 次に、変更した式を示します。

**SortByColumns ( Filter ( 'Project Requests', StartsWith ( Title, TextSearchBox1.Text ) ), "Title", If ( SortDescending1, Descending, Ascending ) )**

この数式はどのような処理を行うのでしょうか? ギャラリーに表示されるデータのソースを判別し、検索ボックスに入力されたテキストを基にデータをフィルター処理し、アプリの並べ替えボタンを基に結果を並べ替えます。 この数式は、次の*関数*を使用します。 関数は、パラメーター (入力) を受け取り、演算 (フィルター処理など) を実行し、値 (出力) を返します。

* [**SortByColumns** 関数](functions/function-sort.md) は、1 つ以上の列に基づいてテーブルを並べ替えます。
* [**Filter** 関数](functions/function-filter-lookup.md) は、指定した数式を満たすテーブル内のレコードを検索します。
* [**StartsWith** 関数](functions/function-startswith.md) は、あるテキスト文字列が別のテキスト文字列で始まるかどうかをテストします。
* [**If** 関数](functions/function-if.md) は、条件が true の場合はある値を返し、同じ条件が false の場合は別の値を返します。

これらの関数を数式に組み込むと、次のようになります。

1. 検索ボックスにテキストを入力すると、**StartsWith** 関数は、このテキストと、リスト内の**タイトル**列にある各文字列の最初の文字を比較します。
   
    **StartsWith ( Title, TextSearchBox1.Text )**
   
    たとえば、検索ボックスに「de」と入力すると、「Desktop」や「Device」で始まる項目を含む 4 つの結果が表示されます。 「Mobile devices」の項目は「de」*で始まる*アイテムではないため、表示されません。

2. **Filter** 関数は**プロジェクトの申請**テーブルの行を*返します*。 検索ボックスに比較するテキストがない場合、**Filter** はすべての行を返します。
   
    **Filter ( 'Project Requests', StartsWith ( Title, TextSearchBox1.Text )**

3. **If** 関数は、変数 **SortDescending1** の設定が true か false かをチェックします (アプリの並べ替えボタンで設定)。 その後、この関数は **Descending** または **Ascending** の値を返します。
   
    **If ( SortDescending1, Descending, Ascending )**

4. これで、**SortByColumns** 関数がギャラリーを並べ替えることができます。 ここでは**タイトル** フィールドを基に並べ替えられていますが、これを検索で使用するのとは別のフィールドにすることもできます。

ここまでお読みいただき、この数式の仕組みや、関数と他の要素を組み合わせて、アプリに必要な動作を制御する方法について理解を深めていただけると幸いです。 詳細については、「[Power Apps 向けの数式のリファレンス](formula-reference.md)」を参照してください。

## <a name="next-steps"></a>次の手順
このチュートリアル シリーズの次の手順では、[プロジェクトの承認を管理するフローを作成](sharepoint-scenario-approval-flow.md) します。

