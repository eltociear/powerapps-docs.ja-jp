---
title: SharePoint の接続の概要 | Microsoft Docs
description: SharePoint での使用可能な機能、応答、および例について説明します。
author: NickWaggoner
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/03/2019
ms.author: niwaggon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0c0f4744e7b323e3262a63278e7c12348142a99b
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/13/2020
ms.locfileid: "3308615"
---
# <a name="connect-to-sharepoint-from-a-canvas-app"></a>キャンバス アプリから SharePoint に接続する

![SharePoint](./media/connection-sharepoint-online/sharepointicon.png)

SharePoint サイトに接続してカスタム リストからアプリを自動的に生成するか、または既存のアプリにデータを追加する前に、またはアプリを最初から構築する前につながりを作成します。

データが存在する場所に応じて、次のアプローチのいずれかまたは両方を実行できます:

- SharePoint Online サイトまたはオンプレミス サイトでカスタム リストのデータを表示します。
- ライブラリ (SharePoint Online のみ) 内の画像を表示し、ビデオまたはオーディオ ファイルを再生します。

## <a name="generate-an-app"></a>アプリの生成

カスタム リストのデータを管理する場合、Power Apps で [3 画面アプリを自動的に生成](../app-from-sharepoint.md) できます。 ユーザーは最初の画面でリストを参照し、2 番目の画面でアイテムの詳細を表示し、3 番目の画面でアイテムを作成または更新できます。

> [!NOTE]
> SharePoint リストに**選択**、**検索**、または**ユーザーまたはグループ**列が含まれている場合は、このトピックの後半にある [ギャラリーでデータを表示する](connection-sharepoint-online.md#show-list-columns-in-a-gallery) を参照してください。

## <a name="create-a-connection"></a>つながりの作成

1. [Power Apps にサインイン](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) し、左側のナビゲーションバーで**データ** > **つながり**を選択してから、左上隅の**新規つながり**を選択します。

    > [!div class="mx-imgBorder"]
    > ![左側のナビゲーションバーでデータ > つながりを選択してから、左上隅の新規つながりを選択します。](./media/connection-sharepoint-online/new-connection.png)

1. 右上隅の検索ボックスで、**SharePoint** を入力または貼り付けてから、**SharePoint** を選択します。

    > [!div class="mx-imgBorder"]
    > ![右上隅の検索ボックスで、SharePoint を入力または貼り付けてから、SharePoint を選択します。](./media/connection-sharepoint-online/select-sharepoint.png)

1. 次の一連の手順のいずれかを実行します:

    - SharePoint Online に接続するには、**直接接続 (クラウド サービス)** を選択し、**作成**を選択してから、資格情報 (要求された場合) を入力します。

        > [!div class="mx-imgBorder"]
        > ![SharePoint Online に接続するため、直接接続 (クラウドサービス) を選択する](./media/connection-sharepoint-online/select-online.png)

        つながりが作成され、既存のアプリにデータを追加したり、アプリを最初から構築したりできます。

    - オンプレミス サイトに接続するには、**オンプレミス データ ゲートウェイを使用して接続**を選択します。

        > [!div class="mx-imgBorder"]
        > ![オンプレミス サイトに接続するため、**オンプレミス データ ゲートウェイを使用して接続する)](./media/connection-sharepoint-online/select-onprem.png)

        認証の種類として **Windows** を指定してから、資格情報を指定します。 (資格情報にドメイン名が含まれる場合は、*ドメイン\エイリアス*として指定します。)

        > [!div class="mx-imgBorder"]
        > ![資格情報の指定](./media/connection-sharepoint-online/specify-creds.png)

        **ゲートウェイを選択**で、使用するゲートウェイを選択してから、**作成**を選択します。

        > [!NOTE]
        > オンプレミスのデータ ゲートウェイがインストールされていない場合は、[ゲートウェイをインストール](../gateway-reference.md) し、アイコンを選択してゲートウェイの一覧を最新の情報に更新します。

        > [!div class="mx-imgBorder"]
        > ![ゲートウェイの選択](./media/connection-sharepoint-online/choose-gateway.png)

        つながりが作成され、既存のアプリにデータを追加したり、アプリを最初から構築したりできます。

## <a name="add-data-to-an-existing-app"></a>既存のアプリにデータを追加する

1. Power Apps Studio で、更新するアプリを開き、**表示**タブを選択してから、**データ ソース**を選択します。

    > [!div class="mx-imgBorder"]
    > ![ビュー タブで、データ ソースを選択する](./media/connection-sharepoint-online/view-data-sources.png)

1. **データ** ウィンドウで、**データ ソースの追加** > **SharePoint** を選択します。

1. **SharePoint サイトへの接続**で、**最近利用したサイト** リスト (または使用するサイトの URL を入力または貼り付ける) のエントリを選択してから、**接続**を選択します。

    > [!div class="mx-imgBorder"]
    > ![サイトの選択](./media/connection-sharepoint-online/select-sp-site.png)

1. **リストの選択**で、 **ドキュメント**または使用する 1 つまたは複数のリスト のチェックボックスをオンにしてから、**接続**を選択します:

    > [!div class="mx-imgBorder"]
    > ![リストの選択で、ドキュメントまたは使用する 1 つまたは複数のリストのチェックボックスをオンにしてから、接続を選択する](./media/connection-sharepoint-online/select-sp-tables.png)

    すべての種類のリストが既定で表示されるわけではありません。 Power Apps ではカスタム リストはサポートされますが、テンプレート ベースのリストはサポートされません。 使用する目的のリストの名前が表示されていない場合は、一番下までスクロールし、**カスタム名を入力**と示されているボックスにリストの名前を入力します。

    > [!div class="mx-imgBorder"]
    > ![カスタム リスト名の入力が含まれているボックスにリストの名前を入力します。](./media/connection-sharepoint-online/custom-list.png)

    データ ソースまたはソースがアプリに追加されます。

## <a name="build-your-own-app-from-scratch"></a>独自のアプリを最初から構築する

[アプリを最初から作成する](../get-started-create-from-blank.md) の概念を、Excel の代わりに SharePoint に適用します。

## <a name="show-list-columns-in-a-gallery"></a>ギャラリーにリストの列を表示する

カスタム リストにこれらのタイプの列のいずれかが含まれている場合、数式バーを使用してそのギャラリーの 1 つ以上の**ラベル** コントロールの**テキスト** プロパティを設定することにより、そのデータを**ギャラリー** コントロールに表示します。

- **選択**または**検索**列で、**ThisItem.**_ColumnName_**.Value** を指定してその列のデータを表示します。

    たとえば、**場所**という名前の**選択**列がある場合は **ThisItem.Location.Value** と指定し、**郵便番号**という名前の**検索**列がある場合は **ThisItem.PostalCode.Value** と指定します。

- **ユーザーまたはグループ**列では、**ThisItem.**_ColumnName_**.DisplayName** と指定して、ユーザーまたはグループの名前を表示します。

    たとえば、**ThisItem.Manager.DisplayName** と指定して、**上司**という名前の**ユーザーまたはグループ**列から名前を表示します。

    電子メール アドレスや役職など、ユーザーに関する別の情報を表示することもできます。 オプションのリスト全体を表示するには、**ThisItem.**_ColumnName_**.** (末尾のピリオドを含む) と指定します。

    > [!NOTE]
    > **CreatedBy** 列では、**ThisItem.Author.DisplayName** と指定してリストの項目を作成したユーザーの表示名を表示します。 **ModifiedBy** 列では、**ThisItem.Editor.DisplayName** と指定してリストの項目を変更したユーザーの表示名を表示します。

- **管理されたメタデータ**列では、**ThisItem.**_ColumnName_**.Label** と指定してその列のデータを表示します。

    たとえば、**言語**という名前の**管理されたメタデータ**列がある場合は **ThisItem.Languages.Label** と指定します。

## <a name="show-data-from-a-library"></a>ライブラリからのデータを表示する

SharePoint ライブラリに複数の画像がある場合、**ドロップ ダウン** コントロールをアプリに追加して、ユーザーが表示する画像を指定できるようにします。 **ギャラリー** コントロール、およびビデオなどの他の種類のデータのような他のコントロールにも同じ原則を適用できます。

1. まだ実行していない場合は、[つながりを作成](#create-a-connection) してから、[既存のアプリにデータを追加](#add-data-to-an-existing-app) します。

1. **ドロップ ダウン** コントロールを追加し、**ImageList** と名前を付けます。

1. **ImageList** の**項目**プロパティを**ドキュメント**に設定します。

1. 右側のウィンドウの**プロパティ** タブで、**値**リストを開いてから、**名前**を選択します。

    ライブラリ内の画像のファイル名は、**ImageList** に表示されます。

    > [!div class="mx-imgBorder"]
    > ![画像の一覧](./media/connection-sharepoint-online/dropdown-items.png)

1. **画像**コントロールを追加し、その**画像**プロパティを次の式に設定します:

    `ImageList.Selected.'Link to item'`

1. F5 キーを押してから、**ImageList** で別の値を選択します。

    指定した画像が表示されます。

    > [!div class="mx-imgBorder"]
    > ![サンプル画像](./media/connection-sharepoint-online/golden-honey.png)

SharePoint ライブラリからデータを表示するためのより複雑なアプローチを示す [サンプル アプリをダウンロード](https://pwrappssamples.blob.core.windows.net/samples/spdoclib_blogapp.msapp) できます。

1. アプリをダウンロードした後、[Power Apps Studio](https://us.create.powerapps.com/studio/#) を開き、左側のナビゲーション バーで**開く**を選択してから、**参照**を選択します。
1. **開く**ダイアログ ボックスで、ダウンロードしたファイルを見つけて開いてから、このトピックの最初の 2 つの手順に従って、SharePoint ライブラリをデータ ソースとして追加します。

> [!NOTE]
> 既定では、このアプリは [委任の警告](../delegation-overview.md) を表示しますが、ライブラリに含まれる項目が 500 未満の場合は無視できます。

この 1 画面アプリでは、左下隅のリストにライブラリ内のすべてのファイルが表示されます。

- 上部にある検索ボックスに 1 つ以上の文字を入力するか貼り付けることにより、ファイルを検索できます。
- ライブラリにフォルダーが含まれている場合、タイトル バーのすぐ下にあるフォルダーのリストでフィルター アイコンを選択することにより、ファイルのリストをフィルター処理できます。

必要なファイルを見つけたら、それを選択して、右側の**ビデオ**、**画像**、または**オーディオ** コントロールに表示します。

> [!div class="mx-imgBorder"]
> ![サンプル画像](./media/connection-sharepoint-online/library-app.png)

## <a name="known-issues"></a>既知の問題

### <a name="lists"></a>リスト

Power Apps はスペースを含む列を読み取ることはできますが、スペースは 16 進数のエスケープ コード **"\_x0020\_"** に置き換えられます。 たとえば、SharePoint の **"列名"** は、データレイアウトで表示したり、数式で使用したりすると、Power Apps では **"Column_x0020_Name"** として表示されます。

一部の種類の列はサポートされておらず、列の中には一部の種類のカードしかサポートしていないものもあります。

| 列の種類 | サポート | 既定のカード |
| --- | --- | --- |
| 1 行テキスト |有効 |テキストの表示 |
| 複数行テキスト |有効 |テキストの表示 |
| 選択 |有効 |検索の表示<br>検索の編集<br>複数選択の表示<br>複数選択の編集 |
| 番号 |有効 |パーセンテージの表示<br>評価の表示<br>テキストの表示 |
| 通貨型  |有効 |パーセンテージの表示<br>評価の表示<br>テキストの表示 |
| 日付と時間 |有効 |テキストの表示 |
| 検索 |有効 |検索の表示<br>検索の編集<br>複数選択の表示<br>複数選択の編集 |
| ブール値 (はい/いいえ) |有効 |テキストの表示<br>トグルの表示 |
| ユーザーまたはグループ |有効 |検索の表示<br>検索の編集<br>複数選択の表示<br>複数選択の編集 |
| ハイパーリンク |有効 |ビュー ​​URL<br>テキストの表示 |
| 写真 |はい (読み取り専用) |画像の表示<br>テキストの表示 |
| 添付 |はい (読み取り専用) |添付ファイルの表示|
| 計算 |はい (読み取り専用) | |
| タスクの結果 |No | |
| 外部データ |No | |
| 管理されたメタデータ |はい (読み取り専用) | |
| 評価 |No | |

### <a name="libraries"></a>ライブラリ

- Power Apps からのファイルをライブラリにアップロードすることはできません。
- ライブラリからの PDF ファイルを PDF ビューアー コントロールに表示することはできません。
- Power Apps モバイルでは**ダウンロード**関数をサポートしていません。
- Power Apps モバイルまたは Windows 10 アプリでユーザーがアプリを実行する場合、**起動**関数を使用してギャラリーでのライブラリ コンテンツを表示します。

## <a name="next-steps"></a>次の手順

- [データ ソースからデータを表示する](../add-gallery.md) 方法についてご確認ください。
- [詳細を表示してレコードを作成または更新する](../add-form.md) 方法についてご確認ください。
- 接続できる他の種類の [データ ソース](../connections-list.md) を参照してください。
