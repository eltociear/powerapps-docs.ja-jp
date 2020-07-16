---
title: 地域政府機関の緊急応答およびモニタリング ソリューションをアップグレード | Microsoft Docs
description: 地域の IT 管理者が地域政府機関の緊急対応およびモニタリング ソリューションを組織にアップグレードするための詳細な手順を示します。
author: pankajarora-msft
manager: annbe
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 06/05/2020
ms.author: pankar
ms.reviewer: kvivek
ms.openlocfilehash: a18c82dc26525b8a9899147aedb17a910e4100d4
ms.sourcegitcommit: b5ab419dad4e9d64a5e6610641363b0d7487930a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2020
ms.locfileid: "3465641"
---
# <a name="upgrade-the-regional-governmentemergency-response-and-monitoring-solution"></a>地域政府機関の緊急応答およびモニタリング ソリューションをアップグレードする

この記事の手順を実行して、地域政府機関の緊急対応およびモニタリング ソリューションの*既存*インストールを最新バージョンにアップグレードします。

このソリューションを初めてインストールする場合は、[ソリューションを展開する](deploy.md) を参照してください。

## <a name="prerequisites"></a>前提条件

- 地域政府機関の緊急応答およびモニタリング ソリューションが現在展開されているグローバル管理者の資格情報と環境の詳細があることを確認します。

-   アップグレードする前に、すべてのユーザーが環境から切断されていることを確認してください。 ユーザーの障害が最小限のときにアップグレード プロセスを計画する必要がある場合があります。   

## <a name="step-1-download-the-upgrade-deployment-package"></a>手順1: アップグレード展開パッケージをダウンロードする

<https://aka.ms/rer-solution> から最新の展開パッケージ (.zip) を取得します。 これは、新規の展開ステップ中にダウンロードしたものと同じ展開パッケージです。

**重要:** .zip ファイルを解凍する前に、ファイルのブロックを解除してください。

1.  .zip ファイルを右クリックし、**プロパティ**を選択します。

2.  プロパティ ダイアログボックスで**ブロック解除**を選択し、**適用**を選択してから、**OK** をクリックします。

ファイルのブロックを解除した後は、.zip ファイルを抽出して、抽出されたフォルダーに以下を表示します。

.zip ファイルを解凍すると、解凍したフォルダーに以下が表示されます。

|**フォルダー**  |**説明**  |
|---------|---------|
|**パッケージ**     |  フォルダーには、Package Deployer ツールと、環境にソリューションを設定するために後でインポートするパッケージが含まれています。       |
|**Power BI テンプレート**     | レポートの構成に使用する Power BI レポートのテンプレート ファイル (.pbit) が含まれています。 詳細: [ステップ3: 最新の Power BI ダッシュボードを公開する](#step-3-publish-the-latest-power-bi-dashboard)         |
|**SampleData**     |   サンプル データのインポートに使用できるサンプル マスター データ ファイル (.xlsx) が含まれています。       |

## <a name="step-2-install-the-upgrade-package"></a>手順2: アップグレード パッケージをインストール

既存のソリューションがインストールされている場所と**同じ環境**にアップグレード パッケージをインストールします。 アップグレード パッケージは、ソリューションを**初めて**展開するときと同じように、次の 3 つの方法のいずれかでインストールできます。

- Microsoft AppSource (Power Apps 米国政府機関のユーザーのみ)。 展開トピックの [オプション A: Microsoft AppSource (米国政府機関のユーザー) からアプリをインストールする](deploy.md#option-a-install-the-app-from-microsoft-appsource-us-govt-customers) を参照してください

- Microsoft AppSource (Power Apps 市販製品のユーザー向け)。 展開トピックの [オプション B: Microsoft AppSource からアプリをインストールする](deploy.md#option-b-install-the-app-from-microsoft-appsource) を参照してください

- 以前にダウンロードした展開パッケージ。 展開トピックの [オプション C: アプリを展開パッケージからインストールする](deploy.md#option-c-install-the-app-from-the-deployment-package) を参照してください

## <a name="step-3-publish-the-latest-power-bi-dashboard"></a>ステップ 3: 最新の Power BI ダッシュボードを公開

アップグレード パッケージの .pbit ファイルを使用して、最新の Power BI ダッシュボードを構成および公開します。 

.pbit ファイルを使用する手順は、元の展開と同じです。Power Apps ポータルへの埋め込みに使用される Power BI レポート URL を保持したい場合は、同じワークスペースを使用して既存の Power BI ダッシュボードを上書きすることを確認してください。 

詳細: デプロイのトピックにある [ステップ 5: Power BI ダッシュボードを構成して公開する](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/deploy#step-5-configure-and-publish-power-bi-dashboard)。

## <a name="step-4-verify-the-power-bi-report-url-in-your-portal"></a>ステップ 4: ポータルで Power BI レポート URL を検証

このステップは、新しいワークスペースでダッシュボードを公開するための前のステップで、Power BI レポート URL が変更された場合のみ必要です。 自分のポータルで **PowerBI パス** サイトを確認して、最新の Power BI レポート URL で値を更新します。

詳細な手順については、デプロイトピックの [ポータルに Power BI レポートを埋め込む](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/deploy#the-process-1) を参照してください。

変更を有効にするために、必ずポータルを再起動します。 詳細: デプロイ トピックの [ポータルを再起動する](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/deploy#restart-the-portal)。

## <a name="step-5-verify-the-processes"></a>ステップ 5: プロセスを確認する

**招待状を送信**および**連絡先にパスワードのリセットを送信**プロセスが、まだ有効であることを確認します。つまり、**差出人**フィールドにメールを送信できるアカウントがあるなら、残りの詳細は問題ありません。

これらのプロセスを修正する方法の詳細については、デプロイ トピックの [ステップ10: アプリのプロセスを修正する](/powerapps/sample-apps/regional-emergency-response/deploy#step-10-fix-the-processes-for-the-app) を参照してください。

## <a name="step-6-verify-the-flows-for-sending-emails"></a>ステップ 6 : メールの送信フローを修正する

次の手順を実行します。

|フロー名|変更|
|--|--|
|**ポータル ユーザーの要請: 要請の却下時に管理者にメールを送信**|接続を更新して Common Data Service に接続し、電子メールを送信するユーザー アカウントを指定します。|
|**ポータル ユーザーの要請: 要請の作成時に管理者にメールを送信**|接続を更新して Common Data Service に接続し、電子メールを送信するユーザー アカウントを指定します。 さらに、ポータル URL に基づいて、電子メール本文のポータル URL を更新します。| 

この詳細については、デプロイ トピックの [ステップ 11.1: メール送信のフロー詳細を修正する](deploy.md##step-111-fix-the-flows-for-sending-emails) を参照してください。

## <a name="step-7-verify-the-flows-for-performing-tasks"></a>ステップ 7: タスクを実行するフローを確認する

特定のタスクを実行するためのフローの接続情報を確認および承認します。

これをおこなうための詳細については、[ステップ 11.2: 特定のタスクを実行するためのフローを修正する](/powerapps/sample-apps/regional-emergency-response/deploy#step-112-fix-the-flows-for-performing-specific-tasks) を参照してください。