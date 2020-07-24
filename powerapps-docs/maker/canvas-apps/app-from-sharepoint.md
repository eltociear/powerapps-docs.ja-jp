---
title: SharePoint リストからキャンバス アプリを作成する | Microsoft Docs
description: Power Apps で、SharePoint リストのデータを管理するキャンバス アプリを自動的に作成する
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 12/05/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 346bb27911549715b6c4fdc40f64552c524527be
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/13/2020
ms.locfileid: "3308477"
---
# <a name="create-a-canvas-app-in-power-apps-from-a-sharepoint-list"></a>SharePoint リストから Power Apps でキャンバス アプリを作成する

このトピックでは、Power Apps を使用し、SharePoint リストの項目に基づいてキャンバス アプリを作成します。 Power Apps または SharePoint Online 内からアプリを作成できます。 データ ゲートウェイを介して[接続する](connections/connection-sharepoint-online.md#create-a-connection) 場合、Power Apps 内から、オンプレミスの SharePoint サイトのリストに基づいてアプリを作成できます。

作成するアプリには、3 つの画面が含まれます。

- 閲覧画面では、リスト内のすべての項目をスクロールできます。
- 詳細画面では、リストの 1 つの項目についてすべての情報を表示することができます。
- 編集画面では、項目の作成または既存の項目に関する情報の更新を行うことができます。

このトピックの概念および手法は、SharePoint の任意のリストに適用できます。 手順を正確に実行するには:

1. SharePoint Online サイトで、**SimpleApp** という名前のリストを作成します。
2. **タイトル**という名前の列内で、**バニラ**、**チョコレート**、および**イチゴ**のエントリを作成します。

テキスト、日付、数字、および通貨などの、さまざまな種類の多くの列を含むはるかに複雑なリストを作成する場合でも、アプリを作成する原則は変わりません。

> [!IMPORTANT]
> Power Apps は、すべての種類の SharePoint データをサポートするわけではありません。 詳細については、[既知の問題](connections/connection-sharepoint-online.md#known-issues) を参照してください。

## <a name="create-an-app-from-within-power-apps"></a>Power Apps 内からアプリを作成する

1. [Power Apps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインします。

1. **自分のアプリを作成する**で、**データから開始** にカーソルを置き、**このアプリの作成**を選択します。

    ![アプリを作成するためのオプション](./media/app-from-sharepoint/start-from-data.png)

1. SharePoint タイルで、**電話レイアウト**を選択します。

    ![アプリを作成するためのオプション](./media/app-from-sharepoint/sharepoint-tile.png)

1. 選択された**直接接続**オプションで、**作成**を選択します。

    ![接続の作成](./media/app-from-sharepoint/create-connection.png)

1. **SharePoint サイトに接続する**で、SharePoint Online サイトの URL を入力または貼り付け、次に**移動**を選択します。

    次の例のように、(リストの名前ではなく) サイトの URL のみを含めます。<br>`https://microsoft.sharepoint.com/teams/Contoso`

1. **リストを選択する**で、**SimpleApp** を選択し、次に**接続**を選択します。

    数分後に、閲覧画面でアプリが開き、リストで作成した項目が表示されます。 リストにデータが**タイトル**以外の列にある場合、アプリはそのデータを表示します。 スクリーン上部で、タイトル バーは、リストの更新、リストの並べ替え、およびリスト内の項目の作成を行うためのアイコンを表示します。 タイトル バーの下で、検索ボックスには入力または貼り付けしたテキストに基づいてリストをフィルター処理するオプションが表示されます。 

    ![閲覧画面](./media/app-from-sharepoint/browse-screen.png)

    このアプリを使用したり、他のユーザーと共有したりする前に、さらに変更を加えることができます。 ベスト プラクティスとして、続行する前に Ctrl-S キーを押し、これまでの作業を保存します。 アプリに名前を付け、次に**保存**を選択します。

## <a name="create-an-app-from-within-sharepoint-online"></a>SharePoint Online 内からアプリを作成する

SharePoint Online コマンド バーからカスタム リストのアプリを作成する場合、アプリはそのリストのビューとして表示されます。 Web ブラウザーに加えて、iOS または Android デバイスでもアプリを実行できます。

1. SharePoint Onlineで、カスタム リストを開き、コマンド バーで **PowerApps** を選択し、次に**アプリの作成**を選択します。

    ![アプリの作成](./media/app-from-sharepoint/generate-new-app.png)

2. 表示されるパネルに、アプリの名前を入力し、次に**作成**を選択します。

    ![アプリに名前を付ける](./media/app-from-sharepoint/app-name.png)

    Web ブラウザーに、SharePoint リストに基づいて作成されたアプリを表示する新しいタブが表示されます。 アプリは、カスタマイズができる Power Apps Studio に表示されます。

    ![既定のアプリ](./media/app-from-sharepoint/default-app.png)

3. (オプション) SharePoint リストのブラウザー タブを (それを選択してから、たとえば F5 キーを押すことにより) 最新の情報に更新し、次に、下記の手順に従ってアプリを実行または管理します。

    - (別のブラウザー タブで) アプリを実行するには、**開く**を選択します。
    - 組織内の他のユーザーがアプリを実行できるようにするには、**このビューを公開する**を選択します。

        他のユーザーがアプリを編集できるようにするには、**編集可能**アクセス許可を使用して[共有します](share-app.md)。

    - SharePoint からビューを削除するには、**このビューを削除する**を選択します。

        Power Apps からアプリを削除するには、[アプリを削除します](delete-app.md)。

> [!NOTE]
> SharePoint リストから作成されたアプリは、現在 Power Apps モバイルに表示されません。

## <a name="next-steps"></a>次の手順
このトピックでは、SharePoint リストのデータを管理するアプリを作成しました。 次の手順として、より複雑なリストからアプリを作成し、次にニーズに合わせてアプリをカスタマイズ (閲覧画面から開始) します。

> [!div class="nextstepaction"]
> [既定の閲覧画面のカスタマイズ](customize-layout-sharepoint.md)
