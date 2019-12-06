---
title: キャンバス ベースのアプリをモバイル デバイス上で実行する | Microsoft Docs
description: キャンバス アプリをモバイル デバイス上で実行する方法について説明します。
author: Mattp123
ms.service: powerapps
ms.component: pa-user
ms.topic: quickstart
ms.date: 11/16/2018
ms.author: matp
ms.custom: ''
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: ad34f7daacf07ebc8ecde2a8ce29c163d0c28e95
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74733340"
---
# <a name="run-a-canvas-app-on-a-mobile-device"></a>キャンバス アプリをモバイル デバイス上で実行する
自分でアプリを作成したり、他のユーザーからアプリの共有を受けたりしたときは、Windows、iOS、Android、または Web ブラウザーでアプリを実行できます。 このトピックでは、モバイル デバイス上でキャンバス アプリを実行する方法について説明します。 モバイル デバイスで実行されるアプリでは、位置情報サービスやカメラなどのデバイス機能を活用できます。

この手順を実行するには、Power Apps にサインアップしていない場合は、開始する前に[無料でサインアップ](https://make.powerapps.com/signup?redirect=marketing&email=)し、 [App Store](https://itunes.apple.com/app/powerapps/id1047318566?mt=8)から power apps をダウンロードするか、[サポートされているオペレーティングシステム](../maker/canvas-apps/limits-and-config.md)を実行している IPhone、iPad、または Android デバイスに[Google Play](https://play.google.com/store/apps/details?id=com.microsoft.msapps)します。 自分で作成したキャンバス アプリ、または他のユーザーが作成して共有されたキャンバス アプリにアクセスできることも確認してください。

## <a name="open-power-apps-and-sign-in"></a>Power Apps を開き、サインインする
モバイルデバイスで Power Apps を開き、Azure Active Directory の資格情報を使用してサインインします。

![ユーザーのログイン](./media/run-app-client/run-client-login.png)

モバイル デバイスに Microsoft Authenticator アプリがインストールされている場合は、メッセージが表示されたらユーザー名を入力し、デバイスに送信される通知を承認するだけです。

## <a name="find-the-app"></a>アプリを見つける
アプリを見つけやすくするには、**PowerApps** メニューを開き、フィルターを選びます。

![アプリのフィルター](./media/run-app-client/filter-menu.png)

次のフィルターを使用できます。

* **[すべてのアプリ]** : 自分が作成したアプリ、他のユーザーが共有したアプリなど、アクセスできるすべてのアプリが表示されます。

* **[マイ アプリ]** : 少なくとも 1 回実行したことのあるアプリが表示されます。

* **[サンプル アプリ]** : 設計の可能性を調査できるように、架空のデータを使って実際のアプリケーションのシナリオが紹介されている、Microsoft からのサンプル アプリが表示されます。

* **[お気に入り]** : アプリ タイルで省略記号 [...] をタップしてから **[お気に入り]** をタップするとマークしたアプリが表示されます。 この一覧からアプリを削除するには、アプリ タイルの省略記号 [...] をタップして、 **[お気に入りから外す]** をタップします。

    ![お気に入りとしてマークする](./media/run-app-client/favorite.png)

アプリをフィルター処理した後は、フィルター処理された一覧を、アプリが最後に開かれたり変更されたりした日付順、または名前のアルファベット順に並べ替えることができます。 これらの設定は、Power Apps を閉じて再度開いたときに保持されます。

![並べ替えメニュー](./media/run-app-client/sort-menu.png)

実行するアプリの名前がわかっている場合は、PowerApps の上部にある検索アイコンをタップして、検索ボックスに名前の一部を入力します。

![Search](./media/run-app-client/search.png)

アプリをフィルター処理した場合は、フィルター処理された一覧が検索されます。

## <a name="run-an-app"></a>アプリを実行する
モバイル デバイスでキャンバス アプリを実行するには、アプリ タイルをタップします。 他のユーザーが作成したキャンバス アプリをメールで共有されている場合は、メールのリンクをタップして、アプリを実行できます。

Power Apps を初めて使用する場合、画面には、アプリを閉じるためのスワイプジェスチャが表示されます。

![アプリの起動](./media/run-app-client/run-client-app.png)

## <a name="give-consent"></a>同意
アプリでデータ ソースへの接続またはデバイスの機能 (カメラや位置情報サービスなど) を使うためのアクセス許可が必要な場合は、アプリを使う前に同意する必要があります。 通常、このことが求められるのは初回のみです。

![Connection](./media/run-app-client/app-connection.png)

## <a name="pin-an-app-to-the-home-screen"></a>ホーム画面へのアプリのピン留め
すばやくアクセスできるように、デバイスのホーム画面にアプリをピン留めすることができます。 アプリ タイルの省略記号 [...] をタップし、 **[ホームにピン留め]** をタップして、表示される指示に従います。

![アプリのピン留め](./media/run-app-client/run-client-pin.png)

## <a name="close-an-app"></a>アプリを閉じる
アプリを閉じるには、アプリの左端から右に向かって指でスワイプします。 Android デバイスでは、[戻る] ボタンを押してから、アプリを閉じることを確認してもかまいません。

## <a name="next-steps"></a>次の手順
このトピックでは、モバイル デバイス上でキャンバス アプリを実行する方法について説明しました。 モバイル デバイスでモデル駆動型アプリを実行することもできます。

> [!div class="nextstepaction"]
> [モバイル デバイスでモデル駆動型アプリを実行する](run-app-client-model-driven.md)
