---
title: 危機管理コミュニケーション アプリ - サンプル テンプレート | Microsoft Docs
description: Power Apps での危機管理コミュニケーションのサンプル テンプレートについて説明します。
author: matthewbolanos
manager: kvivek
ms.service: powerapps
ms.topic: sample
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/27/2020
ms.author: mabolan
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e5f905b546b23fce329f686ed56ff460f76e56b6
ms.sourcegitcommit: c0b694f53af1cd35dce135be9e4e0924ac35608d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2020
ms.locfileid: "3352264"
---
# <a name="set-up-and-learn-about-the-crisis-communication-sample-template-in-power-apps"></a>Power Apps での危機管理コミュニケーションのサンプル テンプレートおよびその設定方法について

危機管理コミュニケーション アプリは、ユーザーと危機に関する情報を接続する使いやすいエクスペリエンスを提供します。 会社の内部ニュースの更新をすやばく取得し、よくある質問の回答を確認し、リンクや緊急連絡先などの重要な情報にアクセスできるようになります。 このアプリをお使いの環境に合わせるには、少しの設定が必要です。

このチュートリアルでは、次の方法を学習します。

- データの場所の作成。
- 危機管理コミュニケーション アプリおよびその管理アプリの両方をインポートします。
- アプリのコンテンツを作成します。
- フローをインポートして、ユーザーに通知を送信します。
- 一元管理された Teams チームを作成してデータを集約し、効果的に問題に対応します。

これらの手順を完了するための推定時間: **20&ndash;25 分**。

> [!NOTE]
> 危機管理コミュニケーション サンプル テンプレートは、Power Apps US Government および Power Automate US Government プランでも利用可能です。 Power Apps および Power Automate US Government バージョンのサービス URL は、市販製品版とは異なります。 詳細については、[Power Apps US Government サービス URL](https://docs.microsoft.com/power-platform/admin/powerapps-us-government#power-apps-us-government-service-urls) および [Power Automate US Government サービス URL](https://docs.microsoft.com/power-automate/us-govt#power-automate-us-government-service-urls) を参照してください。

## <a name="demo-crisis-communication-app"></a>危機管理コミュニケーション アプリのデモ

危機管理コミュニケーション ソリューションの使用方法をご覧ください。

> [!VIDEO https://www.youtube.com/embed/23SypLXiOTw]

## <a name="prerequisites"></a>前提条件

- [サインアップ](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) for Power Apps.
- 有効な SharePoint Online ライセンスと、リストを作成するアクセス許可を持っている必要があります。
- アプリのデータを保存できる公開 SharePoint サイトがを持っている必要があります。
- [aka.ms/CrisisCommunicationSolution](https://aka.ms/CrisisCommunicationSolution) から資産をダウンロードします。

> [!IMPORTANT]
> 危機管理コミュニケーション アプリに関するフィードバックや問題については、次のリンクを使用してください。
> - **[フィードバック](https://aka.ms/crisis-communication-feedback)**
> - **[問題](https://aka.ms/crisis-communication-issues)**

## <a name="demo-build-and-deploy-the-crisis-communication-app"></a>デモ: 危機管理コミュニケーション アプリのビルドおよび展開

危機管理コミュニケーション アプリのビルドおよび展開方法をご覧ください。

> [!VIDEO https://www.youtube.com/embed/Wykrwf9dZ-Y]

## <a name="create-a-home-for-your-data"></a>データのホームの作成

アプリのデータは SharePoint リストに保存されるので、最初のステップは、SharePoint の新しいサイトを作成することです。

### <a name="create-a-sharepoint-site"></a>SharePoint サイトの作成

1. [Office Online](https://www.office.com) にサインインし、**SharePoint** を選択します。
1. **サイトの作成**を選択します。

    ![SharePoint サイトのサンプル](media/sample-crisis-communication-app/01-Create-Site.png)

1. **チームのサイト**を選択します。

    ![チーム サイト](media/sample-crisis-communication-app/02-Team-Site.png)

1. サイトの名前と説明を入力します。
1. **プライバシー設定**を**公開**に設定し、会社の全員が必要な情報を入手できるようにします。

    ![サイト設定](media/sample-crisis-communication-app/03-Privacy-Settings.png)

1. **次へ** を選択します。
1. サイトの所有者を追加します (オプション)。
1. **完了** を選択します。

### <a name="create-sharepoint-lists-for-the-app"></a>アプリの SharePoint リストの作成

アプリは複数のリストを使用してデータを保存します。 ダウンロードした [資産パッケージ](#prerequisites) から利用可能な DeploySPLists フローを使用し、これらのリストを自動的に作成することができます。

#### <a name="import-the-sharepoint-list-deployment-flow"></a>SharePoint リスト展開フローのインポート

1. [flow.microsoft.com](https://flow.microsoft.com) に移動します。
1. 左側のナビゲーション ウィンドウで**マイ フロー**を選択します。
1. コマンド バーの **インポート** を選択します。
1. GitHub リポジトリから **DeploySPLists.zip** をアップロードします。

    ![パッケージのインポート](media/sample-crisis-communication-app/import-package.png)

1. 新しいフローに対する SharePoint 接続を追加するには、**インポート時に選択する**のリンクを選択し、フォームに入力します。

    ![インポート設定](media/sample-crisis-communication-app/import-settings.png)

1. 新しい SharePoint 接続を作成する必要がある場合、**インポート設定**ウィンドウの**新規作成**を選択します。
1. コマンド バーで、**新しい接続**を選択します。

    ![新しいつながりの作成](media/sample-crisis-communication-app/create-connection.png)

1. たとえば、*SharePoint* など、接続の名前を検索します。
1. 作成した接続を選択します。
1. **保存**を選択します。
1. **インポート** を選択します。

#### <a name="edit-the-sharepoint-list-deployment-flow"></a>SharePoint リスト展開フローの編集

1. インポートが完了した後、**マイ フロー**に移動してフローのリストを更新します。
1. 新しくインポートしたフロー **DeploySPLists** を選択します。
1. コマンド バーで、**編集**を選択します。
1. **Variable – Target Site for Lists** のカードを開きます。
1. **Value** に対して、SharePoint サイトの名前を入力します。
1. **Variable – App name** カードを開きます。
1. **Value** にアプリの名前を入力します。既定では、名前は**危機コミュニケーション**になります。

    ![フロー パラメーター](media/sample-crisis-communication-app/04-Flow-Settings.png)

1. **保存**を選択します。

#### <a name="run-the-sharepoint-list-deployment-flow"></a>SharePoint リスト展開フローの実行

1. **DeploySPLists** フローの詳細画面に戻ります。
1. コマンド バーで、**実行**を選択します。
1. **続行**を選択し、**フローの実行**を選択します。

    ![サインインし、フローを実行する](media/sample-crisis-communication-app/sign-in-flow.png)

    ![フローを実行する](media/sample-crisis-communication-app/run-flow.png)

> [!NOTE]
> 位置サービスが必要であることを示すエラーを受け取る場合があります。
これが発生した場合、位置情報サービスに Power Automate のアクセスを許可し、再度試行する前にページを更新してください。

SharePoint サイトで、フローは次の SharePoint リストを作成します。

| **表示タイトル**| **目的** | **説明** |
|-|-|-|
| CI_LogosAssets| アプリから参照されるロゴやその他の画像を保持します。 ロゴは、直接リンクまたは使用するロゴの ID 番号を介して Power Apps で参照されます。 | *[アプリ名]* アプリの関連するロゴやその他の画像資産のライブラリ。 |
| CI_configAdminSetup | アプリ管理者による機能設定に使用されます。<br>**注意:** このリストは、管理者ではないすべてのメンバーに対して読み取り専用である必要があります。 | *[アプリ名]* アプリの管理構成リスト。
| CI_Contacts | 既定の連絡先コンテンツ タイプを使用し、連絡先に関する情報を取得します。 (ユーザー選択ツールは含まれていないため、データが最新であることを確認するには、このリストを手動で維持する必要があります。)<br>**注意**: これは、リストの既定のコンテンツ タイプであるグローバル連絡先リストのタイプに依存します。 | *[アプリ名]* アプリの連絡先リスト。|
| CI_CompanyNews | **会社のニュース** アイテムのコレクション。 | *[アプリ名]* アプリに表示されるニュース項目を管理するためのリスト。 **廃止**列を使用し、レコードとして保持しながら、アプリ ビューからニュース項目を削除することができます。 | 
| CI_FAQ  | よく寄せられる質問。 | *[アプリ名]* アプリについて、よくある質問のリスト。 **廃止**列を使用し、レコードとして保持しながら、アプリ ビューから FAQ 項目を削除することができます。 |
| CI_UsefulLinks | 役に立つハイパーリンクのリスト。 | *[アプリ名]* アプリについて、役立つハイパーリンクのリスト。 **廃止**列を使用し、レコードとして保持しながら、アプリ ビューからハイパーリンク項目を削除することができます。 |
| CI_Employee | 現在の従業員のプレゼンス状態を追跡します。 たとえば、**在宅勤務**、**病欠**、**不在**、および**休暇**などです。  **注意**: ステータス**仕事に来る**と見なされ、リスト オプションには含まれません。 | *[アプリ名]* アプリの従業員のプレゼンス ステータスを示すメッセージのリスト。 **廃止**列を使用し、レコードとして保持しながら、アプリ ビューからステータス メッセージを削除することができます。 |
| CI_HelpfulTips             | ユーザーが仲間に貢献できる役立つヒント。 | *[アプリ名]* アプリの共有ヒントの管理リスト。 **廃止**列を使用し、レコードとして保持しながら、アプリ ビューからヒントを削除することができます。  |

> [!NOTE]
> - これらすべてのリスト列は、依存関係にある見なす必要があります。
    誤操作によるスキーマの変更からリストを保護します (たとえば、新しい列の追加は許可されているが、列を削除するとアプリが破損するなど。)
> - リスト項目を削除するときは注意が必要です。リスト項目の削除により、履歴レコードが削除されます。 廃止の値を**いいえ**から**はい**に切り替え、連絡先、ニュース、FAQ、またはリンクからレコードを削除します。

## <a name="import-and-set-up-the-crisis-communication-app"></a>危機管理コミュニケーション アプリのインポートおよびセットアップ

すべての SharePoint リストが作成された後、アプリをインポートして新しいデータ ソースに接続することができます。

> [!NOTE]
> 管理者アプリを使いたくない場合、SharePoint リストを手動で編集してこれら同じプロパティを編集できます。

### <a name="import-the-app"></a>アプリをインポートする

1. [Power Apps](https://make.powerapps.com) にサインインします。
1. 左側のナビゲーション ウィンドウから、**アプリ**を選択します。
1. コマンド バーの **インポート** を選択します。
1. GitHub リポジトリから **CrisisCommunication.zip** ファイルをアップロードします。

    > [!NOTE]
    > テナントが GCC 環境にある場合、**CrisisCommunicationGCC.zip** をアップロードします。

    ![アプリのパッケージをインポートする](media/sample-crisis-communication-app/31-Import-App.png)

1. **インポート時に選択**ハイパーリンクを使用して適切な接続を選択することにより、**Microsoft Teams 接続**および **Office 365 ユーザー接続**のインポート設定を完了します。ユーザー接続を使用して適切な接続を選択するインポート時に選択ハイパーリンク。 まだ存在していない場合、[新しい接続](add-data-connection.md) を作成する必要があるかもしれません。
1. **インポート** を選択します。

### <a name="update-the-sharepoint-connections"></a>SharePoint 接続を更新する

1. **アプリ** リストに戻る。
1. **危機管理コミュニケーション** アプリの**その他のコマンド** (...) を選択します。
1. コンテキスト メニューから**編集**を選択します。

    ![アプリの編集](media/sample-crisis-communication-app/05-Edit-App.png)

1. サインインするか、または必要な接続を作成してから、**許可**を選択します。

1. 左側のウィンドウのデータ ソースに移動します。

    ![データ ソース](media/sample-crisis-communication-app/data-sources.png)

1. 現在の SharePoint をポイントしていないので、アプリ内の既存の SharePoint リストを削除します。

    ![データ ソースの削除](media/sample-crisis-communication-app/remove-data-source.png)

1. 自分の SharePoint サイトからリストを追加します。 検索バーで **SharePoint** を検索します。

    ![SharePoint の検索](media/sample-crisis-communication-app/sharepoint.png)

1. **SharePoint**を選択し、接続を選択します。

    ![SharePoint 接続](media/sample-crisis-communication-app/sharepoint-connection.png)

1. URL をコピーし、テキスト フィールドの SharePoint サイトに貼り付け、**接続**を選択します。

    ![SharePoint サイトの URL](media/sample-crisis-communication-app/site-url.png)

1. すべての SharePoint リストおよびライブラリを選択し、**接続**を選択します。

    ![SharePoint リストに接続する](media/sample-crisis-communication-app/sharepoint-lists.png)

1. **保存** を選び、そして **公開** を選択します。

### <a name="optional-enable-location-updates"></a>オプション: 位置の更新を有効にする

このアプリにより、ユーザーが状態を設定するたびに、ユーザーの位置を記録し、SharePoint サイトに保存できるようになります。 危機管理チームは、Power BI レポートでこのデータを確認できます。

> [!NOTE]
> 位置の更新の有効化はオプションです。 ユーザーの位置を追跡しない場合、このセクションをスキップできます。 また、現在、位置の追跡は Teams デスクトップではサポートされていません。

**位置の更新を有効にする**

1. **btnDateRange** コントロールを検索します。
1. 数式バーの **btnDateRange** コントロールの **OnSelect** プロパティを開きます。
1. 数式バーの次のスニペットをコピーし、**OnSelect** プロパティに貼り付けます。

    > [!NOTE]
    > 次のスニペットは、2020 年 3 月 16 日より古いバージョンのソリューションで動作することを目的としています。 新しいバージョンでは、*// To implement location* コメントの後でコードを編集します。


    ```
        UpdateContext({locSaveDates: true});
    // Store the output properties of the calendar in static variables and collections.
    ClearCollect(submittedDates,Sort(Filter(selectedDates,ComponentId=CalendarComponent.Id),Date,Ascending));
    Set(varStartDate,First(submittedDates).Date);
    Set(varEndDate,First(Sort(submittedDates,Date,Descending)).Date);
    // Create a new record for work status for each date selected in the date range.
    ForAll(
        Filter(
            RenameColumns(submittedDates,"Date","DisplayDate"),
            ComponentId=CalendarComponent.Id,
            !(DisplayDate in colDates.Date)
        ),
        Patch('CI_Employee Status',Defaults('CI_Employee Status'),
            {
                Title: varUser.userPrincipalName,
                Date: DisplayDate,
                Notes: "",
                PresenceStatus: LookUp(colWorkStatus,Value=WorkStatusComponent.Selected.Value)
                
                // To implement location, add a comma to the line above and uncomment the lines below for latitude and longitude.
                // Latitude: Text(Location.Latitude),
                // Longitude: Text(Location.Longitude)
            }
        )
    );
        // Update existing dates with the new status.
        ForAll(
            AddColumns(
                Filter(
                    RenameColumns(submittedDates,"Date","DisplayDate"),
                    ComponentId=CalendarComponent.Id,
                    DisplayDate in colDates.Date
                ),
                
                // Get the current record for each existing date.
                "LookUpId",LookUp(RenameColumns(colDates,"ID","DateId"),And(Title=varUser.userPrincipalName,Date=DisplayDate)).DateId
            ),
            Patch('CI_Employee Status',LookUp('CI_Employee Status',ID=LookUpId),
                {
                    PresenceStatus: LookUp(colWorkStatus,Value=WorkStatusComponent.Selected.Value)
                }
            )
        );
        If(
            IsEmpty(Errors('CI_Employee Status')),
            
            // Update the list of work status for the logged-in user.
            ClearCollect(colDates,Filter('CI_Employee Status',Title=varUser.userPrincipalName));
            // Send an email receipt to the logged-in user.
            UpdateContext(
                {
                    locReceiptSuccess: 
                    Office365Outlook.SendEmailV2(
                        // To: send an email to oneself
                        varUser.mail,
                        // Subject
                        Proper(WorkStatusComponent.Selected.Value) & ": " & varStartDate & If(varStartDate<>varEndDate," - " & varEndDate),
                        // Body
                        WorkStatusComponent.Selected.DateRangeReceipt & ": " &
                        // Create a bulleted list of dates
                        "<ul>" & 
                            Concat(submittedDates,"<li>" & Date & Char(10)) &
                        "</ul>"
                    )
                }
            );
            If(
                locReceiptSuccess,
                Notify("You successfully submitted your work status. An email has been sent to you with a summary.",NotificationType.Success,3000),
                Notify("There was an error sending an email summary, but you successfully submitted your work status.",NotificationType.Success,3000);
            );
            
            Navigate('Share to Team Screen',LookUp(colStyles,Key="navigation_transition").Value),
            
            // Case: Error submitting work status
            Notify(varString.WorkStatusError,NotificationType.Warning)
        );
        UpdateContext({locSaveDates: false})
    ```

### <a name="optional-add-additional-work-status-messages"></a>オプション: 追加の作業ステータス メッセージを追加します

**自宅勤務**および**外出中**以外に、作業ステータス メッセージをさらに追加したい場合、次の手順を完了します。 始めるには、SharePoint サイトを更新する必要があります。

1. SharePoint サイトに戻り、**サイト コンテンツ**を選択します。
1. **CI_Employee Status** を選択します。
1. **PresenceStatus** 列が存在しない場合、**列の追加**を選択してください。
1. **列の表示/非表示**を選択します。

    ![列の表示/非表示](media/sample-crisis-communication-app/36-hide-show-columns.png)

1. **PresenceStatus** を選択します。
1. **適用**を選択します。
1. **PresenceStatus** 列を選択します。

    ![PresenceStatus 列を選択します](media/sample-crisis-communication-app/37-show-presence.png)

1. **列の設定**を選択し、**編集**を選択します。

    ![PresenceStatus 列の編集](media/sample-crisis-communication-app/38-edit-column.png)

1. **Choices** フィールドで追加の作業ステータス メッセージを追加します。

> [!NOTE]
> 新しい選択肢の名前を記録し、後続のステップで使用できるようにします。

アプリ自体にいくつかの調整を行って、新しい作業ステータス メッセージが表示されるようにする必要があります。

1. Power Apps Studio でアプリを開く<!--edit okay?-->。
1. **作業状態**の画面を選択します。
1. 数式バーに **OnVisible** 関数を設定します。

    ![プレゼンスを表示する](media/sample-crisis-communication-app/39-onvisible-for-screen.png)

1. 次のテンプレートを編集し、値を固有のものに置き換えます。

    ```
        ,"<Name of option in SharePoint list; case sensitive>",
        Table(
            {
                Icon: <Image file>,
                DateRangeQuestion: "Select the dates you'll be <Name of status>.",
                DateRangeReceipt: "You're currently <Name of status>.",
                ShareToTeamEmail: "I'll be <Name of status> on these dates",
                AutoReplyMessage: "I'll be <Name of status> on these dates"
            }
        )
    ```

1. `/* TEMPLATE FOR ADDITIONAL WORK STATUS OPTIONS */` 文字列をテンプレートに置き換えます。
1. **保存** を選び、そして **公開** を選択します。

### <a name="update-the-request-for-help-flow"></a>ヘルプ フローの Request の更新

このフローは、アダプティブ カードを中心的な Teams チームに送信し、ヘルプを要求します。

![ヘルプの要求](media/sample-crisis-communication-app/21-Request-Help.png)

次の手順を完了する前に、Teams で危機管理チームを作成します。 チームを作成した後、ID を取得してフローに取り込むことができます。 Teams チームの作成に関する詳細: [中央危機管理の Teams チームの作成](#create-a-central-crisis-management-teams-team)

1. すべてのヘルプ要求を投稿する Teams チャネルに移動します。
1. チャネルの**その他のオプション** (...) を選択します。
1. **チャンネルのリンクの取得**を選択します。

    ![チャンネルのリンクの取得](media/sample-crisis-communication-app/17-Get-link-to-channel.png)

1. リンクをコピーして、テキスト エディターに貼り付けます。

    ![チーム リンクのコピー](media/sample-crisis-communication-app/18-Copy-link.png)

1. `groupId=` から `&tenantId=` までのすべての、**チーム ID** を抽出します。 <br> たとえば、次の URL において、グループ ID は下記のとおり <br>`8bc7c0c2-0d4c-4fb8-af99-32da74c9237b`
   
   `https://teams.microsoft.com/l/channel/19%3ab2fa9fc20f3042a9b63fc5890e1813f8%40thread.tacv2/General?groupId=8bc7c0c2-0d4c-4fb8-af99-32da74c9237b&tenantId=72f988bf-86f1-41af-91ab-2d7cd011db47`
   
1. `https://teams.microsoft.com/l/channel/` から `/General` までのすべての、**チャネル ID** を抽出します。 <br> たとえば、次の URL において、チャネル ID は下記のとおり<br> `19%3ab2fa9fc20f3042a9b63fc5890e1813f8%40thread.tacv2`
   
   `https://teams.microsoft.com/l/channel/19%3ab2fa9fc20f3042a9b63fc5890e1813f8%40thread.tacv2/General?groupId=8bc7c0c2-0d4c-4fb8-af99-32da74c9237b&tenantId=72f988bf-86f1-41af-91ab-2d7cd011db47`、

1. [flow.microsoft.com](https://flow.microsoft.com) に移動します。

1. 左側のナビゲーション ウィンドウで**マイ フロー**を選択します。

1. **CrisisCommunication.Request** の**その他のコマンド** (...) を選択し、**編集**を選択します。

    ![ヘルプ フローの Request の編集](media/sample-crisis-communication-app/20-Edit-Flow.png)

1. **チーム ID** カードを開きます。

1. チーム ID を**Value** フィールドに貼り付けます。

1. **チャネル ID** カードを開きます。

1. チャネル ID を**Value** フィールドに貼り付けます。

    ![チームおよびチャネル ID の設定](media/sample-crisis-communication-app/22-Set-Team-IDs.png)

1. **時間の読み取り**アクションまで下方向へスクロールし、指定したソースおよび送信先の時間を使用することにより**タイム ゾーンの変換**アクションを更新します。

    ![タイム ゾーン変換の設定](media/sample-crisis-communication-app/convert-time-zone.png)

## <a name="optional-configure-a-shared-inbox"></a>オプション: 共有受信トレイを構成する<a name="optional-configure-shared-inbox"></a>

CrisisCommunication.Request フローは、Teams に送信する前に受信トレイから要求を取得します。 要求電子メールを共有受信トレイに送信する場合は、次の手順に従ってください。

> [!NOTE]
> 共有受信トレイに要求電子メールを送信しない場合は、このセクションをスキップできます。

1. **CrisisCommunication.Request** フローを編集モードで開きます。
1. **電子メールを受信したとき V3** から**その他のコマンド** (...) を選択します。
1. **削除**を選択します。

     ![コネクタの削除](media/sample-crisis-communication-app/33-delete-connector.png)

1. **共有受信トレイが新しい電子メールを受信したとき (V2)** を検索し、選択します。
1. **メールボックスアドレス**に共有受信トレイのアドレスを入力してください。
1. **コメント** カードを開きます。
1. **Value** に**動的な値の追加**を選択します。
1. **本文**を検索し、選択します。

     ![本文を選択します](media/sample-crisis-communication-app/35-body.png)

1. **ユーザー プロファイル カードの取得 (V2)** カードを開きます。
1. **動的な値の追加**を選択します。
1. **フォーム**を検索し、選択します。

     ![フォームの選択](media/sample-crisis-communication-app/34-from.png)

## <a name="import-and-set-up-the-admin-app"></a>管理者アプリのインポートおよびセットアップ

インポートしたアプリを管理するには、管理者アプリに対して同じ手順を繰り返します。

1. [Power Apps](https://make.powerapps.com) にサインインします。
1. 左側のナビゲーション ウィンドウから、**アプリ**を選択します。
1. コマンド バーの **インポート** を選択します。
1. GitHub リポジトリから **CrisisCommunicationAdmin.zip** ファイルをアップロードします。

    ![管理者アプリのパッケージをインポートする](media/sample-crisis-communication-app/import-app.png)

1. **インポート** を選択します。

### <a name="update-sharepoint-connections-for-the-admin-app"></a>管理者アプリの SharePoint 接続を更新する

1. **アプリ** リストに戻る。
1. **危機管理コミュニケーションの管理者アプリ**の**その他のコマンド** (...) を選択します。
1. コンテキスト メニューから**編集**を選択します。

    ![管理者アプリの編集](media/sample-crisis-communication-app/08-Edit-Admin-App.png)

1. サインインするか、または必要な接続を作成してから、**許可**を選択します。

1. 左側のウィンドウのデータ ソースに移動します。

    ![データ ソース](media/sample-crisis-communication-app/data-sources.png)

1. 現在の SharePoint をポイントしていないので、アプリ内の既存の SharePoint リストを削除します。

    ![データ ソースの削除](media/sample-crisis-communication-app/remove-data-source.png)

1. 自分の SharePoint サイトからリストを追加します。 検索バーで **SharePoint** を検索します。

    ![SharePoint の検索](media/sample-crisis-communication-app/sharepoint.png)

1. **SharePoint**を選択し、接続を選択します。

    ![SharePoint 接続](media/sample-crisis-communication-app/sharepoint-connection.png)

1. URL をコピーし、テキスト フィールドの SharePoint サイトに貼り付け、**接続**を選択します。

    ![SharePoint サイトの URL](media/sample-crisis-communication-app/site-url.png)

1. すべての SharePoint リストおよびライブラリを選択し、**接続**を選択します。

    ![SharePoint リストに接続する](media/sample-crisis-communication-app/sharepoint-lists.png)

1. **保存** を選び、そして **公開** を選択します。

## <a name="create-initial-content-for-the-app"></a>アプリの初期コンテンツの作成

この時点で、危機管理コミュニケーション アプリおよびその管理者アプリの両方が正常にインポートされました。 初期コンテンツの作成を開始することができます。 開始するには、危機管理コミュニケーション管理者アプリを開きます。

GCC 環境がある場合、GCC モードを有効にする必要があります。 詳細: [GCC 環境のモバイル クライアントの構成方法](https://docs.microsoft.com/power-platform/admin/powerapps-us-government#configure-mobile-clients)。

![危機管理コミュニケーション 管理者アプリのデモ](media/sample-crisis-communication-app/09-Admin-App.png)

管理者アプリを使用して、危機管理コミュニケーション アプリのすべての情報をカスタマイズし、付属のフローの主要な設定を構成します。

> [!NOTE]
> アラーム&mdash;として管理者アプリを使いたくない場合、SharePoint リストを手動で編集してこれらのプロパティを編集できます。

### <a name="set-up-key-parameters-under-admin-settings"></a>管理設定の下で主要なパラメーターを設定する

アプリを初期化するには、**管理設定**に移動し、すべての必須フィールドを指定する必要があります。

次の表に示すようにすべてのフィールドを指定し、**保存**を選択します。

| **フィールド名** | **SharePoint の論理名** | **目的** | **例** |
|-|-|-|-|
| 管理者電子メール | AdminContactEmail | ここに電子メール要求が送信されます。 ユーザーの電子メール アドレスに設定する必要があります。 別の受信トレイに通知を送信する場合、この記事で既に説明した [オプションの共有受信トレイの設定](#optional-configure-shared-inbox) を参照してください。 | admin@contoso.com |
| ロゴ URL | ロゴ | 左上隅に表示されるアプリのロゴ。 | https://contoso.com/logo.png |
| AAD グループ ID | AADGroupID | **新しい危機管理コミュニケーション ニュースについてユーザーに通知**フローを介して、会社内部の更新についてユーザーに通知を送信するために使用されます。 以下の手順に従って、グループの Azure Active Directory (Azure AD) ID を取得します。 | c0ddf873-b4fe-4602-b3a9-502dd944c8d5 |
| アプリの URL | AppURL | ユーザー アプリの場所により、**新しい危機管理コミュニケーション ニュースについてユーザーに通知** フローは、**詳細**を選択した後にユーザーにリダイレクトされます。 | https://apps.preview.powerapps.com/play/<app URL>?tenantId=<tenant ID>
| Government RSS フィード | GovernmentRSSFeed | アプリで世界のニュース機能を設定するために使用されます。 信頼できるソースから従業員に追加情報を提供する場合に役立ちます。 | https://www.who.int/rss-feeds/news-english.xml |
| 通知メソッド | PreferredSentNotification | **新しい危機管理コミュニケーション ニュースについてユーザーに通知** フローにより使用され、通知を送信するときに使用する必要がある配布チャネルが決定されます。 これは必須フィールドです。 | 電子メール、Teams 通知、プッシュ通知 |
| 機能フラグ | Feature1...8 | アプリケーションの各機能を無効化または有効化にするために使用されます。 |  |

> [!NOTE]
> Teams 通知およびプッシュ通知は、現在 GCC ではサポートされていません。


#### <a name="finding-the-azure-ad-id-for-your-distribution-group"></a>配布グループの Azure AD ID を検索する

1. [aad.portal.azure.com](https://aad.portal.azure.com) に移動します。
1. 左側のナビゲーション ウィンドウから **Azure Active Directory** を選択します。
1. **グループ**を選択します。
1. 配布グループを検索し、選択します。
1. **オブジェクト ID** フィールドをコピーします。

    ![Azure AD ID を取得する](media/sample-crisis-communication-app/11-AAD-Group-ID.png)

1. ID を管理アプリの **AAD グループ ID** フィールドにコピーします。

### <a name="set-up-emergency-contacts"></a>緊急連絡先を設定する

1. **会社の連絡先**に移動します。
1. **新しい連絡先の作成**を選択します。
1. 連絡先の詳細を使用してフォームに入力します。

*リスト スキーマ:*

| **フィールド名** | **SharePoint の論理名** | **目的** |
|-|-|-|
| 氏名 | Fullname | 連絡先の名前。 |
| 電子メール | 電子メール | 連絡先に表示されている電子メール アドレス。 |
| 国 | 国 | 連絡先の国/地域。 このフィールドは、連絡先をグループ化するために使用されます。国/地域が有効でない場合、その他の値を使用して連絡先をグループ化できます。 |
| コメント | コメント | この連絡先に連絡するタイミングを説明するのに役立つ、連絡先に関する追加情報を表示します。 |
| 廃止 | 廃止 | 既存の緊急連絡先を非表示にするために使用します。 |

### <a name="set-up-initial-company-news"></a>初期の会社ニュースを設定する

1. **会社のニュース**に移動します。
1. **新しい投稿の作成**を選択します。
1. フォームに入力します。

*リスト スキーマ:*

| **フィールド名** | **SharePoint の論理名** | **目的** |
|-|-|-|
| タイトル | タイトル | 更新のタイトル。 |
| 詳細 | 詳細 | フル更新。 このフィールドでは HTML を使用できます。 |
| 推薦文 | Blurb | 更新に関する短いメッセージ。 これは**新しい危機管理コミュニケーション ニュースについてユーザーに通知**フローおよび更新のギャラリーで使用されます。 |
| 廃止 | 廃止 | 既存の投稿を非表示にするために使用します。 |

### <a name="set-up-helpful-tips"></a>役に立つヒントの設定

1. **役に立つヒント**に移動します。
1. **新しいヒント**を選択します。
1. フォームに入力します。

*リスト スキーマ:*

| **フィールド名** | **SharePoint の論理名** | **目的** |
|-|-|-|
| タイトル | タイトル | 役に立つヒントのタイトル。 |
| リソース URL | ResourceURL | 追加の読み物へのリンク。 (任意) |
| サブタイトル | SubTitle | ヒントのサブタイトル。 (任意) |
| 内容 | 内容 | 役に立つヒントの完全な説明。 |
| 廃止 | 廃止 | 役立つヒントを非表示にするために使用します。 |

### <a name="set-up-links"></a>リンクの設定

1. **リンク**に移動します。
1. **新しいリンクの作成**を選択します。
1. フォームに入力します。

*リスト スキーマ:*

| **フィールド名** | **SharePoint の論理名** | **目的** |
|-|-|-|
| タイトル | タイトル | リンクのテキスト。 |
| URL | URL | リンクの URL。 |
| 内容 | 内容 | チームに関する追加の詳細。 (任意) |
| 廃止 | 廃止 | リンクを非表示にするために使用します。 |

### <a name="set-up-faqs"></a>FAQ の設定

1. **FAQ** に移動します。
1. **新しい FAQ の作成**を選択します。
1. フォームに入力します。

*リスト スキーマ:*

| **フィールド名** | **SharePoint の論理名** | **目的** |
|-|-|-|
| タイトル | タイトル | FAQ の質問。 |
| 順位 | 順位 | FAQ の質問の順序。 |
| 応答 | 応答 | FAQ の質問に対する答え。 |
| 廃止 | 廃止 | FAQ の質問を非表示にするために使用します。 |

## <a name="test-and-share-the-app"></a>アプリのテストおよび共有

すべてのデータが正常に設定されたので、アプリをテストして、動作を確認することができます。

1. [Power Apps](https://make.powerapps.com) にサインインします。
2. 左側のナビゲーション ウィンドウから、**アプリ**を選択します。
3. **危機管理コミュニケーション**を選択して、アプリを再生します。

アプリのテストが成功した後、会社の全員に共有できます。

## <a name="import-and-set-up-the-notification-flow"></a>通知フローのインポートおよびセットアップ

アプリはフローを使用して、会社の新しい更新があるたびにエンド ユーザーに通知を送信します。

### <a name="import-the-news-notification-flow"></a>ニュース通知フローのインポート

1. [flow.microsoft.com](https://flow.microsoft.com) に移動します。
1. 左側のナビゲーション ウィンドウで**マイ フロー**を選択します。
1. コマンド バーの **インポート** を選択します。
1. GitHub リポジトリから **CrisisCommunicationNewsNotification.zip** をアップロードします。

    > [!NOTE]
    > テナントが GCC 環境にある場合、**CrisisCommunicationNewsNotificationGCC.zip** をアップロードします。

    ![CrisisCommunicationNewsNotification.zip のアップロード](media/sample-crisis-communication-app/upload-news-notification.png)

1. 新しいフローに対する接続を追加するには、各接続について**インポート時に選択する**のリンクを選択し、フォームに入力します。

    ![インポート時に選択する](media/sample-crisis-communication-app/select-during-import.png)

1. 新しい接続を作成する必要がある場合、**インポート設定**ウィンドウの**新規作成**を選択します。
1. コマンド バーで、**新しい接続**を選択します。

    ![新しいつながりの作成](media/sample-crisis-communication-app/create-connection.png)

1. たとえば、**PowerApps** 通知 (プレビュー) など、接続の名前を検索します。

    ![接続名の例](media/sample-crisis-communication-app/notifications.png)

1. 対象の接続を選択します。
1. **PowerApps 通知 (プレビュー)** への接続を作成している場合、次の画像に示すようなダイアログ ボックスが表示されます。

    ![通知 ダイアログ ボックス](media/sample-crisis-communication-app/notifications-dialog.png)

1. ID を取得するには、**アプリ** リストに移動します。
1. **危機管理コミュニケーション** アプリの**その他のコマンド** (...) を選択し、**詳細**を選択します。

    ![接続の詳細](media/sample-crisis-communication-app/06-App-Details.png)

1. **アプリ ID** をコピーします。

    ![アプリ ID](media/sample-crisis-communication-app/07-App-ID.png)

1. アプリ ID を接続作成ダイアログ ボックスに貼り付けて、**作成**を選択します。

    ![つながりの作成](media/sample-crisis-communication-app/target-app-id.png)

1. 新しい接続を作成した後、**インポート設定**ウィンドウを選択し、**リストの更新**を選択します。
1. 新しい接続が表示されます。 選択してから、**保存**​​を選択します。
1. すべての接続の追加が完了した後、**インポート**を選択します。

    ![接続のインポート](media/sample-crisis-communication-app/imported-connections.png)

### <a name="edit-the-news-notification-flow"></a>ニュース通知フローの編集

1. インポートが完了した後、**マイ フロー**に移動します。
1. 新しくインポートしたフロー**新しい危機管理コミュニケーション ニュースについてユーザーに通知**を選択します。

    > [!NOTE]
    > GCC パッケージをアップロードした場合、フロー名は**新しい危機管理コミュニケーション ニュース GCC についてユーザーに通知**になります。

1. コマンド バーで、**編集**を選択します。
1. **新しいアイテムが投稿されるタイミング** カードを開きます。
1. **サイト アドレス**に対して、SharePoint サイトの名前を入力します。
1. **リスト名**に、**CI_CompanyNews** を入力します。
1. **管理構成設定を取得する**カードを開きます。
1. **サイト アドレス**に対して、SharePoint サイトの名前を入力します。
1. **リスト名**に、**CI_configAdminSetup** を入力します。
1. **変数の初期化 – 詳細を読む**カードを開きます。
1. **Value** に、**詳細**を (自分の母国語で) 入力します。

    ![フローの設定](media/sample-crisis-communication-app/flow-options.png)

1. **保存**を選択します。

> [!NOTE]
> 接続の 1 つが承認されていない場合、エラーを受け取ることがあります。
発生した場合、承認されていないな接続でカードを開き、再承認してください。


### <a name="optional-sending-notifications-to-more-than-5000-users"></a>オプション: 5000 を超えるユーザーに通知を送信する

現在の**グループ メンバーを取得する**アクションは、Power Automate Office ライセンスの 5000 ユーザーへのプルに限定されています。 プレミアム ライセンスであっても、通知を送信するユーザーが多すぎると、Teams コネクタで調整の制限に達することあります。 より多くのユーザーに配布するには、代わりに、配信リストに電子メールを送信するようフローを変更できます。

1. **グループ メンバーの取得**および**指定された通知送信設定に切り替える**のカードを削除します。

    ![削除アクション](media/sample-crisis-communication-app/36-delete-actions.png)

1. 新しいアクションを追加します。

1. **電子メールの送信 (V2)** を検索し、選択します。

    ![電子メールの送信の追加](media/sample-crisis-communication-app/37-add-send-an-email.png)

1. **To** フィールドに、配布グループの名前を入力します。

1. **件名**フィールドで、**動的な値の追加**ボタンを選択し、**ニュース アイテムが投稿されるタイミング** カードから**タイトル** フィールドを追加します。

    ![タイトルの追加](media/sample-crisis-communication-app/38-add-title.png)

1. **本文**フィールドで、**動的な値の追加**ボタンを選択し、**ニュース アイテムが投稿されるタイミング** カードから**詳細** フィールドを追加します。

1. **保存**を選択します。

### <a name="optional-deep-link-teams-notification-into-teams-app"></a>オプション: Teams アプリへの Teams 通知のディープ リンク

Teams 通知を Teams 内のキャンバス アプリに直接開くには、次の手順に従います。

1. 管理者アプリで Teams のディープ リンクをポイントするようにアプリ URL を更新します。 <br>
管理者アプリで、`App ID` がアプリの ID である アプリ URLを次のように変更します。

    ```
    https://teams.microsoft.com/l/entity/<APP ID>/<APP ID>
    ```

    ![管理者アプリ](media/sample-crisis-communication-app/42-admin-app.png)

1. 通知フロー内で生成されたアプリ リンクを更新します。 <br> Set App Link Variable のカードを開き、Value の式を次のように変更します。

    ```
    concat(items('Apply_to_each')?['AppUrl'], if(greater(indexOf(items('Apply_to_each')?['AppUrl'], '?'),0),'&','?'), 'context=%7B%22subEntityId%22%3A%22',triggerBody()?['ID'],'%22%7D')
    ```
    ![フロー設定の変更](media/sample-crisis-communication-app/43-flow-settings.png)

1. キャンバス アプリを更新して、正しいニュース記事のディープリンクへのチームのコンテキスト変数を使用します。 <br> アプリの **OnStart** プロパティについて、Param を `newsid` から `subEntityId` へ変更します。

    ![OnStart の変更](media/sample-crisis-communication-app/44-onstart.png)

### <a name="test-the-news-notification-flow"></a>ニュース通知フローのテスト

ニュース通知フローをテストするには、管理アプリに移動し、新しい会社内部の更新を作成します。 後で、配布リスト内のすべてのユーザーが指定した通知方法で更新を受け取ります。

> [!NOTE]
> エラーが発生した場合、管理アプリの設定で配布リストのグループ ID が正しく入力されていることを確認してください。

## <a name="monitor-office-absences-with-power-bi"></a>Power BI でオフィス不在を監視する

アプリを展開し、ユーザーがさまざまな理由 (病気または自宅勤務など) で不在になるという通知の送信を開始した後、Power BI レポートを使用して、通知を送信したユーザーの数と場所を追跡することができます。  
マップ コントロールを動作させるために、[位置追跡を有効にする](#optional-enable-location-updates) 必要があることに注意してください。 

> [!IMPORTANT]
> Power BI レポートが動作するには、**CI_Employee Status** リストに少なくとも 1 つのエントリがある必要があります。

以前に作成した **CI_Employee Status** SharePoint リストから情報が必要になるので、最初に移動しましょう。 サイトでリストを開き、**設定**アイコンの下の**リスト設定**を選択します。

![従業員ステータス リストの設定](media/sample-crisis-communication-app/001-SharePointList-ListSettings-nolines.PNG)

次の画像に示すように、ブラウザーのアドレス バーにあるサイト名とリスト ID をメモします。

![従業員ステータス リストおよびサイト ID](media/sample-crisis-communication-app/002-SharePointList-AddressAndId-nolines.PNG)

この時点で、Power BI レポートを開くことができます。 Power BI を開き、次に **Presence status report.pbix** ファイルを開きます。 省略記号が表示されるまで、**CI_Employee Status** データ ソースの右側にマウス ポインターを移動します。 選択し、**クエリの編集**を選択します。

![クエリの編集](media/sample-crisis-communication-app/003-PowerBI-EditQuery-nolines.PNG)

Power Query エディターが開いた後、**CI_Employee Status** データ ソースを右クリックし、**詳細エディター**を選択します。

![Power Query 詳細エディター](media/sample-crisis-communication-app/004-PowerQuery-AdvancedEditor-nolines.PNG)

ここで、SharePoint リストからのサイト名とリスト ID を使用します。

次の図に示すように、新しい SharePoint サイトをSharePoint.Tables 文字列、およびGUID が強調表示されている 3 つの場所のリスト ID にコピーにし、**完了**を選択します。

![Power Query 詳細エディターの更新](media/sample-crisis-communication-app/005-PowerQuery-AdvancedEditorUpdates-nolines.PNG)

接続情報の更新後に接続エラーが表示された場合、SharePoint リストの接続に使用する資格情報の更新が必要となることがあります。 

**接続を更新する**

1. **ファイル** メニューで**オプションと設定**を選択し、次に**データ ソースの設定**を選択します。

    ![データ ソースの設定](media/sample-crisis-communication-app/PBI-1-DataSourceSettings.PNG)

1. **アクセス許可の編集**を選択します。

    ![アクセス許可の編集](media/sample-crisis-communication-app/PBI-2-DataSourceSettings-EditPermissions.PNG)

1. **資格情報**のタイプを**組織のアカウント**に設定し、資格情報を使用して SharePoint リストにアクセスします。

    ![アクセス許可の編集](media/sample-crisis-communication-app/PBI-3-OrganizationalAccount.PNG)

**閉じて適用**を選択し、レポートを更新して SharePoint リストからデータを取得します。

![Power Query を閉じて適用](media/sample-crisis-communication-app/006-PowerQuery-CloseAndApply-nolines.PNG)

Power BI は、当日のオフィス不在に関する地理情報および複数の日に渡る欠席のような傾向の両方を示す報告ができるようになりました。 組織内のその他の人が見ることができるように、レポートを公開することができます。

![Power BI 公開レポート](media/sample-crisis-communication-app/007-PowerBI-Publish-nolines.PNG)

レポートが公開されるようになりました。 組織内の他のユーザーと共有できます。 [レポートの更新頻度をスケジュールする](https://docs.microsoft.com/power-bi/refresh-scheduled-refresh) こともできます。

## <a name="integrate-your-app-into-teams"></a>アプリを Teams に統合する

すべてのユーザーと共有するよう機能するアプリによって、Teams 内に危機管理チームを作成してアプリを展開し、問題に対応することができます。

### <a name="deploy-the-app-to-the-app-bar"></a>アプリをアプリ バーに展開する

Teams 管理者は、Teams アプリ バーですべてのユーザーにアプリをプッシュできます。

![Teams のアプリ バー](media/sample-crisis-communication-app/19-App-in-Teams.png)

1. [Power Apps](https://make.powerapps.com) にサインインします。
1. 左側のナビゲーション ウィンドウから、**アプリ**を選択します。
1. **危機管理コミュニケーション** アプリの**その他のコマンド** (...) を選択します。
1. **Teams に追加**を選択します。

    ![Teams に追加](media/sample-crisis-communication-app/24-Add-to-Teams.png)

1. **アプリのダウンロード**を選択します。

    ![アプリのダウンロード](media/sample-crisis-communication-app/25-Download-App.png)

1. Teams を開きます。
1. アプリ バーで**アプリ**に移動します。
1. **カスタム アプリのアップロード**を選択します。
1. Teams 管理者の場合、テナント全体に対するアプリをアップロードできます。 **Contoso のアップロード**を選択します (*Contoso* はテナントの名前を表します)。

    ![アプリのアップロード](media/sample-crisis-communication-app/26-Upload-for-Contoso.png)

1. Power Apps からダウンロードしたファイルをアップロードします。
1. [Teams 管理センターに移動](https://admin.teams.microsoft.com/dashboard) に移動します。
1. **Teams アプリ**の下の左側のナビゲーション ウィンドウで、**セットアップ ポリシー**を選択します。

    ![アプリの設定ポリシー](media/sample-crisis-communication-app/27-Setup-Policies.png)

1. **グローバル (組織全体のセットアップ)** を選択します。
1. **アプリの追加**を選択します。

    ![アプリの追加](media/sample-crisis-communication-app/28-Add-App.png)

1. アップロードする**危機情報**アプリを検索し、選択します。

    ![ピン留めされたアプリの追加](media/sample-crisis-communication-app/29-Add-Pinned-App.png)

1. **追加** を選択します。
1. **保存**を選択します。

> [!NOTE]
> ユーザーが、アプリがアプリ バーに自動的に固定されているを確認できるようになるまで、最大 24 時間かかることがあります。

### <a name="create-a-central-crisis-management-team-in-teams"></a>Teams で中央危機管理チームを作成する<a name="create-a-central-crisis-management-teams-team"></a>

危機対応の調整をするには、Teams で中央危機管理チームを作成し、すべての関連情報を設定します。 このチームは、中央対応チームとのみ共有される必要があります。

1. チームに移動します。
1. 左側のアプリ バーから **Teams** を選択します。
1. **チームへの参加または作成**を選択します。
1. **チームの作成**を選択し、残りの手順を完了します。

    ![チームを作成します](media/sample-crisis-communication-app/23-Create-Team.png)

チームが正常に作成されたら、関連情報をタブとしてピン留めすることができます。 たとえば、危機管理の管理アプリまたは Power BI レポートをチームにピン留めすることができます。

**管理アプリをタブとして追加する**

1. **+** ボタンを選択します。
1. **Power Apps** を検索して選択します。
1. **危機情報管理者**を検索し、選択します。

    ![アプリをピン留め](media/sample-crisis-communication-app/32-Pin-Teams-app.png)

1. **保存**を選択します。

**Power BI レポートをタブとして追加する**

1. **+** ボタンを選択します。
1. **Power BI** を検索し、選択します。
1. Power BI レポートを検索し、選択します。
1. **保存**を選択します。

## <a name="faq"></a>よくあるご質問

* **このソリューションを実行するには、どのライセンスが必要ですか ?**

    - このアプリのソリューションは、Office コネクタを使用しているため、ユーザーおよび管理者用アプリの実行および再生を行うのに、シードされた Power Apps ライセンスで十分です。 詳細: [Power Platform ライセンスの概要](https://docs.microsoft.com/power-platform/admin/pricing-billing-skus)
    - Power BI レポート (ソリューションの一部としてパッケージ化されている) を使用する場合、Power BI ライセンスが必要になります。 詳細: [Power BI の価格](https://powerbi.microsoft.com/pricing/)

* **ソリューションについてフィードバックがある場合、どうすればいいですか?**

    このソリューションの展開およびカスタマイズのエクスペリエンスについて、意見をお待ちしています。 エクスペリエンスを共有するには、[aka.ms/crisis-communication-feedback](https://aka.ms/crisis-communication-feedback) に移動してください。

* **アプリにバグが見つかったようです; どうすればいいですか ?**

   ソリューションのバグを報告するには、[aka.ms/crisis-communication-issues](https://aka.ms/crisis-communication-issues) にアクセスします。

* **GCC で現在サポートされていない機能は何ですか?**

    Teams 用 Power Automate ボット コネクタおよびプッシュ通知コネクタは、現在 GCC では使用できません。 代わりに、電子メール オプションを使用して、内部ニュースの更新についてユーザーに警告します。

* **アプリケーションを更新するにはどうすればよいですか?**

    アプリケーションを更新する場合、[aka.ms/CrisisCommunicationSolution](https://aka.ms/CrisisCommunicationSolution) で説明されている次の手順に従ってください。

## <a name="issues-and-feedback"></a>問題とフィードバック

- 危機管理コミュニケーション サンプル テンプレートに関するフィードバックについては、[aka.ms/crisis-communication-feedback](https://aka.ms/crisis-communication-feedback) に移動してください。
- 危機管理コミュニケーション アプリの問題を報告するには、[aka.ms/crisis-communication-issues](https://aka.ms/crisis-communication-issues) に移動してください。

***免責事項:*** *このアプリはサンプルであり、参照情報の頒布のみを目的として Microsoft Power Apps および Teams により使用されます。このアプリは、病気やその他の疾患の診断、治療、軽減、手当て、または防止のために使用することを想定した医療デバイス、臨床サポート、診断ツール、またはその他のテクノロジとして使用することを意図したものではありません。このアプリをそのような目的のために使用するためのライセンスや権限は、Microsoft によって付与されていません。このアプリは、専門的な医療のアドバイス、診断、手当て、または判断の代替となるように設計または意図されていないため、そのようには使用しないでください。お客様は、このアプリのいかなる使用に関しても単独でリスクと責任を負うものとします。Microsoft は、このアプリまたはアプリと共に提供される関連資料が、何らかの医療目的のために適切であること、また任意の人物の健康や医療に関する要求を満たすことを保証することはしません。* 

### <a name="see-also"></a>関連項目

- [数式のリファレンス](formula-reference.md)
- [コントロールのリファレンス](reference-properties.md)
