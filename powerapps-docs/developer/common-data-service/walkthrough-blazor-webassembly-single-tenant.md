---
title: 'チュートリアル: Common Data Service を使用して ASP.NET Core Blazor WebAssembly アプリを作成する | Microsoft Docs'
description: ''
keywords: ''
ms.date: 05/25/2020
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
ms.reviewer: pehecke
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 03762c1dc93b43b51691ed2e8687452055e8b9b1
ms.sourcegitcommit: 2caa32fdcbaef9acffb965138a77a91e31dc9ec1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2020
ms.locfileid: "3413449"
---
# <a name="tutorial-create-an-aspnet-core-blazor-webassembly-app-using-common-data-service"></a>チュートリアル: Common Data Service を使用して ASP.NET Core Blazor WebAssembly アプリを作成する

このチュートリアルの手順を使用して、Common Data Service に接続する Blazor WebAssembly アプリを作成します。 このトピックでは、特定の Common Data Service インスタンスとデータの取得で認証をおこなうための必要な手順を理解することに焦点を当てています。

Blazor WebAssembly は、ASP.NET Core Blazor、もう 1 つは Blazor Server で使用可能な 2 つのホスティング モデルの1つです。 違いの詳細については、[ASP.NET Core Blazor ホスティング モデル](/aspnet/core/blazor/hosting-models) をご覧ください。

このチュートリアルは、[安全な ASP.NET Core Blazor WebAssembly スタンドアロン アプリAzure Active Directory](/aspnet/core/security/blazor/webassembly/standalone-with-azure-active-directory) トピックにある指示に依存しています。 Common Data Service は認証に  Azure Active Directory (Azure AD) を使用することから、このチュートリアルでは、提供されているアプリ テンプレートを使用して作成された基本的なアプリを、Common Data Service に接続できるように変更する方法について説明します。

## <a name="goal"></a>目的

このチュートリアルを完了すると、認証されたユーザーがアクセスできる Common Data Service アカウント エンティティからのデータを表示する Blazor WebAssembly アプリが作成されます。

:::image type="content" source="media/blazor-webassembly-walkthrough-goal.png" alt-text=" このチュートリアルの目標を表します。":::


## <a name="prerequisites"></a>前提条件

このチュートリアルを使用するには、以下が必要です。

- [データベースで Common Data Service 環境に](https://docs.microsoft.com/power-platform/admin/create-environment#create-an-environment-with-a-database) アクセスする
- アカウントおよび連絡先エンティティへの読み取りアクセスを提供するセキュリティ ロールを持つ Common Data Service ユーザー
- Common Data Service 環境を使用する Azure AD テナントへアクセスする、アプリケーション管理者、アプリケーション開発者、クラウド アプリケーション管理者、またはハイブリッド ID 管理者の役割。
- C# プログラミング言語についての理解
- ASP.NET Core Blazor の理解は役に立ちますが必須ではありません
- **ASP.NET と Web 開発** ワークロードがインストールされた Visual Studio 2019 の最新のバージョン。


## <a name="step-1-verify-prerequisites-and-information-about-the-database"></a>ステップ 1: データベースに関する前提条件と情報を確認する

環境が適切に構成されていること、および手順 2 でアクションを実行する場所を理解していることを確認しましょう。

### <a name="verify-common-data-service-database"></a>Common Data Service データベースの検証

1. [Power Apps](https://make.powerapps.com/) にサインインします。
1. ナビゲート ウィンドウで **ソリューション** を選択します。

    :::image type="content" source="media/blazor-webassembly-walkthrough-maker-portal.png" alt-text=" Common Data Service データベースのない環境を示すメーカーポータル。":::

1. インストールされているソリューションのリストが表示されない場合は、上部にある環境セレクターを使用して、データベースがある別の環境を選択してください。 それ以外の場合は、新しい環境を作成します。

### <a name="get-the-common-data-service-web-api-uri"></a>Common Data Service Web API URI を入手する

インスタンス Web API サービスのルート URL が必要になります。 これは、自分の Common Data Service 環境の開発者向けリソースのページにあります。

[開発者向けリソースの表示またはダウンロード](view-download-developer-resources.md) にある指示に従って、URLをコピーします。 

次のように表示されます: `https://yourorgname.api.crm.dynamics.com/api/data/v9.1/`

### <a name="navigate-to-the-azure-active-directory-portal"></a>Azure Active Directory ポータルに移動する

1. [Power Apps](https://make.powerapps.com) にサインインします。
1. 左上隅の [ワッフル] アイコンで、**管理者** を選択します。

    :::image type="content" source="media/blazor-webassembly-walkthrough-navigate-admin-center.png" alt-text=" Microsoft 365 管理センター へのナビゲーション。":::

1. これにより、Microsoft 365 管理センターに移動します。 左側のナビゲーションで、**すべて表示** をクリックして、**Azure Active Directory** を選択します。

    :::image type="content" source="media/blazor-webassembly-walkthrough-navigate-AAD-from-admin-center.png" alt-text=" Azure Active Directory 管理センターへのナビゲーション。":::

1. これにより、Azure Active Directory 管理センターに移動します。 左側のナビゲーション ウィンドウを展開して、**Azure Active Directory** を選択します。

    :::image type="content" source="media/blazor-webassembly-walkthrough-aad-admin-center.png" alt-text="Azure Active Directory ページへのナビゲーション。":::

これにより、ステップ 2 の開始点に移動します。

## <a name="step-2-create-a-blazor-webassembly-standalone-app-using-azure-ad-for-authentication"></a>ステップ 2: 認証用に Azure AD を使用して Blazor WebAssembly スタンドアロンアプリを作成する

[ASP.NET Core Blazor WebAssembly スタンドアロンアプリを Azure Active Directory で保護する](/aspnet/core/security/blazor/webassembly/standalone-with-azure-active-directory) トピックでは、アプリを作成するための完全な手順が掲載されています。

これらのステップでは、Azure AD でアプリ登録を作成する方法と .NET Core CLI コマンドを実行して、Azure AD 認証のサポートを受けて基本的なアプリの足場を生成する方法について説明します。

> [!NOTE]
> 現時点では、.NET Core CLI コマンドを使用してアプリを生成する必要があります。 Visual Studio を使用してプロジェクトを作成する場合、この特定のタイプのアプリのテンプレートはありません。

[ASP.NET Core Blazor WebAssembly スタンドアロンアプリを Azure Active Directory で保護する](/aspnet/core/security/blazor/webassembly/standalone-with-azure-active-directory) に移動して、指示に従って、基本的なアプリ テンプレートを生成します。 

> [!NOTE]
> このセクションの残りのコンテンツでは、[ASP.NET Core Blazor WebAssembly スタンドアロンアプリを Azure Active Directory で保護する](/aspnet/core/security/blazor/webassembly/standalone-with-azure-active-directory) トピックで説明されている手順を完了するのに役立つ補足情報を提供します。 
> 
> これらの手順を完了するときにこれを確認することをお勧めしますが、必須ではありません。 完了したら、ここに戻って、[ステップ3 の API 権限を付与する](#step-3-grant-api-permissions) を開始してください。

アプリケーションの登録には、フォームへの記入があります。 リダイレクト URI のデフォルト値には、ポート値のプレースホルダーがあります。 登録を完了するには、プレースホルダーを数値に置き換える必要があります。たとえば、今は `1111` を加えてみます。 Visual Studio でプロジェクトを開いた後で、ランダムに生成されたポート値を提供できます。 [コールバック URL を更新する](#update-callback-url) を参照してください。

:::image type="content" source="media/blazor-webassembly-walkthrough-register-application.png" alt-text="Azure Active Directory でアプリケーションを登録するフォーム。":::

これにより、.NET Core CLI コマンドに含める必要がある 2 つの ID 値が生成されます。 以下のプレースホルダーがコンテンツで使用されます。 アプリケーション登録プロセスで生成された値を使用する必要があります。

- アプリケーション (クライアント) ID : プレースホルダー: `11111111-1111-1111-1111-111111111111`
- ディレクトリ (テナント) Id : プレースホルダー: `22222222-2222-2222-2222-222222222222`

> [!IMPORTANT]
> [ASP.NET Core Blazor WebAssembly スタンドアロン アプリを Azure Active Directory で保護する](/aspnet/core/security/blazor/webassembly/standalone-with-azure-active-directory) トピックの指示に従って、アクセストークンと ID トークンを有効にして、暗黙的な付与を有効にして変更を保存します。

.NET Core CLI コマンドはこの方法でフォーマットでき、プロジェクトを作成する場所を指定するパラメーターを含めることができます。 通常のコマンド ウィンドウでコマンドを実行できます。

```dotnetcli
dotnet new blazorwasm^
 -au SingleOrg^
 --client-id "11111111-1111-1111-1111-111111111111"^
 --tenant-id "22222222-2222-2222-2222-222222222222"^
 -o "A:\Projects\Blazor-Standalone-AAD Example"
```

コマンドを実行した後、出力フォルダーに移動し、Visual Studio 2019 を使用して.csproj ファイルを開きます。

:::image type="content" source="media/blazor-webassembly-walkthrough-application-files-folder.png" alt-text="Windows エクスプローラーで表示されたテンプレートによって生成されたファイル。":::

Visual Studio 2019 内でプロジェクトは次のようになります。

:::image type="content" source="media/blazor-webassembly-walkthrough-application-solution-explorer.png" alt-text="Visual Studio ソリューション エクスプローラーで表示されたテンプレートによって生成されたプロジェクト。":::

[ASP.NET Core Blazor WebAssembly スタンドアロンアプリを Azure Active Directory で保護する](/aspnet/core/security/blazor/webassembly/standalone-with-azure-active-directory) トピックの残りでは、アプリ テンプレートを作成するためのコンポーネントについて説明します。

### <a name="update-callback-url"></a>コールバック URL を更新する

Visual Studio が使用するポート設定はランダムに生成されます。 アプリケーションをデバッグできるように、アプリケーション登録のコールバック URI を更新する必要があります。

1. Visual Studio で、プロジェクトのプロパティを開き、**デバッグ** を選択します。

    :::image type="content" source="media/blazor-webassembly-walkthrough-project-debug-settings.png" alt-text="Visual Studio プロジェクトの [デバッグ] ページ。":::

1. **Web サーバー設定** で、デバッグ用に割り当てられたランダムなポートを含む **SSL を有効にする** 値をコピーします
1. Azure AD でアプリの登録に戻り、**認証** セクションで、**リダイレクト URI** を変更してこのルートURIを含め、変更を保存します

    :::image type="content" source="media/blazor-webassembly-walkthrough-application-redirect-uri.png" alt-text="登録されているアプリケーションの認証情報。":::

### <a name="verify-that-the-app-runs"></a>アプリが実行されることを確認する

これでリダイレクト URI が更新されました。Visual Studio で F5 を押してアプリを実行できます。

:::image type="content" source="media/blazor-webassembly-walkthrough-application-before-code-changes.png" alt-text="変更が行われる前の Blazor WebAssembly アプリの規定動作。":::

この時点で、ログインしているかどうかにかかわらず、アプリのすべての機能が動作します。 Azure AD テナントのメンバーのみがログインできます。

## <a name="step-3-grant-api-permissions"></a>ステップ 3: API アクセス許可を付与する

Common Data Service に接続するには、アプリが接続するためのアクセス許可を設定する必要があります。

1. Azure AD でアプリの登録に戻り、**API アクセス許可** セクションで、**権限を追加する** をクリックします。

    :::image type="content" source="media/blazor-webassembly-walkthrough-add-permissions.png" alt-text="登録済みアプリケーションの API 権限設定ページ。":::

1. **API 権限を要求する** エリアで、**自分の組織が使用する API** を選択して、*Common Data Service* を検索します。

    :::image type="content" source="media/blazor-webassembly-walkthrough-search-common-data-service-api.png" alt-text="Common Data Service のアクセス許可の検索。":::

1. **Common Data Service** を選択します。 
1. **user_impersonation** のアクセス許可を選択する

    :::image type="content" source="media/blazor-webassembly-walkthrough-user-impersonation-permission.png" alt-text="Common Data Service user_impersonation アクセス許可の追加。":::

    > [!NOTE]
    > Dynamics CRM と Common Data Service は同じサービスを参照します。

1. **アクセス許可の追加** をクリックします。
1. (オプション) **構成済みのアクセス許可** については、**自分の Azure Active Directory テナント名に管理者の同意を付与する** をクリックします。 下のスクリーンショットでは、テナント名は 'デフォルトディレクトリ' です。 あなたのものは違うかもしれません。

    :::image type="content" source="media/blazor-webassembly-walkthrough-grant-admin-consent.png" alt-text="登録済みアプリケーションの管理者の同意を付与するオプションボタンを表示するボタン。":::

## <a name="step-4-apply-code-changes"></a>ステップ 4: コードの変更を適用する

次のファイルに変更を適用して、アプリケーション内の Common Data Service データの表示を有効にします。

### <a name="wwwrootappsettingsjson"></a>\wwwroot\appsettings.json

このファイルには、テンプレートによって生成された構成情報と、Azure AD に登録されているアプリケーションに関する情報が含まれていることがわかります。 これは以下のように表示されます:

```json
{
  "AzureAd": {
    "Authority": "https://login.microsoftonline.com/22222222-2222-2222-2222-222222222222",
    "ClientId": "11111111-1111-1111-1111-111111111111",
    "ValidateAuthority": true
  }
}
```

ファイルを更新して、[Common Data Service Web API の URI を入手する](#get-the-common-data-service-web-api-uri) ステップでコピーした、**インスタンス Web API サービス ルート URL** のルートを含む新しい `CDSWebAPI` セクションを含めます。

> [!NOTE]
> 完全な URL は必要ありません。ルートのみです。

```json
{
  "AzureAd": {
    "Authority": "https://login.microsoftonline.com/22222222-2222-2222-2222-222222222222",
    "ClientId": "11111111-1111-1111-1111-111111111111",
    "ValidateAuthority": true
  },
  "CDSWebAPI": {
    "ResourceUrl": "https://yourorg.api.crm.dynamics.com",
    "Version": "v9.1",
    "TimeoutSeconds": 30
  }
}
```

### <a name="programcs"></a>Program.cs

1. `Microsoft.Extensions.Http` NuGet パッケージをインストールします。
    1. ソリューション エクスプローラーでプロジェクトを右クリックして、**NuGet パッケージを管理する...** を選択します。
    1. **閲覧する** を選択して、`Microsoft.Extensions.Http` を検索します。
    1. パッケージの最新版をインストールします。

    :::image type="content" source="media/blazor-webassembly-walkthrough-install-microsoft.extensions.http-nuget-package.png" alt-text="必要な NuGet パッケージのインストール":::

1. `builder.Services.AddTransient(sp => new HttpClient...` で始まる行の下に次のコードを追加します

    ```csharp
    // Get configuration data about the Web API set in wwwroot/appsettings.json
    var CDSWebApiConfig = builder.Configuration.GetSection("CDSWebAPI");
    var resourceUrl = CDSWebApiConfig.GetSection("ResourceUrl").Value;
    var version = CDSWebApiConfig.GetSection("Version").Value;
    var timeoutSeconds = int.Parse(CDSWebApiConfig.GetSection("TimeoutSeconds").Value);

    // Create an named definition of an HttpClient that can be created in a component page
    builder.Services.AddHttpClient("CDSClient", client =>
    {
        // See https://docs.microsoft.com/powerapps/developer/common-data-service/webapi/compose-http-requests-handle-errors
        client.BaseAddress = new Uri($"{resourceUrl}/api/data/{version}/");
        client.Timeout = TimeSpan.FromSeconds(timeoutSeconds);
        client.DefaultRequestHeaders.Add("OData-Version", "4.0");
        client.DefaultRequestHeaders.Add("OData-MaxVersion", "4.0");
    });
    ```

1. `builder.Configuration.Bind("AzureAd" ...` で始まる行の下に次のコードを追加します

    ```csharp
    // Add access to Common Data Service to the scope of the access token when the user signs in
    options.ProviderOptions.DefaultAccessTokenScopes.Add($"{resourceUrl}/user_impersonation");
    ```

### <a name="add-pagesfetchaccountsrazor"></a>\Pages\FetchAccounts.razor を追加します

これは、アカウント情報を表示する新しいページです。

1. ソリューション エクスプローラーで、**ページ** を右クリックして、**追加** > **Razor コンポーネント…** を選択します コンテキスト メニューから、`FetchAccounts.razor` と名前を付けます。
1. ファイルのコードを以下に置き換えます。

    ```cshtml
    @page "/fetchaccounts"
    @using Microsoft.AspNetCore.Components.WebAssembly.Authentication
    @using System.Net.Http.Headers
    @using System.Net.Http.Json
    @using Microsoft.Extensions.Logging;
    @using System.Text.Json.Serialization;
    @inject IAccessTokenProvider TokenProvider
    @inject IHttpClientFactory ClientFactory
    @inject ILogger<FetchAccounts> logger;

    <AuthorizeView>
        @*Only show the list if the user is signed in and authorized*@
        <Authorized>
            <h3>Fetch Accounts</h3>

            @if (accounts != null)
            {
                <table class="table">
                    <thead>
                        <tr>
                            <th>Name</th>
                            <th>Main Phone</th>
                            <th>City</th>
                            <th>Primary Contact</th>
                            <th>Email (Primary Contact)</th>
                        </tr>
                    </thead>
                    <tbody>
                        @foreach (Account account in accounts.value)
                        {
                            <tr id="@account.accountid">
                                <td>
                                    @((account.name != null)
                                    ? account.name
                                    : string.Empty)
                                </td>
                                <td>
                                    @((account.telephone1 != null)
                                    ? account.telephone1
                                    : string.Empty)
                                </td>
                                <td>
                                    @((account.address1_city != null)
                                    ? account.address1_city
                                    : string.Empty)
                                </td>
                                <td>
                                    @((account.primarycontactid != null)
                                    ? (account.primarycontactid.fullname != null
                                        ? account.primarycontactid.fullname
                                        : string.Empty)
                                    : string.Empty)
                                </td>
                                <td>
                                    @((account.primarycontactid != null)
                                    ? (account.primarycontactid.emailaddress1 !=null
                                        ? account.primarycontactid.emailaddress1
                                        : string.Empty)
                                    : string.Empty)
                                </td>
                            </tr>
                        }
                    </tbody>
                </table>
            }
            else
            {
                <p><em>@message</em></p>
            }
        </Authorized>
        <NotAuthorized>
            <h3>Authentication Failure!</h3>
            <p>You're not signed in.</p>
        </NotAuthorized>
    </AuthorizeView>


    @code {

        //The collection of Account records to display
        private AccountCollection accounts;

        //An informational message
        private string message = "Loading...";

        //Contains data about an error returned from the Web API
        private Error error;

        // Method invoked when the component is ready to start, having received its initial parameters from its parent in the render tree.
        // Override this method if you will perform an asynchronous operation and want the component to refresh when that operation is completed.
        protected override async Task OnInitializedAsync()
        {
            // Tries to get an access token for the current user with the default set of permissions.
            var tokenResult = await TokenProvider.RequestAccessToken();

            // If the token request was successful
            if (tokenResult.TryGetToken(out var token))
            {
                //Creates an HttpClient based on the named definition found in Program.Main
                var client = ClientFactory.CreateClient("CDSClient");

                //Prepare the request to get the data
                var request = new HttpRequestMessage()
                {
                    Method = HttpMethod.Get,
                    RequestUri = new Uri($"{client.BaseAddress}accounts?" +
                    "$select=name,telephone1,address1_city&" +
                    "$expand=primarycontactid($select=fullname,emailaddress1)")
                };
                //Add the access token
                request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", token.Value);
                //Specify a JSON result is expected
                request.Headers.Accept.Add(new MediaTypeWithQualityHeaderValue("application/json"));
                //Limit the number of results to 10
                request.Headers.Add("Prefer", "odata.maxpagesize=10");

                //Send the request
                var response = await client.SendAsync(request);

                if (response.IsSuccessStatusCode)
                {
                    //Parse the JSON returned into a strongly typed AccountCollection
                    accounts = await response.Content.ReadFromJsonAsync<AccountCollection>();
                }
                else
                {
                    //Parse the JSON returned into a strongly typed Error
                    error = await response.Content.ReadFromJsonAsync<Error>();
                    error.statuscode = (int)response.StatusCode;
                    error.reason = response.ReasonPhrase;
                    //Display a message to the user
                    message = "An error occurred.";
                    //Log the details so they can be seen in the browser console
                    logger.LogError($"{error.detail.message}");

                }

            }
            else
            {
                // Notify user that the token request was not successful
                message = "There was a problem authenticating.";
            }

        }


        // The result will be a JSON object with an array of entities set to the value property
        public class AccountCollection
        {
            public Account[] value { get; set; }
        }

        //Just the properties of the Account EntityType used for this sample
        // See https://docs.microsoft.com/dynamics365/customer-engagement/web-api/account
        public class Account
        {

            public Guid accountid { get; set; }

            public string name { get; set; }

            public string telephone1 { get; set; }

            public string address1_city { get; set; }

            public Contact primarycontactid { get; set; }

        }

        //Just the properties of the Contact EntityType that are expanded from the Account entity
        // See https://docs.microsoft.com/dynamics365/customer-engagement/web-api/contact
        public class Contact
        {

            public string fullname { get; set; }

            public string emailaddress1 { get; set; }
        }

        // Contains the error data returned by the Web API and the HttpMessageResponse
        public class Error
        {
            [JsonPropertyName("error")]
            public ErrorDetail detail { get; set; }
            public int statuscode { get; set; }
            public string reason { get; set; }

        }

        //Contains data from the Web API
        //See https://docs.microsoft.com/powerapps/developer/common-data-service/webapi/compose-http-requests-handle-errors#parse-errors-from-the-response
        public class ErrorDetail
        {
            public string code { get; set; }
            public string message { get; set; }

        }
    }
    ```

このコードでは、次のことが行われます。

1. 認証されたユーザーのみがデータを含むページを表示できるようにします。
1. 取得後にアカウント データを表示するテーブルを定義します。
1. accesstokenを要求し、次に HttpRequestMessage でそのトークンを使用して、Common Data Service からデータを取得します。
1. サービスから返された JSON が逆シリアル化されるときに厳密に型指定されたデータを有効にするクラスを定義します。

### <a name="sharednavmenurazor"></a>\Shared\NavMenu.razor

このファイルを編集して、fetchaccounts razor コンポーネント ページを追加します。

このノードを `<ul class="nav flex-column">` エレメント内の好きな場所に追加します。

```html
<li class="nav-item px-3">
    <NavLink class="nav-link" href="fetchaccounts">
        <span class="oi oi-list-rich" aria-hidden="true"></span> Fetch Accounts
    </NavLink>
</li>
```

## <a name="step-5-verify-it-works"></a>ステップ 5: 機能することを確認する

Visual Studio で、F5 キーを押して、コードを変更してアプリを起動します。

1. ログインする前に、**アカウントを取得** へナビゲートします。 エラー通知が表示されるはずです。
1. Common Data Service データにアクセスできるユーザーとしてログインします。

    > [!NOTE]
    > [ステップ 3: API 権限を付与する](#step-3-grant-api-permissions) で管理者の同意を付与しなかった場合、ユーザーには次のようなダイアログが表示されます。
    > 
    > :::image type="content" source="media/blazor-webassembly-walkthrough-request-consent-dialog.png" alt-text="アプリケーションに対して同意するようにユーザーに促すダイアログ。":::
    >
    > 続行するには **同意する** をクリックしてください。

1. **アカウントを取得** へナビゲートして、アカウント データが期待どおりに表示されることを確認します。

    :::image type="content" source="media/blazor-webassembly-walkthrough-goal.png" alt-text="完了が正常におこなわれた際に期待される最後の動作。":::

### <a name="see-also"></a>関連項目

[ASP.NET Core Blazor WebAssembly スタンドアロンアプリを Azure Active Directory で保護する](/aspnet/core/security/blazor/webassembly/standalone-with-azure-active-directory)<br />
[チュートリアル: アプリを Azure Active Directory に登録します](walkthrough-register-app-azure-active-directory.md)<br />
[Common Data Service で OAuth を使用する](authenticate-oauth.md)<br />
[ Common Data Service Web API を使用する](webapi/overview.md)