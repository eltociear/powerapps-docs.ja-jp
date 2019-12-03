---
title: アプリで使用する Excel ファイルの共有 | Microsoft Docs
description: Dropbox、OneDrive、Google Drive で Excel ファイルを共有します。 ユーザーは、ファイルやフォルダーを編集したり閲覧したりすることができます。
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
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2019
ms.locfileid: "74674923"
---
# <a name="share-excel-data-used-by-your-app"></a>アプリで使用される Excel データの共有
OneDrive などの[クラウド アカウント](connections/cloud-storage-blob-connections.md)でアプリのユーザーと Excel データを共有することができます。

たとえば、会社のテクニカル サポート グループの名前と電話番号を表示するアプリを作成するとします。 その情報を記録した Excel スプレッドシートを Dropbox 内のフォルダーに配置します。 そのうえで、アプリのユーザーが名前と電話番号を閲覧できるように、そのフォルダーをアプリのユーザーと共有します。

ユーザーがアプリを実行したり、さらにアプリを変更したりできるように、データを共有する必要があります。 共有アクセス許可を与えられていないユーザーには、Excel ファイル内のデータが表示されません。

このトピックでは、Dropbox、OneDrive、Google Drive を使用して Excel スプレッドシートのデータを共有する方法について説明します。 Excel ファイルのデータを表示するアプリを作成するには、[一連のデータからアプリを作成する方法](get-started-create-from-data.md)に関するページを参照してください。

## <a name="share-data-in-dropbox"></a>Dropbox でデータを共有する
1. Power Apps から Dropbox への接続の作成に使用したものと同じアカウントを使用して、Dropbox にサインインします。
2. Excel ファイルが格納されているフォルダーを選択し、 **[共有]** を選択します。  
   
    ![[共有] コマンド](./media/share-app-data/dropbox-share.png)
3. ダイアログ ボックスで、アプリのユーザーが Dropbox へのサインインに使用する電子メール アドレスを入力します。  
   
    ![Dropbox で共有](./media/share-app-data/dropbox-perms.png)
4. アプリのユーザーがアプリのデータを追加、変更、削除する場合は、 **[編集可能]** を選択します。 それ以外の場合は、 **[表示可能]** を選択します。
5. **[共有]** を選択します。

詳細については、[Dropbox でのフォルダーの共有](https://www.dropbox.com/en/help/19)に関するページを参照してください。

## <a name="share-data-in-onedrive"></a>OneDrive でデータを共有する
1. Power Apps から OneDrive への接続を作成したときに使用したものと同じアカウントを使用して OneDrive にサインインします。
2. ファイルが格納されているフォルダーを選択し、 **[共有]** を選択します。  
   
    ![[共有] コマンド](./media/share-app-data/onedrive-share.png)
   
    > [!NOTE]
   > OneDrive for Business の場合は、ファイルを含むフォルダーではなく、ファイル自体を共有します。
3. ダイアログ ボックスで **[電子メール]** を選択します。
   
    ![メールで共有する](./media/share-app-data/onedrive-email.png)
4. アプリのユーザーが OneDrive へのサインインに使用する電子メール アドレスを指定し、 **[共有]** を選択します。  
   
    ![ユーザーの指定](./media/share-app-data/onedrive-perms.png)

詳細については、「[OneDrive のファイルとフォルダーの共有](https://support.office.com/article/Share-OneDrive-files-and-folders-and-change-permissions-9fcc2f7d-de0c-4cec-93b0-a82024800c07)」を参照してください。

## <a name="share-data-in-google-drive"></a>Google Drive でデータを共有する
1. Power Apps から Google Drive への接続を作成したときと同じアカウントを使用して Google Drive にサインインします。
2. Excel ファイルが格納されているフォルダーを右クリックし、 **[共有]** を選択します。  
   
    ![[共有] コマンド](./media/share-app-data/googledrive-share.png)
3. ダイアログ ボックスで、アプリのユーザーが Google Drive へのサインインに使用する電子メール アドレスを入力します。  
   
    ![ユーザーの指定](./media/share-app-data/googledrive-perms.png)
4. アプリのユーザーがアプリのデータを追加、変更、削除する場合は、アクセス許可の一覧から **[編集可能]** を選択します。 それ以外の場合は、 **[表示可能]** を選択します。
5. **[完了]** を選択します。

詳細については、[Google ドライブのファイルとフォルダーを共有する方法](https://support.google.com/drive/answer/2494822)に関するページを参照してください。

### <a name="known-limitations"></a>既知の制限
お客様の組織内の Excel データを共有する方法の詳細については、[これらの制限をご確認ください](connections/cloud-storage-blob-connections.md#known-limitations)。

