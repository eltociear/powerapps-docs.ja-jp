---
title: Power Apps ポータル管理センターの概要 | MicrosoftDocs
description: Power Apps ポータル管理センターに関する情報。
author: neerajnandwana-msft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: nenandw
ms.reviewer: tapanm
ms.openlocfilehash: 743955dee5b2f2df8992019aef77db81c62e3306
ms.sourcegitcommit: 2fd873a1ea17f419f6194714efffa47a9bd00c2e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "3506870"
---
# <a name="power-apps-portals-admin-center"></a>Power Apps ポータル管理センター

Power Apps ポータル管理センターでポータルの高度な管理操作を実行できます。 管理センターはポータルが正常にプロビジョニングされると利用可能になります。

## <a name="open-power-apps-portals-admin-center"></a>Power Apps ポータル管理センターを開く

1. Power Apps ホーム ページの **最近のアプリ** セクションに移動してポータルを見つけます。

    > [!div class=mx-imgBorder]
    > ![最近のアプリ](../media/recent-apps.png "最近のアプリ")  

2. **その他のコマンド (...)** > **設定** を順に選択します。

    > [!div class=mx-imgBorder]
    > ![ポータル設定オプション](../media/portal-settings-option.png "ポータル設定オプション")

3. **ポータル設定** ウィンドウで **管理** を選択します。

    > [!div class=mx-imgBorder]
    > ![ポータル設定ウィンドウ](../media/portal-settings-admin.png "ポータル設定ウィンドウ")

## <a name="add-yourself-as-an-owner-of-the-azure-ad-application"></a>自分を Azure AD アプリケーションの所有者として追加する

グローバル管理者でなく、すでにプロビジョニングされたポータルを管理しようとした場合、またはプロビジョニングに失敗した場合にプロビジョニングを再実行する場合は、ポータルに接続された Azure Active Directory (Azure AD) アプリケーションの所有者である必要があります。

1. Power Apps ポータル管理センターに移動し、**ポータルの詳細**タブを開きます。

2. **アプリケーション ID** フィールドから値をコピーします。

    > [!div class=mx-imgBorder]
    > ![ポータルの詳細タブ](../media/portal-details-admin.png "ポータルの詳細タブ")

3. テナントに関連付けられる Azure AD に移動します。 [!include[](../../../includes/proc-more-information.md)] [アンマネージド ディレクトリを Azure Active Directory の管理者として引き継ぐ](https://docs.microsoft.com/azure/active-directory/active-directory-manage-o365-subscription)

4. Azure AD では、コピーしたアプリケーション ID を使用してアプリ登録を検索します。 **マイ アプリ**から**すべてのアプリ**への切り替えが必要になることがあります。

5. このアプリ登録の所有者としてユーザーまたはグループを追加します。 [!include[](../../../includes/proc-more-information.md)] [アプリケーションへのアクセスの管理](https://docs.microsoft.com/azure/active-directory/active-directory-managing-access-to-apps)

    > [!Note]
    > このタスクは、組織のグローバル管理者またはこのアプリケーションの既存の所有者のいずれかによって実行できます。

6. 所有者として自分を追加すると、Power Apps ポータル管理センターのページが再オープンされます。