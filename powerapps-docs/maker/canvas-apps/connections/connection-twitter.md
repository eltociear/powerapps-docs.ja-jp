---
title: Twitter の接続の概要 | Microsoft Docs
description: いくつかの例を通して Twitter への接続方法の段階的説明とすべての機能の紹介を確認する
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 07/12/2017
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 50b783bce993d40ae88c438c115b2b859a08b7f8
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3306292"
---
# <a name="connect-to-twitter-from-power-apps"></a>Power Apps から Twitter に接続する
![Twitter](./media/connection-twitter/twittericon.png)

Twitter では、ツイートの投稿および Twitter アカウントからのツイート、タイムライン、フレンド、フォロワーの取得ができます。

この情報を、アプリのラベルに表示できます。 たとえば、入力テキスト ボックスを追加し、ユーザーにツイート テキストの入力を依頼してから、ツイートを "投稿" するボタンを追加できます。 同様の方法で、ツイートを取得または検索してから、アプリのラベルまたはギャラリー コントロールにテキストを表示できます。

このトピックでは、Twitter 接続の作成方法、アプリでの Twitter 接続の使用方法を説明し、使用可能な関数を一覧表示します。

[!INCLUDE [connection-requirements](../../../includes/connection-requirements.md)]

## <a name="connect-to-twitter"></a>Twitter への接続
1. Power Apps を開き、**新規**を選択してから、**空白のアプリ**を作成します。 携帯電話またはタブレットのレイアウトを選択します。 タブレットのレイアウトは、より多くのワークスペースを提供します:  

   ![空のアプリを開く](./media/connection-twitter/blank-app.png)
2. 右側のウィンドウで、**データ** タブをクリックまたはタップしてから、**データソースの追加**をクリックまたはタップします。
3. **新規接続**を選択してから、**Twitter** を選択します。  

    ![Twitter への接続](./media/connection-twitter/addconnection.png)

    ![Twitter への接続](./media/connection-twitter/add-twitter.png)
4. **接続**を選択し、Twitter サインイン用の資格情報を入力してから、**アプリの承認**を選択します。
5. **データ ソースの追加**を選択します。 **データ ソース**で接続が表示されます:  
    ![オプション ウィンドウを閉じる](./media/connection-twitter/twitterdatasource.png)

Twitter 接続が作成され、アプリに追加されました。 これにより、接続を使用できるようになりました。

## <a name="use-the-twitter-connection-in-your-app"></a>アプリで Twitter 接続を使用する
### <a name="show-a-timeline"></a>タイムラインを表示する
1. **挿入**メニューで、**ギャラリー**を選択し、**テキスト付き**ギャラリーのいずれかを追加します。
2. タイムラインをいくつか表示してみましょう:  

   * 現在のユーザーのタイムラインを表示するには、ギャラリーの**[項目](../controls/properties-core.md)** プロパティを次の式に設定します:

       `Twitter.HomeTimeline().TweetText`  
       `Twitter.HomeTimeline({maxResults:3}).TweetText`  
   * 別のユーザーのタイムラインを表示するには、ギャラリーの**[項目](../controls/properties-core.md)** プロパティを次の式に設定します:  

       `Twitter.UserTimeline( *TwitterHandle* ).TweetText`

       二重引用符で囲んだ Twitter ハンドルまたは同等の値を入力します。 たとえば、`"satyanadella"` または `"powerapps"` を数式に直接入力します。
   * **Tweep** という名前のテキスト入力コントロールを追加し、その既定のプロパティを `Tweep.Text` に設定します。 Tweep テキスト ボックスに、`satyanadella` などの Twitter ハンドルを入力します (引用符と @ 記号は除去します)。

       ギャラリー コントロールで、項目プロパティを次の式に設定します:  

       `Twitter.UserTimeline(Tweep.Text, {maxResults:5}).TweetText`

       ギャラリー コントロールでは、入力した Twitter ハンドルのツイートが自動的に表示されます。

     > [!TIP]
     > これらの式の一部は、**maxResults** 引数を使って、タイムラインに最新のツイートの *x* 数を表示します。
3. ギャラリーの**項目**プロパティを `Twitter.HomeTimeline()` に設定します。

    ギャラリーを選択すると、右側のウィンドウにそのギャラリーのオプションが表示されます。
4. 1 番目のリストで **TweetText**、2 番目のリストで **TweetedBy**、3 番目のリストで **CreatedAt** を選択します。

    ギャラリーには、選択したプロパティの値が表示されるようになります。

### <a name="show-followers"></a>フォロワーを表示する
1. **テキスト付き**ギャラリーを使用して、フォロワーの一部を表示してみましょう:  

   * 現在のユーザーのフォロワーを表示するには、ギャラリーの**[項目](../controls/properties-core.md)** プロパティを次の式に設定します:  

       `Twitter.MyFollowers()`  
       `Twitter.MyFollowers({maxResults:3})`
   * 別のユーザーのフォロワーを表示するには、ギャラリーの**[項目](../controls/properties-core.md)** プロパティを次の式に設定します:  

       `Twitter.Followers( *TwitterHandle* )`

       二重引用符で囲んだ Twitter ハンドルまたは同等の値を入力します。 たとえば、`"satyanadella"` または `"powerapps"` を数式に直接入力します。
   * **Tweep** という名前のテキスト入力コントロールを追加し、その既定のプロパティを `Tweep.Text` に設定します。 Tweep テキスト ボックスに、`satyanadella` などの Twitter ハンドルを入力します (引用符と @ 記号は除去します)。

       ギャラリー コントロールで、項目プロパティを次の式に設定します:  

       `Twitter.Followers(Tweep.Text, {maxResults:5})`

       ギャラリー コントロールでは、入力した Twitter ハンドルをフォローしているユーザーが自動的に表示されます。

     > [!TIP]
     > これらの式の一部は、**maxResults** 引数を使って、タイムラインに最新のツイートの *x* 数を表示します。
2. ギャラリーの**項目**プロパティを `Twitter.MyFollowers()` に設定します。

    ギャラリーを選択すると、右側のウィンドウにそのギャラリーのオプションが表示されます。
3. 2 番目のリストで **UserName** を選択し、3 番目のリストで **FullName** を選択します。

    ギャラリーには、選択したプロパティの値が表示されるようになります。

### <a name="show-followed-users"></a>フォローされているユーザーを表示する
1. **テキスト付き**ギャラリーを使用して、フォローされているユーザーの一部を表示してみましょう:  

   * 現在のユーザーがフォローしているユーザーを表示するには、ギャラリーの**[項目](../controls/properties-core.md)** プロパティを次の式に設定します:  

       `Twitter.MyFollowing()`  
       `Twitter.MyFollowing({maxResults:3})`
   * 別のユーザーがフォローしているユーザーを表示するには、ギャラリーの**[項目](../controls/properties-core.md)** プロパティを次の式に設定します:

       `Twitter.Following( *TwitterHandle* )`

       二重引用符で囲んだ Twitter ハンドルまたは同等の値を入力します。 たとえば、`"satyanadella"` または `"powerapps"` を数式に直接入力します。
   * **Tweep** という名前のテキスト入力コントロールを追加し、その既定のプロパティを `Tweep.Text` に設定します。 Tweep テキスト ボックスに、`satyanadella` などの Twitter ハンドルを入力します (引用符と @ 記号は除去します)。

       ギャラリー コントロールで、項目プロパティを次の式に設定します:  

       `Twitter.Following(Tweep.Text, {maxResults:5})`

       ギャラリー コントロールでは、ユーザーがフォローしている他のハンドルが自動的に表示されます。

     ギャラリーを選択すると、右側のウィンドウにそのギャラリーのオプションが表示されます。
2. **Body1** リストで **Description** を、**Heading1** リストで **UserName** を、**Subtitle1** リストで **FullName** を、それぞれ選択します。

    ギャラリーには、選択したプロパティの値が表示されるようになります。

### <a name="show-information-about-a-user"></a>ユーザーについての情報を表示する
ラベルを追加してから、その**[テキスト](../controls/properties-core.md)** プロパティを次の式のいずれかに設定します:  

* `twitter.User( *TwitterHandle* ).Description`
* `twitter.User( *TwitterHandle* ).FullName`
* `twitter.User( *TwitterHandle* ).Location`
* `twitter.User( *TwitterHandle* ).UserName`
* `twitter.User( *TwitterHandle* ).FollowersCount`
* `twitter.User( *TwitterHandle* ).FriendsCount`
* `twitter.User( *TwitterHandle* ).Id`
* `twitter.User( *TwitterHandle* ).StatusesCount`

二重引用符で囲んだ Twitter ハンドルまたは同等の値を入力します。 たとえば、`"satyanadella"` または `"powerapps"` を数式に直接入力します。

または、このトピック全体で行っているように、入力テキスト コントロールを使用して Twitter ハンドルを入力することもできます。

### <a name="search-tweets"></a>ツイートを検索する
1. **テキスト付き**ギャラリーを使用して、その**[項目](../controls/properties-core.md)** プロパティを次の式に設定します:  

    `Twitter.SearchTweet( *SearchTerm* ).TweetText`

    *SearchTerm* は、二重引用符で囲むか、同等の値を参照して入力します。 たとえば、`"PowerApps"` または `"microsoft"` と式に直接入力します。

    または、このトピック全体で行っているように、**入力テキスト** コントロールを使用して検索語句を指定することもできます。

    > [!TIP]
   > maxResults を使用して最初の 5 つの結果を表示します:  

    `Twitter.SearchTweet(SearchTerm.Text, {maxResults:5}).TweetText`
2. ギャラリーの**項目**プロパティを `Twitter.SearchTweet(SearchTerm.Text, {maxResults:5})` に設定します。

    ギャラリーを選択すると、右側のウィンドウにそのギャラリーのオプションが表示されます。
3. 1 番目のリストで **TweetText**、2 番目のリストで **TweetedBy**、3 番目のリストで **CreatedAt** を選択します。

    ギャラリーには、選択したプロパティの値が表示されるようになります。

### <a name="send-a-tweet"></a>ツイートを送信する
1. テキスト入力コントロールを追加してから、名前を **MyTweet** に変更します。
2. ボタンを追加してから、その **[OnSelect](../controls/properties-core.md)** プロパティを次の式に設定します:  
    `Twitter.Tweet({tweetText: MyTweet.Text})`
3. F5 キーを押すか、プレビュー ボタン (![](./media/connection-twitter/preview.png)) を選択します。 **MyTweet** にテキストを入力してから、ボタンを選択して入力したテキストをツイートします。
4. 既定のワークスペースに戻るには、Esc キーを押します。

## <a name="view-the-available-functions"></a>使用可能な関数を表示する
この接続には、次の関数が含まれています:

| 関数名 | 内容 |
| --- | --- |
| [UserTimeline](connection-twitter.md#usertimeline) |指定したユーザーにより投稿された最新のツイートのコレクションを取得します |
| [HomeTimeline](connection-twitter.md#hometimeline) |最新のツイートを取得し、自分と自分のフォロワーに投稿をリツイートします |
| [SearchTweet](connection-twitter.md#searchtweet) |指定したクエリに一致する、関連するツイートのコレクションを取得します |
| [フォロワー](connection-twitter.md#followers) |指定したユーザーをフォローしているユーザーを取得します |
| [MyFollowers](connection-twitter.md#myfollowers) |自分をフォローしているユーザーを取得します |
| [フォロー](connection-twitter.md#following) |指定したユーザーがフォローしているユーザーを取得します |
| [MyFollowing](connection-twitter.md#myfollowing) |自分がフォローしているユーザーを取得します |
| [User](connection-twitter.md#user) |指定したユーザーに関する詳細を取得します (例: ユーザー名、説明、フォロワー数など) |
| [ツイート](connection-twitter.md#tweet) |ツイート |
| [OnNewTweet](connection-twitter.md#onnewtweet) |検索クエリに一致するツイートが新しく投稿されたときに、ワークフローをトリガーします |

### <a name="usertimeline"></a>UserTimeline
ユーザーのタイムラインを取得する: 指定したユーザーが投稿した最新のツイートのコレクションを取得します

#### <a name="input-properties"></a>入力プロパティ

| 件名 | データの種類 | 必要な領域 | 内容 |
| --- | --- | --- | --- |
| userName |string |はい |Twitter ハンドル |
| maxResults |integer |いいえ |取得するツイートの最大数 (例: {maxResults:5}) |

#### <a name="output-properties"></a>出力プロパティ

| プロパティ名 | データの種類 | 必要な領域 | 内容 |
| --- | --- | --- | --- |
| TweetText |string |有効 | |
| TweetId |string |No | |
| CreatedAt |string |No | |
| RetweetCount |integer |有効 | |
| TweetedBy |string |有効 | |
| MediaUrls |配列 |No | |

### <a name="hometimeline"></a>HomeTimeline
ホーム タイムラインを取得する: 自分と自分のフォロワーに投稿された最新のツイートおよびリツイートを取得します

#### <a name="input-properties"></a>入力プロパティ

| 件名 | データの種類 | 必要な領域 | 内容 |
| --- | --- | --- | --- |
| maxResults |integer |いいえ |取得するツイートの最大数 (例: {maxResults:5}) |

#### <a name="output-properties"></a>出力プロパティ

| プロパティ名 | データの種類 | 必要な領域 | 内容 |
| --- | --- | --- | --- |
| TweetText |string |有効 | |
| TweetId |string |No | |
| CreatedAt |string |No | |
| RetweetCount |integer |有効 | |
| TweetedBy |string |有効 | |
| MediaUrls |配列 |No | |

### <a name="searchtweet"></a>SearchTweet
ツイートを検索する: 指定したクエリに一致する、関連するツイートのコレクションを取得します

#### <a name="input-properties"></a>入力プロパティ

| 件名 | データの種類 | 必要な領域 | 内容 |
| --- | --- | --- | --- |
| searchQuery |string |はい |クエリ テキスト (Twitter でサポートされている任意のクエリ演算子を使用する可能性があります: https://www.twitter.com/search) |
| maxResults |integer |いいえ |取得するツイートの最大数 (例: {maxResults:5}) |

#### <a name="output-properties"></a>出力プロパティ

| プロパティ名 | データの種類 | 必要な領域 | 内容 |
| --- | --- | --- | --- |
| TweetText |string |有効 | |
| TweetId |string |No | |
| CreatedAt |string |No | |
| RetweetCount |integer |有効 | |
| TweetedBy |string |有効 | |
| MediaUrls |配列 |No | |

### <a name="followers"></a>フォロワー
フォロワーを取得する: 指定したユーザーをフォローしているユーザーを取得します

#### <a name="input-properties"></a>入力プロパティ

| 件名 | データの種類 | 必要な領域 | 内容 |
| --- | --- | --- | --- |
| userName |string |はい |ユーザーの Twitter ハンドル |
| maxResults |integer |いいえ |取得するユーザーの最大数 (例: {maxResults:5}) |

#### <a name="output-properties"></a>出力プロパティ

| プロパティ名 | データの種類 | 必要な領域 | 内容 |
| --- | --- | --- | --- |
| Fullname |string |有効 | |
| 場所 |string |有効 | |
| ID |integer |No | |
| UserName |string |有効 | |
| FollowersCount |integer |No | |
| 内容 |string |有効 | |
| StatusesCount |integer |No | |
| FriendsCount |integer |No | |

### <a name="myfollowers"></a>MyFollowers
自分のフォロワーを取得する: 自分をフォローしているユーザーを取得します

#### <a name="input-properties"></a>入力プロパティ

| 件名 | データの種類 | 必要な領域 | 内容 |
| --- | --- | --- | --- |
| maxResults |integer |いいえ |取得するユーザーの最大数 (例: {maxResults:5}) |

#### <a name="output-properties"></a>出力プロパティ

| プロパティ名 | データの種類 | 必要な領域 | 内容 |
| --- | --- | --- | --- |
| Fullname |string |有効 | |
| 場所 |string |有効 | |
| ID |integer |No | |
| UserName |string |有効 | |
| FollowersCount |integer |No | |
| 内容 |string |有効 | |
| StatusesCount |integer |No | |
| FriendsCount |integer |No | |

### <a name="following"></a>フォロー
フォローしているユーザーを取得する: 指定したユーザーがフォローしているユーザーを取得します

#### <a name="input-properties"></a>入力プロパティ

| 件名 | データの種類 | 必要な領域 | 内容 |
| --- | --- | --- | --- |
| userName |string |はい |ユーザーの Twitter ハンドル |
| maxResults |integer |いいえ |取得するユーザーの最大数 (例: {maxResults:5}) |

#### <a name="output-properties"></a>出力プロパティ

| プロパティ名 | データの種類 | 必要な領域 | 内容 |
| --- | --- | --- | --- |
| Fullname |string |有効 | |
| 場所 |string |有効 | |
| ID |integer |No | |
| UserName |string |有効 | |
| FollowersCount |integer |No | |
| 内容 |string |有効 | |
| StatusesCount |integer |No | |
| FriendsCount |integer |No | |

### <a name="myfollowing"></a>MyFollowing
自分がフォローしているユーザーを取得する: 自分がフォローしているユーザーを取得します

#### <a name="input-properties"></a>入力プロパティ

| 件名 | データの種類 | 必要な領域 | 内容 |
| --- | --- | --- | --- |
| maxResults |integer |いいえ |取得するユーザーの最大数 (例: {maxResults:5}) |

#### <a name="output-properties"></a>出力プロパティ

| プロパティ名 | データの種類 | 必要な領域 | 内容 |
| --- | --- | --- | --- |
| Fullname |string |有効 | |
| 場所 |string |有効 | |
| ID |integer |No | |
| UserName |string |有効 | |
| FollowersCount |integer |No | |
| 内容 |string |有効 | |
| StatusesCount |integer |No | |
| FriendsCount |integer |No | |

### <a name="user"></a>User
ユーザーを取得する: 指定したユーザーに関する詳細を取得します (例: ユーザー名、説明、フォロワー数など)

#### <a name="input-properties"></a>入力プロパティ

| 件名 | データの種類 | 必要な領域 | 内容 |
| --- | --- | --- | --- |
| userName |string |はい |ユーザーの Twitter ハンドル |

#### <a name="output-properties"></a>出力プロパティ

| プロパティ名 | データの種類 | 必要な領域 | 内容 |
| --- | --- | --- | --- |
| Fullname |string |有効 | |
| 場所 |string |有効 | |
| ID |integer |No | |
| UserName |string |有効 | |
| FollowersCount |integer |No | |
| 内容 |string |有効 | |
| StatusesCount |integer |No | |
| FriendsCount |integer |No | |

### <a name="tweet"></a>ツイート
新しいツイートを投稿する: ツイートします

#### <a name="input-properties"></a>入力プロパティ

| 件名 | データの種類 | 必要な領域 | 内容 |
| --- | --- | --- | --- |
| tweetText |string |いいえ |投稿されたテキスト (例: {tweetText:"hello"}) |
| 本文 |string |いいえ |投稿するメディア |

#### <a name="output-properties"></a>出力プロパティ

| プロパティ名 | データの種類 | 必要な領域 | 内容 |
| --- | --- | --- | --- |
| TweetId |string |有効 | |

### <a name="onnewtweet"></a>OnNewTweet
新しいツイート表示されたとき: 検索クエリに一致するツイートが新しく投稿されたときに、ワークフローをトリガーします

#### <a name="input-properties"></a>入力プロパティ

| 件名 | データの種類 | 必要な領域 | 内容 |
| --- | --- | --- | --- |
| searchQuery |string |はい |クエリ テキスト (Twitter でサポートされている任意のクエリ演算子を使用する可能性があります: https://www.twitter.com/search) |

#### <a name="output-properties"></a>出力プロパティ

| プロパティ名 | データの種類 | 必要な領域 | 内容 |
| --- | --- | --- | --- |
| 値 |配列 |No | |

## <a name="helpful-links"></a>便利なリンク
[使用可能な接続](../connections-list.md) をすべて参照してください。  
アプリに [接続を追加する](../add-manage-connections.md) 方法についてご確認ください。

