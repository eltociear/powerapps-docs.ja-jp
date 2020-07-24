---
title: モデル駆動型アプリでアカウントまたは連絡先を有効または無効にする | MicrosoftDocs
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
ms.openlocfilehash: 2a0474b17f62e30ec41cf04001f774a42ee2e849
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3302911"
---
# <a name="deactivate-or-activate-an-account-or-contact"></a>取引先企業または取引先担当者の非アクティブ化またはアクティブ化

モデル駆動型アプリでは、アカウントまたは連絡先を削除せず、無効にすることができます。 それにより、そのレコードに関連付けられている監査証跡の本来の姿が保たれます。  
  
無効にしたアカウントまたは連絡先は活動を停止します。つまり、編集したり、他のレコードに関連付けたりできません。 ただし、無効になっている項目で作成された関係はすべて、引き続き利用できます。  
  
無効にしたアカウントを後で再び有効にする必要が生じた場合、簡単に有効にできます。   
  
## <a name="deactivate-an-account-or-contact"></a>アカウントまたは連絡先を無効にする 
  
1.  左のメニューから、**[アカウント]** または **[連絡先]** に進みます。  
  
2.  無効にするアクティブなアカウントまたは連絡先を選択し、コマンド バーで **[非アクティブ化]** を選択し、非アクティブ化を確定します。

    > [!div class="mx-imgBorder"]
    > ![Power Appsでアカウントを無効にする](media/DeactiveAccounts.png "Power Appsでアカウントを無効にする")


## <a name="activate-an-account-or-contact"></a>アカウントまたは連絡先を有効にする  
  
1.  左のメニューから、**[アカウント]** または **[連絡先]** に進みます。 
  
2.  **[システム ビュー]** リストに進みます。

3.  **[非アクティブなアカウント]** または **[Inactive Contacts]\(非アクティブな連絡先\)** を選択します。  
  
4.  有効にする非アクティブなアカウントまたは連絡先を選択します。

5.  **[アクティブ化]** を選択し、アクティブ化を確定します。  

    > [!div class="mx-imgBorder"]
    > ![Power Appsでアカウントを有効にする](media/ActiveAccounts.png "Power Apps でアカウントを有効にする")  



