---
title: Common Data Service | からキャンバスアプリを作成します。Microsoft Docs
description: Power Apps で、データを管理するためのキャンバスアプリを自動的に作成 Common Data Service
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: quickstart
ms.custom: canvas
ms.reviewer: ''
ms.date: 12/05/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c62a690073e591c693d914000511b586dfc97b69
ms.sourcegitcommit: d194d2fa009ca7bfcbe95e5f31473832a130e0a6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74959382"
---
# <a name="create-a-canvas-app-from-common-data-service-in-power-apps"></a>Power Apps で Common Data Service からキャンバスアプリを作成する

Power Apps で、 [Common Data Service](../common-data-service/data-platform-intro.md)のサンプルアカウントの一覧に基づいて、キャンバスアプリを作成します。 このアプリでは、すべてのアカウントの参照、1 つのアカウントの詳細の表示、アカウントの作成、更新および削除が可能です。

Power Apps にサインアップしていない場合は、開始する前に[無料でサインアップ](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)してください。

## <a name="prerequisites"></a>前提条件

このクイックスタートを実行するには、[環境](https://docs.microsoft.com/power-platform/admin/database-security#predefined-security-roles)作成者のセキュリティロールに割り当てられている必要があります。また、Common Data Service 内のデータベースが作成され、データが含まれ、更新が許可されている[環境に切り替える](working-with-environments.md)必要があります。 そのような環境がなく、管理者権限を保持している場合、この要件に合う[環境を作成](https://docs.microsoft.com/power-platform/admin/environments-administration#create-an-environment)します。

## <a name="create-an-app"></a>アプリを作成する

1. [Power Apps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)にサインインし、必要に応じて、このトピックで前述した手順に従って環境を切り替えます。

1. **[Make your own app]\(独自アプリの作成\)** の下の **[Start from data]\(データから開始\)** にポインターを合わせ、 **[このアプリの作成]** を選択します。

    ![アプリを作成するためのオプション](./media/data-platform-create-app/start-from-data.png)

1. **[Common Data Service]** タイルで、 **[電話レイアウト]** を選びます。

    ![接続タイル](./media/data-platform-create-app/connection-tile.png)

1. **[テーブルの選択]** で、 **[アカウント]** を選び、 **[接続]** を選びます。

1. **[Power Apps Studio へようこそ]** ダイアログボックスが表示されたら、 **[スキップ]** を選択します。

ブラウザー画面でアプリが開き、ギャラリーと呼ばれるコントロールにアカウントの一覧が表示されます。 画面上部近くのタイトル バーには、ギャラリー内のデータの更新、ギャラリー内のデータのアルファベット順の並べ替え、およびギャラリーへのデータの追加を行うアイコンが表示されます。 オプションで、タイトル バーの下の検索ボックスを使用して、入力または貼り付けたテキストに基づいてギャラリーのデータをフィルタリングできます。 

既定で、ギャラリーにはメール アドレス、市区町村、アカウント名が表示されます。 「[次のステップ](data-platform-create-app.md#next-steps)」を見ていただくとわかるように、ギャラリーをカスタマイズして、データの表示方法を変更したり、他の種類のデータを表示したりすることさえできます。

![ブラウズ画面](./media/data-platform-create-app/browse-screen.png)

## <a name="save-the-app"></a>アプリの保存
このアプリを使用したり、他のユーザーと共有する前に、さらに変更を加えたいことでしょう。 続行する前に、ベスト プラクティスとして作業を保存します。

1. 左上隅にある **[ファイル]** タブを選びます。

1. **[アプリ設定]** ページで、アプリ名を **AppGen** に設定し、背景色を濃い赤に変更し、アイコンをチェック マークに変更します。

    ![アプリの設定ページ](./media/data-platform-create-app/app-settings.png)

1. 左端近くの **[保存]** を選んでから、左下隅の **[保存]** を選びます。

## <a name="next-steps"></a>次の手順
このクイックスタートでは、Common Data Service でアカウントに関するサンプルデータを管理するアプリを作成しました。 次の手順では、ニーズに合わせて既定のブラウザー画面のギャラリーと他の要素をカスタマイズします。

> [!div class="nextstepaction"]
> [ギャラリーをカスタマイズします](customize-layout-sharepoint.md)。
