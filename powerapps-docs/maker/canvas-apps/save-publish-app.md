---
title: キャンバス アプリを保存して発行する | Microsoft Docs
description: アプリ メーカー向けのキャンバス アプリを保存および発行するための手順
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 05/08/2020
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 80e6cebfaef5ba0cbb4ae29bf1c69faa15e4af01
ms.sourcegitcommit: 3448869b74152e01a58f61c37d4361d8ae8bb09d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/09/2020
ms.locfileid: "3354122"
---
# <a name="save-and-publish-a-canvas-app-in-power-apps"></a>Power Apps でキャンバス アプリを保存して公開する

キャンバス アプリへの変更を保存するたびに、使用者とアプリを編集するアクセス許可を持つ他のユーザーのみに、自動的にアプリが発行されます。 変更が完了したら、アプリを共有しているすべてのユーザーが利用できるように、明示的に発行する必要があります。

アプリを共有する方法については、[PowerApps でのアプリの共有](share-app.md) を参照してください。

## <a name="save-changes-to-an-app"></a>アプリへの変更を保存する

Power Apps Studio で、**ファイル**メニュー (左端) の**保存**を選択して、次のいずれかの手順に従います:

* これまでにアプリを保存したことがない場合は、**ファイル**メニューから**保存**を選択すると自動的に**名前を付けて保存**に移行します。 **クラウド**として保存先を選び、名前を入力してから、**保存**を選択します。 <br> 

    ![新しいアプリを保存する](./media/save-publish-app/save-as.png)
* アプリを保存したことがある場合は、**保存**を選択します。 また、バージョン固有のメモやコメントを残すこともできます。  

    ![更新したアプリを保存する](./media/save-publish-app/save-app.png)

Power Apps では、2 分ごとにアプリを定期的に保存できます。 アプリをいったん保存すると、Power Apps はユーザーが保存アクションを押したりタップしたりしなくても、アプリのバージョンを定期的に保存し続けます。 作成者は**ファイル**メニューの**アカウント**タブで、**自動保存**設定を有効または無効にできます。

![自動保存設定](./media/save-publish-app/autosave.png)

## <a name="publish-an-app"></a>アプリを公開

1. Power Apps Studio で、**フィル**メニューの (左端) **保存**を選び、**発行**を選択します。

    ![アプリの発行](./media/save-publish-app/publish-app.png)
2. **発行**ダイアログ ボックスで、**このバージョンの発行**を選択して、アプリを共有しているすべてのユーザーにアプリを発行します。

   ![発行を確認する](./media/save-publish-app/publish-review.png)

   > [!NOTE]
   > キャンバス アプリを発行するたびに、アプリは最新バージョンの Power Apps 上で実行されるようにアップグレードされます。これは、ユーザーが最後に発行して以降、Microsoft が追加したすべての最新機能とパフォーマンスのアップグレードの利点を得ることができるということです。 数か月間、更新プログラムを発行していない場合、再発行からすぐにパフォーマンス上の利点を確認できるようになることが多いです。

## <a name="identify-the-live-version"></a>ライブ バージョンを指定する

[powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) では、**ファイル**メニュー (左端) の **アプリ**を選択し、アプリの詳細アイコンを選択して、**バージョン**タブを選択します。

**ライブ**バージョンは、アプリを共有しているすべてのユーザーに発行されます。 アプリの最新バージョンは、編集のアクセス許可を持つユーザーのみが入手できます。

![ポータルから発行する](./media/save-publish-app/publish-portal.png)

最新バージョンを公開するには、バージョンを強調表示して省略記号 (...) を選択します。次にドロップ ダウン メニューから**このバージョンを公開**を選択します。

## <a name="next-steps"></a>次の手順

* アプリを検索し、[ブラウザー](../../user/run-app-browser.md) または [電話](../../user/run-app-client.md) で実行します。
* powerapps.com から、[アプリ名の変更](set-name-tile.md) を行います。
* アプリに複数のバージョンがある場合、[アプリの復元](restore-an-app.md) を行います。
