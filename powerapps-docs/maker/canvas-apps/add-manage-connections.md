---
title: キャンバス アプリからの接続を追加および管理する | Microsoft Docs
description: キャンバス アプリから、SharePoint、SQL Server、およびビジネス向け OneDrive などのデータ ソースへの接続を追加、削除、および更新する
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 02/05/2020
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9b25eef7460098139c32fba5606b682baae2ada9
ms.sourcegitcommit: d572c38a411e8588203d0909bc34c844ee508330
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2020
ms.locfileid: "3307764"
---
# <a name="manage-canvas-app-connections-in-power-apps"></a>Power Apps でキャンバス アプリの接続を管理する
[powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) で、1 つまたは複数のデータ ソースの接続を作成し、接続を削除し、または、その資格情報を更新します。

キャンバス アプリのデータ接続は、SharePoint、SQL Server、Office 365、ビジネス向け OneDrive、Salesforce、Excel、および他の多くの[データ ソース](connections-list.md) に接続できます。

この記事の後の次の手順では、以下の例のように、アプリでデータ ソースからのデータをアプリで表示および管理します。

* ビジネス向け OneDrive に接続し、アプリで Excel ワークブックのデータを管理します。
* SharePoint サイトのリストを更新します。
* SQL Server に接続し、アプリからテーブルを更新する。
* Office 365 で電子メールを送信する。
* ツイートを送信します。
* Twilio に接続し、アプリから SMS メッセージを送信する。

## <a name="prerequisites"></a>前提条件
1. Power Apps に[サインアップ](../signup-for-powerapps.md)します。
2. 新規登録に使用したのと同じ資格情報を使用して、[make.powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインします。

## <a name="background-on-data-connections"></a>データ接続のバックグラウンド
ほとんどの Power Apps アプリでは、クラウド サービスで格納されている**データ ソース**と呼ばれる外部情報を使用します。 一般的な例は、OneDrive for Business に格納されている Excel ファイル内のテーブルです。 アプリは、**接続**を使用してこれらのデータ ソースにアクセスできます。

最も一般的な種類のデータ ソースはテーブルで、情報の取得および格納に使用できます。 データ ソースへの接続を使用して、Microsoft Excel ブック、SharePoint リスト、SQL テーブル、および ビジネス向け OneDrive、DropBox、SQL Server などのようなクラウド サービスに格納できる他の多くの形式でデータの読み取りおよび書き込みを行うことができます。

メール、カレンダー、twitter、および通知などのテーブルではない他の種類のデータ ソースがあります。

**[Gallery](controls/control-gallery.md)**、**[Display form](controls/control-form-detail.md)**、**[Edit form](controls/control-form-detail.md)** コントロールを使用すると、データ ソースからデータを読み取りおよび書き込むアプリを簡単に作成できます。 始めに、[データ フォームについて](working-with-forms.md) の記事をお読みください。

[powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) で接続を作成および管理することに加えて、次のタスクを実行する場合にも接続を作成します。

* カスタム SharePoint リストなどの、[データからアプリ](app-from-sharepoint.md) を自動的に生成します。
* 既存のアプリを更新、または[接続を追加](add-data-connection.md) で説明されているように最初からアプリを作成します。
* 別のユーザーが作成しおよび[共有した](share-app.md) アプリを開きます。

> [!NOTE]
> 代わりに Power Apps Studio を使用する場合は、**ファイル**メニューを開き、次に**接続**をクリックまたはタップすると、[powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) が開き、そこで接続を作成および管理することができます。

## <a name="create-a-new-connection"></a>新しいつながりの作成
1. この操作を行っていない場合は、[make.powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にログインします。
2. 左側のナビゲーションで、**データ**を展開し、**接続**を選択します。
   
    ![接続の管理](./media/add-manage-connections/open-connections.png)
3. **新規接続** を選択します。
   
    ![接続の追加](./media/add-manage-connections/add-connection.png)
4. 表示されたリストからコネクタを選択して、次にプロンプトに従います。
   
   ![接続の追加](./media/add-manage-connections/choose-connection.png)
5. **作成**ボタンを選択します。
   
   ![接続の追加](./media/add-manage-connections/create-connection.png)
6. プロンプトに従います。 一部のコネクタでは、資格情報の入力、特定のデータ セットの指定、または他の手順の実行をするように要求します。 **Microsoft Translator** などのその他では、要求しません。
   
   たとえば、次のコネクタでは、使用する前に追加情報が必要です。
   
   * [SharePoint](connections/connection-sharepoint-online.md)
   * [SQL Server](connections/connection-azure-sqldatabase.md)

新しいコネクタが**接続**に表示され、[アプリに追加](add-data-connection.md) できます。

## <a name="update-or-delete-a-connection"></a>接続の更新または削除
接続の一覧で、更新または削除する接続を見つけ、次に接続の右側にある省略記号 (...) を選択します。

![更新を接続する](./media/add-manage-connections/auth-or-delete.png)

* 接続の資格情報を更新するには、キー アイコンを選択し、次にその接続の資格情報を入力します。
* 接続を削除するには、削除を選択します。
* 情報アイコンを選択して、接続の詳細を表示します。

