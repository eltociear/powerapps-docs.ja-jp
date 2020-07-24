---
title: レポートの操作 | Microsoft Docs
description: Power Apps でレポートを操作する
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
ms.openlocfilehash: c16a589ddcd1e7beb0be1ce28bc9f6df6a8c8b83
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/13/2020
ms.locfileid: "3303371"
---
# <a name="work-with-reports"></a>レポートを操作する

レポートは自分の業績を確認する上で役立ち、事業目標に向けた進捗状況を監視する目的で役立ちます。 また、傾向を追跡できます。傾向を追跡することで、競合他社より有利になります。  

レポートの整理と作成の詳細については、[レポートのカスタマイズおよび整理](https://docs.microsoft.com/powerapps/maker/model-driven-apps/add-reporting-to-app) を参照してください。
  
## <a name="run-a-report"></a>レポートを実行する  
  
1. 左側のナビゲーション ペインで、レポートの領域を選択します。 
2. 必要なレポート > **レポートの実行** を選択します。  
  
   > [!NOTE]
   >  **レポート ビューア**ダイアログ ボックスで、検索条件をそのままにするか、または必要に応じて変更できます。  
   
   > [!div class="mx-imgBorder"]
   > ![レポートの実行](media/report-run.png "レポートを実行する")
 
  
## <a name="share-a-report-with-other-users-or-teams"></a>他のユーザーまたはチームとレポートを共有する    

1. 左側のナビゲーション ペインで、レポートの領域を選択します。  
2. レポートの一覧で、共有するレポートを選択します。  
3. コマンド バーで **[共有]** を選択します。

   > [!div class="mx-imgBorder"]
   > ![レポートを共有する](media/report-share.png "レポートを共有する")
  
4. **[レポートの共有]** ダイアログ ボックスで、**[ユーザーまたはチームの追加]** を選択します。    
5. **[レコードの検索]** ダイアログ ボックスで、レポートを共有するユーザーまたはチーム レコードを見つけ、レコードの横にあるチェック ボックスを選択します。

   > [!div class="mx-imgBorder"]
   > ![レポートを共有するユーザーを選択する](media/report-share1.png "レポートを共有するユーザーを選択する")

6. **[選択]** を選択して **[選択したレコード]** ボックスにユーザーまたはチーム レコードを追加し、**[追加]** を選択します。

   > [!div class="mx-imgBorder"]
   > ![レポートを共有するユーザーを追加する](media/report-share2.png "レポートを共有するユーザーを追加する")
  
7. **レポートの共有**ダイアログ ボックスで、目的の共有アクセスの種類を選択します。 使用可能なアクセス許可は、[読み取り]、[書き込み]、[削除]、[追加]、[割り当て]、または [共有] です。 これでユーザーまたはチーム レコードが **[選択したレコード]** ボックスに追加されます。

   > [!div class="mx-imgBorder"]
   > ![共有アクセスの選択](media/report-share3.png "共有アクセスを選択する")
  

## <a name="share-a-report-with-your-organization-for-admins"></a>組織とレポートを共有する (管理者向け)
 レポートが全ユーザーにとって役に立つ場合、組織で利用できるようにします。  

1. 左側のナビゲーション ペインで、レポートの領域を選択します。  
2. レポートの一覧で、共有するレポートを選択します。  
3. コマンド バーで、**編集**を選択します。  
4. **[アクション]** メニューで **[レポートを組織で使用可能にする]** を選択します。  
  
   > [!div class="mx-imgBorder"]
   > ![組織とレポートを共有する](media/report-share4.png "組織とレポートを共有する")

## <a name="download-a-report"></a>レポートのダウンロード

1. 左側のナビゲーション ペインで、レポートの領域を選択します。 
2. レポートの一覧で、共有するレポートを選択します。  
3. コマンド バーで、**編集**を選択します。  
4. **[操作]** メニューの **[レポートのダウンロード]** をクリックします。  
RDL ファイルには、レポートの基になっている fetchXML が含まれています。
5. ダウンロードが完了したら、レポートを開きます。





### <a name="see-also"></a>関連項目

[レポート ウィザードを使用してレポートを作成する](create-report-with-wizard.md)

[既存のレポートを追加する](add-existing-report.md)

[レポート フィルターを編集する](edit-report-filter.md)

[レポートに表示されていないデータに関する問題のトラブルシューティング](troubleshoot-reports.md)


