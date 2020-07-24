---
title: Northwind Traders のデータベースとアプリをインストールする | Microsoftドキュメント
description: Northwind データベースとアプリを環境にインストールして、リレーショナル概念を調べます。
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/06/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d100ac7902aa1d50abfc148ab4bbaed9e442a4ae
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3304314"
---
# <a name="install-northwind-traders-database-and-apps"></a>Northwind Traders のデータベースとアプリをインストールする

[この一連のトピック](northwind-orders-canvas-part1.md) の手順に従って、Common Data Service のサンプル データベースに実装されているリレーショナル データに関する概念を検出できます。 また、キャンバスおよびモデル駆動型の両方のサンプル ビジネスアプリを調べ、そのデータを管理し、そのようなアプリの作成による実践経験を積むこともできます。 この最初のトピックでは、Northwind Traders データベースを独自の環境にインストールし、サンプル アプリにアクセスする方法について説明します。サンプル アプリを開いて編集すると、アプリの構築方法を確認できます。

Northwind Traders は、注文、製品、顧客、納入業者、および中小企業の他の多くの側面を管理する架空の組織です。 このサンプルは Microsoft Access の最初のバージョンで表示され、Access テンプレートとして引き続き利用できます。

## <a name="prerequisites"></a>前提条件

- Common Data Service をサポートする Power Apps ライセンス。 30 日間 [無料試用ライセンスを使用](../signup-for-powerapps.md) できます。
- Common Data Service データベースのある環境。 適切なアクセス許可を持っている場合、[このような環境を作成](https://docs.microsoft.com/power-platform/admin/create-environment) できます。

## <a name="download-the-solution"></a>ソリューションをダウンロードする

> [!div class="nextstepaction"]
> [Northwind Traders ソリューション ファイルをダウンロード](https://pwrappssamples.blob.core.windows.net/samples/NorthwindTraders_1_0_0_6.zip)

この [ソリューション](../../developer/common-data-service/introduction-solutions.md) ファイル (.zip) には、エンティティ、オプション セット、およびビジネス プロセスの定義が含まれ、キャンバスおよびモデル駆動型アプリや一緒に使用されるその他の部分も含まれます。

## <a name="install-the-solution"></a>ソリューションのインストール

1. [Power Apps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインしてから、Common Data Service データベースが含まれる環境で作業していることを確認してください。

1. 左側のナビゲーション ウィンドウで、**ソリューション**を選択してから、画面の上部にある**インポート**を選択します:

    > [!div class="mx-imgBorder"]
    > ![ソリューション ビューとインポート ソリューションのエントリ ポイント](media/northwind-install/solution-import.png)

1. **ソリューション パッケージの選択**ページで、**参照**を選択します。

    > [!div class="mx-imgBorder"]
    > ![パッケージが選択される前にソリューション パッケージ ページを選択します](media/northwind-install/select-solution2.png)

1. ダウンロードしたファイルを検索してから、**開く**を選択します。

    別の場所を選択しない限り、ファイルはダウンロード フォルダーにあります。

1. 正しいファイル (バージョン番号は異なる場合があります) がある場合は、**次へ**を選択します:

    > [!div class="mx-imgBorder"]
    > ![パッケージが選択された後にソリューション パッケージ ページを選択します](media/northwind-install/confirm-solution2.png)

1. **ソリューション情報**ページで、ソリューションと発行者の名前が正しい場合は**次へ**を選択します。

    > [!div class="mx-imgBorder"]
    > ![ソリューション情報ページ](media/northwind-install/confirm-publisher.png)

1. **インポート オプション** ページで、**インポート**を選択してサンプルに必要な SDK メッセージ処理を確認します:

    > [!div class="mx-imgBorder"]
    > ![インポート オプション ページ](media/northwind-install/confirm-sdk.png)

    別のページで、ソリューションが次の数分でインストールされる進行状況が表示されます:

    > [!div class="mx-imgBorder"]
    > ![進行状況バー](media/northwind-install/solution-progress.png)

    インストールが完了すると、元のページに結果が表示されます:

    > [!div class="mx-imgBorder"]
    > ![インポート ソリューション ページ](media/northwind-install/solution-success.png)

1. **閉じる**を選択します。

## <a name="load-the-sample-data"></a>サンプル データを読み込む

1. **アプリ**を選択してから、**Northwind サンプル データ**を選択します。

    ソリューションをインストールした直後に Northwind アプリが表示されない場合は、数分お待ちください:

    > [!div class="mx-imgBorder"]
    > ![アプリのリストにある Northwind データベース](media/northwind-install/sample-data-app.png)

1. アプリが Common Data Service とやり取りするアクセス許可を求めるとき、**許可する**を選択します:

    > [!div class="mx-imgBorder"]
    > ![Common Data Service の同意ダイアログ ボックス](media/northwind-install/sample-data-permission.png)

1. アプリが読み込まれ、サンプル エンティティにレコードが含まれていないことが表示された後、**データの読み込み**を選択してエンティティを設定します:

    > [!div class="mx-imgBorder"]
    > ![サンプル データ マネージャでのデータ読み込みボタン](media/northwind-install/sample-data-load.png)

    アプリがデータを読み込むと、点がアプリの上部に移動し、レコード数が増加します。

    エンティティは特定の順序で読み込まれるため、レコード間で関連付けを確立できます。 たとえば、**受注明細**エンティティは、最初に読み込まれる**受注**および**受注製品**エンティティと多対一の関係にあります。

    **キャンセル**を選択して、いつでもプロセスをキャンセルでき、**データの削除**を選択して、いつでもデータを削除できます:

    > [!div class="mx-imgBorder"]
    > ![データが読み込まれるときのサンプル データ マネージャ](media/northwind-install/sample-data-progress.png)

    データの読み込みが完了すると、最後の行 (**多対多の関連付け**) では**完了**が表示され、**データの読み込み**および**データの削除**ボタンが再び有効になります:

    > [!div class="mx-imgBorder"]
    > ![データが読み込まれた後のサンプル データ マネージャ](media/northwind-install/sample-data-complete.png)

## <a name="sample-apps"></a>サンプル アプリ

Northwind ソリューションには、このデータとやり取りする次のアプリが含まれます:

- Northwind Orders (キャンバス)
- Northwind Orders (モデル駆動型)

前の手順でアプリを開いたのと同じ方法で、これらのアプリを開きます。

### <a name="canvas"></a>キャンバス

この単一画面アプリは**受注**エンティティのマスター詳細ビューを提供し、ここで受注や受注の各品目の概要を表示および編集できます。 受注の一覧が左端に表示され、その一覧の矢印を選択してその受注の概要と詳細を表示できます。 詳細: [Northwind Traders のキャンバス アプリの概要](northwind-orders-canvas-overview.md)。

> [!div class="mx-imgBorder"]
> ![Northwind キャンバス アプリの受注と詳細の一覧](media/northwind-install/orders-canvas.png)

### <a name="model-driven"></a>モデル駆動型

このアプリは同じデータ (**受注**エンティティにある) でキャンバス アプリとして機能します。 受注の一覧で、受注番号を選択して、受注に関する詳細情報を表示します:

> [!div class="mx-imgBorder"]
> ![Northwind モデル駆動型アプリの受注の一覧](media/northwind-install/orders-model.png)

受注の概要は別のフォームに表示されます:

> [!div class="mx-imgBorder"]
> ![モデル駆動型アプリでの受注明細](media/northwind-install/orders-model-2.png)

フォームを下にスクロールすると、キャンバス アプリと同じ品目が表示されます:

> [!div class="mx-imgBorder"]
> ![モデル駆動型アプリでのその他の受注明細](media/northwind-install/orders-model-3.png)

## <a name="do-it-yourself"></a>実際にやってみましょう

詳細な手順に従って、このトピックで前に説明したキャンバス アプリを作成できます。  手順は 3 つの部分に分かれています:

1. [受注ギャラリーの作成](northwind-orders-canvas-part1.md)。
1. [概要フォームを作成する](northwind-orders-canvas-part2.md)。
1. [詳細ギャラリーを作成する](northwind-orders-canvas-part3.md)。

スキップしたい場合は、ソリューションに各パーツの開始点アプリが含まれています。  アプリの一覧で、**Northwind Orders (キャンバス) - パート 1 の開始**などを探します。

この [アプリの概要](northwind-orders-canvas-overview.md) では、ユーザー インターフェース、データ ソース、および関連付けの使用方法について説明します。

> [!div class="nextstepaction"]
> [概要を読んで開始する](northwind-orders-canvas-overview.md)
