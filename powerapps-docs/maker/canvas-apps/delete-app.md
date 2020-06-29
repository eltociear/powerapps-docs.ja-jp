---
title: キャンバス アプリを削除する | Microsoft Docs
description: Power Apps から既存のキャンバス アプリを削除する方法
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/08/2020
ms.author: alaug
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 7cc275f50e5c972041e523c6e1118f53dffddccc
ms.sourcegitcommit: 3448869b74152e01a58f61c37d4361d8ae8bb09d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/09/2020
ms.locfileid: "3354022"
---
# <a name="delete-a-canvas-app-from-power-apps"></a>Power Apps からキャンバス アプリを削除する

この記事では、キャンバス アプリを削除する方法について説明します。

## <a name="delete-an-app-as-the-owner"></a>所有者としてアプリを削除する

1. [Power Apps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインします。

1. 左側のウィンドウから、**アプリ**を選択します。

    ![アプリ](./media/delete-app/file-apps.png)

1. (オプション) 右上隅の近くで、アプリのリストをフィルター処理して、所有しているアプリのみを表示します。

    ![アプリ フィルター](./media/delete-app/filter-list.png)

   > [!NOTE]
   > 削除するアプリが表示されない場合は、適切な環境にいることを確認してください。

1. アプリを選択します。

    ![アプリの選択](./media/delete-app/select-app.png)

1. トップ メニューから、**削除**を選択します。 **その他のコマンド** (**...**) を選択してから、代わりに**削除**を選択することもできます。

    ![削除を選択する](./media/delete-app/select-delete.png)

1. **クラウドから削除**を選択します。  

    ![クラウドから削除](./media/delete-app/delete-app.png)

    > [!IMPORTANT]
    > この操作を実行すると、自身のアカウントだけでなく、アプリを共有する全ユーザーのアカウントからも対象のアプリが削除されます。

## <a name="delete-an-app-as-the-administrator"></a>管理者としてアプリを削除する

アプリの所有者がいない場合、グローバル管理者、Azure Active Directory のグローバル管理者、または Dynamics 365 のサービス管理者などがアプリの所有者を設定できます。 そして、[新しい所有者はアプリを削除できます](#delete-an-app-as-the-owner)。

ユーザーをアプリの所有者として設定するには、[管理者向けの Power Apps コマンドレット](https://docs.microsoft.com/power-platform/admin/powerapps-powershell)を使用してください。

> [!TIP]
> アプリが[検出可能](https://docs.microsoft.com/power-platform/admin/powerapps-powershell#display-a-list-of-deleted-power-apps-in-an-environment)である限り、[管理者向け Power Apps コマンドレット](https://docs.microsoft.com/power-platform/admin/powerapps-powershell#recover-a-deleted-canvas-app)を使用して、削除したキャンバス アプリを復元することもできます。

### <a name="see-also"></a>関連項目

[アプリの共有](share-app.md)  
[アプリ名とタイルの変更](set-name-tile.md)  
[アプリを以前のバージョンに復元する](restore-an-app.md)