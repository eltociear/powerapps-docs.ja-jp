---
title: Power Apps CLI のインストール | MicrosoftDocs
description: Microsoft Power Apps CLI を取得して、 Power Apps Component Framework を使用してコード コンポーネントを作成、デバッグおよび展開します。
keywords: Power AppsCLI、コード コンポーネント、コンポーネント フレームワーク、CLI
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 01/28/2020
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f393f227-7a88-4f25-9036-780b3bf14070
ms.openlocfilehash: e0375e3879969e4d3b8881c50ce1db37010f0a97
ms.sourcegitcommit: bd543dccaa38bd63ad576f408c8b669c7e653ca3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/24/2020
ms.locfileid: "3501098"
---
# <a name="what-is-microsoft-power-apps-cli"></a>Microsoft Power Apps CLI とは 

Microsoft Power Apps CLI は、開発者とアプリ メーカーがコード コンポーネントを作成できるようにする、シンプルなシングルストップの開発者コマンド ライン インターフェイスです。 

Power Apps CLI ツーリングは、エンタープライズ開発者と ISV が拡張機能やカスタマイズを、すばやく効率的に作成、構築、デバッグ、および公開できる、包括的なアプリケーション ライフ サイクル (ALM) ストーリーの最初のステップです。  

## <a name="install-power-apps-cli"></a>Power Apps CLI のインストール

Power Apps CLI を取得するには、次の手順を実行します。

1. [Npm](https://www.npmjs.com/get-npm) (Node.js に含まれる) または [Node.js](https://nodejs.org/en/) (npm に含まれる) をインストールします。 LTS (長期サポート）) バージョン10.15.3 以降をお勧めします。

1. [.NET Framework4.6.2開発者パック](https://dotnet.microsoft.com/download/dotnet-framework/net462) をインストールします 。 

1. Visual Studio 2017 以降をお持ちでない場合は、次のいずれかの方法に従ってください:
   - オプション1: [Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2017)以降をインストールします。
   - オプション 2: [.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/current) をインストールしてから、 [Visual Studioコード](https://code.visualstudio.com/Download) をインストールします。

1. [Power Apps CLI](https://aka.ms/PowerAppsCLI) のインストール

1. すべての最新機能を利用するには、このコマンドを使用して Power Apps CLI ツールを最新バージョンに更新します:

    ```CLI
    pac install latest
    ```

> [!NOTE]
> 現在、Power Apps CLI は Windows 10 でのみサポートされています。

## <a name="common-commands"></a>一般的なコマンド 

このテーブルには、CLI で使用されるいくつかの一般的なコマンドがリストされています。

|Command|説明|例|
|------|-----------|--------|
|**pcf**|[Power Apps コンポーネント フレームワーク](/powerapps/developer/component-framework/overview) で作業するためのコマンド。 これには次のパラメータが使用されています : <br/> - **init**：: コード コンポーネント プロジェクトを初期化します。 これには次のパラメータが使用されています <br/> - *名前空間*: コード コンポーネントの名前空間。 <br/> - *名前*: コード コンポーネントの名前です。 <br/> - *テンプレート* : フィールドまたはデータセット <br/> - **プッシュ** : コードコンポーネントを最新のすべての変更を含む Common Data Service インスタンスにプッシュします。 これには次のパラメータが使用されています: <br/> - *公開元の名* : 組織の公開元のプレフックス。<br/> - **バージョン**: コンポーネント マニフェスト ファイルを指定されたパッチ バージョンで更新します。 これには次のパラメータが使用されています : <br/> - *patchversion*: コード コンポーネントのパッチ バージョン。 `patchversion` は次のバージョン タプル (`Major.Minor.Patch`) の 3 番目の部分の値のみを取得します。<br/> - *パス*: コンポーネント マニフェスト ファイルの絶対パスまたは相対パス。<br/> - *allmanifests*: すべてのコンポーネント マニフェスト ファイルのパッチ バージョンを更新します。 <br/> - *戦略*: 指定された戦略値を使用して、マニフェスト ファイルのパッチ バージョンを更新します。| `pac pcf init --namespace <specify your namespace here> --name <Name of the code component> --template <component type>` <br/> <br/> `pac pcf push --publisher-prefix <your publisher prefix>` <br/><br/> `pac pcf version --patchversion <number> --path <Absolute or relative path to component manifest file --allmanifests`  <br/><br/> `pac pcf version --strategy gittags`|
|**ソリューション**|[Common Data Service ソリューション プロジェクト](/powerapps/maker/common-data-service/solutions-overview) で使用するコマンド。 これには次のパラメータが使用されています : <br/> - **init** : ソリューション プロジェクトを初期化します。 これには次のパラメータが使用されています :<br/>  - *公開元名* : 組織の公開元の名前。 <br/>  - *公開元の名* : 組織の公開元のプレフックス。 <br/> - **参照の追加** : `path` パラメータを渡すことで、参照パスをコンポーネント プロジェクト フォルダーに設定します。<br/> - **クローン**: 次のパラメーターを渡すことにより、既存のソリューション プロジェクトに基づいてソリューション プロジェクトを作成します。<br/> -*名前*: エクスポートするソリューションの名前。<br/> -*targetversion*: エクスポートしたソリューションがサポートするバージョン。<br/> -*含む*: エクスポートするソリューションに含める必要がある設定。<br/> -**エクスポート**: 現在の組織から Common Data Service ソリューション プロジェクトをエクスポートします。 これには次のパラメータが使用されています :<br/> -*パス*: エクスポートしたソリューションの zip ファイルが保存される場所。<br/> - *名前*: エクスポートする必要があるソリューションの名前。<br/> - *管理型*: ソリューションを管理ソリューションとしてエクスポートする必要があるかどうかを定義します。<br/>-*targetversion*: エクスポートしたソリューションがサポートするバージョン。<br/> -*含む*: エクスポートするソリューションに含める必要がある設定。|`pac solution init --publisher-name <enter your publisher name> --publisher-prefix <enter your publisher prefix>` <br/><br/> `pac solution add-reference --path <path to your Power Apps component framework project>`<br/><br/> `pac solution clone –name<name of the solution to be exported> --version <version of your solution> --include <settings that should be included>`|
|**auth**|[Common Data Service に対して認証をおこなう](/powerapps/developer/component-framework/import-custom-controls#connecting-to-your-environment) ためのコマンド。 これには次のパラメータが使用されています : <br/> - **作成** : `url` パラメータを渡すことにより、組織の認証プロファイルを作成します。 `url` パラメータのの組織 URL を渡します。 <br/> - **リスト** : 認証プロファイルのリストを提供します。 <br/> - **選択** : `index`パラメータを渡すことにより、以前に作成された認証プロファイルを切り替える方法を提供します。<br/>**削除** : `index`パラメータを渡すことによって作成された認証プロファイルを削除します。|`pac auth create --url <your Common Data Service org’s url>` <br/> <br/> `pac auth list` <br/><br/> `Pac auth select --index <index of the active profile>`|
|**テレメトリ**|テレメトリ設定を管理します。 これには次のパラメータが使用されています : <br/>- *有効化* : テレメトリ オプションを有効にします。<br/> - *無効にする* : テレメトリ オプションを無効にします。<br/> - *状態* : テレメトリが有効か無効かを返します。|`pac telemetry enable` <br/><br/> `pac telemetry disable`|
|**org**|Common Data Service と作業するためのコマンド。|`pac org who`|
|**プラグイン**|[プラグイン](/powerapps/developer/common-data-service/plug-ins) プロジェクトの作成を管理する|`pac plugin init`|

## <a name="uninstall-power-apps-cli"></a>Power Apps CLI をアンインストールします。

Power Apps CLI ツールをアンインストールするには、[こちら](https://aka.ms/PowerAppsCLI)から MSI を実行してください。

**プライベート プレビュー** の参加者の方で、CLI の古いバージョンをお持ちの場合は、次の手順を実行します:

1. Power Apps CLI がインストールされた場所を調べるには、コマンド プロンプトを開いて `where pac` と入力します。

1. PowerAppsCLI フォルダを削除します。

1. コマンド プロンプトでコマンド `rundll32 sysdm.cpl,EditEnvironmentVariables` を実行し、環境変数ツールを開きます。

1. `User variable for...` セクションの `Path` をダブルクリックします。

1. PowerAppsCLI のパスを含む行を選択して、右側の **削除** ボタンを選択します。

1. **OK** を 2 回選択します。


## <a name="see-also"></a>関連項目

[Power Apps コンポーネント フレームワーク](../component-framework/overview.md)