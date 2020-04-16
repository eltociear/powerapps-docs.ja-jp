---
title: 'サンプル: 基本プラグインの作成 (Common Data Service) | Microsoft Docs'
description: このサンプルはフォローアップ活動を作成する簡単なプラグインの作成方法を示します。
ms.custom: ''
ms.date: 1/29/2019
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: samples
author: JimDaly
ms.author: pehecke
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: c3df411b45640551781e37d5b349ee4c4640086d
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155919"
---
# <a name="sample-create-a-basic-plug-in"></a>サンプル: 基本プラグインの作成

このサンプルはフォローアップ活動を作成する簡単なプラグインの作成方法を示します。 サンプルは [ここ](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/FollowupPlugin) からダウンロードできます。

## <a name="how-to-run-this-sample"></a>このサンプルを実行する方法

1. [サンプル](https://github.com/Microsoft/PowerApps-Samples) リポジトリをダウンロードまたは複製して、ローカル コピーを用意します。 このサンプルは PowerApps-Samples-master\cds\orgsvc\C#\FollowupPlugin にあります。
2. Visual Studio でサンプル ソリューションを開き、プロジェクトのプロパティに移動して、ビルド中にアセンブリが署名されることを確認してください。 サンプルのアセンブリ (FollowupPlugin.dll) をビルドするに F6 を押します。
3. プラグイン登録ツールを実行して D365 サーバーのサンドボックスおよびデータベースにサンプルのアセンブリを登録します。 ステップの登録時に、作成メッセージ、アカウント エンティティ、そして非同期モードを指定します。
4. D365 アプリ を使用して適切な操作を実行して、メッセージとプラグインを登録したエンティティの要求を呼び出します（アカウントを作成）。
5. プラグインが実行されると、"FollowupPlugin：タスク アクティビティが正常に作成されました" という新しい追跡ログ エントリ、および "新しい顧客に電子メールを送信する" という件名の新しいアクティビティが表示されます。 7 日以内に有効化する予定です。
6. テストを完了したらアセンブリとステップの登録を解除します。

## <a name="what-this-sample-does"></a>このサンプルの概要

アカウントの作成時に実行されると、プラグインは 7 日以内に取引先企業の顧客をフォローアップするようにユーザーに通知するアクティビティを作成します。

## <a name="how-this-sample-works"></a>このサンプルがどのように動作するか

[このサンプルの概要](#what-this-sample-does) で説明されているシナリオをシミュレートするために、サンプルは次のことを行います。

### <a name="demonstrate"></a>使用方法

1. タスク活動を作成して後日にスケジュールする方法。
2. トレース サービスを使用して実行時の情報を記録する方法。
3. Web サービスから例外をキャッチして処理する方法。

### <a name="see-also"></a>関連項目
[プラグインを記述する](../../write-plug-in.md)  
[プラグインの登録](../../register-plug-in.md)