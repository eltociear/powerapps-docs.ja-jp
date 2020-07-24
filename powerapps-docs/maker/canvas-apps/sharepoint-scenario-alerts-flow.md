---
title: Power BI ダッシュボードのデータ アラートを設定する | Microsoft Docs
description: このタスクでは、保留中のプロジェクトの承認に時間がかかりすぎる場合に通知するアラート、およびアラート発生時に対応するフローを Power BI に追加します。
author: NickWaggoner
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 06/12/2017
ms.author: niwaggon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 37ea7a123562cf4ec9216d484bd6173f33046d72
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2019
ms.locfileid: "3304222"
---
# <a name="set-up-data-alerts-for-the-power-bi-dashboard"></a>Power BI ダッシュボードのデータ アラートを設定する
> [!NOTE]
> この記事は、Power Apps、Power Automate、および Power BI と SharePoint Online の使用に関するチュートリアル シリーズの一部です。 シリーズ全般に関することや、関連するファイルのダウンロードの詳細について、[シリーズの概要](sharepoint-scenario-intro.md) を必ずご覧ください。

このタスクでは、保留中のプロジェクトの承認に時間がかかりすぎる場合に通知するアラート、およびアラート発生時に対応するフローを Power BI に追加します。 アラートの詳細は、[Power BI サービスのデータ アラート](https://docs.microsoft.com/power-bi/service-set-data-alerts) 参照してください。

## <a name="step-1-create-an-alert"></a>手順 1: アラートを作成する
1. Power BI サービスで、前回のタスクで作成したダッシュボードを開きます。
2. 1 つの数値が表示されたカードで、省略記号 (**. . .**) をクリックまたはタップします。
   
    ![承認待ちの最大日数が表示されたカード](./media/sharepoint-scenario-alerts-flow/07-01-01-tile-ellipsis.png)
3. チェックマーク アイコンを ![ベル アイコン](./media/sharepoint-scenario-alerts-flow/icon-bell.png)。
   
    ![タイル メニュー](./media/sharepoint-scenario-alerts-flow/07-01-02-tile-bell.png)
4. 右側のウィンドウで、**アラート ルールの追加**をクリックまたはタップします。
   
    ![アラート ルールの追加](./media/sharepoint-scenario-alerts-flow/07-01-03-add-alert.png)
5. アラートを実行する頻度などの、アラートで使用可能なオプションを確認します。 **しきい値**に 25 の値を入力し、**保存して閉じる**をクリックまたはタップします。
   
    ![アラートのしきい値を設定して保存](./media/sharepoint-scenario-alerts-flow/07-01-04-save-alert.png)

56 は 25 のしきい値を超えていますが、アラートがすぐに発生するわけではありません。 データが更新されるとアラートが発生しますが、これは[シナリオ全体をおさらい](sharepoint-scenario-summary.md) を行うときに確認できます。

アラートが発生すると Power BI がアラートの作成者にメールを送信します。次の手順では、Power Automate を使用して追加のメールを送信する方法を説明します。

## <a name="step-2-create-a-flow-that-responds-to-the-alert"></a>手順 2: アラートに対応するフローを作成する
1. flow.microsoft.com にサイン インし、**サービス**、**Power BI** の順にクリックまたはタップします。
   
    ![Power AutomateのPower BI](./media/sharepoint-scenario-alerts-flow/07-01-05-power-bi.png)
2. **Power BI データのアラートがトリガーされたら、対象ユーザーにメールを送る**をクリックまたはタップします。
   
    ![Power BI データ アラートがトリガーされたときに電子メールを送信](./media/sharepoint-scenario-alerts-flow/07-01-06-alert-flow.png)
3. **このテンプレートを使用**をクリックまたはタップします。
4. サインインをまだ行っていない場合、Outlook および Power BI にサインインし、**続行**をクリックまたはタップします。
   
    ![サイン インして続行](./media/sharepoint-scenario-alerts-flow/07-01-08-continue.png)
5. **アラート ID** のドロップダウン リストで、**承認待ちの最大日数のアラート**を選択します。
   
    ![指定とトリガーとしてのアラート](./media/sharepoint-scenario-alerts-flow/07-01-09-choose-alert.png)
6. **宛先**ボックスに、有効な電子メール アドレスを入力します。
   
    ![電子メールの送信先を指定](./media/sharepoint-scenario-alerts-flow/07-01-10-choose-email.png)
7. **編集**をクリックまたはタップして、更新できるその他のフィールドを表示します。
   
    ![アラート メールの編集](./media/sharepoint-scenario-alerts-flow/07-01-11-email-full.png)
8. 画面の右上で、**フローの作成**、**完了**の順にクリックします。
   
    ![完了ボタン](./media/sharepoint-scenario-alerts-flow/07-01-12-done.png)

[シナリオ全体をおさらいする](sharepoint-scenario-summary.md) ときに、このフローが実行されます。 今度は、このシナリオの最後のタスクである、SharePoint への Power BI レポートの埋め込みに進みます。

## <a name="next-steps"></a>次の手順
チュートリアル シリーズの次の手順で、[SharePoint Online に Power BI プロジェクト レポートを埋め込みます](sharepoint-scenario-embed-report.md)。

