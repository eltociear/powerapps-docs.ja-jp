---
title: Web API CDSWebApiService クラス (C#) (Common Data Service)| Microsoft Docs
description: このサンプル .NET Framework クラス ライブラリ プロジェクトは、Common Data Service Web API および C# を使用しているときにサービス クライアントを定義するアセンブリを示しています。
ms.custom: ''
ms.date: 04/20/2020
ms.service: powerapps
applies_to:
- Dynamics 365 (online)
author: JimDaly
ms.author: pehecke
ms.reviewer: pehecke
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5b0b8335352d80585a9f36494bc5b8f7a06b8b2b
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/21/2020
ms.locfileid: "3276708"
---
# <a name="web-api-cdswebapiservice-class-sample-c"></a>Web API CDSWebApiService クラス サンプル (C#)


これは、CDS Web API を使用しているときにサービスを定義するアセンブリを作成する .NET Framework クラス ライブラリ プロジェクトです。

このアセンブリは、次の方法を示します。

- 一般的な操作を HTTP メソッドで折り返して、コードを「[乾燥](/dotnet/architecture/modern-web-apps-azure/architectural-principles#dont-repeat-yourself-dry)」させます。
- スレッドセーフな方法で <xref:System.Net.Http.HttpClient> を管理します。
- クライアント アプリケーションで表示される、サービス保護の制限 API [429 要求が多すぎます](https://developer.mozilla.org/docs/Web/HTTP/Status/429) エラーを管理します。
    - 詳しくは：[サービス保護APIの制限](../../api-limits.md)を参照してください。

## <a name="example"></a>例

この例は、CDSWebAPIService インスタンスをインスタンス化し、取引先担当者レコードを作成する方法を示しています。

この例では、次に示すように、接続文字列が App.config ファイルに設定されていることを想定しています。

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <startup>
    <supportedRuntime version="v4.0"
                      sku=".NETFramework,Version=v4.7.2" />
  </startup>
  <connectionStrings>
    <add name="Connect"
         connectionString="Url=https://yourorg.api.crm.dynamics.com;
         Authority=null;
         ClientId=51f81489-12ee-4a9e-aaae-a2591f45987d;
         RedirectUrl=app://58145B91-0C36-4500-8554-080854F2AC97;
         UserPrincipalName=you@yourorg.onmicrosoft.com;
         Password=y0urp455w0rd;
         CallerObjectId=null;
         Version=9.1;
         MaxRetries=3;
         TimeoutInSeconds=180;
         "/>
  </connectionStrings>
</configuration>
```
コードは、接続文字列にアクセスして、CDSWebApiService をインスタンス化します。

```csharp
//Get configuration data from App.config connectionStrings
static readonly string connectionString = ConfigurationManager.ConnectionStrings["Connect"].ConnectionString;
static readonly ServiceConfig config = new ServiceConfig(connectionString);

    using (CDSWebApiService svc = new CDSWebApiService(config))
    {
        //Create a contact
        var contact1 = new JObject
            {
                { "firstname", "Rafel" },
                { "lastname", "Shillo" }
            };
        Uri contact1Uri = svc.PostCreate("contacts", contact1);
    }
```

## <a name="properties"></a>プロパティ​​

このクラスは、**BaseAddress** プロパティのみを公開します。 これは、<xref:System.Net.Http.HttpClient> が使用する構成済みの <xref:System.Net.Http.HttpClient.BaseAddress> です。 ほとんどの場合、相対 URI が想定されるため、必要なときに完全な URI を作成すると便利です。

## <a name="methods"></a>メソッド

このクラスには、次のパブリック メソッドが用意されています。

## <a name="postcreate"></a>[PostCreate]

エンティティを同期的に作成し、URI を返します。

### <a name="parameters"></a>パラメーター

|件名  |種類​​  |内容  |
|---------|---------|---------|
|entitySetName|<xref:System.String>|作成するエンティティの種類についてのエンティティ セット名。 |
|本文|[JObject](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_Linq_JObject.htm)|エンティティが作成するデータの内容|

### <a name="return-value"></a>戻り値

作成されたエンティティの <xref:System.Uri>

### <a name="remarks"></a>備考

エンティティの作成は一般的な操作であり、URI は`OData-EntityId` ヘッダーで返されるため、このメソッドが提供されます。 この特殊なメソッドを使用すると、[JObject](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_Linq_JObject.htm) のみを返す [Post](#post) メソッドのみを使用する場合よりコードを少なくできます。

詳細: [Web API を使用してエンティテ レコードを作成する](../create-entity-web-api.md)。

## <a name="postcreateasync"></a>PostCreateAsync

[PostCreate](#postcreate) の非同期バージョン。

## <a name="post"></a>事後

`POST` 要求を同期的に送信し、応答を [JObject](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_Linq_JObject.htm) として返します。

### <a name="parameters"></a>パラメーター

|件名  |種類​​  |内容  |
|---------|---------|---------|
|path|<xref:System.String>|要求を送信するための相対パス。 多くの場合、アクションの名前またはエンティティ セット名。|
|本文|[JObject](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_Linq_JObject.htm)|`POST` へのペイロード|
|ヘッダー|`Dictionary<string, List<string>>`|(オプション) 特別な動作を適用するために必要なヘッダー|

### <a name="return-value"></a>戻り値

応答を含む [JObject](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_Linq_JObject.htm)。

### <a name="remarks"></a>備考

このメソッドは、`POST` HTTP メソッドを使用するすべての操作に使用できますが、応答コンテンツのみが含まれます。 [PostCreate](#postcreate) を使用してエンティティを作成し、作成されたエンティティの URI のみを返します。

詳細:

- [返されるデータで作成する](../create-entity-web-api.md#create-with-data-returned)
- [Web API アクションの使用](../use-web-api-actions.md)


## <a name="postasync"></a>PostAsync

[Post](#post) の非同期バージョン。

## <a name="patch"></a>修正プログラム

`PATCH` 要求を同期的に送信します。

### <a name="parameters"></a>パラメーター

|件名  |種類​​  |内容  |
|---------|---------|---------|
|URI|<xref:System.Uri>|要求を送信するための相対パス。 多くの場合、特定のエンティティの Uri|
|本文|[JObject](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_Linq_JObject.htm)|送信するペイロード|
|ヘッダー|`Dictionary<string, List<string>>`|(オプション) 特別な動作を適用するために必要なヘッダー|

### <a name="remarks"></a>備考

パッチは、レコードの更新または Upsert に頻繁に使用されます。

詳細:

- [基本的な更新](../update-delete-entities-using-web-api.md#basic-update)
- [エンティティの Upsert](../update-delete-entities-using-web-api.md#upsert-an-entity)

## <a name="patchasync"></a>PatchAsync

[Patch](#patch) の非同期バージョン。

## <a name="get"></a>入手

`GET` 要求を同期的に送信し、データを返す

### <a name="parameters"></a>パラメーター

|件名  |種類​​  |内容  |
|---------|---------|---------|
|path|<xref:System.String>|返すリソースへの相対パス |
|ヘッダー|`Dictionary<string, List<string>>`|(オプション) 特別な動作を適用するために必要なヘッダー|

### <a name="return-value"></a>戻り値

要求されたデータを表す [JToken](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_Linq_JToken.htm)。

### <a name="remarks"></a>備考

詳細:

- [Web API を使用したクエリ データ](../query-data-web-api.md)
- [Web API を使用してエンティティ レコードを取得する](../retrieve-entity-using-web-api.md)
- [Web API 関数の使用](../use-web-api-functions.md)


## <a name="getasync"></a>GetAsync

[Get](#get) の非同期バージョン。

## <a name="delete"></a>削除​​

`DELETE` 要求を同期的に送信します。

### <a name="parameters"></a>パラメーター

|件名  |種類​​  |内容  |
|---------|---------|---------|
|URI|<xref:System.Uri>|削除するリソースの相対パス |
|ヘッダー|`Dictionary<string, List<string>>`|(オプション) 特別な動作を適用するために必要なヘッダー|

### <a name="remarks"></a>備考

詳細:

- [基本的な削除](../update-delete-entities-using-web-api.md#basic-delete)
- [エンティティへの参照の削除](../associate-disassociate-entities-using-web-api.md#remove-a-reference-to-an-entity)
- [単一のプロパティ値の削除](../update-delete-entities-using-web-api.md#delete-a-single-property-value)

## <a name="deleteasync"></a>DeleteAsync

[削除](#delete) の非同期バージョン。

## <a name="put"></a>プット

`PUT` 要求を同期的に送信します。

### <a name="parameters"></a>パラメーター

|件名  |種類​​  |内容  |
|---------|---------|---------|
|URI|<xref:System.Uri>|更新するリソースへの相対パス。|
|プロパティ|<xref:System.String>|更新するプロパティの名前|
|値|<xref:System.String>|設定する値|

### <a name="remarks"></a>備考

Put は、特定のエンティティ プロパティを更新するために使用されます。

**注意**: HTTP `PUT` メソッドは、メタデータの更新にも使用されます。 このメソッドはその目的には使用できません。 ビジネス データ専用です。

詳細: 

- [単一のプロパティ値の更新](../update-delete-entities-using-web-api.md#update-a-single-property-value)
- [単一値ナビゲーション プロパティでの参照の変更](../associate-disassociate-entities-using-web-api.md#change-the-reference-in-a-single-valued-navigation-property)


## <a name="putasync"></a>PutAsync

[Put](#put) の非同期バージョン。

## <a name="private-sendasync-method"></a>プライベート SendAsync メソッド

上記のすべてのメソッドは、プライベートな `SendAsync` メソッドを介して要求をルーティングします。 ここで、低レベルの共通ロジックが発生します。

このメソッドには、サービス保護 API 429 エラーを管理し、サービスで構成可能な回数だけそれらを再試行するロジックが含まれています。

これを行うには、実際の要求ではなく要求のコピーを送信します。これは、要求が破棄され、エラーが返された場合は再度送信できないためです。

Extensions.cs ファイルで定義されたカスタム <xref:System.Net.Http.HttpRequestMessage> `Clone` メソッドがあるため、要求のコピーを使用できます。

## <a name="oauthmessagehandler"></a>OAuthMessageHandler

内部 <xref:System.Net.Http.HttpClient> が CDSWebApiService コンストラクターで初期化されると、このクラスのインスタンスが <xref:System.Net.Http.HttpMessageHandler> として設定されます。 このクラスは ADAL ライブラリと連携して、要求が送信されるたびに `accessToken` が更新されるようにします。 `accessToken` の期限が切れると、ADAL ライブラリ メソッドが自動的に更新します。

詳細: [DelegatingHandler を示す例](../../authenticate-oauth.md#example-demonstrating-a-delegatinghandler)

## <a name="serviceconfig"></a>ServiceConfig

CDSWebApiService クラスは、ServiceConfig クラスを介して接続文字列で初期化する必要があります。

ServiceConfig コンストラクターは、通常は App.config 構成からの接続文字列を受け入れ、そこで定義されたデータは、CDSWebApiService コンストラクターが必要とする ServiceConfig インスタンスに解析されます。

### <a name="properties"></a>プロパティ​​

ServiceConfig クラスのプロパティは次のとおりです。

|件名|種類​​|内容|
|---------|---------|---------|
|オーソリティ|<xref:System.String>|許可されているユーザーに使用するオーソリティ。 既定: 「https://login.microsoftonline.com/common」|
|CallerObjectId|<xref:System.Guid>|ユーザーが他のユーザーを偽装するための Azure AD ObjectId。|
| クライアント ID|<xref:System.String>|Azure AD に登録されているアプリケーションの ID|
|MaxRetries|<xref:System.Byte>|サービス保護の制限によってブロックされた要求を再試行する最大試行回数。 既定値は 3 です。|
|パスワード|<xref:System.Security.SecureString>|ユーザー プリンシパルのパスワード|
|RedirectUrl|<xref:System.String>|Azure AD に登録されているアプリケーションのリダイレクト URL|
|TimeoutInSeconds|`ushort`|要求がキャンセルされる前に要求の完了を試みる時間。 既定値: 120 (2 分)|
|URL|<xref:System.String>|CDS 環境への URL、つまり 「https://yourorg.api.crm.dynamics.com」|
|UserPrincipalName|<xref:System.String>|ユーザーのユーザー プリンシパル名。 すなわち、you@yourorg.onmicrosoft.com|
|バージョン|<xref:System.String>|使用する Web API のバージョン。 既定: 「9.1」|

### <a name="example-connection-string"></a>接続文字列の例

CDSWebApiService を使用する各サンプルには、共通の App.config への参照と、「`Connect`」という名前の接続文字列値を読み取るコードが含まれています。 次に、その App.config の例を示します。

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <startup>
    <supportedRuntime version="v4.0"
                      sku=".NETFramework,Version=v4.7.2" />
  </startup>
  <connectionStrings>
    <add name="Connect"
         connectionString="Url=https://yourorg.api.crm.dynamics.com;
         Authority=null;
         ClientId=51f81489-12ee-4a9e-aaae-a2591f45987d;
         RedirectUrl=app://58145B91-0C36-4500-8554-080854F2AC97;
         UserPrincipalName=you@yourorg.onmicrosoft.com;
         Password=y0urp455w0rd;
         CallerObjectId=null;
         Version=9.1;
         MaxRetries=3;
         TimeoutInSeconds=180;
         "/>
  </connectionStrings>
</configuration>
```

**ClientId** と **RedirectUrl** の値は、サンプル アプリケーション用です。 これらを使用してサンプルを実行できますが、独自のアプリケーションを登録し、これらのプロパティに対応する値を入力する必要があります。 

詳細: [チュートリアル: Azure Active Directory でアプリを登録する](../../walkthrough-register-app-azure-active-directory.md)

## <a name="serviceexception"></a>ServiceException

このクラスは単に <xref:System.Exception> を拡張し、エラー応答から追加のプロパティを提供します。

### <a name="properties"></a>プロパティ​​

|件名  |種類​​  |内容  |
|---------|---------|---------|
|メッセージ|<xref:System.String>|プラットフォームから返されたメッセージ|
|エラー コード|<xref:System.Int32>|プラットフォームから返されたエラー コード|
|StatusCode|<xref:System.Int32>|<xref:System.Net.Http.HttpResponseMessage>.<xref:System.Net.Http.HttpResponseMessage.StatusCode>|
|ReasonPhrase|<xref:System.String>|<xref:System.Net.Http.HttpResponseMessage>.<xref:System.Net.Http.HttpResponseMessage.ReasonPhrase>|

## <a name="samples-using-this-class"></a>このクラスを使用したサンプル

次のサンプルでは、このクラスを使用しています。

- [Web API CDSWebApiService の基本操作のサンプル (C#)](cdswebapiservice-basic-operations.md)
- [Web API CDSWebApiService の並列操作のサンプル (C#)](cdswebapiservice-parallel-operations.md)
- [Web API CDSWebApiService の非同期並列操作のサンプル (C#)](cdswebapiservice-async-parallel-operations.md)