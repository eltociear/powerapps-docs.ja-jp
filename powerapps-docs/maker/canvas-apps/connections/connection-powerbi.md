---
title: Power BI の接続の概要 | Microsoft Docs
description: 使用可能な Power BI 接続について説明します
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/12/2016
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 40741bbaaba75f6cb1312057d5bba8c02ea15835
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3306315"
---
# <a name="connect-to-power-bi-from-power-apps"></a>Power Apps から Power BI に接続する
![Power BI](./media/connection-powerbi/powerbiicon.png)

Power BI は一連のビジネス分析ツールで、データを分析したりインサイトを共有します。 さまざまなデバイスに対応した機能豊富なダッシュボードでビジネスを監視し、すばやく回答を得ることができます。 アプリでは、Power BI サービスで設定しているデータ アラートの状態を確認できます。 Power BI でのデータ アラートの詳細については、[ドキュメント ページ](https://docs.microsoft.com/power-bi/service-set-data-alerts) を参照してください。

このトピックでは、アプリで Power BI の接続を使用する方法を説明し、使用可能な関数の一覧を表示します。

## <a name="prerequisites"></a>前提条件
* [サインアップ](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)
* Power BI [接続](https://powerapps.microsoft.com/tutorials/add-manage-connections/) を追加する
* [テンプレート](https://powerapps.microsoft.com/tutorials/get-started-test-drive/)から、[データ](https://powerapps.microsoft.com/tutorials/get-started-create-from-data/)から、または[新規に](https://powerapps.microsoft.com/tutorials/get-started-create-from-blank/)アプリを作成する

## <a name="use-the-power-bi-connection-in-your-app"></a>アプリで Power BI 接続を使用する
### <a name="list-the-alerts-that-youve-set-up-in-the-power-bi-service"></a>Power BI サービスで設定したアラートを一覧表示する
1. **挿入**メニューで、**ギャラリー**を選択し、**テキスト ギャラリー**のいずれかを追加します。
2. 現在のユーザーのアラートを表示するには、ギャラリーの [項目](../controls/properties-core.md) プロパティを次の数式に設定します:

   `PowerBI.GetAlerts()`

ギャラリーは、アラートの一覧で更新されます。 各アラートについては、アラート名、アラートの ID 番号、およびアラートが構成されたグループ ワークスペースの ID が表示されます。 アラートの詳細情報を取得するには、アラート ID が必要です。

### <a name="view-the-status-of-an-alert"></a>アラートの状態を表示する
アラートの状態を表示するには、上記の手順から取得したアラート ID で CheckAlertStatus 関数を呼び出します。

アラート ID は、リテラル文字列 (例:"1234 ") として、またはGetAlerts() 呼び出し (Gallery1.Selected.alertId など) を使用して設定しているギャラリー セクションへの参照として渡すことができます

続行するには、ラベルを追加し、その [テキスト](../controls/properties-core.md) プロパティをこれらの数式のいずれかに設定します:

* `PowerBI.CheckAlertStatus( /* alert ID that you received from GetAlert */ ).alertTitle`
* `PowerBI.CheckAlertStatus( /* alert ID that you received from GetAlert */ ).currentTileValue`
* `PowerBI.CheckAlertStatus( /* alert ID that you received from GetAlert */ ).alertThreshold`
* `PowerBI.CheckAlertStatus( /* alert ID that you received from GetAlert */ ).isAlertTriggered`

ラベルでは、アラートの現在の状態が更新されます。

## <a name="view-the-available-functions"></a>使用可能な関数を表示する
この接続には、次の関数が含まれています:

| 関数名 | 内容 |
| --- | --- |
| GetAlerts |Power BI サービスで設定したアラートを一覧表示する |
| CheckAlertStatus |特定のアラートの状態を確認する |

## <a name="getalerts"></a>GetAlerts
Power BI サービスで設定したアラートを一覧表示します。

#### <a name="input-properties"></a>入力プロパティ
ありません。

#### <a name="output-properties"></a>出力プロパティ

| プロパティ名 | データの種類 | 必要な領域 | 内容 |
| --- | --- | --- | --- |
| 値 |配列 |No |Power BI サービスで設定したデータ アラートの配列。 配列内の各要素は次のものを含みます: <ul><li>alertTitle: アラートのタイトル</li><li>alertId: アラートの ID</li><li>groupId: アラートが作成されたグループの ID</li></ul> |

## <a name="checkalertstatus"></a>CheckAlertStatus
アラートの状態を確認します。

> [!NOTE]
> このエンドポイントへの要求は、あまり頻繁に呼び出されるとアラートごとに調整されます。

#### <a name="input-properties"></a>入力プロパティ

| プロパティ名 | データの種類 | 必要な領域 | 内容 |
| --- | --- | --- | --- |
| alertId |integer |有効 |GetAlerts によって返される、アラートの ID |

#### <a name="output-properties"></a>出力プロパティ

| プロパティ名 | データの種類 | 必要な領域 | 内容 |
| --- | --- | --- | --- |
| tileValue |数値 |No |アラートがトリガーされたときのタイルの値 |
| tileUrl |string |No |アラートがあるタイルの URL |
| alertTitle |string |No |アラートの名前 |
| isAlertTriggered |boolean |No |アラートが現在トリガーされているかどうか |
| alertThreshold |数値 |No |アラームがトリガーされるしきい値 |

## <a name="helpful-links"></a>便利なリンク
[使用可能な接続](../connections-list.md) をすべて参照してください。  
アプリに [接続を追加する](../add-manage-connections.md) 方法についてご確認ください。

