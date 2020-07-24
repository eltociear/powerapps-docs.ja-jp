---
title: モデル駆動型アプリでダッシュボードとグラフを使って進行状況を追跡する | MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 10/4/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
- D365CE
ms.openlocfilehash: 70c6f97c2617c9d6084c3aa8a0861793a0c059d5
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3302773"
---
# <a name="track-your-progress-with-dashboards-and-charts"></a>ダッシュボードとグラフを使って進行状況を追跡する

ダッシュボードでは、主要業績評価指標 (KPI) やその他の重要なデータを読みやすい対話型の図やグラフに表示するため、アプリ データのコレクションが取得され、分析情報が提供されます。 ダッシュボードはすべてのレコードの種類について使用できます。

> [!div class="mx-imgBorder"]
> ![ダッシュボード​​](media/Dashboard.png "ダッシュボード​​") 

-  別のダッシュボードのレイアウトを表示するには、ダッシュボードの名前の隣にある下向き矢印を選択して、対象のレイアウトを選択します。
-  既定のダッシュボードを選択するには、対象のダッシュボードを表示してから、画面の上部にある **[既定として設定​​]** を選択します。

   > [!div class="mx-imgBorder"]
   > ![ダッシュボードを追加または変更する](media/add_dashboard.png "ダッシュボードを追加または変更する") 

## <a name="create-a-new-dashboard"></a>新しいダッシュボードを作成します

1. 新しいダッシュボードを作成するには、**[Dynamics 365 ダッシュボードを作成します]** を選択します。 

   > [!div class="mx-imgBorder"]
   > ![新しいダッシュボードを追加する](media/new_dashboard.png "新しいダッシュボードを追加する")
   
2. ダッシュボードのレイアウトを選択し、**[作成]** を選択します。  

   > [!div class="mx-imgBorder"]
   > ![ダッシュボードを作成する](media/create_dashboard.png "ダッシュボードを作成する")
 
3. ダッシュボードの名前を入力します。 
4. ダッシュボードの各領域に表示させるものを追加します。 たとえば、グラフを追加します。 

   > [!div class="mx-imgBorder"]
   > ![グラフの追加](media/add_chart.png "グラフの追加")
 
 5. グラフの **[レコードの種類]** を選択します。
 6. グラフ内のデータが表示される **[ビュー]** を選択します。
 7. グラフを選択し、**[追加]** を選択します。
 8. ダッシュボードへのコンポーネントの追加を続け、完了したら **[保存]** をクリックします。 
 
作成したダッシュボードは、使用可能なダッシュボードのドロップダウン メニューに表示されます。

## <a name="use-charts"></a>グラフを使用する 

グラフを使用すると、目標をどのように追跡しているかを簡単に確認できます。 また、対話型であるため、グラフの領域をクリックまたはタップして詳細情報を表示できます。

-   グラフの上にマウス ポインターを置くと、グラフのその領域についての簡単な情報を示すツールヒントが表示されます。
-   グラフの領域をクリックすると、グラフ内のデータに関する詳細を含むグリッド ビューが表示されます。
-   グラフを展開するには、**[グラフの展開]**  ![グラフ ビューの展開](media/expandviewbutton.png "グラフ ビューの展開") ボタンを選択します。
-   グラフのレコードの表示、またはグラフの更新を行うには、![その他のコマンド](media/MoreButton.png "その他のコマンド") を選択してから、アクション: **最新の情報に更新** または **レコードの表示** を選択します。
     
     > [!div class="mx-imgBorder"]
     > ![Power Apps でのグラフの表示](media/ViewOfCharts.png "Power Apps でのグラフの表示")  
       

**グラフ ビューを変更する**
 
グラフ ビューを変更すると、特定の期間内にオープンされた営業案件など、データのさまざまな内訳が表示されます。 グラフ ビューを変更するには、[グリッド] ページで [ビュー] セレクターを選択します。

たとえば、[すべての営業案件] を選択してから別のビューを選択すると、グラフとグリッドの両方が最新の情報に更新されます。

> [!div class="mx-imgBorder"]
> ![Power Apps でグラフ ビューを変更する](media/ChangeChartView.png "Power Apps でグラフ ビューを変更する")

## <a name="known-issues"></a>既知の問題  
グラフ デザイナーでは、特定の計算フィールドに "並べ替え" を追加することはサポートされていないため、エラーが発生します。  この原因となった計算フィールドでは、別の計算フィールド、関連エンティティ フィールド、またはエンティティのローカル フィールドが使用されています。



