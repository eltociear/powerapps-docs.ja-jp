---
title: Oracle データベースへの接続 | Microsoft Docs
description: PowerApps で Oracle データベースに接続し、このデータベースを利用してアプリを作成する方法について説明します。
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/14/2017
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 31bf18342de1191dbd816093186fe33e31755232
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2019
ms.locfileid: "74678743"
---
# <a name="connect-to-an-oracle-database-from-powerapps"></a>PowerApps から Oracle データベースへの接続
接続を作成し、Power Apps でアプリを構築した後、Oracle データベースでテーブルを一覧表示したり、テーブル行を作成、読み取り、更新、削除したりします。 Oracle データベースへの接続では、フィルター処理や並び替えなど、トリガーとストアド プロシージャを除く機能の完全委任がサポートされています。

## <a name="prerequisites"></a>前提条件
* Oracle 9 以降
* Oracle クライアント ソフトウェア 8.1.7 以降
* オンプレミス データ ゲートウェイのインストール
* Oracle クライアント SDK のインストール

### <a name="install-an-on-premises-data-gateway"></a>オンプレミス データ ゲートウェイをインストールする
ゲートウェイをインストールするには、[こちらのチュートリアル](../gateway-management.md)の手順に従います。

オンプレミスデータゲートウェイはブリッジとして機能し、オンプレミスのデータ (クラウドにないデータ) と、Power BI、電力の自動化、Logic Apps、および Power Apps のサービスの間で、迅速かつ安全なデータ転送を提供します。 複数のサービスやデータ ソースで、同一のゲートウェイを使用できます。 詳細については、[ゲートウェイの概要](../gateway-reference.md)に関する記事を参照してください。

### <a name="install-oracle-client"></a>Oracle クライアントをインストールする
オンプレミス データ ゲートウェイと同じコンピューターに、[64-bit ODAC 12c Release 4 (12.1.0.2.4) for Windows x64](https://www.oracle.com/technetwork/database/windows/downloads/index-090165.html) をインストールします。 このインストールを行わないと、既知の問題の一覧で説明しているように、接続の作成時または使用時にエラーが発生します。

## <a name="create-an-app-from-a-table-in-an-oracle-database"></a>Oracle データベースのテーブルからアプリを作成する
1. Power Apps Studio で、 **[ファイル]** メニュー (左端近く) の **[新規]** をクリックまたはタップします。
   
   ![[新規] オプション](./media/connection-oracledb/new-app.png)
2. **[データを使用して開始]** の下にある矢印をクリックまたはタップします。
   
      既にある接続の一覧が表示されます。
3. **[新しい接続]** をクリックまたはタップします。
   
   ![新しい接続](./media/connection-oracledb/new-connection.png)
4. 接続の一覧で **[Oracle Database]** をクリックまたはタップします。
   
   ![新規データベース](./media/connection-oracledb/oracle-db.png)
5. Oracle サーバーの名前と、ユーザー名およびパスワードを指定します。
   
    SID が必要な場合は、次の形式でサーバーを指定します。<br>
    *ServerName*/*SID*
   
   ![接続パラメーター](./media/connection-oracledb/connection-params.png)
6. 使用するゲートウェイをクリックまたはタップするか、ゲートウェイをインストールします。
   
    インストール後にゲートウェイが表示されない場合は、 **[ゲートウェイ一覧を最新の情報に更新]** をクリックします。
   
   ![新規ゲートウェイ](./media/connection-oracledb/choose-gateway.png)
7. **[作成]** をクリックまたはタップして接続を作成します。
   
   ![新規](./media/connection-oracledb/create-button.png)
8. **[既定]** データセットをクリックまたはタップします。
   
   ![新規](./media/connection-oracledb/choose-dataset.png)
9. テーブルの一覧で、使用するテーブルをクリックまたはタップします。
   
   ![新規](./media/connection-oracledb/choose-table.png)
10. **[接続]** をクリックしてアプリを作成します。
    
    ![新規](./media/connection-oracledb/connect-button.png)

Power Apps は、3つの画面を含むアプリを作成し、選択したテーブルのデータを表示します。

* **BrowseScreen1** には、テーブルに含まれるすべてのエントリが一覧表示されます。
* **DetailScreen1** には、1 つのエントリに関する詳細が表示されます。
* **EditScreen1** では、ユーザーがエントリの更新または作成を行うことができます。

![新規](./media/connection-oracledb/afd-app.png)

## <a name="next-steps"></a>次の手順
* 生成したアプリを保存するには、Ctrl+S キーを押します。
* 既定で表示される **BrowseScreen1** のカスタマイズ方法については、[レイアウトのカスタマイズ](../customize-layout-sharepoint.md)に関するページを参照してください。
* **DetailsScreen1** または **EditScreen1** のカスタマイズ方法については、[フォームのカスタマイズ](../customize-forms-sharepoint.md)に関するページを参照してください。

## <a name="known-issues-tips-and-troubleshooting"></a>既知の問題、ヒント、およびトラブルシューティング
1. ゲートウェイに到達できません。
   
    このエラーは、オンプレミス データ ゲートウェイがクラウドへ接続できない場合に表示されます。 ゲートウェイの状態を確認するには、powerapps.microsoft.com にサインインして **[ゲートウェイ]** をクリックまたはタップし、使用するゲートウェイをクリックまたはタップします。
   
    ゲートウェイが実行中でありインターネットに接続可能であることを確認してください。 電源がオフになっているかスリープ状態のコンピューターには、ゲートウェイをインストールしないでください。 また、オンプレミス データ ゲートウェイ サービス (PBIEgwService) を再起動してみてください。
2. System.Data.OracleClient には Oracle クライアント ソフトウェア version 8.1.7 以降が必要です。
   
    このエラーは、オンプレミス データ ゲートウェイと同じコンピューターに Oracle クライアント SDK がインストールされていない場合に表示されます。 この問題を解決するには、[正式なプロバイダーをインストールしてください](https://go.microsoft.com/fwlink/p/?LinkID=272376)
3. テーブル '[Tablename]' には、キー列が定義されていません。
   
    このエラーは、Oracle データベースへの接続に必要な主キーが設定されていないテーブルへ接続しようとすると表示されます。
4. 執筆時点では、ストアド プロシージャ、複合キーの設定されたテーブル、テーブル内で入れ子になったオブジェクト型はサポートされていません。

