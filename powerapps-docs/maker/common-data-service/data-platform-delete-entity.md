---
title: ユーザー定義エンティティの削除 | Microsoft Docs
description: ユーザー定義エンティティを削除し Power Apps のすべてのデータを消去する方法に関する詳細な手順
author: lancedMicrosoft
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8925c11d202ce73a7690687762c8bc2282913050
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "2883665"
---
# <a name="delete-a-custom-entity"></a>ユーザー定義エンティティの削除
ユーザー定義エンティティを削除できますが、標準のエンティティは削除できません。

1. [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) で**データ**セクションを展開し、左側のナビゲーション ウィンドウで**エンティティ**をクリックまたはタップします。

    ![エンティティの詳細](./media/data-platform-cds-create-entity/entitylist.png "エンティティ リスト")

2. エンティティの一覧で、削除するエンティティをクリックまたはタップし、コマンド バーから**エンティティの削除**オプションをクリックまたはタップします。

3. 表示するダイアログ ボックスで、**削除**をクリックまたはタップしてエンティティを削除します。

>[!NOTE]
>エンティティを削除すると、エンティティ定義およびエンティティに含まれるすべてのデータの両方とも削除されます。 エンティティおよびエンティティ内のデータは削除後には復旧できません。

>[!NOTE]
>そのアプリで使用されるエンティティを削除すると、アプリやフローが破損する場合があります。

>[!NOTE]
>エンティティ A にエンティティ B への [検索フィールド](data-platform-entity-lookup.md) がある場合、エンティティ A を削除する前にエンティティ B を削除する必要があります。

