---
title: 'サンプル: ユーザー定義ワークフロー活動を使用した次回の誕生日の更新(Common Data Service) | Microsoft Docs'
description: 'サンプル ワークフロー活動は次回の誕生日を返します。 顧客に誕生日の挨拶を送信するワークフローでこれを使用します。 '
ms.custom: ''
ms.date: 1/28/2020
ms.reviewer: pehecke
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: samples
applies_to:
- Dynamics 365 (online)
ms.assetid: 1cff83b0-1f7b-4ddb-a2af-b85f9f785529
caps.latest.revision: 21
author: JimDaly
ms.author: jdaly
manager: KumarVivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: b419800c6a556c61a8b9bf1ea0344e6798ea6e79
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2020
ms.locfileid: "3154931"
---
# <a name="sample-update-next-birthday-using-a-custom-workflow-activity"></a>サンプル: ユーザー定義ワークフロー活動を使用した次回の誕生日の更新

[WorkflowActivities](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/WorkflowActivities) からサンプル全体をダウンロードします。

## <a name="prerequisites"></a>前提条件

[!INCLUDE [sdk-prerequisite](../../../includes/sdk-prerequisite.md)]
  
## <a name="requirements"></a>要件 
 
このユーザー定義のワークフロー活動が機能するためには、次のカスタム フィールドが存在している必要があります。  
  
-   `Contact`.`new_nextbirthday`  
  
## <a name="demonstrates"></a>説明  
 次のサンプル ワークフロー活動は次回の誕生日を返します。 顧客に誕生日の挨拶を送信するワークフローでこれを使用します。  
  
## <a name="example"></a>例  

[NextBirthday.cs](https://github.com/microsoft/PowerApps-Samples/blob/master/cds/orgsvc/C%23/WorkflowActivities/WorkflowActivities/NextBirthday.cs)
  
### <a name="see-also"></a>関連項目

[ワークフローの拡張機能](workflow-extensions.md)<br />
[チュートリアル: ワークフロー拡張の作成](tutorial-create-workflow-extension.md)<br />
[サンプル: カスタム ワークフロー活動の作成](sample-create-custom-workflow-activity.md)<br />
[サンプル: ユーザー定義ワークフロー活動でクレジット スコアを計算する](sample-calculate-credit-score-custom-workflow-activity.md)
