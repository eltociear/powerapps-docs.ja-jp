---
title: キャンバス アプリにレコードを表示、編集、または追加する | Microsoft Docs
description: データ ソース内のテーブルからレコードを表示、編集、または追加するには、キャンバス アプリ フォームを使用します。
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/22/2020
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 92d48215c4d85c5fa1435b47e92de2f62475e6da
ms.sourcegitcommit: 5a87f0e3ec317ccb8752a6635a4c5b2091aadbca
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2020
ms.locfileid: "3309443"
---
# <a name="show-edit-or-add-a-record-in-a-canvas-app"></a>キャンバス アプリにレコードを表示、編集、または追加する

キャンバス アプリで、**[表示](controls/control-form-detail.md)** フォーム コントロールを追加および構成して、レコード内のすべてのフィールドを表示します。**[編集](controls/control-form-detail.md)** フォーム コントロールを追加および構成して、レコード内のフィールドを編集し、レコードを追加し、変更内容をデータ ソースに保存することもできます。

## <a name="prerequisites"></a>前提条件

- Power Apps に[コントロールを追加および構成](add-configure-controls.md) する方法について説明します。
- [この Excel ファイル](https://az787822.vo.msecnd.net/documentation/get-started-from-data/FlooringEstimates.xlsx) をダウンロードして、チュートリアルのサンプル データを取得します。
- Excel ファイルを OneDrive for Business などの[クラウド ストレージ アカウント](connections/cloud-storage-blob-connections.md) にアップロードします。
- 電話用のアプリを作成するか開いて、 Excel ファイルの **FlooringEstimates** テーブルへの[接続を追加](add-data-connection.md) します。

    タブレット PC アプリにフォームを追加できますが、フォームには既定で 3 つの列があるため、この記事には適合しません。

- 既存のアプリを開く場合は、[スクリーンを追加](add-screen-context-variables.md) します。

## <a name="add-a-form-and-show-data"></a>フォームを追加し、データを表示する
1. 空白のスクリーンで、**[ドロップ ダウン](controls/control-drop-down.md)** コントロールを追加して、**ChooseProduct** と名前を付けます。

    > [!NOTE]
   > コントロールの追加、コントロールの名前変更、およびプロパティの設定の方法がわからない場合は、[コントロールの追加および構成](add-configure-controls.md) を参照してください。

1. 右側のウィンドウの**プロパティ** タブで、**Items** を `FlooringEstimates` に、**Value** を `Name` に設定します。

    ![フォームの Items プロパティを設定する](./media/add-form/items-property.png)

    一覧に、データ ソースから取得したフローリング製品の名前が表示されます。

1. **編集**フォーム コントロールを追加し、それを **ChooseProduct** の下に移動して、フォームがスクリーンの大部分を占めるようにサイズ変更します。

    ![フォームの追加](./media/add-form/add-a-form.png)

    > [!NOTE]
   > このトピックでは**編集**フォーム コントロールについて説明していますが、同様の原則が**表示**フォーム コントロールにも当てはまります。

1. フォームの **[DataSource](controls/control-form-detail.md)** プロパティを **FlooringEstimates** に設定し、フォームの **[Item](controls/control-form-detail.md)** プロパティを次の数式に設定します。

    `ChooseProduct.Selected`

   この式では、フォームの構成が完了した後、**ChooseProduct** でユーザーが選択したレコードが表示されるように指定しています。

1. 右側のウィンドウの**プロパティ** タブで**フィールドの編集**を選択します。

    ![フィールドを編集する](./media/add-form/edit-fields.png)

1. **フィールド** ウィンドウで**フィールドの追加**を選択し、各フィールドのチェック ボックスをオンにしてから、**追加**を選択します。

    ![フィールドの追加](./media/add-form/add-fields.png)

1. **フィールドを追加**の隣の省略記号 (...) を選択し、**すべて折りたたむ**を選択してから、**名前**を一覧の一番上にドラッグします。

    ![フィールドの移動](./media/add-form/move-field.png)

    **編集**フォーム コントロールに変更内容が反映されます。

    ![フォームの表示](./media/add-form/show-form1.png)

## <a name="set-the-card-type-for-a-field"></a>フィールドにカードの種類を設定する
1. **フィールド** ウィンドウで、**価格**フィールドの下矢印を選択して展開します。

1. **コントロールの種類**の一覧を開き、**スライダーを編集**を選択します。

    ![スライダーを編集](./media/add-form/edit-slider.png)

    フォームでは、**価格**フィールドは**テキスト入力**コントロールの代わりに**スライダー** コントロールを表示します。

1. (オプション) 同じプロセスに従って、**概観**フィールドのコントロールを**複数行テキストの編集**コントロールに変更します。

## <a name="edit-form-only-save-changes"></a>(編集フォームのみ) 変更を保存する

1. フォームの名前を **EditForm** に変更します。

1. **[ボタン](controls/control-button.md)** コントロールを追加し、**[OnSelect](controls/properties-core.md)** プロパティに次の式を設定します。

   `SubmitForm(EditForm)`

1. F5 キーを押してプレビューを開き、製品の名前を変更してから、作成したボタンを選択します。

    **[SubmitForm](functions/function-form.md)** 関数は変更をデータ ソースに保存します。

1. (オプション) Esc キーを押して (または右上隅の閉じるアイコンを選んで)、プレビューを閉じます。

## <a name="next-steps"></a>次の手順
[フォーム](working-with-forms.md) と[数式](working-with-formulas.md) の操作についてさらに説明します。
