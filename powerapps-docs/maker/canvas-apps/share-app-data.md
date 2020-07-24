---
title: アプリで使用する Excel ファイルの共有 | Microsoft Docs
description: Dropbox、OneDrive、および Google Drive で Excel ファイルを共有します。 ユーザーは、ファイルやフォルダーを編集したり閲覧したりすることができます。
author: jamesol-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/16/2016
ms.author: jamesol
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b2eca27d418a762820bf0955edafff435a176efb
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2019
ms.locfileid: "3304245"
---
# <a name="share-excel-data-used-by-your-app"></a>アプリで使用される Excel データの共有
OneDrive などの [クラウド アカウント](connections/cloud-storage-blob-connections.md) のアプリ ユーザーと Excel データを共有できます。

たとえば、会社のテクニカル サポート グループの名前と電話番号を表示するアプリを作成するとします。 情報は Excel スプレッドシートに保存され、Dropbox 内のフォルダーに配置します。 そのうえで、アプリ ユーザーが名前と電話番号を閲覧できるように、そのフォルダーをアプリ ユーザーと共有します。

データを共有して、ユーザーがアプリを実行したり、さらにアプリを変更したりできるようにする必要があります。 共有アクセス許可を与えられていないユーザーには、Excel ファイル内のデータが表示されません。

このトピックでは、Dropbox、OneDrive、および Google Drive を使用して Excel スプレッドシートのデータを共有する方法について説明します。 Excel ファイルからデータを表示するアプリを作成するには、[一連のデータからアプリを作成する方法](get-started-create-from-data.md) を参照してください。

## <a name="share-data-in-dropbox"></a>Dropbox でデータを共有する
1. Power Apps から Dropbox への接続を作成したときと同じアカウントで、Dropbox にサインインします。
2. Excel ファイルが格納されているフォルダーを選択し、**共有**を選択します:  
   
    ![コマンドを共有する](./media/share-app-data/dropbox-share.png)
3. ダイアログ ボックスで、アプリのユーザーが Dropbox へのサインインに使用する電子メール アドレスを入力します。  
   
    ![Dropbox で共有する](./media/share-app-data/dropbox-perms.png)
4. アプリのユーザーがアプリのデータを追加、変更、削除する場合は、**編集可能**を選択します。 それ以外の場合は、**表示可能**を選択します。
5. **共有**を選択します。

詳細については、[Dropbox でフォルダーを共有する](https://www.dropbox.com/en/help/19) を参照してください。

## <a name="share-data-in-onedrive"></a>OneDrive のデータを共有する
1. Power Apps から OneDrive への接続を作成したときと同じアカウントで、OneDrive にサインインします。
2. ファイルが格納されているフォルダーを選択し、**共有**を選択します。  
   
    ![コマンドを共有する](./media/share-app-data/onedrive-share.png)
   
    > [!NOTE]
   > ビジネス用の OneDrive では、ファイルを含むフォルダーではなく、ファイル自体を共有します。
3. ダイアログ ボックスで、**メール**を選択します。
   
    ![メールで共有する](./media/share-app-data/onedrive-email.png)
4. アプリのユーザーが OneDrive へのサイン インに使用するメール アドレスを指定し、**共有**を選択します。  
   
    ![ユーザーを指定する](./media/share-app-data/onedrive-perms.png)

詳細については、[OneDrive ファイルとフォルダーを共有する](https://support.office.com/article/Share-OneDrive-files-and-folders-and-change-permissions-9fcc2f7d-de0c-4cec-93b0-a82024800c07) を参照してください。

## <a name="share-data-in-google-drive"></a>Google Drive でデータを共有する
1. Power Apps から Google Drive への接続を作成したときと同じアカウントで Google Drive にサインインします。
2. Excel ファイルが格納されているフォルダーを右クリックし、**共有**を選択します。  
   
    ![コマンドを共有する](./media/share-app-data/googledrive-share.png)
3. ダイアログ ボックスで、アプリのユーザーが Google Drive へのサイン インに使用するメール アドレスを入力します:  
   
    ![ユーザーを指定する](./media/share-app-data/googledrive-perms.png)
4. アプリ ユーザーがアプリのデータを追加、変更、削除する場合は、アクセス許可の一覧から**編集可能**を選択します。 それ以外の場合は、**表示可能**を選択します。
5. **完了**を選択します。

詳細については、[Google Drive のファイルとフォルダーを共有する](https://support.google.com/drive/answer/2494822) を参照してください。

### <a name="known-limitations"></a>既知の制限
組織内の Excel データを共有する方法については、[これらの制限を確認する](connections/cloud-storage-blob-connections.md#known-limitations) をご覧ください。

