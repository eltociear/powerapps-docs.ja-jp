---
title: 設計 - アプリで実行するタスク | Microsoft Docs
description: Power Appsプロジェクトの設計フェーズの一環として、アプリで実行するタスクを特定する方法を説明します。
author: TGrounds
ms.service: powerapps
ms.topic: conceptual
ms.custom: guidance
ms.date: 06/16/2020
ms.author: thground
ms.reviewer: kathyos
ms.openlocfilehash: 980e43c992c4143c42ee24c4762e33178531e691
ms.sourcegitcommit: 213c46f7055eb71b9064b0645d8d17cf8eaad179
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/16/2020
ms.locfileid: "3461577"
---
# <a name="identifying-the-tasks-to-be-done-in-the-app"></a>アプリで実行するタスクを特定する

アプリで必要なタスクを特定するには、計画フェーズで作成したビジネス プロセス フローチャートを参照して、詳細を追加する必要があります。 情報を整理し、各画面で実行するタスクをリスト化します。

タスクを書くときは、画面やアプリを使うペルソナごとにタスクを考慮するようにしてください。 それらをセクション別に仕分けをしてください。

ユーザーが実行する必要があるタスクとともに、各タスクの完了に必要となる情報についてのメモを参照してください。 これにより、保存や表示する必要がある情報を定義するの際に役立ちます。

複数の人と作業している場合、Microsoft Planner や Microsoft Whiteboard アプリなどのツールを使用すると、効率的に共同作業を行い、タスクの一覧の作成に役立ちます。

## <a name="example-tasks-for-creating-and-viewing-expense-reports"></a>例 : 経費報告書を作成および表示するためのタスク

経費報告書を作成し、表示する人々が行うタスクについて検討しました。 承認と毎週の予算報告については、別途検討を行います。

![アプリを作成および表示する経費報告書のタスクを含むビジネス プロセス フローチャート](media/app-tasks.png "アプリを作成および表示する経費報告書のタスクを含むビジネス プロセス フローチャート")

上記に基づき、経費レポートの作成/表示アプリには次の画面とコンポーネントが必要であると判断しました :

- フィルター付きのレポートのリスト

- 編集モードと表示専用モードを備えた単一のレポート ビュー

- キャンセル、保存、送信を行う編集ビューのボタン

- データのエクスポートに使用するアカウンティング用のボタン

- さまざまな送信/キャンセル/保存に関するメッセージ

- レシートの写真を添付して添付ファイルを閲覧できる機能

> [!div class="nextstepaction"]
> [次のステップ : 画面のスケッチ](sketching.md)
