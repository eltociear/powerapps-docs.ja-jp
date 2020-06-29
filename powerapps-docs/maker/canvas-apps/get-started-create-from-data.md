---
title: Excel からキャンバス アプリを作成する | Microsoft Docs
description: Power Apps を使用して、クラウド ストレージ アカウントに格納されている Excel ファイルを使用して自動的にキャンバス アプリを作成する
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
ms.openlocfilehash: 2199d94938e51154d0f616f424f674c408277b52
ms.sourcegitcommit: d194d2fa009ca7bfcbe95e5f31473832a130e0a6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "3307442"
---
# <a name="create-a-canvas-app-from-excel-in-power-apps"></a>Power Apps で Excel からキャンバス アプリを作成する

このトピックでは、Power Apps で Excel テーブルからのデータを使用して最初のキャンバス アプリを作成します。 Excel ファイルを選択して、アプリを作成し、作成したアプリを実行します。 作成されたすべてのアプリには、レコードの参照、レコードの詳細の表示、レコードの作成または更新のための画面が含まれています。 アプリを生成することにより、Excel のデータを使用して実際に機能するアプリをすばやく入手することができ、その後でニーズに合わせてアプリをカスタマイズできます。 

Excel ファイルは、OneDrive、Google Drive、Dropbox などのクラウド ストレージ アカウントに置かれている必要があります。 このトピックでは、OneDrive for Business を使用します。

Power Apps のライセンスがない場合は、 [無料で新規登録](../signup-for-powerapps.md) することができます。

## <a name="prerequisites"></a>前提条件

このトピックの内容に正確に従うには、Excel で [Flooring Estimates](https://az787822.vo.msecnd.net/documentation/get-started-from-data/FlooringEstimates.xlsx) ファイルをダウンロードし、[クラウド ストレージ アカウント](connections/cloud-storage-blob-connections.md) に保存します。

> [!IMPORTANT]
> ご自身の Excel ファイルを使用するには、データがテーブルとして書式設定されている必要があります。 詳しくは、「[テーブルの書式設定](how-to-excel-tips.md)」を参照してください。 

## <a name="create-the-app"></a>アプリの作成

1. [Power Apps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインします。

1. **自分のアプリを作成する**で、**データから開始** にカーソルを置き、**このアプリの作成**を選択します。

    ![アプリを作成するためのオプション](./media/get-started-create-from-data/start-from-data.png)

1. **データを使用して開始する**で、クラウド ストレージ アカウントのタイルで**携帯電話レイアウト**をクリックまたはタップします。

    ![アプリを作成するためのオプション](./media/get-started-create-from-data/odfb-tile.png)

1. メッセージが表示されたら、**接続**をクリックまたはタップし、そのアカウントの資格情報を指定します。

1. **Excel ファイルの選択**で、**FlooringEstimates.xlsx** を参照してクリックまたはタップします。 

1. **テーブルの選択**で、**FlooringEstimates** をクリックまたはタップしてから、**接続**をクリックまたはタップします。

    ![アプリを作成するためのオプション](./media/get-started-create-from-data/choose-table.png)

## <a name="run-the-app"></a>アプリの実行

1. F5 キーを押して (または右上隅の再生アイコンをクリックまたはタップして) プレビューを開きます。

    ![プレビューを開く](./media/get-started-create-from-data/open-preview.png)

1. 右上隅にある並べ替えアイコンをクリックまたはタップして、並べ替え順序を切り替えます。

    ![並べ替えのアイコン](./media/get-started-create-from-data/sort-icon.png)

1. 検索ボックスに 1 つ以上の文字を入力するか貼り付けて、一覧をフィルター処理します。

    たとえば、**Honey** と入力するか貼り付けて、その文字列が製品の名前、カテゴリ、または概要に表示される唯一のレコードを表示します。

    ![フィルターの例](./media/get-started-create-from-data/filter-example.png)

1. レコードを追加する:

    1. プラス アイコンを選択します。

        ![プラス アイコン](./media/get-started-create-from-data/plus-icon.png)

    1. 必要なデータを追加し、チェックマーク アイコンを選択して変更を保存します。

        ![保存アイコン](./media/get-started-create-from-data/save-icon.png)

1. レコードを編集:

    1. 編集するレコードの矢印を選択します。

        ![次へ進む矢印](./media/get-started-create-from-data/next-arrow.png)

    1. 鉛筆アイコンを選択します。

        ![鉛筆のアイコン](./media/get-started-create-from-data/pencil-icon.png)

    1. 1 つ以上のフィールドを更新して、チェックマーク アイコンを選択して変更を保存します。

        ![保存アイコン](./media/get-started-create-from-data/save-icon.png)

        または、キャンセル アイコンを選択して変更を破棄します。

1. レコードを削除します。

    1. 削除するレコードの次へ進む矢印を選択します。

        ![次へ進む矢印](./media/get-started-create-from-data/next-arrow.png)

    1. ごみ箱アイコンを選択します。

        ![ごみ箱アイコン](./media/get-started-create-from-data/trash-icon.png)

## <a name="next-steps"></a>次の手順

ニーズに合わせて既定のブラウザー画面をカスタマイズします。 たとえば、カテゴリや概要ではなく、製品名だけで一覧を並べ替えてフィルター処理できます。

> [!div class="nextstepaction"]
> [既定の閲覧画面をカスタマイズ](customize-layout-sharepoint.md) します。
