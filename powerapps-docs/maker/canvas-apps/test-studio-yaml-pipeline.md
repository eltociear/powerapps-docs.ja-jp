---
title: YAML を使用して Azure Pipelines でテストを自動化する | Microsoft Docs
description: Azure Pipelines YAML を使用してテスト スイートおよびケースを自動化する方法について説明します。
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
ms.openlocfilehash: b1408e52dd9d29a10cffeb7ec811d514a9c4aba0
ms.sourcegitcommit: c017debf26774dbe621f80dccf372cd852e6026c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "3334903"
---
# <a name="automate-tests-with-azure-pipelines-using-yaml"></a>YAMLを使用して Azure Pipelines でテストを自動化する

この記事では、[Azure DevOps サービス](https://docs.microsoft.com/azure/devops/user-guide/what-is-azure-devops?view=azure-devops) の [YAML パイプライン](https://docs.microsoft.com/azure/devops/pipelines/get-started/pipelines-get-started?view=azure-devops#define-pipelines-using-yaml-syntax) を使用して、テスト スタジオで作成されたキャンバス アプリ テストを設定および実行する方法を説明します。

GitHub&mdash;[Microsoft/PowerAppsTestAutomation](https://GitHub.com/microsoft/PowerAppsTestAutomation)&mdash; でパブリック プロジェクトを使用して、次のことができます。

- アプリケーションへのサインインの操作を自動化します。
- ビルド エージェントでブラウザーを開き、一連のテスト ケースおよびスイートを実行します。
- Azure DevOps パイプラインでテスト実行の状態を表示します。

> [!NOTE]
> [テスト スタジオ](test-studio.md) 機能はまだ実験段階であり、非運用アプリのみのテストを書き込むために使用することをお勧めします。 詳細については: [実験的な機能およびプレビュー機能](working-with-experimental-preview.md)

## <a name="prerequisites"></a>前提条件

開始する前に、次の手順を実行する必要があります。

- GitHub で [Microsoft/PowerAppsTestAutomation](https://GitHub.com/microsoft/PowerAppsTestAutomation) プロジェクトを [フォーク](#step-1---fork-the-powerappstestautomation-project) します。

    > [!NOTE]
    > パブリック フォークを非公開にすることはできません。 非公開リポジトリを作成する場合は、[リポジトリを複製](https://help.GitHub.com/GitHub/creating-cloning-and-archiving-repositories/duplicating-a-repository) する必要があります。

- パイプラインから実行するアプリ テスト URL を含む、新しい [テスト URL .json ファイル](#step-2---create-a-test-url-json-file) を作成します。

- 新しい [Azure Pipelines YAML ファイル](#step-3---create-an-azure-pipeline-yaml-file) を作成します。 

- リポジトリに [GitHub サービス接続](#step-4---create-a-github-service-connection) を作成します。

### <a name="step-1---fork-the-powerappstestautomation-project"></a>ステップ 1 - PowerAppsTestAutomation プロジェクトをフォークする

*[フォーク](https://help.GitHub.com/GitHub/getting-started-with-GitHub/fork-a-repo)* はリポジトリのコピーです。 リポジトリをフォークすることによって、元のプロジェクトに影響を与えずに変更を加えることができます。

1. [GitHub](https://GitHub.com/) にサインインします。

1. [microsoft/PowerAppsTestAutomation](https://GitHub.com/microsoft/PowerAppsTestAutomation) リポジトリに移動します。 代わりに **microsoft/PowerAppsTestAutomation** を検索して、リポジトリを選択することもできます。

    ![GitHub を検索する](media/test-studio-classic-pipeline-editor/search-GitHub.png "GitHub を検索する")

1. **フォーク**を選択します。

    ![フォーク](media/test-studio-classic-pipeline-editor/fork.png "フォーク")

1. フォークを保存する場所を選択します。

    ![フォーク アカウント](media/test-studio-classic-pipeline-editor/fork-account.png "フォーク アカウント")

フォークされたリポジトリが使用できるようになりました。

### <a name="step-2---create-a-test-url-json-file"></a>ステップ 2 - テスト URL .json ファイルを作成する

テスト URL .json ファイルには、アプリを検証するためのテスト スイートおよびテスト ケースの URL が含まれます。 アプリ テスト スイートおよびテスト ケースの URL は、テスト スタジオで[再生リンクをコピーする](working-with-test-studio.md#playing-tests-in-a-browser) を選択することにより取得できます。

前の手順で作成したリポジトリで、サンプル ファイルである Samples/TestAutomationURLs.json を見つけることができます。

1. リポジトリに TestURLs.json ファイルという名前の新しいファイルを作成するか、または任意のファイル名を使用します。 ファイル名および場所は、ドキュメントの後半でパイプライン変数にマップされます。

1. Samples/TestAutomationURLs.json ファイルから形式をコピーします。

1. アプリで検証するテストで、**テスト URL** セクションを更新します。

1. 変更をリポジトリにコミットします。

    ![JSON ファイルを更新する](media/test-studio-classic-pipeline-editor/json-update.png "JSON ファイルを更新する")

### <a name="step-3---create-an-azure-pipeline-yaml-file"></a>ステップ 3 - Azure Pipeline YAML ファイルを作成する

前の手順で作成したリポジトリで、サンプル ファイルである Samples/azure-pipelines.yml を見つけることができます。

1. リポジトリに、azure-pipelines.yml ファイルという名前の新しいファイルを作成します。

1. Samples/azure-pipelines.yml ファイルからコンテンツをコピーします。

1. 変更をリポジトリにコミットします。 ステップ 4 でパイプラインを構成するときに、azure-pipelines.yml ファイルを参照して更新します。

### <a name="step-4---create-a-github-service-connection"></a>ステップ 4 - GitHub サービス接続を作成する

1. Azure DevOps インスタンスにサインインします。

1. 既存のプロジェクトを選択するか、または新しいプロジェクトを作成します。

1. 左側のナビゲーション ウィンドウの下部で**プロジェクト設定**を選択します。

    ![パイプラインの作成](media/test-studio-yaml-pipeline/project-settings.png "パイプラインの作成")

1. **パイプライン**で、**サービス接続**を選択します。

    ![サービス接続](media/test-studio-yaml-pipeline/select-service-connections.png "サービス接続")

1. **サービス接続の作成**を選択します。

1. **GitHub** サービスを選択します。

1. **次へ** を選択します。

    ![GitHub サービス接続](media/test-studio-yaml-pipeline/select-GitHub.png "GitHub サービス接続")

1. **OAuth 構成**で、**AzurePipelines** を選択します。

1. **承認**を選択します。

    ![サービス接続の承認](media/test-studio-yaml-pipeline/azure-pipelines-authorize.png "サービス接続の承認")

1. オプションで、**サービス接続名**を更新できます。

1. **保存**を選択します。

    ![サービス接続の保存](media/test-studio-yaml-pipeline/service-connection-save.png "サービス接続の保存")

## <a name="create-a-pipeline"></a>パイプラインの作成

1. 左側のナビゲーション ウィンドウで、**パイプライン**を選択します。

1. **パイプラインの作成**を選択します。

    ![パイプラインの作成](media/test-studio-classic-pipeline-editor/create-pipeline.png "パイプラインの作成")

1. **GitHub YAML** を選択します。

    ![GitHub YAML](media/test-studio-yaml-pipeline/use-github-yaml.png "GitHub YAML")

1. リポジトリを検索または選択します。

    ![リポジトリの選択](media/test-studio-yaml-pipeline/select-repo.png "リポジトリの選択")

1. **既存の Azure Pipelines YAML ファイル**を選択します。

1. 前の手順で作成した [Azure YAML パイプライン ファイル](#step-3---create-an-azure-pipeline-yaml-file) へのパスを設定します。

1. **続行**を選択します。

    ![YAML の確認](media/test-studio-yaml-pipeline/use-existing-pipelines-yaml.png "YAML の確認")

    azure-pipelines.yml ファイルが表示されます。

    ![Azure YAML の確認](media/test-studio-yaml-pipeline/review-pipeline-yaml.png "Azure YAML の確認")

1. リポジトリに**リポジトリ名**を更新します。 

1. **エンドポイント**を、前の手順で作成した [GitHub サービス接続](#step-4---create-a-github-service-connection) の名前に更新します。

    ![YAML エンドポイント](media/test-studio-yaml-pipeline/update-yaml-endpoint.png "YAML エンドポイント")

1. **TestAutomationURLs** ファイル名を更新します。 これは、前の手順で作成した[テスト URL .json ファイル](#step-2---create-a-test-url-json-file) のファイルです。

1. 変更した場合は、**LocalProjectName** 値をリポジトリ名に更新します。

1. **TestAutomationURLFilePath** を、リポジトリのテスト URL .json ファイルの場所に更新します。

    ![テスト パラメーター](media/test-studio-yaml-pipeline/update-yaml-test-file.png "テスト パラメーター")

1. **変数**を選択します。

1. **OnlineUsername** という名前の変数を追加し、値をアプリケーションにサインインするユーザー コンテキストの Azure Active Directory (Azure AD) のメール アドレスに設定します。 テストは、このユーザー アカウントのコンテキストで実行されます。

1. **OK** を選択します。

1. **OnlinePassword** という名前の別の変数を追加します。 値を、前の手順で作成した Azure AD アカウントのパスワードに設定します。

1. **この値を秘密に保持する**、および**このパイプラインの実行時にユーザーがこの値を上書きできるようにする**を選択します。
 
    ![パイプライン変数](media/test-studio-yaml-pipeline/set-password-variable.png "パイプライン変数")

1. リポジトリの変更を**保存**および**確定**します。  

    ![パイプライン構成を保存する](media/test-studio-yaml-pipeline/save-pipeline.png "パイプライン構成を保存する")

## <a name="run-and-analyze-tests"></a>テストを実行して分析する

テストが正常に実行されているかどうかを検証するには、**実行**を選択します。 必要に応じて、オプションで、テストを実行するサーバー イメージおよびブラウザーの種類を選択できます。

![ジョブを実行](media/test-studio-yaml-pipeline/run-job.png "ジョブの実行")

ジョブの実行中に、それを選択して、実行中の各タスクの詳細な状態が表示されます。

![ジョブの詳細](media/test-studio-yaml-pipeline/job-details.png "ジョブの詳細")

ジョブが完了されると、高レベルのジョブの概要、およびエラーまたは警告を表示できます。 **テスト** タブを選択すると、実行したテスト ケースの特定の詳細を表示できます。

次の例は、Chrome ブラウザーを使用してテストを実行しているときに、少なくとも 1 つのテスト ケースが失敗したことを示しています。

![Chrome - 失敗](media/test-studio-classic-pipeline-editor/chrome-failed.png "Chrome - 失敗")

**RunTestAutomation** を選択し、失敗したテスト ケースに関する詳細をより細かく確認します<!--Edit okay?-->。 **添付ファイル** タブで、テスト実行の概要およびテスト スイートで失敗または合格したテスト ケースを見ることができます。

![添付ファイル タブ](media/test-studio-classic-pipeline-editor/attachments-tab.png "添付ファイル タブ")

> [!NOTE]
> テスト スイートを実行する場合、合格および失敗したテスト ケースの概要が表示されます。 テスト ケースを実行すると、可能な場合、トレース情報とともに失敗に関する特定の詳細が表示されます。

## <a name="known-limitations"></a>既知の制限

- 多要素認証はサポートされていません。

- Internet Explorer 11 および Microsoft Edge はサポートされていないブラウザーです。

- テスト概要は、ブラウザーごとに 1 つのテスト結果を報告します。 テスト結果には、1 つ以上のテスト ケースまたはテスト スイートの結果が含まれます。

- Azure AD サインイン以外の任意の認証プロセスについて、**PowerAppsTestAutomation** ソリューションでサインイン プロセスをカスタマイズする必要があります。

### <a name="see-also"></a>関連項目

- [テスト スタジオの概要](test-studio.md)
- [Test Studio の操作](working-with-test-studio.md)
- [クラシック エディターを使用して Azure Pipelines でテストを自動化する](test-studio-classic-pipeline-editor.md)