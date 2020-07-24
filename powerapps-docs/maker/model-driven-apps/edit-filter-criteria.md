---
title: Power Apps を使用してモデル駆動型アプリ ビューでフィルター条件を編集し、並べ替え順を変更する | MicrosoftDocs
description: ビューでフィルター条件を編集し、並べ替え順を変更する方法を説明する
ms.custom: ''
ms.date: 03/26/2020
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: fecf23c9-05e6-4397-9a5d-37210bcc2816
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: fd5541059b743115a56614671b72e5e00deabfd2
ms.sourcegitcommit: 3c6c5594b73abd5ff438d50f3b579d56cef7241c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2020
ms.locfileid: "3285569"
---
# <a name="edit-filter-criteria-and-change-sort-order-in-model-driven-app-views"></a>モデル駆動型アプリ ビューでフィルター条件を編集し、並べ替え順を変更する

<a name="BKMK_EditFilterCriteria"></a>   

ビューに表示される列ととも、ビューに適用されるフィルター条件は、ビューが提供する値の重要な要素です。 フィルター条件を追加または編集し、ビューに含める列の並べ替え順を変更できます。 ビューに並べ替え順が設定されていない場合、既定では、ビューはビューのプライマリ フィールドで昇順(A から Z) に並べ替えられます。

## <a name="change-the-sort-order-of-a-view"></a>ビューの並べ替え順の変更

1.  [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインします。  

2.  **データ**を展開して**エンティティ**を選択し、目的のエンティティを選択してから**ビュー** タブを選択します。

3.  ビューを選択して、ビュー デザイナーで開きます。

    > [!div class="mx-imgBorder"] 
    > ![フィルターの編集](media/view-column-menu.png "フィルターの編集")

4.  列見出しでフィールド名を選択し、列メニューから **A から Z に並べ替え**または **Z から A に並べ替え**を選択します。並べ替え順は、列見出しに上矢印または下矢印で示されます。

ビューのプロパティ パネルを使用して、並べ替え順を変更することもできます。 

1.  ビューに並べ替え順が設定されていない場合は、**並べ替え**を選択し、次に列によるプライマリの並べ替えを選択します。

2.  追加の列でビューを並べ替えする場合は、**次に並べ替え**を選択し、ビューの列で追加の並べ替えを選択します。

    1 つの列に同じ値でグループ化するデータがあり、同じ値のグループ内の別の列を並べ替える場合は、複数の列で並べ替えることができます。

3.  並べ替え式を削除するには、**並べ替え式を削除する**を選択します (**X** ボタン)。

## <a name="add-or-edit-filter"></a>フィルターの追加または編集

1.  列を選択し、列メニューから**フィルター**を選択します。

    > [!div class="mx-imgBorder"] 
    > ![フィルターの編集](media/edit-filter-criteria.png "フィルターの編集")

2.  使用する条件の演算子を選択します。

3.  条件の比較値を入力または選択します。

4.  **適用**を選択します。

    ビューのフィルター式は、ビューのプロパティ パネルに表示されます。
    
5.  フィルター式を編集するには、ビューのプロパティ パネルからフィルター選択式を選択します。

6.  フィルター式を削除するには、**X** ボタンを選択します。 

また、ビュー デザイナーの式ビルダーを使用して、現在のビューのエンティティのフィールドまたは関連エンティティのフィールドのフィルターを追加または編集することもできます。 詳細: [モデル駆動型アプリ ビューでフィルターを作成または編集する](create-edit-view-filters.md)

## <a name="use-solution-explorer-to-edit-filter-criteria-and-change-sort-order"></a>ソリューション エクスプローラーを使用してフィルターを編集、および並べ替え順を変更する

ビューの並べ替え順を変更します。

1.  [ソリューション エクスプローラー](advanced-navigation.md#solution-explorer) を開いて、**エンティティ**を展開し、目的のエンティティを選択してから、**ビュー**を選択して表示したいビューを開きます。

2.  ビュー デザイナーで **並べ替えの構成** を選択します。  

    > [!div class="mx-imgBorder"] 
    > ![並べ替えを構成する](media/configure-sorting.png "並べ替えを構成する")
  
3.  **並べ替え順の構成**ダイアログ ボックスの**並べ替えの基準**の一覧で、並べ替える列を選択し、**昇順**または**降順**を選択します。  
  
4.  **OK** を選択して並べ替え順を保存します。  

ビューのフィルター条件を変更します。

1.  ビュー デザイナーでビューを作成または編集する場合、**タスク** ウィンドウで**フィルター条件の編集**を選択します。  
  
2.  ダイアログに、**高度な検索**と同様のユーザー インターフェイスが表示されます。 フィルター句を選択した後、**Group AND** または **Group OR** を選択することにより、**AND** および **OR** 句を使用してグループ条件を指定できます。  

3.  **OK** を選択し、フィルター条件を保存します。  
  
フィルター句の構築の詳細については、「[高度な検索の作成、編集または保存](https://docs.microsoft.com/dynamics365/customer-engagement/basics/save-advanced-find-search)」を参照してください。   
 
## <a name="next-steps"></a>次のステップ
[ビューについて](create-edit-views.md)
