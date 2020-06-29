---
title: Common Data Service を使用して一からキャンバス アプリを作成する | Microsoft Docs
description: Power Apps で、Common Data Service のレコードを追加、更新および削除するキャンバス アプリを作成します。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 05/21/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 624dd66a2f0574a33f4bb796b88e3e4d5845c973
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/13/2020
ms.locfileid: "3308339"
---
# <a name="create-a-canvas-app-from-scratch-using-common-data-service"></a>Common Data Service を使用してキャンバス アプリを一から作成する

標準エンティティ (組み込み)、カスタム エンティティ (組織が作成)、またはその両方を使用して Common Data Service に保存されているデータを管理するキャンパス アプリを構築します。

Common Data Service からアプリを構築する場合、SharePoint、Dynamics 365、Salesforce などのデータ ソースが利用できるので、Power Apps から接続を作成する必要はありません。 アプリで表示または管理するエンティティを指定するだけです。

## <a name="prerequisites"></a>前提条件

- 一からアプリを作成する前に、[アプリを作成](data-platform-create-app.md)し、そのアプリの [ギャラリー](customize-layout-sharepoint.md)、[フォーム](customize-forms-sharepoint.md)、および[カード](customize-card.md)をカスタマイズして Power Apps の基本情報を詳しく理解してください。
- サンプル データを使用してデータベースが作成された[環境に切り替えます](working-with-environments.md)。 適切なライセンスがある場合は、ニーズを満たす[環境を作成する](../../administrator/create-environment.md)ことができます。
- アプリを作成するには、[環境作成者](https://docs.microsoft.com/power-platform/admin/database-security#predefined-security-roles)セキュリティ ロールが割り当てられている必要があります。

## <a name="open-a-blank-app"></a>空のアプリを開く

1. [Power Apps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインします。

1. **自分のアプリを作成する**で、**キャンバス アプリを一から作成**を選択します。

    ![空のアプリのタイル](./media/data-platform-create-app-scratch/blank-app.png)

1. アプリに名前を指定し、**電話**を選択し、**作成**を選択します。

    アプリはタブレット向けに一から作成できますが、このトピックではスマートフォン向けのアプリの構築について説明します。

## <a name="specify-an-entity"></a>エンティティを指定する

1. 画面の中央で**データに接続**を選択します。

1. **データ** ウィンドウで **Common Data Service** を選択し、**アカウント** チェックボックスをオンにして、**接続**を選択します。

1. 右上隅の閉じるアイコンを選択して、**データ** ウィンドウを閉じます。

## <a name="add-a-list-screen"></a>リスト画面を追加する

1. **ホーム** タブで、**新しい画面**の下矢印を選択し、**リスト**を選択します。

    ![リスト画面を追加する](./media/data-platform-create-app-scratch/list-screen.png)

1. 左側のナビゲーション バーで、**BrowseGallery1** を選択し、**Items** プロパティの値を次の式に設定します。

    `SortByColumns(Search(Accounts, TextSearchBox1.Text, "name"), "name", If(SortDescending1, SortOrder.Descending, SortOrder.Ascending))`

    この数式は次のことを指定します。

   - ギャラリーは、**取引先企業**エンティティからのデータを表示する必要があります。
   - ユーザーが並べ替えボタンを選択して並べ替え順序を切り替えるまで、データは昇順で並べ替えられる必要があります。
   - ユーザーが検索バー (**TextSearchBox1**) に 1 つ以上の文字を入力するか貼り付けた場合、ユーザーが指定した文字が**名前**フィールドに含まれる取引先企業のみがリストに表示されます。

     [これらの関数とその他の多くの関数](formula-reference.md)を使用して、アプリの表示と動作の方法を指定できます。

     ![ギャラリーの Items プロパティを設定する](./media/data-platform-create-app-scratch/gallery-items.png)

1. [ギャラリーのカスタマイズ](customize-layout-sharepoint.md)の説明に従って、各アカウントの名前のみが表示されるようにギャラリーのレイアウトを設定し、**参照**という単語が表示されるようにタイトル バーを構成します。

    ![閲覧画面](./media/data-platform-create-app-scratch/final-browse.png)

1. 左側のナビゲーション バーで、**Screen1** にカーソルを合わせ、省略記号アイコン (...) を選択し、**削除**を選択します。

1. 左側のナビゲーション バーで、**Screen2** にカーソルを合わせ、省略記号アイコン (...) を選択し、**名前の変更**を選択します。

1. **BrowseScreen** を入力または貼り付け、その画面でギャラリーの名前を **BrowseGallery** に変更します。

    ![参照画面ギャラリーの名前を変更する](./media/data-platform-create-app-scratch/rename-browse.png)

## <a name="add-a-form-screen"></a>フォーム画面を追加する

1. 前の手順の最初のステップを繰り返しますが、**リスト**画面の代わりに**フォーム**画面を追加します。

1. 右側のウィンドウの**詳細設定**タブに示すように、フォームの **DataSource** プロパティを **Accounts** に設定し、**Item** プロパティを **BrowseGallery.Selected** に設定します。

    ![フォームのデータソースと Item プロパティを設定する](./media/data-platform-create-app-scratch/form-datasource.png)

1. 右側のウィンドウの**プロパティ** タブで**フィールドの編集**を選択して、**フィールド** ウィンドウを開きます。

1. **フィールドの追加**を選択し、次のフィールドのチェック ボックスをオンにします。

    - **取引先企業名**
    - **住所 1: 番地**
    - **住所 1: 市区町村**
    - **住所 1: 郵便番号**
    - **従業員数**
    - **売上高**

    > [!NOTE]
    > このシナリオ以外では、**新しいフィールド**を選択して必要な情報を入力し、**完了**を選択してカスタム フィールドを作成できます。 詳細については、[フィールドの作成](../common-data-service/create-edit-field-portal.md#create-a-field)を参照してください。<br><br>![](media/data-platform-create-app-scratch/choose-or-add-fields.png "Select and add a field")

1. **追加** を選択します。

1. タイトル バーの **Text** プロパティを**作成/編集**が表示されるように設定します。

    画面に変更内容が反映されます。

    ![フォームのデータソースと Item プロパティを設定する](./media/data-platform-create-app-scratch/field-list.png)

1. この画面の **FormScreen** の名前を変更します。

## <a name="configure-icons"></a>アイコンを構成する

1. **BrowseScreen** で、画面の上部付近にある円形アイコンの **OnSelect** プロパティを次の式に設定します。

    `Refresh(Accounts)`

    ![更新アイコン](./media/data-platform-create-app-scratch/refresh-icon.png)

1. プラス アイコンの **OnSelect** プロパティを次の式に設定します。

    `NewForm(EditForm1); Navigate(FormScreen, ScreenTransition.None)`

    ![追加アイコン](./media/data-platform-create-app-scratch/plus-icon.png)

1. 右を指している最初の矢印の **OnSelect** プロパティを次の式に設定します。

    `EditForm(EditForm1); Navigate(FormScreen, ScreenTransition.None)`

    ![次へアイコン](./media/data-platform-create-app-scratch/next-icon.png)

1. **FormScreen** で、キャンセル アイコンの **OnSelect** プロパティを次の式に設定します。

    `ResetForm(EditForm1);Navigate(BrowseScreen, ScreenTransition.None)`

    ![キャンセル アイコン](./media/data-platform-create-app-scratch/cancel-icon.png)

1. チェックマーク アイコンの **OnSelect** プロパティを次の式に設定します。

    `SubmitForm(EditForm1); Navigate(BrowseScreen, ScreenTransition.None)`

    ![チェックマーク アイコン](./media/data-platform-create-app-scratch/checkmark-icon.png)

1. **挿入**タブで**アイコン**を選択し、**ごみ箱**アイコンを選択します。

1. **ごみ箱**アイコンの**色**プロパティを**白**に設定し、**OnSelect** プロパティを次の式に設定します。

    `Remove(Accounts, BrowseGallery.Selected); Navigate(BrowseScreen, ScreenTransition.None)`

    ![ごみ箱アイコン](./media/data-platform-create-app-scratch/trash-icon.png)

## <a name="test-the-app"></a>アプリをテストする

1. 左側のナビゲーション バーで、**BrowseScreen** を選択し、F5 キーを押して (または右上隅の再生アイコンを選択して) プレビューを開きます。

    ![プレビューを開く](./media/data-platform-create-app-scratch/open-preview.png)

1. 一覧の昇順と降順の並べ替え順を切り替え、アカウント名の 1 文字以上の文字によって一覧をフィルター処理します。

1. アカウントを追加し、追加したアカウントを編集し、アカウントを更新して変更をキャンセルし、アカウントを削除します。

## <a name="next-steps"></a>次の手順

- [ソリューションにこのアプリをリンク](add-app-solution.md)することにより、たとえば、別の環境に 展開したり、AppSource に公開することができます。
- [1 つまたは複数のサンプル アプリを開き](open-and-run-a-sample-app.md)、作成可能なさまざまな種類のアプリを調べます。
