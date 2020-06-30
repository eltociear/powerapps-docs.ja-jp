---
title: 地域政府機関の緊急応答およびモニタリング ソリューションを展開する | Microsoft Docs
description: 地域の IT 管理者が地域政府機関の緊急対応およびモニタリング ソリューションを組織に展開するための詳細な手順を示します。
author: KumarVivek
manager: annbe
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 06/05/2020
ms.author: kvivek
ms.reviewer: kvivek
searchScope:
- PowerApps
ms.openlocfilehash: 5c689f3b5761be0f92fe6282cec0b5543454e482
ms.sourcegitcommit: 6f904789d817248eac0a4c9dd0c5fe37dfbb77ad
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2020
ms.locfileid: "3434483"
---
# <a name="deploy-the-regional-governmentemergency-response-and-monitoring-solution"></a>地域政府機関の緊急応答およびモニタリング ソリューションを展開する

地域組織の IT 管理者は、この記事を使用して、地域政府機関の緊急対応およびモニタリング ソリューションを展開できます。 この展開プロセスが終了すると、次のものが表示されます。

- 親組織とその医療機関のマスター データを構成および表示し、ポータルを使用して医療機関のデータを報告できるように、親組織の管理ユーザーを追加および管理できる管理アプリ (モデル駆動型アプリ)。

- 個々の親組織が、ユーザー、医療機関、地域、施設、患者、消耗品、スタッフに関連するデータを追加および管理できるようにする Web ポータル。

- 地域の管理者が Power BI テナントでアクセスして、地域の組織にデータを報告するすべての親組織の主要なデータとインサイトを表示する Power BI ダッシュボード。 同じダッシュボードがポータルに組み込まれており、親組織の管理者は、親組織と医療機関に関する主要なデータとインサイトを表示できます。

組織に地方政府機関の緊急対応およびモニタリング ソリューションを展開するには、次の手順を実行します。

これらの手順を完了するための推定時間: 35〜40 分。

> [!IMPORTANT]
> このソリューションの既存のインストールがある場合は、代わりに次の手順に従って最新バージョンにアップグレードしてください: [ソリューションをアップグレードする](upgrade.md)

## <a name="service-urls-for-us-government-customers"></a>米国政府機関のユーザー向けのサービス URL

Power Apps 米国政府機関の環境や Power BI 米国政府機関のテナントにアクセスするための一連の URL は、市販製品版とは異なります。 この記事では、市販製品版のサービス URL を使用しています。 米国政府組織の場合は、展開の際に以下に記載する米国政府機関の URL を使用してください。

| **商用バージョンの URL**                | **US Government バージョンの URL**  |
|-------------------------------------------|--------------------------------|
| [https://make.powerapps.com](https://make.powerapps.com)                | [https://make.gov.powerapps.us](https://make.gov.powerapps.us) (GCC)<br/><br/>[https://make.high.powerapps.us](https://make.high.powerapps.us) (GCC High)                |
| [https://admin.powerplatform.microsoft.com](https://admin.powerplatform.microsoft.com) | [https://gcc.admin.powerplatform.microsoft.us](https://gcc.admin.powerplatform.microsoft.us) (GCC)<br/><br/>[https://high.admin.powerplatform.microsoft.us](https://high.admin.powerplatform.microsoft.us) (GCC High) |
| [https://app.powerbi.com/](https://app.powerbi.com/)                  | [https://app.powerbigov.us](https://app.powerbigov.us) (GCC)<br/><br/>[https://app.high.powerbigov.us](https://app.high.powerbigov.us) (GCC High)                 |

Power Apps と Power BI についての、米国政府機関の計画の詳細については次を参照してください：

- [米国政府機関用 Power Apps ](https://docs.microsoft.com/power-platform/admin/powerapps-us-government)
- [米国政府機関用 Power BI ](https://docs.microsoft.com/power-bi/service-govus-overview)

## <a name="step-1-download-the-deployment-package"></a>ステップ 1: デプロイ パッケージのダウンロード

> [!IMPORTANT]
> 市販製品版のユーザーは、展開パッケージの代わりに AppSource オプションを使用して、アプリと Power BI ダッシュボードをインストールします。 [サンプル データ](configure.md##add-and-manage-master-data)を使用するには、展開パッケージをダウンロードする必要があります。

<https://aka.ms/rer-solution> から最新の展開パッケージ (.zip) をダウンロードします。

.zip ファイルを解凍する前に、ファイルのブロックを解除してください。

1.  .zip ファイルを右クリックし、**プロパティ**を選択します。

2.  プロパティ ダイアログボックスで **ブロック解除** を選択し、続いて **適用** を選択し、**OK** をクリックします。

    > [!div class="mx-imgBorder"] 
    > ![ソリューション パッケージ プロパティ](media/deploy-deployment-package.png "ソリューション パッケージ プロパティ")

.zip ファイルを解凍すると、解凍したフォルダーに以下が表示されます。

|**フォルダー**  |**説明**  |
|---------|---------|
|**パッケージ**     |  フォルダーには、Package Deployer ツールと、環境にソリューションを設定するために後でインポートするパッケージが含まれています。       |
|**Power BI テンプレート**     | レポートの構成に使用する Power BI レポートのテンプレート ファイル (.pbit) が含まれています。 詳細: [ステップ 5: Power BI ダッシュボードを構成して公開する](#step-5-configure-and-publish-power-bi-dashboard)        |
|**SampleData**     |   サンプル データのインポートに使用できるサンプル マスター データ ファイル (.xlsx) が含まれています。 詳細: [サンプル ファイルを使用してデータをインポートする](configure.md#import-data-using-sample-files)      |

## <a name="step-2-sign-up-for-power-apps-and-create-an-environment"></a>ステップ 2: Power Apps にサインアップして、環境を作成する

Power Apps をまだ持っていない場合は Power Apps にサインアップして適切なライセンスを購入します。
詳細:

- [Power Apps 価格設定](https://powerapps.microsoft.com/pricing/)

- [購入Power Apps](https://docs.microsoft.com/power-platform/admin/signup-for-powerapps-admin)

Power Apps を購入後、Common Data Service データベースで環境を作成します。

1.  [Power Platform 管理センター](https://aka.ms/ppac) にサインインします。

2.  データベースで Common Data Service 環境を作成します。 詳細: [環境の作成と管理](https://docs.microsoft.com/power-platform/admin/create-environment)

    > [!IMPORTANT] 
    > データベースの作成中に、データベースのセキュリティ グループを選択すると、セキュリティ グループのメンバーであるユーザーと のみ アプリを共有できます。

3.  自分の環境に適切なユーザーを作成します。 詳細情報: [ユーザーを作成し、セキュリティ ロールを割り当てる](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles)

環境を作成したら、次の URL を使用してアクセスできます: https://[myenv].crm.dynamics.com、ここで [myenv] は環境の名前です。 この環境 URL をメモします。

## <a name="step-3-create-a-power-apps-portal-in-your-environment"></a>ステップ 3: 環境で Power Apps ポータルを作成する

1.  [Power Apps](https://make.powerapps.com) にサインインします。

2.  右上隅で新しく作成した環境が選択されていることを確認します。

3.  画面の左側にある**アプリ**を選択し、**アプリの作成** \> **ポータル**を選択します。

    > [!div class="mx-imgBorder"] 
    > ![Power Apps ポータルの作成](media/deploy-create-powerapps-portal.png "Power Apps ポータルの作成")

4.  **空のポータル** ページで適切な値を指定してから、**作成**を選択します。

    > [!div class="mx-imgBorder"] 
    > ![ポータルを一から作成する](media/deploy-portal-from-blank.png "ポータルを一から作成する")

Power Apps はポータルのプロビジョニングを開始し、進行状況メッセージがページの右上隅に表示されます。

> [!NOTE]
> ポータルのプロビジョニングにはしばらく時間がかかる場合があります。

ポータルがプロビジョニングされると、Power Apps の**アプリ** リストにポータルが表示されます。 ポータル レコードの省略記号 (…) を選択し、**ブラウズ**を選択してスターター ポータルを表示します。

> [!div class="mx-imgBorder"] 
> ![スターター ポータルを表示する](media/deploy-view-starter-portal.png "スターター ポータルを表示する")

  > [!IMPORTANT]
  > ポータルのプロビジョニングが完了してから、次の手順に進みます。

## <a name="step-4-install-the-app"></a>ステップ 4: アプリのインストール

ポータルがプロビジョニングされたら、地域政府機関の緊急応答およびモニタリング アプリをインストールして、以前に作成したポータルを構成し、管理アプリ (モデル駆動型アプリ) をインストールします。

次の 3 つのオプションのいずれかを使用してアプリをインストールできます。

- Microsoft AppSource (Power Apps 米国政府機関のユーザーのみ)。 [オプション A: Microsoft AppSource (US Govt customers) からアプリをインストールする](#option-a-install-the-app-from-microsoft-appsource-us-govt-customers)を参照

- Microsoft AppSource (Power Apps 市販製品のユーザー向け)。 [オプション B: Microsoft AppSource からアプリをインストールする](#option-b-install-the-app-from-microsoft-appsource)を参照

- 以前にダウンロードした展開パッケージ。 [オプション C: 展開パッケージからアプリをインストールする](#option-c-install-the-app-from-the-deployment-package)を参照

### <a name="option-a-install-the-app-from-microsoft-appsource-us-govt-customers"></a>オプション A: Microsoft AppSource (米国政府機関のユーザー) からアプリをインストールする

1.  Power Platform 管理センターにサインインします。 適切な URL を使用してサインインします。
    - **GCC**: [https://gcc.admin.powerplatform.microsoft.us](https://gcc.admin.powerplatform.microsoft.us)
    - **GCC High**: [https://high.admin.powerplatform.microsoft.us](https://high.admin.powerplatform.microsoft.us).

2.  左側のウィンドウで、**環境**を選択し、前の手順で作成した環境の名前を選択します。

3. 環境の詳細ページで、**Dynamics 365 アプリを管理する**を選択します。

    > [!div class="mx-imgBorder"] 
    > ![環境の設定](media/ppac-env-setting.png "環境の設定")

3.  Dynamics 365 アプリ ページで、**アプリをインストールする**を選択します。 次に右のウィンドウで**地域政府機関の緊急応答およびモニタリング**を選択し、**次へ**を選択します。

    > [!div class="mx-imgBorder"] 
    > ![AppSource](media/ppac-install-app.png "アプリのインストール")

4.  次のページで、条件に同意し、**インストール**を選択します。

5.  インストールが開始され、Dynamics 365 アプリ ページでアプリのインストールの進行状況を監視できます。

    > [!div class="mx-imgBorder"] 
    > ![アプリのインストール進行状況を監視する](media/ppac-app-install-progress.png "アプリのインストール進行状況を監視する")

    > [!IMPORTANT]
    > アプリのインストールにはしばらく時間がかかる場合があります。

6.  アプリをインストールしたら、[Power Apps](https://make.powerapps.com) に移動し、右上隅から環境を選択します。 **アプリ** リストに新しい管理アプリが表示されます。

    > [!div class="mx-imgBorder"] 
    > ![アプリ リストの新しい管理アプリ](media/deploy-new-admin-app.png "アプリ リストの新しい管理アプリ")

### <a name="option-b-install-the-app-from-microsoft-appsource"></a>オプション B: Microsoft AppSource からアプリをインストールする

1.  [AppSource](https://appsource.microsoft.com/) に移動し、「地域政府機関の緊急応答」を検索します。<br/>または、このリンクを使用して、直接 AppSource のアプリに移動します: <https://appsource.microsoft.com/product/dynamics-365/mscrm.pprersapp>

2.  地域政府機関の緊急応答およびモニタリング ページで、**今すぐ入手する**を選択します。

    > [!div class="mx-imgBorder"] 
    > ![AppSource](media/deploy-appsource-01.png "AppSource のアプリ")

3.  AppSource 契約条件を確認するように求められます。 ダイアログには、サインインに使用されているアカウントも表示されます。 **続行** を選択します。 資格情報の確認を求められる場合があります。

4.  次のページで、アプリをインストールする環境を選択します。 法的条項とプライバシーに関する声明のチェック ボックスを選択し、**同意する**を選択します。

    > [!div class="mx-imgBorder"] 
    > ![環境を選択する](media/deploy-appsource-02.png "環境を選択する")

5.  アプリのインストールの進行状況を監視できる Dynamics 365 管理センターに移動します。

    > [!div class="mx-imgBorder"] 
    > ![AppSource](media/deploy-appsource-03.png "アプリのインストール進行状況を監視する")

    > [!IMPORTANT]
    > アプリのインストールにはしばらく時間がかかる場合があります。

6. アプリをインストールしたら、[Power Apps](https://make.powerapps.com) に移動し、右上隅から環境を選択します。 **アプリ** リストに新しい管理アプリが表示されます。

    > [!div class="mx-imgBorder"] 
    > ![アプリ リストの新しい管理アプリ](media/deploy-new-admin-app.png "アプリ リストの新しい管理アプリ")

### <a name="option-c-install-the-app-from-the-deployment-package"></a>オプション C: 展開パッケージからアプリをインストールする

1.  [展開パッケージ](#step-1-download-the-deployment-package) (.zip); を抽出した場所に移動すると、**パッケージ** フォルダーが表示されます。 **パッケージ** フォルダーの下で、**PackageDeployer.exe** ファイルを実行し、ツールを実行してパッケージを展開します。

2.  次の画面で**続行**を選択します。

3.  環境に接続するように求められます。 **展開の種類**として**Office 365**を選択し、**詳細の表示**を選択し、次に資格情報を入力して環境に接続します。

    > [!div class="mx-imgBorder"] 
    > ![展開パッケージ](media/deploy-connect-to-environment.png "展開パッケージ")

4.  **ログイン**を選択し続行します。

5.  複数の Common Data Service 環境にアクセスできる場合、次の画面で、パッケージをインストールする環境を選択するように求められます。 環境を 1 つ選択し、**ログイン**を選択します。

    > [!div class="mx-imgBorder"] 
    > ![環境を選択する](media/deploy-select-environment.png "環境を選択する")

6.  次の画面で**次へ**を選択します。

7.  次の画面には、パッケージがインストールされる環境の名前が表示されます。 情報を確認し、**次へ** を選択します。

8.  次の画面では、スターター ポータルが環境で使用可能かどうかを検証します。 **次へ**を選択して、インストールを続行します。

    > [!div class="mx-imgBorder"] 
    > ![スターター ポータルの検証](media/deploy-validate-starter-portal.png "スターター ポータルの検証")

9.  次の画面にパッケージのインストールの状態が表示されます。 パッケージのインストール完了にはしばらく時間がかかる場合があります。

10. インストールが完了したら、**次へ** を選択します。

11.  次の画面で、**完了**を選択して完了し、設定を閉じます。

12. アプリをインストールしたら、[Power Apps](https://make.powerapps.com) に移動し、右上隅から環境を選択します。 **アプリ** リストに新しい管理アプリが表示されます。

    > [!div class="mx-imgBorder"] 
    > ![アプリ リストの新しい管理アプリ](media/deploy-new-admin-app.png "アプリ リストの新しい管理アプリ")

## <a name="step-5-configure-and-publish-power-bi-dashboard"></a>ステップ 5: Power BI ダッシュボードを構成して公開する

このステップでは、Power BI ダッシュボードを構成して公開し、ポータルに埋め込むことができます。 このステップの最後に、レポートをポータルに埋め込むために使用されるレポート URL が表示されます。

Power BI ダッシュボードを公開するには、次のいずれかのオプションを使用してください: AppSource のテンプレート アプリ、または展開パッケージで利用可能な .pbit ファイルを使用します。

### <a name="option-a-publish-using-the-template-app-from-appsource-preferred-option"></a>オプション A：AppSource のテンプレートアプリを使用して公開する（推奨オプション）

AppSource のテンプレート アプリの使用に関する詳細: [地域の緊急時対応ダッシュボードに接続する](https://docs.microsoft.com/power-bi/connect-data/service-connect-to-regional-emergency-response)

### <a name="option-b-publish-using-the-pbit-file-in-the-deployment-package"></a>オプションB：展開パッケージの .pbit ファイルを使用して公開する

このセクションでは、展開パッケージで使用可能な**地域の緊急時対応アプリ .pbit** ファイルを使用してダッシュボードを公開する方法について説明します。

#### <a name="prerequisites"></a>前提条件

-   レポートを構成および公開するためには、グローバル管理者であり、Power BI Pro ライセンスを保持している必要があります。

-   レポートを公開するワークスペースを Power BI で作成します。 Power BI にサインインして、ワークスペースを作成します。 詳細:  [Power BI で新しいワークスペースを作成する](https://docs.microsoft.com/power-bi/service-create-the-new-workspaces)

-   Microsoft Store から Power BI Desktop をインストールします: <https://aka.ms/pbidesktop>

    > [!NOTE]
    > 既にダウンロード センターのページから実行ファイルとして直接ダウンロードし、 Power BI Desktop をインストールしていた場合は、削除して Microsoft Store のものを使用してください。 Microsoft Store のバージョンは、バージョンは新しいリリースがされると自動的に更新されます。
    >
    > Microsoft Store からインストールできない場合は、[ダウンロード センター ページ](https://www.microsoft.com/download/details.aspx?id=58494)から Microsoft Store 以外の最新バージョンをインストールしてください。

#### <a name="the-process"></a>プロセス

1.  Power BI Desktop を実行し、アカウントを使用してサインインします。

2.  [展開パッケージ](#step-1-download-the-deployment-package) (.zip) を抽出した場所に移動します。 Power BI テンプレート フォルダーに、 **地域の緊急時対応アプリ .pbit** が表示されます。

3.  Power BI Desktop にある**地域の緊急時対応アプリ .pbit**  を開きます。 次の値を入力するように求められます: **CDS_base_solution_URL**。 Common Data Service の環境インスタンスの URL を入力します。 例えば、https://*[myenv]*.crm.dynamics.com などです。ここで *[myenv]* は環境の名前です。 **読み込み**を選択します。

    > [!div class="mx-imgBorder"] 
    > ![Power BI ダッシュボードを構成する](media/deploy-config-dashboard.png "Power BI ダッシュボードを構成する")

4.  Common Data Service 環境に接続するための資格情報を入力するように求められます。  **組織アカウント** \> **サインイン** を選択して、自分の Common Data Service 資格情報を指定します。

    > [!div class="mx-imgBorder"] 
    > ![Common Data Service 環境に接続](media/deploy-connect-cds.png "Common Data Service 環境に接続する")

5.  サインイン後、 **接続** を選択して、Common Data Service のデータに接続します。

6.  接続に成功すると、Power BI レポートが表示されます。 保留中の変更をクエリに適用するように求められるので、 **変更を適用**を選択します。

    > [!NOTE]
    > システムにまだデータを追加していないため、レポートは空白です。

7.   **公開** を選択して Power BI ワークスペースにデータを公開します。 変更を保存するように求められますので、 **保存** を選択します。

     > [!div class="mx-imgBorder"] 
     > ![Power BI ワークスペースを保存する](media/deploy-save-workspace.png "Power BI ワークスペースを保存する")

8.  ファイルを Common Data Service 環境情報とともに、 .pbix ファイルとして保存するように求められます。 名前を入力して、コンピューターに保存します。

9.  .pbix ファイルを保存すると、レポートを公開するように求められます。 **Power BI** へ公開ページで、公開するワークスペースを選択して **選択する** をクリックします。

    > [!div class="mx-imgBorder"] 
    > ![Power BI に公開する](media/deploy-publish-workspace.png "Power BI に公開する")

10.  レポートがワークスペースで使用可能になります。 次に、データセットのデータ更新設定を構成します。 ワークスペースの**データセット** タブで、公開したレポートのデータセットの**スケジュールの更新**アイコンを選択します。

      > [!div class="mx-imgBorder"] 
      > ![ワークスペースで使用可能なレポート](media/deploy-report-workspace.png "ワークスペースで使用可能なレポート")

11.  データ更新設定を初めて設定しようとすると、 **設定** ページに資格情報が無効であることを示すメッセージが表示されます。  **データソース資格情報**から **資格情報を編集する** を選択して、自分の資格情報を指定します。

      > [!div class="mx-imgBorder"] 
      > ![データ ソース資格情報](media/deploy-datasource-credentials.png "データ ソース資格情報")

12.  次の画面で次の操作を行います。

      1.  **認証**方法を **OAuth2** として選択します。

      2.  **このデータ ソースのプライバシー レベルの設定** を **組織的** として設定します。

      3.  **サインイン**を選択します。

13.  資格情報を指定してサインインするように求められます。 サインインに成功すると **設定** ページに戻ります。

14.  **設定** ページで **スケジュールされた更新** を展開して、スケジュールに基づいてデータを更新するために必要な詳細を指定します。 **適用**を選択します。

      > [!div class="mx-imgBorder"] 
      > ![データ更新のスケジュール](media/deploy-schedule-refresh-data.png "データ更新のスケジュール")

      > [!NOTE]
      > - データを更新できる回数には制限があります。 Power BI は共有容量のデータセットを 1 日 8 回の更新に制限します。 データセットが Premium 容量にある場合、データセット設定で 1 日あたり最大 48 回の更新をスケジュールできます。 詳細:  [データを差真の状態に更新](https://docs.microsoft.com/power-bi/refresh-data#data-refresh)
      >- 30 分ごとに更新するようにデータを設定することをお勧めします。

15.  次に、ワークスペースに戻り、**レポート** タブを選択し、レポートを選択してブラウザで開きます。

        > [!div class="mx-imgBorder"] 
        > ![ブラウザーでレポートを開く](media/deploy-open-report.png "ブラウザーでレポートを開く")

16.  URL は次の形式になります: https://app.powerbi.com/groups/3d6db5d0-22c7-4674-b957-0605c021511d/reports/bf9cd5a1-c176-4786-9c4e-684a79678575/ReportSection?redirectedFromSignup=1<br/>
    ポータルに埋め込むために次のセクションで必要になるため、Power BI レポートの URL をメモ帳にコピーします。

17. この Power BI レポートを Power BI テナント内の他のユーザーが使用できるようにする場合は、レポートをアプリとして公開することを検討してください。 左側のウィンドウでワークスペース名を選択し、次に右上隅にある **アプリを作成** を選択します。  

18. アプリ公開ページで次のことをおこないます。

    1. **セットアップ** タブで、アプリの名前と説明を指定します。

    2. **ナビゲーション** タブで、発行する場所を指定します。

    3. **許可** タブで、このアプリを表示できるユーザーまたはグループを指定します。 エンドユーザー向けにこのアプリを自動的にインストールするために **このアプリを自動的にインストール** チェックボックスをオンにします。 詳細: [エンドユーザー向けのアプリを自動的にインストールする](https://docs.microsoft.com/power-bi/service-create-distribute-apps#automatically-install-apps-for-end-users)  

        > [!div class="mx-imgBorder"]
        > ![select-install-apps-automatically](media/select-install-apps-automatically.png)

18. **アプリの公開** を選択します。 Power BI でのアプリの公開についての詳細は [アプリの公開](https://docs.microsoft.com/power-bi/service-create-distribute-apps#publish-your-app) を参照してください。


## <a name="step-6-embed-power-bi-report-in-portal"></a>ステップ 6: ポータルに Power BI レポートを埋め込む

このステップでは、Power BI レポート (前のステップで公開された) をポータルに埋め込みます。

### <a name="prerequisites"></a>前提条件

- このステップを実行するには、グローバル管理者のロールを保持している必要があります。

- Power BI レポートを Power Apps ポータルに埋め込む前に、[Power Apps ポータル管理センター](https://docs.microsoft.com/powerapps/maker/portals/admin/admin-overview)を使用して、**Power BI のビジュアル化**および **Power BI Embedded サービス**がポータルで有効になっている必要があります。

  > [!div class="mx-imgBorder"] 
  > ![Power Apps ポータル管理センター](media/deploy-admin-center.png "Power Apps ポータル管理センター")

詳しい手順については、以下の Power Apps ポータル ドキュメントを参照してください。

-   [Power BI のビジュアル化を有効にする](https://docs.microsoft.com/powerapps/maker/portals/admin/set-up-power-bi-integration#enable-power-bi-visualization)

-   [Power BI Embedded サービスを有効にする](https://docs.microsoft.com/powerapps/maker/portals/admin/set-up-power-bi-integration#enable-power-bi-embedded-service)

### <a name="the-process"></a>プロセス

Power BI のビジュアル化と Power BI Embedded サービスの両方を有効にしたので、ポータルに埋め込むレポート URL を追加します。 前のステップの Power BI レポート URL が手元にあることを確認してください。

1.  [Power Apps](https://make.powerapps.com) にサインインします。

2.  左側のウィンドウで、**アプリ**を選択し、**ポータル管理**アプリを選択して開いてください。

    > [!div class="mx-imgBorder"] 
    > ![ポータル管理アプリを開く](media/deploy-open-mgmt-app.png "ポータル管理アプリを開く")

3.  左側のウィンドウで**サイト設定**を選択し、**新規**を選択します。

    > [!div class="mx-imgBorder"] 
    > ![新しいサイトの設定](media/deploy-site-settings.png "新しいサイトの設定")

4.  **新しいサイトの設定**ページで、次の値を指定します。

    1.  **名前**: PowerBI パス

    2.  **ウェブサイト**: **スターター ポータル**を選択する

    3.  **値**: 前のステップから Power BI レポート URL をコピーする。

        > [!div class="mx-imgBorder"] 
        > ![サイト設定値](media/deploy-site-setting-values.png "サイト設定値")

5.  **保存して閉じる**を選択して、レコードを保存します。

### <a name="restart-the-portal"></a>ポータルを再起動する

変更を有効にするため、すぐにポータルを再起動します。

1.  [Power Apps](https://make.powerapps.com) にサインインします。

2.  左側のウィンドウで**アプリ**を選択し、ポータルの省略記号 (…) メニューを選択し、**設定**を選択します。

    > [!div class="mx-imgBorder"] 
    > ![アプリ ポータル メニュー](media/deploy-portal-menu.png "アプリ ポータル メニュー")

3.   **ポータル設定** ウィンドウで **管理**を選択します。

    > [!div class="mx-imgBorder"] 
    > ![ポータル設定管理](media/deploy-settings-admin.png "[ポータル設定管理")

4.  Power Apps ポータル管理センターで、**ポータル アクション**\>**再起動**を選択します。

    > [!div class="mx-imgBorder"] 
    > ![ポータル アクションの再起動](media/deploy-portal-restart.png "ポータル アクションの再起動")

5.  確認メッセージで**再起動**を選択し、ポータルを再起動します。

  > [!NOTE]
  > オプションで、カスタム ドメイン名を使用してポータルのバニティ URL を設定することもできます。 カスタム ドメインにより顧客はサポート リソースをより簡単に見つけることが可能になり、これはブランドの向上に役立ちます。 そのための詳細情報については、ポータル ドキュメントの[カスタム ドメインを追加する](https://docs.microsoft.com/powerapps/maker/portals/admin/add-custom-domain)を参照してください。

## <a name="step-7-add-a-custom-title-and-logo-for-your-portal"></a>ステップ 7: ポータルのカスタム タイトルとロゴを追加する

カスタム ロゴおよびタイトルをポータルに追加して、組織のブランドに合わせることができます。

> [!NOTE]
> カスタム ロゴ画像の場合、推奨される色は、アイコン フレーム サイズが 40x40px、アイコン サイズが 24x24px、SVG 形式のパディングが 8px の白の透明色です。 ロゴに PNG/JPG 形式を使用している場合は、80x80px のアイコン フレーム サイズと 16px のパディング付き 48x48px のアイコン サイズを使用します。

### <a name="the-process"></a>プロセス

1.  [Power Apps](https://make.powerapps.com) にサインインします。

2.  アプリ リストから**ポータル管理**アプリを開きます。

3.  左側のウィンドウで**サイト設定**を選択し、**新規**を選択します。

4.  **新しいサイトの設定**ページで、次の値を指定します。

    1.  **名前**: SiteTitle

    2.  **ウェブサイト**: **スターター ポータル**を選択する

    3.  **値**: ポータルの左上隅に表示する文字列。

        > [!div class="mx-imgBorder"] 
        > ![ポータル管理サイトの設定](media/deploy-portal-site-settings.png "ポータル管理サイトの設定")
        
5.  サイトの設定レコードを保存するには、**保存**を選択します。

6.  **新規**を選択して、別のサイト設定レコードを作成します。

7.  **新しいサイトの設定**ページで、次の値を指定します。

    1.  **名前**: SiteLogoPath

    2.  **ウェブサイト**: **スターター ポータル**を選択する

    3.  **値**: ロゴ画像ファイルの名前。 たとえば、mylogo.png を指定すると、ポータルはポータルのルートでこのファイルを探します。 後でロゴ ファイルをポータルにアップロードします。

        > [!div class="mx-imgBorder"] 
        > ![新しいサイト設定レコードを作成する](media/deploy-create-new-settings.png "[新しいサイト設定レコードを作成する")       

8.  **保存して閉じる**を選択して、このレコードを保存しページを閉じます。

9.  次に、ロゴ画像ファイルをアップロードします。 左側のウィンドウで **Web ファイル**を選択し、**新規**を選択します。

10. **新しい Web ファイル**画面で、次の値を指定します。

    1.  **名前**: mylogo.png

    2.  **ウェブサイト**: **スターター ポータル**を選択する

    3.  **親ページ:** **設備を選択**を選択する

    4.  **部分 URL:** mylogo.png

        > [!IMPORTANT]
        > この値が、前に **SiteLogoPath** のサイト設定で指定した値と一致することを確認してください。

    5.  **公開状況**: **公開済み**を選択する

        > [!div class="mx-imgBorder"] 
        > ![新しい Web ファイル](media/deploy-new-web-file.png "新しい Web ファイル")

11.  **保存**を選択して、レコードを保存します。

12.  **メモ**のタブを選択し、次に**メモ**に続く **+** を選択します。

      > [!div class="mx-imgBorder"] 
      > ![Web ファイル メモ](media/deploy-web-file-notes.png "Web ファイル メモ")

13.  **タイトル** フィールドに mylogo.png を入力します。 添付アイコンを選択して、コンピューターからロゴ画像ファイルを選択します。

      > [!div class="mx-imgBorder"] 
      > ![ロゴ画像を添付](media/deploy-attach-logo.png "ロゴ画像を添付")

14.  コンピューターから適切なロゴ画像 (.PNG 形式) を選択します。
    選択した画像がページに表示されます。

15.  **メモを追加**を選択します。

16.  ページの右下隅にある保存を選択して、レコードを保存します。

これで終了です。 最新のタイトルとロゴがポータルに表示されるまで、しばらく時間がかかる場合があります。 5 〜 10 分以内にポータルを更新して、最新のタイトルとロゴを確認してください。

## <a name="step-8-add-a-custom-about-page-in-your-portal"></a>ステップ 8: ポータルにカスタム情報ページを追加する

ポータルにカスタム情報ページを追加して、ユーザーに情報やリソースを追加/提示できます。

1.  [Power Apps](https://make.powerapps.com) にサインインします。

2.  左側のウィンドウで**アプリ**を選択し、ポータルの省略記号 (…) メニューを選択し、**編集**を選択します。 これにより、ポータルの構成ページが開きます。

3.  **新しいページ**\>**固定レイアウト**\>**会社紹介ページ テンプレート**を選択します。

    > [!div class="mx-imgBorder"] 
    > ![会社紹介ページ](media/deploy-aboutus-page.png "会社紹介ページ")
    

4.  新しいウェブページの、右ウィンドウにある**部分 URL** フィールドで、**詳細**を使用していることを確認してください。 選択した名前を**名前**フィールドで使用できます。**Contoso について**を使用しています。

    > [!div class="mx-imgBorder"] 
    > ![部分 URL で詳細を使用する](media/deploy-partial-url.png "部分 URL で詳細を使用する")    

5.  左ウィンドウをクリックしてコンテンツを編集します。 既定のエディターを使用するか、右下隅にある **\</\>** を選択して HTML エディターを開きます。

    > [!div class="mx-imgBorder"] 
    > ![会社紹介ページを編集する](media/deploy-edit-aboutus.png "会社紹介ページを編集する")    

6.  情報ページに必要な変更を加えた後、それを保存して右上隅の**同期の構成**を選択します。

ポータルのヘッダーにある**情報**リンクを使用して、ポータル ユーザーは新しく作成された情報ページにアクセスできます。

## <a name="step-9-set-up-server-side-synchronization-of-emails"></a>ステップ 9: 電子メールのサーバー側同期の設定

サーバー側の同期により、Common Data Service の電子メールを、Microsoft Exchange Online、Microsoft Exchange Server (設置型)、および Gmail や Outlook.com などの Web でホストされる電子メール用の POP3 電子メール サーバーと同期できます。

> [!div class="mx-imgBorder"] 
> ![電子メールの同期設定](media/deploy-email-synchronization.png "電子メールの同期設定")

サーバー側の同期を設定する詳細な手順については、次のリソースを参照してください。

-   [サーバー側同期の設定](https://docs.microsoft.com/power-platform/admin/set-up-server-side-synchronization-of-email-appointments-contacts-and-tasks)

-   [Exchange Online への接続](https://docs.microsoft.com/power-platform/admin/connect-exchange-online)

-   [Exchange Server への接続 (オンプレミス)](https://docs.microsoft.com/power-platform/admin/connect-exchange-server-on-premises)

    > [!WARNING]
    > このユーザーが他の Common Data Service または Dynamics 365 環境でサーバー側の同期用に構成されていないことを確認してください。 別の環境でサーバー側同期を設定している場合、ここでサーバー側同期を有効にすると、以前に使用されていた環境でそれが無効になります。

## <a name="step-10-fix-the-processes-for-the-app"></a>手順 10 : アプリのプロセスを修正する

この手順では、次のプロセスを修正します :

- 招待状の送信

- 連絡先にパスワード再設定を送信します。

- Web ロールを新しいユーザーに割り当て

### <a name="step-101-fix-the-send-invitation-process"></a>ステップ 10.1: 招待状の送信プロセスを修正する

このステップでは、**招待状を送信**プロセスを修正して、ポータルの招待状が個々の病院管理者に送信される電子メール アドレスと、招待メールで送信される招待 URL を指定します。

1.  [Power Apps](https://make.powerapps.com) にサインインします。

2.  右上隅の設定ギアを選択してから、**詳細設定**を選択します。

3.  設定ページで、**設定**の横にあるドロップダウン矢印を選択し、**プロセス**を選択します。

    > [!div class="mx-imgBorder"] 
    > ![招待状の送信プロセスを修正する](media/deploy-settings-processes.png "招待状の送信プロセスを修正する")
    

4.  **プロセス** ページで「招待状を送信」を検索し、**招待状を送信**プロセスを選択してそれを開きます。

5.  プロセス定義ページで:

    1.  コマンド バーから**非アクティブ化**を選択してプロセスを非アクティブにします。 非アクティブ化を確認します。

    2.  ステップ領域の下で、**電子メールの作成**ステップの**プロパティの設定**を選択します。

        > [!div class="mx-imgBorder"] 
        > ![電子メール作成のプロパティを設定する](media/deploy-email-properties.png "電子メール作成のプロパティを設定する")

6.  **電子メールの作成**ステップ定義ページで:

    1.  **差出人**フィールドで、ポータル招待リンクの送信に使用される電子メール ID を選択します。 メールを送信するには、ここで指定するユーザー アカウントでサーバー側の同期を有効にする必要があります。

        > [!TIP]
        >  サーバー側の同期を有効にし、no-reply\@*顧客ドメイン* .com のような電子メールアドレスを使用して、環境にアカウントを設定し、ポータル招待メールを送信することができます。

    2.  電子メール本文の https://**regionaldev**.powerappsportals.com 文字列を、ポータルの実際の URL で更新します。 また、黄色で強調表示されている**招待コードのエンコード**のコンテンツを変更しないでください。

        必要に応じて電子メールの本文に他の変更を加え、組織のブランドに合わせることができます。

    3.  **保存して閉じる**を選択して変更を保存します。

        > [!div class="mx-imgBorder"] 
        > ![ポータル URL の更新](media/deploy-update-url.png "ポータル URL の更新")
        

3.  プロセス定義ページに戻ります。 変更を保存してプロセスを**アクティブ化**します。

    > [!div class="mx-imgBorder"] 
    > ![プロセスをアクティブ化する](media/deploy-activate-process.png "プロセスをアクティブ化する")    

### <a name="step-102-fix-the-send-password-reset-to-contact-process"></a>ステップ 10.2: 連絡先へのパスワード再設定送信プロセスを修正する

このステップでは、**連絡先にパスワードの再設定を送信する**のプロセスを修正して、ポータル ユーザーがポータルの**パスワードを忘れた場合**のリンクを使用してパスワードのリセットをするよう要求した際に、ポータル パスワードの再設定メールが送信される電子メール アドレスを指定します。

1.  [Power Apps](https://make.powerapps.com) にサインインします。

2.  右上隅の設定ギアを選択してから、**詳細設定**を選択します。

3.  設定ページで、**設定**の横にあるドロップダウン矢印を選択し、**プロセス**を選択します。

    > [!div class="mx-imgBorder"] 
    > ![連絡先にパスワードの再設定を送信する](media/deploy-password-reset.png "連絡先にパスワード再設定を送信します。")
   

4.  **プロセス** ページで、「連絡先にパスワードの再設定を送信する」を検索し、検索結果から**連絡先にパスワードの再設定を送信する**のプロセスを選択して開きます。

5.  プロセス定義ページで:

    1.  コマンド バーから**非アクティブ化**を選択してプロセスを非アクティブにします。
        非アクティブ化を確認します。

    2.  ステップ領域の下で、**電子メールの送信**ステップの**プロパティの設定**を選択します。

        > [!div class="mx-imgBorder"] 
        > ![電子メール送信のプロパティを設定する](media/deploy-set-email-properties.png "[電子メール送信のプロパティを設定する")
       

6.  **電子メールの送信**ステップの定義ページで、**フォーム** フィールドから動的な値 (黄色で強調表示) を削除します。

    > [!div class="mx-imgBorder"] 
    > ![電子メール送信のステップ定義](media/deploy-email-step-definition.png "電子メール送信のステップ定義")
    

7.  **差出人**フィールドで、ポータル招待リンクの送信に使用される電子メール ID を選択します。 メールを送信するには、ここで指定するユーザー アカウントでサーバー側の同期を有効にする必要があります。

    > [!TIP]
    > サーバー側の同期を有効にし、no-reply\@*顧客ドメイン* .com のような電子メールアドレスを使用して、環境にアカウントを設定し、パスワード再設定の電子メールを送信することができます。
    > 黄色で強調表示されている動的な値を更新しないようにしてください。 必要に応じて、電子メール本文の組織ごとにそのコンテンツを更新できます。

    > [!div class="mx-imgBorder"] 
    > ![動的な値を更新しない](media/deploy-dynamic-values.png "動的な値を更新しない")
    

8.  **保存して閉じる**を選択して変更を保存します。

9.  プロセス定義ページに戻ります。 変更を保存してプロセスを**アクティブ化**します。

    > [!div class="mx-imgBorder"] 
    > ![変更の保存とプロセスのアクティブ化](media/deploy-save-activate-process.png "変更の保存とプロセスのアクティブ化")    

### <a name="step-103-verify-assign-web-roles-to-new-users-process-is-enabled"></a>ステップ 10.3: 新しいユーザーへの Web ロールの割り当てプロセスが有効になっていることを検証する

1.  [Power Apps](https://make.powerapps.com) にサインインします。

2.  右上隅の設定ギアを選択してから、**詳細設定**を選択します。

3.  設定ページで、**設定**の横にあるドロップダウン矢印を選択し、**プロセス**を選択します。

    > [!div class="mx-imgBorder"] 
    > ![Web ロールを新しいユーザーに割り当てる](media/deploy-assign-webroles.png "Web ロールを新しいユーザーに割り当てる")    

4.  **プロセス** ページで 「Web の割り当て」を検索し、**新しいユーザーに Web ロールを割り当てる**プロセスが有効になっていることを確認します。

    > [!div class="mx-imgBorder"] 
    > ![プロセスが有効になっていることを確認する](media/deploy-process-enabled.png "プロセスが有効になっていることを確認する")    

5.  有効になっていない場合は、プロセス名を選択してレコードを開き、**アクティブ化**を選択します。 プロセスのアクティブ化を確認する。

## <a name="step-11-fix-the-flows-for-the-app"></a>手順 11 : アプリのフローを修正する

このステップでは、アプリに必要となるフローを修正します。 次の手順を使用して、アプリで使用されるすべてのフローを表示できます :

1.  [Power Automate](https://flow.microsoft.com/) にサインインする。

2.  左側のウィンドウで、**ソリューション**を選択します。 ソリューション リストから、**地域の緊急時対応ソリューション**を選択し、ソリューションを開きます。

    > [!div class="mx-imgBorder"] 
    > ![ソリューションを開く](media/deploy-open-solution.png "ソリューションを開く")

3.  ソリューションでは、**フロー**でフィルター処理し、すべてのフローを検索します。

    > [!div class="mx-imgBorder"] 
    > ![アプリのフロー](media/conf-all-flows.png "アプリのフロー")

フィールドには 2 つの種類が存在します :

- 最初の一連のフローは、電子メールの送信に活用できます :
    - ポータル ユーザーの要請: 要請の却下時に管理者にメールを送信
    - ポータル ユーザーの要請: 要請の作成時に管理者にメールを送信
    
    これらのフローでは、接続を認証してから、メールを送信するユーザーアカウントを指定して、フローを有効化する必要があります。

- フローの 2 つ目のセットは、タスクを完了する際に役立ちます :
    - 新しい消耗品の入力レコードの処理
    - フロー消耗品の追跡
    - CDC データの入力 - 医療スタッフ
    - CDC データの入力 - 医療消耗品
    - CDC データの入力 - 患者および病院のキャパシティ
    - ポータルに新規入力されたスタッフ エントリーを処理する 

    これらのフローでは、接続を承認してからフローを有効化する必要があります。


### <a name="step-111-fix-the-flows-for-sending-emails"></a>手順 11.1 : 電子メールの送信フローを修正する

このステップでは、以下のことを行います。

|フロー名|変更|
|--|--|
|**ポータル ユーザーの要請: 要請の却下時に管理者にメールを送信**|接続を更新して Common Data Service に接続し、電子メールを送信するユーザー アカウントを指定します。|
|**ポータル ユーザーの要請: 要請の作成時に管理者にメールを送信**|接続を更新して Common Data Service に接続し、電子メールを送信するユーザー アカウントを指定します。 さらに、ポータル URL に基づいて、電子メール本文のポータル URL を更新します。| 

1.  [Power Automate](https://flow.microsoft.com/) にサインインする。

2.  左側のウィンドウで、**ソリューション**を選択します。 ソリューション リストから、**地域の緊急時対応ソリューション**を選択し、ソリューションを開きます。

    > [!div class="mx-imgBorder"] 
    > ![ソリューションを開く](media/deploy-open-solution.png "ソリューションを開く")

3.  ソリューションでは、**フロー**でフィルター処理し、フローを検索します。 

    > [!div class="mx-imgBorder"] 
    > ![フロー消耗品の追跡レコードを検索する](media/deploy-find-record1.png "フローの検索")

4.  **ポータル ユーザーの要請: 要請の却下時にメールを送信**の名前を選択し、フロー定義を開きます。 ツールバーで、**編集**を選択します。

5.  **接続**を選択して Common Data Service に接続する接続を指定し、次に既存の接続を使用するか、**新しい接続を追加**を選択して新しい資格情報を使用します。  

    > [!div class="mx-imgBorder"] 
    > ![資格情報の修正](media/deploy-specify-cred.png "資格情報の修正")

6.  Common Data Service に接続するための接続を修正した後、**IfRequestState ==** を選択し、電子メールを送信するためのメールボックスが有効なアカウントを持つユーザー アカウントを指定します。

    > [!div class="mx-imgBorder"] 
    > ![Outlook の資格情報を指定する](media/deploy-fix-cred2.png "Outlook の資格情報を指定する")

7. **保存**を選択して変更の保存を行い、**有効にする**を選択します。

8.  次に、フロー リストに移動し、**ポータル ユーザーの要請: 要請の作成時に管理者にメールを送信**の名前を選択してフロー定義を開きます。 コマンド バーで、**編集**を選択します。

9.  **接続**を選択して Common Data Service に接続する接続を修正し、次に既存の接続を使用するか、**新しい接続を追加**を選択して新しい資格情報を使用します。

10. 接続を修正した後、Common Data Service に接続します。
     1. **IfRequestState ==** を選択する
     2. **接続**を選択して、Common Data Service に接続する接続を指定する 
     3. **接続**を選択して、電子メールを送信するためのメールボックスが有効なアカウントを持つユーザー アカウントの資格情報を指定する

    > [!div class="mx-imgBorder"] 
    > ![Outlook の資格情報を指定する](media/deploy-fix-cred3.png "Outlook の資格情報を指定する")

11. **電子メールの送信**で、ポータルの URL に従って URL を修正してください。 たとえば、この場合、rer6 を URL 値に変更します。

    > [!div class="mx-imgBorder"] 
    > ![Outlook の資格情報を指定する](media/deploy-fix-cred4.png "Outlook の資格情報を指定する")

12. **保存**を選択して変更の保存を行い、**有効にする**を選択します。

### <a name="step-112-fix-the-flows-for-performing-specific-tasks"></a>手順11.2 : 特定のタスクを実行するフローを修正する

この手順では、特定のタスクの実行に役立つフローの接続情報を承認し、有効化します。

1.  [Power Automate](https://flow.microsoft.com/) にサインインする。

2.  左側のウィンドウで、**ソリューション**を選択します。 ソリューション リストから、**地域の緊急時対応ソリューション**を選択し、ソリューションを開きます。

3.  ソリューションでは、**フロー**をフィルター処理し、**フロー消耗品の追跡**レコードを検索します。

4.  フロー名を選択してフロー定義を開きます。 フロー定義で、ツールバーの**編集**を選択します。

5.  **接続**を選択して Common Data Service に接続する接続を指定し、次に既存の接続を使用するか、**新しい接続を追加**を選択して新しい資格情報を使用します。  

    > [!div class="mx-imgBorder"] 
    > ![資格情報の修正](media/authorize-cred.png "資格情報の修正")

6. **保存**を選択して変更の保存を行い、**有効にする**を選択します。

7. 次の各フローで手順 4 から 6 を実行して接続を承認し、フローを有効化します。

    - 新しい消耗品の入力レコードの処理
    - CDC データの入力 - 医療スタッフ
    - CDC データの入力 - 医療消耗品
    - CDC データの入力 - 患者および病院のキャパシティ
    - ポータルに新規入力されたスタッフ エントリーを処理する

## <a name="step-12-share-admin-app-with-other-admin-users"></a>ステップ 12: 管理アプリを他の管理ユーザーと共有する

ビジネス管理者ユーザーが管理アプリ (モデル駆動型アプリ) を使用してデータを入力および管理するには、アプリを管理者ユーザーと共有する必要があります。 Azure AD グループを使用すると、管理ユーザーのグループとアプリをより簡単に共有できます。

> [!IMPORTANT]
> アプリを共有する予定のユーザーまたはグループが 既に 環境へのアクセスができていることを確認してください。 通常、環境を設定する 間には、ユーザーまたはグループはすでに追加されています。 または、こちらのステップに従ってユーザーを環境に追加し、アプリをユーザーと共有する前に適切なアクセスを提供できます: [ユーザーを作成してセキュリティ ロールを割り当てる](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles)。

1.  [Power Apps](https://make.powerapps.com) にサインインします。

2.  左側のナビゲーション ウィンドウで、**アプリ**を選択し、モデル駆動型アプリ (**管理アプリ – 地域の緊急対応時アプリ**) を選択し、バナーで**共有**を選択します。

    > [!div class="mx-imgBorder"] 
    > ![管理アプリの共有](media/deploy-share-admin-app.png "管理アプリの共有")

3.  このアプリを共有する Azure AD グループまたは管理ユーザーを指定し、**地域の緊急対応時管理者**セキュリティ ロールを割り当て、**共有**を選択します。

    > [!div class="mx-imgBorder"] 
    > ![Azure AD グループまたは管理ユーザーを指定する](media/deploy-specify-share.png "Azure AD グループまたは管理ユーザーを指定する")

## <a name="next-steps"></a>次のステップ

これで展開手順が完了しました。 ビジネス管理者は、[構成](configure.md)トピックを使用して、次の手順を実行します。

-  マスター データの構成と管理

-  ポータル ユーザーを作成して個々の病院の管理者ユーザーを招待し、ポータルを使用してデータとユーザーを追加および管理できるようにします。

- テナントの Power BI ダッシュボードを表示します。

## <a name="issues-and-feedback"></a>問題とフィードバック

- 地域政府機関の緊急応答およびモニタリング ソリューションに関する問題を報告するには、<https://aka.ms/rer-issues> を参照してください。

- 地域政府機関の緊急応答およびモニタリング ソリューションに関するフィードバックについては、<https://aka.ms/rer-feedback> を参照してください。
