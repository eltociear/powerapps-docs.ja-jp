---
title: PowerApps でモデル駆動型アプリのフォームに順序を割り当てる | MicrosoftDocs
description: アプリで既定のフォームを割り当てる方法を学習する
ms.custom: ''
ms.date: 03/07/2019
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
ms.assetid: 914c5694-9c80-4424-be89-9f63256b4811
caps.latest.revision: 33
ms.author: matp
manager: kvivek
tags: ''
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 90190dc9021d3852d123dd63e678c7924e164838
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "2700876"
---
# <a name="assign-model-driven-app-form-order"></a>モデル駆動型アプリの順序の割り当て

 エンティティに対して、複数のメイン フォーム、簡易作成フォーム、簡易表示フォーム、またはカード フォームが存在する場合、フォームの順序を割り当てることができます。 フォームの順序によって、使用可能なフォームの中でどれが既定で表示されるかが決まります。 使用可能なメイン フォームは、そのフォームにセキュリティ ロールを割り当てることによってさらに制御できます。 詳細については、「[フォームへのアクセスを制御する](control-access-forms.md)」を参照してください。  
  
 簡易作成フォーム、簡易表示フォーム、カード フォームにはセキュリティ ロールを割り当てることはできません。したがって、すべてのユーザーによって使用される唯一のフォームは、フォームの順序の最上部のフォームです。  
  
## <a name="to-assign-a-form-order"></a>フォームの順序を割り当てるには  
  
1.  [ソリューション エクスプローラー](advanced-navigation.md#solution-explorer)を開き、対象のエンティティを展開し、**フォーム**を選択します。  
  
2.  フォームの一覧で、**フォームの順序**を選択します。  

     > [!div class="mx-imgBorder"] 
     > ![フォームの順序ツール バー コマンド](media/form-order.png)
  
3.  作業するフォームの種類に基づいて、**メイン フォーム セット**、**簡易作成フォーム セット**、**簡易表示フォーム セット**、または **カード フォーム セット** のいずれかを選択します。 詳細情報: [フォームの種類](types-forms.md)。 
  
4.  **フォームの順序**ダイアログは、選択したフォームの順序を上下に移動できる単純な一覧です。  
  
5.  順序の設定が完了したら、**OK** をクリックしてダイアログを閉じます。  

## <a name="next-steps"></a>次のステップ

[フォーム内でのナビゲーションの変更](use-the-form-editor-legacy.md)
