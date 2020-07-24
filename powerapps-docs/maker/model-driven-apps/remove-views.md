---
title: Power Apps 内でのモデル駆動型アプリ ビューの削除または非アクティブ化 | MicrosoftDocs
description: ビューを削除または非アクティブ化する方法を説明します。
ms.custom: ''
ms.date: 03/30/2020
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
ms.assetid: 60865f78-7482-42da-8960-adbd3c155028
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4c0eea329561fdf35646a04d50ac1b01915ff52b
ms.sourcegitcommit: 3c6c5594b73abd5ff438d50f3b579d56cef7241c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2020
ms.locfileid: "3285764"
---
# <a name="delete-or-deactivate-a-model-driven-app-view"></a>モデル駆動型アプリのビューの削除または非アクティブ化 

<a name="BKMK_RemoveViews"></a>   

 人に見せたくないビューがあるかもしれません。 ビューの種類に基づいて、ビューを削除または非アクティブにすることができます。 ビューを完全に削除したくない場合は、削除する代わりに、それを非アクティブ化できます。
 
  * ユーザー定義の共有ビューはいずれも削除できます。 実際に削除することを確認すると、ビューは完全に削除されます。

  * システムが作成した共有ビューを含めて、どの[システム ビュー](create-edit-views.md#system-views)も削除または非アクティブ化することはできません。 システムが作成した共有ビューを含めて、どの共有ビューも非アクティブ化することはできます。

## <a name="delete-a-view"></a>ビューの削除

1.  [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインします。  

2.  **データ**を展開して**エンティティ**を選択し、目的のエンティティを選択してから**ビュー** タブを選択します。

3.  目的のビューの横にある**他のコマンド** ![他のコマンド ボタン](media/more-commands.gif "フォームの その他のコマンド ボタン") を選択してから、**ビューの削除**を選択します。 メニュー バーで、**ビューの削除**を選択することもできます。

## <a name="deactivate-or-activate-views"></a>ビューの非アクティブ化またはアクティブ化  

1.  [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインします。  

2.  **データ**を展開して**エンティティ**を選択し、目的のエンティティを選択してから**ビュー** タブを選択します。

3.  目的のビューの横にある**他のコマンド** ![他のコマンド ボタン](media/more-commands.gif "フォームの その他のコマンド ボタン") を選択してから、**非アクティブ化**または**アクティブ化**のいずれかを選択します。 メニュー バーで、**非アクティブ化**または**アクティブ化**を選択することもできます。

## <a name="delete-a-view-in-solution-explorer"></a>ソリューション エクスプローラーでビューを削除  

ユーザー定義の共有ビューはいずれも削除できます。 [ビュー定義へのアクセス](accessing-view-definitions.md#open-a-view-for-editing-in-solution-explorer) のステップを使用して、削除するビューを見つけ、![削除ボタン](media/delete.gif "[削除] ボタン")**削除**コマンドを使用します。 実際に削除することを確認すると、ビューは完全に削除されます。  
  
## <a name="deactivate-or-activate-views-in-solution-explorer"></a>ソリューション エクスプローラーでのビューの非アクティブ化またはアクティブ化 

1.  「[ビュー定義へのアクセス](accessing-view-definitions.md#open-a-view-for-editing-in-solution-explorer)」に説明されているとおりに、**システム ビュー**に移動します。  
  
2.  共有ビューを選択します。 非アクティブなビューを表示するには、**非アクティブな共有ビュー**ビューを使用します。  
  
3.  メニュー バーで、**他の操作**を選択してから、**非アクティブ化**または**アクティブ化**を選択します。  
  
4.  **すべてのカスタマイズの公開**を選択します。 

## <a name="next-steps"></a>次のステップ
[ビューの作成または編集](create-and-edit-views.md)
