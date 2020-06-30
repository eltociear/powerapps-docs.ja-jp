---
title: コンポーネントのインポート | Microsoft Docs
description: この記事では、コード コンポーネントをインポートする方法について説明します
keywords: ''
ms.author: nabuthuk
manager: kvivek
ms.date: 06/20/2019
ms.service: powerapps
ms.suite: ''
ms.topic: article
author: Nkrb
ms.openlocfilehash: 1ca2846dd061f46a34fc1034ace5eb934f6ad543
ms.sourcegitcommit: b8845f5acb74b5204ef40df1b3d4b70ceeced1d9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "3419536"
---
# <a name="package-a-code-component"></a>コード コンポーネントをパッケージ化する

この記事では、コード コンポーネントを Common Data Service にインポートする方法について説明します。 Power Apps CLIを使用してコード コンポーネントを実装した後、次の手順としては、すべてのコード コンポーネント要素をソリューション ファイルにバンドルし、ソリューション ファイルを  Common Data Service にインポートします。これによりランタイムでコード コンポーネントを表示できるようになります。

ソリューション ファイルを作成およびインポートするには:

1.  `pcfproj` ファイルを持つフォルダー内に、`mkdir Solutions`と言うコマンドを使用して新しいフォルダーを作成して **ソリューション** (または任意の名前) として名前を付けます。 コマンド `cd Solutions` を使用して、ディレクトリに移動します。

2. 次のコマンドを使用して新しいソリューション プロジェクトを作成します。 ソリューション プロジェクトは、Common Data Service へインポートするために使用されるソリューション zip ファイルにコード コンポーネントをビルドするために使用されます。
   
   ```CLI
   pac solution init --publisher-name developer --publisher-prefix dev
   ```

   > [!NOTE]
   > `publisher-name` と `publisher-prefix` の値は環境に固有である必要があります。
 
3. 新しいソリューション プロジェクトが作成されたら、作成したサンプル コンポーネントがある場所の **ソリューション** フォルダーを参照します。 以下に示すコマンドを使用して参照を追加することができます。 この参照は、コード コンポーネントがビルド中に追加すべきソリューションのプロジェクトを通知します。 参照を 1 つのソリューションのプロジェクトの複数コンポーネントへ追加できます。

   ```CLI   
    pac solution add-reference --path c:\downloads\mysamplecomponent
   ```

3. ソリューション プロジェクトから zip ファイルを生成するには、ソリューション プロジェクトのディレクトリに移動して、以下のコマンドを使用してプロジェクトを構築する必要があります。 このコマンドは *MSBuild* を使用して、復元の一部として *NuGet* の依存関係をプルダウンすることで、ソリューション プロジェクトを構築します。 初めてソリューションプロジェクトを構築する際には `/restore` のみを使用します。 その後の各ビルドに対しては、コマンド `msbuild` を実行できます。

   ```CLI
   msbuild /t:build /restore
   ```

    > [!TIP]
    > - msbuild 15.9.*がパスに存在しない場合は、VS2017の開発者コマンドプロンプトを開いて `msbuild` コマンドを実行します。
    > - *デバッグ* 構成でソリューションをビルドして、アンマネージド ソリューション パッケージを生成します。 管理ソリューション パッケージは、*リリース* 構成でソリューションを構築することにより生成されます。 これらの設定は、`cdsproj` ファイルの `SolutionPackageType` プロパティを指定することでオーバーライドできます。
    > - 運用ビルドを発行するために`Release` にmsbuild構成を設定できます。 例: `msbuild /p:configuration=Release`
    > - ソリューションで `msbuild` コマンドを実行する際に *Ambiguous project name* と言うエラーが発生した場合は、ソリューション名とプロジェクト名が同じでないことを確認してください。

4. 生成されたソリューション ファイルは、ビルド正常に行なわれたら `\bin\debug\` フォルダー内に配置されます。
5. Web ポータルを使用して手動で [ソリューションを Common Data Service](https://docs.microsoft.com/powerapps/maker/common-data-service/import-update-export-solutions) にインポートするか、[Microsoft Power Platform Build Tools](https://marketplace.visualstudio.com/items?itemName=microsoft-IsvExpTools.PowerApps-BuildTools) を使用して自動的にインポートします。

## <a name="connecting-to-your-environment"></a>環境に接続しています

Common Data Service 環境に接続することで Power Apps CLI から直接コード コンポーネントを展開し、更新されたコンポーネントをプッシュできます。

認証プロファイルを作成するには、次の手順に従って、Common Data Service に接続し、更新したコンポーネントをプッシュします。 
 
1. 次のコマンドを使用して、認証プロファイルを作成します。 
 
    ```CLI
    pac auth create --url https://xyz.crm.dynamics.com 
    ```
 
2. 前に認証プロファイルを作成した場合は、次のコマンドを使用してすべての既存プロファイルを表示できます。 

   ```CLI
    pac auth list 
   ```
 
3. 前に作成した認証プロファイル間を切り替えるには、次のコマンドを使用します: 
   
   ```CLI
    pac auth select --index <index of the active profile>
    ``` 

4. 環境に関する基本情報を取得するには、次のコマンドを使用します。 接続は既定の認証のプロファイルを使用しておこないます。 

    ```CLI
    pac org who 
    ```
 
5. 特定の認証プロファイルを削除するには、`pac auth delete --index <index of the profile>` コマンドを使用します。 
6. ローカル コンピューターからすべての認証プロファイルをオフにする場合は、`pac auth clear` コマンドを使用します。 この操作は、ローカル コンピュータから完全に `authprofile.json` ファイルやトークン キャッシュ ファイルを削除するため不可逆です。 

## <a name="deploying-code-components"></a>コード コンポーネントのデプロイ 

正常に認証プロファイルを作成したら、すべて最新の変更で Common Data Service インスタンスにコード コンポーネントをプッシュし始めることができます。 

`push` 機能は、コード コンポーネントのバージョン管理要件をバイパスして、コード コンポーネントをインポートするためにソリューション (cdsproj) を作成する必要がないため、社内開発者サイクルの開発を高速化します。 

`push` 機能を使用するには、以下のことを行います:

1. 有効な認証のプロファイルを作成したことを確認します。
2. コード コンポーネントのプロジェクトが作成されたルート ディレクトリに移動します。
3. コマンドを実行します。

   ```CLI
   pac pcf push --publisher-prefix <your publisher prefix>
   ```

   > [!NOTE]
   > `push` コマンドで使用する公開元は、コンポーネントを含むソリューションの公開元の接頭辞と一致させる必要があります。

## <a name="create-a-solution-project-based-on-an-existing-solution-in-common-data-service"></a>Common Data Service の既存のソリューションに基づくソリューション プロジェクトの作成

Common Data Service で既存のソリューションに基づくソリューションを作成するには、コマンド `pac solution clone` を実行します。 それには、次を実行します。

1. 有効な認証のプロファイルを作成したことを確認します。
2.  コマンドを実行します。 

   ```CLI
   pac solution clone –-name(-n) <name of the solution to be exported> --targetversion(-v) <version of your solution> --include(-i) <settings that should be included>
   ```

   > [!NOTE]
   > 設定値: autonumbering、calendar、customization、emailtracking、externalapplications、general、isvconfig、marketing、outlooksynchronization、relationshiproles、sales。

詳細 : [オプションの設定](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.exportsolutionrequest?view=dynamics-general-ce-9)

## <a name="create-a-plug-in-project-and-add-a-reference-to-it-in-your-solution"></a>プラグイン プロジェクトを作成し、ソリューションへの参照を追加する 

> [!NOTE]
> プラグイン コマンドはパブリック プレビューにあり、 Power Apps CLI は、プラグイン プロジェクトへの参照を追加することで、プラグインプロジェクトの作成とソリューションへのパッケージ化をサポートするようになりました。 `pac plugin init` コマンドは、ディレクトリにテンプレートファイル (csproj、＃Plugin.cs＆ServiceHelper.cs) を作成します。 それには、次を実行します。 

1. 有効な認証のプロファイルを作成したことを確認します。
2. プロジェクトを作成するルート ディレクトリに移動します。
3.  コマンドを実行します。 

   ```CLI
   pac auth create –url <https://xyz.crm.dynamics.com>
   ```
4. コマンドを実行してプラグイン プロジェクトを作成します

   ```CLI
   pac plugin init
   ```

5. ソリューションのビルド時にプラグイン プロジェクトがビルドされるように、次のコマンドを使用してソリューション プロジェクトへの参照を追加します。

   ```CLI
   pac solution add-reference –path <path to your plugin project>
   ```

6. コマンドを実行して、ソリューションと参照プラグインをビルドします。

   ```CLI
   msbuild
   ```

## <a name="remove-components-from-a-solution"></a>ソリューションからのコンポーネントの削除

ソリューション ファイルからコード コンポーネントを削除したい場合:

1. ソリューション プロジェクト ディレクトリの `cdsproj` ファイルを編集し、コンポーネントへの参照を削除します。 以下は、コンポーネント 参照の例です:

   ```XML
   <ItemGroup>
       <Projectreference Include="..\pcf_component\pcf_component.pcfproj">
         <Project>0481bd83-ffb0-4b70-b526-e0b3dd63e7ef</Project>
         <Name>pcf_component </Name>
         <Targets>Build</Targets>
         <referenceOutputAssembly>false</referenceOutputAssembly>
         <OutputItemType>Content</OutputItemType>
         <CopyToOutputDirectory>Always</CopyToOutputDirectory>
       </Projectreference>
   </ItemGroup>
   ```

2. 以下のコマンドを使用して再構築 (またはクリーンアップ) を実行します:
   
    ```CLI
    msbuild /t:rebuild
    ```

### <a name="see-also"></a>関連項目

[モデル駆動型アプリでフィールドやエンティティにコード コンポーネントを追加する](add-custom-controls-to-a-field-or-entity.md)<br/>
[キャンバス アプリにコンポーネントを追加する](component-framework-for-canvas-apps.md#add-components-to-a-canvas-app)<br/>
[Power Apps Component Framework API の参照](reference/index.md)<br/>
[Power Apps Component Framework の概要](overview.md)
