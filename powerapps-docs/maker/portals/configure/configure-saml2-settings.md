---
title: ポータル用 SAML 2.0 プロバイダー設定の構成 | MicrosoftDocs
description: ポータルの SAML 2.0 プロバイダー設定を追加およびコンフィギュレーションする指示をします。
author: sandhangitmsft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: sandhan
ms.reviewer: tapanm
ms.openlocfilehash: 3478fea889957b0e4a819231d9e89293b18506d3
ms.sourcegitcommit: c12260f372ad2cc48d3146be570d2088c9ef1d86
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2020
ms.locfileid: "3490045"
---
# <a name="configure-saml-20-provider-settings-for-portals"></a>ポータルの SAML 2.0 プロバイダー設定を構成します

外部認証を提供するには、1 つ以上の [SAML 2.0](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html)– 準拠の ID プロバイダー (IdP) を追加できます。 この文書は、ポータルをサービス プロバイダー (SP) として統合して機能させるための、さまざまな ID プロバイダーの設定方法について説明します。  

## <a name="ad-fs-idp"></a>AD FS (IdP)

[!include[](../../../includes/pn-active-dir-fed-svcs-ad-fs.md)] などの ID プロバイダーの設定です。

### <a name="create-an-ad-fs-relying-party-trust"></a>AD FS 証明書利用者信頼を作成

> [!Note]
> [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] スクリプトでこれらの手順を実行する方法については、後述の [PowerShell を使用して AD FS を構成する](#configure-ad-fs-by-using-powershell) を参照してください。

[!include[](../../../includes/pn-adfs-short.md)] 管理ツールを使い、**サービス** > **クレームの説明**の順に移動します。

1.  **クレーム内容を追加**を選択します。
2.  要求の指定:

    -  表示名:**永続的な識別子**

    -  要求の識別子:**urn:oasis:names:tc:SAML:2.0:nameid-format:persistent**

    -  **有効化**チェックボックス: このフェデレーション サービスが受け取ることができる要求の種類として、この要求の説明をフェデレーション メタデータで発行します。

    -  **有効化**チェックボックス: このフェデレーション サービスが送信できる要求の種類として、この要求の説明をフェデレーション メタデータで発行します。

3.  **OK** を選びます。

[!include[](../../../includes/pn-adfs-short.md)] 管理ツールを使用して、**信頼関係** > **証明書利用者信頼**を選択します。

1. **Relying Party Trust を追加**を選択します。
2. ようこそ: **スタート画面**の選択。
3. データ ソースの選択: **依拠当事者に関するデータを手動で入力**を選び、**次** を選択します。
4. ディスプレイ名を指定: 名前 を入力し、**次** を選択します。
   例: https://portal.contoso.com/
5. プロファイルの選択: **AD FS 2.0 プロファイル**を選択し、**次へ**を選択します。
6. 証明書の構成: **次へ**を選択します。
7. URL の構成: **SAML 2.0 WebSSO プロトコールのサポートを有効化**チェック ボックスを選択します。
   証明書利用者のSAML 2.0 SSOサービスURL:https://portal.contoso.com/signin-saml2を入力する
   - メモ: [!include[](../../../includes/pn-adfs-short.md)] はポータルが HTTPS で実行される必要があります。

   > [!Note] 
   > 結果のエンドポイントには、次の設定があります。 
   > - エンドポイントの種類:**SAML アサーションの消費エンドポイント**             
   > - バインド:**POST**                                            
   > - インデックス: n/a (0)                                              
   > - URL: **https://portal.contoso.com/signin-saml2**

8. IDの構成:https://portal.contoso.com/を指定して、**追加**を選択し、次いで**次へ**を選択します。
   必要であれば、各証明書利用者ポータルに ID をさらに追加できます。 ユーザーは、使用できるいずれかまたはすべての ID で認証できます。
9. 発行権限ルールの選択: **全てのユーザーが依存当事者にアクセスできるよう許可**を選び、**次** を選択します。
10. 信頼を追加する準備: **次へ**を選択します。
11. **クローズ**を選択します。

証明書利用者信頼に**名前 ID** 要求を追加します。

**[!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] アカウント名を** **名前 ID** 要求へ変換 (入力方向の要求を変換):

- 入力方向の要求の種類:**[!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] アカウント名**

- 出力方向の要求の種類: **名前 ID**

- 送信される名前 ID の形式: **永続的な識別子**

- すべての要求値をパス スルーする

### <a name="create-site-settings"></a>サイトの設定の作成

上述の [!include[](../../../includes/pn-adfs-short.md)] 証明書利用者信頼を参照するポータル サイト設定を適用します。

> [!Note]
> 標準[!include[](../../../includes/pn-adfs-short.md)] (IdP) 構成は、次の設定のみを使用します (例値を含む) : Authentication/SAML2/ADFS/MetadataAddress - <https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml>  
> - Authentication/SAML2/ADFS/AuthenticationType - https://adfs.contoso.com/adfs/services/trust    
>   -   フェデレーション メタデータのルート要素の **entityID** 属性の値を使用 (**MetadataAddress URL** を上記のサイト設定の値のブラウザーで開く) 
> - Authentication/SAML2/ADFS/ServiceProviderRealm - https://portal.contoso.com/  
> - Authentication/SAML2/ADFS/AssertionConsumerServiceUrl - https://portal.contoso.com/signin-saml2  
>   **フェデレーション メタデータ**は [!include[](../../../includes/pn-adfs-short.md)] サーバー: `Import-Module adfs`
>   `Get-ADFSEndpoint -AddressPath /FederationMetadata/2007-06/FederationMetadata.xml` で次のスクリプトを実行することで **[!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)]** で取得できます:

[プロバイダー] タグのラベルを置き換えて、複数の IdP サービスを構成することができます。 それぞれの固有のラベルは、IdP に関連する設定グループとなります。 例: ADFS、[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD、MyIdP


| サイト設定の名前                                             | 内容                                                                                                                                                                                                                                                                                                                                                                                                                             |
|---------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/Registration/ExternalLoginEnabled              | 外部アカウントのサインインと登録を有効化または無効化します。 既定値: true                                                                                                                                                                                                                                                                                                                                                            |
| Authentication/SAML2/[プロバイダー]/MetadataAddress             | 必須。 [!include[](../../../includes/pn-adfs-short.md)] (STS) サーバーの [WS-Federation](https://msdn.microsoft.com/library/bb498017.aspx) メタデータ URLです。 通常は次のパスで終わります:/FederationMetadata/2007-06/FederationMetadata.xml。 例: `https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml`。 [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.MetadataAddress](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.metadataaddress.aspx) |  
| Authentication/SAML2/[プロバイダー]/AuthenticationType          | 必須。 OWIN 認証のミドルウェアの種類を指定します。 フェデレーション メタデータ XML のルートで [entityID](https://docs.microsoft.com/azure/active-directory/develop/active-directory-federation-metadata) 属性の値を指定します。 例: `https://adfs.contoso.com/adfs/services/trust`。 [!include[](../../../includes/proc-more-information.md)] [AuthenticationOptions.AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx)                                                            |  
| Authentication/SAML2/[プロバイダー]/ServiceProviderRealm<br>または <br>Authentication/SAML2/[プロバイダー]/Wtrealm                      | 必須。 [!include[](../../../includes/pn-adfs-short.md)] 証明書利用者 ID です。 例: `https://portal.contoso.com/`。 [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.Wtrealm](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wtrealm.aspx)                       |  
| Authentication/SAML2/[プロバイダー]/AssertionConsumerServiceUrl<br>または<br>Authentication/SAML2/[プロバイダー]/Wreply                       | 必須。 [!include[](../../../includes/pn-adfs-short.md)] SAML コンシューマ アサーションのエンドポイントです。 例: https://portal.contoso.com/signin-saml2。 [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.Wreply](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wreply.aspx)                                                                                                                                                                                                  |  
| Authentication/SAML2/[プロバイダー]/Caption                     | 推奨要件。 ユーザーがサインインのユーザー インターフェイスに表示できるテキストです。 既定: [プロバイダー]。 [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.Caption](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.caption.aspx)                |  
| Authentication/SAML2/[プロバイダー]/CallbackPath                | 認証コールバックを処理する任意の制約されたパスです。 [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.CallbackPath](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.callbackpath.aspx)                                                                                                                                                                                                                      |  
| Authentication/SAML2/[プロバイダー]/BackchannelTimeout          | バック チャネル コミュニケーション用のタイムアウト値。 例: 00:05:00 (5 分)。 [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.BackchannelTimeout](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.backchanneltimeout.aspx)                                                                                                                                                                                                                   |  
| Authentication/SAML2/[プロバイダー]/UseTokenLifetime            | 認証セッションの有効期限 (例: クッキー) は認証トークンと一致する必要があることを示します。 [WsFederationAuthenticationOptions.UseTokenLifetime](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.usetokenlifetime.aspx)。                                                                                                                                                                               |  
| Authentication/SAML2/[プロバイダー]/AuthenticationMode          | OWIN 認証のミドルウェアのモードを指定します。 [!include[](../../../includes/proc-more-information.md)] [AuthenticationOptions.AuthenticationMode](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx)                                                                                                                                                                                                                                                                              |  
| Authentication/SAML2/[プロバイダー]/SignInAsAuthenticationType  | System.Security.Claims.ClaimsIdentity の作成時に使用される AuthenticationType です。 [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.SignInAsAuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.signinasauthenticationtype.aspx)                                                                                                                                                                                                 |  
| Authentication/SAML2/[プロバイダー]/ValidAudiences              | 対象者 URL のコンマ区切り一覧です。 [!include[](../../../includes/proc-more-information.md)] [TokenValidationParameters.AllowedAudiences](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.allowedaudiences.aspx)                                                                                                                                                                                                                                                                          |  
| Authentication/SAML2/[プロバイダー]/ClockSkew                   | 時間を有効にする際に適用するクロック スキューです。                                                                                                                                                                                                                                                                                                                                                                                          |
| Authentication/SAML2/[プロバイダー]/RequireExpirationTime       | トークンに "期限切れ" の値が必要かどうかを示す値です。                                                                                                                                                                                                                                                                                                                                                                      |
| Authentication/SAML2/[プロバイダー]/ValidateAudience            | 対象者がトークンの検証時に検証されるかどうかを制御するブール値です。                                                                                                                                                                                                                                                                                                                                                         |

### <a name="idp-initiated-sign-in"></a>IdP で開始されたサインイン

[!include[](../../../includes/pn-adfs-short.md)] は、SAML 2.0 の [仕様](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html#5.1.4.IdP-Initiated%20SSO:%20POST%20Binding|outline) の [IdP で開始されたシングル サインオン (SSO)](https://technet.microsoft.com/library/jj127245.aspx) プロファイルをサポートします。 IdP によって開始された SAML 要求に対して、ポータル (サービス プロバイダー) が適切に応答するためには、[RelayState](https://blogs.technet.com/b/askds/archive/2012/09/27/ad-fs-2-0-relaystate.aspx) パラメーターが適切にエンコードされている必要があります。  

SAML RelayState パラメータにエンコードされる基本的な文字列値は、**ReturnUrl=/content/sub-content/**, where **/content/sub-content/** の形式である必要があります。これは、ポータル (SP) に移動する Web ページへのパスです。 パスは、ポータルでの任意の有効な Web ページで置き換えることができます。 文字列値はエンコードされ、**RPID=&lt;URL エンコードされた RPID&gt;&RelayState=&lt;URL エンコードされた RelayState&gt;** の形式でコンテナ文字列の中に置かれます。 全体の文字列はさらにエンコードされ、**<https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx?RelayState=&lt;URL> エンコードされた RPID/RelayState&gt;** の形式で別のコンテナに追加されます。

たとえば、サービス プロバイダーのパスが **/content/sub-content/** および証明書利用者 ID が**https://portal.contoso.com/** であるとき、次の手順で URL が構築されます:

ReturnUrl=/content/sub-content/ の値をエンコードします

-   ReturnUrl%3D%2Fcontent%2Fsub-content%2F を取得するため

<!-- -->

-   値 https://portal.contoso.com/ のエンコード

<!-- -->

-   https%3A%2F%2Fportal.contoso.com%2F を取得するため

<!-- -->

-   RPID=https%3A%2F%2Fportal.contoso.com%2F&RelayState=ReturnUrl%3D%2Fcontent%2Fsub-content%2F の値をエンコードします

<!-- -->

-   RPID%3Dhttps%253A%252F%252Fportal.contoso.com%252F%26RelayState%3DReturnUrl%253D%252Fcontent%252Fsub-content%252F を取得するため

<!-- -->

-   AD FS IdP で開始された SSO パスを追加して、最終的な URL を取得します

<!-- -->

-   https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx?RelayState=RPID%3Dhttps%253A%252F%252Fportal.contoso.com%252F%26RelayState%3DReturnUrl%253D%252Fcontent%252Fsub-content%252F

次の [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] スクリプト (「Get-IdPInitiatedUrl.ps1」という名前でファイルに保存します) は、URL の構築に使用できます。

```
<#

.SYNOPSIS 

Constructs an IdP-initiated SSO URL to access a portal page on the service provider.

.PARAMETER path

The path to the portal page.

.PARAMETER rpid

The relying party identifier.

.PARAMETER adfsPath

The AD FS IdP initiated SSO page.

.EXAMPLE

PS C:\\> .\\Get-IdPInitiatedUrl.ps1 -path "/content/sub-content/" -rpid "https://portal.contoso.com/" -adfsPath "https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx"

#>

param

(

[parameter(mandatory=$true,position=0)]

$path,

[parameter(mandatory=$true,position=1)]

$rpid,

[parameter(position=2)]

$adfsPath = https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx

)

$state = ReturnUrl=$path

$encodedPath = [uri]::EscapeDataString($state)

$encodedRpid = [uri]::EscapeDataString($rpid)

$encodedPathRpid = [uri]::EscapeDataString("RPID=$encodedRpid&RelayState=$encodedPath")

$idpInitiatedUrl = {0}?RelayState={1} -f $adfsPath, $encodedPathRpid

Write-Output $idpInitiatedUrl
```

## <a name="saml-20-settings-for-pn-azure-active-directory"></a>[!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)]に対する SAML 2.0 設定

[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] は標準の [SAML 2.0](https://msdn.microsoft.com/library/azure/dn195591.aspx)&ndash; に準拠した IdP として動作するため、[!include[](../../../includes/pn-adfs-short.md)] を説明した前のセクションは [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD](https://msdn.microsoft.com/library/azure/mt168838.aspx) にも適用できます。 開始するには、[[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] 管理ポータル](https://msdn.microsoft.com/library/azure/hh967611.aspx#bkmk_azureportal) にサインインして、既存ディレクトリを作成または選択します。 ディレクトリが使用可能な場合、ディレクトリに [アプリケーションを追加](https://msdn.microsoft.com/library/azure/dn132599.aspx) するための説明に従います。  

1.  ディクショナリの**アプリケーション**メニューで、**追加**を選択します。
2.  **自分の組織が作成するアプリケーションを追加**を選択します。
3.  カスタマイズされた名前をアプリケーションに指定して、**Web アプリケーションまたは Web API** の種類を選択します。
4.  **サインオンURL**および**アプリID URI**には、両方のフィールドhttps://portal.contoso.com/にポータルの URL を指定します。
    これは、**ServiceProviderRealm** (Wtrealm) サイト設定値に相当します。
5. この時点で、新しいアプリケーションが作成されます。 メニューの**構成**セクションに移動します。

    **シングル サインオン**セクションで、最初の**返信URL**エントリを更新してURL https://portal.contoso.com/signin-azure-adにパスを含めます。

    **AssertionConsumerServiceUrl** (Wreply) サイトの設定値に対応します。

6. フッター メニュー で、**エンドポイントの表示**を選び、**フェデレーション メタデータ ドキュメント**フィールドを留意します。

これは、**MetadataAddress** サイト設定値に相当します。

-   フェデレーション メタデータ XML を表示するには、この URL をブラウザ ウィンドウに貼り付け、ルート要素の**エンティティ ID** 属性を注記します。
-   **AuthenticationType** サイトの設定値に対応します。

> [!Note]
> 標準[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD 構成は、次の設定のみを使用します (例値を含む) : Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD/MetadataAddress - <https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/federationmetadata/2007-06/federationmetadata.xml> 
> - Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/AuthenticationType - <https://sts.windows.net/01234567-89ab-cdef-0123-456789abcdef/>  
> - フェデレーション メタデータのルート要素の **entityID** 属性の値を使用 (**MetadataAddress URL** を上記のサイト設定の値のブラウザーで開く) 
> - Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/ServiceProviderRealm - <https://portal.contoso.com/>  
> - Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/AssertionConsumerServiceUrl - <https://portal.contoso.com/signin-azure-ad>                                                                                   |

## <a name="shibboleth-identity-provider-3"></a>Shibboleth ID プロバイダー 3

[Shibboleth ID プロバイダー](https://wiki.shibboleth.net/confluence/display/IDP30/Home) を IdP サービスとして正しく構成するには、次のガイドラインに従います。 説明では、IdPがドメインhttps://idp.contoso.comでホストされていると仮定します。  

フェデレーション メタデータURLはhttps://idp.contoso.com/idp/shibbolethである

-   IdP は、永続的な識別子を生成または提供するように構成されている必要があります。 [永続的な識別子の生成](https://wiki.shibboleth.net/confluence/display/IDP30/NameIDGenerationConfiguration)を有効にするには、手順に従ってください。  

-   IdP フェデレーション メタデータ (&lt;IDPSSODescriptor&gt;) は、[SSO リダイレクト バイディング](https://shibboleth.net/about/advanced.html) に含むように構成する必要があります。 [例](https://wiki.shibboleth.net/confluence/display/SHIB2/MetadataExample)。  

```
<SingleSignOnService Binding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-Redirect"

Location=https://idp.contoso.com/idp/profile/SAML2/Redirect/SSO/>
```

[metadata-providers.xml](https://wiki.shibboleth.net/confluence/display/IDP30/MetadataConfiguration)を設定して、サービス プロバイダー (証明書利用者) を構成します。  

-   各 サービス プロバイダー フェデレーション メタデータ (&lt;SPSSODescriptor&gt;) には、アサーションの顧客サービスへのポスト バインディングが含まれている必要があります。 1 つの方法は、[FilesystemMetadataProvider](https://wiki.shibboleth.net/confluence/display/IDP30/FilesystemMetadataProvider) を使用して次の内容を含む構成ファイルを参照することです。  

```
<AssertionConsumerService index=1 isDefault=true

Binding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-POST"

Location=https://portal.contoso.com/signin-saml2/>
```

場所属性は、**AssertionConsumerServiceUrl** (Wreply) 設定に対応します。

-   サービス プロバイダー フェデレーション メタデータは、**AuthenticationType** 設定に対応する EntityDescriptor の **entityID** 属性を指定する必要があります。

**&lt;EntityDescriptor entityID=<https://portal.local.contoso.com/&gt>;...**

> [!Note] 
> 標準の Shibboleth 構成は、次の設定のみを使用します (値の例を含む)。   
> Authentication/SAML2/Shibboleth/MetadataAddress - https://idp.contoso.com/idp/shibboleth   
> -   Authentication/SAML2/Shibboleth/AuthenticationType - https://idp.contoso.com/idp/shibboleth 
> -   フェデレーション メタデータのルート要素の **entityID** 属性の値を使用 (**MetadataAddress URL** を上記のサイト設定の値のブラウザーで開く)  
> -   Authentication/SAML2/Shibboleth/ServiceProviderRealm - https://portal.contoso.com/ 
> -   Authentication/SAML2/Shibboleth/AssertionConsumerServiceUrl - https://portal.contoso.com/signin-saml2 

### <a name="idp-initiated-sign-in"></a>IdP で開始されたサインイン

Shibboleth は、 SAML 2.0 の [仕様](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html#5.1.4.IdP-Initiated%20SSO:%20POST%20Binding|outline) の [IdP で開始された SSO](https://wiki.shibboleth.net/confluence/display/SHIB2/IdPUnsolicitedSSO) プロファイルをサポートします。 IdP によって開始された SAML 要求に対して、ポータル (サービス プロバイダー) が適切に応答するためには、RelayState パラメーターが適切にエンコードされている必要があります。  

SAML RelayState パラメータにエンコードされる基本的な文字列値は、**ReturnUrl=/content/sub-content/**, where **/content/sub-content/** の形式である必要があります。これは、ポータル (SP) に移動する Web ページへのパスです。 パスは、ポータルでの任意の有効な Web ページで置き換えることができます。 完全に IdP で開始された SSO URL は、<https://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO?providerId=&lt;URL> エンコードされたプロバイダー ID&gt;&target=&lt;URL エンコードされたリターン パス&gt; の形式である必要があります。

たとえば、サービス プロバイダーのパスが **/content/sub-content/** および証明書利用者IDが**https://portal.contoso.com/** であるとき、最終的なURLはhttps://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO?providerId=https%3A%2F%2Fportal.contoso.com%2F&target=ReturnUrl%3D%2Fcontent%2Fsub-content%2Fである

次の [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] スクリプト (「Get-ShibbolethIdPInitiatedUrl.ps1」という名前でファイルに保存します) は、URL の構築に使用できます。

```
<# 

.SYNOPSIS

Constructs an IdP initiated SSO URL to access a portal page on the service provider.

.PARAMETER path

The path to the portal page.

.PARAMETER providerId

The relying party identifier.

.PARAMETER shibbolethPath

The Shibboleth IdP-initiated SSO page.

.EXAMPLE

PS C:\\> .\\Get-ShibbolethIdPInitiatedUrl.ps1 -path "/content/sub-content/" -providerId "https://portal.contoso.com/" -shibbolethPath "https://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO"

#>

param

(

[parameter(mandatory=$true,position=0)]

$path,

[parameter(mandatory=$true,position=1)]

$providerId,

[parameter(position=2)]

$shibbolethPath = https://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO

)

$state = ReturnUrl=$path

$encodedPath = [uri]::EscapeDataString($state)

$encodedRpid = [uri]::EscapeDataString($providerId)

$idpInitiatedUrl = {0}?providerId={1}&target={2} -f $shibbolethPath, $encodedRpid, $encodedPath

Write-Output $idpInitiatedUrl
```

## <a name="configure-ad-fs-by-using-powershell"></a>PowerShell を使用した AD FS の構成

[!include[](../../../includes/pn-adfs-short.md)] の証明書利用者信頼を追加するプロセスは、[!include[](../../../includes/pn-adfs-short.md)] サーバーで次の [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] スクリプトを実行することによっても行うことができます (「Add-AdxPortalRelyingPartyTrustForSaml.ps1」という名前で内容をファイルに保存します)。 スクリプトの実行後、ポータル サイト設定の構成を続行します。

```
<# 

.SYNOPSIS

Adds a SAML 2.0 relying party trust entry for a website.

.PARAMETER domain

The domain name of the portal.

.EXAMPLE

PS C:\\> .\\Add-AdxPortalRelyingPartyTrustForSaml.ps1 -domain portal.contoso.com

#>

param

(

[parameter(Mandatory=$true,Position=0)]

$domain,

[parameter(Position=1)]

$callbackPath = /signin-saml2

)

$VerbosePreference = Continue

$ErrorActionPreference = Stop

Import-Module adfs

Function Add-CrmRelyingPartyTrust

{

param (

[parameter(Mandatory=$true,Position=0)]

$name

)

$identifier = https://{0}/ -f $name

$samlEndpoint = New-ADFSSamlEndpoint -Binding POST -Protocol SAMLAssertionConsumer -Uri (https://{0}{1} -f $name, $callbackPath)

$identityProviderValue = Get-ADFSProperties | % { $_.Identifier.AbsoluteUri }

$issuanceTransformRules = @'

@RuleTemplate = MapClaims

@RuleName = Transform [!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] Account Name to Name ID claim

c:[Type == "https://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname"]

=> issue(Type = "https://schemas.xmlsoap.org/ws/2005/05/identity/claims/nameidentifier", Issuer = c.Issuer, OriginalIssuer = c.OriginalIssuer, Value = c.Value, ValueType = c.ValueType, Properties["https://schemas.xmlsoap.org/ws/2005/05/identity/claimproperties/format"] = "urn:oasis:names:tc:SAML:2.0:nameid-format:persistent");

@RuleTemplate = LdapClaims

@RuleName = Send LDAP Claims

c:[Type == "https://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname", Issuer == "AD AUTHORITY"]

=> issue(store = "[!INCLUDE[pn-active-directory](../../../includes/pn-active-directory.md)]", types = ("https://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname", "https://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname", "https://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress"), query = ";givenName,sn,mail;{{0}}", param = c.Value);

'@ -f $identityProviderValue

$issuanceAuthorizationRules = @'

@RuleTemplate = AllowAllAuthzRule

=> issue(Type = https://schemas.microsoft.com/authorization/claims/permit, Value = true);

'@

Add-ADFSRelyingPartyTrust -Name $name -Identifier $identifier -SamlEndpoint $samlEndpoint -IssuanceTransformRules $issuanceTransformRules -IssuanceAuthorizationRules $issuanceAuthorizationRules

}

# add the 'Identity Provider' claim description if it is missing

if (-not (Get-ADFSClaimDescription | ? { $_.Name -eq Persistent Identifier })) {

Add-ADFSClaimDescription -name "Persistent Identifier" -ClaimType "urn:oasis:names:tc:SAML:2.0:nameid-format:persistent" -IsOffered:$true -IsAccepted:$true

}

# add the portal relying party trust

Add-CrmRelyingPartyTrust $domain
```

### <a name="see-also"></a>関連項目

[ポータル認証の構成](configure-portal-authentication.md)  
[ポータル用の認証 ID の設定](set-authentication-identity.md)  
[ポータル用 OAuth2 プロバイダーの設定](configure-oauth2-settings.md)  
[ポータルの Open ID 接続プロバイダーの設定](configure-openid-settings.md)  
[ポータル用 WS-Federation プロバイダーの設定](configure-ws-federation-settings.md)  
