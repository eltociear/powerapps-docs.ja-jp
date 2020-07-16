---
title: ポータルの Azure AD B2C プロバイダー設定 | MicrosoftDocs
description: ポータルの Azure AD B2C プロバイダー設定を有効にするための手順。
author: sandhangitmsft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 01/03/2020
ms.author: sandhan
ms.reviewer: tapanm
ms.openlocfilehash: 457a7127102fa3cc1af37979bd281a5bc32288af
ms.sourcegitcommit: c12260f372ad2cc48d3146be570d2088c9ef1d86
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2020
ms.locfileid: "3494787"
---
# <a name="azure-ad-b2c-provider-settings-for-portals"></a>ポータルの Azure AD B2C プロバイダー設定

[!include[Azure](../../../includes/pn-azure-shortest.md)] Active Directory (Azure AD) は従業員または内部認証のために Office 365 および Dynamics 365 サービスを強化します。 [!include[Azure](../../../includes/pn-azure-shortest.md)] Active Directory B2C はその認証モデルを拡張したもので、ローカルの資格情報およびさまざまな一般的なソーシャル ID プロバイダーとのフェデレーションを通して外部顧客のサインインを可能にします。

ポータルの所有者は、[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C を ID プロバイダーとして受け入れるようにポータルを構成できます。 [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C はフェデレーション用の Open ID 接続をサポートしています。

[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C をポータル用の ID プロバイダーとして構成するプロセス中に、後にポータルを構成する間に使用することになる複数の値が生成されます。 次の表にこれらの値を書き留めることができます。 ポータルの構成中に、変数名をここで書き留めた値に置き換えます。

| 変数名     | 値 | 内容                                                           |
|-------------------|-------|-----------------------------------------------------------------------|
| アプリケーション名  |       | 証明書利用者としてのポータルを表すアプリケーションの名前 |
| アプリケーション ID    |       | Azure Active Directory B2C で作成されたアプリケーションに関連付けられているアプリケーション ID。  |
| 発行者 URL |       | メタデータ エンドポイントで定義された発行者 (iss) URL。                |
| フェデレーション名   |       | 'B2C' などのフェデレーション プロバイダーの種類を識別する一意の名前。 これは、この特定のプロバイダの構成設定をグループ化するためにサイト設定名の中で使用されます。                                                                      |
| | | |

### <a name="use-azure-ad-b2c-as-an-identity-provider-for-your-portal"></a>Azure AD B2C をポータル用の ID プロバイダーとして使用する

1. [Azure ポータル](https://portal.azure.com/)にサインインします。
1. [Azure AD B2C テナントの作成](https://docs.microsoft.com/azure/active-directory-b2c/active-directory-b2c-get-started)。
1. 左端のナビゲーション バーの **[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C** を選択します。
1. [Azure アプリケーションを作成](https://docs.microsoft.com/azure/active-directory-b2c/active-directory-b2c-app-registration#register-a-web-application)します。

   > [!Note]
   > **暗黙的なフローの許可**フィールドで**はい**を選択し、**返信 URL** フィールドでポータルの URL を指定する必要があります。 **返信 URL** フィールドの値は [ポータル ドメイン]/signin-[フェデレーション名] という形式である必要があります。 たとえば、`https://contosocommunity.microsoftcrmportals.com/signin-B2C` などとします。

1. アプリケーション名をコピーして、それを上記の表の「アプリケーション名」の値として入力します。
1. アプリケーション（クライアント）の ID をコピーして、それを上記の表の 「アプリケーション ID」 の値として入力します。
1. [サインアップまたはサインイン ポリシーを作成](https://docs.microsoft.com/azure/active-directory-b2c/active-directory-b2c-reference-policies#create-a-sign-up-or-sign-in-policy)します。
1. **Azure AD B2C** リソースに移動します。
1. ポリシー配下の **ユーザー フロー** を選択します。
1. 新たに作成したサイン アップとログインのポリシーを選択します。
1. **設定**リストから、**プロパティ**を選択します
1. **トークンの互換性設定** 配下の **発行者 (iss) 要求** リストから、パスに **/tfp** が入っている URL を選択します。
1. ポリシーを保存します。
1. **このポリシーの メタデータ エンドポイント**フィールドで URL を選択します。
1. 発行者フィールドの値をコピーして、それを前述の表の「発行者 URL」の値として入力します。 

## <a name="portal-configuration"></a>ポータル構成

[!include[Azure](../../../includes/pn-azure-shortest.md)] で B2C テナントを作成および構成したら、Open ID 接続プロトコルを使用して [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C とフェデレーションするようにポータルを構成する必要があります。 [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C へのフェデレーションの一意の名前&mdash;たとえば B2C&mdash;を作成し、それを上記の表の*フェデレーション名*変数の値として保存する必要があります。

### <a name="configure-your-portal"></a>ポータルを構成する
1. ポータル管理アプリを開きます。
2. **ポータル** > **Web サイト**に移動します。
3. [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C を有効にする必要がある Web サイト レコードを選択します。
4. **サイト設定**に移動します。
5. 次のサイト設定を作成します。
   -   **名前**: Authentication/OpenIdConnect/[フェデレーション名]/Authority

       **値**：[発行元の URL]
   -   **名前**: Authentication/OpenIdConnect/[フェデレーション名]/ClientId

       **値**: [アプリケーション ID]
   -   **名前**: Authentication/OpenIdConnect/[フェデレーション名]/RedirectUri

       **値**: [ポータル ドメイン]/signin-[フェデレーション名]

       例: `https://mysite.com/signin-b2c` 
6. フェデレーション サインアウトをサポートするには、次のサイト設定を作成します。
   - **名前**: Authentication/OpenIdConnect/[フェデレーション名]/ExternalLogoutEnabled

     **値**: true
7. ポータルを単一の ID プロバイダーにハードコードするには、次のサイト設定を作成します。
   - **名前**: Authentication/Registration/LoginButtonAuthenticationType

     **値**：[発行元の URL]

8. パスワード リセットをサポートするには、[こちら](#password-reset)で説明されている必要なサイト設定を作成します。
9. クレーム マッピングをサポートするには、[こちら](#claims-mapping)で説明されている必要なサイト設定を作成します。

関連するサイト設定の完全なリストについては、[こちら](#related-site-settings)を参照してください。

### <a name="password-reset"></a>パスワードのリセット

[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C ローカル アカウントでパスワード リセットをサポートする場合は、次のサイト設定が必要です。

| サイト設定                                                        | 説明                                                                                                          |
|---------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| Authentication/OpenIdConnect/[フェデレーション名]/PasswordResetPolicyId | パスワード リセット ポリシーの ID。                                                                                     |
| Authentication/OpenIdConnect/[フェデレーション名]/ValidIssuers         | [発行者 URL] とパスワード リセット ポリシーの発行者を含む、発行者のコンマ区切りリスト。 |
|Authentication/OpenIdConnect/[フェデレーション名]/DefaultPolicyId | サインインまたはサインアップ ポリシーの ID。|
|||

### <a name="related-site-settings"></a>関連するサイト設定

ポータルで次のサイト設定を作成または構成し、[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C を ID プロバイダーとしてサポートすることができます。


| サイト設定                                                         | 内容                                                                                                                                                                                                                                                        |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/Registration/ProfileRedirectEnabled                   | 正常なサインインの後に、ポータルがユーザーをプロフィール ページにリダイレクトできるかどうかを指定します。 既定では true に設定されています。                                                                                                                                            |
| Authentication/Registration/EmailConfirmationEnabled                 | 電子メールの検証が必要かどうかを指定します。 既定では true に設定されています。                                                                                     |
| Authentication/Registration/LocalLoginEnabled                        | ローカル サインインが必要かどうかを指定します。 既定では true に設定されています。                                                                        |
| Authentication/Registration/ExternalLoginEnabled                     | 外部認証を有効または無効にします。       |
| Authentication/Registration/AzureADLoginEnabled                      | [!include[Azure](../../../includes/pn-azure-shortest.md)] AD を外部 ID プロバイダーとして有効または無効にします。 既定では true に設定されています。                                                                                                                                                                      |
| Authentication/OpenIdConnect/[フェデレーション名]/ExternalLogoutEnabled | フェデレーションによるサインアウトを有効または無効にします。true に設定すると、ユーザーはポータルからサインアウトしたときにフェデレーション サインアウト ユーザー エクスペリエンスにリダイレクトされます。 false に設定すると、ユーザーはポータルからのみサインアウトします。 既定では false に設定されています。               |
| Authentication/LoginTrackingEnabled                                  | ユーザーの最後のサインインの追跡を有効または無効にします。 true に設定すると、取引先担当者レコードの**最後のサインイン成功**フィールドに日時が表示されます。 既定では、これは false に設定されています。                                                            |
| Authentication/OpenIdConnect/[フェデレーション名]/RegistrationEnabled   | 既存の ID プロバイダーの登録要件を有効または無効にする。 true に設定すると、サイト設定 Authentication/Registration/Enabled も true に設定されている場合にのみ、既存のプロバイダーの登録が有効になります。 既定では true に設定されています。 |
|Authentication/OpenIdConnect/[フェデレーション名]/PostLogoutRedirectUri |ユーザーがサインアウトした後にリダイレクトする先の、ポータル内の URL を指定します。 |
| | |

### <a name="related-content-snippet"></a>関連コンテンツ スニペット

ユーザーが招待状を引き換えた後にユーザーの登録が無効である場合、次のコンテンツ スニペットを使用してメッセージを表示します。

**名前**: Account/Register/RegistrationDisabledMessage

**値**: 登録が無効になっています。

## <a name="customize-the-includeazure-ad-b2c-user-interface"></a>[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C のユーザー インターフェイスをカスタマイズする

[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C はユーザー インターフェイスのカスタマイズをサポートしています。 サインアップおよびサインイン シナリオのユーザー エクスペリエンスをカスタマイズできます。

### <a name="step-1-create-a-web-template"></a>ステップ 1: Web テンプレートの作成
次の値を使用して Web テンプレートを作成します。

**名前**: [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C カスタム ページ

**ソース**: 次のサンプルの Web テンプレート ソース HTML を使用します。

```html
<!DOCTYPE html>
<html lang=en-US>
  <head>
    <meta charset=utf-8>
    <meta name=viewport content=width=device-width, initial-scale=1.0>
    <meta http-equiv=X-UA-Compatible content=IE=edge>
    <title>
      {{ page.title | h }}
    </title>
                        <link href={{ request.url | base }}/bootstrap.min.css rel=stylesheet>
                        <link href={{ request.url | base }}/theme.css rel=stylesheet>
                        <style>
                          .page-heading {
            padding-top: 20px;
      }
      .page-copy {
            margin-bottom: 40px;
      }
      .highlightError {
        border: 1px solid #cb2027!important;
        background-color: #fce8e8!important;
      }
      .attrEntry .error.itemLevel {
        display: none;
        color: #cb2027;
        font-size: .9em;
      }
      .error {
        color: #cb2027;
      }
      .entry {
        padding-top: 8px;
        padding-bottom: 0!important;
      }
      .entry-item {
        margin-bottom: 20px;
      }
      .intro {
        display: inline;
        margin-bottom: 5px;
      }
      .pageLevel {
          width: 293px;
          text-align: center;
          margin-top: 5px;
          padding: 5px;
          font-size: 1.1em;
          height: auto;
      }
      #panel, .pageLevel, .panel li, label {
          display: block;
      }
      #forgotPassword {
          font-size: .75em;
          padding-left: 5px;
      }
      #createAccount {
          margin-left: 5px;
      }
      .working {
          display: none;
          background: url(data:image/gif;base64,R0lGODlhbgAKAPMAALy6vNze3PTy9MTCxOTm5Pz6/Ly+vNTS1Pz+/�N0Jp6BUJ9EBIISAQAh+QQJCQAKACxRAAIABgAGAAAEE1ClYU4RIIMTdCaegVCfRASCEgEAOw==) no-repeat;
          height: 10px;
          width: auto;
      }
      .divider {
        margin-top: 20px;
        margin-bottom: 10px;
      }
      .divider h2 {
        display: table;
        white-space: nowrap;
        font-size: 1em;
        font-weight: 700;
      }
      .buttons {
        margin-top: 10px;
      }
      button {
            width:auto;
            min-width:50px;
            height:32px;
            margin-top:2px;
            -moz-border-radius:0;
            -webkit-border-radius:0;
            border-radius:0;
            background:#2672E6;
            border:1px solid #FFF;
            color:#fff;
            transition:background 1s ease 0s;
            font-size:100%;
            padding:0 2px
      }

      button:hover {
            background:#0F3E83;
            border:1px solid #3079ed;
            -moz-box-shadow:0 0 0;
            -webkit-box-shadow:0 0 0;
            box-shadow:0 0 0
      }
      .password-label label {
        display: inline-block;
        vertical-align: baseline;
      }
      img {
            border:0
      }
      .divider {
            margin-top:20px;
            margin-bottom:10px
      }
      .divider h2 {
            display:table;
            white-space:nowrap;
            font-size:1em;
            font-weight:700
      }
      .divider h2:after,.divider h2:before {
            border-top:1px solid #B8B8B8;
            content:'';
            display:table-cell;
            position:relative;
            top:.7em;
            width:50%
      }
      .divider h2:before {
            right:1.8%
      }
      .divider h2:after {
            left:1.8%
      }
      .verificationErrorText {
            color:#D63301
      }
      .options div {
            display:inline-block;
            vertical-align:top;
            margin-top:7px
      }
      .accountButton,.accountButton:hover {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAh1BMVEX///9QUFBOTk5LS0tERERCQkI/Pz9ISEg6OjpGRkZNTU08PDyAgID09PSlpaWWlpZxcXFgYGBZWVlUVFT6+vrx8fHt7e3s7Ozo6Oji4uLJycnGxsa4uLiqqqqgoKCNjY2JiYmGhoZra2tmZmb7+/vu7u7d3d3U1NTNzc2+vr67u7usrKx7e3vprNQnAAAA8klEQVQ4y63Q127DMAxAUZpDwyMeSdqsNqu7/f/va6zahgGJKAr0vgk6DyQh+6V/BiTOOeNRA9zuAWBdM6WBlPDTvaUUoAuMrT0mgNvA1IJjQB3MKjACvp6DK0WAH+agtH8H9jQHLUUgz7Uhx8xOXzNESxirLCYA2mw8tacI5FyIYXq8A9ge2Qs6oTnw2e2ruho2rjBcXJ4ADh3jBOQLQnVhRFx2gNDZ4ACogbHXj/ft9Dj5AcgbJFu5AThQWuYBIGmgtAFQo4EFB+CPGthJAPypgY3BHsheA5UNwLyAvsYNoDyroKUe4EoFTQ/yDtTONvsGUJ8KTUYyH+UAAAAASUVORK5CYII=);
            background-repeat:no-repeat
      }
      .accountButton {
            border:1px solid #FFF;
            color:#FFF;
            margin-left:0;
            margin-right:2px;
            transition:background-color 1s ease 0s;
            -moz-border-radius:0;
            -webkit-border-radius:0;
            border-radius:0;
            text-align:center;
            word-wrap:break-word;
            height:34px;
            width:158px;
            padding-left:30px;
            background-color:#505050;
      }
      .accountButton:hover {
            background-color:#B9B9B9;
            border:1px solid #FFF;
            -moz-box-shadow:0 0 0;
            -webkit-box-shadow:0 0 0;
            box-shadow:0 0 0
      }
      .accountButton:focus {
            outline:gold solid 1px
      }
      #MicrosoftAccountExchange {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAPFBMVEU1pe/////t+v4uoe5btvNixPVVwfUsoe9tyfXU7/y95vu24vrd9f5NtfLH6/ys3/o/sPE6qfD2/f+f2vnAysuQAAAAaElEQVQ4y93SORKAIAwFUEGCsoT1/nd1JkkDFhY24qt+8VMkk20lu6DAaVBOBsVKsuO8aYo08IqlYyxoRTQExfyKheRIgu5Yl4KoVhSUgNOhoiYRsmb5g2u+LtzXDNOhjKgoAZ9/8k8uZWsGqcIav5wAAAAASUVORK5CYII=);
            background-color:#33A7F2
      }
      #MicrosoftAccountExchange:hover {
            background-color:#ADDBF9
      }
      #GoogleExchange {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAb1BMVEXcTkH////cTD/bSj3ZQDLYOyzaRDbeV0vbSDrZPS/66Obyv7rsnpfpkorjcWfgZlvXOCr++Pj5393haFz88/L88fD67Or319T1zsv1zsrxuLPuqaLuqKLoi4LlfXTgYlbWMyTWMiPwtrHwta/fXVH/sCIIAAAAmElEQVQ4y+2RyQ7DIBBDMcwAIXvovqXb/39jRaX0AEmr5px3tSV7PGLhX6TVRFpN61l9zPNS6kn9gDcXO67zDnCnO2BCiNIyMtgKKJgyY2zQ68JEDtqju0nFTcOsxPUMw1GDDUqt+tY51/YNVlhvacTgEfCDIY0Q/lkBSg4RaUmmDo4/JdMzHy1Q2ejMeCj6PrXQP5+1MI8X0Y4HL4c826EAAAAASUVORK5CYII=);
            background-color:#DC4E41
      }
      #GoogleExchange:hover {
            background-color:#F1B8B3
      }
      #TwitterExchange {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAdVBMVEVgqd3///9Ypdtdp9xaptxSotpQodlNn9lWo9pUo9rX6Pa+2vGTw+iLvuZlqt79/P7K4PO62O+y0+6hyutysuD2+fzi7vne6/fT5PTE3fKs0O2lzeuZx+l7tuJqrd71+Pzz9vzn8PnQ4/SCueSAueNsrt9InNh7sQwBAAAAwklEQVQ4y92PRw6EMAwAXeIkdBbY3uv/n7gSAoLDD5hbPCPZgZVihEgYgNSUpmfS7bfbtHS2nReyL2Qoc+yp8ZRAwCEWjgGAPQ7sssKoAGsWBrrgyMZCwD77Uel+59E3Tt14xZ7qlY7BRf1CDgeMKMw8sBXGlKxWtLGvHCgkQ80m0YHpjjq4sQ74pn1mISLJVSAMiwJO98l/TWSNF1eGKzqKfZ7Vj0mnHHwodpP+WIYlZP373DTtVWxYr2FD3pOBdfIHhOAHYHQI9VgAAAAASUVORK5CYII=);
            background-color:#60A9DD
      }
      #TwitterExchange:hover {
            background-color:#BFDCF1
      }
      #FacebookExchange {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAaVBMVEU7W5z///85Wps3WJsiRo8xU5fw8vYyUpY0VZiAj70pS5OBkb0vUpb7+fwsTpTR1ud6irllerBPaqX09fnx8vfs7fSQoMZxg7VsgLNGY6FCX58ZP4v++/7r7vTZ3OupstGIlsFWcalDYaCK3qwDAAAAnklEQVQ4y+XQyw7CIBAFUBgc5VUoWGtb3/7/RyoYkyZAiSsXvdt7kstA/hRg/B0GpZ6byQ3Dw0NBaH+lMYRle3T0kwayACRdBrr/gnN+QtpQWv8cR4DswiUAjozlz4RdF8AmlnmwjaDQImoZwQkRedoToUS7D+ColGoTwQidx8oEQDMHN1MBva5MOL70SCHuE1TOhOpHrRt0FWAOP4IX8PsG2qEOR30AAAAASUVORK5CYII=);
            background-color:#3B5B9C
      }
      #FacebookExchange:hover {
            background-color:#B0BDD7
      }
      #LinkedInExchange {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAb1BMVEUAe7b///8AdrMklscAc7EAeLUAcbB5ttifzeMqmckAdLIAaqz7+/6PxeAShr0CgLkAba4nmMctksTv9Puw1eij0OWGvNtfrNJNo80YjMAeib/D4vGt3Oy82+yfzOOCvtyJvdx3tddirtI/ncoxmMj9KsrQAAAAw0lEQVQ4y9WSVw7DIAxAG8CkjJDVzO5x/zMWk0RNJaB/kfo+sGUeCMvstgI4J7F9aS5NxSLnTWLpZVDgexTqIiycUNBhgTxRyCKPYJ3dl7sITCkO+FyLXaWU310DscASOesf3ahWChGJ5cb4ASO5Joiu2EegWEmZa1c3yUwOHmHNuQgJup4CgF8YlKpcMhKvkNmb1REz6hdetsyziIBldv8lpH8ouGm28zQFCu2SOSAXlJYGYCgpFThEMFPm/zCryja8Acy7CRfMrcKPAAAAAElFTkSuQmCC);
            background-color:#0077B5
      }
      #LinkedInExchange:hover {
            background-color:#99CAE1
      }
      #AmazonExchange {
            background-image:url(https://images-na.ssl-images-amazon.com/images/G/01/lwa/btnLWA_gold_156x32.png);
            background-color:#FFF;
            color:transparent
      }

      #next {
            -moz-user-select:none;
            user-select:none;
            cursor:pointer;
            width:auto;
            padding-left:10px;
            padding-right:10px;
            height:30.5px;
            -moz-border-radius:0;
           -webkit-border-radius:0;
            border-radius:0;
            background:#2672E6;
            border:1px solid #FFF;
            color:#fff;
            transition:background 1s ease 0s;
            font-size:100%
      }
      #next:hover {
            background:#0F3E83;
            border:1px solid #FFF;
            box-shadow:0 0 0
      }
      #next:hover,.accountButton:hover {
            -moz-box-shadow:0 0 0;
            -webkit-box-shadow:0 0 0;
            box-shadow:0 0 0;
      }
                        </style>
  </head>
  <body>
    <div class=navbar navbar-inverse navbar-static-top role=navigation>
      <div class=container>
        <div class=navbar-header>
          <div class=visible-xs-block>
            {{ snippets[Mobile Header] }}
          </div>
          <div class=visible-sm-block visible-md-block visible-lg-block navbar-brand>
            {{ snippets[Navbar Left] }}
          </div>
        </div>
      </div>
    </div>
    <div class=container>
      <div class=page-heading>
        <ul class=breadcrumb>
          <li>
            <a href={{ request.url | base }} title=Home>Home</a>
          </li>
          <li class=active>{{ page.title | h}}</li>
        </ul>
        {% include 'Page Header' %}
     </div>
     <div class=row>
      <div class=col-md-12>
        {% include 'Page Copy' %}
        <div id=api></div>
      </div>
     </div>
    </div>
    <footer role=contentinfo>
      <div class=footer-top hidden-print>
        <div class=container>
          <div class=row>
            <div class=col-md-6 col-sm-12 col-xs-12 text-left>
               {{ snippets[About Footer] }}
            </div>
            <div class=col-md-6 col-sm-12 col-xs-12 text-right>
              <ul class=list-social-links>
                <li><a href=#><span class=sprite sprite-facebook_icon></span></a></li>
                <li><a href=#><span class=sprite sprite-twitter_icon></span></a></li>
                <li><a href=#><span class=sprite sprite-email_icon></span></a></li>
              </ul>
            </div>
          </div>
        </div>
      </div>
      <div class=footer-bottom hidden-print>
        <div class=container>
          <div class=row>
            <div class=col-md-4 col-sm-12 col-xs-12 text-left>
               {{ snippets[Footer] | liquid }}
            </div>
            <div class=col-md-8 col-sm-12 col-xs-12 text-left >
            </div>   
          </div>
        </div>
      </div>
    </footer>
  </body>
</html>
```
### <a name="step-2-create-a-page-template"></a>ステップ 2: ページ テンプレートの作成

次のページ テンプレートを作成します
- **名前**: [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C カスタム ページ
- **種類**: Web テンプレート
- **Web テンプレート**: [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C カスタム ページ
- **Web サイトのヘッダーとフッターの使用**: このチェック ボックスをオフにする

### <a name="step-3-create-a-webpage"></a>ステップ 3: Web ページの作成

次の Web ページを作成します。
- **名前**: サインイン
- **親**ページ: ホーム
- **部分 URL**: azure-ad-b2c-sign-in
- **ページ テンプレート**: [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C カスタム ページ
- **公開状態**: 公開済み

### <a name="step-4-create-site-settings"></a>ステップ 4: サイト設定の作成

[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C がカスタム ページを要求し、サインインまたはサインアップのユーザー インターフェイスを挿入できるようにするには、クロス オリジン リソース共有 (CORS) を構成するサイト設定が必要です。 次のサイト設定を作成します。

| 名前                              | 値                             |
|-----------------------------------|-----------------------------------|
| HTTP/Access-Control-Allow-Methods | GET、OPTIONS                      |
| HTTP/Access-Control-Allow-Origin  | `https://login.microsoftonline.com` |
| | |

他の CORS 設定の完全なリストについては、「[CORS プロトコル サポート](../add-web-resource.md#cors-protocol-support)」を参照してください。

### <a name="step-5-includeazure-configuration"></a>ステップ 5: [!include[Azure](../../../includes/pn-azure-shortest.md)] の構成

1. [!include[Azure portal](../../../includes/pn-azure-portal.md)]にサインインします。
2. **[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C テナント管理** ブレードに移動します。
3. **設定** > **サインアップまたはサインイン ポリシー**に移動します。 使用できるポリシーの一覧が表示されます。
4. 編集するポリシーを選択します。
5. **編集**を選択します。
6. **ポリシーの編集** > **ページの UI カスタマイズ** > **統合サインアップまたはサインイン ページ**を選択します。
7. **カスタムページを使用する**を**はい**に設定します。
8. **カスタム ページ URI** を、この手順のステップ 3 で作成した [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C カスタム ページ Web ページの URL に設定します。 たとえば、`https://mydomain.com/azure-ad-b2c-sign-in` などとします。
9. **OK** を選びます。

## <a name="claims-mapping"></a>クレーム マッピング

初めてでもそれ以降でも、ユーザーがサインインすると、フェデレーション ID プロバイダーはユーザーのサインインに関するデータベースに基づいたクレームを提供します。 これらのクレームは、ID プロバイダーで構成できます。

### <a name="includeazure-ad-b2c-email-claims"></a>[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 電子メール クレーム

[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C はコレクションとして電子メール クレームを送信します。 ポータルは、コレクション内で提供される最初の電子メールを取引先担当者の既定電子メールアドレスとして受け取ります。

### <a name="claims-to-support-sign-up-scenarios"></a>サインアップ シナリオをサポートするクレーム

Common Data Service に存在しない新規顧客がプロビジョニングされると、インバウンド クレームを使用してポータルが作成する新しい取引先担当者レコードをシードできます。 一般的なクレームには名と姓、電子メール アドレス、および電話番号を含めることができますが、それらは構成可能です。 次のサイト設定が必要です。

**名前**: Authentication/OpenIdConnect/[フェデレーション名]/RegistrationClaimsMapping

**説明**: 登録中に作成された取引先担当者レコードの属性にクレーム値をマップするのに使用される、論理名 / クレーム ペアのリスト。

**形式**: attribute1=claim1,attribute2=claim2,attribute3=claim3

例: firstname=<https://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname,lastname=https://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname,jobtitle=jobTitle>

> [!NOTE]
> 電子メール アドレスを、取引先担当者の主要電子メール (emailaddress1) にマッピングします。 第二電子メール (emailaddress2) または代替電子メール (emailaddress3) を取引先担当者レコードに追加して、それを電子メールにマッピングした場合、ID 情報はその取引先担当者に追加されず、第一電子メール (emailaddress1) 内の登録セットに使用する電子メール アドレスで新しい ID 情報が作成されます。

### <a name="claims-to-support-sign-in-scenarios"></a>サインイン シナリオをサポートするクレーム

Common Data Service と ID プロバイダーのデータは直接リンクされていませんので、同期しなくなるかもしれません。ポータルには、Common Data Service で更新するサインイン イベントから受け入れるクレームのリストが必要です。 これらのクレームは、サインイン シナリオから入ってくるクレームのサブセット、またはそれと同等である可能性があります。 重要なポータル属性を上書きしてしまうことがないように、これはサインイン クレーム マッピングとは別に構成する必要があります。 次のサイト設定が必要です。

**名前**: Authentication/OpenIdConnect/[フェデレーション名]/LoginClaimsMapping

**説明**: サインイン後に作成された取引先担当者レコードの属性にクレーム値をマップするのに使用される、論理名 / クレーム ペアのリスト。

**形式**: attribute1=claim1, attribute2=claim2, attribute3=claim3

例: firstname=<https://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname,lastname=https://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname,jobtitle=jobTitle> 

クレーム名は、サインイン ポリシーの [アプリケーション] クレームで属性の横に表示されている [クレームの種類] フィールドです。

### <a name="allow-auto-association-to-a-contact-record-based-on-email"></a>電子メールに基づいて取引先担当者レコードへの自動関連付けを許可する 

電子メールが関連付けられて取引先担当者レコードを取得した顧客は、外部ユーザーが電子メール検証メカニズムを使用して [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C でサインインする Web サイトを立ち上げます。 新しいサインインは、重複レコードを作成するのではなく、既存の取引先担当者レコードと関連付ける必要があります。 この機能は、アクティブな ID を持たない取引先担当者のみを正常にマップするので、電子メール アドレスは一意である (複数の取引先担当者レコードに関連しない) 必要があります。 次のサイト設定が必要となります:

**名前**: Authentication/[プロトコル]/[プロバイダー]/AllowContactMappingWithEmail

**説明**: 取引先担当者が対応する電子メールにマップされるかどうかを指定します。 この設定を true に設定すると、一意の取引先担当者レコードが一致する電子メールアドレスに関連付けられ、ユーザーが正常にサインインした後に自動的に外部 ID プロバイダーがその取引先担当者に割り当てられます。 ここは既定では、 *False* に設定されています。

**名称**: Authentication/UserManager/UserValidator/RequireUniqueEmail

**説明**: ユーザーの検証に一意の電子メールアドレスが必要かどうかを指定します。 既存の連絡先電子メールアドレスを使用してサインインする場合は、設定を false に設定する必要があります。 既定では *true* に設定されており、電子メールアドレスがすでに存在する取引先担当者レコードの場合は、サインインに失敗する場合があります。
