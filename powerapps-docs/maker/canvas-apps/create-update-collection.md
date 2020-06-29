---
title: キャンバス アプリでコレクションを作成および更新する | Microsoft Docs
description: キャンバス アプリでコレクションを作成し、コレクションにアイテムを追加し、1 つまたはすべてのアイテムを削除する
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 01/28/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b124a27119a7b91572bdfef563e0f99e9d5da08d
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3305763"
---
# <a name="create-and-update-a-collection-in-a-canvas-app"></a>キャンバス アプリでコレクションを作成および更新する

コレクションを使用すると、ユーザーはアプリで管理できるデータを格納できます。 コレクションは、製品一覧内の製品など、類似したアイテムのグループです。 コレクションなど、さまざまなタイプの変数の詳細については、[キャンバス アプリの変数について](working-with-variables.md)を参照してください。

## <a name="prerequisites"></a>前提条件

- Power Apps に[サインアップ](../signup-for-powerapps.md) し、登録に使用した同じ資格情報を使用して[サインイン](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) します。
- Power Apps で、アプリを作成するか既存のアプリを開きます。
- Power Apps で[コントロールを構成する](add-configure-controls.md)方法を説明します。

## <a name="create-a-multicolumn-collection"></a>複数列コレクションの作成

1. Power Apps Studio で、**テキスト入力**コントロールを追加します。

    ![テキスト入力コントロールを挿入する](./media/create-update-collection/add-textbox.png)

1. 左側のナビゲーション ウィンドウで省略記号を選択し、**名前の変更**、次に**製品名**を入力してコントロール名を変更します。

    ![コントロール名の変更](./media/create-update-collection/rename-textbox.png)

1. **ドロップ ダウン** コントロールを追加します。

    ![ドロップダウン リストの追加](./media/create-update-collection/add-dropdown.png)

1. **ドロップ ダウン** コントロールの**色**の名前を変更し、そして **Items** プロパティがプロパティ リストで選択されていることを確認します。

    ![Items プロパティ](./media/create-update-collection/items-property.png)

1. 数式バーで、**DropDownSample** をこの式で置き換えます。

    `["Red","Green","Blue"]`

1. **Button** コントロールを追加し、**Text** プロパティを**追加**し、その **OnSelect**  プロパティをこの式に設定します。

    ```powerapps-dot
    Collect(
        ProductList,
        {
            Product: ProductName.Text,
            Color: Colors.Selected.Value
        }
    )
    ```

1. F5 キーを押して **ProductName** にテキストを入力し、**色**のオプションを選択して**追加**を選択します。

    ![アプリのプレビュー](./media/create-update-collection/preview-add.png)

1. 前のステップを少なくともあと 2 回繰り返してから、Esc キーを押します。

1. **ファイル** メニューで**コレクション**を選択し、作成したコレクションを表示します。

    ![コレクションの表示](./media/create-update-collection/show-collection.png)

## <a name="show-a-collection"></a>コレクションの表示

1. 垂直方向の **Gallery** コントロールを追加します。

    ![縦方向のギャラリーの追加](./media/create-update-collection/add-gallery.png)

1. ギャラリー **Items** プロパティを **ProductList** に設定します。

1. **データ** ウィンドウで、サブタイトル フィールドを**色**、タイトル フィールドを**製品**に設定します。

    ![ギャラリーの Items プロパティを設定し、表示されるフィールドを変更する](./media/create-update-collection/configure-gallery.png)

1. **データ** ウィンドウを閉じて、ギャラリーを選択してから、**レイアウト** フィールドに**タイトルとサブタイトル**を設定します。

    ![ギャラリーの Items プロパティを設定し、表示されるフィールドを変更する](./media/create-update-collection/change-layout.png)

    画面は次の例のようになります。

    ![最初の画面例](./media/create-update-collection/screen-example1.png)

## <a name="remove-one-or-all-items"></a>1 つまたはすべてのアイテムを削除する

1. ギャラリーの下部の近くをクリックまたはタップし、左上隅にある鉛筆アイコンをクリックまたはタップして、ギャラリー テンプレートを選択します。

    ![ギャラリー テンプレートを選択する](./media/create-update-collection/select-template.png)

1. **ごみ箱**アイコンをギャラリー テンプレートに追加します。

    ![ごみ箱アイコンを追加する](./media/create-update-collection/trash-icon.png)

1. そのアイコンの **OnSelect** プロパティを次の式に設定します。

    `Remove(ProductList, ThisItem)`

1. ギャラリーの外側にボタンを追加し、**Text** プロパティを**クリア**に設定し、**OnSelect** プロパティを次の式に設定します。

    `Clear(ProductList)`

1. Alt キーを押しながら、**ごみ箱**アイコンを選択して、コレクションからそのアイテムを削除します。または**クリア**ボタンを選択して、コレクションからすべてのアイテムを削除します。

## <a name="put-a-sharepoint-list-into-a-collection"></a>SharePoint リストをコレクションに配置する

1. [SharePoint リストへの接続を作成します](connections/connection-sharepoint-online.md#create-a-connection)。

1. ボタンを追加して、**[OnSelect](controls/properties-core.md)** プロパティをこの関数に設定し、*ListName* を SharePoint リストの名前に置き換えます。<br>

    `Collect(MySPCollection, ListName)`

    この関数は、**MySPCollection** という名前の SharePoint リストと同じデータを含むコレクションを作成します。

1. Alt キーを押しながら、ボタンを選択します。

1. (任意) 作成したコレクションをプレビューするには、**ファイル** メニューの **コレクション**を選択します。

ギャラリーで SharePoint リスト (日付、選択肢、ユーザーなど) のデータを表示する方法については、[ギャラリーにリストの列を表示する](connections/connection-sharepoint-online.md#show-list-columns-in-a-gallery)を参照してください。 フォームで (ドロップダウン リスト、日付の選択、およびユーザーの選択を使用して) データを表示する方法については、[フォームの編集コントロールとフォームの表示コントロール](controls/control-form-detail.md)を参照してください。

## <a name="next-steps"></a>次の手順

- [リファレンス トピック](functions/function-clear-collect-clearcollect.md)で **Collect** 関数をレビューします。
- [AddColumns、DropColumns、RenameColumns、および ShowColumns](functions/function-table-shaping.md) 関数を使用して、コレクション内のデータを形成する方法を説明します。
