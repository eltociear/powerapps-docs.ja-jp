---
title: 高等教育機関の財務危機影響度追跡をデプロイする - サンプル ソリューション | Microsoft Docs
description: 高等教育機関の財務危機影響度追跡をデプロイする - サンプル ソリューション。
author: ramanasridhar
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 06/22/2020
ms.author: ramanasr
ms.reviewer: nkrb
ms.openlocfilehash: a3199d27bbe8c99c359050f685e5128605f9748b
ms.sourcegitcommit: bd543dccaa38bd63ad576f408c8b669c7e653ca3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/24/2020
ms.locfileid: "3500793"
---
# <a name="deploy-the-higher-education-crisis-financial-impact-tracker-app"></a>高等教育機関の財務危機影響度追跡アプリをデプロイする

高等教育機関の財務危機影響度追跡アプリは、最低限の設定だけでニーズに適応させることができます。 この記事では、大学の IT 管理者が自身の所属する組織でアプリケーションをデプロイして構成するための詳細な手順について説明します。

ソリューションのダウンロード、またはデプロイ方法に関する概要のビデオを参照するか、この記事に記載の手順に従ってください。 これら手順の推定完了時間 : **30 - 35 分**

## <a name="demo-quick-overview-of-how-to-download-and-deploy-the-solution"></a>デモ : ソリューションのダウンロードおよびデプロイ方法の概要

ソリューションのダウンロードおよびデプロイ方法の簡単な概要を説明します。

<br/>

> [!VIDEO https://www.youtube.com/embed/IZhgSWfRh4g]

## <a name="step-1-download-the-deployment-package"></a>ステップ 1: デプロイ パッケージのダウンロード

[こちら](https://aka.ms/HECFIT)から最新のデプロイ パッケージ (.zip) をダウンロードします。 .zip ファイルを解凍する前に、ファイルのブロックを解除してください。 

.zipファイルのブロック解除方法 :

- zip ファイルを右クリックし、**プロパティ**を選択します。

- **プロパティ** ダイアログ ボックスで**ブロック解除**を選択し、**適用** を選択してから、**OK** をクリックします。

.zipファイルを解凍すると、解凍されたフォルダーに以下のコンポーネントが表示されます。

|コンポーネント| ファイル名 |内容
|-------|-------|------|
| AppIcons | 高等教育機関の財務危機影響度追跡.png| サンプル アプリ アイコン。|
| データ​​|インポート テンプレート  | .xlsx (Excel) 形式のデータ ロード ファイルに使用する個別のエンティティ テンプレート。 ファイルは、インポートする順序で配置されています。|
| データ​​|サンプル データ  | .xlsx (Excel) 形式の個別のエンティティ サンプル データ。 ファイルは、インポートする順序で配置されています。|
| パッケージ |高等教育機関の財務危機影響度追跡アプリ パッケージに関連するファイル。|アプリのデプロイに必要なファイルの完全なリスト。|
| Power BI テンプレート | PBITemplate.pbix | アプリの Common Data Service インスタンスへの接続に使用するサンプル Power BI テンプレート。|

## <a name="step-2-sign-up-for-power-apps-and-create-an-environment"></a>手順 2 : Power Apps にサインアップして、環境を作成する

Power Apps をまだご利用でない場合は、[Power Apps](https://docs.microsoft.com/power-platform/admin/signup-for-powerapps-admin) にサイン アップし、適切なライセンスを購入します。 詳細: [Power Apps の価格](https://powerapps.microsoft.com/pricing/)

Power Apps の購入後、Common Data Service データベースを使用して環境を作成します。

1. [Power Platform 管理センター](https://aka.ms/ppac) にサインインします。

1. データベースを使用して Common Data Service 環境を作成します。 詳細: [環境の作成と管理](https://docs.microsoft.com/power-platform/admin/create-environment)

    > [!IMPORTANT]
    > データベースを作成する際にセキュリティ グループを選択した場合、このセキュリティ グループのメンバーのみがアプリ共有できることに留意してください。

1. ユーザーを作成して適切なセキュリティ ロールを割り当てます。 詳細情報: [ユーザーを作成し、セキュリティ ロールを割り当てる](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles)

## <a name="step-3-install-the-app"></a>ステップ 3: アプリのインストール

以下の手順に従って、高等教育機関の財務危機影響度追跡アプリをインストールして構成します。

### <a name="install-the-app-from-the-deployment-package"></a>デプロイ パッケージからアプリをインストールする

1. デプロイ パッケージ (.zipファイル) を解凍したフォルダーに移動します。 **パッケージ**フォルダが表示されます。 **パッケージ**フォルダを開き、**PackageDeployer.exe** をダブルクリックして選択します。

1. 次の画面で**続行**を選択します。

1. 環境への接続を求められます。 **デプロイ タイプ**に **Office 365** を選択し、**詳細を表示する**を選択します。続いて、資格情報を入力して環境に接続します。

   > [!div class="mx-imgBorder"]
   > ![Package Deployer](./media/package-deployer-connection-details-pane.png "Package Deployer")

1. **ログイン**を選択し続行します。

1. 単数の Common Data Service 環境以上にアクセスできる場合、次の画面で、利用可能な環境のリストからパッケージをインストールする環境を選択するよう促されます。 対象の環境を選択し、**ログイン** を選択します。

    > [!div class="mx-imgBorder"]
    > ![組織の一覧](./media/list-of-organizations-available.png "組織の一覧")

1. 次の画面で**次へ**を選択します。

1. 次の画面で、パッケージがインストールされている環境の名称が表示されます。 情報を確認し、 **次へ** を選択します。

1. 次の画面で、パッケージを環境にインストールできるかどうかを検証します。 **次へ**を選択して、インストールを続行します。

   > [!div class="mx-imgBorder"]
   > ![構成の読み取り](./media/reading-installer-configuration.png "構成の読み取り")

1. 次の画面にパッケージのインストールの状態が表示されます。 インストールが完了したら、**次へ** を選択します。

   > [!div class="mx-imgBorder"]
   > ![アクションの実行](./media/execute-install-actions.png "アクションの実行")

   > [!div class="mx-imgBorder"]
   > ![ファイルのインポート](./media/importing-files.png "ファイルのインポート")

   > [!NOTE]
   >  パッケージのインストールには数分間かかる場合があります。

1. 次の画面で、**完了**を選択して完了し、設定を閉じます。

1. アプリのインストール後は、[Power Apps](https://make.powerapps.com/)にアクセスし、右上隅から環境を選択します。 **アプリ**配下にに新しいアプリが表示されます。

   > [!div class="mx-imgBorder"]
   > ![アプリの選択](./media/select-app-from-list-of-apps.png "アプリの選択")

このインストールでは、高等教育機関の財務危機影響度追跡アプリの構成データも追加されます。

**高等教育機関の財務危機影響度追跡アプリ**を選択し、モデル駆動型アプリを開いて、残りのデプロイ設定を構成します。 このアプリには、大学システムのデータ追加、および管理できるエンティティがいくつか存在します。 左側のナビゲーション ペインの下部にある領域ピッカーを使用して、別のエリアを選択することができます。

## <a name="step-4-update-the-app-branding-and-tracking-level"></a>手順4 : アプリのブランディングと追跡レベルを更新する

アプリのアイコン、配色、表示名は組織のブランドに合わせて変更することができます。 **管理**エリアで**アプリ構成**のエンティティを使用します。

1. Admin App を開き、左側のペインの領域ピッカーで **管理** を選択して、**アプリの構成** を選択します。 これは、**AppConfig.xlsx**ファイルからインポートしたすべてのレコードを表示します。

   > [!div class="mx-imgBorder"]
   > ![アプリの構成レコード](./media/select-app-config-record.png "アプリの構成レコード")

1. **高等教育機関の財務危機影響度追跡** レコードを選択します。

    > [!div class="mx-imgBorder"]
    > ![レコードの選択](./media/cfit-app-config-record.png "レコードの選択")

1. アプリの詳細ページで、以下の操作を行います :

   - アプリのアイコンをダブルクリックして、**AppIcons** フォルダーからアプリのアイコン ファイルを選択します。 画像ファイルには直感的に名前が付けられるため、正しいアイコンを簡単に選択できます。 たとえば、**高等教育機関の財務危機影響度追跡**の `Higher Education Crisis Financial Impact Tracker.png` ファイルを選択します。 また、組織のブランディングに合わせてカスタム イメージを選択することができます。

   - 必要に応じて、**アプリ名**を変更します。

   - 必要に応じて、アプリの**プライマリとセカンダリ カラー**の値を更新して、アプリ一覧でアプリの表示色を設定します。

   - 必要に応じて、初期サイン イン時にユーザーに表示する HTML 形式のウェルカム メッセージを更新します。

1. **保存**を選択します。

## <a name="step-5-share-canvas-apps-with-the-users-in-your-organization"></a>手順 5: 組織内のユーザーとキャンバス アプリを共有する

現場のユーザーがモバイル デバイスのキャンバス アプリでデータを使用するには、アプリがユーザーと共有されている必要があります。 ユーザーのグループでアプリを共有すには、Azure Active Directory (Azure AD) グループを使用するのが最も簡単です。

1. [Power Apps](https://make.powerapps.com/) にサインインします。

1. 左側のナビゲーション ペインで **アプリ** を選択して、すべてのアプリの一覧を表示します。

1. 対象のアプリを選択し、**共有** を選択します。

   > [!div class="mx-imgBorder"]
   > ![アプリの共有](./media/share-app.png "アプリの共有")

1. このアプリを共有する Azure AD グループまたはユーザーを指定します。 アプリが Common Data Service データに接続するため、エンティティへのアクセス許可を提供する必要があります。 共有パネルでは、エンティティのセキュリティを管理するように求められます。 このアプリで使用される **高等教育機関の財務危機影響度追跡ユーザー** および **Common Data Serviceユーザー** セキュリティ ロールをエンティティに割り当て、続いて**共有**を選択します。

   > [!div class="mx-imgBorder"]   
   > ![ロールの割り当て](./media/assign-roles.png "ロールの割り当て")

## <a name="step-6-share-the-model-driven-app-with-admins-in-your-organization"></a>手順 6 : 組織内の管理者とモデル駆動型アプリを共有する

管理者ユーザーが管理アプリ (モデル駆動型アプリ) を使用できるようにするには、アプリを管理者ユーザーと共有する必要があります。 管理者ユーザーのグループでアプリを共有すには、 Azure AD グループを使用するのが最も簡単です。

1. [Power Apps](https://make.powerapps.com/) にサインインします。

2. 左側のペインで **アプリ** を選択して、すべてのアプリの一覧を表示します。

3. モデル駆動型アプリ**高等教育機関の財務危機影響度追跡アプリ**を選択し、続いてバナーで**共有**を選択します。

4. このアプリを共有する Azure AD グループ、または管理者ユーザーを指定し、**高等教育機関の財務危機影響度追跡アプリ ユーザー**のセキュリティ ロールを割り当て、続いて**共有**を選択します。

## <a name="issues-and-feedback"></a>問題とフィードバック 

- Higher Education Crisis Financial Impact Tracker アプリの問題を報告するには、<https://aka.ms/crisis-financial-impact-tracker-issues> にアクセスしてください。
- Higher Education Crisis Financial Impact Tracker アプリに関するフィードバックについては、<https://aka.ms/crisis-financial-impact-tracker-feedback> にアクセスしてください。

