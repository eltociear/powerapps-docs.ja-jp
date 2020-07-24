---
title: クラシック エディターを使用して Azure Pipelines でテストを自動化する | Microsoft Docs
description: Azure Pipelines からクラシック エディターを使用してテスト スイートおよびケースを自動化する方法について説明します。
author: aengusheaney
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/24/2020
ms.author: aheaney
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: fc3572ffe59226e096c92bc84de35945593a6089
ms.sourcegitcommit: 51fa748cde4ea81e918dae1b39f9dca1d6e4e546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2020
ms.locfileid: "3309696"
---
# <a name="automate-tests-with-azure-pipelines-using-classic-editor"></a>クラシック エディターを使用して Azure Pipelines でテストを自動化する

この記事では、[Azure DevOps サービス](https://docs.microsoft.com/azure/devops/user-guide/what-is-azure-devops?view=azure-devops) の [Azure Pipelines クラシック エディター](https://docs.microsoft.com/azure/devops/pipelines/get-started/pipelines-get-started?view=azure-devops#define-pipelines-using-the-classic-interface) を使用して、テスト スタジオで作成されたキャンバス アプリ テストを設定および実行する方法を説明します。

GitHub のパブリック プロジェクト - [Microsoft/PowerAppsTestAutomation](https://github.com/microsoft/PowerAppsTestAutomation) を使用して、次のことができます。

- アプリケーションへのサインインの操作を自動化します。
- ビルド エージェントでブラウザーを開き、一連のテスト ケースおよびスイートを実行します。
- Azure DevOps パイプラインでテスト実行の状態を表示します。

> [!NOTE]
> [テスト スタジオ](test-studio.md) 機能はまだ実験段階であり、非運用アプリのテストを書き込むために使用することをお勧めします。 詳細については [実験的機能とプレビュー機能](working-with-experimental-preview.md) を参照してください。

## <a name="prerequisites"></a>前提条件

開始する前に、次の手順を実行する必要があります。

- GitHub で [Microsoft/PowerAppsTestAutomation](https://github.com/microsoft/PowerAppsTestAutomation) プロジェクトを[フォーク](#step-1---fork-the-powerappstestautomation-project) します。

    > [!NOTE]
    > パブリック フォークを非公開にすることはできません。 非公開リポジトリを作成する場合は、[リポジトリを複製](https://help.github.com/github/creating-cloning-and-archiving-repositories/duplicating-a-repository) してください。

- パイプラインから実行するアプリ テスト URL を使用して、リポジトリに新しい[*テスト URL .json ファイル*](#step-2---create-test-url-json-file) を作成します。

### <a name="step-1---fork-the-powerappstestautomation-project"></a>ステップ 1 - PowerAppsTestAutomation プロジェクトをフォークする

[フォーク](https://help.github.com/github/getting-started-with-github/fork-a-repo) はリポジトリのコピーです。 リポジトリをフォークすることによって、元のプロジェクトに影響を与えずに変更を加えることができます。

1. [GitHub](https://github.com/) にサインインします。

1. [microsoft/PowerAppsTestAutomation](https://github.com/microsoft/PowerAppsTestAutomation) リポジトリに移動します。 代わりに **microsoft/PowerAppsTestAutomation** を検索して、リポジトリを選択することもできます。

    ![GitHub を検索する](media/test-studio-classic-pipeline-editor/search-github.png "GitHub を検索する")

1. **フォーク**を選択します。

    ![フォーク](media/test-studio-classic-pipeline-editor/fork.png "フォーク")

1. フォークする場所を選択します。

    ![フォーク アカウント](media/test-studio-classic-pipeline-editor/fork-account.png "フォーク アカウント")

フォークされたリポジトリが使用できるようになりました。

### <a name="step-2---create-test-url-json-file"></a>ステップ 2 - テスト URL .json ファイルを作成する

テスト URL .json ファイルには、アプリを検証するためのテスト スイートおよびテスト ケースの URL が含まれます。 アプリ テスト スイートおよびテスト ケースの URL は、テスト スタジオで[再生リンクをコピーする](working-with-test-studio.md#playing-tests-in-a-browser) を選択することにより取得できます。

前の手順で作成したリポジトリで、サンプル ファイルである ```Samples/TestAutomationURLs.json``` を見つけることができます。

1. リポジトリに新しい ```TestURLs.json``` ファイルを作成するか、または他のファイル名を使用します。 <br> ファイル名および場所は、ドキュメントの後半でパイプライン変数にマップされます。

1. ```Samples/TestAutomationURLs.json``` ファイルからフォーマットをコピーします。

1. アプリで検証するテストで、テスト URL セクションを更新します。

1. 変更をリポジトリに確定します。

    ![JSON の更新](media/test-studio-classic-pipeline-editor/json-update.png "JSON の更新")

## <a name="create-a-pipeline"></a>パイプラインの作成

1. Azure DevOps インスタンスにサインインします。

1. 既存のプロジェクトを選択するか、または新しいプロジェクトを作成します。

1. 左側のメニューで**パイプライン**を選択します。

1. **パイプラインの作成**を選択します。

    ![パイプラインの作成](media/test-studio-classic-pipeline-editor/create-pipeline.png "パイプラインの作成")

1. **クラシック エディターを使用する**を選択します。

    ![クラシック エディター](media/test-studio-classic-pipeline-editor/use-classic-editor.png "クラシック エディター")

1. ソースとして GitHub を選択します。

1. 必要に応じて、OAuth を使用するかまたは個人用アクセス トークンを使用して、GitHub 接続を承認します。

    ![パイプライン - GitHub](media/test-studio-classic-pipeline-editor/pipeline-github.png "パイプライン - GitHub")

1. 必要に応じて、接続名を編集します。

1. **リポジトリ**入力の右側から **...** (省略記号) を選択します。

1. GitHub にプロジェクトの名前を入力し、次に**選択します**。

    ![リポジトリの選択](media/test-studio-classic-pipeline-editor/select-repo.png "リポジトリの選択")

1. **続行** を選択します。

1. テンプレートの選択のスクリーンで、**空のジョブ**を選択します。

    ![空のジョブ](media/test-studio-classic-pipeline-editor/empty-job.png "空のジョブ")

1. パイプラインを**保存**します。

## <a name="add-tasks-to-the-pipeline"></a>パイプラインにタスクを追加する

新しいジョブ タスクを追加し、次の順序でパイプラインからテストを実行するようにタスクを構成します。

1. [PowerShell を使用してスクリーン解像度を構成します。](#step-1---configure-screen-resolution-using-powershell)

1. [PowerAppsTestAutomation ソリューションの NuGet パッケージを復元します。](#step-2---restore-nuget-packages)

1. [PowerAppsTestAutomation ソリューションを構築します。](#step-3---build-the-powerappstestautomation-solution)

1. [Google Chrome 用の Visual Studio テストを追加します。](#step-4---add-visual-studio-tests-for-google-chrome)

1. [Mozilla Firefox 用の Visual Studio テストを追加します。](#step-5---add-visual-studio-tests-for-mozilla-firefox)

### <a name="step-1---configure-screen-resolution-using-powershell"></a>ステップ 1 - PowerShell を使用してスクリーン解像度を構成する

1. *エージェント ジョブ 1* の横の **+** を選択します。

1. **PowerShell** を検索します。

1. **追加**を選択して、PowerShell タスクをジョブに追加します。

    ![PowerShell](media/test-studio-classic-pipeline-editor/powershell.png "PowerShell")

1. タスクを選択します。 <br>
    表示名を*エージェント スクリーン解像度を 1920 x 1080 に設定*、または類似したものに更新することもできます。

1. スクリプトの種類として**インライン**を選択して、スクリプト ウィンドウに次のように入力します。

    ```powershell
    # Set agent screen resolution to 1920x1080 to avoid sizing issues with Portal  
    Set-DisplayResolution -Width 1920 -Height 1080 -Force
    # Wait 10 seconds  
    Start-Sleep -s 10
    # Verify Screen Resolution is set to 1920x1080  
    Get-DisplayResolution
    ```

    ![スクリプト](media/test-studio-classic-pipeline-editor/script.png "スクリプト")

### <a name="step-2---restore-nuget-packages"></a>ステップ 2 - NuGet パッケージを復元する

1. *エージェント ジョブ 1* の横の **+** を選択します。

1. **NuGet**を検索します。

1. **追加**を選択して、NuGet タスクをジョブに追加します。

1. タスクを選択します。
    <br> 表示名を **NuGet パッケージを復元する**、または類似したものに更新することもできます。

1. **…** を選択します **ソリューション、packages.config、または project.json へのパス**構成フィールドの (省略記号)。

1. PowerAppsTestAutomation.sln ソリューション ファイルを選択します。

1. **OK** を選択します。

    ![NuGet パッケージ](media/test-studio-classic-pipeline-editor/nuget.png "NuGet パッケージ")

### <a name="step-3---build-the-powerappstestautomation-solution"></a>ステップ 3 - PowerAppsTestAutomation ソリューションを構築する

1. *エージェント ジョブ 1* の横の **+** を選択します。

1. **Visual Studio ビルド**を検索します。

1. **追加**を選択して、Visual Studio ビルド タスクをジョブに追加します。

1. タスクを選択します。
    <br> 表示名を **Power Apps テスト Automation ソリューションを構築する**、または類似したものに更新することもできます。

1. **…** を選択します **ソリューション**構成フィールドの (省略記号)。

1. PowerAppsTestAutomation.sln ソリューション ファイルを選択します。

1. **OK** を選択します。

### <a name="step-4---add-visual-studio-tests-for-google-chrome"></a>ステップ 4 - Google Chrome 用の Visual Studio テストを追加する

1. *エージェント ジョブ 1* の横の **+** を選択します。

1. **Visual Studio テスト**を検索します。

1. **追加**を選択して、Visual Studio テスト タスクをジョブに追加します。

1. タスクを選択します。
    <br> 表示名を **\$(BrowserTypeChrome) から Power Apps テスト Automation テストを実行する**、または類似したものに更新することもできます。

1. **テスト ファイル** テキスト フィールドの既定のエントリを削除し、次を追加します。

    ```**\Microsoft.PowerApps.TestAutomation.Tests\bin\\Debug\Microsoft.PowerApps.TestAutomation.Tests.dll```

1. **テスト フィルターの条件**フィールドに ```TestCategory=PowerAppsTestAutomation``` を入力します。

1. **テスト ミックスには UI テストが含まれています**を選択します。

    ![Chrome](media/test-studio-classic-pipeline-editor/chrome.png "Chrome")

1. **…** を選択します **設定ファイル** フィールドの (省略記号)。

1. **Microsoft.PowerApps.TestAutomation.Tests** を展開し、**patestautomation.runsettings** ファイルを選択し、次に **OK** を選択します。

    ![設定を実行](media/test-studio-classic-pipeline-editor/runsettings.png "設定を実行")

1. **テスト実行パラメーターを上書きする**フィールドに以下のものをコピーします。

    ```
    -OnlineUsername $(OnlineUsername) -OnlinePassword $(OnlinePassword) -BrowserType $(BrowserTypeChrome) -OnlineUrl $(OnlineUrl) -UsePrivateMode $(UsePrivateMode) -TestAutomationURLFilePath $(TestAutomationURLFilePath) -DriversPath $(ChromeWebDriver)
    ```

    > [!NOTE]
    > これは、パイプラインの変数が構成された場所であり、上記の \$(VariableName) のフォームで表されます。

1. **テスト実行タイトル** フィールドに **\$(BrowserTypeChrome) から Power Apps テスト Automation テストを実行する**、または類似したものを入力します。

    ![テストの実行](media/test-studio-classic-pipeline-editor/test-run.png "テストの実行")

### <a name="step-5---add-visual-studio-tests-for-mozilla-firefox"></a>ステップ 5 - Mozilla Firefox 用の Visual Studio テストを追加する

1. **Chrome用の Visual Studio テストを追加する**タスクを右クリックし、**クローン タスク**を選択します。

1. タスクを選択して、次の領域を更新します。

    1. **タイトル**:  \$(BrowserTypeFirefox) から Power Apps テスト Automation テストを実行する

    1.  **テスト実行パラメーターを上書きする**

        ```
        -OnlineUsername $(OnlineUsername) -OnlinePassword $(OnlinePassword) -BrowserType $(BrowserTypeFirefox) -OnlineUrl $(OnlineUrl) -UsePrivateMode $(UsePrivateMode) -TestAutomationURLFilePath $(TestAutomationURLFilePath) -DriversPath $(GeckoWebDriver)
        ```

    1.  **テストの実行タイトル**: \$(BrowserTypeFirefox) から Power Apps テスト Automation テストを実行する

## <a name="configure-pipeline-variables"></a>パイプライン変数を構成する

ここで、[前の手順](#add-tasks-to-the-pipeline) で追加したタスクの定義されたパイプライン変数を構成します。

1. **変数**タブを選択します。

1. **追加**を選択し、この手順を繰り返して次の変数を構成します。

| 変数名             | 変数値                                                                                                                 |
|---------------------------|--------------------------------------------------------------------------------------------------------------------------------|
| BrowserTypeChrome         | Chrome                                                                                                                         |
| BrowserTypeFirefox        | Firefox                                                                                                                        |
| OnlineUrl                 | <https://make.powerapps.com>                                                                                                   |
| TestAutomationURLFilePath | ```$(Build.SourcesDirectory)\<test URL file>.json``` <br>**注意:** これは、前の手順で作成した[*テスト URL .json*](#step-2---create-test-url-json-file) ファイルです。                      |
| UsePrivateMode            | True                                                                                                                           |
| OnlineUsername            | アプリケーションにサインインするユーザー コンテキストの Azure Active Directory メール アドレスを入力します。 テストは、このユーザー アカウントのコンテキストで実行されます。 |

1. **追加**を選択し、変数名で **OnlinePassword** を入力します。

1. ロック変数を確認して、この変数を秘密にします。

    ![変数](media/test-studio-classic-pipeline-editor/variables.png "変数")

1. パイプライン構成を**保存**します。

## <a name="run-and-analyze-tests"></a>テストを実行して分析する

テストが正常に実行されているか検証するには、**キュー**を選択し、次に**実行**を選択します。 ジョブが実行を開始します。

![ジョブを実行](media/test-studio-classic-pipeline-editor/run-job.png "ジョブの実行")

ジョブの実行中に、ジョブを選択して、実行中の各タスクの詳細な状態を表示します。

![ジョブの詳細](media/test-studio-classic-pipeline-editor/job-details.png "ジョブの詳細")

ジョブが完了すると、高レベルのジョブの概要、およびエラーまたは警告を表示できます。 **テスト** タブを選択すると、実行したテスト ケースの特定の詳細を表示できます。

次の例は、Chrome ブラウザーを使用してテストを実行しているときに、少なくとも 1 つのテスト ケースが失敗したことを示しています。

![Chrome - 失敗](media/test-studio-classic-pipeline-editor/chrome-failed.png "Chrome - 失敗")

**RunTestAutomation** テストを選択し、失敗したテスト ケースの詳細をより細かく確認します。 **添付ファイル** タブで、テスト実行の概要およびテスト スイートで失敗または合格したテスト ケースを見ることができます。

![添付ファイル タブ](media/test-studio-classic-pipeline-editor/attachments-tab.png "添付ファイル タブ")

> [!NOTE]
> テスト スイートを実行する場合、合格および失敗したテスト ケースの概要が表示されます。 テスト ケースを実行すると、可能な場合、トレース情報とともに失敗に関する特定の詳細が表示されます。

## <a name="known-limitations"></a>既知の制限

- 多要素認証はサポートされていません。

- Internet Explorer 11 および Microsoft Edge はサポートされていないブラウザーです。

- テスト概要は、ブラウザーごとに 1 つのテスト結果を報告します。 テスト結果には、1 つ以上のテスト ケースまたはテスト スイートの結果が含まれます。 

- Azure Active Directory サインイン フロー以外の任意の認証プロセスは、**PowerAppsTestAutomation** ソリューションでサインイン プロセスのカスタマイズが必要です。

### <a name="see-also"></a>関連項目

- [テスト スタジオの概要](test-studio.md)
- [Test Studio の操作](working-with-test-studio.md)
- [YAML を使用してパイプラインを構成する](test-studio-yaml-pipeline.md)
