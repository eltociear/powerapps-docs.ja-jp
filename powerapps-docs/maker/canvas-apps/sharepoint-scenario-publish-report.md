---
title: Power BI プロジェクト レポートの発行とダッシュボードの作成 | Microsoft Docs
description: このタスクでは、データセットとレポートを Power BI サービスに発行します。その後、レポートに基づくダッシュボードを作成します。
author: NickWaggoner
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/30/2018
ms.author: niwaggon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d90d26c3cbc00b621ee2857c5c0d8ce3169f8939
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2019
ms.locfileid: "3304176"
---
# <a name="publish-the-power-bi-project-report-and-create-a-dashboard"></a>Power BI プロジェクト レポートの発行とダッシュボードの作成
> [!NOTE]
> この記事は、Power Apps、Power Automate、および Power BI と SharePoint Online の使用に関するチュートリアル シリーズの一部です。 シリーズ全般に関することや、関連するファイルのダウンロードの詳細について、[シリーズの概要](sharepoint-scenario-intro.md) を必ずご覧ください。

このタスクでは、データセットとレポートを Power BI サービスに発行します。その後、レポートに基づくダッシュボードを作成します。 多くの場合、レポートには多数の視覚エフェクトが含まれますが、ダッシュボードではサブセットのみが使用されます。 ここでは、ダッシュボードに 4 つの視覚エフェクトをすべて追加します。

## <a name="step-1-publish-the-dataset-and-report"></a>手順 1: データセットとレポートを発行する
1. Power BI Desktop で、**ホーム** タブで、**発行**をクリックまたはタップします。
   
    ![データセットとレポートの発行](./media/sharepoint-scenario-publish-report/06-01-01-publish.png)
2. Power BI サービスにまだサインインしていない場合は、アカウントを入力して、**サインイン**をクリックまたはタップします。
   
    ![アカウントへのサインイン](./media/sharepoint-scenario-publish-report/06-01-02-account.png)
3. パスワードを入力して、**サインイン**をクリックまたはタップします。
   
    ![アカウントのパスワードを入力](./media/sharepoint-scenario-publish-report/06-01-03-password.png)
4. レポートの宛先を選択し、**選択**をクリックまたはタップします。 SharePoint でのレポートへのアクセスを簡素化するために、グループ ワークスペースに発行することをお勧めします。 ここでは、**プロジェクト管理**のグループ ワークスペースに発行しています。 詳細については、「[Power BI アプリ ワークスペースでの共同作業](https://docs.microsoft.com/power-bi/service-collaborate-power-bi-workspace)」を参照してください。
   
    ![宛先のワークスペース](./media/sharepoint-scenario-publish-report/06-01-04-workspace.png)
5. 発行が完了したら、**Power BI で 'project-analysis.pbx' を開く** をクリックまたはタップします。
   
    ![発行に成功](./media/sharepoint-scenario-publish-report/06-01-05-open-report.png)
6. Power BI サービスにより、レポートがブラウザーで読み込まれます。 左側のナビゲーション ウィンドウが展開されていない場合には、左上のメニュー **(a)** をクリックまたはタップして展開します。
   
    ![Power BI サービスのレポート](./media/sharepoint-scenario-publish-report/06-01-06-service-report.png)
   
    発行したときに、Power BI Desktop にデータセット **(d)** とレポート **(c)** がアップロードされたことがわかります。 Power BI Desktop ではなくサービスでダッシュボードを作成しますが、このワークスペースにはまだダッシュボードがありません **(b)**。 後ほどの手順で作成します。

## <a name="step-2-configure-credentials-for-refresh"></a>手順 2: 更新のための資格情報を構成する
1. サービスで、右上隅の![歯車アイコン](./media/sharepoint-scenario-publish-report/icon-gear.png) をクリックまたはタップし、**設定**をクリックまたはタップします。
2. **データセット**、**project-analysis** の順にクリックまたはタップします。
   
    ![project-analysis データセット](./media/sharepoint-scenario-publish-report/06-01-07-dataset.png)
3. **データ ソースの資格情報**を展開して、**資格情報の編集**をクリックまたはタップします。
   
    ![データ ソースの資格情報を編集](./media/sharepoint-scenario-publish-report/06-01-08-credentials.png)
4. 認証方法で **OAuth2** を選択して、**サインイン**をクリックまたはタップします。
   
    ![SharePoint にサインインする](./media/sharepoint-scenario-publish-report/06-01-09-sign-in.png)
5. SharePoint リストのアクセス許可のあるアカウントを選択、またはアカウントにサインインします。
   
    ![Office 365 にサインインしています](./media/sharepoint-scenario-publish-report/06-01-10-account.png)
   
    プロセスが完了すると、サービスで次のメッセージが表示されます。
   
    ![データ ソースが更新されました](./media/sharepoint-scenario-publish-report/06-01-11-updated.png)

## <a name="step-3-create-a-dashboard"></a>手順 3: ダッシュボードを作成する

1. レポートに戻るには、**レポート**以下の **project-analysis** をクリックまたはタップします。

1. 左上のグラフをクリックまたはタップし、 ![ピン留めアイコンをクリックまたはタップします](./media/sharepoint-scenario-publish-report/icon-pin.png)。
   
    ![グラフのピン留め](./media/sharepoint-scenario-publish-report/06-01-12-pin-projected.png)
2. ピン留めするダッシュボードの名前を入力し、**ピン留め**をクリックまたはタップします。
   
    ![新しいダッシュボードにグラフをピン留めする](./media/sharepoint-scenario-publish-report/06-01-13-pin-new.png)
3. 左上のグラフをクリックまたはタップし、 ![ピン留めアイコンをクリックまたはタップします](./media/sharepoint-scenario-publish-report/icon-pin.png)。
   
    ![グラフのピン留め](./media/sharepoint-scenario-publish-report/06-01-14-pin-variance.png)
4. 既存のダッシュボードを選択し、**ピン留め**をクリックまたはタップします。
   
    ![既存のダッシュボードにグラフをピン留め](./media/sharepoint-scenario-publish-report/06-01-15-pin-existing.png)

5. 残り 2 つの視覚エフェクトについても、ピン留めのプロセスを繰り返します。

6. 左側のナビゲーション ウィンドウで、ダッシュボード名をクリックまたはタップします。
   
    ![サイト ナビゲーションの新しいダッシュボード](./media/sharepoint-scenario-publish-report/06-01-16-dashboard-menu.png)

7. ダッシュボードを確認します。 タイルをクリックすると、レポートに戻ります。
   
    ![完成したダッシュボード](./media/sharepoint-scenario-publish-report/06-01-17-dashboard-completed.png)

これで、Power BI での作業はほぼ終わりです。 レポートとダッシュボードを初めて作成した方は、お疲れさまでした。 すでに慣れていらっしゃる場合は、すばやく作成できたと思います。 今度は、ダッシュボードに注意を払う必要があるかを把握するためのアラートを追加します。

## <a name="next-steps"></a>次の手順
このチュートリアル シリーズの次の手順では、[Power BI プロジェクト レポートのデータ アラートを設定](sharepoint-scenario-alerts-flow.md) します。

