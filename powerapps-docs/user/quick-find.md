---
title: 簡易検索 | MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 1/28/2020
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 42691193a90d56f773de5723c4c27e883b3216ad
ms.sourcegitcommit: 303d5aed44f2bbb406cabeb6b9c8474d738d9114
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2020
ms.locfileid: "3303095"
---
# <a name="using-quick-find-to-search-for-records"></a>簡易検索を使用してレコードを検索する

## <a name="single-entity-quick-find"></a>単一エンティティの簡易検索

単一エンティティの簡易検索は、1 種類のレコードのみを検索するために使用されます。 この検索オプションは、ビュー内から使用できます。 

   > [!div class="mx-imgBorder"]
   > ![単一エンティティの簡易検索](media/single-quick-find-search-box.png "単一エンティティの簡易検索の検索ボックス") 

## <a name="multiple-entity-quick-find-categorized-search"></a>複数エンティティの簡易検索 (カテゴリ別検索)

複数エンティティの簡易検索は、カテゴリ別検索とも呼ばれます。 

1.  カテゴリ別検索を開始するには、上部のナビゲーション バーで **[検索]** を選択します。  

     > [!div class="mx-imgBorder"]
     > ![[グローバル検索] ボタン](media/global-search-button.png "グローバル検索")
  
2.  検索ボックスに検索語を入力し、**[検索]** を選択します。 カテゴリ別検索では、結果がエンティティの種類別 (アカウントや連絡先など) にグループ化されて返されます。

     > [!div class="mx-imgBorder"]
     > ![カテゴリ別検索結果](media/categorized-search-results.png "カテゴリ別検索結果ページ") 

カテゴリ別検索では、特定の単語で始まるレコードを検索したり、ワイルドカード文字を使用したりできます。
  
- **次の値で始まる**: 結果には特定の単語で始まるレコードが含まれます。 たとえば、"Alpine Ski House" を検索する場合、検索ボックスに「**alp**」と入力します。「**ski**」を入力すると、そのレコードは表示されません。  
  
- **ワイルドカード**: 例、*ski または*ski\*。 

  > [!NOTE]
  >  (単一エンティティまたは複数エンティティの) 簡易検索の検索クエリの先頭でワイルドカードを使用すると、パフォーマンスが低下する可能性があります。
  
## <a name="filter-categorized-search-results"></a>カテゴリ別検索結果のフィルター処理 
  
-   レコードの種類によって結果をフィルター処理するには、**[フィルター]** リストからレコードの種類を選択します。 

    > [!div class="mx-imgBorder"]
    > ![カテゴリ別検索結果のフィルター処理](media/filter-categorized-search-results.png "カテゴリ別検索結果のフィルター処理")  

  
-   すべてのレコードの種類を検索するには、**[フィルター]** リストから **[なし]** を選択します。  
