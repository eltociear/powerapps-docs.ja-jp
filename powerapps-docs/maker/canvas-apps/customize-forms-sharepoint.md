---
title: キャンバス アプリでフォームをカスタマイズする | Microsoft Docs
description: Power Apps で、キャンバス アプリのフォームに、どのデータを、どのような順番で、どのコントロールに表示するかを指定します。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/17/2018
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f522f520c0f0f042e73932630980dee93bc5c89c
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3305786"
---
# <a name="customize-a-canvas-app-form-in-power-apps"></a>Power Apps でキャンバス アプリ フォームをカスタマイズする

キャンバス アプリでは、最も重要なデータを、ユーザーが簡単に理解して更新できるよう、最も見やすい直感的な順序で表示されるように、**Display form** コントロールと **Edit form** コントロールをカスタマイズできます。

それぞれのフォームは、少なくとも 1 つのカードで構成され、データ ソースから取得された特定の列のデータが個々のカードに表示されます。 このトピックの手順に従って、フォームに表示するカードを指定したり、フォーム内でカードの位置を上げ下げしたりできます。

キャンバス アプリに慣れていない場合は、[キャンバス アプリとは?](getting-started.md) を参照してください。

## <a name="prerequisites"></a>前提条件

Common Data Service から[アプリを生成](data-platform-create-app.md)して、そのアプリで[ギャラリーをカスタマイズ](customize-layout-sharepoint.md)します。

## <a name="show-and-hide-cards"></a>カードの表示と非表示

1. [Power Apps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にログインして、生成しカスタマイズしたアプリを開きます。

1. 左側のナビゲーション バーで、要素の一覧をフィルター処理するために検索バーに **D** と入力もしくは貼り付けし、**DetailForm1** を選択します。

    > [!div class="mx-imgBorder"]
    > ![詳細画面を選択](./media/customize-forms-sharepoint/select-detailform.png)

1. 右側のウィンドウの**プロパティ** タブで **フィールドの編集** を選択して、**フィールド** ウィンドウを開きます。

    > [!div class="mx-imgBorder"]
    > ![フィールド ウィンドウを開く](./media/customize-forms-sharepoint/edit-fields.png)

1. **説明**などのフィールドにカーソルを合わせ、省略記号 (...) を選択してから**削除**を選択し、フィールドを非表示にします。

    > [!div class="mx-imgBorder"]
    > ![フィールド リスト](./media/customize-forms-sharepoint/hide-fields.png)

1. **フィールドの追加**を選択してフィールドを表示するには、検索ボックスにフィールド名の最初の数文字を入力または貼り付け、フィールドのチェック ボックスをオンにして、**追加**を選択します。

    > [!div class="mx-imgBorder"]
    > ![フィールド リスト](./media/customize-forms-sharepoint/show-field.png)

## <a name="reorder-the-cards"></a>カードの並び替え

1. **フィールド** ウィンドウで、**アカウント名**フィールドを一覧の一番上にドラッグします。

    **DetailForm1** のカードは変更を反映しています。

    > [!div class="mx-imgBorder"]
    > ![並べ替え後のカード](./media/customize-forms-sharepoint/reordered-card.png)

1. (任意) その他のカードをこの順序に並べ替えます。

    - アカウント名
    - 従業員数
    - 年間売上
    - 代表電話
    - 住所 1: 番地 1
    - 住所 1: 番地 2
    - 住所 1: 市区町村
    - 住所 1: 郵便番号

1. 左側のナビゲーション バーで、検索バーに **Ed** と入力するか貼り付け、**EditForm1** を選択します。

1. 前の手順とこれを繰り返して、**EditForm1** のフィールドが **DetailForm1** のフィールドと一致するようにします。

## <a name="run-the-app"></a>アプリの実行

1. 左側のナビゲーション バーで、検索バーに **Br** と入力するか貼り付け、**BrowseScreen1** を選択します。

1. F5 キーを押して (または右上隅の**プレビュー** アイコンを選択して) プレビュー モードを開きます。

    > [!div class="mx-imgBorder"]
    > ![プレビュー アイコン](./media/customize-forms-sharepoint/open-preview.png)

1. 右上隅のプラス アイコンを選択して、**EditScreen1** でレコードを追加します。

    > [!div class="mx-imgBorder"]
    > ![レコードの追加](./media/customize-forms-sharepoint/add-record.png)

1. 必要なデータを追加し、右上隅のチェックマーク アイコンを選択して変更を保存し、**BrowseScreen1** に戻ります。

    > [!div class="mx-imgBorder"]
    > ![レコードの保存](./media/customize-forms-sharepoint/save-record.png)

1. 今作成した項目の矢印を選択して、その詳細を **DetailScreen1** に表示します。

    > [!div class="mx-imgBorder"]
    > ![右矢印](./media/customize-forms-sharepoint/right-arrow.png)

1. 右上隅の編集アイコンを選択して、**EditScreen1** でレコードを更新します。

    > [!div class="mx-imgBorder"]
    > ![レコードの編集](./media/customize-forms-sharepoint/edit-record.png)

1. 少なくとも 1 つのフィールドの情報を変更し、右上隅のチェック マークを選択して変更内容を保存し、**DetailScreen1** に戻ります。

    > [!div class="mx-imgBorder"]
    > ![変更の保存](./media/customize-forms-sharepoint/save-record.png)

1. 右上隅にあるごみ箱アイコンを選択して、先ほど更新したレコードを削除し、**BrowseScreen1** に戻ります。

    > [!div class="mx-imgBorder"]
    > ![レコードの削除](./media/customize-forms-sharepoint/delete-record.png)

1. Esc キーを押して (または左上隅の閉じるアイコンを選択して)、プレビュー モードを閉じます。

## <a name="next-steps"></a>次の手順

- アプリを[保存して公開](save-publish-app.md)します。
- アプリの[カードをカスタマイズ](customize-card.md)します。