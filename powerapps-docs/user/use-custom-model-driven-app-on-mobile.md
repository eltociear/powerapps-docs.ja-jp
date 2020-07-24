---
title: モバイル デバイスでモデル駆動型アプリを使用する方法 | Microsoft Docs
description: モバイル デバイスでカスタムのモデル駆動型アプリを使用する方法について説明します。
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: quickstart
ms.date: 05/07/2020
ms.author: mkaur
ms.custom: ''
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: e2b401a2977a4c58fb7357de06e47019b2edf5ae
ms.sourcegitcommit: eda1684352baa7cb0f95119362177f3934a7bd4d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/28/2020
ms.locfileid: "3409926"
---
# <a name="user-guide-for-model-driven-apps-running-on-the-power-apps-mobile-app"></a>Power Apps モバイル アプリで動作するモデル駆動型アプリのユーザー ガイド

Power Apps モバイル アプリを使用すると、モバイル デバイスでモデル駆動型アプリを実行できます。 アプリをインストールして開始する方法について詳しくは、[モバイル デバイスでキャンバス アプリやモデル駆動型アプリを実行する](run-canvas-and-model-apps-on-mobile.md) をご覧ください。

> [!IMPORTANT]
> Dynamics 365 Sales、Dynamics 365 Customer Service、Dynamics 365 Field Service は、Power Apps モバイル アプリで実行しないでください。 代わりに、スマートフォンやタブレットのアプリに Dynamics 365 を使用します。 詳細情報については、[タブレット用の電話用 Dynamics 365 のユーザー ガイド](https://docs.microsoft.com/dynamics365/mobile-app/dynamics-365-phones-tablets-users-guide) を参照してください。

## <a name="home-screen"></a>ホーム画面 

Power Apps モバイル アプリの操作は簡単です。 次の図は、ホーム画面のプライマリ ナビゲーション要素を示しています。 

![ナビゲーション コントロール、展開されたビュー](media/home_screen_iphone.png "ナビゲーション コントロール、展開されたビュー")

凡例:

1. **サイト マップ**: メニューを開き、アプリ間を移動したり、お気に入りのレコードや最近使用したレコードにアクセスしたり、設定にアクセスしたりできます。
2. **検索**: Common Data Service でアプリ レコードを検索します。
3. **新規**: 新しいレコードを作成し、ほぼすべての種類の情報をシステムにすばやく入力できます。
4. **リレーションシップ アシスタント**: アシスタントを使用して、毎日のアクションと通信を監視および追跡します。 これは、アプリ全体で目立つように表示され、調整されたアクションにつながる分析情報が提供される分析情報カードと共に、毎日の作業をうまくこなすのに役立ちます。

## <a name="site-map"></a>サイト マップ 

ホーム画面で、サイト マップ ![サイト マップ アイコン](media/pa_mobile_sitemap_icon.png "サイト マップ アイコン") を選択すると、エンティティ、お気に入りのレコードや最もよく使用するレコード、他のアプリ、設定にアクセスできます。

 
   > [!div class="mx-imgBorder"]
   > ![サイト マップ スクリーン](media/go_to_sitemap_iphone.gif "この画像は、サイト マップ画面を表示する方法を示しています")
   


次の図は、サイト マップ スクリーンのプライマリ ナビゲーション要素を示しています。 

![サイト マップ スクリーン](media/site_map_iphone.png "サイト マップ スクリーン")

凡例

1. **アプリ セレクター**: このメニューを開いて、アプリを終了し、別のアプリに切り替えます。
2. **ホーム画面**: これを選択して、ホーム画面に戻ります。
3. **プロファイル**: プロファイル画面にアクセスして、サインアウトするか、アプリを再構成します。 
4. **最近表示したレコード**: 最近使用したレコードの一覧を表示します。 
5. **ピン留めされたレコード**: お気に入りの (ピン止めされた) レコードを表示し、開きます。 
6. **エンティティ ナビゲータ**: この領域には、アプリで使用可能なエンティティが一覧表示されます。
7. **ヘルプ**: Power Apps モバイル アプリの使用方法の詳細については、ヘルプ コンテンツをご覧ください。
8. **オフライン状態**: インターネットにアクセスできない場合でも、オフライン モードでデータを操作できます。 詳細: [モバイル デバイスでオフラインの作業をする](https://docs.microsoft.com/dynamics365/mobile-app/work-in-offline-mode)
9. **設定**: アクセス設定。

## <a name="pin-favorite-records"></a>お気に入りのレコードをピン留めする

**ピン留め済み** と **最近使ったアイテム** の一覧から、最近使ったレコードやお気に入りにピン留めしたレコードにすばやくアクセスできます。 お気に入りのレコードをピン留めするには、**最近使ったアイテム** の一覧を使用します。  

1. サイトマップ ![サイト マップ アイコン](media/pa_mobile_sitemap_icon.png "サイト マップ アイコン")で、**最近使ったレコード** ![最近使ったレコード アイコン](media/pa_mobile_recent_icon.png "最近使用したレコード アイコン") を選択します。

2. **最近使ったアイテム** レコード スクリーンで、レコードの横にあるプッシュピン アイコンを選択して、お気に入り (ピン留めしたレコード) に追加します。

3. 新しくピン留めしたレコードを表示するには、![[戻る] アイコン](media/mobile_go_back_icon.png "戻るアイコン") を選択してから、**ピン留め済み** ![ピン留めしたお気に入りアイコン](media/mobile_pinned_favs_icon.png "ピン留めしたお気に入りアイコン") を選択します。

   
   > [!div class="mx-imgBorder"]
   > ![レコードをお気に入りにピン留めする](media/pin_to_fav.gif "この画像は、お気に入りのレコードをピン留めする方法を示しています")
   

### <a name="unpin-a-record"></a>レコードのピン留めを外す

1. サイト マップ ![サイト マップ アイコン](media/pa_mobile_sitemap_icon.png "サイト マップ アイコン")で、**ピン留め済み** ![ピン留めしたお気に入りアイコン](media/mobile_pinned_favs_icon.png "ピン留めしたお気に入りアイコン") を選択します。

2. レコードの横にあるピンを削除するアイコン ![ピンの削除アイコン](media/pa_mobile_remove_pin_icon.png "ピンの削除アイコン") を選択して、お気に入り (ピン留めしたレコード) から削除します。


   > [!div class="mx-imgBorder"]
   > ![レコードのピン留めを外す](media/unpin_favs.gif "この画像では、レコードのピン留めを外す方法を示しています")
   

## <a name="change-views"></a>ビューを変更する

- ホーム画面で、現在のビューの横にある下矢印 ![ビューの変更アイコン](media/mobile_view_selector_icon.png "ビューの変更アイコン") を選択してから、新しいビューを選択します。


   > [!div class="mx-imgBorder"]
   > ![ビューを変更する](media/change_views_iphone.gif "この画像では、別のビューを選択する方法を示しています")


## <a name="add-a-record-quickly"></a>レコードをすばやく追加する

1. ホーム画面で、**新規作成** ![レコードの作成ボタン](media/create-record-button.png "レコードの作成ボタン") を選択します。
2. フィールドに入力し、**保存**を選択します。
3. レコードが作成されたら、新しいレコードを表示できます。 

   > [!div class="mx-imgBorder"]
   > ![レコードを作成する](media/pamobile_add_record_1.gif "この画像では、新しいレコードを作成する方法を示しています")


-  作成したレコードを保存して開くには、**その他** ![その他のコマンド アイコン](media/pa_mobile_more_commands_icon.png "その他のコマンド アイコン") を選択してから、**保存して開く** を選択します。

- 保存して別のレコードを作成するには、**その他** ![その他のコマンド アイコン](media/pa_mobile_more_commands_icon.png "そのほかのコマンド アイコン") を選択してから、**保存して新規作成** を選択します。


   > [!div class="mx-imgBorder"]
   > ![レコードを作成する](media/pa_mobile_save_create_new.gif "この画像では、レコードを保存して開いたり、新しいレコードの保存や作成を行う方法を示しています")


## <a name="view-commands-for-a-record-android"></a>レコードのコマンドを表示する (Android)

1. ホーム画面で、レコードを開きます。
2. 開いているレコードで、**その他** ![その他のレコード コマンド アイコン](media/access_record_commands_icon.png "その他のレコード コマンド アイコン") を選択して、その他のコマンドにアクセスします。


   > [!div class="mx-imgBorder"]
   > ![レコードのコマンド](media/pa_mobile_view_record_commands.gif "この画像では、レコードのその他のコマンドにアクセスする方法を示しています")


## <a name="edit-a-record"></a>レコードを編集する

1. ホーム画面で、編集するレコードを開きます。 
2. レコードの編集が完了したら、**保存** を選択します。 変更をキャンセルするには、**破棄** を選択します。


   > [!div class="mx-imgBorder"]
   > ![レコードを編集する](media/save_on_iphone.gif "この画像では、レコードを編集して保存する方法を示しています")



## <a name="go-back-to-the-home-screen"></a>ホーム画面に戻る

- レコードを使用しているときにホーム画面に戻るには、**戻る** ![戻るアイコン](media/pa_mobile_back_icon.png "戻るアイコン") を選択します。
- どの時点でも、**戻る** ![戻るアイコン](media/pa_mobile_back_icon.png "戻るアイコン") を長押しすると、ホーム画面に戻ることができます。 

   > [!div class="mx-imgBorder"]
   > ![ホーム画面に戻る](media/go_back_home.gif "この画像では、戻るアイコンを押しながらホーム画面に戻る方法を示しています")


## <a name="sign-out"></a>サインアウト

サイト マップ ![サイト マップ アイコン](media/pa_mobile_sitemap_icon.png "サイト マップ アイコン")で、プロファイル アイコン ![プロファイル アイコン](media/profile_icon.png "サイト マップ アイコン") を選択してから、**サインアウト** を選択します。
