---
title: キャンバス アプリをテストするためのテスト スタジオの操作 | Microsoft Docs
description: キャンバス アプリをテストするためにテスト スタジオとサンプルを使用する方法について説明します。
author: aengusheaney
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/04/2020
ms.author: aheaney
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 63f8d27877b8c4035afe2204f5e8b5aff5e06959
ms.sourcegitcommit: dab754a07a4d4aa7a361a70173009c37fc80b0ed
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2020
ms.locfileid: "3433418"
---
# <a name="working-with-test-studio-experimental"></a>テスト スタジオの操作 (試験段階)

このクイックスタートでは、Kudos というキャンバス アプリを対象にしたテストを作成します。 また、テストの概念を調べて理解し、独自のキャンバス アプリのテストを記述するために適用することもできます。 サンプルの Kudos アプリは、[従業員エクスペリエンス スタート キット](https://powerapps.microsoft.com/en-us/blog/powerapps-employee-experience-starter-kit)からダウンロードできる従業員エンゲージメント アプリのスイートの一部です。

> [!NOTE]
> この機能はまだ実験段階であり、非運用アプリのテストの書き込みに使用することをお勧めします。 詳細については [実験的機能とプレビュー機能](working-with-experimental-preview.md) を参照してください。

## <a name="open-test-studio"></a>テスト スタジオを開く

他の試験的な機能と同様に、アプリでこの機能を有効にする必要はありません。 既定では、すべてのキャンバス アプリでテスト スタジオを使用できます。

1. [Power Apps](https://make.powerapps.com) にサインインします。

2. [新しいアプリ](get-started-test-drive.md)を作成するか、[既存のアプリを編集](edit-app.md)します。

3. アプリを Power Apps に保存して、テスト スタジオを開きます。 
    
    > [!NOTE]
    > アプリのテストを記述する前に、アプリを保存する必要があります。

4. 左のナビゲーションにある**詳細ツール**を選択します。

5. **テストを開く**を選択して、このアプリケーション用のテスト スタジオを開きます。 このアクションにより、新しいブラウザー タブでテスト スタジオが開きます。

    ![テスト スタジオを開く](./media/working-with-test-studio/open-tests.png "テスト スタジオを開く")

> [!NOTE]
> テストが公開され、アプリ パッケージに保存されます。 キャンバス アプリ パッケージを別の環境にエクスポートおよびインポートすると、作成したテスト スイートやテスト ケースなどのすべてのテスト定義も含まれます。 

## <a name="create-a-test-suite"></a>テスト スイートの作成

既定では、テスト スイートとテスト ケースがテスト スタジオで自動的に作成されます。 テスト スイートは、テスト ケースを整理するために使用します。 1 つのアプリに 1 つまたは複数のテスト スイートを含めることができます。 既定のテスト スイートとテスト ケースを使用してテストの記述をすぐに開始することも、新しいテスト スイートを作成することもできます。

1. **新しいスイート**を選択します。
2. メイン グリッドでフィールドを選択して、**テスト スイートの名前と説明**を更新します。

    ![新しいテスト スイート](./media/working-with-test-studio/new-test-suite.png "新しいテスト スイート")

## <a name="create-a-test-case"></a>テスト ケースの作成

テストをどのように整理またはグループ化したいかに応じて、1 つのテスト スイートに複数のテスト ケースを作成できます。 各ケースでは、アプリ内の特定の機能または機能のサブセットをテストできます。

1. テスト スイートを選択します。
2. 上部のメニューで**新しいケース**を選択して、新しいケースを作成します。
3. メイン グリッドでフィールドを選択して、**テスト ケースの名前と説明**を更新します。

 ![新しいテスト ケース](./media/working-with-test-studio/new-test-case.png "新しいテスト ケース")

## <a name="record-a-test-case"></a>テスト ケースの記録

テスト ケースは、アクションが含まれるテスト ステップで構成されます。 テスト アクションは、タスクを実行する Power Apps 式を使用して記述されます。 レコーダーを使用して、アプリを操作しながらテスト ステップを自動的に生成できます。 記録した後、テスト ケースを更新したり、新しいステップを追加したり、ステップを削除したり、テスト アサーションを記述してテストの結果を検証できます。

> [!NOTE]
> 発行済みのアプリのみが記録モードで再生されます。 テスト ケースの記録を開始する前に、アプリへの任意の最新の変更を公開します。 最新の変更を公開せずに記録すると、最後に公開されたアプリのバージョンが記録モードで再生されます。

1. 上部のメニューから**レコード**を選択します。 これにより、発行済みのアプリが新しいブラウザー タブに記録モードで表示されます。

    > [!IMPORTANT]
    > 既存のテスト ケース上に記録すると、既に存在する既存のテスト ステップが上書きされます。

    ![テストの記録](./media/working-with-test-studio/record-tests.png "テストの記録")

2. アプリを操作します。 操作は、左側のウィンドウで**記録済**です。

3. 操作が完了したら、**完了**を選択します。 必要に応じて、**キャンセル**を選択して、操作を記録せずにテスト スタジオに戻ることができます。 

    ![記録の保存](./media/working-with-test-studio/save-recording.png "記録の保存")

4. テスト スタジオで自動的に生成されたテスト ステップと式を表示します。

5. 必要に応じて、メイン グリッド内のステップの説明のテキストを編集します。 メイン グリッドで数式を選択して、テスト ステップのアクションを更新することもできます。

    ![テスト ケースの更新](./media/working-with-test-studio/update-test-case.png "テスト ケースの更新")

### <a name="add-test-steps-and-test-assertions"></a>テスト ステップとテスト アサーションの追加

すべてのテスト ケースには、予想される結果が必要です。 Kudos の例では、Kudo を送信する場合に想定される結果の 1 つは、Common Data Service (Common Data Service) データベースに新しいレコードを作成することです。 次に、テスト ケースを更新し、その他のテスト ステップを追加して、レコードが正常に作成されたことを検証します。

次の手順に従って、レコードが正常に作成されたことを検証します。

- テスト ケースの冒頭で、データベース内の Kudo レコード総数に対する変数を初期化します。
- テスト ケースの最後に、データベース内の Kudo レコード総数に対する変数を初期化します。
- 総数が 1 ずつ増分されていることを検証するためのテスト アサーション式を記述します。 このカウントが 1 ずつ増加していない場合、テスト アサーションは失敗し、テスト ケースが失敗します。

Kudos アプリにテスト ステップとテスト アサーションを追加するには:

1. ステップ 1 またはその上に新しいステップを挿入するステップを選択します。 

2. 上部のメニューから**上にステップを挿入**を選択するか、アクティブな行からオプションを選択します。 このアクションで空のステップが作成されます。

    ![手順の挿入](./media/working-with-test-studio/insert-step-above.png "手順の挿入")

    > [!NOTE]
    > **上にステップを挿入**を選択すると、現在のステップの上に新しい空のステップが追加されます。 代わりに**アサート**、**SetProperty**、**選択**または**追跡**アクションを使用することもできます。 これにより、編集可能な各アクション数式がステップに追加されます。

3. ステップの説明を更新します。 たとえば、"データベースの Kudo 総数"。

4. テスト実行前にデータベース内のレコードをカウントするアクション入力に、式または数式を入力します。

    サポートされている任意の式を使用できます。 また、アプリに含まれているデータ ソース、コレクション、変数、実行フローのクエリを実行したり、テストで使用する新しいグローバル変数やコレクションを作成したりすることもできます。

    ```powerapps-dot
    Set(kudosBeforeTest, CountRows(Filter(Kudos, Receiver.Email = "someone@example.com")))```

5. Select Step 2 or the step above which you want to insert a new step.

6. Select **Insert a step above** from the top menu or by selecting the option from the active row. This action creates an empty step.

7. Enter an expression or formula in the action input to [Trace](./functions/function-trace.md) and write the *kudosBeforeTest* value to the test results record.

    ```powerapps-dot
    Trace("kudosBeforeTest : " & kudosBeforeTest);
    ```

    ![テスト前の Kudos](./media/working-with-test-studio/kudos-before-test.png "テスト前の Kudos")

8. テスト ケースの下部に移動し、テスト完了後にデータベース内のレコードをカウントする新しいステップを挿入します。

    ```powerapps-dot
    Set(kudosAfterTest, CountRows(Filter(Kudos, Receiver.Email = "someone@example.com")))```

9. Add a final step to validate that the record count in the database has increased by a count of 1, and enter the following assertion action to verify:

    ```powerapps-dot
    Assert(kudosAfterTest = kudosBeforeTest + 1, "Kudos count incorrect. Expected : " & kudosBeforeTest + 1  & " Actual :" & kudosAfterTest)
    ```

    ![テスト アサート後の Kudos](./media/working-with-test-studio/kudos-after-test-assert.png "テスト アサート後の Kudos")

10. テスト スタジオの右上のメニューからテスト ケースを保存します。 

## <a name="play-back-your-test"></a>テストの再生

記録されたテストを再生して、アプリ機能を検証できます。 単一のテスト スイートまたは単一のテスト ケース内のすべてのテストを再生できます。 

最近の変更を加えた記録を再生する前に、アプリを公開する必要があります:

![公開せずに再生する](./media/working-with-test-studio/publish-test-studio-changes.png "公開せずに再生する")

> [!IMPORTANT]
> 公開をスキップする場合、記録再生には最新のテスト変更は含まれません。 最後に公開されたテスト ケースまたはテスト スイートが、アプリに対して再生されます。

1. **公開する** を選択して、テストを自動的に保存して公開します。

    ![変更の公開](./media/working-with-test-studio/publish-button.png "変更の公開")

2. テスト スイートまたは単一のテスト ケースのどちらかを選択します。

3. **再生**を選択します。 公開されたアプリが**再生**モードで開き、テスト ステップが自動的に再生されることを確認できます。 緑のチェック マークは、テスト ステップが正常に実行されたことを示します。 ステップが失敗すると、エラー メッセージと共に赤いエラー インジケーターが表示されます。

    ![再生モード](./media/working-with-test-studio/play-mode.png "再生モード")

4. **完了**を選択してテスト スタジオに戻ります。

### <a name="failed-assertion"></a>失敗したアサーション

このセクションでは、テスト アサーションを変更して、失敗したテストを試します:

1. 式のボックスを選択して、アサーション ステップを編集します。

2. テスト アクションの ```+ 1``` を ```+ 2``` に更新します。 このアップデートは、テストで 2 つのレコードが作成されることを想定していることを意味しますが、これは正しくありません。 テストが成功していれば、データベースにはレコードが 1 つだけ作成されているはずです。

    ```powerapps-dot
    Assert(kudosAfterTest = kudosBeforeTest + 2, "Kudos count incorrect. Expected : " & kudosBeforeTest + 2  & " Actual :" & kudosAfterTest)
    ```

    ![カウント更新のアサート](./media/working-with-test-studio/assert-count-update.png "カウント更新のアサート")

3. **公開** を選択します。

4. **再生**を選択します。

5. テストの再生を表示します。 最後のステップが失敗し、エラーおよびアサーション ステップに指定したメッセージが表示されます。  

    ![再生エラー](./media/working-with-test-studio/playback-error.png "再生エラー")

### <a name="playing-tests-in-a-browser"></a>ブラウザーでのテストの再生

リンクをコピーして、テスト スタジオ外部の別のブラウザーでテストを再生することもできます。 これにより、**Azure DevOps** などの継続的なビルドとリリースのパイプラインにテストを統合できます。

選択したテストの再生リンクが保持されます。 テスト スイートまたはテスト ケースは変更されません。 ビルドおよびリリース プロセスを変更することなく、テストを更新できます。

ブラウザーでテストを再生するには:

1. 右側のウィンドウでテスト スイートまたはテスト ケースを選択します。

2. **再生リンクのコピー**をクリックします。

    ![再生リンクのコピー](./media/working-with-test-studio/copy-play-link.png "再生リンクのコピー")

3. 発行されていない変更がある場合は、テストを発行するように求められます。

    ![リンクをコピーする前に公開する](./media/working-with-test-studio/publish-before-copy-link.png "リンクをコピーする前に公開する")

4. 公開プロセスをスキップして再生リンクをコピーすることを選択できます。 スキップした場合、テストに対する新しい変更は再生されません。

    ![コピーしたリンクの再生](./media/working-with-test-studio/copy-play-link-ack.png "コピーしたリンクの再生")

5. ブラウザーを開き、URL をアドレス バーに貼り付けてテストを再生します。

6. テストの再生を表示します。

## <a name="setup-your-tests"></a>テストをセットアップする

テストスイートの **OnTestCaseStart** プロパティは、自分のテストをセットアップできます。 このプロパティに入力された式は、ケースの実行が開始される前に、スイート内のすべてのテスト ケースに対してトリガーされます。 **OnTestCaseStart** は、すべてのケースの最初に同じテスト手順を書くことを避けるのに役立ちます。 このプロパティをカスタマイズして、次のようなスイートのすべてのケースに共通する設定タスクを実行できます。

- 常に最初の画面からテスト実行を開始します。 
- 一般的なコレクションまたは変数の初期化。 
- 現在実行中のテストのデータ ソースからテストデータを取得する 

**TestCaseInfo** レコードには、実行中の現在のテストの詳細が含まれています。 以下のプロパティを含みます。

- *TestCaseName* – テスト ケースの名前。
- *TestCaseDescription* – テストケースの説明。
- *TestCaseId* – テスト ケースの ID。
- *TestSuiteName* – ケースが属するテスト スイート名。
- *TestSuiteDescription* – テスト スイートの説明。
- *TestSuiteId* – ケースが属するテスト スイートの ID。

以下の例では、**OnTestCaseStart** プロパティをカスタマイズするので、すべてのテスト ケースはアプリの最初の画面から始まります。 また、テスト ケースの手順で参照できるデータ ソースからテスト データをフェッチします。

1. 左側のウィンドウで**テスト**を選択するか、スイート ヘッダーで**表示**します。

    ![設定プロパティのテストまたは表示](./media/working-with-test-studio/test-or-view-to-set-property.png "設定プロパティのテストまたは表示")

2. **OnTestCaseStart** アクションを選択します。

3. 最初の画面に移動する式を入力し、テストのテスト データをフェッチします。 

    ```powerapps-dot
    //Start every cases on the first screen in the Kudos app
    Navigate('Dashboard Screen');

    //Initialize my test data for the current case. 
    Set(currentTestData, LookUp(KudosTestData, TestCase = TestCaseInfo.TestCaseName));

    //Set kudosBeforeTest to 0
    Set(kudosBeforeTest, 0)
    ```
    ![OnTestCaseStart の例](./media/working-with-test-studio/ontestcasestart-example.png "OnTestCaseStart の例")

## <a name="processing-test-results"></a>テスト結果の処理

ブラウザーを使用する場合、テスト スタジオでのテスト再生時に表示されるテスト パネルは表示されません。 この動作により、実行する特定のテスト ステップを判別することや、テストが成功または失敗したかどうかを判断することはできません。

テスト スタジオの外部でテスト結果を確認するために、テスト オブジェクトで使用可能な **OnTestCaseComplete** および **OnTestSuiteComplete** という 2 つのプロパティがあり、テストの結果を処理するために使用できます。 **Azure DevOps** のような継続的なビルドとリリースのパイプラインにテストを統合する場合は、これらのプロパティを使用して、アプリの展開を続行する必要があるかどうかを判断できます。

これらのプロパティに入力した式は、各ケースまたはスイートが完了するとトリガーされます。 これらのプロパティをカスタマイズして処理し、テストの結果を次のさまざまなデータ ソースまたはサービスに送信できます:

- SQL Server。
- Common Data Service。
- Power Automate。
- Office 365 を使用する電子メール。

これらの設定は、アプリ内のすべてのテスト スイートまたはテスト ケースに適用されます。 各テスト スイートまたはテスト ケースが完了すると、テスト結果とテストに含まれるすべての追跡メッセージが、**TestCaseResult** および **TestSuiteResult** レコードで使用できるようになります。

**TestCaseResult** レコードには、次のプロパティが含まれます:

- *TestCaseName* – テスト ケースの名前。
- *TestCaseDescription* – テストケースの説明。
- *TestCaseId* – テスト ケースの ID。
- *TestSuiteName* – ケースが属するテスト スイート名。
- *TestSuiteDescription* – テスト スイートの説明。
- *TestSuiteId* – ケースが属するテスト スイートの ID。
- *StartTime* – テストの実行開始時刻。
- *EndTime* – テストの実行終了時刻。
- *Trace* – テスト アサーションの結果および Trace 関数からのメッセージ。
- *Success* – テスト ケースが正常に完了したかどうかを示します。
- *TestFailureMessage* – ケースが失敗した場合のエラー メッセージ。

**TestSuiteResult** レコードには、次のプロパティが含まれます: 

- *TestSuiteName* – テスト スイート名。
- *TestSuiteDescription* – テスト スイートの説明。 
- *TestSuiteId* – テスト スイート ID。
- *StartTime* – テスト スイートの実行開始時刻。
- *EndTime* – テスト スイートの実行終了時刻。
- *TestsPassed* – スイートで正常に完了したテスト ケースの数。
- *TestsFailed* - スイートで失敗したテスト ケースの数。

このクイックスタートでは、Common Data Service データベースに 2 つのユーザー定義エンティティを作成し、**OnTestCaseComplete** および **OnTestSuiteComplete** プロパティをカスタマイズして、テスト結果を格納します:

1. 左側のウィンドウで**テスト**を選択するか、スイート ヘッダーで**表示**します。

    ![設定プロパティのテストまたは表示](./media/working-with-test-studio/test-or-view-to-set-property.png "設定プロパティのテストまたは表示")

2. **OnTestCaseComplete** アクションを選択します。

3. テストの結果を処理する式を入力します。 次のサンプルでは、各テスト ケースの結果を Common Data Service のカスタム AppTestResults エンティティに保存します。 オプションで、テスト結果を SQL、SharePoint、またはその他のデータ ソースに格納できます。 データ ソースの追跡フィールドを必要に応じて設定または増加させることが必要になる場合があります。

    > [!NOTE]
    > 次のサンプルでは[Common Data Service の接続](https://docs.microsoft.com/connectors/commondataservice/)が必要です。 [簡単なアプリ](data-platform-create-app.md)を作成したり、Common Data Service を使用して[アプリをゼロから構築する](data-platform-create-app-scratch.md)こともできます。 また、次のサンプルで使用されるデータ ソースのレコードを変更する方法の詳細については、[Patch](./functions/function-patch.md) 関数リファレンスを参照してください。

    ```powerapps-dot
    //Save to Common Data Service
    Patch(AppTestResults
    , Defaults(AppTestResults)
    , {
             TestPass: TestCaseResult.TestCaseName & ":" & Text(Now())
             ,TestSuiteId: TestCaseResult.TestSuiteId
             ,TestSuiteName: TestCaseResult.TestSuiteName
             ,TestCaseId: TestCaseResult.TestCaseId
             ,TestCaseName: TestCaseResult.TestCaseName
             ,StartTime: TestCaseResult.StartTime
             ,EndTime: TestCaseResult.EndTime
             ,TestSuccess: TestCaseResult.Success
             ,TestTraces: JSON(TestCaseResult.Traces)
             ,TestFailureMessage: TestCaseResult.TestFailureMessage
    }
    );
    ```
    ![OnTestCaseComplete の例](./media/working-with-test-studio/ontestcasecomplete-example.png "OnTestCaseComplete の例")

4. **OnTestSuiteComplete** アクションを選択します。

5. テストの結果を処理する式を入力します。 次のサンプルでは、各テスト スイートの結果を Common Data Service のカスタム AppTestSuiteResults エンティティに保存します。 

    ```powerapps-dot
    //Save to Common Data Service
    Patch(AppTestSuiteResults
        , Defaults(AppTestSuiteResults)
        , {
             TestSuiteId: TestSuiteResult.TestSuiteId
             ,TestSuiteName: TestSuiteResult.TestSuiteName
             ,StartTime: TestSuiteResult.StartTime
             ,EndTime: TestSuiteResult.EndTime
             ,TestPassCount: TestSuiteResult.TestsPassed
             ,TestFailCount: TestSuiteResult.TestsFailed
        }
    );
    ```

    ![OnTestSuiteComplete の例](./media/working-with-test-studio/ontestsuitecomplete-example.png "OnTestSuiteComplete の例")

これらのプロパティで使用できるその他の式の例を次に示します:

- Power Automate のフローに結果を送信します。

    ```powerapps-dot
    MyTestResultsFlow.Run(JSON(TestCaseResult))
    ```

- 結果を電子メールで送信します。

    ```powerapps-dot
    Office365.SendMailV2("someone@example.com", "Test case results", JSON(TestCaseResult, JSONFormat.IndentFour))
    ```

- テスト結果のアプリ通知を受信します。

  たとえば、テスト スタジオ外部のブラウザーでテストを再生した場合、テスト完了後に通知を受け取ります。

    ```powerapps-dot
    Notify(TestCaseResult.TestCaseName & " : "
            & If( TestCaseResult.Success
                , " Passed"
                , TestCaseResult.TestFailureMessage)
            ,If(  TestCaseResult.Success
                , NotificationType.Success
                , NotificationType.Error)
    )
    ```

## <a name="test-functions"></a>Test 関数

Power Apps で使用可能な [関数](formula-reference.md) に加えて、テストを作成するときに通常使用する一般的な関数を次に示します。

- [Select](./functions/function-select.md)
- [SetProperty](./functions/function-setproperty.md)
- [Assert](./functions/function-assert.md)
- [トレース](./functions/function-trace.md)

## <a name="next-steps"></a>次の手順

- [クラシック エディターを使用して Azure Pipelines でテストを自動化する](test-studio-classic-pipeline-editor.md)
