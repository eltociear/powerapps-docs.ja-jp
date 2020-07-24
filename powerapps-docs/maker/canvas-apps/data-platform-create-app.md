---
title: Common Data Service からキャンバス アプリを作成する | Microsoft Docs
description: Power Apps で、Common Data Service のデータを管理するキャンバス アプリを自動的に作成する
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
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "3307419"
---
# <a name="create-a-canvas-app-from-common-data-service-in-power-apps"></a>Power Apps で、Common Data Service からキャンバス アプリを作成する

Power Apps で、[Common Data Service](../common-data-service/data-platform-intro.md) のサンプル アカウントのリストに基づいてキャンバス アプリを作成します。 このアプリでは、すべてのアカウントの参照、1 つのアカウントの詳細の表示、アカウントの作成、更新および削除が可能です。

Power Apps にサインアップしていない場合は、開始する前に[無料でサインアップ](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)してください。

## <a name="prerequisites"></a>前提条件

このクイックスタートを実行するには、[環境作成者](https://docs.microsoft.com/power-platform/admin/database-security#predefined-security-roles)のセキュリティ ロールが割り当てられている必要があります。また、Common Data Service のデータベースが作成され、データが含まれ、更新が許可されている[環境に切り替える](working-with-environments.md)必要があります。 そのような環境がなく、管理者特権を保持している場合、この要件を満たす[環境を作成](https://docs.microsoft.com/power-platform/admin/environments-administration#create-an-environment)することができます。

## <a name="create-an-app"></a>アプリの作成

1. [Power Apps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインし、必要に応じて、このトピックで前に説明したように環境を切り替えます。

1. **自分のアプリを作成する**で、**データから開始** にカーソルを置き、**このアプリの作成**を選択します。

    ![アプリを作成するためのオプション](./media/data-platform-create-app/start-from-data.png)

1. **Common Data Service** タイルで、**携帯電話レイアウト**を選択します。

    ![接続タイル](./media/data-platform-create-app/connection-tile.png)

1. **テーブルの選択**で、**取引先企業**を選び、**接続**を選択します。

1. **Power Apps Studio へようこそ**のダイアログ ボックスが表示されたら、**スキップ**を選択します。

ブラウザー画面でアプリが開き、ギャラリーと呼ばれるコントロールにアカウントの一覧が表示されます。 画面上部近くのタイトル バーには、ギャラリー内のデータの更新、ギャラリー内のデータのアルファベット順の並べ替え、およびギャラリーへのデータの追加を行うアイコンが表示されます。 オプションで、タイトル バーの下の検索ボックスを使用して、入力または貼り付けたテキストに基づいてギャラリーのデータをフィルター処理できます。 

既定で、ギャラリーには電子メール アドレス、市区町村、アカウント名が表示されます。 [次のステップ](data-platform-create-app.md#next-steps)にあるように、ギャラリーをカスタマイズして、データの表示方法を変更したり、他の種類のデータを表示することもできます。

![閲覧画面](./media/data-platform-create-app/browse-screen.png)

## <a name="save-the-app"></a>アプリの保存
このアプリを使用したり、他のユーザーと共有したりする前に、さらに変更を加えることができます。 続行する前に、ベスト プラクティスとして作業を保存します。

1. 左上隅にある**ファイル** タブを選択します。

1. **アプリ設定** ページで、アプリ名を **AppGen** に設定し、背景色を濃い赤に変更し、アイコンをチェックマークに変更します。

    ![アプリの設定ページ](./media/data-platform-create-app/app-settings.png)

1. 左端近くの**保存**を選んでから、左下隅の**保存**を選択します。

## <a name="next-steps"></a>次の手順
このクイック スタートでは、Common Data Service の取引先企業のサンプル データを管理するアプリを作成しました。 次の手順では、ニーズに合わせて既定のブラウザー画面のギャラリーと他の要素をカスタマイズします。

> [!div class="nextstepaction"]
> [ギャラリーをカスタマイズします](customize-layout-sharepoint.md)。
