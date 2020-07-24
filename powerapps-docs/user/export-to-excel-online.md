---
title: モデル駆動型アプリで Excel Online にデータをエクスポートする |MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 11/16/2018
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
- D365CE
ms.openlocfilehash: 6cb8fe650db464f41c63af87c3fcb34bb2203cf2
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "3302451"
---
# <a name="export-your-data-to-excel-online"></a>Excel Online にデータをエクスポートする 

アプリから Excel Online にデータをエクスポートすることによって、アプリ内のデータのアドホック分析を迅速に実行できます。
  
Excel Online でデータを変更したら、更新された情報をアプリに保存できます。 インポート中の問題を回避するために、必ず Excel のセルの既存の形式を保持してください。 グラフ、チャート、色など、スプレッドシートに追加された情報は保存されません。  
  
## <a name="prerequisites"></a>前提条件  
  
- この機能を使うには、 Office 365 のサブスクリプション、または SharePoint Online または Exchange Online などのオンライン サービスに対するサブスクリプションが必要です。
  
- Microsoft のアカウントが必要となります。    
  
## <a name="open-app-data-in-excel-online"></a>Excel Online でアプリ データを開く  

Excel Online でデータを開くオプションは、すべてのレコードの種類で使用できるわけではありません。 オプションが表示されない場合、これはそのレコードに対して使用できません。  
  
> [!NOTE]
> Excel Online で過去 2 分間に同じビューを開いた場合、アプリ内の更新されたデータはすぐには Excel Online に反映されません。 その時間が過ぎた後、更新されたデータが Excel Online で表示されます。
  
アプリ内のレコードの一覧を開くには、コマンド バーで **[Excel にエクスポート]** メニューを選択し、**[Excel Online で開く]** を選択します。 

> [!div class="mx-imgBorder"] 
> ![Excel Online にエクスポート](media/exportexcelonline.png "Excel Online にエクスポート")  

  
## <a name="save-your-data-and-import-it-back-to-the-app"></a>データを保存してアプリにインポートし直す  
  
1. 変更が完了したら、**[保存]** を選択します。  
  
   > [!NOTE]
   > - Excel Online での "*アドホック*" 分析のためのデータは、一時的に保存されます。 グラフ、計算、列などの追加は、Excel Online でのアドホック分析からアプリに保存し直されません。  
   > 
   > - 多数の変更を行った場合、ファイルのインポートが失敗する可能性があります。 データに大量の変更を加えてからアプリにインポートし直す必要がある場合は、代わりに Excel でワークシートをエクスポートすることをお勧めします。  
   > 
   > - 仕様により、Excel Online で **[ファイル]** > **[名前を付けて保存]** を行うことはできません。 これを行うと、**ワークブックを保存できません**というエラー メッセージが表示されます。   
2. **[インポート用にデータが送信されました]** ダイアログ ボックスで、**[閉じる]** を選択します。  
  

  

 
