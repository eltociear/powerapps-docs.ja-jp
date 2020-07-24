---
title: SQL Server への接続の概要 | Microsoft Docs
description: Azure SQL またはオンプレミス SQL Server データベースに接続する方法に関する詳細な手順
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 07/12/2016
ms.author: lanced
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 08e54e48b371e71364edd2da09648af354a4d9ec
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3306453"
---
# <a name="connect-to-sql-server-from-power-apps"></a>Power Apps から SQL Server に接続する
![SQL Server アイコン](./media/connection-azure-sqldatabase/sqlicon.png)

Azure またはオンプレミス データベースで SQL Server に接続し、Power Apps でそこから情報を表示できるようにします。

## <a name="prerequisites"></a>前提条件

* Power Apps に [サインアップ](../../signup-for-powerapps.md) し、サインアップに使用した同じ資格情報を使用して [サインイン](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) します。
* 主キーを持つテーブルが 1 つ以上含まれるデータベースに関して次の情報を集めます:
  
  * データベースの名前
  * データベースがホストされているサーバーの名前
  * データベースに接続するための有効なユーザー名およびパスワード
  * データベースへの接続に必要な認証の種類
    
    この情報がない場合、使用するデータベースの管理者にお問い合わせください。
* オンプレミス データベースの場合、共有されている [データ ゲートウェイ](../gateway-management.md) を特定します (あるいはデータ ゲートウェイを作成します)。
  
    > [!NOTE]
  > ゲートウェイおよびオンプレミス接続は、ユーザーの [既定の環境](../working-with-environments.md) で作成および使用できます。

## <a name="generate-an-app-automatically"></a>アプリを自動的に生成する
1. Power Apps Studio で、**ファイル** メニュー (左端に表示される) の**新規**をクリックまたはタップします。
   
    ![ファイル メニューの新しいオプション](./media/connection-azure-sqldatabase/file-new.png)
2. **データを使用して開始する**で、コネクタの行端にある右矢印をクリックまたはタップします。
3. 使用するデータベースへの接続が既に与えられている場合、それをクリックまたはタップしてから、手順 7 に進んでください。
4. **新規接続**をクリックまたはタップしてから、**SQL Server** をクリックまたはタップします。
   
    ![SQL Server 接続を追加する](./media/connection-azure-sqldatabase/add-sql-connection.png)
5. 次の手順のいずれかを実行します:
   
   * **直接接続 (クラウド サービス)** を指定してから、サーバー名、データベース名、ユーザー名、使用するデータベースのパスワードを入力するか、貼り付けます。
     
       ![Azure のデータベースに接続する](./media/connection-azure-sqldatabase/connect-azure.png)
   * **オンプレミス データ ゲートウェイを使用する接続**を指定し、サーバー名、データベース名、ユーザー名、使用するデータベースのパスワードを入力するか貼り付けて、認証の種類とゲートウェイを指定します。
     
       ![オンプレミス データベースに接続する](./media/connection-azure-sqldatabase/connect-onprem.png)
     
       > [!NOTE]
     > ゲートウェイがない場合は、[ゲートウェイをインストール](../gateway-reference.md) してから、**ゲートウェイ一覧を最新の情報に更新** をクリックまたはタップします。
6. **接続**をクリックまたはタップします。
7. **データセットの選択**でオプションをクリックまたはタップし、**テーブルの選択**でオプションをクリックまたはタップしてから、**接続**をクリックまたはタップします。
   
    Power Apps では、3 つの画面にデータを表示するアプリが作成されます。 ヒューリスティックスにより表示するデータの種類が提案されますが、場合によっては、自分のニーズに合わせて UI をカスタマイズする必要があります。
8. アプリのカスタマイズは、[Excel からアプリを作成する](../get-started-create-from-data.md) にある説明と同様の手法で行います。最初にアプリのレイアウトを変更します。

## <a name="build-an-app-from-scratch"></a>アプリをゼロから作成
1. Power Apps のサインアップに使用したものと同じアカウントで [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインします。
2. 左側のナビゲーション バーで、**接続**をクリックまたはタップします:  
   
    ![接続の管理](./media/connection-azure-sqldatabase/manage-connections.png)
3. 右上隅で**新しい接続**をクリックまたはタップし、**SQL Server** をクリックまたはタップします。
4. 次の手順のいずれかを実行します:
   
   * **直接接続 (クラウド サービス)** を指定してから、サーバー名、データベース名、ユーザー名、使用するデータベースのパスワードを入力するか、貼り付けます。
     
       ![Azure のデータベースに接続する](./media/connection-azure-sqldatabase/connect-azure-portal.png)
   * **オンプレミス データ ゲートウェイを使用する接続**を指定し、サーバー名、データベース名、ユーザー名、使用するデータベースのパスワードを入力するか貼り付けて、認証の種類とゲートウェイを指定します。
     
       ![Azure のデータベースに接続する](./media/connection-azure-sqldatabase/connect-onprem-portal.png)
     
       > [!NOTE]
     > ゲートウェイがない場合は、[ゲートウェイをインストール](../gateway-reference.md) し、時計回りアイコンをクリックまたはタップしてから、一覧を更新します。
5. **作成**をクリックまたはタップして接続を作成します。
6. [アプリを最初から作成する](../get-started-create-from-blank.md) の説明と同様の手法でアプリを作成します。

## <a name="update-an-existing-app"></a>既存のアプリを更新する
1. Power Apps Studio で、更新するアプリを開きます。
2. リボンの**ビュー** タブで、**データ ソース**をクリックまたはタップします。
3. 右側のウィンドウで、**データ ソースの追加**をクリックまたはタップします。
   
    ![データ ソースの追加](./media/connection-azure-sqldatabase/add-data-source.png)
4. **新しい接続**をクリックまたはタップし、**SQL Server** をクリックまたはタップしてから、**接続**をクリックまたはタップします。
5. 次の手順のいずれかを実行します:
   
   * **直接接続 (クラウド サービス)** を指定してから、サーバー名、データベース名、ユーザー名、使用するデータベースのパスワードを入力するか、貼り付けます。
     
       ![Azure のデータベースに接続する](./media/connection-azure-sqldatabase/connect-azure-fromblank.png)
   * **オンプレミス データ ゲートウェイを使用する接続**を指定し、サーバー名、データベース名、ユーザー名、使用するデータベースのパスワードを入力するか貼り付けて、認証の種類とゲートウェイを指定します。
     
       ![Azure のデータベースに接続する](./media/connection-azure-sqldatabase/connect-onprem-fromblank.png)
     
       > [!NOTE]
     > ゲートウェイがない場合は、[ゲートウェイをインストール](../gateway-reference.md) し、円アイコンをクリックまたはタップして一覧を更新します。
6. **接続**をクリックまたはタップします。
7. **データセットの選択**で、オプションをクリックまたはタップします。
8. **テーブルの選択**で 1 つまたは複数のチェック ボックスをオンにし、**接続**をクリックまたはタップします。

## <a name="next-steps"></a>次の手順
* [データ ソースからデータを表示する](../add-gallery.md) 方法についてご確認ください。
* [詳細を表示してレコードを作成または更新する](../add-form.md) 方法についてご確認ください。
* 接続できる他の種類の [データ ソース](../connections-list.md) を参照してください。  
* 表形式のデータ ソースの[テーブルとレコードについて](../working-with-tables.md)。

<!--NotAvailableYet
## View the available functions ##
This connection includes the following functions:

| Function Name |  Description |
| --- | --- |
|[GetItems](connection-azure-sqldatabase.md#getitems) | Retrieves rows from a SQL table |
|[PostItem](connection-azure-sqldatabase.md#postitem) | Inserts a new row into a SQL table |
|[GetItem](connection-azure-sqldatabase.md#getitem) | Retrieves a single row from a SQL table |
|[DeleteItem](connection-azure-sqldatabase.md#deleteitem) | Deletes a row from a SQL table |
|[PatchItem](connection-azure-sqldatabase.md#patchitem) | Updates an existing row in a SQL table |
|[GetTables](connection-azure-sqldatabase.md#gettables) | Retrieves tables from a SQL database |

### GetItems
Get rows: Retrieves rows from a SQL table

#### Input properties

| Name| Data Type|Required|Description|
| ---|---|---|---|
|table|string|yes|Name of SQL table|
|$skip|integer|no|Number of entries to skip (default = 0)|
|$top|integer|no|Maximum number of entries to retrieve (default = 256)|
|$filter|string|no|An ODATA filter query to restrict the number of entries|
|$orderby|string|no|An ODATA orderBy query for specifying the order of entries|

### PostItem
Insert row: Inserts a new row into a SQL table

#### Input properties

| Name| Data Type|Required|Description|
| ---|---|---|---|
|table|string|yes|Name of SQL table|
|item| |yes|Row to insert into the specified table in SQL|

#### Output properties

| Property Name | Data Type | Required | Description |
|---|---|---|---|
|value|array|No | |


### GetItem
Get row: Retrieves a single row from a SQL table

#### Input properties

| Name| Data Type|Required|Description|
| ---|---|---|---|
|table|string|yes|Name of SQL table|
|id|string|yes|Unique identifier of the row to retrieve|

#### Output properties

| Property Name | Data Type | Required | Description |
|---|---|---|---|
|ItemInternalId|string|No | |


### DeleteItem
Delete row: Deletes a row from a SQL table

#### Input properties

| Name| Data Type|Required|Description|
| ---|---|---|---|
|table|string|yes|Name of SQL table|
|id|string|yes|Unique identifier of the row to delete|

#### Output properties
None.

### PatchItem
Update row: Updates an existing row in a SQL table

#### Input properties

| Name| Data Type|Required|Description|
| ---|---|---|---|
|table|string|yes|Name of SQL table|
|id|string|yes|Unique identifier of the row to update|
|item| |yes|Row with updated values|

#### Output properties

| Property Name | Data Type | Required | Description |
|---|---|---|---|
|ItemInternalId|string|No | &nbsp; |


### GetTables
Get tables: Retrieves tables from a SQL database

#### Input properties
None.

#### Output properties

| Property Name | Data Type | Required | Description |
|---|---|---|---|
|value|array|No | Can output the Name and DisplayName properties |

### ExecuteProcedure
Execute stored procedure: Executes a stored procedure in SQL

#### Input properties

| Name| Data Type|Required|Description|
| ---|---|---|---|
|procedure|string|yes|Procedure name|
|parameters| |yes|Input parameters|

#### Output properties
Result of the stored procedure execution.

| Property Name | Data Type | Required | Description |
|---|---|---|---|
|OutputParameters|object|No | Output parameter values |
|ReturnCode|integer|No | Return code of a procedure |
|ResultSets|object|No | Result sets|

-->
