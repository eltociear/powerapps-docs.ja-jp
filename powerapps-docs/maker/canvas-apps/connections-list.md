---
title: キャンバス アプリ用のコネクタの概要 | Microsoft Docs
description: キャンバス アプリの構築に使用できる利用可能なすべての接続の概要
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/23/2020
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 984cb472a3efeb0fc4f702cfed67d76d437b88c4
ms.sourcegitcommit: e2c92335fe6162c4576f0b86238ccbe4a7f74732
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2020
ms.locfileid: "3418237"
---
# <a name="overview-of-canvas-app-connectors-for-power-apps"></a>Power Apps のキャンバス アプリ コネクタの概要
データは、Power Apps で構築されたものを含め、ほとんどのアプリの中核にあります。 データは*データ ソース*に格納され、*接続*を作成することによってそのデータをアプリに取り込みます。 接続では、データソースとの通信に*コネクタ*を使用します。 Power Apps には、SharePoint、SQL Server、Office 365、Salesforce、Twitter など、よく使われているサービスやオンプレミスのデータ ソースの多くに対応したコネクタが用意されています。 キャンバス アプリへのデータの追加を開始するには、[Power Apps でのデータ接続の追加](add-data-connection.md) を参照してください。

コネクタは、データまたは**アクション**の**テーブル**を提供する場合があります。 テーブルのみ、またはアクションのみを提供するコネクタがあり、両方を提供するコネクタもあります。 また、コネクタは、標準コネクタのまたはカスタム コネクタのいずれかとなります。

## <a name="tables"></a>テーブル

コネクタでテーブルが提供されている場合は、テーブル ソースを追加してから、管理するデータ ソース内でテーブルを選択します。 Power Apps は、アプリにテーブル データを取得し、データ ソース内のデータを更新します。 たとえば、**レッスン**という名前のテーブルが含まれるデータ ソースを追加してから、ギャラリーやフォームなどのコントロールの**項目**プロパティを数式バーの次の値に設定できます:

 ![プレーン データ ソースの項目プロパティ](./media/connections-list/ItemPropertyPlain.png)

データを表示するコントロールの**項目**プロパティをカスタマイズすることにより、アプリが取得するデータを指定できます。 前の例に続けて、**レッスン** テーブル内のデータを並べ替えまたはフィルター処理できます。そのためには、**検索**関数および **SortByColumn** 関数の引数としてその名前を使用します。 この図では、**項目**プロパティが設定された式では、**TextSearchBox1** 内のテキストに基づいてデータの並べ替えおよびフィルター処理を行うように指定されています。 

 ![拡張されたデータ ソースの項目プロパティ](./media/connections-list/ItemPropertyExpanded.png)

テーブルを使用して式をカスタマイズする方法の詳細については、次のトピックを参照してください:

  [Power Apps のデータ ソースについて](working-with-data-sources.md)<br> 
  [Excel データからアプリを生成する](get-started-create-from-data.md)<br> 
  [アプリの一からの作成](get-started-create-from-blank.md)<br>
  [Power Apps におけるテーブルとレコードについて](working-with-tables.md)

  > [!NOTE]
  > Excel ワークブック内のデータに接続するには、OneDrive のようなクラウド ストレージ サービスでホストされる必要があります。 詳細については、[Power Apps からのクラウド ストレージに接続する](connections/cloud-storage-blob-connections.md) を参照してください。

## <a name="actions"></a>操作​​

コネクタによってアクションが提供される場合でも、以前と同じようにデータ ソースを選択する必要があります。 ただし、次の手順としてテーブルを選択するのでなく、コントロールをアクションに手動で接続します。そのためには、データを表示するコントロールの**項目**プロパティを編集します。 **項目**プロパティを設定した計算式では、データを取得するアクションが指定されています。 たとえば、Yammer に接続してから、**項目**プロパティをデータ ソースの名前に設定した場合、アプリは任意のデータを取得しません。 コントロールにデータを設定するには、**GetMessagesInGroup(5033622).messages** のようなアクションを指定します。

![アクション データ ソースの項目プロパティ](./media/connections-list/ItemPropertyAction.png)

アクション コネクタ用のカスタム データ更新に対処する必要がある場合は、**パッチ**関数を含む計算式を構築します。 計算式では、アクションおよびアクションにバインドするフィールドを特定します。  

カスタム更新の計算式をカスタマイズする方法の詳細については、次のトピックを参照してください:

[Patch](functions/function-patch.md)<br>[Collect](functions/function-clear-collect-clearcollect.md)<br>[更新プログラム](functions/function-update-updateif.md)

> [!NOTE]
>  **Power Apps は動的スキーマでは機能しません**。 動的スキーマというフレーズは、同じアクションが異なる列を持つ異なるテーブルを返す可能性を示しています。 テーブルの列が異なる可能性のある条件には、アクション入力パラメーター、アクションを実行しているユーザーまたはロール、ユーザーが作業しているグループなどがあります。 たとえば、SQL Server ストアド プロシージャは、異なる入力で実行すると、異なる列を返す場合があります。 動的スキーマを持つアクションの場合、コネクタのドキュメントは戻り値として**この操作の出力は動的です。** と表示します。 一方、Power Automate は動的スキーマで動作し、シナリオの回避策を提供する場合があります。

## <a name="popular-connectors"></a>一般的なコネクタ

このテーブルには最も一般的なコネクタに関する詳細情報へのリンクが含まれています。 コネクタのリスト全体については、[すべてのコネクタ](https://docs.microsoft.com/connectors/connector-reference/) を参照してください。

| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- | --- | --- |
| ![Common Data Service](./media/connections-list/cdm.png) |[**Common Data Service**](connections/connection-common-data-service.md) |&nbsp; |![クラウド ストレージ](./media/connections-list/onedrive.png) |[**クラウド ストレージ**](connections/cloud-storage-blob-connections.md) ** |
| ![Dynamics AX](./media/connections-list/dynamics-ax.png) |[**Dynamics AX**](connections/connection-dynamicsax.md)|&nbsp; |![Excel](./media/connections-list/excel.png) |[**Excel**](connections/connection-excel.md)|
| ![Microsoft Translator](./media/connections-list/microsoft-translator.png) |[**Microsoft Translator**](connections/connection-microsoft-translator.md)|&nbsp; | ![Office 365 Outlook](./media/connections-list/office365.png) |[**Office 365 Outlook**](connections/connection-office365-outlook.md)|
| ![Office 365 Users](./media/connections-list/office365.png) |[**Office 365 ユーザー**](connections/connection-office365-users.md)  |&nbsp; | ![Oracle](./media/connections-list/oracle-icon.png) |[**Oracle**](connections/connection-oracledb.md)|
| ![Power BI](./media/connections-list/powerbi.png) |[**Power BI**](connections/connection-powerbi.md) |&nbsp; | ![SharePoint](./media/connections-list/sharepoint.png) |[**SharePoint**](connections/connection-sharepoint-online.md) |
| ![SQL Server](./media/connections-list/sql.png) |[**SQL Server**](connections/connection-azure-sqldatabase.md) |&nbsp; | ![Twitter](./media/connections-list/twitter.png) |[**Twitter**](connections/connection-twitter.md) |

**Azure Blob、Box、Dropbox、Google Drive、OneDrive および OneDrive for Business に適用されます

## <a name="standard-and-custom-connectors"></a>標準コネクタおよびカスタム コネクタ
Power Apps は、多くの一般的に使用されるデータ ソースに*標準*コネクタを提供します。 Power Apps に使用するデータ ソースの種類に対する標準コネクタがある場合は、そのコネクタを使用する必要があります。 自分で構築したサービスなど、別の種類のデータ ソースに接続する必要がある場合は、[カスタム コネクタを登録して使用する](../canvas-apps/register-custom-api.md) を参照してください。

## <a name="all-standard-connectors"></a>すべての標準コネクタ
標準コネクタには特別なライセンスは必要ありません。 詳細については、[Power Apps プラン](https://powerapps.microsoft.com/pricing/) を参照してください。

[Power Apps フォーラム](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1) で特定のコネクタについて質問できます。さらに [Power Apps アイデア](https://powerusers.microsoft.com/t5/PowerApps-Ideas/idb-p/PowerAppsIdeas) で追加すべきコネクタまたは他の改善事項を提案できます。

## <a name="security-and-types-of-authentication"></a>セキュリティおよび認証の種類

アプリを作成してデータ ソースへの接続を作成すると、コネクタの選択により、認証に異なる方法を使用できるようになる場合があります。 たとえば、SQL Server コネクタを使用すると、統合済み Azure AD、SQL Server 認証、および Windows 認証を使用できます。 認証の種類ごとに、関連するセキュリティのレベルが異なります。  アプリケーションを使用するユーザーと共有する情報および権利について理解することが重要です。 この記事の主な例は SQL Serverですが、原則はすべてのタイプの接続に適用されます。

### <a name="azure-ad-integrated"></a>統合済み Azure AD

これはセキュリティで保護されたタイプの接続です。  例えば、SharePoint ではこのタイプの認証を使用します。  SQL Server では、このタイプの認証も可能です。  接続すると、Azure AD サービスは、ユーザーの代わりに SharePoint に対してユーザーを個別に識別します。  ユーザー名やパスワードを入力する必要はありません。  作成者は、資格情報を使用してデータ ソースを作成および操作できます。  アプリケーションを公開し、アプリケーション ユーザーがログインする場合、資格情報を使用して実行します。 データがバックエンドで適切に保護されている場合、ユーザーは資格情報に基づいて、表示を許可されているもののみを表示できます。   このタイプのセキュリティでは、アプリケーションが公開された後に、バックエンド データ ソースで特定のアプリケーション ユーザーの権限を変更できます。  たとえば、バックエンド データ ソースでアクセス権の許可、拒否、またはユーザーまたは一連のユーザーが表示できるものすべてを調整できます。

### <a name="open-standard-authorization-oauth"></a>オープンスタンダード認証 (OAuth)

このタイプの接続もセキュリティで保護されています。  例えば、Twitter ではこのタイプの認証を使用します。  接続するときは、ユーザー名とパスワードを入力する必要があります。  作成者は、資格情報を使用してデータ ソースを作成および操作できます。  アプリケーションを公開し、アプリケーション ユーザーがログインする場合、資格情報も入力する必要があります。  ユーザーはデータ ソース サービスにアクセスするために自分の認証情報を使用する必要があるため、このタイプの接続はセキュリティ保護されています。 

### <a name="sql-user-name-and-password-authentication"></a>SQL ユーザー名とパスワード認証

このタイプの接続は、エンドユーザー認証に依存しないため、あまり安全ではありません。  SQL Server では、このタイプの認証も可能です。  SQL Server では、このタイプの認証は **SQL Server 認証**と呼ばれます。  他の多くのデータベース データ ソースが同様の機能を提供します。  アプリケーションを公開するとき、ユーザーは一意のユーザー名とパスワードを入力する必要はありません。  アプリケーションを作成するときに入力したユーザー名とパスワードを使用しています。  データ ソースへの接続認証は、ユーザーと**暗黙的に共有**されます。  アプリケーションが一旦公開されると、接続も公開され、ユーザーが使用できるようになります。  エンド ユーザーは、共用されている SQL Server 認証による接続を使用してアプリケーションを作成することもできます。  ユーザーはユーザー名やパスワードを表示できませんが、接続は利用可能です。  このタイプの接続には、確実に有効なシナリオがあります。  たとえば、社内の全員が利用できる読み取り専用データベースがある場合、このタイプの接続は有効である可能性があります。 

### <a name="windows-authentication"></a>Windows 認証

このタイプの接続は、エンドユーザー認証に依存しないため、あまり安全ではありません。 **オンプレミス**であるデータ ソースに接続する必要がある場合は、Windows 認証を使用します。 このタイプの接続の例として、SQL Server を持つオンプレミス サーバーへの接続があります。 接続はゲートウェイを経由する必要があります。 ゲートウェイを経由するため、コネクタはそのデータ ソース上のすべてのデータにアクセスできます。 その結果、入力する Windows 資格情報を使用してアクセスできる任意の情報をコネクタで利用できます。 さらにアプリケーションが一旦公開されると、接続も公開され、ユーザーが使用できるようになります。  つまり、エンド ユーザーも同じ接続を使用してアプリケーションを作成し、そのコンピューターのデータにアクセスできます。 データ ソースへの接続も、アプリが共有されているユーザーと**暗黙的に共有**されます。 このタイプの接続は、データ ソースがオンプレミス サーバーにのみ存在し、そのソースのデータを自由に共有できる場合に有効です。
