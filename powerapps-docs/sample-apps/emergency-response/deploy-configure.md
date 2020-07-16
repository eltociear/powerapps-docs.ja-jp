---
title: Hospital Emergency Response アプリを展開する | Microsoft Docs
description: 病院の IT 管理者が、自分たちの組織のためのサンプル アプリをデプロイして構成するための詳細な手順を示します。
author: pankajarora-msft
manager: annbe
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 06/10/2020
ms.author: pankar
ms.reviewer: kvivek
ms.openlocfilehash: 30aa2a2d44cdb2f85f73296601f4117f8a0b2dcc
ms.sourcegitcommit: 997384ebd01bda4f456f08689e024fb8ca5bf057
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2020
ms.locfileid: "3455208"
---
# <a name="deploy-the-hospital-emergency-response-app"></a>病院緊急時対応アプリをデプロイする

病院緊急時対応アプリでは、ニーズに適応するために多少の設定が必要です。 この記事では、病院の IT 管理者が、自分たちの組織のためのサンプル アプリケーションをデプロイして構成するための詳細な手順を示します。

これらの手順を完了するための推定時間: **35〜40 分**。

## <a name="service-urls-for-us-government-customers"></a>米国政府機関のユーザー向けのサービス URL

Hospital Emergency Response ソリューションは、米国政府機関のユーザーにご利用いただけます。 Power Apps米国政府機関の環境や Power BI にアクセスする URL が市販製品とは異なる設定になっています。

このサポート記事では、市販製品版のサービス URL を使用しています。 米国政府機関のユーザーは、展開の際に以下に記載する米国政府機関の URL を使用してください：


| **商用バージョンの URL**                | **US Government バージョンの URL**  |
|-------------------------------------------|--------------------------------|
| [https://make.powerapps.com](https://make.powerapps.com)                | [https://make.gov.powerapps.us](https://make.gov.powerapps.us) (GCC) <br/><br/>[https://make.high.powerapps.us](https://make.high.powerapps.us) (GCC High)                |
| [https://admin.powerplatform.microsoft.com](https://admin.powerplatform.microsoft.com) | [https://gcc.admin.powerplatform.microsoft.us](https://gcc.admin.powerplatform.microsoft.us) (GCC)<br/><br/>[https://high.admin.powerplatform.microsoft.us](https://high.admin.powerplatform.microsoft.us) (GCC High)|
| [https://app.powerbi.com/](https://app.powerbi.com/)                  | [https://app.powerbigov.us](https://app.powerbigov.us) (GCC)<br/><br/>[https://app.high.powerbigov.us](https://app.high.powerbigov.us) (GCC High)                 |

Power Apps と Power BI についての、米国政府機関の計画の詳細については次を参照してください：
- [米国政府機関用 Power Apps ](https://docs.microsoft.com/power-platform/admin/powerapps-us-government)
- [米国政府機関用 Power BI ](https://docs.microsoft.com/power-bi/service-govus-overview)


## <a name="step-1-download-the-deployment-package"></a>ステップ 1: デプロイ パッケージのダウンロード

> [!IMPORTANT]
> 市販製品のユーザーは、この手順をスキップし、代わりに AppSource オプションを使用して、アプリと Power BI ダッシュボードをインストールします。 

<https://aka.ms/emergency-response-solution> から最新の展開パッケージ (.zip) をダウンロードします。

.zip ファイルを解凍する前に、ファイルのブロックを解除してください。

1.  .zip ファイルを右クリックし、**プロパティ** を選択します。

2.  プロパティ ダイアログボックスで **ブロック解除** を選択し、続いて **適用** を選択し、**OK** をクリックします。

.zip ファイルを解凍すると、解凍したフォルダーに以下が表示されます。

|**フォルダー**  |**説明**  |
|---------|---------|
|**パッケージ**     |  Package Deployer ツールと、環境にソリューションを設定するために後で展開するパッケージが含まれています。 詳細: [オプション C: 展開パッケージからアプリをインストールする](#option-c-install-the-app-from-the-deployment-package)     |
|**Power BI テンプレート**     | レポートの構成に使用する Power BI レポートのテンプレート ファイル (.pbit) が含まれています。 詳細: [ステップ 10: Power BI ダッシュボードを公開する](#step-10-publish-the-power-bi-dashboard)        |

## <a name="step-2-sign-up-for-power-apps-and-create-an-environment"></a>ステップ 2: Power Apps にサインアップして、環境を作成する

Power Apps をまだ持っていない場合は Power Apps にサインアップして適切なライセンスを購入します。

詳細:

-   [Power Apps 価格設定](https://powerapps.microsoft.com/pricing/)
-   [購入Power Apps](https://docs.microsoft.com/power-platform/admin/signup-for-powerapps-admin)

Power Apps を購入後、Common Data Service データベースで環境を作成します。

1.  [Power Platform 管理センター](https://aka.ms/ppac) にサインインします。

2.  データベースで Common Data Service 環境を作成します。 詳細: [環境の作成と管理](https://docs.microsoft.com/power-platform/admin/create-environment)

    > [!IMPORTANT]
    > データベースの作成中に、データベースのセキュリティ グループを選択すると、セキュリティ グループのメンバーであるユーザーと *のみ* アプリを共有できます。

3.  自分の環境に適切なユーザーを作成します。 詳細情報: [ユーザーを作成し、セキュリティ ロールを割り当てる](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles)

## <a name="step-3-install-the-app"></a>ステップ 3: アプリのインストール

以下の手順に従って、Hospital Emergency Response アプリを構成とサンプル データとともにインストールします。

> [!NOTE]
> 
> - 構成とサンプル データは、新規インストールの場合にのみインストールされます。 このアプリを以前に環境にインストールしている場合、既存のデータが上書きされないようにするため、インストール中に構成データとサンプル データはインストールされません。
>
> - 病院から[地域](/powerapps/sample-apps/regional-emergency-response/overview)ソリューションにデータを転送する場合は、ソリューションをインストールする前に[接続の作成](/powerapps/sample-apps/emergency-response-data-transfer#step-1-create-connections)で説明したように、ご利用の環境に接続を作成しておく必要があります。 既成のソリューション [病院から地域へデータを転送する](../emergency-response-data-transfer.md) では、データ転送メカニズムにセキュア ファイル転送プロトコル (SFTP) を使用しています。 

次の 3 つのオプションのいずれかを使用してアプリをインストールできます。

- Microsoft AppSource (Power Apps 米国政府機関のユーザーのみ)。 [オプション A: Microsoft AppSource (US Govt customers) からアプリをインストールする](#option-a-install-the-app-from-microsoft-appsource-us-govt-customers)を参照

- Microsoft AppSource (Power Apps 市販製品のユーザー向け)。 [オプション B: Microsoft AppSource からアプリをインストールする](#option-b-install-the-app-from-microsoft-appsource)を参照

- 以前にダウンロードした展開パッケージ。 [オプション C: 展開パッケージからアプリをインストールする](#option-c-install-the-app-from-the-deployment-package)を参照

### <a name="option-a-install-the-app-from-microsoft-appsource-us-govt-customers"></a>オプション A: Microsoft AppSource (米国政府機関のユーザー) からアプリをインストールする

1.  Power Platform 管理センターにサインインします。 適切な URL を使用してサインインします。
    - **GCC**: [https://gcc.admin.powerplatform.microsoft.us](https://gcc.admin.powerplatform.microsoft.us)
    - **GCC High**: [https://high.admin.powerplatform.microsoft.us](https://high.admin.powerplatform.microsoft.us)

2.  左側のウィンドウで、**環境**を選択し、前の手順で作成した環境の名前を選択します。

3. 環境の詳細ページで、**Dynamics 365 アプリを管理する**を選択します。

    > [!div class="mx-imgBorder"] 
    > ![環境の設定](media/ppac-env-setting.png "環境の設定")

3.  Dynamics 365 アプリ ページで、**アプリをインストールする**を選択します。 次に、右のウィンドウにある **Power Platform 緊急時対応アプリ**を選択し、**次へ**を選択します。

    > [!div class="mx-imgBorder"] 
    > ![アプリのインストール](media/ppac-install-app.png "アプリのインストール")

4.  次のページで、条件に同意し、**インストール**を選択します。

5.  インストールが開始され、Dynamics 365 アプリ ページでアプリのインストールの進行状況を監視できます。

    > [!div class="mx-imgBorder"] 
    > ![アプリのインストール進行状況を監視する](media/ppac-app-install-progress.png "アプリのインストール進行状況を監視する")

    > [!IMPORTANT]
    > アプリのインストールにはしばらく時間がかかる場合があります。

6.  アプリをインストールしたら、[Power Apps](https://make.powerapps.com) に移動し、右上隅から環境を選択します。 **アプリ**に新しいアプリが表示されます。

    > [!div class="mx-imgBorder"] 
    > ![新しいアプリ](media/conf-apps-new-apps.png "新しいアプリ")

    インストールでは、Hospital Emergency Response アプリの構成とサンプル データも追加されます。

### <a name="option-b-install-the-app-from-microsoft-appsource"></a>オプション B: Microsoft AppSource からアプリをインストールする

1.  [AppSource](https://appsource.microsoft.com/)に移動し、「Hospital Emergency Response アプリ」を検索します。<br/>または、このリンクを使用して、直接 AppSource のアプリに移動します: <https://appsource.microsoft.com/product/dynamics-365/mscrm.pphersapp>

2.  Hospital Emergency Response アプリ ページで、**今すぐ入手する**を選択します。

    > [!div class="mx-imgBorder"] 
    > ![AppSource](media/appsource-01.png "AppSource のアプリ")

3.  AppSource 契約条件を確認するように求められます。 ダイアログには、サインインに使用されているアカウントも表示されます。 **続行** を選択します。 資格情報の確認を求められる場合があります。

4.  次のページで、アプリをインストールする環境を選択します。 法的条項とプライバシーに関する声明のチェック ボックスを選択し、**同意する**を選択します。

    > [!div class="mx-imgBorder"] 
    > ![環境を選択する](media/appsource-02.png "環境を選択する")

5.  アプリのインストールの進行状況を監視できる Dynamics 365 管理センターに移動します。

    > [!div class="mx-imgBorder"] 
    > ![AppSource](media/appsource-03.png "アプリのインストール進行状況を監視する")

    > [!IMPORTANT]
    > アプリのインストールにはしばらく時間がかかる場合があります。

6.  アプリをインストールしたら、[Power Apps](https://make.powerapps.com) に移動し、右上隅から環境を選択します。 **アプリ**に新しいアプリが表示されます。

    > [!div class="mx-imgBorder"] 
    > ![新しいアプリ](media/conf-apps-new-apps.png "新しいアプリ")

    インストールでは、Hospital Emergency Response アプリの構成とサンプル データも追加されます。

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

8.  次の画面では、パッケージを環境にインストールできるかどうかを検証します。 **次へ**を選択して、インストールを続行します。

    > [!div class="mx-imgBorder"] 
    > ![環境の検証](media/conf-validate-env.png "環境の検証")

9.  次の画面にパッケージのインストールの状態が表示されます。 インストールが完了したら、**次へ** を選択します。

    > [!div class="mx-imgBorder"] 
    > ![インストールの状態](media/conf-package-install.png "インストールの状態")

    > [!NOTE]
    > パッケージのインストール完了にはしばらく時間がかかる場合があります。 

10.  次の画面で、**完了**を選択して完了し、設定を閉じます。

11.  アプリをインストールしたら、[Power Apps](https://make.powerapps.com) に移動し、右上隅から環境を選択します。 **アプリ**に新しいアプリが表示されます。

        > [!div class="mx-imgBorder"] 
        > ![新しいアプリ](media/conf-apps-new-apps.png "新しいアプリ")

        インストールでは、Hospital Emergency Response アプリの構成とサンプル データも追加されます。

**管理アプリ** を選択して、残りのデプロイ設定を構成できるモデル駆動型アプリを開きます。 管理アプリには、自分の病院システムのデータを追加および管理できるエンティティがいくつかあります。 左側のナビゲーション ウィンドウの下部にあるエリア ピッカーを使用して、別のエリアを選択できます。

> [!div class="mx-imgBorder"] 
> ![管理アプリを開く](media/conf-admin-app-open.png "管理アプリを開く")

## <a name="step-4-update-the-mobile-app-branding-and-tracking-level"></a>ステップ 4: モバイル アプリのブランディングとトラッキング レベルを更新する

モバイル アプリのアプリ アイコン、配色、または表示名を変更して、組織のブランドに合わせることができます。 また、現場の従業員がモバイル アプリを使用して場所または施設の情報を追跡できるように、指定することもできます。 **管理**エリアで**アプリ**および**アプリ構成**エンティティを使用します。

1.  管理アプリを開き、管理アプリの左側のナビゲーション ウィンドウで、エリアピッカーから **管理** を選択し、次に **アプリ** を選択します。

    > [!div class="mx-imgBorder"] 
    > ![管理アプリ](media/conf-admin-app-records.png "管理アプリ")

1.  アプリレコードの1つを選択して開きます。 

    > [!div class="mx-imgBorder"] 
    > ![Power App ID フィールド ](media/conf-powerapp-id-field.png "アプリの更新情報")

1.  アプリの詳細ページ:
 
    1. 組織のブランディングに合わせてアプリのアイコンにカスタム イメージを選択するには、アプリのアイコンをダブルクリックして、任意のアイコン ファイルを選択します。

    3. 必要に応じて、アプリの **説明文** または **表示名** をアップデートします。

    > [!TIP]
    > 別の表示名を選択して、テスト環境でアプリを識別することができます。 例えば : **テスト-ベッドのキャパシティ**などです。

    4. 必要に応じて、アプリをアプリ リストに表示すべき場合は **メニューからアプリを隠す** 値を更新します。 **緊急対応アプリ** はコンテナー アプリですので、この値は規定では **いいえ** に設定します。

    5. 必要に応じて、**アプリ表示ランク** 値をアプリ リストのアプリの表示位置を設定するように更新します。

    6. 必要に応じて、このモバイル アプリのデータを **場所** や **施設** レベルで追跡するかどうかを指定するには、**追跡レベル** フィールドの値を選択してください。 詳細については、[モバイル アプリのトラッキン グレベルを管理する](configure-data-reporting.md#manage-tracking-level-for-mobile-apps) を参照してください

    7. **保存**を選択します。

1.  **アプリ** 下の各キャンバス アプリ レコードに対してステップ 2 と 3 を繰り返します。

1.  左側のウィンドウで、**アプリの構成** を選択します。

1.  **緊急対応アプリ** レコードを選択して、編集のために開きます。

1.  必要に応じて、モバイル アプリの色を更新します。

    > [!TIP]
    > テスト環境のアプリを識別するために、プライマリ カラーを指定するケースが考えられます。

2.  **デバイス共有を有効にする** フィールドで **はい** または **いいえ** を選択して、モバイルアプリで **サインアウト** オプションが利用できるかどうかを指定します。 **はい** を選ぶと **サインアウト** オプションが使用可能になります。 詳細については、ユーザーガイドの [シフト終了 - サインアウト](use.md#end-shift---sign-out) を参照してください。

    > [!div class="mx-imgBorder"] 
    > ![デバイス共有有効化フィールド](media/conf-device-sharing-enabled-field.png "デバイス共有有効化フィールド")

1.  変更を保存するには、画面の右下隅にある **保存** を選択します。

## <a name="step-5-bypass-consent-for-mobile-apps-optional"></a>ステップ 5: モバイル アプリの同意のバイパス (オプション)

必要に応じて、モバイル アプリのユーザーの同意をバイパスするように構成して、ユーザーに位置情報のアクセス許可を許可しないようにすることができます。 このステップを完了するには、テナント管理者である必要があります。 また、このステップを実行する前に、各モバイル アプリ (キャンバス アプリ) のアプリ ID が必要になります。

自分のアプリにアプリ ID を取得するには、管理アプリの左側のナビゲーション ウィンドウで、エリアピッカーから **管理** を選択し、次に **アプリ** を選択します。 これにより、すべてのモバイル アプリ (キャンバス アプリ) が表示されます。 アプリ ID を表示するには、モバイル アプリを選択します 各アプリのアプリ ID をメモ帳ファイルにコピーします。

> [!div class="mx-imgBorder"] 
> ![アプリ ID を取得する](media/conf-admin-get-app-id.png "アプリ ID を取得する")

次に以下のステップを実行します。

1.  メモ帳を開いて、この PowerShell スクリプトをコピーします:

    ```powershell
    # MUST BE A TENANT ADMIN TO RUN THIS
    Install-Module -Name Microsoft.PowerApps.Administration.PowerShell
    Install-Module -Name Microsoft.PowerApps.PowerShell -AllowClobber
    Import-Module -Name Microsoft.PowerApps.Administration.PowerShell
    Import-Module -Name Microsoft.PowerApps.PowerShell
    
    # This call opens prompt to collect credentials 
    # (Azure Active Directory account and password) 
    # used by the commands
    Add-PowerAppsAccount
    
    # Change the App ID for each new app (APPGUIDHERE)
    Set-AdminPowerAppApisToBypassConsent -AppName APPGUIDHERE
    ```

2.  キャンバスアプリの実際のアプリ ID を持つ `APPGUIDHERE` 値を置き替えます。

3.  ファイルを .ps1 ファイル形式で保存します。

4.  管理者として PowerShell を実行し、作成した .ps1 ファイルを実行します。

5.  各キャンバス アプリごとにステップ 2 - 4 を繰り返します。

## <a name="step-6-add-azure-application-insights-key-to-mobile-apps-for-telemetry-optional"></a>手順 6：Azure Application Insights キーをテレメトリ用モバイル アプリのキーに追加する（オプション）

オプションで、Azure Application Insights を使用してモバイル アプリ（キャンバス アプリ）の詳細なテレメトリを収集し、アプリの使用状況についての分析情報を得ることができます。 この詳細については、[Application Insights を使用してアプリのテレメトリを分析する](https://docs.microsoft.com/powerapps/maker/canvas-apps/application-insights) を参照してください

## <a name="step-7-share-canvas-apps-with-users-in-your-organization"></a>ステップ 7: 組織内のユーザーとキャンバス アプリを共有する

最前線にいるユーザーがモバイル デバイスのキャンバス アプリを使用してデータを使用するには、アプリが共有されていなければなりません。 Azure AD グループを使用すると、ユーザーのグループとアプリをより簡単に共有できます。

> [!IMPORTANT]
> アプリを共有する予定のユーザーまたはグループが *既に* 自分の環境へのアクセスができていることを確認してください。 通常、[環境を設定する](#step-2-sign-up-for-power-apps-and-create-an-environment) 間には、ユーザーまたはグループはすでに追加されています。 または、こちらのステップに従ってユーザーを環境に追加し、アプリをユーザーと共有する前に適切なアクセスを提供できます: [ユーザーを作成してセキュリティ ロールを割り当てる](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles)。

1.  [Power Apps](https://make.powerapps.com) へのサインイン

2.  左側のナビゲーション ウィンドウで **アプリ** を選択して、すべてのアプリのリストを表示します。

3.  モバイル アプリ (キャンバス アプリ) を選択し、バナーの **共有** を選択します。

    > [!div class="mx-imgBorder"] 
    > ![キャンバス アプリを共有する](media/conf-share-canvas-apps.png "キャンバス アプリを共有する")

4.  このアプリを共有する Azure AD グループまたはユーザーを指定します。 アプリが Common Data Service データに接続するので、エンティティへのアクセス許可も提供する必要もあります。 共有パネルでは、エンティティのセキュリティを管理するように求められます。 **緊急対応ユーザー** と **Common Data Service ユーザー** のセキュリティ ロールをこのアプリを使用してエンティティに割り当て、**共有** を選択します。

    > [!div class="mx-imgBorder"] 
    > ![アプリを Azure AD グループまたはユーザーと共有する](media/conf-share-app-groups-users.png "アプリを Azure AD グループやユーザーと共有する")

5.  各モバイル アプリごとにステップ 3 と 4 を繰り返します。

アプリの共有に関する詳細情報: [キャンバス アプリを共有する](https://docs.microsoft.com/powerapps/maker/canvas-apps/share-app)

## <a name="step-8-set-your-mobile-app-as-hero-and-featured-app-optional"></a>ステップ 8: モバイル アプリをヒーローおよびおすすめアプリとして設定する (オプション)

オプションで、モバイル アプリをヒーローとして設定し、**Power Apps** モバイル アプリ内でおすすめアプリにすることができます。 このステップを完了するには、テナント管理者である必要があります。

このステップを実行する前に、ヒーローおよびおすすめアプリとして設定する各モバイル アプリ (キャンバス アプリ) のアプリ ID が必要です。 キャンバス アプリのアプリ ID を取得する方法については、次を参照してください 

次に以下を実行します。

1.  メモ帳を開いて、この PowerShell スクリプトをコピーします:


    ```powershell
    # MUST BE A TENANT ADMIN TO RUN THIS
    Install-Module -Name Microsoft.PowerApps.Administration.PowerShell
    Install-Module -Name Microsoft.PowerApps.PowerShell -AllowClobber
    Import-Module -Name Microsoft.PowerApps.Administration.PowerShell
    Import-Module -Name Microsoft.PowerApps.PowerShell

    # This call opens prompt to collect credentials 
    # (Azure Active Directory account and password) 
    # used by the commands
    Add-PowerAppsAccount

    # Use the "Emergency Response App" App ID
    # To clear a featured app use Clear-AdminPowerAppAsFeatured

    #Change the App ID for each new app (APPGUIDHERE)
    Set-AdminPowerAppAsFeatured -AppName APPGUIDHERE

    # To clear a hero app use Clear-AdminPowerAppAsHero
    # Change the App ID for each new app (APPGUIDHERE)
    Set-AdminPowerAppAsHero -AppName APPGUIDHERE
    ```

2.  スクリプトの `APPGUIDHERE` 値を、それぞれお薦めやヒーローとして設定するアプリの実際のアプリ ID と置き換えます。

3.  ファイルを .ps ファイルとして保存します。

4.  管理者として PowerShell を実行し、今作成した .ps ファイルを実行します。
 

## <a name="step-9-share-model-driven-app-with-admins-in-your-organization"></a>ステップ 9: モデル駆動型アプリを組織の管理者と共有する

管理ユーザーが管理アプリ (モデル駆動型アプリ) を使用するには、それを管理者と共有する必要があります。 Azure AD グループを使用すると、管理ユーザーのグループとアプリをより簡単に共有できます。

> [!IMPORTANT]
> アプリを共有する予定のユーザーまたはグループが *既に* 環境へのアクセスができていることを確認してください。 通常、[環境を設定する](#step-2-sign-up-for-power-apps-and-create-an-environment) 間には、ユーザーまたはグループはすでに追加されています。 または、こちらのステップに従ってユーザーを環境に追加し、アプリをユーザーと共有する前に適切なアクセスを提供できます: [ユーザーを作成してセキュリティ ロールを割り当てる](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles)。

1. [Power Apps](https://make.powerapps.com) にサインインします。

2. 左側のナビゲーション ウィンドウで、アプリ を選択してすべてのアプリのリストを表示します。

3. モデル駆動型アプリ (**管理アプリ – 緊急対応アプリ**) を選択して、バナーで **共有** を選択します。

4. このアプリを共有する Azure AD グループまたは管理ユーザーを指定して、**緊急対応管理者** セキュリティ ロールを割り当て、**共有** を選択します。

## <a name="step-10-publish-the-power-bi-dashboard"></a>ステップ 10: Power BI ダッシュボードを公開する

Power BI ダッシュボードを公開し、組織内のユーザーと共有することで、インサイトと意思決定のためにダッシュボードを使用できます。

Power BI ダッシュボードを公開するには、次のいずれかのオプションを使用てください：AppSource のテンプレートアプリを使用する、*または* デプロイメント パッケージで利用可能な **.pbit** ファイルを使用します。

### <a name="option-a-publish-using-the-template-app-from-appsource-preferred-option"></a>オプション A：AppSource のテンプレートアプリを使用して公開する（推奨オプション）

AppSource のテンプレート アプリの使用に関する詳細情報は、[病院の緊急対応意思決定サポート ダッシュボードに接続する](https://docs.microsoft.com/power-bi/connect-data/service-connect-to-health-emergency-response) を参照してください。

> [!IMPORTANT]
> これは、.pbit ファイルのオプションを使用して公開するよりも、 Power BI のダッシュボードを簡単に公開することができます。 .pbit ファイルのオプションを使用して発行するよりも、このオプションの使用を推奨しています。 

### <a name="option-b-publish-using-the-pbit-file-in-the-deployment-package"></a>オプションB：展開パッケージの .pbit ファイルを使用して公開する

このセクションでは、展開パッケージで利用可能な**緊急時対応アプリ .pbit** ファイルを使用してダッシュボードを公開する方法について説明します。

#### <a name="prerequisites"></a>前提条件

- <https://aka.ms/emergency-response-solution> から展開パッケージ (.zip file) をダウンロードします。 ダウンロード後、.zip ファイルをコンピューターに解凍します。 .pbit ファイルは P**ower BI テンプレート** フォルダーにあります

- レポートにアクセスするユーザーに割り当てられる Power BI Premium 容量または Power BI Pro ライセンス。 

- レポートを公開する Power BI でワークスペースを作成します。 Power BI にサインインして、ワークスペースを作成します。 詳細: [Power BI で新しいワークスペースを作成する](https://docs.microsoft.com/power-bi/service-create-the-new-workspaces)

- Windows の App Store: <https://aka.ms/pbidesktop> からの Power BI Desktop のインストール

   > [!NOTE] 
   > 既にダウンロード センターのページから実行ファイルとして直接ダウンロードし、 Power BI Desktop をインストールしていた場合は、削除して Microsoft Store のものを使用してください。 Microsoft Store のバージョンは、バージョンは新しいリリースがされると自動的に更新されます。
   >
   > Microsoft Store からインストールできない場合は、[ダウンロード センター ページ](https://www.microsoft.com/download/details.aspx?id=58494) から Microsoft Store 以外の最新バージョンをインストールしてください。

- App Store から Power BI Desktop をインストールし、実行し、組織内で Power BI アプリを公開するための権限を持つアカウントを使用してログインします。

#### <a name="publish-the-dashboard-using-the-pbit-file"></a>.pbit ファイルを使用してダッシュボードを公開する

1. デプロイ パッケージを抽出する場所に移動します。 **Power BI テンプレート** フォルダー下に **緊急時対応アプリ.pbit** ファイルがあります。

2. Power BI Desktop で **緊急時対応アプリ.pbit** ファイルを開きます。 次の値を入力するように求められます。

    - **組織名**: 各レポート ページの左上隅に表示される組織名を入力します。
        > [!TIP]
        > テスト環境で Power BI ダッシュボードを識別するには、**Organization_name** に別の値を指定した方が分かりやすい場合もあります。 例えば、**Contoso テスト システム**と入力します。

    - **CDS_base_solution_URL**: Common Data Service 環境インスタンスの URL を入力します。 例: https://*[myenv]*.crm.dynamics.com

    > [!div class="mx-imgBorder"]
    > ![組織名とベースURLを指定する](media/pbi-pub-rep1.png)

    **読み込み** を選択します。

3. Common Data Service 環境に接続するための資格情報を入力するように求められます。 **組織アカウント** > **サインイン** を選択して、自分の Common Data Service 資格情報を指定します。  

    > [!div class="mx-imgBorder"]
    > ![select-organizational-account](media/select-organizational-account.png)

4. サインイン後、**接続** を選択して、Common Data Service のデータに接続します。

5. 接続に成功すると、データが Power BI レポートに表示されます。 保留中の変更をクエリに適用するように求められ、**変更を適用** を選択します。

6. **公開** を選択してデータを自分の Power BI ワークスペースに公開します。 変更を保存するように求められますので **保存** を選択します。

    > [!div class="mx-imgBorder"]
    > ![select-refresh-publish](media/select-refresh-publish.png)

7. ファイルを Common Data Service 環境情報とともに、 .pbix ファイルとして保存するように求められます。 名前を入力して、コンピューターに保存します。

8. .pbix ファイルを保存すると、レポートを公開するように求められます。 **Power BI** へ公開ページで、公開するワークスペースを選択して **選択する** をクリックします。

12. レポートがワークスペースで使用可能になります。 次に、データセットのデータ更新設定を構成します。 ワークスペースでデータセットを選択し **更新のスケジュール** アイコンを選択します。  
    
    > [!div class="mx-imgBorder"]
    > ![schedule-refresh](media/schedule-refresh.png)

13. データ更新設定を初めて設定しようとすると、**設定** ページに認証情報が無効であることを示すメッセージが表示されます。 **データ ソース資格情報** から **資格情報を編集する** を選択して、自分の資格情報を指定します。  

    > [!div class="mx-imgBorder"]
    > ![select-edit-credentials](media/select-edit-credentials.png)

14. 次の画面で次の操作を行います。
    - **認証方法** を **OAuth2** として選択します。
    - **このデータ ソースのプライバシー レベルの設定** を **組織的** として設定します。
    - **サインイン**を選択します。

    資格情報を指定してサインインするように求められます。 サインインに成功すると **設定** ページに戻ります。

15. **設定** ページで **スケジュールされた更新** を展開して、スケジュールに基づいてデータを更新するために必要な詳細を指定します。 **適用**を選択します。

    > [!div class="mx-imgBorder"]
    > ![スケジュールされた更新](media/refresh-schedule.png)

    > [!NOTE] 
    > データを更新できる回数には制限があります。 Power BI は共有容量のデータセットを 1 日 8 回の更新に制限します。 データセットが Premium 容量にある場合、データセット設定で 1 日あたり最大 48 回の更新をスケジュールできます。 詳細: [データを差真の状態に更新](https://docs.microsoft.com/power-bi/refresh-data#data-refresh)

16. 左側のウィンドウでワークスペース名を選択し、次に右上隅にある **アプリを作成** を選択します。  

    > [!div class="mx-imgBorder"]
    > ![select-create-app](media/select-create-app.png)

17. アプリ公開ページで次のことをおこないます。

    1. **セットアップ** タブで、アプリの名前と説明を指定します。

    2. **ナビゲーション** タブで、ダッシュボードを公開する場所を指定します。

    3. **許可** タブで、このアプリを表示できるユーザーまたはグループを指定します。 エンドユーザー向けにこのアプリを自動的にインストールするために **このアプリを自動的にインストール** チェックボックスをオンにします。 詳細: [エンドユーザー向けのアプリを自動的にインストールする](https://docs.microsoft.com/power-bi/service-create-distribute-apps#automatically-install-apps-for-end-users)  

        > [!div class="mx-imgBorder"]
        > ![select-install-apps-automatically](media/select-install-apps-automatically.png)

18. **アプリの公開** を選択します。 Power BI でのアプリの公開についての詳細は [アプリの公開](https://docs.microsoft.com/power-bi/service-create-distribute-apps#publish-your-app) を参照してください。

### <a name="after-publishing-the-dashboard"></a>ダッシュボードの公開後

公開された Power BI ダッシュボードを表示するには、[Power BI のダッシュボードを表示する](configure-data-reporting.md#view-power-bi-dashboard) を参照してください

## <a name="step-11-enable-flows-for-populating-cdc-data"></a>手順 11 : CDC データを取り込むのフローを有効化する

疾病予防管理センター (CDC) が各病院に報告を要求している形式で、ソリューション内のさまざまなソースからのデータの照合に役立つ次のフローを有効にする必要があります :

- CDC データの入力 - 医療スタッフ
- CDC データの入力 - 医療消耗品
- CDC データの入力 - 患者および病院のキャパシティ

1.  [Power Automate](https://flow.microsoft.com/) にサインインする。

2.  左側のウィンドウで、**ソリューション**を選択します。 ソリューションのリストから、**地域の緊急時対応ソリューション**を選択し、ソリューションを開きます。

3.  ソリューションでは、**フロー**でフィルター処理し、すべてのフローを検索します。

    > [!div class="mx-imgBorder"]
    > ![すべてのフロー](media/all-flows.png)

4.  フロー名を選択してフロー定義を開きます。 例えば、**CDC データの入力 - 医療スタッフ** です。

5.  ツールバーで **編集** を選択し、接続情報を確認します。  

6. **保存**を選択して変更の保存を行い、**有効にする**を選択します。

7. 次の各フローで手順 4 から 6 を実行して接続を承認し、フローを検証します。

    - CDC データの入力 - 医療消耗品
    - CDC データの入力 - 患者および病院のキャパシティ

## <a name="issues-and-feedback"></a>問題とフィードバック

- 病院緊急時対応サンプル アプリに関する問題を報告するには、<https://aka.ms/emergency-response-issues> にアクセスしてください。

- 病院緊急時対応サンプル アプリに関するフィードバックについては、<https://aka.ms/emergency-response-feedback> にアクセスしてください。

## <a name="next-step"></a>次のステップ

[データを構成してレポートを表示する](configure-data-reporting.md)
