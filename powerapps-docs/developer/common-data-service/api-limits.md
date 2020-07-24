---
title: サービス保護 API の制限 (Common Data Service) | Microsoft Docs
description: API 要求に対するサービス保護制限について理解します。
ms.custom: ''
ms.date: 04/20/2020
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 9f349a913056fe2a964db537b62774eccabdc21e
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/21/2020
ms.locfileid: "3275795"
---
# <a name="service-protection-api-limits"></a>サービス保護の API 制限

すべてのユーザーに一貫した可用性とパフォーマンスを確実に提供するために、API の使用方法にいくつかの制限を適用します。 これらの制限は、クライアント アプリケーションがサーバー リソースに対して異常な要求を行っていることを検出するように設計されています。

これらの制限が対話型クライアントの標準ユーザーに影響しないようにします。 異常な API 要求を実行するクライアント アプリケーションのみが影響を受けます。 この制限は、Common Data Service プラットフォームの可用性とパフォーマンス特性に対する脅威となる、ランダムに発生する予期しない要求数の急増に備えて一定レベルの保護を提供します。

クライアント アプリケーションが非常に負荷の高い要求を行うと、Common Data Service はオンライン サービスの一般的なパターンに従います。 要求が多すぎることを示すエラーを返します。

- Web API を使用して、[429 要求が多すぎます](https://developer.mozilla.org/docs/Web/HTTP/Status/429)エラーを返します。
- 組織サービスを使用すると、3 つの特定のエラー コードの 1 つを含む、[OrganizationServiceFault](/dotnet/api/microsoft.xrm.sdk.organizationservicefault) エラーが表示されます。 詳細: [返されたサービス保護 API の制限エラー](#service-protection-api-limit-errors-returned)


## <a name="impact-on-client-applications"></a>クライアント アプリケーションへの影響

サービス保護 API の制限エラーを管理するのはクライアント アプリケーションの責任です。 このエラーを正確に管理する方法は、アプリケーションの性質によって異なります。 

### <a name="interactive-client-applications"></a>対話型クライアント アプリケーション

サービス保護制限は十分に高いため、通常の使用中に、対話型クライアント アプリケーションを使用している個人に発生することはめったにありません。 ただし、クライアント アプリケーションで一括操作が許可されている場合は可能です。 クライアント アプリケーションの開発者は、サービス保護 API の制限がどのように適用されるかを認識し、ユーザーが非常に負荷の高い要求をサーバーに送信する可能性を減らすように UI を設計する必要があります。 ただし、サービス保護 API の制限エラーが発生する可能性があり、処理できるように準備しておく必要があります。

クライアント アプリケーションの開発者は、ユーザーにメッセージを表示するために単にエラーをスローするべきではありません。 エラー メッセージはエンド ユーザーを対象としたものではありません。 特定の方法については、「[操作の再試行](#retry-operations)」を参照してください。

### <a name="data-integration-applications"></a>データ統合アプリケーション

データを CDS にロードするか、一括更新を実行するように設計されたアプリケーションは、サービス保護 API の制限エラーを管理できなければなりません。 これらのアプリケーションはスループットを優先するので、最短時間で作業を完了できます。 これらのアプリケーションには、操作を再試行する方法が必要です。 最大のスループットを得るために適用できる方法はいくつかあります。 詳細: [スループットを最大化する方法](#how-to-maximize-throughput)。

### <a name="portal-applications"></a>ポータル アプリケーション

ポータル アプリケーションは通常、単一のサービス プリンシパル アカウントを通じて匿名ユーザーから要求を送信します。 サービス保護 API の制限はユーザー単位のため、ポータル アプリケーションは、ポータルで発生するトラフィック量に基づいてサービス保護 API の制限に達する可能性があります。 対話型クライアント アプリケーションと同様に、サービス保護 API の制限エラーがポータル エンド ユーザーに表示されることは想定されていません。 UI が、それ以上の要求を無効にし、サーバーがビジーであるというメッセージを表示するようにします。 メッセージには、アプリケーションが新しい要求の受け入れを開始できる時間が含まれる場合があります。

## <a name="impact-on-plug-ins-and-custom-workflow-activities"></a>プラグインおよびユーザー定義ワークフロー活動の影響

プラグインとユーザー定義ワークフロー活動は、受信要求によってトリガーされるビジネス ロジックを適用します。 サービス保護制限は、プラグインおよびユーザー定義ワークフロー活動には適用されません。 プラグインとユーザー定義ワークフロー活動がアップロードされ、分離されたサンドボックス サービス内で実行されます。 Common Data Service サンドボックス サービスで呼び出される操作は、パブリック API エンドポイントを使用しません。

アプリケーションがユーザー定義ロジックをトリガーする操作を実行する場合、プラグインまたはユーザー定義ワークフロー活動によって送信された要求の数は、サービス保護 API の制限にカウントされません。 ただし、これらの操作がもたらす追加の計算時間は、それらをトリガーした最初の要求に追加されます。 この計算時間は、サービス保護 API の制限の一部です。 詳細: [サービス保護 API の制限の適用方法](#how-service-protection-api-limits-are-enforced)

## <a name="retry-operations"></a>再試行操作

サービス保護 API の制限エラーが発生すると、ユーザーからの新しい要求が処理されるまでの期間を示す値が提供されます。

- 429 エラーが Web API から返された場合、応答には[後に試行](https://developer.mozilla.org/docs/Web/HTTP/Headers/Retry-After)の秒数が含まれます。
- 組織サービスでは、[TimeSpan](/dotnet/api/system.timespan)値が <xref:Microsoft.Xrm.Sdk.OrganizationServiceFault>.<xref:Microsoft.Xrm.Sdk.BaseServiceFault.ErrorDetails> で返されます `Retry-After` キーを使用するコレクション。

### <a name="interactive-application-re-try"></a>対話型アプリケーションの再試行 

クライアントが対話型アプリケーションの場合、ユーザーが行った要求を再試行する間、サーバーがビジーであることを示すメッセージを表示する必要があります。 ユーザーが操作をキャンセルするためのオプションを提供することができます。 送信した前の要求が完了するまで、ユーザーがそれ以上要求を送信できないようにします。

### <a name="non-interactive-application-re-try"></a>非対話型アプリケーションの再試行

クライアントが対話型でない場合、一般的には、要求が再度送信される前に、期間が経過するのを待つだけです。 これは通常、[Thread.Sleep](/dotnet/api/system.threading.thread.sleep) または同等のメソッドを使用して、現在のスレッドの実行を一時停止することによって行われます。



## <a name="how-service-protection-api-limits-are-enforced"></a>サービス保護 API の制限の適用方法

サービス保護 API の制限は、5 分 (300 秒) のスライディング ウィンドウ内で評価されます。 前の 300 秒以内にいずれかの制限を超えた場合、後続の要求でサービス保護 API の制限エラーが返され、Retry-After 期間が終了するまでサービスを保護します。

サービス保護 API の制限は、ユーザーごとに評価されます。 認証された各ユーザーは個別に制限されます。 特別な要求をしているユーザー アカウントのみが制限されます。 他のユーザーは影響を受けません。

サービス保護 API の制限は、次の 3 つのファセットに基づいて実施されます。

- ユーザーが送信した要求の数。
- ユーザーが送信した要求を処理するために必要だった合計実行時間。
- ユーザーが送信した同時実行要求の数。

ユーザーが送信する要求の数に制限がある場合は、それをバイパスすることができます。 これらの試行に対して他のファセットが追加されました。 たとえば、次のようなものです。

- バッチ操作でバンドルすることにより、送信する要求を減らすことができます。
  - 合計実行時間制限はこれに対するものです。
- 要求を連続して個別に送信するのではなく、サービス保護 API の制限が適用される前に、5 分間のスライディング ウィンドウ内に多数の同時実行要求を送信できます。
  - 同時実行要求制限はこれに対するものです。

環境で利用可能な各 Web サーバーは、これらの制限を個別に適用します。 ほとんどの環境には、複数の Web サーバーがあります。 試用環境には、単一の Web サーバーのみが割り当てられます。 ご使用の環境で使用できる Web サーバーの実際の数は、提供する管理されたサービスの一部である複数の要因によって異なります。 要因の 1 つは、購入したユーザー ライセンスの数です。

次の表に、5 分間のスライディング ウィンドウ内で *Web サーバーごと*に適用されるデフォルトのサービス保護 API の制限を示します。

|メジャー|内容|Web サーバーごとの制限|
|--|--|--|
|要求の数|ユーザーが行った要求の累積数。|6000|
|実行時間|ユーザーが行ったすべての要求の合計実行時間。| 20 分 (1200 秒)|
|同時実行要求の数|ユーザーが行った同時実行要求の累積数|52|

> [!IMPORTANT]
> これらの制限は変更される可能性があり、環境によって異なる場合があります。 これらの数値はデフォルト値を表し、予期できる値についてのアイデアを提供しています。

### <a name="the-retry-after-duration"></a>Retry-After 期間

`Retry-After` 期間は、直前の 5 分間に送信された操作の性質によって異なります。 要求の負荷が高いほど、サーバーの回復に時間がかかります。

現在、制限の評価方法により、サービス保護 API の制限が有効になるまでに、要求数と実行時間の制限が 5 分間超えることが予想されます。 ただし、同時実行要求の数を超えるとすぐにエラーが返されます。 アプリケーションがこのように負荷の高い要求を送信し続ける場合、共有リソースへの影響を最小限に抑えるために期間が延長されます。 これにより、個々の Retry-After 期間が長くなるため、アプリケーションが待機している間、非アクティブ状態の期間が長くなります。 この動作は将来変更される可能性があります。

可能であれば、要求の数を減らし、サービス保護 API の制限に達するまで徐々に増やして、一定のレートを達成することをお勧めします。 その後、5 分以内に処理できる要求の数をサーバーに通知します。 要求の最大数をこの 5 分の期間内に制限し、徐々に増やしていくと、Retry-After 期間を低く抑え、合計スループットを最適化し、サーバー リソースのスパイクを最小限に抑えられます。

## <a name="service-protection-api-limit-errors-returned"></a>返されたサービス保護 API の制限エラー

このセクションでは、返される可能性のある 3 種類のサービス保護 API の制限エラーと、これらのエラーの原因となる可能性のある軽減策について説明します。

- **エラー コード**は、組織サービス <xref:Microsoft.Xrm.Sdk.OrganizationServiceFault>.<xref:Microsoft.Xrm.Sdk.BaseServiceFault.ErrorDetails> によって返される数値のエラー値です。
- **16 進コード**は、Web API から返される 16 進数のエラー値です。

### <a name="number-of-requests"></a>要求の数

この制限は、前の 300 秒間の要求の総数をカウントします。

| エラー コード | 16 進コード | メッセージ |
|------------|------------|-------------------------------------|
|`-2147015902`|`0x80072322`|`Number of requests exceeded the limit of 6000 over time window of 300 seconds.`|

アプリケーションでユーザーが一括操作を実行できる場合以外、対話型アプリケーションの一般的なユーザーが、この制限を超える 1 分あたり 1,200 の要求を送信することはできません。

たとえば、リスト ビューで一度に 250 レコードの選択が可能で、ユーザーがこれらすべてのレコードに対して何らかの操作を実行できる場合、ユーザーはこの操作を 300 秒間に 24 回実行する必要があります。 ユーザーは各リストの操作を 12.5 秒以内に完了する必要があります。

アプリケーションがこの機能を提供する場合、以下の方法のいくつかを検討する必要があります。

- リストで選択できるレコードの総数を減らします。 リストに表示されるアイテムの数を 50 に減らすと、ユーザーはこの操作を 300 秒以内に 120 回実行する必要があります。 ユーザーは各リストの操作を 2.5 秒以内に完了する必要があります。
- 選択した操作をバッチに結合します。 バッチには最大 1000 個の操作を含めることができ、要求数の制限を回避できます。 ただし、実行時間の制限に備える必要があります。

### <a name="execution-time"></a>実行時間

この制限は、先行する 300 秒間に受信した要求の合計実行時間を追跡します。

| エラー コード | 16 進コード | メッセージ |
|------------|------------|-------------------------------------|
|`-2147015903`|`0x80072321`|`Combined execution time of incoming requests exceeded limit of 1,200,000  milliseconds over time window of 300 seconds. Decrease number of concurrent requests or reduce the duration of requests and try again later.`|

一部の操作では、他の操作よりも多くのリソースが必要です。 バッチ操作、インポート ソリューション、および非常に複雑なクエリでは、負荷が非常に高くなる場合があります。 これらの操作は、同時実行要求で同時に実行することもできます。 したがって、5 分のウィンドウ内で、合計で 20 分を超える合計計算時間を必要とする操作を要求することができます。

この制限は、要求数の制限を回避するためにバッチ操作と同時実行要求を使用する方法が使用されている場合に発生する可能性があります。

### <a name="concurrent-requests"></a>同時実行要求

この制限は、前の 300 秒間の同時実行要求の総数を追跡します。

| エラー コード | 16 進コード | メッセージ |
|------------|------------|-------------------------------------|
|`-2147015898`|`0x80072326`|`Number of concurrent requests exceeded the limit of 52.`|

クライアント アプリケーションは、要求を個別に連続して送信するだけではありません。 クライアントは、並列プログラミング パターンやさまざまなメソッドを適用して、複数の要求を同時に送信できます。 サーバーは、同じユーザーからの複数の要求に同時に応答していることを検出できます。 この同時実行要求数を超えると、このエラーがスローされます。

同時実行要求を送信することは、スループットを最大化するための方法の重要な部分ですが、制御下に置いておくことが重要です。

[.NET における並列プログラミング](/dotnet/standard/parallel-programming/)を使用する場合、デフォルトの並列度は、コードを実行しているサーバーの CPU コアの数によって異なります。 52 を超えないようにしてください。 [ParallelOptions.MaxDegreeOfParallelism プロパティ](/dotnet/api/system.threading.tasks.paralleloptions.maxdegreeofparallelism)を同時実行タスクの最大数を定義するように設定できます。

## <a name="how-to-maximize-throughput"></a>スループットを最大化する方法

最短期間でほとんどのデータを移動するため、スループットを優先する必要があるアプリケーションの場合に適用できる方法がいくつかあります。

### <a name="let-the-server-tell-you-how-much-it-can-handle"></a>サーバーがどれだけ処理できるかを通知するようにします

一度に送信する要求の数を計算しようとしないでください。 それぞれの環境は異なる場合があります。 制限に達し始めるまで要求を送信するレートを徐々に上げて、サービス保護 API の制限の `Retry-After` 値に応じて、いつさらに送信すべきかを通知します。 この値は、スループット総数を可能な限り高いレベルに保ちます。

### <a name="use-multiple-threads"></a>複数のスレッドの使用

同時スレッド数の上限を、アプリケーションでパフォーマンスを大幅に向上させるために使用できます。 これは、個々の操作が比較的速い場合に当てはまります。 処理するデータの性質によっては、最適なスループットを得るためにスレッド数を調整する必要があります。

詳細:

- [Web API でタスク並列ライブラリを使用する](#use-task-parallel-library-with-web-api)
- [CrmServiceClient でタスク並列ライブラリを使用する](#use-task-parallel-library-with-crmserviceclient)

### <a name="avoid-batching"></a>バッチの回避

組織サービスでは、一般的に <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> を使用して、複数の操作をバンドルします。 主な利点は、ネットワーク経由で送信する必要のある SOAP XML ペイロードの総量が削減されることです。 これにより、ネットワーク遅延が問題となる場合にパフォーマンスを向上できます。

これまで、パフォーマンスへの影響のため ExecuteMultiple 操作は一度に 2 つに制限されていました。 サービス保護 API の制限により、この制限は冗長になり、当てはまらなくなりました。

ほとんどのシナリオでは、高度な並列処理で単一の要求を送信するのが最も高速です。 バッチ サイズによってパフォーマンスが向上する可能性がある場合は、10 の小さなバッチサイズから始めて、再試行するサービス保護 API の制限エラーが発生し始めるまで、同時実行数を増やすことをお勧めします。

Web API を使用する場合、個々の要求に対してネットワーク経由で送信される JSON ペイロードが小さいため、ネットワーク遅延は問題ではありません。 $batch を使用して送信されるペイロードの総量は、個々の要求を送信するよりも多くなります。 変更セットを使用してトランザクションを管理する場合にのみ、$batch を使用してください。 詳細: [Web API を使用してバッチ操作を実行する](webapi/execute-batch-operations-using-web-api.md)

> [!NOTE]
> バッチ操作は、権利制限を回避するための有効な方法ではありません。 サービス保護 API の制限と権利制限は別々に評価されます。 権利制限は CRUD 操作に基づいており、それらがバッチ操作に含まれているかどうかにかかわらず発生します。 詳細: [権利制限](../../maker/common-data-service/api-limits-overview.md#entitlement-limits)

### <a name="remove-the-affinity-cookie"></a>アフィニティ Cookie の削除

Azure 上のサービスに接続すると、応答とともに Cookie が返され、容量管理により別のサーバーに移動するよう強制されない限り、後続のすべての要求は同じサーバーにルーティングされます。 この Cookie を削除すると、送信する各要求は、適格なサーバーのいずれかにルーティングされます。 サーバーごとに制限が適用されるため、これによってスループットが向上します。 これにより、利用可能な場合に、より多くのサーバーを使用できるようになります。

> [!NOTE]
> この方法は、スループットを最適化しようとしているアプリケーションでのみ使用してください。 対話型クライアント アプリケーションは、アフィニティ Cookie のメリットを享受できます。アフィニティ Cookie を使用すると、キャッシュ データを再利用できるため、パフォーマンス低下を招く再作成の必要はありません。

次のコードは、認証の管理にユーザー定義の HttpMessageHandler を使用していると想定して、Web API で HttpClient を初期化するときに Cookie を無効にする方法を示しています。 詳細: [DelegatingHandler を示す例](authenticate-oauth.md#example-demonstrating-a-delegatinghandler)

```csharp
HttpMessageHandler messageHandler = new OAuthMessageHandler(
    config,
    new HttpClientHandler() { UseCookies = false }
    );
HttpClient httpClient = new HttpClient(messageHandler)
```

CrmServiceClient を使用している場合は、App.config ファイルの AppSettings ノードに以下を追加します。

```xml
<add key="PreferConnectionAffinity" value="false" /> 
```

### <a name="optimize-your-connection"></a>接続の最適化

接続を最適化することで、スループットの向上が期待できます。 .NET サンプル コードをサポートするには、次の設定を使用します。

```csharp
//Change max connections from .NET to a remote service default: 2
System.Net.ServicePointManager.DefaultConnectionLimit = 65000;
//Bump up the min threads reserved for this app to ramp connections faster - minWorkerThreads defaults to 4, minIOCP defaults to 4 
System.Threading.ThreadPool.SetMinThreads(100, 100);
//Turn off the Expect 100 to continue message - 'true' will cause the caller to wait until it round-trip confirms a connection to the server 
System.Net.ServicePointManager.Expect100Continue = false;
//Can decreas overall transmission overhead but can cause delay in data packet arrival
System.Net.ServicePointManager.UseNagleAlgorithm = false;
```
詳細: [接続の管理](/dotnet/framework/network-programming/managing-connections)

## <a name="strategies-to-manage-service-protection-api-limits"></a>サービス保護 API の制限の管理方法

このセクションでは、サービス保護 API の制限エラーを回避するようにクライアントとシステムを設計する方法について説明します。 影響を減らすために、ライセンス管理の方法を考慮することもできます。

### <a name="update-your-client-application"></a>クライアント アプリケーションの更新

サービス保護 API の制限は 2018 年以降 CDS に適用されていますが、多くのクライアント アプリケーションはこれらの制限が存在する前に作成されました。 これらのクライアントは、これらのエラーを予期していないため、エラーを正しく処理できません。 これらのアプリケーションを更新し、以下の[組織サービスの使用](#using-the-organization-service)または [Web API の使用](#using-the-web-api)セクションで説明されているパターンを適用する必要があります。

### <a name="move-towards-real-time-integration"></a>リアルタイム統合に向けて

サービス保護 API の制限の主なポイントは、短期間に発生する負荷の高い要求の影響を取り除くことです。 現在のビジネス プロセスが、大量のデータを短期間に処理しようとする夜間、毎週、または毎月の大規模で定期的なジョブに依存している場合は、リアルタイム データ統合方法を有効にする方法を検討してください。 負荷の高い操作を必要とするプロセスを避けられる場合は、サービス保護の制限による影響を軽減できます。

## <a name="using-the-web-api"></a>Web API の使用

クライアント ライブラリで Web API を使用している場合は、429 エラーで予期される再試行動作がサポートされていることがあります。 クライアント ライブラリの発行元に確認してください。

独自のライブラリを作成した場合は、このサンプル コードに含まれているのと同様の動作をヘルパーに含めることができます。[Web API CDSWebApiService クラス サンプル (C#)](webapi/samples/cdswebapiservice.md)。

```csharp
private async Task<HttpResponseMessage> SendAsync(
    HttpRequestMessage request,
    HttpCompletionOption httpCompletionOption = HttpCompletionOption.ResponseHeadersRead,
    int retryCount = 0)
{
    HttpResponseMessage response;
    try
    {
        //The request is cloned so it can be sent again.
        response = await httpClient.SendAsync(request.Clone(), httpCompletionOption);
    }
    catch (Exception)
    {
        throw;
    }

    if (!response.IsSuccessStatusCode)
    {
        if ((int)response.StatusCode != 429)
        {
            //Not a service protection limit error
            throw ParseError(response);
        }
        else
        {
            // Give up re-trying if exceeding the maxRetries
            if (++retryCount >= config.MaxRetries)
            {
                throw ParseError(response);
            }

            int seconds;
            //Try to use the Retry-After header value if it is returned.
            if (response.Headers.Contains("Retry-After"))
            {
                seconds = int.Parse(response.Headers.GetValues("Retry-After").FirstOrDefault());
            }
            else
            {
                //Otherwise, use an exponential backoff strategy
                seconds = (int)Math.Pow(2, retryCount);
            }
            Thread.Sleep(TimeSpan.FromSeconds(seconds));

            return await SendAsync(request, httpCompletionOption, retryCount);
        }
    }
    else
    {
        return response;
    }
}
```

.NET の回復性と一時的なエラー処理ライブラリ、[Polly](https://github.com/App-vNext/Polly) を使用して、開発者は再試行、サーキット ブレーカー、タイムアウト、バルクヘッド分離、フォールバックなどのポリシーを流暢かつスレッド セーフな方法で表現できます。

### <a name="http-response-headers"></a>HTTP 応答ヘッダー

Web API で HTTP 要求を使用している場合、次の HTTP 応答ヘッダーで残りの制限値を追跡できます。

|[ヘッダー]  |値の説明  |
|---------|---------|
|`x-ms-ratelimit-burst-remaining-xrm-requests`|この接続の残りの要求の数|
|`x-ms-ratelimit-time-remaining-xrm-requests`|同じユーザー アカウントを使用するすべての接続の残りの合計期間|

送信する要求の数を制御するために、これらの値に依存するべきではありません。 これらはデバッグを目的としています。 アフィニティ Cookie を削除する場合、別のサーバーに接続すると、これらの値は再設定されます。

### <a name="use-task-parallel-library-with-web-api"></a>Web API でタスク並列ライブラリを使用する

最適なスループットを実現するために、複数のスレッドを使用する必要があります。 Task Parallel Library (TPL) は、アプリケーションに並列処理と並行処理を追加するプロセスを簡略化することで、開発者の生産性を高めます。

[Web API CDSWebApiService クラス サンプル (C#)](webapi/samples/cdswebapiservice.md) を使用する次の例を参照してください。

- [Web API CDSWebApiService の並列操作のサンプル (C#)](webapi/samples/cdswebapiservice-parallel-operations.md)
- [Web API CDSWebApiService の非同期並列操作のサンプル (C#)](webapi/samples/cdswebapiservice-async-parallel-operations.md)


## <a name="using-the-organization-service"></a>組織サービスの使用

組織サービスを使用している場合は、<xref:Microsoft.Xrm.Tooling.Connector>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient> を使用することをお勧めします。 このクラスは、<xref:Microsoft.Xrm.Sdk.IOrganizationService> メソッドを実装し、返されるサービス保護 API の制限エラーを管理できます。 

Xrm.Tooling.Connector バージョン 9.0.2.16 以降では、Retry-After 期間が経過すると、要求は自動的に一時停止して再送信されます。

アプリケーションが、現在低レベルの <xref:Microsoft.Xrm.Sdk.Client>.<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy> クラスを または <xref:Microsoft.Xrm.Sdk.WebServiceClient>.<xref:Microsoft.Xrm.Sdk.WebServiceClient.OrganizationWebProxyClient>  使用している場合。 これらを CrmServiceClient クラスで置き換えることができるはずです。 <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy> は非推奨です。

詳細:

- [XRM ツールを使用して Windows のクライアント アプリケーションを作成](/xrm-tooling/build-windows-client-applications-xrm-tools)。
- [Common Data Service に接続するための Office365 認証の種類と OrganizationServiceProxy クラスの廃止](/power-platform/important-changes-coming#deprecation-of-office365-authentication-type-and-organizationserviceproxy-class-for-connecting-to-common-data-service)

### <a name="use-task-parallel-library-with-crmserviceclient"></a>CrmServiceClient でタスク並列ライブラリを使用する

最適なスループットを実現するために、複数のスレッドを使用する必要があります。 Task Parallel Library (TPL) は、アプリケーションに並列処理と並行処理を追加するプロセスを簡略化することで、開発者の生産性を高めます。

CrmServiceClient には TPL を使用してクライアントの複数のインスタンスを管理できる <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.Clone> メソッドが含まれているため、<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient> で TPL を使用できます。 例については、「[CrmServiceClient を使用したタスク並列ライブラリ](xrm-tooling/sample-tpl-crmserviceclient.md)」を参照してください。

## <a name="frequently-asked-questions"></a>よくあるご質問

このセクションには、よく寄せられる質問が含まれています。 回答されていない質問がある場合は、このページの下部にある**フィードバック**ボタンを使用して、このページに関するフィードバックを送信してください。

### <a name="im-using-an-etl-application-i-licensed-how-do-i-get-optimum-throughput"></a>ライセンスを取得した ETL アプリケーションを使用しています。 最適なスループットを得る方法を教えてください。

ETL アプリケーション ベンダーと協力して、適用する設定を確認します。 Retry-After 動作をサポートするバージョンの製品を使用していることを確認してください。

### <a name="see-also"></a>関連項目

[Power Platform の管理 / ライセンスとライセンス管理 / 要求の制限と割り当て](/power-platform/admin/api-request-limits-allocations)<br />
[Common Data Service API 制限の概要](../../maker/common-data-service/api-limits-overview.md)<br />
[Common Data Service Web API を使用する](webapi/overview.md)<br />
[Common Data Service 組織サービスを使用する](org-service/overview.md)
