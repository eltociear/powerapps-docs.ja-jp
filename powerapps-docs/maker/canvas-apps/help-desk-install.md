---
title: キャンバス アプリ用の Help Desk サンプルをインストールして構成する | Microsoft Docs
description: Power Apps でキャンバス アプリ用の Help Desk サンプルをインストールして構成する詳細な手順を示します。
author: matthewbolanos
manager: kvivek
ms.service: powerapps
ms.topic: sample
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/20/2020
ms.author: mabolan
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 3bfe3e9ba1c4f26b01fd267eef71c579a394ad46
ms.sourcegitcommit: f8a56fea78213fb5077240bbf27bc06b4719f32f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2020
ms.locfileid: "3495908"
---
# <a name="install-and-configure-the-help-desk-sample-in-power-apps"></a>Power Apps で Help Desk サンプルをインストールして構成する

Power Apps でキャンバス アプリ用の Help Desk サンプルをインストールして構成する詳細な手順を示します。

これらの手順を完了するための推定時間: **10 〜 15 分**。

> [!TIP]
> この手順のデモについては、こちらの[ビデオ](https://youtu.be/z4cdtD6hB_4) をご覧ください。

## <a name="overview-of-the-sample"></a>サンプルの概要

Help Desk は、使いやすいエクスペリエンスを提供し、エンド ユーザーとサポート担当者をつなぎます。 最も重要な質問への回答をすばやく見つけ、空きチケットの進行状況を追跡し、以前のリクエストの詳細を確認します。 このアプリをお使いの環境に合わせるには、少しの設定が必要です。

![Help Desk Tickets アプリの開始画面](./media/help-desk-install/login-screen.png)

> [!TIP]
> Help Desk Tickets サンプル アプリの使い方については、こちらの[ビデオ](https://youtu.be/sl5fXwwnvzI)をご覧ください。

## <a name="prerequisites"></a>前提条件

- Power Apps に[サインアップ](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)します。
- 有効な SharePoint Online ライセンスと、リストを作成するアクセス許可を持っている必要があります。

## <a name="create-the-helpdesk-sharepoint-list"></a>HelpDesk SharePoint リストを作成する

このリストは、Help Desk のチケットを格納します。

1. ブラウザーを開き、https://admin.microsoft.com にアクセスします。
2. SharePoint リストを作成するアクセス許可を持つアカウントでサイン インします。
3. HelpDesk リストを作成するサイト コレクションに移動します。
4. Web ページの右上にある**歯車アイコン**を選択します。
5. **アプリの追加**を選択します。
6. **アプリの検索**テキストボックスに、**カスタム**と入力します。
7. **検索アイコン**を選択します。
8. **カスタム リスト** アプリを選択します。
9. **名前** テキストボックスに、**HelpDesk** と入力します。

    > [!IMPORTANT]
    > リストに別の名前を使う場合は、書き留めておいてください。以降のインストールと構成のプロセスで、HelpDesk となっているすべての箇所を置き換える必要があります。

10. **作成**を選びます。

### <a name="create-description-column"></a>説明列を作成する

1. HelpDesk リストの横にある省略記号を選択して、**設定** を選択します。
2. **列の作成** を選択します。
3. 列名のテキストボックスに  **説明**と入力します。
4. **この列の情報の種類**ラジオ ボタン リストで、**複数行テキスト** を選択します。
5. **この列への情報の入力を必須にする**ラジオ ボタン リストで、**はい**を選択します。
6. **使用可能なテキストの種類を指定する**ラジオ ボタン リストで、**書式なしテキスト**を選択します。
7. **OK** を選択します。

### <a name="create-category-column"></a>カテゴリ列を作成する

1. **列の作成** を選択します。
2. 列名テキストボックスに**カテゴリ**と入力します。
3. **この列の情報の種類**ラジオ ボタン リストで、**選択肢**を選択します。
4. **それぞれの行に選択肢を入力する**のテキストボックスに、次の値をそれぞれ別の行に入力します。 
    - ラップトップ / PC 機器の問題
    - ラップトップ / PC ソフトウェアの問題
5. **固有の値を適用する**ラジオ ボタン リストで、**いいえ**を選択します。
6. **選択肢の表示形式**ラジオ ボタンのリストで、**ドロップ ダウン メニュー**を選択します。
7. **既定値**テキストボックスに、**ラップトップ / PC 機器の問題**と入力します。
8. **OK** を選択します。

### <a name="create-percentcomplete-column"></a>PercentComplete 列を作成する

1. **列の作成** を選択します。
2. 列名のテキストボックスに **PercentComplete** と入力します。
3. **この列の情報の種類**ラジオ ボタンのリストで、**数値 (1、10、100)** を選択します。
4. **この列への情報の入力を必須にする**ラジオ ボタン リストで、**いいえ**を選択します。
5. **OK** を選択します。

### <a name="create-priority-column"></a>優先度列を作成する

1. **列の作成** を選択します。
2. 列名のテキストボックスに **優先度**と入力します。
3. **この列の情報の種類**ラジオ ボタンのリストで、**選択肢**を選択します。
4. **それぞれの行に選択肢を入力する**のテキストボックスに、次の値をそれぞれ別の行に入力します。
    - 高
    - 中
    - 低
5. **固有の値を適用する**ラジオ ボタン リストで、**いいえ**を選択します。
6. **選択肢の表示形式**ラジオ ボタンのリストで、**ドロップ ダウン メニュー**を選択します。
7. **既定値**テキストボックスに、**低**と入力します。
8. **OK** を選択します。

### <a name="create-taskstatus-column"></a>TaskStatus 列を作成する

1. **列の作成** を選択します。
2. 列名のテキストボックスに **TaskStatus** と入力します。
3. **この列の情報の種類**ラジオ ボタン リストで、**選択肢**を選択します。
4. **それぞれの行に選択肢を入力する**のテキストボックスに、次の値をそれぞれ別の行に入力します。 
    - 開始前
    - 進行中
    - 完了
    - 遅延
    - CSR 待機中
5. **固有の値を適用する**ラジオ ボタン リストで、**いいえ**を選択します。
6. **選択肢の表示形式**ラジオ ボタンのリストで、**ドロップ ダウン メニュー**を選択します。
7. **既定値**テキストボックスに、**開始前**と入力します。
8. **OK** を選択します。

### <a name="create-assignedto-column"></a>AssignedTo 列を作成する

1. **列の作成** を選択します。
2. 列名のテキストボックスに **AssignedTo** と入力します。
3. **この列の情報の種類**ラジオ ボタン リストで、**ユーザーまたはグループ**を選択します。
4. **この列への情報の入力を必須にする**ラジオ ボタン リストで、**いいえ**を選択します。
5. **複数の選択を許可**ラジオ ボタン リストで、**いいえ**を選択します。
6. **OK** を選択します。

### <a name="edit-title-column"></a>「タイトル」列を編集する

1. **タイトル** 列のリンクを選択します。
2. **この列への情報の入力を必須にする**ラジオ ボタン リストで、**いいえ**を選択します。
3. **OK** を選択します。

## <a name="download-the-app"></a>アプリをダウンロードする

1.  Power Apps パッケージを[ダウンロード](https://pappsfeprodwestuscontent.blob.core.windows.net/sampleapps/helpdesk/docs/HelpDesk(SP_List).zip) して、お使いのコンピューターに保存します。

## <a name="create-connections"></a>接続を作成する

1.  [Power Apps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインします。
2.  サインアップに使用したものと同じ資格情報でサインインします。
3.  左側のメニューで、**データ**、**接続**の順に選択します。
    
### <a name="create-office-365-outlook-connection"></a>Office 365 Outlook 接続を作成する

1.  **+ 新規接続** を選択します。
2.  **検索**テキストボックスに、**Office 365 Outlook** と入力します。
3.  リストで **Office 365 Outlook** を選択します。
4.  **作成**を選びます。
5.  ポップアップ ウィンドウで、ログインに使ったアカウントを選択します。

### <a name="create-sharepoint-connection"></a>SharePoint 接続を作成する

1.  **+ 新規接続** を選択します。
2.  **検索**テキストボックスに、**SharePoint** と入力します。
3.  リストで **SharePoint** を選択します。
4.  **作成**を選びます。
5.  ポップアップ ウィンドウで、ログインに使ったアカウントを選択します。

### <a name="create-office-365-users-connection"></a>Office 365 ユーザー接続を作成する

1.  **+ 新規接続** を選択します。
2.  **検索**テキストボックスに、**Office 365 ユーザー**と入力します。
3.  リストで **Office 365 ユーザー**を選択します。
4.  **作成**を選びます。
5.  ポップアップ ウィンドウで、ログインに使ったアカウントを選択します。

## <a name="import-the-app"></a>アプリをインポートする

1. [Power Apps](https://make.powerapps.com) にサインインします。
2. サインアップに使用したものと同じ資格情報でサインインします。
3. 左側のメニューで**アプリ**を選択します。 
4. **インポート パッケージ (プレビュー)** を選択します。
    
   ![パッケージのインポートの画面](./media/help-desk-install/import-package.png)

5. **アップロード** ボタンを選択して、前述の手順でダウンロードしたパッケージを選びます。
6. **アプリ**および**フロー**のリソースの種類では、**インポート設定**を**新規作成**に設定します。
7. **SharePoint** および **Outlook** の接続では、**インポート設定**を**インポート時に選択する**に設定します。
    
   ![インポート設定画面](./media/help-desk-install/import-settings.png)

8. **SharePoint 接続**の**赤いアイコン**を選択します。
9. 接続の一覧で、自分のユーザー名の項目を選択します。

   ![インポート設定画面](./media/help-desk-install/import-settings-sharepoint.png)

10. **保存**を選択します。
11. **Office 365 Outlook 接続**の**赤いアイコン**を選択します。
12. 接続の一覧で、自分のユーザー名の項目を選択します。

    ![インポート設定画面](./media/help-desk-install/import-settings-office365outlook.png)

13. **保存**を選択します。

    > [!TIP] 
    > 完了すると次のようになります。

    ![インポート設定画面](./media/help-desk-install/import-settings-done.png)

14. **インポート** を選択して、プロセスが完了するまで待ちます。

    ![インポート設定画面](./media/help-desk-install/import-done.png)

## <a name="configure-the-app-to-use-the-sharepoint-list"></a>SharePoint リストを使用するようにアプリを構成する

1. 次の手順では、**アプリを開く** を選択します。
2. アクセスの許可を求められたら、**許可** を選択します。

    ![接続の許可](./media/help-desk-install/prompted-allow-connections.png)

### <a name="delete-connections"></a>接続の削除

1. **ビュー** タブで、**データ ソース**を選択します。

    ![データ ソースの表示](./media/help-desk-install/view-data-sources.png)
 
1. **データ** ウィンドウで、**HelpDesk** の隣の省略記号 (...) を選択してから、**削除**を選択します。

    ![SharePoint 接続を削除する](./media/help-desk-install/remove-sharepoint-connection.png)

### <a name="helpdesk-list"></a>HelpDesk リスト

1. **ビュー** タブで、**データ ソース**を選択します。
1. **データ** ウィンドウで、**データ ソースの追加**を選択します。
1. [上記手順で](#create-sharepoint-connection)作成した SharePoint 接続を選択します。

    ![SharePoint 接続を削除する](./media/help-desk-install/sharepoint-connection.png)

1. **最近利用したサイト**一覧で、HelpDesk リストを作成した SharePoint サイトを選びます。

    ![SharePoint  サイトの選択](./media/help-desk-install/select-sharepoint-site.png)

    > [!TIP]
    > サイトが一覧に表示されない場合は、テキスト ボックスに SharePoint サイトの URL を入力するか貼り付けて、**移動**を選択します。

1. **ヘルプデスク** の一覧を選択します。 検索ボックスを使用して**ヘルプデスク**と入力することで結果をフィルタ処理することもできます。

1. **HelpDesk** の隣のチェックボックスをオンにして、**接続**を選択します。

    ![ヘルプデスク の一覧を選択する](./media/help-desk-install/select-helpdesk-list.png)

### <a name="update-admin-list"></a>管理者一覧を更新する

1. ツリー ビューから**アプリ**を選択します。
2. 上部のドロップダウン プロパティ リストから **OnStart** を選択します。
3. 数式ウィンドウを展開して、**AdminList** コレクションを探します。
4. <strong>user@microsoft.com</strong> を HelpDesk 管理者に置換します。

    ![管理者一覧を更新する](./media/help-desk-install/change-admin.png)
    
   > [!TIP]
   > 管理者が複数いる場合は、コンマを使用して管理者のリストを区切ります。 例: "admin1@microsoft.com","admin2@microsoft.com"。
   > AdminList のアドレスが Power Apps で必要な形式と一致していることを確認するには、表示 > 変数 > グローバル > MyProfile の順に選択して、「メール」列のメール形式を調べます。

1. **ファイル** > **保存** > **公開** > **このバージョンを公開する**を選択し、アプリを[保存して公開](save-publish-app.md)します。

## <a name="modify-the-flow"></a>フローを変更する

1.  [Power Apps](https://make.powerapps.com) にサインインします。
1.  左側のウインドウで、**フロー** を選択します。

    ![フロー](./media/help-desk-install/flows.png)

4.  **HelpDeskFlow**フローの隣にある、鉛筆アイコンを選択してフローを編集します。
 
    ![フロー編集画面](./media/help-desk-install/edit-flow.png)

5.  **アイテムの取得**アクションを展開します。

    ![項目の取得を展開する](./media/help-desk-install/expand-get-items.png)
 
6.  作成した HelpDesk SharePoint リストと一致するように、**サイト アドレス**と**リスト名**を変更します。
    
    ![フロー編集画面](./media/help-desk-install/edit-flow-getitems.png)

1.  **それぞれに適用する**アクションを展開します。

    ![それぞれへの適用を展開する](./media/help-desk-install/expand-apply-to-each.png)

7.  **スイッチ**を展開します。

    ![スイッチを展開します](./media/help-desk-install/expand-switch.png)

8.  **開始前**ケースを展開します。
9.  **ケースが開始されていない場合の通知** アクションを展開します。

    ![ケースが開始されていない場合の通知を展開します](./media/help-desk-install/case-not-started-notification.png)

10. **宛先**を HelpDesk 管理者のメール アドレスに変更します。

    ![フロー編集画面](./media/help-desk-install/edit-flow-condition-send-email.png)

11. **保存** を選択して、フローの変更を保存します。

    ![フローを保存する](./media/help-desk-install/save-flow.png) 

## <a name="play-the-app"></a>アプリを再生する

1. [Power Apps](https://make.powerapps.com) にサインインします。
1. **ヘルプ デスク チケット**アプリを選択して再生します。

    ![アプリを再生する](./media/help-desk-install/play-app.png) 

> [!TIP]
> Help Desk Tickets サンプル アプリの使い方については、こちらの[ビデオ](https://youtu.be/sl5fXwwnvzI)をご覧ください。

## <a name="next-steps"></a>次の手順

- [キャンバス アプリを共有する](share-app.md)

### <a name="see-also"></a>関連項目

- [SharePoint リスト フォームのカスタマイズ](customize-list-form.md)
- [コントロールの追加と構成](add-configure-controls.md)
- [SharePoint リストまたはライブラリのアクセス許可の編集と管理](https://support.office.com/article/edit-and-manage-permissions-for-a-sharepoint-list-or-library-02d770f3-59eb-4910-a608-5f84cc297782)
