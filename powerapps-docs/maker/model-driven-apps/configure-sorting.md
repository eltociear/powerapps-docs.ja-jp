---
title: Power Apps のモデル駆動型アプリ ビューでレコードを並び替える | MicrosoftDocs
ms.custom: ''
ms.date: 04/17/2020
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
ms.assetid: 25f5aa52-56dc-4be5-884e-9346616f665f
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: a89a2c4953f5a78a58ff6717f15a803a7cf58527
ms.sourcegitcommit: 3c6c5594b73abd5ff438d50f3b579d56cef7241c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2020
ms.locfileid: "3285657"
---
# <a name="sort-records-in-a-model-driven-app-view"></a>モデル駆動型アプリ ビューでレコードを並び替える


ビューを作成または編集するとき、昇順または降順の並べ替え順を構成できます。

ビュー デザイナーで並べ替え順を変更するには、[Power Apps でパブリック ビューを作成する](create-edit-views-app-designer.md#create-a-public-view-in-power-apps) を参照してください。

## <a name="change-the-sort-order-using-solution-explorer"></a>ソリューション エクスプローラーを使用して、並べ替え順を変更

1.  [ソリューション エクスプローラー](advanced-navigation.md#solution-explorer) を開いて、**エンティティ**を展開し、目的のエンティティを選択してから、**ビュー**を選択して表示したいビューを開きます。

2.  ビュー デザイナーで **並べ替えの構成** を選択します。  

    > [!div class="mx-imgBorder"] 
    > ![並べ替えを構成する](media/configure-sorting.png "並べ替えを構成する")
  
3.  **並べ替え順の構成**ダイアログ ボックスの**並べ替えの基準**の一覧で、並べ替える列を選択し、**昇順**または**降順**を選択します。  
  
4.  **OK** を選択して、**並べ替え順の構成**ダイアログ ボックスを閉じます。 

    > [!IMPORTANT]
    > 統一インターフェイス アプリのグリッドは、ビューの基になる FetchXML から表示された列のリストを取得します。 Common Data Service から返された FetchXML に列がない場合、その列は表示されません。 これは、列が FetchXML に存在せず、LayoutXM Lに存在する従来の Web アプリケーションとは対照的です。そのような列は、表示される列のリストに自動的に追加されます。 統一インターフェイス アプリは、OData を FetchXML で直接使用して、サーバーからデータを取得します。

## <a name="next-steps"></a>次のステップ
[ビューを作成または編集する](create-edit-views.md)
[FetchXML を使用し、データをクエリする](../../developer/common-data-service/use-fetchxml-construct-query.md)
