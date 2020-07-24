---
title: データがレポートに表示されない問題のトラブルシューティング | Microsoft Docs
description: データがレポートに表示されない問題のトラブルシューティング
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 06/27/2019
ms.author: mkaur
ms.custom: ''
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 1156aa8fb5fbc3ae51c21b8aa41606df6dbc2e86
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "3302405"
---
# <a name="troubleshoot-problems-with-data-not-displaying-in-a-report"></a>データがレポートに表示されない問題のトラブルシューティング

レポートに予期するデータが表示されない場合、いくつかの原因が考えられます。  
  
- **セキュリティのアクセス許可が十分ではありません**。 Common Data Service でレコードを表示する権限がない場合、レコードはレポートに表示されません。  
  
- **データが入力されていません。** データの入力者がフィールドを空のままにした可能性があります。  
  
- **データがレポートの条件と一致していない** 多くのレポートには、アクティブなレコードのみを表示する規定のフィルターが含まれています。または、一致するレコードがない条件を選択した可能性があります。 レポート フィルターを変更してみてください。 詳細については、「[レポートの既定のフィルターの編集](edit-report-filter.md)」を参照してください。  
  
- **レポートのキャッシュされたコピーを表示している。** 既定では、Common Data Service レポートのデータは、レポートを実行するたびにデータベースから取得されます。 ただし、システム管理者がレポートをキャッシュから実行するように変更している場合があります。 最近入力したデータがレポートに表示されない場合は、キャッシュからの古いバージョンのレポートが表示されている可能性があります。 レポートを更新するには、[レポート] ツールバーで、**[更新]** ボタンを選択します。  
  
- **サブレポート内のレコードを読み取るアクセス許可がない。** サブレポートに含まれるレコードの種類を読み取るアクセス許可がない場合は、サブレポートを表示できないという内容のエラー メッセージが表示されます。  
  
- **Microsoft Internet Explorer のプライバシーの設定により、必要な Cookie がブロックされている。** グラフ レポートで、グラフの代わりに赤い X の文字が表示される場合は、グラフ コントロールに必要な Cookie がプライバシーの設定によってブロックされている可能性があります。 この問題を解決するには、ブラウザーで、Reporting Services を実行しているサーバーの Cookie を有効にします。  
  

### <a name="see-also"></a>関連項目
[レポートを操作する](work-with-reports.md) 

[レポート ウィザードを使用してレポートを作成する](create-report-with-wizard.md)

[既存のレポートを追加する](add-existing-report.md)

[レポート フィルターを編集する](edit-report-filter.md)

