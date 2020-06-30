---
title: コードコンポーネントの作成と構築 | Microsoft Docs
description: Power Apps component framework ツールを使用してコンポーネントを作成する
keywords: Power Apps component framework、コード コンポーネント、コンポーネント フレームワーク
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 06/20/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2cbf58a-9112-45c2-b823-2c07a310714c
ms.openlocfilehash: 7fc225e385ba19377d837550c7d3e903082e753d
ms.sourcegitcommit: e1a6113bc54d23f94a2ec336076ca715df75f67f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/12/2020
ms.locfileid: "3370091"
---
# <a name="create-and-build-a-code-component"></a>コードコンポーネントを作成、構築する

この記事では、Power Apps CLI を使用してコード コンポーネントを作成してデプロイする方法について説明します。 [Microsoft Power Apps CLI](https://aka.ms/PowerAppsCLI) がインストールされていることが前提となります。

## <a name="create-a-new-component"></a>新しいコンポーネントの作成

まず、Power Apps CLI のインストール後、**VS 2017 以降の開発者コマンドプロンプト**を開きます。

1. 開発者コマンド プロンプトで、ローカルマシンに新規フォルダを作成します。たとえば、`mkdir <Specify the folder name>`コマンドを使用して、*C:\Users\your name \ Documents \ My_code_Component* を作成します。
2. コマンド `cd <specify your new folder path>` を使用して、新しく作成したフォルダに移動します。
3. このコマンドを実行して、基本パラメータを渡して新たなコンポーネントプロジェクトを作成します。

    ```CLI
    pac pcf init --namespace <specify your namespace here> --name <Name of the code component> --template <component type>
    ```
 
   > [!NOTE]
   > 現在、 Power Apps CLIでは二つの種類のコンポーネントに対応しています: モデル駆動型アプリケーションの **フィールド** と **データセット**。  キャンバス アプリの場合は、**フィールド** タイプはこの試験的なプレビューに対応しています。

4. 必要なプロジェクトの依存関係をすべて取得するには、コマンド `npm install` を実行します。
5. 任意の開発者環境でプロジェクト フォルダ ( `C:\Users\<your name>\Documents\<My_code_Component>` ) を開き、コード コンポーネントの開発を始めます。 最も手軽に開始するには、 `C:\Users\<your name>\Documents\<My_code_Component>` に移動してコマンド プロンプトで `code .` を実行する方法があります。 このコマンドは、 Visual Studio コードにあるコンポーネントプロジェクトを開きます。
6. マニフェスト、コンポーネント ロジック、スタイル設定などのコンポーネントに必要なアーティファクトを実装し、コンポーネント プロジェクトを構築します。 詳しくは： [初めてのコードコンポーネント作成](implementing-controls-using-typescript.md) を参照してください。

## <a name="build-your-component"></a>コンポーネントを構築する

コンポーネント プロジェクト を構築するには、 Visual Studio コードで `package.json` を含むプロジェクトのフォルダを開きます。(Ctrl-Shift-B) コマンドを使用して、構築オプションを選択します。 

または、VS 2017 ウィンドウの開発者向けコマンド プロンプトで  `npm run build` コマンドを使用することで、簡単にコンポーネントを構築することができます。

> [!TIP]
> 構築中、または構築完了後にコンポーネントのデバッグを行うには、 [コード コンポーネントのデバッグ](debugging-custom-controls.md) を参照してください。

TypeScript でコンポーネントロジックの実装が完了したら、すべてのコードコンポーネント要素を ソリューション ファイル に バンドル して、ソリューションを Common Data Service に インポートできるようにする必要があります。 詳細: [コード コンポーネントをパッケージする](import-custom-controls.md)

### <a name="see-also"></a>関連項目

[コード コンポーネントのデバッグ](debugging-custom-controls.md)<br/>
[コード コンポーネントをパッケージ化する](import-custom-controls.md)<br/>
[コード コンポーネントをフィールドやエンティティに追加する](add-custom-controls-to-a-field-or-entity.md)<br/>
[既存のコード コンポーネントを更新する](updating-existing-controls.md)<br/>
[Power Apps Component Framework API の参照](reference/index.md)<br/>
[Power Apps Component Framework の概要](overview.md)
