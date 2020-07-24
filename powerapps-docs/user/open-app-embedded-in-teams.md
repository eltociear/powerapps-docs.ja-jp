---
title: Microsoft Teams にアプリを追加する | Microsoft Docs
description: Microsoft Teams チャネルにアプリを追加して、アプリの共有相手であるユーザーがそのチャネルでアプリを開くことができるようにする方法について説明します。
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: quickstart
ms.date: 11/16/2018
ms.author: mduelae
ms.custom: ''
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 97be49797df13b82901425ae9389e85538068f5d
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3302819"
---
# <a name="add-an-app-to-microsoft-teams"></a>Microsoft Teamsにアプリを追加する

Office 365テクノロジーは、Microsoft Teams に基づいて構築されたチャット ベースのコラボレーションプラットフォームです。 Teams のチャネルに Power Apps キャンバス アプリを追加して、Teams のエクスペリエンスをカスタマイズできます。 このトピックでは、Product Showcase サンプル アプリを Teams のチャネルに追加し、そのチャネルからアプリを開く方法を説明します。 

![Microsoft Teams に埋め込まれたアプリ](./media/open-app-embedded-in-teams/embedded-app.png)

Power Apps にサインアップしていない場合は、[無料でサインアップ](https://make.powerapps.com/signup?redirect=marketing&email=) してください。

## <a name="prerequisites"></a>前提条件

この手順を行うには、[Office 365 サブスクリプション](https://signup.microsoft.com/Signup?OfferId=467eab54-127b-42d3-b046-3844b860bebf&dl=O365_BUSINESS_PREMIUM&ali=1) と [Teams のチャネル](https://www.youtube.com/watch?v=he2f1quaR7M) が必要です。

## <a name="sign-in-to-power-apps"></a>Power Apps にサインインする

[https://make.powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)で、Power Apps にサインインします。

## <a name="add-an-app"></a>アプリの追加

1. Microsoft Teams で、チームを選択し、そのチームが所有するチャネルを選びます。 この例では、**Business Development** チームの **General** チャネルです。

    ![](./media/open-app-embedded-in-teams/teams-select-channel.png)

2. **[+]** を選んでタブを追加します。

    ![](./media/open-app-embedded-in-teams/teams-add-tab.png)

3. **タブの追加**  ダイアログ ボックスで、**PowerApps** を選びます。

    ![](./media/open-app-embedded-in-teams/add-a-tab.png)

4. **[サンプル アプリ]** > **[Product Showcase]** > **[保存]** の順に選びます。

    ![](./media/open-app-embedded-in-teams/select-an-app.png)

    アプリがチャネルで使用可能になりました。

    ![](./media/open-app-embedded-in-teams/app-in-channel.png)

> [!NOTE]
> 独自のアプリの場合は、Teams に追加する前に[共有する](../maker/canvas-apps/share-app.md)必要があります (サンプル アプリは既定で共有されます)。

## <a name="open-an-app"></a>アプリを開く

1. Microsoft Teams で、チームと、アプリを含むチャネルを選びます。

    ![](./media/open-app-embedded-in-teams/teams-select-channel.png)

2. **[Product Showcase]** タブを選びます。

    ![](./media/open-app-embedded-in-teams/open-tab.png)

    チャネルでアプリが開きます。

    ![](./media/open-app-embedded-in-teams/app-in-channel.png)

## <a name="known-issues"></a>既知の問題

Microsoft Teams のデスクトップ アプリでは：

* アプリは、セキュリティで保護された (https) 接続経由でイメージや .pdf ファイルなどのコンテンツを読み込む必要があります。
* すべてのセンサー (**Acceleration**、**Compass**、**Location** など) がサポートされているとは限りません。
* サポートされているオーディオ形式は、AAC、H264、OGG Vorbis、および WAV のみです。

## <a name="clean-up-resources"></a>リソースのクリーンアップ

チャネルからアプリを削除するには、**[Product Showcase]** タブ、**[削除]** の順に選びます。

## <a name="next-steps"></a>次のステップ

このトピックでは、Product Showcase サンプル アプリを Teams のチャネルに追加して、そのチャネルからアプリを開きました。 Power Apps についてさらに詳しく学習するには、Power Apps のチュートリアルを続けてください。

> [!div class="nextstepaction"]
> [Power Apps チュートリアル](../maker/canvas-apps/get-started-create-from-blank.md)
