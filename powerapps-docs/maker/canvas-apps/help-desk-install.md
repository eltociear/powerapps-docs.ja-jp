---
title: キャンバス アプリ用の Help Desk サンプルをインストールして構成する | Microsoft Docs
description: Power Apps でキャンバス アプリ用の Help Desk サンプルをインストールして構成する詳細な手順を示します。
author: matthewbolanos
manager: kvivek
ms.service: powerapps
ms.topic: sample
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 01/15/2020
ms.author: mabolan
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 4eafe6aaafb2fe461a98212a64d3858ebf5f5f0f
ms.sourcegitcommit: 1c4ab1859febccf79a835bd2f168e7e12a953a18
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2020
ms.locfileid: "3307557"
---
# <a name="install-and-configure-the-help-desk-sample-in-power-apps"></a>Power Apps で Help Desk サンプルをインストールして構成する

Power Apps でキャンバス アプリ用の Help Desk サンプルをインストールして構成する詳細な手順を示します。

これらの手順を完了するための推定時間: **10 〜 15 分**。

> [!TIP]
> この手順のデモについては、こちらの[ビデオ](https://youtu.be/z4cdtD6hB_4) をご覧ください。

## <a name="overview-of-the-sample"></a>サンプルの概要

Help Desk は、使いやすいエクスペリエンスを提供し、エンド ユーザーとサポート担当者をつなぎます。 最も重要な質問への回答をすばやく見つけ、空きチケットの進行状況を追跡し、以前のリクエストの詳細を確認します。 このアプリをお使いの環境に合わせるには、少しの設定が必要です。

![Help Desk PowerApp の開始画面](./media/help-desk-install/Login-screen.png)

> [!TIP]
> Help Desk PowerApp サンプルの使い方については、こちらの[ビデオ](https://youtu.be/sl5fXwwnvzI) をご覧ください。

## <a name="prerequisites"></a>前提条件

- Power Apps に[サインアップ](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)します。
- 有効な SharePoint Online ライセンスと、リストを作成するアクセス許可を持っている必要があります。

## <a name="create-the-helpdesk-sharepoint-list"></a>HelpDesk SharePoint リストを作成する

このリストは、Help Desk のチケットを格納します。

1. Web ブラウザーを開いて、https://admin.microsoft.com に移動します。
2. SharePoint リストを作成するアクセス許可を持つアカウントでログインします。
3. HelpDesk リストを作成するサイト コレクションに移動します。
4. Web ページの右上にある**歯車アイコン**をクリックします。
5. **アプリの追加**をクリックします。
6. **アプリの検索**テキストボックスに、**カスタム**と入力します。
7. **検索アイコン**をクリックします。
8. **カスタム リスト**アプリをクリックします。
9. **名前** テキストボックスに、**HelpDesk** と入力します。

    > [!IMPORTANT]
    > リストに別の名前を使う場合は、書き留めておいてください。以降のインストールと構成のプロセスで、HelpDesk となっているすべての箇所を置き換える必要があります。

10. **作成** をクリックします。

### <a name="create-description-column"></a>説明列を作成する

1. HelpDesk リストの横にある省略記号を選択して、**設定**をクリックします。
2. **列の作成**をクリックします。
3. **列名**テキストボックスに**説明**と入力します。
4. **この列の情報の種類**ラジオ ボタン リストで、**複数行テキスト** を選択します。
5. **この列への情報の入力を必須にする**ラジオ ボタン リストで、**はい**を選択します。
6. **使用可能なテキストの種類を指定する**ラジオ ボタン リストで、**書式なしテキスト**を選択します。
7. **OK** をクリックします。

### <a name="create-category-column"></a>カテゴリ列を作成する

1. **列の作成**をクリックします。
2. **列名**テキストボックスに**カテゴリ**と入力します。
3. **この列の情報の種類**ラジオ ボタン リストで、**選択肢**を選択します。
4. **それぞれの行に選択肢を入力する**のテキストボックスに、次の値をそれぞれ別の行に入力します。 
    - ラップトップ / PC 機器の問題
    - ラップトップ / PC ソフトウェアの問題
5. **固有の値を適用する**ラジオ ボタン リストで、**いいえ**を選択します。
6. **選択肢の表示形式**ラジオ ボタン リストで、**ドロップダウン メニュー**を選択します。
7. **既定値**テキストボックスに、**ラップトップ / PC 機器の問題**と入力します。
8. **OK** をクリックします。

### <a name="create-percentcomplete-column"></a>PercentComplete 列を作成する

1. **列の作成**をクリックします。
2. **列名**テキストボックスに **PercentComplete** と入力します。
3. **この列の情報の種類**ラジオ ボタン リストで、**数値 (1、10、100)** を選択します。
4. **この列への情報の入力を必須にする**ラジオ ボタン リストで、**いいえ**を選択します。
5. **OK** をクリックします。

### <a name="create-priority-column"></a>優先度列を作成する

1. **列の作成**をクリックします。
2. **列名**テキストボックスに**優先度**と入力します。
3. **この列の情報の種類**ラジオ ボタン リストで、**選択肢**を選択します。
4. **それぞれの行に選択肢を入力する**のテキストボックスに、次の値をそれぞれ別の行に入力します。 
    - 高
    - 中
    - 低
5. **固有の値を適用する**ラジオ ボタン リストで、**いいえ**を選択します。
6. **選択肢の表示形式**ラジオ ボタン リストで、**ドロップダウン メニュー**を選択します。
7. **既定値**テキストボックスに、**低**と入力します。
8. **OK** をクリックします。

### <a name="create-taskstatus-column"></a>TaskStatus 列を作成する

1. **列の作成**をクリックします。
2. **列名**テキストボックスに **TaskStatus** と入力します。
3. **この列の情報の種類**ラジオ ボタン リストで、**選択肢**を選択します。
4. **それぞれの行に選択肢を入力する**のテキストボックスに、次の値をそれぞれ別の行に入力します。 
    - 開始前
    - 進行中
    - 完了
    - 遅延
    - CSR 待機中
5. **固有の値を適用する**ラジオ ボタン リストで、**いいえ**を選択します。
6. **選択肢の表示形式**ラジオ ボタン リストで、**ドロップダウン メニュー**を選択します。
7. **既定値**テキストボックスに、**開始前**と入力します。
8. **OK** をクリックします。

### <a name="create-assignedto-column"></a>AssignedTo 列を作成する

1. **列の作成**をクリックします。
2. **列名**テキストボックスに **AssignedTo** と入力します。
3. **この列の情報の種類**ラジオ ボタン リストで、**ユーザーまたはグループ**を選択します。
4. **この列への情報の入力を必須にする**ラジオ ボタン リストで、**いいえ**を選択します。
5. **複数の選択を許可**ラジオ ボタン リストで、**いいえ**を選択します。
6. **OK** をクリックします。

### <a name="edit-title-column"></a>「タイトル」列を編集する

1. **タイトル**列のリンクをクリックします。
2. **この列への情報の入力を必須にする**ラジオ ボタン リストで、**いいえ**を選択します。
3. **OK** をクリックします。

## <a name="download-the-app"></a>アプリをダウンロードする

1.  Power Apps パッケージを[ダウンロード](https://pappsfeprodwestuscontent.blob.core.windows.net/sampleapps/helpdesk/docs/HelpDesk(SP_List).zip) して、お使いのコンピューターに保存します。

## <a name="create-connections"></a>接続を作成する

1.  Web ブラウザーで [make.powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) に移動します。
2.  サインアップに使用したものと同じ資格情報でサインインします。
3.  左側のメニューで、**データ**、**接続**の順に選択します。
    
### <a name="create-office-365-outlook-connection"></a>Office 365 Outlook 接続を作成する

1.  **+ 新しい接続**をクリックします。
2.  **検索**テキストボックスに、**Office 365 Outlook** と入力します。
3.  リストで **Office 365 Outlook** を選択します。
4.  **作成** をクリックします。
5.  ポップアップ ウィンドウで、ログインに使ったアカウントを選択します。

### <a name="create-sharepoint-connection"></a>SharePoint 接続を作成する

1.  **+ 新しい接続**をクリックします。
2.  **検索**テキストボックスに、**SharePoint** と入力します。
3.  リストで **SharePoint** を選択します。
4.  **作成** をクリックします。
5.  ポップアップ ウィンドウで、ログインに使ったアカウントを選択します。

### <a name="create-office-365-users-connection"></a>Office 365 ユーザー接続を作成する

1.  **+ 新しい接続**をクリックします。
2.  **検索**テキストボックスに、**Office 365 ユーザー**と入力します。
3.  リストで **Office 365 ユーザー**を選択します。
4.  **作成** をクリックします。
5.  ポップアップ ウィンドウで、ログインに使ったアカウントを選択します。

## <a name="import-the-app"></a>アプリをインポートする

1. Web ブラウザーで、https://make.powerapps.com に移動します。
2. サインアップに使用したものと同じ資格情報でサインインします。
3. 左側のメニューで**アプリ**を選択します。 
4. **パッケージのインポート (プレビュー)** をクリックします。
    
   ![パッケージのインポートの画面](./media/help-desk-install/import-package.png)

5. **アップロード** ボタンをクリックして、前の手順でダウンロードした PowerApp パッケージを選択します。
6. **アプリ**および**フロー**のリソースの種類では、**インポート設定**を**新規作成**に設定します。
7. **SharePoint** および **Outlook** の接続では、**インポート設定**を**インポート時に選択する**に設定します。
    
   ![インポート設定画面](./media/help-desk-install/import-settings.png)

8. **SharePoint** 接続の**赤いアイコン**をクリックします。
9. 接続の一覧で、自分のユーザー名の項目をクリックします。

   ![インポート設定画面](./media/help-desk-install/import-settings-sharepoint.png)

10. **保存**をクリックします。
11. **Office 365** Outlook 接続の**赤いアイコン**をクリックします。
12. 接続の一覧で、自分のユーザー名の項目をクリックします。

    ![インポート設定画面](./media/help-desk-install/import-settings-office365outlook.png)

13. **保存**をクリックします。

    > [!TIP] 
    > 完了すると次のようになります。

    ![インポート設定画面](./media/help-desk-install/import-settings-done.png)

14. **インポート**をクリックして、プロセスが完了するまで待ちます。

    ![インポート設定画面](./media/help-desk-install/import-done.png)

## <a name="configure-the-app-to-use-the-sharepoint-list"></a>SharePoint リストを使用するようにアプリを構成する

1. 次の手順で、**アプリを開く**をクリックします。
2. アクセス許可を求められたら、**許可**をクリックします。

### <a name="delete-connections"></a>接続の削除

1. **ビュー** タブで、**データ ソース**を選択します。
1. **データ** ウィンドウで、**HelpDesk** の隣の省略記号 (...) を選択してから、**削除**を選択します。

### <a name="helpdesk-list"></a>HelpDesk リスト

1. **ビュー** タブで、**データ ソース**を選択します。
1. **データ** ウィンドウで、**データ ソースの追加** > **新しい接続** > **SharePoint** > **作成** を選択します。
1. **最近利用したサイト**一覧で、HelpDesk リストを作成した SharePoint サイトを選びます。

    > [!TIP] 
    > サイトが一覧に表示されない場合は、テキスト ボックスに SharePoint サイトの URL を入力するか貼り付けて、**移動**を選択します。

1. 一覧の先頭にある**検索**ボックスに、**HelpDesk** と入力するか貼り付けます。
1. **HelpDesk** の隣のチェックボックスをオンにして、**接続**を選択します。

### <a name="update-admin-list"></a>管理者一覧を更新する

1. **アプリ**を選択します。
2. ドロップダウンで **OnStart** を選択します。
3. 数式ウィンドウを展開して、**AdminList** コレクションを探します。
4. <strong>user@microsoft.com</strong> を HelpDesk 管理者に置換します。

    ![管理者一覧を更新する](./media/help-desk-install/Change-admin.png)
    
   > [!TIP]
   > 管理者が複数いる場合は、コンマを使用して管理者のリストを区切ります。 例: "admin1@microsoft.com","admin2@microsoft.com"。
   > AdminList のアドレスが Power Apps で必要な形式と一致していることを確認するには、表示 > 変数 > グローバル > MyProfile の順に選択して、「メール」列のメール形式を調べます。

1. **ファイル** > **保存** > **発行** > **このバージョンの発行**の順に選択します。

## <a name="modify-the-flow"></a>フローを変更する

1.  左側のメニューで、**フロー**をクリックします。
2.  サインインを求められたら、サインアップに使用したものと同じ資格情報でサインインします。
3.  上部のメニューで、**マイ フロー**を選択します。
4.  **HelpDeskFlow** フローの隣の鉛筆アイコンをクリックします。 
 
    ![フロー編集画面](./media/help-desk-install/edit-flow.png)

5.  **アイテムの取得**アクションを展開します。 
6.  作成した HelpDesk SharePoint リストと一致するように、**サイト アドレス**と**リスト名**を変更します。
    
    ![フロー編集画面](./media/help-desk-install/edit-flow-getitems.png)

    > [!TIP] 
    > 手入力する必要はありません。ドロップダウン リストで選択できます。

7.  **切り替え**を展開します。
8.  **開始前**ケースを展開します。
9.  **開始前のケース** アクションを展開します。
10. **宛先**を HelpDesk 管理者のメール アドレスに変更します。

    ![フロー編集画面](./media/help-desk-install/edit-flow-condition-send-email.png) 

11. **フローの更新**をクリックします。

## <a name="play-the-app"></a>アプリを再生する

1. Web ブラウザーで**アプリ**をクリックします。
2. HelpDesk アプリの隣の省略記号 (...) をクリックします。
3. **開く** をクリックします。 

> [!TIP]
> Help Desk PowerApp サンプルの使い方については、こちらの[ビデオ](https://youtu.be/sl5fXwwnvzI) をご覧ください。

## <a name="next-steps"></a>次の手順
- [SharePoint リスト フォームのカスタマイズ](https://docs.microsoft.com/powerapps/maker/canvas-apps/customize-list-form)
- [コントロールの追加と構成](https://docs.microsoft.com/powerapps/maker/canvas-apps/add-configure-controls)
- [SharePoint リストまたはライブラリのアクセス許可の編集と管理](https://support.office.com/article/edit-and-manage-permissions-for-a-sharepoint-list-or-library-02d770f3-59eb-4910-a608-5f84cc297782)
