---
title: PowerApps Component Framework のツールの入手 | Microsoft Docs
description: Microsoft PowerApps CLI を取得して、 PowerApps Component Framework を使用してコード コンポーネントを作成、デバッグおよび展開します。
keywords: PowerApps component framework、コード コンポーネント、コンポーネント フレームワーク
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f393f227-7a88-4f25-9036-780b3bf14070
ms.openlocfilehash: 496b7d443775da075dd8da52ac4b0a754121bf28
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749058"
---
# <a name="get-tooling-for-powerapps-component-framework"></a>PowerApps Component Framework のツールを入手します。

PowerApps Component Framework を使用して、コード コンポーネントを作成、デバッグ、および展開するには、**Microsoft PowerApps CLI** (コマンドライン インターフェイス) を使用します。 PowerApps CLI を使用すると、開発者はコードコンポーネントを簡単に作成することができます。 将来的に、追加の開発やアプリケーション ライフサイクル管理 (ALM) のエクスペリエンスのサポートを含むように拡張されます。 

## <a name="what-is-microsoft-powerapps-cli"></a>Microsoft PowerApps CLI とは 

Microsoft PowerApps CLIは、開発者やアプリ作成者がコード コンポーネントを作成できるようにするシンプルでワンストップな開発者向けコマンド ライン インターフェイスです。 PowerApps CLI ツールは、エンタープライズ開発者と ISV が拡張機能とカスタマイズを、すばやく効率的に作成、構築、デバッグ、および公開できる、包括的な ALM ストーリーの最初のステップです。  

## <a name="install-microsoft-powerapps-cli"></a>Microsoft PowerApps CLI のインストール

Microsoft PowerApps CLI を取得するには、次の手順を実行します。

1. [Npm](https://www.npmjs.com/get-npm) (Node.js に含まれる) または [Node.js](https://nodejs.org/en/) (npm に含まれる) をインストールします。 最も安定している LTS (長期サポート) バージョン 10.15.3 LTS をお勧めします。

1. [.NET Framework4.6.2開発者パック](https://dotnet.microsoft.com/download/dotnet-framework/net462) をインストールします 。 

1. Visual Studio 2017 以降をお持ちでない場合は、次のいずれかの方法に従ってください:
   - オプション1: [Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2017)以降をインストールします。
   - オプション 2: [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) をインストールしてから、 [Visual Studioコード](https://code.visualstudio.com/Download) をインストールします。

1. [Microsoft PowerApps CLI](https://aka.ms/PowerAppsCLI) のインストール
1. すべての最新機能を利用するには、このコマンドを使用して PowerApps CLI ツールを最新バージョンに更新します:

    ```CLI
    pac install latest
    ```

> [!NOTE]
> - PowerApps CLI を使用してコード コンポーネントを展開するには、システム管理者またはシステム カスタマイザー特権を持つ Common Data Service 環境が必要です。
> - 現在、PowerApps CLI は Windows 10 でのみサポートされています。

## <a name="microsoft-powerapps-cli-telemetry"></a>Microsoft PowerApps CLI テレメトリ

PowerApps CLI ツールで開発者によってどの機能や能力が最も頻繁に使用されるかを理解するために、この機能のチームは匿名化したテレメトリを集約しています。 集計データは不可欠なことに焦点を合わせて、顧客に最高のエクスペリエンスを提供することを可能にします。

> [!NOTE]
> テレメトリ収集を無効にするには、次のコマンド `pac telemetry disable` を実行します。 テレメトリを元に戻すには、次のコマンド `pac telemetry enable` を使用します。


## <a name="uninstall-microsoft-powerapps-cli"></a>Microsoft PowerApps CLI をアンインストールします。

PowerApps CLI ツールをアンインストールするには、[こちら](https://aka.ms/PowerAppsCLI)から MSI を実行してください。 

プライベート プレビューの参加者の方で、CLI の古いバージョンをお持ちの場合は、次の手順を実行します:

1. PowerApps CLI がインストールされた場所を見つけるには、コマンド プロンプトを開いて `where pac` と入力します。
1. PowerAppsCLI フォルダを削除します。
1. コマンド プロンプトでコマンド `rundll32 sysdm.cpl,EditEnvironmentVariables` を実行し、環境変数ツールを開きます。
1. `User variable for...` セクションの `Path` をダブルクリックします。
1. PowerAppsCLI のパスを含む行を選択して、右側の **削除** ボタンを選択します。
1. **OK** を 2 回選択します。

### <a name="see-also"></a>関連項目

[TypeScript を使ってコンポーネントを実装する](implementing-controls-using-typescript.md)<br/>
