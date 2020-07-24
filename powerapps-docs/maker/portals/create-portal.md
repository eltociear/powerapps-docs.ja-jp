---
title: Power Apps でポータルの作成 | Microsoft Docs
description: Power Apps のポータルを作成するための手順。
author: neerajnandwana-msft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 02/07/2020
ms.author: nenandw
ms.reviewer: tapanm
ms.openlocfilehash: fdc81c20e17b2d45c19784af2023e1f2725b1dc9
ms.sourcegitcommit: 2fd873a1ea17f419f6194714efffa47a9bd00c2e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "3507587"
---
# <a name="create-a-common-data-service-starter-portal"></a>Common Data Service スターター ポータルの作成

Power Apps でポータルを構築する機能を使用すると、外部および内部ユーザー用のWeb サイトを作成して、 Common Data Service に保存されたデータを操作することができます 。

これらは、ポータルを作成する利点です:

- データは Common Data Serviceに格納されているため、 SharePoint や Dynamics 365 や Salesforce のモデル駆動型アプリケーションのように Power Apps から接続を作成する必要はありません。 ポータルで表示または管理するエンティティを指定するだけです。

- WYSIWYG Power Apps ポータルスタジオ を使用してポータルを設計するには、Webページにコンポーネントを追加して構成します。

新しい環境または既存の環境でポータルを作成できます。

**新しい環境を作成します** リンクを使用して、新しい環境でポータルを作成することを選択した場合、エンティティ、データ、スターター ポータル テンプレートなどの必須ポータルの前提条件が、環境の作成時に、インストールされます。 この方法では、ポータルは数分でプロビジョニングされます。

ポータルの前提条件がない既存の環境でポータルを作成する場合は、前提条件が最初にインストールされてから、ポータルが作成されます。 この方法では、ポータルのプロビジョニングに時間がかかることがあり、ポータルがプロビジョニングされると通知を受け取ります。

Power Apps での指定環境に基づいて、Common Data Service スターター ポータルまたは Dynamics 365 のモデル駆動型のアプリ含む環境のポータルを作成できます。

> [!NOTE]
> ポータルを作成すると、いくつかの ソリューション が インストール され、サンプルデータ が インポート されます。

環境に関する作業の詳細: [環境と Microsoft Power Apps に関する作業](https://docs.microsoft.com/powerapps/maker/canvas-apps/working-with-environments)

使用可能なポータル テンプレートの詳細: [ポータル テンプレート](portal-templates.md)

ポータルを作成するには:

1.  [Power Apps](https://make.powerapps.com) にサインインします。  

2.  **自分のアプリを作成する** 配下の **空のポータル** を選択します。

3.  選択した環境にポータルの前提条件が含まれていない場合は、 **空のポータル** ウィンドウにメッセージが表示され、別の環境を選択するか、新しい環境を作成するように指示されます。

    > [!div class=mx-imgBorder]
    > ![新しい環境メッセージの作成](media/create-portal-message.png "新規環境のメッセージを作成")

4.  現在の環境で続行することを選択した場合、次の手順で説明するように、ウィンドウに必要な情報を入力します。 新しい環境を作成するを選択する場合、 [新しい環境の作成](#create-new-environment) を参照してください。

5.  **空のポータル** ウィンドウで、ポータルの名前およびWeb サイトのアドレスを入力し、ドロップダウン リストから言語を選択します。 完了したら、 **作成** を選択します。

    > [!TIP]
    > 別の言語を使用してポータルを作成するには、最初に [環境で言語を有効にする](https://docs.microsoft.com/power-platform/admin/enable-languages#enable-the-language) 必要があります。その後、言語ドロップ ダウンリストで使用できるようになります。

    > [!div class=mx-imgBorder]
    > ![新しいポータルの作成](media/create-new-portal.png "新規ポータルの作成")  

**作成** を選択した後、ポータルはプロビジョニングを開始し、プロビジョニングの状態が [通知](#portal-provisioning-notifications) によって表示されます。

ポータルの前提条件がインストールされていない環境でポータルを作成した場合、プロビジョニングの状態もグリッドに表示されます:

> [!div class=mx-imgBorder]
> ![グリッドの通知](media/provision-progress-notif.png "グリッドの通知")

ポータルが正常にプロビジョニングされると、状態は更新され、ポータルはグリッドで表示されます:

> [!div class=mx-imgBorder]
> ![プロビジョニングされているポータル](media/recent-apps.png "プロビジョニングされているポータル")

Power Apps ポータルスタジオ で ポータルを編集するには、 [ポータルの編集](manage-existing-portals.md#edit) を参照してください。

> [!NOTE]
> - ひとつの環境で作成されたひとつの言語に対して、各タイプのポータルをひとつだけ作成できます。
> - ポータルをプロビジョニングする十分な特権がない場合は、エラーが表示されます。 ポータルを作成するには、 Common Data Service のシステム管理者の役割が必要です。 ユーザー レコードの **クライアント アクセス ライセンス (CAL) 情報** で **アクセス モード** を **読み取り/書き込み** に設定する必要があります。
> - 古いポータルアドオンを購入し、そのアドオンを使用してポータルをプロビジョニングする場合は、**Dynamics 365管理センター**ページに移動する必要があります。 詳細については次を参照してください: [古いポータル アドオンを使用してポータルをプロビジョニングする](provision-portal-add-on.md)
> - 古いポータル アドオンを使用したポータルをプロビジョニングする場合は、 [make.powerapps.com](https://make.powerapps.com) にてカスタマイズ、管理することができます。
> - [make.powerapps.com](https://make.powerapps.com) からのポータルをプロビジョニングすると、古いポータル アドオンを使用しません。 また、これらのポータルは、 **Dynamics 365管理センター** ページの **アプリケーション** タブ配下には表示されません。
> - Common Data Service スターター ポータルは、 **Dynamics 365管理センター** ページから作成することはできません
> - Power Apps ポータルはフランス地域では使用できません。

## <a name="create-new-environment"></a>新しい環境の作成

**空のポータル** ウィンドウに用意されているオプションを使用して環境を作成する場合は、次の手順に従ってください。

1.  **新しい環境** ウィンドウで、環境の名前を入力し、ドロップダウン リストのリージョンと環境の種類を選択します。 環境の作成後に、リージョンを変更することはできません。 終了したら、 **環境の作成** を選択します。

    > [!div class=mx-imgBorder]
    > ![新規環境を作成する](media/create-new-environment.png "新しい環境の作成")  

2.  環境が作成されると、ダイアログ ボックスに確認メッセージが表示され、データベースを作成するよう求められます。 **データベースの作成** を選択して、 Common Data Service へのアクセスを有効にします。

    > [!NOTE]
    > データベースを作成するためのプロンプトが自動的に表示されない場合があります。 この場合、新しい環境に移動し、再度、 **空のポータル** タイルを選択する必要があります。

    > [!div class=mx-imgBorder]
    > ![作成された新規の環境](media/new-environment-created.png "作成された新規環境")  

3.  データベースに保存されたデータの通貨と言語を選択します。 データベースが作成されると、通貨や言語を変更できません。 終了したら、 **データベースの作成** を選択します。 データベースはスターター ポータルで作成されます。これにより、ポータルがプロビジョニングされるとサンプル コンテンツをすぐに開始できます。

    > [!NOTE]
    > **スターター ポータルを含める** オプションは、 オプションは、 **空のポータル** ウィンドウのオプションを使用して環境を作成する場合にのみ使用できます。 このオプションは、 Power Apps 管理センターから環境を作成する場合、利用できません。

    > [!div class=mx-imgBorder]
    > ![新規データベースを作成する](media/create-new-database.png "新規データベースを作成する") 

    Common Data Service にデータベースを作成するには、数分かかる場合があります。 データベースを作成した後は、新しい環境は、 Power Apps ホーム ページの環境リストでが選択され、ポータル管理 アプリが作成されます。 このアプリは、は実際のポータルではなく、事前の設定アクティビティを実行できる、モデル駆動のコンパニオン アプリです。 外部接続型Web サイトをデザインするためのポータルの作成に進むことができます。

    > [!div class=mx-imgBorder]
    > ![ポータル管理アプリ](media/portal-mgmt-app.png "ポータル管理アプリ")

4. 環境とデータベースの作成後、 **自分のアプリを作成する** の **空のポータル** を選択します。 

    > [!NOTE]
    > データベースが作成後も、データベース作成の確認画面が引き続き表示される場合は、 **空のポータル** タイルを選択する前に、 Power Apps ホーム ページを更新する必要があります。


## <a name="portal-provisioning-notifications"></a>ポータル プロビジョニング 通知

**作成** を選択した後、ポータルはプロビジョニングを開始し、プロビジョニングの状態が通知によって表示されます。

**トーストとして通知**

次の通知は、ポータルをプロビジョニングするために **作成** を選択したときに表示されます。

> [!div class=mx-imgBorder]
> ![トーストの通知](media/toast-notif.png "トーストの通知") 

**通知ウィンドウの通知**

プロビジョニング要求が正常に配置されると、次の通知が **通知** ウィンドウに表示されます。

進行中のプロビジョニングに対して表示される通知

> [!div class=mx-imgBorder]
> ![ウィンドウの通知](media/pane-notif.png "ウィンドウの通知") 

正常完了したプロビジョニングに対して表示される通知

> [!div class=mx-imgBorder]
> ![成功通知のプロビジョニング](media/provision-complete-notif.png "成功通知のプロビジョニング") 

ポータル プロビジョニングが失敗した場合は、同様に通知が表示されます。
  
**電子メールを介した通知**

プロビジョニング要求が正常に送信されると、ポータルを作成するユーザーに確認の電子メール通知が送信されます。 また、ポータルのプロビジョニングが完了した後でユーザーに電子メールが送信されます。

## <a name="disable-portal-creation-in-a-tenant"></a>テナントでポータル作成の無効化

全体管理者として、管理者以外のユーザーがテナントでポータルの作成をできないようにするには、PowerShellで `disablePortalsCreationByNonAdminUsers` のテナント レベル設定を有効にすること実行できます。 PowerShell コマンドレットを実行するには、最初に、必須モジュールをインストールする必要があります。 必須 PowerShell モジュールのインストールについては、 [インストール](https://docs.microsoft.com/power-platform/admin/powerapps-powershell#installation) を参照してください。

モジュールをインストールしたら、PowerShell ウィンドウで次のコマンドを実行します (PowerShellを管理者として実行)。

```
Set-TenantSettings -RequestBody @{ "disablePortalsCreationByNonAdminUsers" = $true }
```

管理者は、次の Azure ロールの 1 つを持つユーザーです:

-  グローバル管理者
- Dynamics 365 サービス管理者
- Power Platform サービス管理者

前述 Azure ロールのいずれにも持っていないユーザーは、管理者以外のユーザーと見なされます。

ポータルの作成がテナントで無効とされると、管理者以外のユーザーには、次のエラーが表示されます:

> [!div class=mx-imgBorder]
> ![ポータル作成ブロックエラー](media/portal-create-blocked-error.png "ポータル作成ブロックエラー")
