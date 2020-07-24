---
title: Power Apps プロジェクト - フィードバックとテレメトリー | Microsoftドキュメント
description: アプリの改善方法として、フィードバックを収集し、遠隔測定を分析することは、アプリを洗練させるプロセスにおける重要な部分です。
author: taiki-yoshida
ms.service: powerapps
ms.topic: conceptual
ms.custom: guidance
ms.date: 06/16/2020
ms.author: tayoshi
ms.reviewer: kathyos
ms.openlocfilehash: 65ca35ba7dbd3cf0f11b09eae7a8790804294821
ms.sourcegitcommit: 213c46f7055eb71b9064b0645d8d17cf8eaad179
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/16/2020
ms.locfileid: "3461583"
---
# <a name="collecting-feedback-and-analyzing-telemetry"></a>フィードバックの収集とテレメトリの分析

アプリの改善方法として、フィードバックを収集し、遠隔測定を分析することは、アプリを洗練させるプロセスにおける重要な部分です。 計画フェーズで設定した目標を振り返り、アプリがどれだけ貢献しているかを振り返ります。

## <a name="collecting-feedback"></a>フィードバックの収集

フィードバックを入力する場を提供することで、アプリが引き続きユーザーのニーズを反映するようになります。 Microsoft Forms と Power Automate を活用することで、貴重なフィードバックを自動的に収集します。 Forms にはネット プロモーター スコアが組み込まれています。

## <a name="analyzing-telemetry"></a>テレメトリの分析

アプリを正常に使用するには、アプリの分析機能を活用する必要があります。 Power Apps アナリティクスは、次のような情報を提供します。

- アクティブ ユーザー数

- 使用されているブラウザーとデバイス

- 場所

- アプリの診断

- サービスのパフォーマンス

アプリの作成者は、[https://make.powerapps.com](https://make.powerapps.com) でアプリの使用状況レポートにアクセスして、分析情報を利用できます。 このレポートは、キャンバス アプリの所有者または共同所有者が利用できます。 データは30日間利用でき、アプリの起動数、日別のユニーク ユーザーなどの使用状況を表示できます。

![アプリの使用状況レポートのスクリーンショット](media/telemetry.png "アプリの使用状況レポートのスクリーンショット")

管理者の場合、全体的なテナント レベルでアナリティクスにアクセスできます。
詳細情報 : [Power Apps の管理者分析](https://docs.microsoft.com/power-platform/admin/analytics-powerapps)

### <a name="adding-manual-telemetry-using-azure-application-insights"></a>Azure Application Insights を使用した手動テレメトリの追加

[Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview) の機能の一部である Application Insights への接続を設定することで、アプリに関するさらなる分析情報やテレメトリを得ることができます。
これを設定することで得られるテレメトリには、次のものがあります。

- アプリを使用しているアクティブ ユーザーの数。

- アプリが使用されている場所。

- 最も使用されている画面。

- ある画面から別の画面へのユーザー フロー。

![Application Insights のスクリーンショット](media/app-insights.png "Application Insights のスクリーンショット")

[トレース機能](../../maker/canvas-apps/functions/function-trace.md)を使用してカスタム テレメトリを設定することもできます。
