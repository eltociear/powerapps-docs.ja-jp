---
title: SharePoint Online の Power Apps、Power Automate、および Power BI との統合のためのリスト設定 | Microsoft Docs
description: このタスクでは SharePoint リストを設定して、アプリ、フロー、レポート、およびダッシュボードのデータ ソースとして使用します。
author: NickWaggoner
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 12/19/2017
ms.author: niwaggon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c1b2e7dc4bb3f56983ddcdec39ecf7d37a283754
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2019
ms.locfileid: "3304061"
---
# <a name="set-up-lists-for-sharepoint-online-integration-with-power-apps-power-automate-and-power-bi"></a>SharePoint Online の Power Apps、Power Automate、および Power BI との統合のためのリスト設定
> [!NOTE]
> この記事は、Power Apps、Power Automate、および Power BI と SharePoint Online の使用に関するチュートリアル シリーズの一部です。 シリーズ全般に関することや、関連するファイルのダウンロードの詳細について、[シリーズの概要](sharepoint-scenario-intro.md) を必ずご覧ください。

SharePoint には共有やコラボレーションの機能が多数ありますが、このシナリオでは [SharePoint リスト](https://support.office.com/article/Introduction-to-lists-0A1C3ACE-DEF0-44AF-B225-CFA8D92C52D7) の機能に焦点を当てて説明します。 リストとは、チーム メンバーやその他のサイト ユーザーと共有できる単なるデータのコレクションです。 ここではこのシナリオに使用するリストについて説明しますので、ご使用の SharePoint Online サイトでリストを作成できるようになります。

## <a name="step-1-understand-the-lists"></a>手順 1: リストについて理解する
1 つ目のリストは、**プロジェクトの申請**です。このリストを使用して、プロジェクト申請者が申請を追加します。 その後、プロジェクト承認者が申請を確認し、承認または却下します。

| **リストの列** | **データの種類** | **メモ** |
| --- | --- | --- |
| タイトル |1 行テキスト |プロジェクト名に使用する既定の列 |
| 内容 |1 行テキスト | |
| ProjectType |1 行テキスト |値: 新規ハードウェア、アップグレードしたハードウェア、新規ソフトウェア、アップグレードしたソフトウェア |
| RequestDate |Date | |
| 申請者 |1 行テキスト | |
| EstimatedDays |番号 |申請者の見積とプロジェクト管理者の見積を、実際の値と比較できます |
| 承認済み |1 行テキスト |値: 保留中、はい、いいえ |

> [!NOTE]
> この他に **ID** 列も使用します。この列は SharePoint によって生成されますが、既定では非表示になっています。 ここでは簡単にするために基本的なデータ型を使用していますが、**申請者**列の**ユーザーまたはグループ**のように、実際のアプリでは複雑な型を使用する場合があります。 Power Apps でサポートされているデータ型については、「[Microsoft Power Apps から SharePoint への接続](connections/connection-sharepoint-online.md#known-issues)」をご覧ください。

2 つ目のリストは、**プロジェクトの詳細**です。承認されたすべてのプロジェクトに関する詳細 (割り当てられたプロジェクト管理者など) を追跡します。

| **リストの列** | **データの種類** | **メモ** |
| --- | --- | --- |
| タイトル |1 行テキスト |プロジェクト名に使用する既定の列 |
| RequestID |番号 |**プロジェクトの申請**リストの **ID** 列の値と一致します |
| ApprovedDate |Date | |
| ステータス |1 行テキスト |値: 開始前、進行中、完了 |
| ProjectedStartDate |Date |プロジェクト管理者の見積によるプロジェクト開始予定日 |
| ProjectedEndDate |Date |プロジェクト管理者の見積によるプロジェクト終了予定日 |
| ProjectedDays |番号 |作業日。通常は計算されますが、このシナリオでは計算しません |
| ActualDays |番号 |完了したプロジェクトに使用します |
| PMAssigned |1 行テキスト |プロジェクト マネージャー |

## <a name="step-2-create-and-review-the-lists"></a>手順 2: リストを作成してレビューする
シナリオを続けるには、前述の 2 つの SharePoint リストを作成し、これらのリストにサンプル データを入力する必要があります。 実際にリストを作成し、サンプル データをリストに貼り付けながら、この方法について説明します。 [ダウンロード パッケージ](https://aka.ms/o4ia0f) から Excel ファイルを取得していることを確認してください。

> [!NOTE]
> この手順では、Internet Explorer を使用します。

### <a name="create-the-lists"></a>リストを作成する

1. Internet Explorer でお使いの SharePoint サイトを開き、**新規**、**リスト** の順にクリックまたはタップします。
   
    ![新規 SharePoint リストを作成する](./media/sharepoint-scenario-setup/01-01-01-new-list.png)

2. 「プロジェクトの申請」という名前を入力し、**作成**をクリックまたはタップします。
   
    ![新しいリストの名前を指定する](./media/sharepoint-scenario-setup/01-01-02-create-list.png)
   
    既定の**タイトル** フィールドが表示された状態で**プロジェクトの申請**リストが作成されました。
   
    ![プロジェクトの申請リスト](./media/sharepoint-scenario-setup/01-01-03-initial-list.png)

### <a name="add-columns-to-the-list"></a>リストに列を追加する

1. ![新しいアイテムのアイコン](./media/sharepoint-scenario-setup/icon-new.png)、**1 行テキスト**の順にクリックまたはタップします。
   
    ![1 行テキスト フィールドの追加](./media/sharepoint-scenario-setup/01-01-04-add-column.png)

2. 「説明」という名前を入力し、**保存**をクリックまたはタップします。
   
3. 手順 **1.** および **2.** を、リストの別の列に対して繰り返します。
   
   1. **1 行テキスト** > "ProjectType"
   2. **日付** > "RequestDate"
   3. **1 行テキスト** > "Requestor"
   4. **数値** > "EstimatedDays"
   5. **1 行テキスト** > "Approved"

### <a name="copy-data-into-the-list"></a>データをリストにコピーする
1. **クイック編集**をクリックまたはタップします。
   
    ![リストのクイック編集](./media/sharepoint-scenario-setup/01-01-06-quick-edit.png)
2. グリッド内のセルを選択します。
   
    ![すべての列が表示されたリスト](./media/sharepoint-scenario-setup/01-01-07-empty-grid.png)
3. project-requests.xlsx ワークブックを開き、見出しを除くすべてのデータを選択します。
   
    ![プロジェクトの申請の Excel テーブル](./media/sharepoint-scenario-setup/01-01-08-excel-table.png)
4. データをコピーし、SharePoint のグリッドに貼り付けて、**完了**をクリックまたはタップします。
   
    ![データが入力された完成リスト](./media/sharepoint-scenario-setup/01-01-09-full-grid.png)
5. 「プロジェクトの詳細」リストでも、project-details.xlsx ワークブックを使用して、リストの作成とコピーのプロセスを繰り返します。 列の名前とデータ型については、「[手順 1: リストについて理解する](#step-1-understand-the-lists)」のプロジェクトの詳細テーブルをご覧ください。

## <a name="step-3-update-connections-to-samples---optional"></a>手順 3: サンプルへの接続を更新する - 省略可能
このチュートリアル シリーズの冒頭でお伝えしたように、[ダウンロード パッケージ](https://aka.ms/o4ia0f) には 2 つのサンプル アプリと 1 つのレポートが含まれています。 これらのサンプルを使用しなくてもこのシナリオは完了できますが、サンプルを使用する場合は、SharePoint リストへの接続を更新する必要があります。 接続を更新すると、Microsoft のリストではなく、 *お客様* のリストがデータ ソースとして使用されます。

### <a name="update-connections-for-the-sample-apps"></a>サンプル アプリの接続を更新する

1. [Power Apps Studio](https://create.powerapps.com/studio/) で、左側のウィンドウから**開く**をクリックまたはタップします。 

2. **参照**をクリックまたはタップし、ダウンロードした **project-management-app.msapp** ファイルを開きます。

3. **許可**をクリックまたはタップします。これにより、Power Apps で SharePoint を使用できるようになります。

4. リボンの**ビュー**タブで、**データ ソース**をクリックまたはタップします。

    ![Power Apps データ ソース](./media/sharepoint-scenario-setup/01-03-01-data-sources.png)
5. **データ** パネルで、**プロジェクトの詳細**の隣にある省略記号 (**. . .**) をクリックまたはタップし、**削除**をクリックまたはタップします。
   
    ![プロジェクトの詳細のデータ ソースの削除](./media/sharepoint-scenario-setup/01-03-02-remove.png)
6. **データ ソースの追加**をクリックまたはタップします。
   
    ![データ ソースの追加](./media/sharepoint-scenario-setup/01-03-03-add.png)

7. Power Apps で SharePoint への接続が既に確立されているか否かによりますが、リストに接続するための方法が 2 つ表示されます。 

    * SharePoint への接続が既に表示されている場合は、その接続をクリックまたはタップします。

        ![既存の接続](./media/sharepoint-scenario-setup/01-03-03aa-existing-connection.png)

    * SharePoint への接続が表示されていない場合は、**新しい接続**をクリックまたはタップします。

        ![新しいつながり](./media/sharepoint-scenario-setup/01-03-03a-new-connection.png)

        **SharePoint** をクリックまたはタップし、**作成**をクリックまたはタップします。
   
        ![SharePoint 接続](./media/sharepoint-scenario-setup/01-03-03b-sharepoint.png)

8. 作成したリストが含まれる SharePoint Online サイトの URL を入力し、**移動**をクリックまたはタップします。
   
    ![SharePoint URL](./media/sharepoint-scenario-setup/01-03-03c-sharepoint-url.png)
9. **プロジェクトの詳細**リストを選択し、**接続**をクリックまたはタップします。
   
    ![プロジェクトの詳細リスト](./media/sharepoint-scenario-setup/01-03-03d-project-details.png)
   
    **データ** パネルに、作成した接続が表示されます。
   
    ![データ ソース](./media/sharepoint-scenario-setup/01-03-03e-data-sources.png)

10. **プロジェクトの詳細**の隣にある省略記号 (**. . .**) をクリックまたはタップし、**更新**をクリックまたはタップします。
    
    ![プロジェクトの詳細のデータ ソースの更新](./media/sharepoint-scenario-setup/01-03-02-remove.png)

11. をクリックします。 ![アプリの実行アイコン](./media/sharepoint-scenario-setup/icon-run-arrow.png) を右上隅でクリックしてアプリを実行し、接続が正常に機能することを確認します。

12. **ファイル**をクリックまたはタップし、アプリをクラウドに保存します。 

12. **project-requests-app.msapp** でも**プロジェクトの申請**リストを使用して、このセクションの手順を繰り返します。

### <a name="update-connections-for-the-sample-report"></a>サンプル レポートの接続を更新する
1. Power BI Desktop で **project-analysis.pbix** を開きます。

2. リボンの**ホーム** タブで、**クエリを編集**、**データ ソース設定**の順にクリックまたはタップします。
   
    ![クエリを編集](./media/sharepoint-scenario-setup/01-03-04-edit-queries.png)

3. **ソースの変更**をクリックまたはタップします。
   
    ![データ ソースの設定](./media/sharepoint-scenario-setup/01-03-05-settings.png)

4. お使いの SharePoint Online のサイトの URL を入力し、**OK** の次に**閉じる**をクリックまたはタップします。
   
    ![SharePoint リストの URL](./media/sharepoint-scenario-setup/01-03-06-list-url.png)

5. Power BI Desktop のリボンの下にバナーが表示されます。このバナーで変更を適用して新しいソースからデータを取り込むことができます。 **変更の適用**をクリックまたはタップします。
   
    ![クエリの変更を適用](./media/sharepoint-scenario-setup/01-03-07-apply.png)

6. Microsoft アカウント (SharePoint Online にアクセスするときに使用するアカウント) でサインインし、**接続**をクリックまたはタップします。
   
    ![SharePoint Online への接続](./media/sharepoint-scenario-setup/01-03-08-connect.png)

## <a name="next-steps"></a>次の手順
このチュートリアル シリーズの次の手順では、[プロジェクト申請を処理するアプリを生成](sharepoint-scenario-generate-app.md) します。

