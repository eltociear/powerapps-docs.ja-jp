---
title: レポート ウィザードを使用してレポートを作成する | Microsoft Docs
description: Power Apps でレポート ウィザードを使用してレポートを作成する
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
ms.openlocfilehash: 8c7bde8d3aa5406a7ddcc5ecb2df4c2c7db7051e
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3302934"
---
# <a name="create-a-report-using-the-report-wizard"></a>レポート ウィザードを使用してレポートを作成する


レポート ウィザードを使用すると、ご自分のデータを容易に分析できるグラフやテーブルを使用してレポートを作成することができます。 

レポート ウィザードを使用して作成したすべてのレポートは、フェッチベースのレポートです。 レポート ウィザードで生成されたレポートはすべて、横向きモードで出力されることに注意してください。

## <a name="create-a-new-report"></a>新しいレポートの作成

1. 左側のナビゲーション ペインで、レポートの領域を選択します。  
2. コマンド バーで、**[新規]** を選択します。

    > [!div class="mx-imgBorder"]
    > ![新しいレポートの作成](media/newreport.png "新しいレポートの作成")
  
3. **[レポート: 新しいレポート]** 画面が表示されます。 **[レポートの種類]** では、既定の選択である **[Report Wizard Report]\(レポート ウィザード レポート\)** をそのままにして、**[レポート ウィザード]** ボタンを選択します。 

    > [!div class="mx-imgBorder"]
    > ![レポート ウィザード](media/report_wizard.png "[レポート ウィザード] 画面")
  
4. 次の画面では、既定の選択をそのままにして、**[次へ]** を選択します。
 
    > [!div class="mx-imgBorder"]
    > ![レポート ウィザード](media/report_wizard_1.png "[レポート ウィザード] 画面")
   
4. **[レポートのプロパティ]** 画面で、レポートの名前を入力してから、レポートに含めるレコードを選択して、**[次へ]** を選択します。
 
    > [!div class="mx-imgBorder"]
    > ![[レポートのプロパティ] 画面](media/report_wizard_2.png "[レポートのプロパティ] 画面")
  
5.  **[レポートに含めるレコードの選択]** 画面で、レポートに含めるレコードを決定するためのフィルターを選択します。 たとえば、過去 60 日間に変更されたレコードの結果のみを表示する場合は、この画面でそのフィルターを設定できます。 データをフィルター処理しない場合は、**[クリア]** を選択します。

    > [!div class="mx-imgBorder"]
    > ![レポートに含めるレコードの選択*](media/report_wizard_3.png "レポートに含めるレコードの選択")
  
6. **[レイアウト フィールド]** 画面で、レポートのレイアウトを選択します。 **[グループを追加するときはここをクリックします]** を選択し、データをグループ化する方法を選択します。

    > [!div class="mx-imgBorder"]
    > ![レイアウト フィールド](media/report_wizard_4.png "[レイアウト フィールド]")

7. レポート内でグループ化するデータの **[レコードの種類]** と **[列]** を選択します。 選択が完了したら、**[OK]** を選択します。

    > [!div class="mx-imgBorder"]
    > ![[グループ化の追加]](media/report_wizard_5.png "[グループ化の追加] 画面") 画面
  
8. 前の手順で選択したレコードの種類に関連するデータの列に対して、**[列を追加するにはここをクリックします]** を選択します。  

    > [!div class="mx-imgBorder"]
    > ![[グループ化の追加] 画面](media/report_wizard_6.png "[グループ化の追加] 画面")

9. **[列の追加]** 画面で、列に表示させたいデータを選択し、**[OK]** を選択します。 

    > [!div class="mx-imgBorder"]
    > ![[列の追加] 画面](media/report_wizard_7.png "[列の追加] 画面")
  
10. 追加する列が他にもある場合は、前の手順を繰り返します。 完了したら、**[レイアウト フィールド]** 画面で、**[次へ]** を選択します。
 
    > [!div class="mx-imgBorder"]
    > ![さらに列を追加する画面](media/report_wizard_8.png "さらに列を追加する画面")
  
11. **[レポートの書式設定]** 画面で、レポートの書式を設定する方法を選択して、**[次へ]** を選択します。
 
    > [!div class="mx-imgBorder"]
    > ![レポートの書式設定](media/report_wizard_9.png "[レポートの書式設定] 画面")

12. レポートの概要を確認し、**[次へ]** を選択してから、**[完了]** を選択します。 これで、システムのレポートの一覧にこのレポートが表示されます。

    > [!div class="mx-imgBorder"]
    > ![レポートを表示する](media/report_wizard_10.png "レポートを表示する")

### <a name="see-also"></a>関連項目
[レポートを操作する](work-with-reports.md) 

[既存のレポートを追加する](add-existing-report.md)

[レポート フィルターを編集する](edit-report-filter.md)

[レポートに表示されていないデータに関する問題のトラブルシューティング](troubleshoot-reports.md)


