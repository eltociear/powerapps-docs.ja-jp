---
title: ポータル用 OpenID 接続プロバイダー設定の構成 | MicrosoftDocs
description: ポータルの OpenID 接続プロバイダー設定を追加およびコンフィギュレーションする指示をします。
author: sandhangitmsft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: sandhan
ms.reviewer: tapanm
ms.openlocfilehash: fea85107fba2a57d77332c964ff72dc170e96e58
ms.sourcegitcommit: c12260f372ad2cc48d3146be570d2088c9ef1d86
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2020
ms.locfileid: "3494562"
---
# <a name="configure-open-id-connect-provider-settings-for-portals"></a>ポータルの Open ID 接続プロバイダー設定を構成します

[OpenID 接続](https://openid.net/connect/) の外部 ID プロバイダーは、Open ID 接続の [仕様](https://openid.net/developers/specs/)に準拠したサービスです。 プロバイダーを統合するには、プロバイダーに関連付けられる権限 (または発行者) の URL を探します。 構成のための URL は、認証ワークフローに必要なメタデータを提供する発行機関から判別できます。 プロバイダ設定は、[OpenIdConnectAuthenticationOptions](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.aspx) クラスのプロパティに基づきます。

以下は発行機関の URL の例です。

- [Google](https://developers.google.com/identity/protocols/OpenIDConnect): <https://accounts.google.com/><https://accounts.google.com/.well-known/openid-configuration>
- [[!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)]](https://msdn.microsoft.com/library/azure/mt168838.aspx): [https://login.microsoftonline.com/&lt;[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD アプリケーション&gt;/](https://login.microsoftonline.com/contoso.onmicrosoft.com/.well-known/openid-configuration)

各 OpenID 接続 プロバイダーには、アプリケーション (OAuth 2.0 プロバイダーのものに似ています) の登録とクライアント ID の取得も含まれます。権限 URL と生成されたアプリケーションのクライアント ID は、ポータルとIDプロバイダ間の外部認証を有効にするために必要な設定です。

> [!Note]
> Google の OpenID 接続エンドポイントは、現在サポートされていません。これは、基盤とするライブラリが互換性問題のある初期リリース段階にあるためです。 [ポータル用 OAuth2 プロバイダーの設定](configure-oauth2-settings.md) エンドポイントを代わりに使用できます。

## <a name="openid-settings-for-pn-azure-active-directory"></a>[!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)]に対する OpenID 設定

開始するには、[[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] 管理ポータル](https://msdn.microsoft.com/library/azure/hh967611.aspx#bkmk_azureportal) にサインインして、既存ディレクトリを作成または選択します。 ディレクトリが使用可能な場合、ディレクトリに [アプリケーションを追加](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications) するための説明に従います。  

1. ディレクトリの**アプリケーション**メニューの下で、**追加**を選択します。
2. **自分の組織が作成するアプリケーションを追加**を選択します。
3. カスタマイズされた**名前**をアプリケーションに指定して、**Web アプリケーションまたは Web API** の種類を選択します。
4. **サインオン URL** および **アプリ ID URI** には、両方のフィールドにポータルの URL を指定 https://portal.contoso.com/
5. この時点で、新しいアプリケーションが作成されます。 メニューの**構成**セクションに移動します。

    **シングル サインオン**セクションで、最初の**返信URL**エントリを更新してURL: https://portal.contoso.com/signin-azure-adにパスを含めます。 これは、**RedirectUri** サイト設定値に相当

6. **プロパティ**セクションで、**クライアント ID** フィールドを見つけます。 これは、**ClientId** サイト設定値に相当します。
7. フッター メニューで、**エンドポイントの表示**を選び、**フェデレーション メタデータ ドキュメント**フィールドを留意します。

URL の左の部分は**権限**の値で、次の形式のいずれかになります。

- https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/
- https://login.microsoftonline.com/contoso.onmicrosoft.com/

サービスの構成 URL を取得するには、FederationMetadata/2007-06/FederationMetadata.xml のパス末尾を .well-known/openid-configuration のパスに置換します。 たとえば、<https://login.microsoftonline.com/contoso.onmicrosoft.com/.well-known/openid-configuration>

これは、**MetadataAddress** サイト設定値に相当します。

### <a name="related-site-settings"></a>関連するサイト設定

上述のアプリケーションを参照するポータル サイト設定を適用します。

> [!Note]
> 標準の [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD 構成は、次の設定のみを使用します (値の例を含む):                                 
> - Authentication/OpenIdConnect/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/Authority - <https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/>                                                    
> - Authentication/OpenIdConnect/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/ClientId - fedcba98-7654-3210-fedc-ba9876543210                                      
>   クライアント ID および発行機関 URL は、同じ値を含むことはできず、個別に取得する必要があります。           
> - Authentication/OpenIdConnect/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/RedirectUri - https://portal.contoso.com/signin-azure-ad
 
\[プロバイダー\] タグのラベルを置き換えて、複数の ID プロバイダーを構成することができます。 それぞれの固有のラベルは、ID プロバイダーに関連する設定グループとなります。 例: [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD、MyIdP


|                          サイト設定の名前                           |                                                                                                                                                                                                         内容                                                                                                                                                                                                          |
|----------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           Authentication/Registration/ExternalLoginEnabled           |                                                                                                                                                                         外部アカウントのサインインと登録を有効化または無効化します。 既定値: true                                                                                                                                                                         |
|         Authentication/OpenIdConnect/\[プロバイダー\]/Authority          |                                               必須。 OpenIdConnect の呼び出しの作成に使用する発行機関。 例: `https://login.microsoftonline.com/contoso.onmicrosoft.com/`。 詳細は、[OpenIdConnectAuthenticationOptions.Authority](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.authority.aspx) を参照してください。                                                |
|      Authentication/OpenIdConnect/\[プロバイダー\]/MetadataAddress       | メタデータを取得するための探索エンドポイントです。 通常は次のパスで終わります:/.well-known/openid-configuration 。 例: `https://login.microsoftonline.com/contoso.onmicrosoft.com/.well-known/openid-configuration`。 詳細は、[OpenIdConnectAuthenticationOptions.MetadataAddress](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.metadataaddress.aspx) を参照してください。 |
|     Authentication/OpenIdConnect/\[プロバイダー\]/AuthenticationType     |                                   OWIN 認証のミドルウェアの種類を指定します。 サービス構成メタデータにある発行者の値を指定します。 例: `https://sts.windows.net/contoso.onmicrosoft.com/`。 詳細は、[AuthenticationOptions.AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx) を参照してください。                                   |
|          Authentication/OpenIdConnect/\[プロバイダー\]/ClientId          |                                                  必須。 プロバイダーのアプリケーションから取得した クライアント ID の値。 「アプリ ID」または「コンシューマ キー」と呼ばれる場合もあります。 詳細は、[OpenIdConnectAuthenticationOptions.ClientId](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.clientid.aspx) を参照してください。                                                   |
|        Authentication/OpenIdConnect/\[プロバイダー\]/ClientSecret        |                                              プロバイダーのアプリケーションから取得した クライアント シークレットの値。 「アプリ シークレット」または「コンシューマ シークレット」と呼ばれる場合もあります。 詳細は、[OpenIdConnectAuthenticationOptions.ClientSecret](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.clientsecret.aspx) を参照してください。                                              |
|        Authentication/OpenIdConnect/\[プロバイダー\]/RedirectUri         |                                                        推奨要件。 AD FS WS-Federation のパッシブ エンドポイントです。 例: https://portal.contoso.com/signin-saml2。 詳細は、[OpenIdConnectAuthenticationOptions.RedirectUri](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.redirecturi.aspx) を参照してください。                                                        |
|          Authentication/OpenIdConnect/\[プロバイダー\]/Caption           |                                                              推奨要件。 ユーザーがサインインのユーザー インターフェイスに表示できるテキストです。 既定: \[プロバイダー\]。 詳細は、[OpenIdConnectAuthenticationOptions.Caption](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.caption.aspx) を参照してください。                                                               |
|          Authentication/OpenIdConnect/\[プロバイダー\]/Resource          |                                                                                                       'resource' (リソース)。 詳細は、[OpenIdConnectAuthenticationOptions.Resource](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.resource.aspx) を参照してください。                                                                                                        |
|        Authentication/OpenIdConnect/\[プロバイダー\]/ResponseType        |                                                                                                '応答の\_種類'。 詳細は、[OpenIdConnectAuthenticationOptions.ResponseType](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.responsetype.aspx) を参照してください。                                                                                                 |
|           Authentication/OpenIdConnect/\[プロバイダー\]/Scope            |                                                                                要求に対するアクセス許可のスペース区切りの一覧。 既定: openid。 詳細は、[OpenIdConnectAuthenticationOptions.Scope ](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.scope.aspx) を参照してください。                                                                                 |
|        Authentication/OpenIdConnect/\[プロバイダー\]/CallbackPath        |                      認証コールバックを処理する任意の制約されたパスです。 提供されず、RedirectUri がある場合、この値は RedirectUri から生成されます。 詳細は、[OpenIdConnectAuthenticationOptions.CallbackPath](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.callbackpath.aspx) を参照してください。                      |
|     Authentication/OpenIdConnect/\[プロバイダー\]/BackchannelTimeout     |                                                                バック チャネル コミュニケーション用のタイムアウト値。 例: 00:05:00 (5 分)。 詳細は、[OpenIdConnectAuthenticationOptions.BackchannelTimeout](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.backchanneltimeout.aspx) を参照してください。                                                                |
| Authentication/OpenIdConnect/\[プロバイダー\]/RefreshOnIssuerKeyNotFound |                                      メタデータの更新を SecurityTokenSignatureKeyNotFoundException の後に実行するかどうかを指定します。 詳細は、[OpenIdConnectAuthenticationOptions.RefreshOnIssuerKeyNotFound](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.refreshonissuerkeynotfound.aspx) を参照してください。                                       |
|      Authentication/OpenIdConnect/\[プロバイダー\]/UseTokenLifetime      |                                               認証セッションの有効期限 (例: クッキー) は認証トークンと一致する必要があることを示します。 詳細は、[OpenIdConnectAuthenticationOptions.UseTokenLifetime](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.usetokenlifetime.aspx) を参照してください。                                               |
|     Authentication/OpenIdConnect/\[プロバイダー\]/AuthenticationMode     |                                                                                                     OWIN 認証のミドルウェアのモードを指定します。 詳細は、[AuthenticationOptions.AuthenticationMode](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx) を参照してください。                                                                                                     |
| Authentication/OpenIdConnect/\[プロバイダー\]/SignInAsAuthenticationType |                                                   System.Security.Claims.ClaimsIdentity の作成時に使用される AuthenticationType です。 詳細は、[OpenIdConnectAuthenticationOptions.SignInAsAuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.signinasauthenticationtype.aspx) を参照してください。                                                   |
|   Authentication/OpenIdConnect/\[プロバイダー\]/PostLogoutRedirectUri    |                                                                                 'post\_logout\_redirect\_uri' (ログアウト後のリダイレクト URI)。 詳細は、[OpenIdConnectAuthenticationOptions.PostLogoutRedirectUri](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.postlogoutredirecturi.aspx) を参照してください。                                                                                 |
|       Authentication/OpenIdConnect/\[プロバイダー\]/ValidAudiences       |                                                                                                  対象者 URL のコンマ区切り一覧です。 詳細は、[TokenValidationParameters.AllowedAudiences](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.allowedaudiences.aspx) を参照してください。                                                                                                  |
|        Authentication/OpenIdConnect/\[プロバイダー\]/ValidIssuers        |                                                                                                       発行者 URL のコンマ区切り一覧です。 詳細は、[TokenValidationParameters.ValidIssuers](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.validissuers.aspx) を参照してください。                                                                                                       |
|         Authentication/OpenIdConnect/\[プロバイダー\]/ClockSkew          |                                                                                                                                                                                        時間を有効にする際に適用するクロック スキューです。                                                                                                                                                                                        |
|       Authentication/OpenIdConnect/\[プロバイダー\]/NameClaimType        |                                                                                                                                                                              名前の要求を格納する ClaimsIdentity に使用される要求の種類です。                                                                                                                                                                              |
|       Authentication/OpenIdConnect/\[プロバイダー\]/RoleClaimType        |                                                                                                                                                                              ロールの要求を格納する ClaimsIdentity に使用される要求の種類です。                                                                                                                                                                              |
|   Authentication/OpenIdConnect/\[プロバイダー\]/RequireExpirationTime    |                                                                                                                                                                              トークンに "期限切れ" の値が必要かどうかを示す値です。                                                                                                                                                                              |
|    Authentication/OpenIdConnect/\[プロバイダー\]/RequireSignedTokens     |                                                                                                                               System.IdentityModel.Tokens.SecurityToken xmlns=<https://ddue.schemas.microsoft.com/authoring/2003/5> が署名されていない場合に有効になりうるかどうかを示す値です。                                                                                                                                |
|      Authentication/OpenIdConnect/\[プロバイダー\]/SaveSigninToken       |                                                                                                                                                                        セッションの作成時に元のトークンが保存されるかを制御するブール値です。                                                                                                                                                                        |
|       Authentication/OpenIdConnect/\[プロバイダー\]/ValidateActor        |                                                                                                                                                            System.IdentityModel.Tokens.JwtSecurityToken.Actor を有効にする必要があるかどうかを示す値です。                                                                                                                                                            |
|      Authentication/OpenIdConnect/\[プロバイダー\]/ValidateAudience      |                                                                                                                                                                       対象者がトークンの検証時に検証されるかを制御するブール値です。                                                                                                                                                                        |
|       Authentication/OpenIdConnect/\[プロバイダー\]/ValidateIssuer       |                                                                                                                                                                        発行者がトークンの検証時に検証されるかを制御するブール値です。                                                                                                                                                                         |
|      Authentication/OpenIdConnect/\[プロバイダー\]/ValidateLifetime      |                                                                                                                                                                       有効期限がトークンの検証時に検証されるかを制御するブール値です。                                                                                                                                                                        |
|  Authentication/OpenIdConnect/\[プロバイダー\]/ValidateIssuerSigningKey  |                                                                                                                  securityToken xmlns=<https://ddue.schemas.microsoft.com/authoring/2003/5> に署名したSystem.IdentityModel.Tokens.SecurityKey の検証を呼び出すかどうかを制御するブール値です。                                                                                                                  |
|                                                                      |                                                                                                                                                                                                                                                                                                                                                                                                                              |

## <a name="enable-authentication-using-a-multi-tenant-azure-active-directory-application"></a>マルチテナント Azure Active Directory アプリケーションを使用して認証を有効にする

[!include[](../../../includes/pn-azure-active-directory.md)] に登録されたマルチテナント型のアプリケーションを使用することにより、単に特定のテナントではなく、[!include[](../../../includes/pn-azure-shortest.md)] 内の任意のテナントからの [!include[](../../../includes/pn-azure-active-directory.md)] ユーザーを受入れるようにポータルを構成することができます。 マルチテナント機能を有効にするには、[!include[](../../../includes/pn-azure-active-directory.md)] アプリケーションで**マルチテナント型**スイッチを**はい**にセットします。

![Azure Active Directory アプリケーションでマルチテナント機能を有効化](../media/enable-multi-tenancy.png "Azure Active Directory アプリケーションでマルチテナント機能を有効化")

### <a name="related-site-settings"></a>関連するサイト設定

[プロバイダー] タグのラベルを置き換えて、複数の ID プロバイダーを構成することができます。 それぞれの固有のラベルは、ID プロバイダーに関連する設定グループとなります。 マルチテナント型アプリケーションを使用する [!include[](../../../includes/pn-azure-active-directory.md)] に対する認証をサポートするように、ポータル内の以下のサイトの設定を作成または構成することができます。

|サイト設定の名前    |説明   |
|---|---|
|Authentication/OpenIdConnect/[プロバイダー]/Authority   |OpenIdConnect の呼び出しの作成に使用する発行機関。 例: `https://login.microsoftonline.com/common`   |
|Authentication/OpenIdConnect/[プロバイダー]/ClientId   |プロバイダーのアプリケーションから取得した クライアント ID の値。 アプリ ID またはコンシューマ キーと呼ばれる場合もあります。   |
|Authentication/OpenIdConnect/[プロバイダー]/ExternalLogoutEnabled   |外部アカウントのサインアウトと登録を有効化または無効化します。 この値を True としてセットします。   |
|Authentication/OpenIdConnect/[プロバイダー]/IssuerFilter   |すべてのテナントですべての発行者に一致するワイルドカード ベースのフィルター。 大抵の場合、以下の値を使用します。`https://sts.windows.net/*/`   |
|Authentication/OpenIdConnect/[プロバイダー]/RedirectUri  |プロバイダが認証の応答を送信する返信 URL の場所。例: `https://portal.contoso.com/signin-oidc` |
|Authentication/OpenIdConnect/[プロバイダー]/ValidateIssuer   |発行者がトークンの検証時に検証されるかを制御するブール値です。 この値を False としてセットします。   |
|||

### <a name="see-also"></a>関連項目
[ポータル認証の構成](configure-portal-authentication.md)  
[ポータル用の認証 ID の設定](set-authentication-identity.md)  
[ポータル用 OAuth2 プロバイダーの設定](configure-oauth2-settings.md)  
[ポータル用 WS-Federation プロバイダーの設定](configure-ws-federation-settings.md)  
[ポータルの SAML 2.0 プロバイダーの設定](configure-saml2-settings.md)  

