---
title: アクセス チームを使ってレコードを共有する | Microsoft Docs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 12/11/2018
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 7dd418db04f72310210925345611bc1a0b2a6f17
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "3302543"
---
# <a name="share-records-using-access-team"></a>アクセス チームを使ってレコードを共有する

アクセス チームは、共有レコードを介してレコードへのアクセス権を付与します。 アクセス チーム メンバーは、個々のセキュリティ ロールとメンバーであるチームのロールに定義されている特権を持ちます。 

> [!NOTE]
> アクセス チームを使用してレコードを共有する前に、管理者はアクセス チーム テンプレートを設定する必要があります。 詳細については、[チーム テンプレート](https://docs.microsoft.com/previous-versions/dynamicscrm-2016/admins-customizers-dynamics-365/mt812239(v%3dcrm.8))に関するページを参照してください。 

1. レコードへのアクセス許可をユーザーに付与するには、サイト マップからレコードの種類を選択します。 たとえば、**[アカウント]** です。
2. レコードの一覧から、他のユーザーにアクセス権を付与するレコードを開きます。

  > [!div class="mx-imgBorder"]
  > ![自分のアクティブなアカウント](media/AccessTeam1.png "自分のアクティブなアカウント")

3. **[Access Team Members]\(チーム メンバーへのアクセス\)** セクションで **[その他のコマンド]** (**[...]**) > **[ユーザーの追加]** の順に選択します。

  > [!div class="mx-imgBorder"]
  > ![ユーザーをアクセス チームに追加する](media/AccessTeam2.png "ユーザーをアクセス チームに追加する")

 4. 検索ボックスにユーザー名を入力してユーザーを検索し、**[追加]** を選択します。
  
  > [!div class="mx-imgBorder"]
  > ![ユーザーを検索する](media/AccessTeam3.png "ユーザーを検索する")  
  
 
## <a name="remove-a-user-from-access-teams"></a>アクセス チームからユーザーを削除する

 レコードに対するユーザーのアクセス権は、追加したときと同様に、簡単に削除できます。
 
1.  ユーザーを削除するレコードを開きます。
2.  **[Access Team Members]\(チーム メンバーへのアクセス\)** サブグリッドで、**[ユーザーの削除]** を選択します。

  > [!div class="mx-imgBorder"]
  > ![ユーザーをアクセス チームから削除する](media/AccessTeam4.png "ユーザーをアクセス チームから削除する")  
  
  
