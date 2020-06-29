---
title: Application Insights を使用してアプリのテレメトリを分析する | Microsoft Docs
description: Application Insights を使用してアプリのテレメトリを分析する方法
author: aengusheaney
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/24/2020
ms.author: aheaney
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 72de7fbd47678a8b6424fe04c5527311d31b549b
ms.sourcegitcommit: 0c92e85f95f3baa04cce140c96e53d5d86d685c0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "3333238"
---
# <a name="analyze-app-telemetry-using-application-insights"></a>Application Insights を使用してアプリのテレメトリを分析する

アプリを [Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview) の機能である[Application Insights](https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview) に接続できます。 Application Insights には、問題を診断し、およびユーザーがアプリで実際に行うことを理解するのに役立つ強力な分析ツールが含まれています。 

アプリを Applications Insights に接続すると、より適切なビジネス上の意思決定に役立つ情報を収集し、およびアプリの品質を向上することができます。

このクイック スタートでは、Kudos というキャンバス アプリをインストルメントします。 これにより、テレメトリの概念を調べ、検出し、それらを独自のキャンバス アプリに適用することができます。 サンプルの Kudos アプリは、 [従業員エクスペリエンス スターター キット](https://powerapps.microsoft.com/blog/powerapps-employee-experience-starter-kit) からダウンロードできる従業員エンゲージメント アプリのスイートの一部です。

## <a name="prerequisites"></a>前提条件

- [Azure portal](https://portal.azure.com) にアクセスできる必要があります。
- [Azure リソースを作成する](https://docs.microsoft.com/azure/role-based-access-control/quickstart-assign-role-user-portal) へのアクセス許可が必要です。

### <a name="optional"></a>任意

- [従業員エクスペリエンス スターター キット](https://powerapps.microsoft.com/blog/powerapps-employee-experience-starter-kit) から Kudos アプリをダウンロードおよびインストールします。 代わりに、既存のアプリを使用することもできます。

## <a name="create-an-application-insights-resource"></a>Application Insights リソースの作成

アプリのテレメトリを送信する前に、イベントを格納する Application Insights リソースを作成する必要があります。

1.  [Azure Portal](https://portal.azure.com/) にサインインします。

1. Application Insights を検索します。

    ![Application Insights](./media/application-insights/azureappinsights.png "Application Insights")

1. Application Insights リソースを作成します。

    ![Application Insights リソースの追加](./media/application-insights/azureappinsights-add.png "Application Insights リソースを追加する")

1. 適切な値を入力し、および**レビュー + 作成**を選択します。 詳細については、[Application Insights リソースを作成](https://docs.microsoft.com/azure/azure-monitor/app/create-new-resource) をお読みください。 

    ![リソースの作成](./media/application-insights/createresource.png "リソースの作成")

1. Application Insights インスタンスの作成後、インスタンスの概要が表示されます。 **インストルメンテーション キー**をコピーします。 アプリを構成するには、このキーが必要です。

    ![インストルメンテーション キーをコピーする](./media/application-insights/instrumentation-key.png "インストルメンテーション キーをコピーする")

## <a name="connect-your-app-to-application-insights"></a>アプリを Application Insights に接続する

1. [Power Apps](https://make.powerapps.com) にサインインします。

1. 左側のナビゲーションから**アプリ**を選択します。 アプリのリストから **Kudos** アプリを選択し、次に**編集**を選択します。

    ![Kudos アプリを編集する](./media/application-insights/edit-kudos-app.png "Kudos アプリを編集する")

    > [!NOTE]
    > 新しいアプリを[作成する](open-and-run-a-sample-app.md)または代わりに既存のアプリを[編集する](edit-app.md) こともできます。

1. 左側のナビゲーション ツリー ビューから**アプリ** オブジェクトを選択し、**インストルメンテーション キー**を貼り付けます。

    ![インストルメンテーション キーを追加する](./media/application-insights/add-instrumentation-key.png "インストルメンテーション キーを追加する")

1. アプリを**保存**および**公開**します。

1. 別のスクリーンによって公開されているアプリを**再生**および参照します。 

別のスクリーンを閲覧すると、次のような使用詳細などを含むイベントが自動的に Application Insights に記録されます。

- アプリへのアクセス元。
- 使用されているデバイス。
- 使用されているブラウザーの種類。

> [!IMPORTANT]
> Application Insights にイベントを送信するには公開されているアプリを再生する必要があります。 Power Apps Studio でアプリをプレビューした場合、イベントは Application Insights に送信されません。

## <a name="view-events-in-application-insights"></a>Application Insights でイベントを表示する

1.  [Azure Portal](https://portal.azure.com/) にサインインし、および[先ほど](#create-an-application-insights-resource) 作成した Application Insights リソースを開きます。

1. 左側のナビゲーション ウィンドウで下方向へスクロールし、および**使用**セクションで**ユーザー**を選択します。 

    > [!NOTE]
    > **ユーザー** ビューには、次のようなアプリの使用詳細が表示されます。
    > - アプリを表示したユーザーの数。
    > - アプリのユーザーによるセッションの数。
    > - アプリに対して記録されたイベントの数。
    > - ユーザーのオペレーティング システムおよびブラウザー バージョンの詳細。
    > - ユーザーのリージョンと場所。
    > 
    > 詳細については、[ユーザー、セッション、および Application Insights でイベントを分析](https://docs.microsoft.com/azure/azure-monitor/app/usage-segmentation) をお読みください。

1. ユーザー セッションの 1 つを選択して、特定の詳細をより細かく調べます。 セッションの長さおよび表示したスクリーンなどの情報を参照できます。

    ![ユーザーの使用詳細](./media/application-insights/appinsights-users.gif "ユーザーの使用詳細")

1. **使用**セクションの左側のナビゲーション ウィンドウで**イベント** ビューを選択します。 すべてのアプリ セッションの間で表示されたすべてのスクリーンの概要を参照できます。

    ![アプリのイベントの詳細](./media/application-insights/appInsights-events.gif "アプリのイベントの詳細")

> [!TIP]
> 使用できる追加の Application Insights 機能の一部は次のとおりです。  
> - [じょうごグラフ](https://docs.microsoft.com/azure/azure-monitor/app/usage-funnels)
> - [コーホート](https://docs.microsoft.com/azure/azure-monitor/app/usage-cohorts)
> - [影響分析](https://docs.microsoft.com/azure/azure-monitor/app/usage-impact)
> - [リテンション期間の分析](https://docs.microsoft.com/azure/azure-monitor/app/usage-retention)
> - [使用フロー](https://docs.microsoft.com/azure/azure-monitor/app/usage-flows)

## <a name="create-custom-trace-events"></a>カスタム トレース イベントを作成する

カスタム トレースを Application Insights に直接書き込み、シナリオに特有の情報の分析を開始できます。 [トレース](https://docs.microsoft.com/powerapps/maker/canvas-apps/functions/function-trace) 機能を使用すると以下を収集できます。

- スクリーンのコントロールの詳細な使用情報。
- アプリにアクセスしている特定のユーザー。
- 発生したエラー。

ユーザーがアプリを参照してさまざまなアクションを実行しながら情報の記録を送信できるので、トレースは問題を診断するのにも役立ちます。

アプリから Application Insights にカスタム トレース 情報を送信する場合、トレース メッセージには 3 つの重大度があります。

- 情報
- 警告
- エラー

シナリオに応じて、適切な重大度のトレース メッセージを送信するように選択できます。 データをクエリし、およびメッセージの重大度に基づいて特定のアクションを実行できます。

> [!NOTE]
> 人事データを記録する場合、GDPRなどの、データ コンプライアンスの義務を考慮する必要があり、必要に応じて実装する必要もあります。

ここで、アプリを更新し、およびアプリの各スクリーンでフィードバックを収集するための新しいコンポーネントを作成します。 Application Insights にイベントを書き込みます。

1. [Power Apps](https://make.powerapps.com) にサインインします。

1. 左側のナビゲーションから**アプリ**を選択します。 アプリのリストから **Kudos** アプリを選択し、次に**編集**を選択します。

    > [!NOTE]
    > 新しいアプリを[作成する](open-and-run-a-sample-app.md)または代わりに既存のアプリを[編集する](edit-app.md) こともできます。

1. **ツリー ビュー**の**コンポーネント** オプションを選択します。

    ![コンポーネント](./media/application-insights/new-component.png "コンポーネント")

1. **新しいコンポーネント**を選択し、次に幅を 200 および高さを 75 にサイズ変更します。

    ![高さおよび幅](./media/application-insights/resize-component.png "高さと幅")

1. メニューから**挿入**を選択し、次に**アイコン**を選択して*絵文字 - しかめっ面アイコン*および*絵文字 - 笑顔アイコン*を選択します。

    ![アイコンを追加する](./media/application-insights/add-icons.png "アイコンを追加する")

1. **新しいカスタム プロパティ**を選択して、カスタム プロパティを作成します。

    ![カスタム プロパティを作成する](./media/application-insights/create-custom-property.png "カスタム プロパティを作成する")

1. *FeedbackSceen* などのプロパティ*名*および*表示名*を入力します。

1. プロパティの*内容*を入力します。

1. **プロパティの種類**を**入力**、および**データ型**を**スクリーン**として選択します。

    ![カスタム プロパティ](./media/application-insights/custom-input-property.png "カスタム プロパティ")

    > [!NOTE]
    > プロパティを入力すると、スクリーン名およびそのコンポーネントを取り込むことができるので、Application Insights にこの情報を記録することができます。

1. **ツリー ビュー**のコンポーネントを選択し、**その他の操作** (**...**) を選択し、次に**名前の変更**を選択し、*FeedbackComponent* などのわかりやすい名前にコンポーネントの名前を変更をします。

    ![コンポーネントおよびアイコンの名前を変更する](./media/application-insights/rename-component-icons.png "コンポーネントおよびアイコンの名前を変更する")

1. アイコンを選択し、**その他の操作** (**...**) を選択し、次に**名前の変更**を選択して *FrownIcon* および *SmileIcon* などのわかりやすい名前にアイコンの名前を変更します。

1. **FrownIcon** を選択し、**OnSelect** プロパティを選択し、次に数式バーに次のような式を入力します。

    ```powerapps-dot
    Trace(
       "App Feedback",
       TraceSeverity.Information,
           {
             UserName: User().FullName,
             UserEmail: User().Email,
             Screen: FeedbackComponent.FeedbackScreen.Name,
             FeedbackValue: "-1"
           }
         );
    Notify("Thanks for you feedback!");
    ```

    ![しかめっ面アイコンの数式](./media/application-insights/frownicon-formula.png "しかめっ面アイコンの数式")

    > [!NOTE]
    > 数式の式は*ユーザー名*、*UserEmail*、*スクリーン*、および*フィードバック* (値が *-1*) を Application Insights に送信します。

1. **SmileIcon** を選択し、**OnSelect** プロパティを選択し、次に数式バーに次のような式を入力します。
    
    ```powerapps-dot
    Trace(
       "App Feedback",
       TraceSeverity.Information,
           {
             UserName: User().FullName,
             UserEmail: User().Email,
             Screen: FeedbackComponent.FeedbackScreen.Name,
             FeebackValue: "1"
           }
         );
    Notify("Thanks for you feedback!");
    ```

1. アプリのいずれかの画面にコンポーネントを追加します。

    ![フィードバック コンポーネントを追加する](./media/application-insights/add-feedback-component.png "フィードバック コンポーネントを追加する")

1. **保存**を選択し、次に**公開**を選択してアプリを保存および公開します。

1. 公開されたアプリを再生し、スクリーンから笑顔およびしかめっ面フィードバックを送信します。

    > [!IMPORTANT]
    > Application Insights にイベントを送信するには公開されているアプリを再生する必要があります。 Power Apps Studio でアプリをプレビューした場合、イベントは Application Insights に送信されません。

    ![公開アプリを再生する](./media/application-insights/play-published-app.png "公開アプリを再生する")

## <a name="analyze-data-in-application-insights"></a>Application Insights でデータを分析する

これで、Application Insights でアプリから[トレース](#create-custom-trace-events) 機能を使用して送信したデータの分析を開始することができます。

1.  [Azure Portal](https://portal.azure.com/) にサインインし、[先ほど](#create-an-application-insights-resource) 作成した Application Insights リソースを開きます。

    ![Application Insights を選択する](./media/application-insights/select-app-insights.png "[Application Insights の選択]")

1. 左側のナビゲーション ウィンドウから**監査**の下の**ログ**を選択します。

    ![ロゴの選択](./media/application-insights/select-logs.png "ロゴの選択")

1. 次のクエリを入力し、**実行**を選択します。 アプリから受信されたフィードバックが返されます。

    ```kusto
    traces
    | where message == "App Feedback"
    | order by timestamp
    ```

    ![アプリのフィードバッグを表示する](./media/application-insights/view-app-feedback.png "アプリのフィードバッグを表示する")

1. 結果の行を選択し、*customDimensions* フィールドを展開します。 

    コンポーネントの中の笑顔またはしかめっ面アイコンの**OnSelect**イベントのための**スクリーン**、**ユーザー名**、**UserEmail**、および **FeedbackValue** の値が記録されました。 <br>
    **appId**、**appName**、および **appSessionId** などの Application Insights に送信される各イベントに対していくつかの追加された値の記録もあります。

    ![カスタム ディメンションを展開する](./media/application-insights/expand-custom-dimensions.png "カスタム ディメンションを展開する")

1. 次のクエリ例では、JSON カスタム ディメンションのプロパティを拡張し、および結果ビューに列を表示できます。

    ```kusto
    traces
        | extend customdims = parse_json(customDimensions)
        | where message == "App Feedback"
        | project timestamp
            , message
            , AppName = customdims.['ms-appName']
            , AppId = customdims.['ms-appId']
            , FeedbackFrom = customdims.UserEmail
            , Screen = customdims.Screen
            , FeedbackValue = customdims.FeedbackValue
        | order by timestamp desc
    ```

    ![customDimensions クエリを拡張する](./media/application-insights/custom-dimensions-extend-query.png "customDimensions クエリを拡張する")

    > [!TIP]
    > *ログ クエリ*は非常に強力です。 これらを使用して、複数のテーブルを結合し、大量のデータを集計し、および複雑な操作を実行できます。 詳細については、[ログ クエリ](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview) をお読みください。

## <a name="export-data-to-power-bi"></a>Power BI へのデータのエクスポート

Application Insights データおよびクエリ結果を Power BI にエクスポートして、分析およびデータ プレゼンテーションをすることができます。

1.  [Azure Portal](https://portal.azure.com/) にサインインし、[先ほど](#create-an-application-insights-resource) 作成した Application Insights リソースを開きます。

1. 左側のナビゲーション ウィンドウから**監査**の下の**ログ**を選択します。

1. ログ分析クエリ ウィンドウから**エクスポート** ドロップダウン メニューを選択します。

1. **Power BI(M クエリ) にエクスポートする**オプションを選択します。 これにより Power BI クエリ ファイルをコンピューターにダウンロードします。

    ![Power BI クエリのエクスポート](./media/application-insights/export-powerbi-query.png "Power BI クエリのエクスポート")

1. ダウンロードしたファイルをテキスト エディターで開き、クエリをクリップボードにコピーします。

1. Power BI を開きます。

1. **ホーム**リボンの**データ取得**のドロップダウン メニューを選択し、次に**空のクエリ**を選択します。

    ![Power BI 空のクエリ](./media/application-insights/powerbi-blank-query.png "Power BI 空のクエリ")

1. クエリのウィンドウで、**詳細エディター**を選択します。 手順 5 からのクエリをウィンドウに貼り付け、**完了**を選択し、次に**閉じる & 適用**を選択します。

    ![Power BI 事前クエリ](./media/application-insights/powerbi-advance-query.png "Power BI 事前クエリ")

1. Power BI でグラフおよびビジュアル化を作成して、アプリで受け取ったフィードバックを表示するだけでなく、データに基づく決定および操作を行なうこともできます。

    ![グラフおよびビジュアル化](./media/application-insights/powerbi-feedback.png "グラフおよびビジュアル化")

## <a name="default-trace-event-context-and-dimensions"></a>既定のトレース イベント コンテキストおよびディメンション

既定のディメンションのセットは各トレース イベントの *customDimensions* プロパティにも追加されます。 これらのディメンションは、イベントが発生したアプリケーションとアプリケーションのセッションを識別するために使用できます。 トレース機能を使用して追加のカスタム データを記録する場合、それらもカスタム ディメンションに表示されます。

| ディメンション名  | 説明                                            |
|-----------------|-------------------------------------------------------|
| ms-appId        | イベントを送信したアプリのアプリケーション ID。     |
| ms-appName      | イベントを送信したアプリのアプリケーションの名前。   |
| ms-appSessionId | アプリケーション セッション ID。                           |

