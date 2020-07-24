---
title: 計画 -  Power Apps プロジェクトのスコープを定義する | Microsoftドキュメント
description: スコープは、アプリを作る際のどの機能を含めるか、含めないかを直接的な影響を与え決定します。 考慮すべきスコープの制約について説明します。
author: taiki-yoshida
ms.service: powerapps
ms.topic: conceptual
ms.custom: guidance
ms.date: 06/16/2020
ms.author: tayoshi
ms.reviewer: kathyos
ms.openlocfilehash: 97854c73d1bc7447849f603bc1c629d0091b419f
ms.sourcegitcommit: 213c46f7055eb71b9064b0645d8d17cf8eaad179
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/16/2020
ms.locfileid: "3461588"
---
# <a name="defining-the-project-scope"></a>プロジェクトのスコープの定義

プロジェクト内における達成度合いがわかるように、プロジェクトの範囲を確認しておきましょう。 何を完全なものと定義し、何をプロジェクトの範囲外を定義するのか (次のバージョンで対応すべきもの) を明確にロードマップにしておきましょう。 スコープは、アプリを作る際の[どの機能を含めるか、含めないか](prioritizing-features.md)に直接的な影響を与え決定します。

プロジェクトのスコープを定義するには、以下の制約を考慮する必要があります。

- **時間** : プロジェクトの目標を達成する期限を設定します。 小規模なプロジェクトの場合は、数週間の場合もありますが、大規模なプロジェクトの場合は数か月かかる場合があります。

- **人** : プロジェクトに携わる人数

- **予算** : 自分や同僚が費やした時間を計上する必要がある場合、または専門家を雇う必要がある場合は、予算を設定する必要があります。

- **実現可能性** : 利用可能な専門知識、必要なデータへのアクセスの欠如、または組織が求めている変化の大きさによっては制約を受ける場合があります。

また、使用可能な範囲で提供可能な機能部分についても検討する必要があります。 アプリがいくつかの機能を完全に提供していないのでは、何の役にも立ちません。各コンポーネントを実行形式でエンドツーエンドで提供する計画を立てます。 必要な機能がすべて揃っていない場合でも、使用できるものを提供してください。 プロジェクト計画では、各フェーズで何を提供するかを明確化する必要があります。

## <a name="example-expense-report-project-scope"></a>例 : 経費報告プロジェクトのスコープ

ビジネス プロセスを見ると、5つの主要なタスクに分かれていることがわかります。

1. 経費報告書の作成

2. 経費報告書の承認

3. 金融決済システムにデータを取り込む

4. 毎週の予算分析の見直し

5. 監査

![主要なタスクとタスクの場所が呼び出されたビジネス プロセス フロー チャート](media/task-chart.png "主要なタスクとタスクの場所が呼び出されたビジネス プロセス フロー チャート")

経費報告アプリと承認プロセスを作成するための専門知識を有していると前提で考えます。 監査の要件は、経費報告書の承認に必要なものとかなり重複しているようです。

経費報告書の作成が終われば、予算分析にも取り組めることになります。データモデルが整い次第、別の Power BI 専門家チームにも並行してプロジェクトを開始してもらうことができます。

現時点ではアクセスできないシステムの専門知識が必要となるため、データを直接金融システムに取り込むかどうかは不明です。 そのため、現時点ではプロジェクトの範囲外ですが、後のフェーズで追加する可能性が高いです。

プロジェクト全体のミッション (「従業員と経理部門にとって効率的なプロセスを作り、予算管理を迅速化し、監査での露出を減らす」) に常に立ち返ることで、プロジェクトのスコープが適切であるかを判断できます。

> [!div class="nextstepaction"]
> [次の手順 : 機能の優先順位付け](prioritizing-features.md)