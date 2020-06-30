---
title: 一般的な問題と回避策 (Power Apps Component Framework) | Microsoft Docs
description: Power Apps Component Framework と CLI の使用中に発生する既知の問題と回避策に関する情報を提供します
keywords: ''
author: Nkrb
ms.author: nabuthuk
manager: kvivek
ms.date: 11/25/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.openlocfilehash: 8a1cf58022d28366a9f24821a5a78dc9a661b559
ms.sourcegitcommit: e1a6113bc54d23f94a2ec336076ca715df75f67f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/12/2020
ms.locfileid: "3370087"
---
# <a name="common-issues-and-workarounds"></a>共通の問題と回避策

以下は、 Power Apps Component Framework と Power Apps CLI の使用中に遭遇する可能性のある一般的な問題です。

## <a name="msbuild-error-msb4036"></a>Msbuild エラー MSB4036

- プロジェクト ファイルのタスク名はタスク クラスの名前と同じです。
- タスク クラスはパブリックで Microsoft.Build.Framework.ITask インターフェイスを実装しています。
- タスクは、プロジェクト ファイルの *\<UsingTask>* または、 パス ディレクトリに格納されている、 *.tasks ファイルにて正しく宣言されています。

**回避策**:

- Visual Studio インストーラーを開きます。
- Visual Studio 2017 以降の場合は、**修正** を選択します。
- **個別のコンポーネント** を選択します。
- コード ツール配下の **NuGet ターゲットと構築タスク** を確認します。

> [!NOTE]
> 開発プロセス中に遭遇するたびに、共通の問題と回避策を常に追加します。 問題が発生して回避策があり、それが役立つと思う場合は、 [ここ](https://powerusers.microsoft.com/t5/Power-Apps-Component-Framework/bd-p/pa_component_framework) で問題を提起するか、プル リクエストを提起して、リストを確認してリストに追加できるようにします。

## <a name="publisher-prefix"></a>発行元の接頭辞

0.4.3 より前の CLI バージョンを使用してコンポーネントを作成した場合、 Common Data Service にソリューション ファイルを再インポートしようとするとエラーが発生します。 

**回避策**:

- Common Data Serviceからソリューションに関連するコンポーネントを削除します。 
- コンポーネントが依存関係を回避するようにすでに構成されている場合は、コンポーネントをフィールドまたはグリッドから削除する必要があります。
- 最新の CLI バージョンで構築されたコンポーネントに対する更新を使用して、新しいソリューションをインポートします。
- 新たに読み込まれたコンポーネントは、フォームまたはグリッド上で設定できるようになっています。  

## <a name="issues-while-updating-existing-code-components"></a>既存のコード コンポーネントの更新中の問題

- pcf-scripts の使用方法を尋ねる 1ES 通知を取得した場合、これらのスクリプトはコード コンポーネントの作成のみに使用され、結果のコンポーネントによってバンドルまたは使用されないことに注意してください。
- CLI バージョン 0.1.817.1 以前を使用してコード コンポーネントを作成、あるいは、最新のビルドおよびデバッグ モジュールが使用されていることを確認したい場合は、以下に示すように `package.json` ファイルを更新します:
   
   ```JSON
   "dependencies": { "@types/node": "^10.12.18", "@types/powerapps-component-framework": "1.1.0"}, "devDependencies": { "pcf-scripts": "~0", "pcf-start": "~0" } 
   ```

## <a name="error-failed-to-retrieve-information-about-microsoftpowerappsmsbuildpcf-from-remote-source-feed-url-when-the-build-fails-for-authorization-issues"></a>エラー: 承認の問題でビルドが失敗したとき、リモート ソース <Feed Url> から Microsoft.PowerApps.MSBuild.Pcf に関する情報を取得できませんでした。 

   **回避策**

   - **%APPDATA%\NuGet** から `NuGet.Config` ファイルを開きます。 ユーザーがエラーを得たフィードはこのファイルにある必要があります。 
   - `NuGet.Config file` からフィードを削除するか、PATトークンを生成して、 ` Nuget.Config file` に追加します。 たとえば、次のようなものです。

     ```XML
     <?xml version="1.0" encoding="utf-8"?>  
     <configuration>  
     <packageSources>  
         <add key="CRMSharedFeed" value="https://dynamicscrm.pkgs.visualstudio.com/_packaging/CRMSharedFeed/nuget/v3/index.json" />  
      </packageSources>  
      <packageSourceCredentials>  
      <CRMSharedFeed>  
      <add key="Username" value="anything" />  
      <add key="Password" value="User PAT" />  
        </CRMSharedFeed>  
        </packageSourceCredentials>  
       </configuration>
     ```

## <a name="web-resource-size-is-too-large"></a>Web リソース サイズが大きすぎます

エラー  **ソリューションのインポート エラー: Web リソースのコンテンツサイズが大きすぎます**。

**回避策**

- コマンドを使用して webpack を運用モードに設定するリリース構成として `.pcfproj` をビルドします 
  ```CLI
  msbuild /property:configuration=Release
  ```
- 以下に示すように、追加のプロパティを指定して msbuild コマンドを実行します: 
  ```CLI
  msbuild /p:PcfBuildMode=production
  ```
- プロパティ `PcfBuildMode` を運用に設定して、常に運用モードで webpack をビルドするように `.pcfproj` を編集します:
  ```XML
  <PropertyGroup>
    <Name>TS_ReactStandardControl</Name>
    <ProjectGuid>0df84c56-2f55-4a80-ac9f-85b7a14bf378</ProjectGuid>
    <OutputPath>$(MSBuildThisFileDirectory)out\controls</OutputPath>
    <PcfBuildMode>production</PcfBuildMode>
  </PropertyGroup>
  ```

## <a name="when-running-power-apps-checker-with-the-solution-built-using-cli-tooling-in-default-configuration"></a>既定の構成で CLI ツールを使用して構築されたソリューションを備えた Power Apps チェッカーを実行している場合

**エラー: 「eval」関数または同等の機能を使用しないでください** 既定の `msbuild` 構成が `Configuration=Debug` であるため、この警告は仕様によるものです。 これにより、`eval()` を出力する開発モードでパッケージ化するように webpack (コード コンポーネントをバンドルするために使用) に指示されます。 

**回避策**

次のいずれかのコマンドを使用してソリューション ファイルを再構築し、ソリューションを Common Data Service に再インポートします。

```CLI
msbuild/property:configuration:Release
```

```CLI
npm run build -- --buildMode production
```

## <a name="power-apps-component-framework-datasets-getvalue-by-property-alias-doesnt-work"></a>Power Apps component framework Datasets プロパティ エイリアスによる getValue が機能しない

Power Apps component framework データセット API の getValue 関数は、マニフェストに設定されたプロパティ エイリアスではなく、データセットの列名でのみレコードを検索します。 プロパティ エイリアスによって値を取得しようとすると、空の値が返されます。

**回避策**

データセットの列名 (コンポーネントはエイリアスを使用して列配列を検索することでデータセットの列名を取得できます) を使用します。 

   ***予想される動作*** 

   ```TypeScript
   long  = dataSet.records[currentRecordId].getValue("Longitude") //based on property set in manifest"-122.3514661"
   ```

   ***現在の回避策***

   ```TypeScript
   lat = dataSet.records[currentRecordId].getValue("Address_x0020_1_x003a__x0020_Latitude")//based on the dataset column name
   ```

## <a name="power-apps-component-framework-datasets-sharepoint-issue"></a>Power Apps component framework データセット SharePoint イシュー

Power Apps component framework データセット コンポーネントは現在、SharePoint のレコードを正しく表示していません。 ネットワーク要求は正しいデータ レコードが返されて成功しますが、逆シリアル化は失敗し、空のデータセットが返されます。

**回避策**

現在のところ、回避策はありません。 展開トレインに修正プログラムをプッシュする作業を行っています。

