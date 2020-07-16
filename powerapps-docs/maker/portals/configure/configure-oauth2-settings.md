---
title: ポータル用 OAuth2 プロバイダー設定の構成 | MicrosoftDocs
description: ポータルの OAuth2 プロバイダー設定を追加およびコンフィギュレーションする指示をします。
author: sandhangitmsft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 01/17/2020
ms.author: sandhan
ms.reviewer: tapanm
ms.openlocfilehash: c025c3d089fd30afafd2680b4c3f7edaaa2d9f76
ms.sourcegitcommit: c12260f372ad2cc48d3146be570d2088c9ef1d86
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2020
ms.locfileid: "3494697"
---
# <a name="configure-oauth2-provider-settings-for-portals"></a>ポータル用 OAuth2 プロバイダー設定を構成します

OAuth 2.0 ベースの外部 ID プロバイダーは、「クライアント ID」と「クライアント シークレット」の組を取得するために、サード パーティ サービスの「アプリケーション」の登録を行います。 通常このアプリケーションは、ID プロバイダーがユーザーをポータル (証明書利用者) に送り返すためのリダイレクト URL を指定することを要求します。 クライアント ID とクライアント シークレットはポータル サイトの設定として構成され、証明書利用者から ID プロバイダーへの保護された接続が確立されます。 設定は、[[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]AccountAuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.aspx)、[TwitterAuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.twitter.twitterauthenticationoptions.aspx)、[FacebookAuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.facebook.facebookauthenticationoptions.aspx)、および [GoogleOAuth2AuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.google.googleoauth2authenticationoptions.aspx) クラスのプロパティーに基づいています。  

サポートされるプロバイダーは次のとおりです。

- [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] アカウント
- Twitter
- Facebook
- Google
- LinkedIn
- Yahoo

## <a name="create-oauth-applications"></a>OAuth アプリケーションを作成する

一般に、OAuth プロバイダーがリダイレクト URI の値を必要とするアプリケーションを使用する場合、プロバイダーがリダイレクト URI を検証する方法に合わせて (一部のプロバイダでは、ドメイン名のほかに URL の完全なパスを指定する必要があります) <https://portal.contoso.com/or>https://portal.contoso.com/signin-\[プロバイダー\] を指定します。 リダイレクト URI の \[プロバイダー\] を、プロバイダーの名前に置き換えます。

## <a name="google-people-api-settings"></a>Google People API の設定

> [!NOTE]
> [Google+ API](https://developers.google.com/people/legacy) の使用は非推奨です。 [Google People API](https://developers.google.com/people) に移行することを強くお勧めします。

次の手順に従い、 Power Apps ユーザー認証に [Google の Oauth 2.0認証] を実装したポータルの設定をします。

1. [Google 開発者コンソール](https://console.developers.google.com/) を開きます。  
1. API プロジェクトを作成するか、または既存のプロジェクトを開きます。
1. API とサービスのダッシュボードから **API とサービスを有効にする** を選択します。
1. API を検索して有効にします **Google People API**。
1. **Google API** の内部で、左側のナビゲーションから **資格情報** を選択します。

    > [!NOTE]
    > ポータルのトップ レベル ドメインに既に同意の画面を構成している場合は、手順 6〜14 をスキップして、手順15にに進んでください。 ただし、同意画面を構成していてもポータルのトップ レベルのドメインが追加されていない場合は、手順 11 を実行してから手順 15 に進んでください。

1. **同意画面の構成** を選択します。
1. **外部** ユーザー タイプを選択します。
1. **作成**を選びます。
1. **アプリケーション名** を入力し、必要に応じてロゴの画像をアップロードします。
1. 適切なものを選択してください**サポート メール**。
1. **承認済みドメイン** のトップ レベルドメインとして **powerappsportals.com** と入力します。 まだ [Power Apps ポータルドメイン名の更新](../admin/update-portal-domain.md) をしていない場合は、 **microsoftcrmportals.com** を入力してください。 設定している場合は、 [カスタムドメイン名](../admin/add-custom-domain.md) を入力することもできます。 
1. 必要に応じて、ホームページ、プライバシー ポリシー、利用規約へのリンクを設定します。 
1. **保存**を選択します。
1. 左のナビゲーションメニューから **資格情報** 選択します。
1. **資格情報を作成する** ドロップ ダウン メニューから **OauthクライアントID** を選択します。
1. アプリケーションの種類に **Web アプリケーション** を選択します。
1. Oauth クライアントID に **名前** を入力します。
1. **承認された JavaScript の発行元** リストに Power Apps のポータルURL を入力します。
1. Power Apps ポータルのURLの **/signin-google** の後に、 **許可されたリダイレクトのURI** を入力します。 たとえば、ポータルのURLが https://contoso.powerappsportals.com の場合は、承認済みリダイレクトのURIフィールドは https://contoso.powerappsportals.com/signin-google となります。
1. **作成**を選びます。
1. **Oauth クライアント** ダイアログ ボックスから **クライアント ID** と **クライアントの秘密** をコピーし、 Power Apps ポータルの [OAuth2 サイト 設定](https://docs.microsoft.com/powerapps/maker/portals/configure/configure-oauth2-settings#create-site-settings-by-using-oauth2) を設定します。

## <a name="facebook-app-settings"></a>Facebook アプリの設定

1. [Facebook 開発者アプリ ダッシュボード](https://developers.facebook.com/apps) を開きます  
2. **新アプリの追加**を選択します。
3. **ウェブサイト**を選択します。
4. **アプリ ID スキップと作成**を選択します。
    - **名前表示**を選択します。
    - **カテゴリー**を選択します。
    - **アプリ ID 作成**を選択します。

5. 新しいアプリのダッシュボードにいる間、**設定** &gt; **基本**(タブ) へ進み、次の詳細へ追加します。
    - アプリケーションのドメイン (任意) : portal.contoso.com 
    - 担当者の電子メール: *&lt;自分で選択した電子メール アドレス&gt;* 
    - **プラットフォームの追加**を選択し、**ウェブサイト**を選びます。 
    - サイトの URL: https://portal.contoso.com/ または https://portal.contoso.com/signin-facebook

6. **変更を保存**を選択します。
7. **ステイタス & リビュー** &gt; **ステイタス**タブへ進みます。
8. アプリとそのすべての機能を一般に公開するように促された時、**はい**を選択します。 この設定を有効にするには、上記の手順 5 で有効なデータを入力する必要があります。

### <a name="cc-microsoft-application-settings"></a>[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] アプリケーションの設定

1. [[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] アカウント デベロッパー センター](https://account.live.com/developers/applications/index)を開きます  
2. **アプリケーションの作成**を選択し、**アプリケーションの名前**を指定します。
3. 使用条件に同意したら、**同意する**を選択します。
4. **設定** &gt;**API 設定**の順に移動してから、リダイレクト URL を https://portal.contoso.com/signin-microsoft として設定します 

## <a name="twitter-apps-settings"></a>Twitter アプリケーションの設定

1. [Twitter アプリケーション管理](https://apps.twitter.com/) を開きます。 
2. **新アプリを作成**を選択します。

    - アプリの**名前**と**内容**を指定します。
    - Web サイトの URL を https://portal.contoso.com として設定します。
    - コールバック URL を https://portal.contoso.com または https://portal.contoso.com/signin-twitter として設定します。

3. **Twitter アプリケーションの作成**を選択します。

## <a name="linkedin-app-settings"></a>LinkedIn アプリケーションの設定

1. [LinkedIn 開発者ネットワーク](https://www.linkedin.com/secure/developer) を開きます。  
2. **新アプリケーションの追加**を選択します。

    - **アプリケーションの名前**や**内容**などを指定します。
    - Web サイトの URL を https://portal.contoso.com として設定します。
    - OAuth のユーザー許諾/既定スコープの設定: r\_basicprofie および r\_emailaddress
    - OAuth 2.0 のリダイレクト URL を https://portal.contoso.com/signin-linkedin に設定します。

3. **アプリケーションの追加**を選択します。

## <a name="yahoo-ydn-app-settings"></a>Yahoo! YDN アプリケーションの設定

> [!NOTE]
> 更新された Yahoo YDN OAuthプロバイダ エンドポイントと Power Apps ポータルの間では継続的な互換性の問題があるため、ユーザーは一時的に Yahoo アイデンティティ プロバイダでの認証でがきません。

1. [Yahoo! 開発者ネットワーク](https://developer.yahoo.com/apps) を開きます。
2. **アプリ作成**を選択します。
    
    - **アプリケーションの名前**を指定します。
    - アプリケーション タイプ: **Web アプリケーション**。
    - コールバック ドメイン: portal.contoso.com

3. **アプリ作成**を選択します。

## <a name="create-site-settings-by-using-oauth2"></a>OAuth2 使いサイト設定を作成

各プロバイダのアプリケーション ダッシュボードには、各アプリケーションについて、クライアント ID (アプリケーション ID、コンシューマ キー) およびクライアント シークレット (アプリケーション シークレット、コンシューマ シークレット) が表示されます。 これら 2 つの値を使用して、ポータル サイトの設定を構成します。

>[!Note]
> 標準 OAuth2 構成には次の設定のみが必要です (例として Facebook を使用)。
> - `Authentication/OpenAuth/Facebook/ClientId`
> - `Authentication/OpenAuth/Facebook/ClientSecret`

サイト設定名の `[provider]` タグを、特定の ID プロバイダー名に置き換えてください: Facebook、Google、Yahoo、[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]、 LinkedIn、または Twitter。

|**サイト設定の名前**                                           |**説明**                                                                                                                                                                                                                                                                                                                                      |
|-----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/Registration/ExternalLoginEnabled                | 外部アカウントのサインインと登録を有効化または無効化します。 既定値: true                                                                                                                                                                                                                                                                         |
| Authentication/OpenAuth/\[プロバイダー\]/ClientId                   | 必須。 プロバイダーのアプリケーションから取得した クライアント ID の値。 アプリ ID またはコンシューマ キーと呼ばれる場合もあります。  下位互換性のために次の設定名が使用できます: Authentication/OpenAuth/Twitter/ConsumerKey <ul><li>Authentication/OpenAuth/Facebook/AppId</li><li>Authentication/OpenAuth/LinkedIn/ConsumerKey</li> |
| Authentication/OpenAuth/\[プロバイダー\]/ClientSecret               | 必須。 プロバイダーのアプリケーションから取得した クライアント シークレットの値。 アプリ シークレットまたはコンシューマ シークレットと呼ばれる場合もあります。  下位互換性のために次の設定名が使用できます: Authentication/OpenAuth/Twitter/ConsumerSecret <ul><li>Authentication/OpenAuth/Facebook/AppSecret</li><li>Authentication/OpenAuth/LinkedIn/ConsumerSecret</li> |
| Authentication/OpenAuth/\[プロバイダー\]/AuthenticationType         | OWIN 認証のミドルウェアの種類を指定します。 例: yahoo。 [authenticationoptions.authenticationtype](https://msdn.microsoft.com//library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx)。                                                                                                                                |  
| Authentication/OpenAuth/\[プロバイダー\]/Scope                      | 要求に対するアクセス許可のコンマ区切りの一覧。 [microsoftaccountauthenticationoptions.scope](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.scope.aspx)。                                                                                                                |  
| Authentication/OpenAuth/\[プロバイダー\]/Caption                    | ユーザーがサインインのユーザー インターフェイスに表示できるテキストです。 。[microsoftaccountauthenticationoptions.caption](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.caption.aspx).                                                                                              |  
| Authentication/OpenAuth/\[プロバイダー\]/BackchannelTimeout         | バック チャネル コミュニケーション用のミリ秒単位のタイムアウト値。 [microsoftaccountauthenticationoptions.backchanneltimeout](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.backchanneltimeout.aspx)。                                                                         |  
| Authentication/OpenAuth/\[プロバイダー\]/CallbackPath               | ユーザー エージェントが返される、アプリケーションの基本パス内におけるリクエスト パス。 [microsoftaccountauthenticationoptions.callbackpath](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.callbackpath.aspx)。                                                         |  
| Authentication/OpenAuth/\[プロバイダー\]/SignInAsAuthenticationType | 実際に**userClaimsIdentity**の発行を担当する、別の認証ミドルウェアの名前。 [microsoftaccountauthenticationoptions.signinasauthenticationtype](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.signinasauthenticationtype.aspx)。 |  
| Authentication/OpenAuth/\[プロバイダー\]/AuthenticationMode         | OWIN 認証のミドルウェアのモードを指定します。 [security.authenticationoptions.authenticationmode](https://msdn.microsoft.com//library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx)。                                                                                                                                       |  

### <a name="see-also"></a>関連項目

[ポータル認証の構成](configure-portal-authentication.md)  
[ポータル用の認証 ID の設定](set-authentication-identity.md)  
[ポータルの Open ID 接続プロバイダーの設定](configure-openid-settings.md)   
[ポータル用 WS-Federation プロバイダーの設定](configure-ws-federation-settings.md)  
[ポータルの SAML 2.0 プロバイダーの設定](configure-saml2-settings.md)
