---
title: Oracle データベースへの接続 | Microsoft Docs
description: Oracle データベースに接続し、Power Apps でアプリを構築するためにそれを使用する方法について説明します。
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 01/29/2020
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b60ab00d4f4fecca7ead1cac629e0e34f26f302b
ms.sourcegitcommit: d0f02fdaa125feaea884932e1ef31b8fea1bd10c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2020
ms.locfileid: "3307718"
---
# <a name="connect-to-an-oracle-database-from-power-apps"></a>Power Apps から Oracle データベースへの接続
List tables, and create, read, update and delete table rows in an Oracle database after you create a connection and build an app in Power Apps で接続を作成し、アプリを構築した後、Oracle データベースでテーブルを一覧表示し、テーブル行を作成、読み取り、更新、および削除します。 Oracle データベース接続では、フィルター処理や並び替えなど、およびその他の機能の完全な委任がサポートされますが、トリガーとストアド プロシージャはサポートされません。

## <a name="prerequisites"></a>前提条件
* Oracle 9 以降
* Oracle クライアント ソフトウェア 8.1.7 以降
* オンプレミス データ ゲートウェイのインストール
* Oracle クライアント SDK のインストール

### <a name="install-an-on-premises-data-gateway"></a>オンプレミス データ ゲートウェイをインストールする
ゲートウェイをインストールするには、[このチュートリアル](../gateway-management.md) の手順に従います。

オンプレミス データ ゲートウェイはブリッジとして機能し、オンプレミ スデータ (クラウドに含まれていないデータ) と Power BI、Power Automate、Logic Apps、および Power Apps サービスとの間の迅速かつ安全なデータ転送を提供します。 複数のサービスやデータ ソースで、同一のゲートウェイを使用できます。 詳細については、[ゲートウェイの概要](../gateway-reference.md) を参照してください。

### <a name="install-oracle-client"></a>Oracle クライアントをインストールする
オンプレミス データ ゲートウェイと同じコンピューターに、[64-bit ODAC 12c Release 4 (12.1.0.2.4) for Windows x64](https://www.oracle.com/technetwork/database/windows/downloads/index-090165.html) をインストールします。 このインストールを行わないと、既知の問題の一覧で説明しているように、接続を作成または編集しようとするとエラーが表示されます。

## <a name="create-an-app-from-a-table-in-an-oracle-database"></a>Oracle データベースのテーブルからアプリを作成する
1. Power Apps Studio で、**ファイル** メニュー (左端の近く) の**新規**をクリックまたはタップします。
   
   ![新規オプション](./media/connection-oracledb/new-app.png)
2. **データを使用して開始する**で、矢印をクリックまたはタップします。
   
      既にある接続の一覧が表示されます。
3. **新しい接続**をクリックまたはタップします。
   
   ![新しいつながり](./media/connection-oracledb/new-connection.png)
4. 接続の一覧で、**Oracle データベース**をクリックまたはタップします。
   
   ![新規データベース](./media/connection-oracledb/oracle-db.png)
5. Oracle サーバーの名前、ユーザー名およびパスワードを指定します。
   
    SID が必要な場合は、次の形式でサーバーを指定します:<br>
    *ServerName*/*SID*
   
   ![接続パラメーター](./media/connection-oracledb/connection-params.png)
6. 使用するゲートウェイをクリックまたはタップするか、ゲートウェイをインストールします。
   
    インストール後にゲートウェイが表示されない場合は、**ゲートウェイ一覧を最新の情報に更新する**をクリックします。
   
   ![新規ゲートウェイ](./media/connection-oracledb/choose-gateway.png)
7. **作成**をクリックまたはタップして接続を作成します。
   
   ![新規​​](./media/connection-oracledb/create-button.png)
8. **既定**のデータセットをクリックまたはタップします。
   
   ![新規​​](./media/connection-oracledb/choose-dataset.png)
9. テーブルの一覧で、使用するテーブルをクリックまたはタップします。
   
   ![新規​​](./media/connection-oracledb/choose-table.png)
10. **接続**をクリックしてアプリを作成します。
    
    ![新規​​](./media/connection-oracledb/connect-button.png)

Power Apps では 3 つの画面があるアプリが作成され、選択したテーブルのデータが表示されます:

* **BrowseScreen1** には、テーブルに含まれるすべてのエントリが一覧表示されます。
* **DetailScreen1** には、単一のエントリに関する詳細情報が表示されます。
* **EditScreen1** では、ユーザーがエントリの更新または作成を行うことができます。

![新規​​](./media/connection-oracledb/afd-app.png)

## <a name="next-steps"></a>次の手順
* 先ほど生成したアプリを保存するには、Ctrl-S キーを押します。
* **BrowseScreen1**(既定で表示される) をカスタマイズするには、[レイアウトのカスタマイズ](../customize-layout-sharepoint.md) を参照してください。
* **DetailsScreen1** または **EditScreen1** をカスタマイズするには、[フォームのカスタマイズ](../customize-forms-sharepoint.md) を参照してください。

## <a name="known-issues-tips-and-troubleshooting"></a>既知の問題、ヒント、およびトラブルシューティング
1. ゲートウェイに到達できません。
   
    このエラーは、オンプレミス データ ゲートウェイがクラウドへ接続できない場合に表示されます。 ゲートウェイの状態を確認するには、powerapps.microsoft.com にサインインして、**ゲートウェイ**をクリックまたはタップしてから、使用するゲートウェイをクリックまたはタップします。
   
    ゲートウェイが実行中であり、インターネットに接続可能であることを確認してください。 電源がオフになっているかスリープ状態のコンピューターには、ゲートウェイをインストールしないでください。 また、オンプレミス データ ゲートウェイ サービス (PBIEgwService) を再起動してみてください。
2. System.Data.OracleClient には Oracle クライアント ソフトウェア バージョン 8.1.7 以降が必要です。
   
    このエラーは、Oracle クライアント SDK がオンプレミス データ ゲートウェイと同じコンピューターにインストールされていない場合に表示されます。 この問題を解決するには、[正式なプロバイダーをインストール](https://go.microsoft.com/fwlink/p/?LinkID=272376) します。
3. テーブル '[Tablename]' には、任意のキー列が定義されていません。
   
    このエラーは、Oracle データベース接続に必要な主キーが設定されていないテーブルへ接続しようとする場合に表示されます。
4. 現時点で、ストアド プロシージャ、複合キーの設定されたテーブル、テーブル内で入れ子になったオブジェクト型は Power Apps で直接サポートされていません。 ただし、Power Automate を使用するストアド プロシージャはサポートされています。

