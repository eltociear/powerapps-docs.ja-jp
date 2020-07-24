---
title: Power Apps の外部からレポートを追加する | Microsoft Docs
description: Power Apps の外部からレポートを追加する
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
ms.openlocfilehash: e730d498a4d82518d0f908645e26a541c1e8c6af
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3302957"
---
# <a name="add-a-report-from-outside-power-apps"></a>Power Apps の外部からレポートを追加する

システムの外でカスタム レポートを作成した場合、それを Power Apps に簡単に追加できます。

カスタム レポートを作成する方法の詳細については、[レポートと分析に関するガイド](https://docs.microsoft.com/dynamics365/customer-engagement/analytics/get-started-writing-reports)を参照してください。

1. 左側のナビゲーション ペインで、レポートの領域を選択します。 
2. コマンド バーで、**[新規]** を選択します。
  
   **別のアプリケーションで作成したファイルの追加**  
  
   1. **[ソース]** セクションの **[レポートの種類]** ボックスで、**[既存のファイル]** を選択します。  
   
     > [!div class="mx-imgBorder"]
     > ![既存のレポートを追加する](media/add_existing_report.png "既存のレポートを追加する")
  
   2. **ファイルの場所**ボックスに、追加するファイルのパスとファイル名を入力するか、**参照**を選択してファイルを選択します。 
   
      Excel ファイルなど、その他のさまざまな種類のファイルをアップロードできますが、SQL Server Reporting Services レポートや Report Wizard で作成したレポートのように実行するには、ファイルが .RDL ファイルになっている必要があります。 詳細については、 [SQL Server Data Tools を使用したレポート作成環境](https://docs.microsoft.com/dynamics365/customer-engagement/analytics/report-writing-environment-using-sql-server-data-tools) を参照してください。
  
      または  
  
   **Web ページへのリンクの追加**  
  
   1.  **ソース**セクションの**レポートの種類**ボックスで、**Web ページへのリンク**を選択します。  
  
   2.  **Web ページの URL** ボックスに、Web ページの URL を入力します。  
  
3. レポートのプロパティを指定します。
  
   1.  **詳細**セクションで、レポートに対して意味のある名前と説明を指定します。  
  
   2.  現在のレポートの親レポートが存在する場合は、**親レポート**テキスト ボックスにそれが表示されます。  
  
   3. **カテゴリ**。 **[このフィールドの値を選択または変更します]** ![省略記号ボタン](media/ellipsis-button.png "省略記号ボタン") ボタンを選択し、このレポートに含めるカテゴリを指定します。  
  
   4. **関連するレコードの種類**。 あるページの [レポート] リストにレコードの種類を指定した上でレポートを表示するには、**[このフィールドの値を選択または変更します]** ![省略記号ボタン](media/ellipsis-button.png "省略記号ボタン") ボタンを選択し、レコードの種類を選択します。  
  
   5. **表示形式**。 レポートを表示する場所を指定するには、**[このフィールドの値を選択または変更します]** ![省略記号ボタン](media/ellipsis-button.png "省略記号ボタン") ボタンを選択し、オプションを 1 つまたは複数選択します。  
  
        値が選択されていない場合、エンド ユーザーにはレポートが表示されません。  
  
4. **保存**または**保存して閉じる**を選択します。  




### <a name="see-also"></a>関連項目
[レポートを操作する](work-with-reports.md) 

[レポート ウィザードを使用してレポートを作成する](create-report-with-wizard.md)

[レポート フィルターを編集する](edit-report-filter.md)

[レポートにデータが表示されない問題を解決する](troubleshoot-reports.md)
