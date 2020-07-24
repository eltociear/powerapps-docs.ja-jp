---
title: Power Apps で Cognitive Services を使用する | Microsoft Docs
description: Azure Cognitive Services の Text Analytics API を使用した基本的なキャンバス アプリを構築して、テキストを分析します。
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 01/17/2020
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 4f8f4694b1ffdf6f415ae5f8a9275976b7dd20d7
ms.sourcegitcommit: 6b2961308c41867756ecdd55f55eccbebf70f7f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2020
ms.locfileid: "3307672"
---
# <a name="use-cognitive-services-in-power-apps"></a>Power Apps で Cognitive Services を使用する
この記事では、[Azure Cognitive Services の Text Analytics API](https://docs.microsoft.com/azure/cognitive-services/text-analytics/overview) を使用する基本的なキャンバス アプリを構築して、テキストを分析する方法を説明します。 Text Analytics API の設定方法と、[Text Analytics コネクタ](https://docs.microsoft.com/connectors/cognitiveservicestextanalytics/) で Text Analytics API に接続する方法を説明します。 次に、API を呼び出すキャンバス アプリを作成する方法を説明します。

> [!NOTE]
> Power Apps でアプリを初めて構築する場合は、この記事を読み進める前に、[アプリの一からの作成](get-started-create-from-blank.md) を読むことをお勧めします。

## <a name="introduction-to-azure-cognitive-services"></a>Azure Cognitive Services の概要
Azure Cognitive Services は、API、SDK、およびアプリケーションをさらにインテリジェントで魅力的、また検索されやすいものにするサービスのセットです。 これらのサービスを利用すると簡単にインテリジェントな機能 – 感情や動画の検出; 顔や音声および画像の認識; 音声や言語の理解などの – アプリケーションに追加できます。

この記事では "言語の理解" に注目して、Text Analytics API を使用します。 この API を使用すると、テキストからセンチメント、キー フレーズ、トピックおよび言語を検出できます。 まず API のデモを試したあと、プレビュー バージョンにサインアップしてみましょう。

### <a name="try-out-the-text-analytics-api"></a>Text Analytics API を試用する
API にはオンライン デモがあります – API の動作を参照し、サービスが返す JSON を見ることができます。

1. [Text Analytics API](https://azure.microsoft.com/services/cognitive-services/text-analytics/) のページに移動します。

2. **アクションで参照**セクションで、テキスト例を使用するか、独自のテキストを入力します。 その後、**分析**をクリックまたはタップしてください。 
   
    ![Text Analytics API デモ](./media/cognitive-services-api/text-analytics-demo.png)

3. このページは、**分析されたテキスト** タブに書式設定された結果、および **JSON** タブに JSON 応答が表示されます。[JSON](https://json.org/) は、データを表す方法です - この場合、Text Analytics API によって返されるデータです。

## <a name="sign-up-for-the-text-analytics-api"></a>Text Analytics API へのサインアップ
API は無料のプレビューとして使用可能で、Azure サブスクリプションに関連付けられます。 Azure Portal で API を管理します。

1. Azure サブスクリプションをまだお持ちでない場合は、[無料のサブスクリプションにサインアップします](https://azure.microsoft.com/free/)。

2. [このページ](https://ms.portal.azure.com/#create/Microsoft.CognitiveServicesTextAnalytics) では、このイメージに示されているように、Text Analytics API に関する情報を入力します。 **F0** (無料) 価格レベルを選択します。
   
    ![Text Analytics API の作成](./media/cognitive-services-api/azure-create.png)

5. 左下隅で、**作成**をクリックまたはタップします。

6. **ダッシュボード**で、作成した API をクリックまたはタップします。
   
    ![Azure ダッシュボード](./media/cognitive-services-api/azure-dashboard.png)

7. **キー**をクリックまたはタップします。
   
    ![Azure メニュー](./media/cognitive-services-api/azure-menu-keys.png)

8. 画面の右側のキーの 1 つをコピーします。 このキーは、後で API への接続を作成するときに使用します。
   
    ![API キー](./media/cognitive-services-api/azure-keys.png)

## <a name="build-the-app"></a>アプリを構築
これで Text Analytics API が稼働したので、Power Apps から接続し、API を呼び出すアプリを構築します。 これは、Text Analytics API ページのデモと同様の機能を備えた、単一画面アプリです。 この構築を始めましょう!

### <a name="create-the-app-and-add-a-connection"></a>アプリの作成および接続の追加
まず、空の電話アプリを作成し、**テキスト分析**コネクタで接続を追加します。 これらのタスクの詳細情報が必要な場合には、[アプリの一からの作成](get-started-create-from-blank.md) および[Power Apps で接続を管理する](add-manage-connections.md) を参照してください。

1. [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) で、**一から開始** > ![電話アプリのアイコン](./media/cognitive-services-api/icon-phone-app.png) (電話) > **このアプリの作成**の順に選択します。

    ![一から開始](./media/cognitive-services-api/start-from-blank.png)

2. Power Apps Studio の中央のウィンドウで、**データに接続**を選択します。

3. **データ** パネルで、**新しい接続** > **テキスト分析**をクリックまたはタップします。

4. キーを**アカウント キー**にコピーし、**作成**をクリックまたはタップします。
   
    ![テキスト分析コネクタ](./media/cognitive-services-api/create-connection-ta.png)

### <a name="add-controls-to-the-app"></a>アプリにコントロールを追加
アプリの作成の次の手順では、すべてのコントロールを追加します。 通常アプリを構築するときにコントロールに数式を追加しますが、この場合はまずコントロールに注目し、次のセクションでいくつかの数式を追加します。 次のイメージは、すべてのコントロールを使用したアプリを示しています。

![完成したアプリ](./media/cognitive-services-api/finished-app-no-data.png)

この画面を作成するには、以下の手順を実行します。 コントロール名を指定すると、その名前が次のセクションの数式で使用されます。

1. **ホーム** タブで、**新しい画面**、**スクロール可能な画面**の順にクリックまたはタップします。 

2. **画面 2** で、**[タイトル]** を選択し、それを**テキスト分析**に変更します。

3. 導入テキストに、**ラベル** コントロールを追加します。

4. 分析するテキストを入力できるように、**テキスト入力**コントロールを追加します。 コントロールに **tiTextToAnalyze** という名前を付けます。 アプリは次のイメージのようになります。
   
    ![タイトル、サブタイトル、およびテキスト入力を使用したアプリ](./media/cognitive-services-api/partial-app-step1.png)

5. 実行する API 操作を選択できるように、3 つの**チェック ボックス** コントロールを追加します。 コントロールに **chkLanguage**、**chkPhrases**、および **chkSentiment** という名前を付けます。

6. 実行する操作を選択した後、API を呼び出すことができるように、ボタンを追加します。 アプリは次のイメージのようになります。
   
    ![チェック ボックスとボタンを使用したアプリ](./media/cognitive-services-api/partial-app-step2.png)

7. 3 つの**ラベル** コントロールを追加します。 最初の 2 つは、言語およびセンチメント API の呼び出し結果を保持します; 3 つ目は、画面下部のギャラリーの概要です。

8. **空の垂直ギャラリー** コントロールを追加し、**ラベル** コントロールをギャラリーに追加します。 ギャラリーは、キー フレーズ API の呼び出し結果を保持します。 アプリは次のイメージのようになります。
   
    ![ラベルおよびギャラリーを使用したアプリ](./media/cognitive-services-api/partial-app-step3.png)

9. 左のウィンドウで、**画面 1** > 省略記号 (**. . .**) > **削除**を選択します (アプリには、この画面は不要です)。

Text Analytics API を呼び出すことに集中するため、アプリをシンプルな状態にしてきましたが、次のものを追加することもできます - 選択したチェック ボックスに基づいてコントロールの表示や非表示を行うロジック、ユーザーがオプションを選択しない場合のエラー処理などです。

### <a name="add-logic-to-make-the-right-api-calls"></a>右側の API 呼び出しを行うロジックの追加
さて、見栄えの良いアプリになりましたが、まだ何も実行していません。 すぐに修正します。 ただし詳しく説明する前に、次のアプリのパターンを説明します:

1. アプリは選択されたチェック ボックスに基づいて、特定の API 呼び出しを行います。 **テキスト分析**をクリックまたはタップすると、アプリは 1 つ、2 つ、または 3 つの API 呼び出しを行います。

2. このアプリは API が返すデータを 3 つの異なる[コレクション](working-with-variables.md#use-a-collection) に格納します: **languageCollect**、**sentimentCollect**、および **phrasesCollect** です。

3. このアプリは、ラベルの 2 つの**テキスト** プロパティおよびギャラリーの**アイテム** プロパティを、3 つのコレクションの内容に基づいて更新します。

それを踏まえて、ボタンの **OnSelect** プロパティに数式を追加しましょう。 ここがすべてのマジックが起きるところです。

```powerapps-dot
If( chkLanguage.Value = true,
    ClearCollect( languageCollect, 
        TextAnalytics.DetectLanguageV2(
            {
                text: tiTextToAnalyze.Text
            }
        ).detectedLanguages.name
    )
);

If( chkPhrases.Value = true,
    ClearCollect( phrasesCollect, 
        TextAnalytics.KeyPhrasesV2(
            {
                language: "en", 
                text: tiTextToAnalyze.Text
            }
        ).keyPhrases
    )
);

If( chkSentiment.Value = true,
    ClearCollect( sentimentCollect, 
        TextAnalytics.DetectSentimentV2(
            {
                language: "en", 
                text: tiTextToAnalyze.Text
            }
        ).score
    )
)
```

ここで少し進んでいるので、詳しく見てみましょう:

* **If** ステートメントは簡単です - 特定のチェック ボックスが選択された場合、API を呼び出します。

* 各呼び出しでは、適切なパラメーターを指定します:

  * 3 つの呼び出しすべてで、入力テキストとして **tiTextToAnalyze.Text** を指定します。

  * **DetectLanguage()** で、**numberOfLanguagesToDetect** を 1 にハード コーディングされますが、アプリ内のロジックに基づいて、このパラメーターを渡すことができます。

  * **KeyPhrases()** および **DetectSentiment()** で、**言語**を "en" にハード コーディングされますが、アプリ内のロジックに基づいて、このパラメーターを渡すことができます。 たとえば、まず言語を検出し、次に **DetectLanguage()** が返すものに基づいて、このパラメーターを設定します。

* 各呼び出しが行われるごとに、結果を適切なコレクションに追加します:

    * **languageCollect** には、テキストで特定された言語**名**を追加します。

    * **phrasesCollect** には、テキストで特定された **keyPhrases** を追加します。

    * **sentimentCollect** には、テキストに対するセンチメントの**スコア**を追加します。その値は 0-1 で、1 なら 100% ポジティブです。

### <a name="display-the-results-of-the-api-calls"></a>API 呼び出しの結果の表示
API 呼び出しの結果を表示するには、各コントロールで適切なコレクションを参照します:

1. 言語ラベルの**テキスト** プロパティを `"The language detected is " & First(languageCollect).name` に設定します。
   
    **First()** 関数は、**languageCollect** の最初 (この場合では唯一) のレコードを返し、そのレコードに関連付けられた**名** (唯一のフィールド) を表示します。

2. センチメント ラベルの**テキスト** プロパティを `"The sentiment score is " & Round(First(sentimentCollect.Value).Value, 3)*100 & "% positive."` に設定します。
   
    この数式では **First()** 関数も使用して、最初および唯一のレコードから**値** (0-1) を取得し、その値をパーセント形式にします。

3. キー フレーズ ギャラリーの**アイテム** プロパティを `phrasesCollect` に設定します。
   
    今度はギャラリーと連動しているため、**First()** 関数で 単一の値を抽出する必要はありません。 コレクションを参照し、ギャラリーにキー フレーズをリストとして表示します。

## <a name="run-the-app"></a>アプリの実行

アプリが完成したので、起動して動作を確認します: 右上隅の実行ボタンをクリックまたはタップします ![アプリの実行](./media/cognitive-services-api/icon-run-app.png)。 次のイメージでは、3 つのオプションすべてが選択され、テキストは、Text Analytics API ページの既定のテキストと同じです。

![データ付きの完成したアプリ](./media/cognitive-services-api/finished-app.png)

このアプリの出力を、この記事の最初の Text Analytics API のページと比較する場合、同じ結果を表示します。

これで Text Analytics API に関する理解を深め、アプリに組み込む方法について楽しんでご覧いただけたら幸いです。 記事で、詳しく取り上げてほしい Cognitive Services (または他の全般的なサービス) が他にある場合はお知らせください。 いつものように、コメントにフィードバックおよび質問をお寄せください。

