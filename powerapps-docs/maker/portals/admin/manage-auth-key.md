---
title: ポータルを Common Data Service 環境に接続する | MicrosoftDocs
description: ポータルを Common Data Service 環境に接続する方法と認証キーを更新する方法を学習します。
author: neerajnandwana-msft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 05/20/2020
ms.author: nenandw
ms.reviewer: tapanm
ms.openlocfilehash: 546fb189ba7f50be08b0ab40b8ad8e77f0848cf8
ms.sourcegitcommit: 2fd873a1ea17f419f6194714efffa47a9bd00c2e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "3507767"
---
# <a name="connect-to-a-common-data-service-environment-using-a-portal"></a>ポータルを使用して Common Data Service 環境に接続する

ポータルは Azure Active Directory アプリケーションを使用して Common Data Service 環境と接続します。 アプリケーションは、ポータルがプロビジョニングされるのと同じテナントに作成されます。 アプリケーションは、ポータルのプロビジョニング プロセス中に Common Data Service 環境に登録されます。

![Common Data Service 環境でポータルに接続する](../media/connect-with-dynamics.png "Common Data Service  環境でポータルに接続する")

各ポータルには、同じ Common Data Service 環境に接続されているかどうかに関係なく、個別の Azure Active Directory アプリケーションが関連付けられています。 ポータルのために作成されたデフォルトの Azure Active Directory 認証プロバイダーは、ポータルを認証するために同じ Azure Active Directory アプリケーションを使用します。 承認はポータルにアクセスするユーザーに割り当てられた Web ロールで実施されます。

関連付けられたポータル アプリケーションを Azure Active Directory で表示できます。 このアプリケーションの名前は Microsoft CRM Portals で、ポータル ID は Azure Active Directory アプリケーション**の App ID URI** フィールドにあります。 ポータルをプロビジョニングするユーザーがこのアプリケーションを所有します。 このアプリケーションは削除または変更しないでください。ポータル機能が壊れる場合があります。 Power Apps ポータル管理センターからポータルを管理するには、アプリケーション所有者である必要があります。

## <a name="authentication-key"></a>認証キー

Azure Active Directory アプリケーションを使用して Common Data Service に接続するポータルについては、Azure Active Directory アプリケーションに接続した認証キーが必要です。 このキーは、ポータルをプロビジョニングして、このキーの公開パートが自動的に Azure Active Directory アプリケーションにアップロードされるときに生成されます。

> [!IMPORTANT]
> 認証キーは 2 年で有効期限が切れます。 ポータルが継続して Common Data Service 環境に接続できるようにするには、2 年ごとに更新する必要があります。 キーを更新しない場合、ポータルは動作を停止します。  

### <a name="authentication-key-details"></a>認証キーの詳細

認証キーの詳細は、Power Apps ポータル管理センターおよびポータルに表示されます。

**Power Apps ポータル管理センター**

1. [Power Apps ポータル管理センター](admin-overview.md) を開きます。

2. **ポータル認証キーの管理**を選択します。 認証キーは有効期限およびサムプリントとともに表示されます。

   > [!div class=mx-imgBorder]
   > ![Power Apps ポータルの管理センターの認証キーの詳細](../media/manage-auth-key.png "Power Apps  ポータル管理センターの認証キーの詳細")

**ポータル**

1. ポータルに管理者としてサインインします。

2.  URL <portal_path>/_services/about に移動します。 認証キーの有効期限が表示されます。 

   > [!div class=mx-imgBorder]
   > ![ポータル サービス ページ](../media/portal-services-page.png "ポータル サービス ページ")

> [!NOTE]
> 認証キー情報を表示するには、同じブラウザー セッション内のポータルにサインインする必要があり、すべての Web サイト アクセス許可を所有している必要があります。

### <a name="authentication-key-expiration-notification"></a>認証キーの有効期限切れの通知

認証キーの有効期限が切れる前に、電子メール、Power Apps ポータル管理センター、ポータルで通知されます。

**電子メール**

電子メールは、ポータルに接続された組織の電子メール通知にサインアップしているユーザーに送信されます。 電子メール通知へのサインアップの詳細については以下を参照してください: [管理者への電子メール通知の管理](https://docs.microsoft.com/dynamics365/customer-engagement/admin/manage-email-notifications)

電子メール通知は次の間隔で送信されます。 
- 90 日間 
- 60 日間 
- 30 日間 
- 15 日間 
- 7 日間 
- 6 日 
- 5 日 
- 4 日 
- 3 日 
- 2 日 
- 1 日 
- 12 時間 
- 6 時間 
- 3 時間

また、キーの有効期限が切れてから 1 週間、毎日通知されます。

> [!NOTE]
> - 間隔はキー有効期限から UTC で計算されます。
> - 電子メールは厳密に上記のような間隔になるとは保証されません。 電子メール通知は遅延または失われる場合があります。 オンラインでもキー有効期限を確認してください。

**Power Apps ポータル管理センター**

キーの有効期限に関するメッセージはページのトップに表示されます。

> [!div class=mx-imgBorder]
> ![Power Apps ポータルの管理センターの認証キーの通知](../media/portal-admin-center-auth-notif.png "Power Apps  ポータルの管理センターでの認証キーの通知")

**ポータル**

URL <portal_path>/_services/about に移動すると、キーの有効期限に関する通知がページのトップに表示されます。

> [!NOTE]
> 同じブラウザー セッション内のポータルにサインインする必要があり、すべての Web サイト アクセス許可を割り当てられている必要があります。

> [!div class=mx-imgBorder]
> ![ポータル上の認証キーの通知](../media/portal-service-page-auth-notif.png "ポータル上の認証キーの通知")

## <a name="renew-portal-authentication-key"></a>ポータル認証キーの更新

ポータルが Common Data Service 環境に接続できるようにするには、2 年ごとにキーを更新する必要があります。

> [!NOTE]
> キーを更新するには、ポータル管理へのアクセス許可が必要です。

1. [Power Apps ポータル管理センター](admin-overview.md) を開きます。

2. **ポータル認証キーの管理**を選択します。 認証キーは有効期限およびサムプリントとともに表示されます。

    > [!div class=mx-imgBorder]
    > ![ポータル認証キーの管理](../media/manage-portal-auth-key.png "ポータル認証キーの管理")

3. **キーの更新**を選択します。

4. メッセージの**更新**を選択します。 更新プロセスが開始され、メッセージが表示されます。

> [!NOTE]
> - このプロセスはバックグラウンドで実行されますが、ポータルは一度再起動します。
> - キーを更新すると、次の 2 年間有効になります。
> - このプロセスには 5 から 7 分かかります。
> - 認証キーを更新しても、他のポータル構成やポータルの状態は変更されません。

### <a name="troubleshooting"></a>トラブルシューティング​​

キーの更新に失敗する場合、以下のアクションとともにエラー メッセージが表示されます。

- **認証キー更新の再試行**。 このアクションにより、ポータル認証キーの更新プロセスを再起動することができます。 更新プログラムが複数回失敗した場合は、Microsoft サポートまでお問い合わせください。

    > [!div class=mx-imgBorder]
    > ![ポータル認証キーの更新を再試行する](../media/retry-auth-key-update.png "ポータル認証キーの更新を再試行する")
