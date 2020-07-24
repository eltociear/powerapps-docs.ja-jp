---
title: オフライン対応キャンバス アプリを開発する | Microsoft Docs
description: オンラインまたはオフラインにかかわらず、ユーザーが生産性を高めることができるオフライン対応キャンバス アプリを開発します。
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 02/29/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 6ec1a55713b3cce0a98c02058124b5b3d159b376
ms.sourcegitcommit: 129d004e3d33249b21e8f53e0217030b5c28b53f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2020
ms.locfileid: "3308017"
---
# <a name="develop-offline-capable-canvas-apps"></a>オフライン対応キャンバス アプリを開発する

通常、モバイル ユーザーは、接続が制限されているか、または接続されていない場合でも、生産的である必要があります。 キャンバス アプリをビルドすると、次のタスクを実行できます。

- Power Apps モバイルを開き、オフライン時にアプリを実行します。
- [Connection](functions/signals.md#connection) シグナル オブジェクトを使用して、アプリがオフライン、オンライン、または従量制課金接続かを決定します。
- オフライン時の基本的なデータ ストレージで、[コレクション](create-update-collection.md) を使用し、[**LoadData** および **SaveData**](functions/function-savedata-loaddata.md) などの関数を使用します。

この記事には、Twitter のデータを使用する例が含まれています。  接続を必要としないさらに簡単な例は、[**LoadData** および **SaveData** 関数リファレンス](functions/function-savedata-loaddata.md) に含まれています。

## <a name="limitations"></a>制限

**LoadData** および **SaveData** を統合して簡単なメカニズムにし、ローカル デバイスには少量のデータを保存します。 これらの関数を使用することにより、簡単な Offline 機能 をあなたのアプリに追加することもできます。

これらの関数は、メモリ内コレクションで動作するため、アプリの利用可能なメモリ容量によって制限されます。 利用可能なメモリは、デバイス、オペレーティング システム、Power Apps モバイルが使用するメモリ、および画面とコントロールに関するアプリの複雑さによって異なります。 数メガバイトを超えるデータを保存する場合、実行が予想されるデバイス上で、予想されるシナリオを使用してアプリをテストします。 一般的に、30 メガバイトから 70 メガバイトの利用可能なメモリがあります。

関数は、デバイスがオンラインになったとき、マージの競合を自動的に解決しません。 保存するデータと再接続の処理方法の構成は、式を記述するときにメーカーが決定します。

オフライン機能の更新については、このトピックに戻り、[Power Apps ブログ](https://powerapps.microsoft.com/blog/) に登録してください。

## <a name="overview"></a>概要

オフライン シナリオを設計する場合、まずアプリがデータを使用する方法を検討する必要があります。 Power Apps  のアプリは、主に、SharePoint、Office 365、および Common Data Service など、プラットフォームが提供する一連の [コネクタ](../canvas-apps/connections-list.md) を通してデータにアクセスします。 RESTful エンドポイントを提供するサービスへのアプリのアクセスを可能にするカスタム コネクタを構築することもできます。 Web API や Azure Functions などのサービスが考えられます。 これらのコネクタは、すべてがインターネット経由で HTTPS を使用します。つまり、ユーザーは、データやサービスが提供するその他の機能にアクセスするには、オンラインである必要があります。

![Power Apps とコネクタ](./media/offline-apps/online-app.png)

### <a name="handling-offline-data"></a>オフライン データの処理

Power Apps では、データ ソースに関係なく、一貫した方法でデータのフィルター処理、検索、並べ替え、集計、および操作を行うことができます。 アプリのメモリ内のコレクションから SharePoint へのソース範囲は、SQL データベースおよび Common Data Service に一覧表示されます。 この一貫性のため、アプリを簡単にリターゲットして、異なるデータ ソースを使用することができます。 オフライン シナリオについてさらに重要なのは、アプリのロジックをほとんど変更せずに、データ管理でローカル コレクションを使用できることです。 実際、ローカル コレクションは、オフライン データを処理するための主要なメカニズムです。

## <a name="build-an-offline-app"></a>オフライン アプリの構築

アプリ開発のオフラインの側面へのフォーカスを維持するために、このトピックでは Twitter に重点を置いた単純なシナリオを示します。 オフライン中に Twitter の投稿を読み、ツイートを送信することができるアプリを作成します。 アプリがオンラインになったときに、ツイートを投稿し、ローカル データを再度読み込みます。

高レベルで、アプリは次のタスクを実行します。

- ユーザーがアプリを開いたとき。

  - デバイスがオンラインの場合は、アプリは Twitter コネクタを通してデータをフェッチし、そのデータをコレクションに設定します。
  - デバイスがオフラインの場合、アプリは [**LoadData**](../canvas-apps/functions/function-savedata-loaddata.md) 関数を使用して、ローカルのキャッシュ ファイルからデータを読み込みます。
  - ユーザーはツイートを送信することができます。 アプリがオンラインの場合、ツイートを直接 Twitter に投稿し、ローカル キャッシュを更新します。

- アプリがオンラインである間は 5 分ごと。

  - アプリはすべてのツイートをローカルキャッシュに投稿します。
  - アプリはローカル キャッシュを更新し、[**SaveData**](../canvas-apps/functions/function-savedata-loaddata.md) 関数を使用して保存します。

### <a name="step-1-add-twitter-to-a-blank-phone-app"></a>ステップ 1: Twitterを空の電話アプリに追加する

1. Power Apps Studio で、**ファイル** > **新規**を選択します。
1. **空のアプリ** タイルで、**携帯電話レイアウト** を選択します。
1. **ビュー** タブで、**データ ソース**を選択します。
1. **データ** ウィンドウで、**データ ソースの追加**を選択します。
1. **新しい接続** > **Twitter** > **作成**を選択します。
1. 資格情報を入力し、接続を作成してから、**データ** ウィンドウを閉じます。

### <a name="step-2-collect-existing-tweets"></a>ステップ 2: 既存のツイートを収集する

1. **ツリー ビュー** ウィンドウで、**アプリ**を選択し、その **OnStart** プロパティをこの式に設定します。

    ```powerapps-dot
    If( Connection.Connected,
        ClearCollect( LocalTweets, Twitter.SearchTweet( "PowerApps", {maxResults: 10} ) );
            Set( statusText, "Online data" ),
        LoadData( LocalTweets, "LocalTweets", true );
            Set( statusText, "Local data" )
    );
    SaveData( LocalTweets, "LocalTweets" );
    ```

    > [!div class="mx-imgBorder"]
    > ![ツイートを読み込むための数式](./media/offline-apps/load-tweets.png)

1. **ツリー ビュー** ウィンドウで、**アプリ** オブジェクトの省略記号メニューを選択し、次に **OnStart で実行**を選択してその式を実行します。

    > [!div class="mx-imgBorder"]
    > ![式を実行してツイートを読み込む](./media/offline-apps/load-tweets-run.png)

    > [!NOTE]
    > ブラウザーがサポートしていないため、**LoadData** および **SaveData** 関数で Power Apps Studio のエラーが表示されることがあります。 ただし、このアプリをデバイスに展開した後は、正常に実行されます。

この数式は、デバイスがオンラインかどうかを確認します。

- デバイスがオンラインの場合、式は **LocalTweets** コレクションに最大 10 個のツイートを、検索用語「PowerApps」付きで読み込みます。
- デバイスがオフラインの場合、式は「LocalTweets」という名前のファイルからローカル キャッシュを読み込みます (使用できる場合)。

### <a name="step-3-show-tweets-in-a-gallery"></a>ステップ 3: ギャラリーにツイートを表示する

1. **挿入** タブで、**ギャラリー** > **変更可能な高さ (空)** を選択します。

1. [**ギャラリー**](controls/control-gallery.md) コントロールの **Items** プロパティを `LocalTweets` に設定します。

1. ギャラリー テンプレートで、[**ラベル**](controls/control-text-box.md) コントロールを 3 つ追加し、各ラベル コントロールの **Text** プロパティをこれらの値のいずれかに設定します。

    - `ThisItem.UserDetails.FullName & " (@" & ThisItem.UserDetails.UserName & ")"`
    - `Text(DateTimeValue(ThisItem.CreatedAtIso), DateTimeFormat.ShortDateTime)`
    - `ThisItem.TweetText`

1. 最後のラベルのテキストを太字にし、ギャラリーがこの例に似るようにします。

    > [!div class="mx-imgBorder"]
    > ![サンプル ツイートを表示しているギャラリー](./media/offline-apps/tweet-gallery.png)

### <a name="step-4-show-connection-status"></a>ステップ 4: 接続状態を表示する

1. ギャラリーの下にラベルを挿入し、その **Color** プロパティを**赤**に設定します。

1. 最も新しいラベルの **Text** プロパティを次の式に設定します:

    `If( Connection.Connected, "Connected", "Offline" )`

この数式は、デバイスがオンラインかどうかを決定します。 その場合、ラベルには**接続中**と表示され、それ以外の場合は**オフライン**と表示されます。

### <a name="step-5-add-a-box-to-compose-tweets"></a>ステップ 5: ツイートを作成するボックスを追加する

1. 接続状態ラベルの下に、[**テキスト入力**](controls/control-text-input.md) コントロールを挿入し、名前を **NewTweetTextInput** に変更します。

1. テキスト入力ボックスの **Default** プロパティを `""` に設定します。

    > [!div class="mx-imgBorder"]
    > ![状態に関する情報およびテキスト入力ボックス上のギャラリー](./media/offline-apps/status-input.png)

### <a name="step-6-add-a-button-to-post-the-tweet"></a>手順 6: ツイートを投稿するためのボタンを追加する

1. テキスト入力ボックスの下に、**Button** コントロールを追加し、その **Text** プロパティをこの値に設定します。

    `"Tweet"`

1. ボタンの **OnSelect** プロパティを次の数式に設定します。

    ```powerapps-dot
    If( Connection.Connected,
        Twitter.Tweet( "", {tweetText: NewTweetTextInput.Text} ),
        Collect( LocalTweetsToPost, {tweetText: NewTweetTextInput.Text} );
            SaveData( LocalTweetsToPost, "LocalTweetsToPost" )
    );
    Reset( NewTweetTextInput );
    ```  

1. **アプリ**の **OnStart** プロパティで、式の最後に行を追加します。

    ```powerapps-dot
    If( Connection.Connected,
        ClearCollect( LocalTweets, Twitter.SearchTweet( "PowerApps", {maxResults: 100} ) );
            Set( statusText, "Online data" ),
        LoadData( LocalTweets, "LocalTweets", true );
            Set( statusText, "Local data" )
    );
    SaveData( LocalTweets, "LocalTweets" );
    LoadData( LocalTweetsToPost, "LocalTweetsToPost", true );  // added line
    ```

    > [!div class="mx-imgBorder"]
    > ![コメントを付けていない明細行のあるツイートを読み込む式を実行する](./media/offline-apps/load-tweets-save.png)

この数式は、デバイスがオンラインかどうかを決定します。

- デバイスがオンラインの場合、すぐにツイートを投稿します。
- デバイスがオフラインの場合、ツイートは **LocalTweetsToPost** コレクション内にキャプチャされてデバイスに保存します。

その後、数式は、テキスト入力ボックス内のテキストをリセットします。

### <a name="step-7-check-for-new-tweets"></a>ステップ 7: 新しいツイートを確認する

1. ボタンの右側に、**タイマー** コントロールを追加します。

    > [!div class="mx-imgBorder"]
    > ![完成版のアプリ](./media/offline-apps/final-app.png)

1. タイマーの **Duration** プロパティを **300000** に設定します。

1. タイマーの **AutoStart** および **Repeat** プロパティを **true** に設定します。

1. タイマーの **OnTimerEnd** を次の式に設定します:

    ```powerapps-dot
    If( Connection.Connected,
        ForAll( LocalTweetsToPost, Twitter.Tweet( "", {tweetText: tweetText} ) );
        Clear( LocalTweetsToPost );
        ClearCollect( LocalTweets, Twitter.SearchTweet( "PowerApps", {maxResults: 10} ) );
        SaveData( LocalTweets, "LocalTweets" );
   )
    ```

この数式は、デバイスがオンラインかどうかを決定します。 そうであれば、アプリは **LocalTweetsToPost** コレクション内のすべてのアイテムをツイートし、その後コレクションをクリアします。

## <a name="test-the-app"></a>アプリをテストする

1. インターネットに接続されているモバイル デバイスでアプリを開きます。

    既存のツイートがギャラリーに表示され、状態には**接続済み**と表示されます。

1. デバイスの機内モードを有効にして Wi-Fi を無効にし、デバイスをインターネットから切断します。

    状態ラベルには、アプリが**オフライン**であることが表示されます。

1. デバイスがオフラインの間、**PowerApps** を含むツイートを書き、次に **ツイート** ボタンを選択します。

    ツイートは、**LocalTweetsToPost** コレクション内にローカルで格納されます。

1. デバイスの機内モードを無効にして Wi-Fi を有効にし、デバイスをインターネットに再接続します。

    5 分以内にアプリはツイートを投稿し、ギャラリーに表示されます。

この記事では、オフライン アプリを構築するための Power Apps の機能について、その概要を説明しました。 いつものように、[フォーラム](https://powerusers.microsoft.com/t5/PowerApps-Forum/bd-p/PowerAppsForum1) にフィードバックをお送りください。また、作成したオフライン アプリを [Power Apps コミュニティ ブログ](https://powerusers.microsoft.com/t5/PowerApps-Community-Blog/bg-p/PowerAppsBlog) でサンプルとして共有してください。