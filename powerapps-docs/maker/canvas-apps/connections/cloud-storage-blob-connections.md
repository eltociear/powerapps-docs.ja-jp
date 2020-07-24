---
title: クラウド ストレージ接続の概要 | Microsoft Docs
description: クラウド ストレージ アカウントに接続し、アプリで Excel データを表示する方法について説明します
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 07/12/2016
ms.author: lanced
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: dd5135aa04a552fc5606918a8158b40457a6eb6f
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/13/2020
ms.locfileid: "3308546"
---
# <a name="connect-to-cloud-storage-from-power-apps"></a>Power Apps からクラウド ストレージに接続する
Power Apps は、いくつかのクラウド ストレージ接続を提供します。 いずれかの接続を使用し、Excel ファイルを保存し、それに含まれる情報をアプリ全体で使用することができます。 これらの接続は次のとおりです:  

| **Azure Blob** | **Box** | **Dropbox** | **Google Drive** | **OneDrive** | **OneDrive<br>for Business** |
| --- | --- | --- | --- | --- | --- |
| ![アイコン](./media/cloud-storage-blob-connections/blobicon.png) |![API アイコン][boxicon] |![API アイコン][dropboxicon] |![API アイコン][googledriveicon] |![API アイコン][onedriveicon] |![API アイコン][onedriveforbusinessicon] |

[!INCLUDE [connection-requirements](../../../includes/connection-requirements.md)]

* [テーブルとして書式設定された](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-E81AA349-B006-4F8A-9806-5AF9DF0AC664) データを含む Excel ファイル:
  
  1. Excel ファイルを開き、使用するデータの任意のセルを選択します。
  2. **挿入**タブの**テーブル**を選択します。
  3. **テーブルとして保存**ダイアログ ボックスで**先頭行をテーブルの見出しとして使用する**チェック ボックスを選択し、**OK** を選択します。
  4. 変更を保存。

## <a name="connect-to-the-cloud-storage-connection"></a>クラウド ストレージ接続に接続する
1. [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) で、**管理**を展開し、**接続**を選択します。  
   
    ![接続を選択する](./media/cloud-storage-blob-connections/connections.png)
2. **新しい接続**を選択し、クラウド ストレージ接続を選択します。 たとえば、**OneDrive** を選択します。
3. クラウド ストレージ アカウントのユーザー名とパスワードが求められます。 それらを入力し、**サインイン**を選択します:  
    ![ユーザー名とパスワードを入力する](./media/cloud-storage-blob-connections/signin.png)
   
    サインインすると、アプリ内でこの接続を使用できるようになります。
4. アプリ内で、リボンの**ビュー** タブの**データ ソース**をクリックまたはタップします。 右側のウィンドウで、**データ ソースの追加**をクリックまたはタップし、使用するクラウド ストレージ接続をクリックまたはタップしてから Excel テーブルを選択します。
5. **接続** を選択します。
   
    そのテーブルがデータ ソースとして一覧表示されます:
   
    ![Excel テーブルを選択する](./media/cloud-storage-blob-connections/selecttable.png)
   
    > [!NOTE]
   > Excel データはテーブルとして書式設定されている必要があります。

## <a name="using-the-excel-data-in-your-app"></a>アプリで Excel データを使用する
1. **挿入**タブで**ギャラリー**を選択し、**テキスト付き**ギャラリー コントロールを選択します。
2. ギャラリーの**[アイテム](../controls/properties-core.md)** プロパティを Excel テーブルに設定します。 たとえば、Excel テーブルの名前が**テーブル 1** の場合、テーブル 1 に設定します:  
   
    ![アイテム プロパティ](./media/cloud-storage-blob-connections/itemsproperty.png)  
   
    ギャラリーは Excel テーブルからの情報で自動的に更新されます。
3. ギャラリーで、2 番目または 3 番目の**ラベル** コントロールを選択します。 既定では、2 番目の**テキスト**プロパティが表示されます。3 番目のラベルは自動的に `ThisItem.something` に設定されます。 これらのラベルはテーブルの任意の列に設定できます。
   
    次の例では、2 番目のラベルが `ThisItem.Name` に設定され、3 番目のラベルが `ThisItem.Notes` に設定されています。  
   
    ![2 番目のラベル](./media/cloud-storage-blob-connections/items-secondtextbox.png)  
   
    ![3 番目のラベル](./media/cloud-storage-blob-connections/items-thirdtextbox.png)  
   
    サンプル出力:  
    ![2 番目と 3 番目のラベル](./media/cloud-storage-blob-connections/secondthirdtextboxes.png)
   
> [!NOTE]
> 1 番目のボックスは、実際にはイメージ コントロールです。 Excel テーブルにイメージがない場合、イメージ コントロールを削除し、その場所にラベルを追加できます。 [コントロールの追加および構成](../add-configure-controls.md) は優れたリソースです。

[テーブルとレコードについて](../working-with-tables.md) に詳細といくつかの例があります。  

## <a name="sharing-your-app"></a>アプリの共有
[アプリ](../share-app.md)、コネクタなどの[リソース](../share-app-resources.md)、組織内の他の[データ](../share-app-data.md) を共有できます。

Dropbox のフォルダーを共有する場合は、共有フォルダーをユーザーの Dropbox アカウントに添付する必要があります。

Excel ファイルに関連するコネクタには、[特定の制限](#sharing-excel-tables) があります。

## <a name="known-limitations"></a>既知の制限
アプリで Excel 接続を使用しようとしたとき、**サポートされていないデータ型**または**テーブルとして書式設定されていない**が表示された場合、[データをテーブルとして書式設定](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-E81AA349-B006-4F8A-9806-5AF9DF0AC664) してください。

Excel データに計算列が含まれる場合、それを使用してアプリを構築することはできません。そのデータを既存のアプリに追加することもできません。

### <a name="sharing-excel-tables"></a>Excel のテーブルの共有
Excel ファイル内のデータを共有するには:

* OneDrive for Business の場合は、ファイル自体を共有します。
* OneDrive では、任意のメディアで、ファイルが含まれているフォルダーを共有し、URL ではなくファイル パスを指定します。
* Dropbox または Google ドライブでは、ファイルまたはフォルダーを共有します。

## <a name="helpful-links"></a>便利なリンク
[使用可能な接続](../connections-list.md) をすべて参照してください。  
アプリに[接続を追加](../add-manage-connections.md) および[データ ソースを追加](../add-data-connection.md) する方法を説明します。  
表形式のデータ ソースの[テーブルとレコードについて](../working-with-tables.md)。  
いくつかの追加ギャラリー リソースには、[アイテムの一覧を表示](../add-gallery.md) および[ギャラリーでイメージとテキストを表示](../show-images-text-gallery-sort-filter.md) が含まれます。

<!--Icon references-->
[boxicon]: ./media/cloud-storage-blob-connections/boxicon.png
[dropboxicon]: ./media/cloud-storage-blob-connections/dropboxicon.png
[googledriveicon]: ./media/cloud-storage-blob-connections/googledriveicon.png
[onedriveicon]: ./media/cloud-storage-blob-connections/onedriveicon.png
[onedriveforbusinessicon]: ./media/cloud-storage-blob-connections/onedriveforbusinessicon.png
