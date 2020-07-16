---
title: ポータル用 WS-Federation プロバイダー設定の構成 | MicrosoftDocs
description: ポータル用WS-Federationの構成を追加して構成するための手順ついての説明です。
author: sandhangitmsft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: sandhan
ms.reviewer: tapanm
ms.openlocfilehash: 285b87fa6df450cbb9ac0dceb5414bca546c586b
ms.sourcegitcommit: c12260f372ad2cc48d3146be570d2088c9ef1d86
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2020
ms.locfileid: "3489955"
---
# <a name="configure-ws-federation-provider-settings-for-portals"></a>ポータル用 WS-Federation プロバイダー設定を構成します

単一の [!INCLUDE[pn-active-directory](../../../includes/pn-active-directory.md)] フェデレーション サービスのサーバー (または別の [WS-Federation](https://msdn.microsoft.com/library/bb498017.aspx)–に準拠した Security Token Service) を ID プロバイダーとして追加できます。 さらに、単一の [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] ACS](https://azure.microsoft.com/documentation/articles/active-directory-dotnet-how-to-use-access-control/) 名前空間を個別の ID プロバイダーのセットとして構成できます。 AD FS と ACS の両方の設定は、[WsFederationAuthenticationOptions](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.aspx) クラスのプロパティに基づいています。

## <a name="create-an-ad-fs-relying-party-trust"></a>AD FS 証明書利用者信頼を作成

AD FS 管理ツールを使用して、**信頼関係** &gt; **証明書利用者信頼**へ移動します。

1.  **Relying Party Trust を追加**を選択します。
2.  ようこそ: **スタート画面**の選択。
3.  データ ソースの選択: **依拠当事者に関するデータを手動で入力**を選び、**次** を選択します。
4.  ディスプレイ名を指定: **名前**を入力し、**次** を選択します。
    例: https://portal.contoso.com/
5.  プロファイルの選択: **AD FS 2.0 プロファイル**を選択し、**次へ**を選択します。
6.  証明書の構成: **次へ**を選択します。
7.  URL の構成: **WS-Federation パッシブ プロトコルのサポートを有効にする**チェックボックスを選択します。

証明書利用者の WS-Federation パッシブ プロトコル URL: https://portal.contoso.com/signin-federation を入力

-   メモ: AD FS はポータルが **HTTPS** で実行される必要があります。

    > [!Note]
    > 結果のエンドポイントには、次の設定があります。エンドポイントの種類 : **WS-Federation**
    > -   バインド:**POST**
    > -   インデックス: n/a (0)
    > -   URL: **https://portal.contoso.com/signin-federation**

8.  IDの構成:https://portal.contoso.com/を指定して、**追加**を選択し、次いで**次へ**を選択します。
    必要であれば、各証明書利用者ポータルに複数の ID を追加できます。 ユーザーは、使用できるいずれかまたはすべての ID で認証できます。
9.  発行権限ルールの選択: **全てのユーザーが依存当事者にアクセスできるよう許可**を選び、**次** を選択します。
10.  信頼を追加する準備: **次へ**を選択します。
11.  **クローズ**を選択します。

証明書利用者信頼に**名前 ID** 要求を追加します。

**[!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] アカウント名を****名前 ID 要求へ変換** (入力方向の要求を変換):
- 入力方向の要求の種類: Windows アカウント名
- 出力方向の要求の種類: [名前 ID]
- 出力方向の名前 ID 形式: [指定なし]
- すべての要求値をパス スルーする

### <a name="create-ad-fs-site-settings"></a>AD FS サイト設定の作成

上述のAD FS 証明書利用者信頼を参照するポータル サイト設定を適用します。

> [!Note]
> 標準の AD FS (STS) 構成は、次の設定のみを使用します (値の例を含む)。
> - Authentication/WsFederation/ADFS/MetadataAddress - https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml
> - Authentication/WsFederation/ADFS/AuthenticationType - https://adfs.contoso.com/adfs/services/trust
>   - フェデレーション メタデータのルート要素の **entityID** 属性の値を使用 (**MetadataAddress URL** を上記のサイト設定の値のブラウザーで開く)
> - Authentication/WsFederation/ADFS/Wtrealm - https://portal.contoso.com/
> - Authentication/WsFederation/ADFS/Wreply - https://portal.contoso.com/signin-federation

**WS-Federation メタデータ**は AD FS サーバーで次のスクリプトを実行することで **[!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)]** で取得できます。

```
Import-Module adfs
Get-ADFSEndpoint -AddressPath /FederationMetadata/2007-06/FederationMetadata.xml
```


|                      サイト設定の名前                      |                                                                                                                                                                                                                                                 内容                                                                                                                                                                                                                                                 |
|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      Authentication/Registration/ExternalLoginEnabled       |                                                                                                                                                                                                                外部アカウントのサインインと登録を有効化または無効化します。 既定値: true                                                                                                                                                                                                                 |
|      Authentication/WsFederation/ADFS/MetadataAddress       | 必須。 AD FS (STS) サーバーの [WS-Federation](https://msdn.microsoft.com/library/bb498017.aspx) メタデータ URLです。 通常は次のパスで終わります:/FederationMetadata/2007-06/FederationMetadata.xml。 例: <https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml>。 詳細は、[WsFederationAuthenticationOptions.MetadataAddress](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.metadataaddress.aspx)。 |
|     Authentication/WsFederation/ADFS/AuthenticationType     |            必須。 OWIN 認証のミドルウェアの種類を指定します。 フェデレーション メタデータ XML のルートで [entityID](https://docs.microsoft.com/azure/active-directory/develop/active-directory-federation-metadata) 属性の値を指定します。 例: https://adfs.contoso.com/adfs/services/trust。 詳細は、[AuthenticationOptions.AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx) を参照してください。             |
|          Authentication/WsFederation/ADFS/Wtrealm           |                                                                                                              必須。 AD FS 証明書利用者 ID です。 例: `https://portal.contoso.com/`。 詳細は、[WsFederationAuthenticationOptions.Wtrealm](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wtrealm.aspx)。                                                                                                               |
|           Authentication/WsFederation/ADFS/Wreply           |                                                                                                     必須。 AD FS WS-Federation のパッシブ エンドポイントです。 例: https://portal.contoso.com/signin-federation。 詳細は、[WsFederationAuthenticationOptions.Wreply](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wreply.aspx)。                                                                                                     |
|          Authentication/WsFederation/ADFS/Caption           |                                                                                                           推奨要件。 ユーザーがサインインのユーザー インターフェイスに表示できるテキストです。 既定: ADFS。 詳細は、[WsFederationAuthenticationOptions.Caption](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.caption.aspx)。                                                                                                            |
|        Authentication/WsFederation/ADFS/CallbackPath        |                                                                                                             認証コールバックを処理する任意の制約されたパスです。 詳細は、[WsFederationAuthenticationOptions.CallbackPath](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.callbackpath.aspx)。                                                                                                              |
|       Authentication/WsFederation/ADFS/SignOutWreply        |                                                                                                                               サインアウトに使用される "wreply" 値です。詳細情報: [WsFederationAuthenticationOptions.SignOutWreply](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.signoutwreply.aspx)。                                                                                                                               |
|     Authentication/WsFederation/ADFS/BackchannelTimeout     |                                                                                                         バック チャネル コミュニケーション用のタイムアウト値。 例: 00:05:00 (5 分)。 詳細は、[WsFederationAuthenticationOptions.BackchannelTimeout](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.backchanneltimeout.aspx)。                                                                                                         |
| Authentication/WsFederation/ADFS/RefreshOnIssuerKeyNotFound |                                                                                  メタデータの更新を SecurityTokenSignatureKeyNotFoundException の後に実行するかどうかを指定します。 詳細情報: [WsFederationAuthenticationOptions.RefreshOnIssuerKeyNotFound](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.refreshonissuerkeynotfound.aspx)。                                                                                  |
|      Authentication/WsFederation/ADFS/UseTokenLifetime      |                                                                                                   認証セッションの有効期限 (例: クッキー) は認証トークンと一致する必要があることを示します。 [WsFederationAuthenticationOptions.UseTokenLifetime](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.usetokenlifetime.aspx)。                                                                                                   |
|     Authentication/WsFederation/ADFS/AuthenticationMode     |                                                                                                                                            OWIN 認証のミドルウェアのモードを指定します。 詳細は、[AuthenticationOptions.AuthenticationMode](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx) を参照してください。                                                                                                                                             |
| Authentication/WsFederation/ADFS/SignInAsAuthenticationType |                                                                                            System.Security.Claims.ClaimsIdentity の作成時に使用される AuthenticationType です。 詳細は、[WsFederationAuthenticationOptions.SignInAsAuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.signinasauthenticationtype.aspx)。                                                                                            |
|       Authentication/WsFederation/ADFS/ValidAudiences       |                                                                                                                                         対象者 URL のコンマ区切り一覧です。 詳細は、[TokenValidationParameters.AllowedAudiences](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.allowedaudiences.aspx) を参照してください。                                                                                                                                          |
|        Authentication/WsFederation/ADFS/ValidIssuers        |                                                                                                                                              発行者 URL のコンマ区切り一覧です。 詳細は、[TokenValidationParameters.ValidIssuers](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.validissuers.aspx) を参照してください。                                                                                                                                               |
|         Authentication/WsFederation/ADFS/ClockSkew          |                                                                                                                                                                                                                               時間を有効にする際に適用するクロック スキューです。                                                                                                                                                                                                                                |
|       Authentication/WsFederation/ADFS/NameClaimType        |                                                                                                                                                                                                                     名前の要求を格納する ClaimsIdentity に使用される要求の種類です。                                                                                                                                                                                                                      |
|       Authentication/WsFederation/ADFS/RoleClaimType        |                                                                                                                                                                                                                     ロールの要求を格納する ClaimsIdentity に使用される要求の種類です。                                                                                                                                                                                                                      |
|   Authentication/WsFederation/ADFS/RequireExpirationTime    |                                                                                                                                                                                                                     トークンに "期限切れ" の値が必要かどうかを示す値です。                                                                                                                                                                                                                      |
|    Authentication/WsFederation/ADFS/RequireSignedTokens     |                                                                                                                                                                       System.IdentityModel.Tokens.SecurityToken xmlns=<https://ddue.schemas.microsoft.com/authoring/2003/5> が署名されていない場合に有効になりうるかどうかを示す値です。                                                                                                                                                                       |
|      Authentication/WsFederation/ADFS/SaveSigninToken       |                                                                                                                                                                                                               セッションの作成時に元のトークンが保存されるかを制御するブール値です。                                                                                                                                                                                                                |
|       Authentication/WsFederation/ADFS/ValidateActor        |                                                                                                                                                                                                   System.IdentityModel.Tokens.JwtSecurityToken.Actor を有効にする必要があるかどうかを示す値です。                                                                                                                                                                                                    |
|      Authentication/WsFederation/ADFS/ValidateAudience      |                                                                                                                                                                                                               対象者がトークンの検証時に検証されるかを制御するブール値です。                                                                                                                                                                                                               |
|       Authentication/WsFederation/ADFS/ValidateIssuer       |                                                                                                                                                                                                                発行者がトークンの検証時に検証されるかを制御するブール値です。                                                                                                                                                                                                                |
|      Authentication/WsFederation/ADFS/ValidateLifetime      |                                                                                                                                                                                                               有効期限がトークンの検証時に検証されるかを制御するブール値です。                                                                                                                                                                                                               |
|  Authentication/WsFederation/ADFS/ValidateIssuerSigningKey  |                                                                                                                                                         securityToken xmlns=<https://ddue.schemas.microsoft.com/authoring/2003/5> に署名したSystem.IdentityModel.Tokens.SecurityKey の検証を呼び出すかどうかを制御するブール値です。                                                                                                                                                          |
|            Authentication/WsFederation/ADFS/Whr             |                                                                                                                                       ID プロバイダー リダイレクト URL に "whr" パラメーターを指定します。 詳細情報:  [wsFederation](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation)。                                                                                                                                       |

## <a name="ws-federation-settings-for-pn-azure-active-directory"></a>[!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)] の WS-Federation 設定

[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD は標準の [WS-Federation](https://docs.microsoft.com/azure/active-directory/develop/active-directory-developers-guide) に準拠した Security Token Service として動作するため、AD FS を説明した前のセクションは [!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)] ([[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD](https://msdn.microsoft.com/library/azure/mt168838.aspx)) にも適用できます。 開始するには、[[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] 管理ポータル](https://msdn.microsoft.com/library/azure/hh967611.aspx#bkmk_azureportal) にサインインして、既存ディレクトリを作成または選択します。 ディレクトリが使用可能な場合、ディレクトリに [アプリケーションを追加](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications) するための説明に従います。

1.  ディレクトリの**アプリケーション**メニューの下で、**追加**を選択します。
2.  **自分の組織が作成するアプリケーションを追加**を選択します。
3.  カスタマイズされた**名前**をアプリケーションに指定して、**Web アプリケーションまたは Web API** の種類を選択します。
4.  **サインオン URL** および**アプリ ID URI** には、両方のフィールドにポータルの URL https://portal.contoso.com/ を指定します。
    - これは、**Wtrealm** サイトの設定値に相当します。
5.  この時点で、新しいアプリケーションが作成されます。 メニューの**構成**セクションに移動します。
6.  **シングル サインオン**セクションで、最初の**返信 URL** エントリを更新して URL https://portal.contoso.com/signin-azure-ad にパスを含めます。
    - これは、**Wreply** サイト設定値に相当します。
7.  フッターで**保存**を選択します。
8.  フッター メニュー で、**エンドポイントの表示**を選び、**フェデレーション メタデータ ドキュメント**フィールドを留意します。

    - これは、**MetadataAddress** サイト設定値に相当します。
    - フェデレーション メタデータ XML を表示するには、この URL をブラウザ ウィンドウに貼り付け、ルート要素の**エンティティ ID** 属性を注記します。
    - これは、**AuthenticationType** サイト設定値に相当します。

> [!Note]
> 標準の [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD 構成は、次の設定のみを使用します (値の例を含む):
> - Authentication/WsFederation/ADFS/MetadataAddress - https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/federationmetadata/2007-06/federationmetadata.xml
> - Authentication/WsFederation/ADFS/AuthenticationType - https://sts.windows.net/01234567-89ab-cdef-0123-456789abcdef/
>   - フェデレーション メタデータのルート要素の **entityID** 属性の値を使用 (**MetadataAddress URL** を上記のサイト設定の値のブラウザーで開く)
> - Authentication/WsFederation/ADFS/Wtrealm - https://portal.contoso.com/
> - Authentication/WsFederation/ADFS/Wreply - https://portal.contoso.com/signin-azure-ad

### <a name="see-also"></a>関連項目

[ポータル認証の構成](configure-portal-authentication.md)  
[ポータル用の認証 ID の設定](set-authentication-identity.md)  
[ポータル用 OAuth2 プロバイダーの設定](configure-oauth2-settings.md)  
[ポータルの Open ID 接続プロバイダーの設定](configure-openid-settings.md)  
[ポータルの SAML 2.0 プロバイダーの設定](configure-saml2-settings.md)  
