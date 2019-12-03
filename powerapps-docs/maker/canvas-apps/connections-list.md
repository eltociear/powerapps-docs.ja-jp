---
title: キャンバス アプリ用のコネクタの概要 | Microsoft Docs
description: キャンバス アプリの構築に使用できるすべての有効な接続の概要
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/19/2019
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 6cda843ea95f79e907aa738a6546d63a6a3be270
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2019
ms.locfileid: "74678858"
---
# <a name="overview-of-canvas-app-connectors-for-powerapps"></a>PowerApps 用のキャンバス アプリ コネクタの概要
データは、Power Apps で構築したものも含め、ほとんどのアプリの中核になります。 *データ ソース*に格納されたデータは、*接続*を作成することでアプリに取り込まれます。 接続は特定の*コネクタ*を使用してデータ ソースと通信します。 Power Apps には、多くの人気のあるサービスやオンプレミスのデータソース (SharePoint、SQL Server、Office 365、Salesforce、Twitter など) 用のコネクタが用意されています。 キャンバス アプリへのデータの追加を開始するには、[PowerApps でのデータ接続の追加](add-data-connection.md)に関するページを参照してください。

コネクタから、データの**テーブル**または**アクション**が提供される場合があります。 コネクタの中には、テーブルのみを提供するもの、アクションのみを提供するもの、そして両方を提供するものがあります。 また、ご利用のコネクタは、標準コネクタのまたはカスタム コネクタのいずれかとなります。

## <a name="tables"></a>テーブル

ご利用のコネクタでテーブルが提供されている場合は、使用するテーブル ソースを追加してから、管理するデータ ソース内でテーブルを選択します。 Power Apps はどちらも、テーブルデータをアプリに取得し、データソース内のデータを更新します。 たとえば、**Lessons** という名前のテーブルが含まれているデータ ソースを追加してから、数式バー内でギャラリーやフォームなどのコントロールの **Items** プロパティを次の値に設定することができます。

 ![プレーン データ ソースの Items プロパティ](./media/connections-list/ItemPropertyPlain.png)

データを表示するコントロールの**Items**プロパティをカスタマイズすることで、アプリが取得するデータを指定できます。 前の例に続けて、**Lessons** テーブル内のデータを並べ替えまたはフィルター処理することができます。そのためには、その名前を、**Search** 関数および **SortByColumn** 関数で引数として使用します。 次の図において、**Items** プロパティが設定された数式では、**TextSearchBox1** 内のテキストに基づいてデータの並べ替えおよびフィルター処理を行うように指定されています。 

 ![拡張されたデータ ソースの Items プロパティ](./media/connections-list/ItemPropertyExpanded.png)

テーブルを使用して数式をカスタマイズする方法の詳細については、次のトピックを参照してください。

  [PowerApps のデータ ソースについて](working-with-data-sources.md)<br> 
  [Excel データからアプリを生成する](get-started-create-from-data.md)<br> 
  [アプリを最初から作成する](get-started-create-from-blank.md)<br>
  [PowerApps におけるテーブルとレコードについて](working-with-tables.md)

  > [!NOTE]
  > Excel データ内のデータに接続するには、そのブックを OneDrive のようなクラウド ストレージ サービスでホストする必要があります。 詳細については、「[クラウド ストレージ接続](connections/cloud-storage-blob-connections.md)」を参照してください。

## <a name="actions"></a>措置

ご利用のコネクタによってアクションが提供される場合も、前に行ったように使用するデータ ソースを選択する必要があります。 ただし、次の手順としては、テーブルを選択するのでなく、コントロールをアクションに手動で接続します。そのためには、ご利用のデータを表示するコントロールの **Items** プロパティを編集します。 **Items** プロパティを設定した数式では、データを取得するアクションが指定されています。 たとえば、Yammer に接続してから、**Items** プロパティをデータ ソースの名前に設定した場合、アプリによってデータは取得されません。 コントロールにデータを設定するには、**GetMessagesInGroup(5033622).messages** のようなアクションを指定します。

![アクション データ ソースの Items プロパティ](./media/connections-list/ItemPropertyAction.png)

アクション コネクタ用のカスタム データ更新プログラムに対処する必要がある場合は、**Patch** 関数を含む数式を作成します。 数式内で、アクションと、アクションにバインドするフィールドとを特定します。  

カスタム更新のために数式をカスタマイズする方法の詳細については、次のトピックを参照してください。

[Patch](functions/function-patch.md)<br>[Collect](functions/function-clear-collect-clearcollect.md)<br>[Update](functions/function-update-updateif.md)

> [!NOTE]
>  **Power Apps は動的スキーマでは動作しません**。 "動的スキーマ" とは、同じアクションが異なる列を持つ別のテーブルを返す可能性を意味します。 テーブル内の列が異なる可能性のある条件としては、アクションの入力パラメーター、アクションを実行しているユーザーまたはロール、およびユーザーが作業しているグループなどがあります。 たとえば、SQL Server のストアドプロシージャでは、異なる入力を使用して実行すると、異なる列が返される場合があります。 動的スキーマを使用するアクションの場合、コネクタのドキュメントは、**この操作の出力が動的**であることを示しています。 戻り値として。 これに対して、Power の自動化は動的スキーマを使用して機能し、シナリオの回避策を提供する場合があります。

## <a name="popular-connectors"></a>一般的なコネクタ

次の表には最も一般的なコネクタに関する詳細情報へのリンクが含まれています。 すべてのコネクタの一覧については、「[すべてのコネクタ](https://docs.microsoft.com/connectors/)」をご覧ください。

| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- | --- | --- |
| ![Common Data Service](./media/connections-list/cdm.png) |[**Common Data Service**](connections/connection-common-data-service.md) |&nbsp; |![クラウドの記憶域](./media/connections-list/onedrive.png) |[**クラウドストレージ**](connections/cloud-storage-blob-connections.md) ** |
| ![Dynamics 365](./media/connections-list/dynamics-365.png) |[**Dynamics 365**](connections/connection-dynamics-crmonline.md) |&nbsp; | ![Dynamics AX](./media/connections-list/dynamics-ax.png) |[**Dynamics AX**](connections/connection-dynamicsax.md) |
|![Excel](./media/connections-list/excel.png) |[**Excel**](connections/connection-excel.md) |&nbsp; |![Microsoft Translator](./media/connections-list/microsoft-translator.png) |[**Microsoft Translator**](connections/connection-microsoft-translator.md) |
|![Office 365 Outlook](./media/connections-list/office365.png) |[**Office 365 Outlook**](connections/connection-office365-outlook.md) |&nbsp; | ![Office 365 Users](./media/connections-list/office365.png) |[**Office 365 Users**](connections/connection-office365-users.md) |
| ![Oracle](./media/connections-list/oracle-icon.png) |[**Oracle11i**](connections/connection-oracledb.md) |&nbsp; | ![Power BI](./media/connections-list/powerbi.png) |[**Power BI**](connections/connection-powerbi.md) |
| ![SharePoint](./media/connections-list/sharepoint.png) |[**SharePoint**](connections/connection-sharepoint-online.md) |&nbsp; | ![SQL Server](./media/connections-list/sql.png) |[**SQL Server**](connections/connection-azure-sqldatabase.md) 
|![Twitter](./media/connections-list/twitter.png) |[**Twitter**](connections/connection-twitter.md)

\* * Azure Blob、Box、Dropbox、Google Drive、OneDrive、OneDrive for Business に適用されます。

## <a name="standard-and-custom-connectors"></a>標準コネクタとカスタム コネクタ
Power Apps には、上記のような一般的に使用される多くのデータソース用の*標準*コネクタが用意されています。 使用するデータソースの種類に対して、Power Apps に標準コネクタがある場合は、そのコネクタを使用する必要があります。 自分で構築したサービスなど、別の種類のデータ ソースに接続する必要がある場合は、「[Microsoft Flow でカスタム コネクタを登録して使用する](../canvas-apps/register-custom-api.md)」を参照してください。

## <a name="all-standard-connectors"></a>すべての標準コネクタ
すべての標準コネクタの一覧については、[Microsoft Connector リファレンス](https://docs.microsoft.com/connectors/)に関するページを参照してください。 Premium コネクタには、Power Apps プラン1またはプラン2が必要です。 詳細については、「 [Power Apps のプラン](https://powerapps.microsoft.com/pricing/)」を参照してください。

[Power apps フォーラム](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1)で特定のコネクタに関する質問をすることができます。また、追加するコネクタや、 [Power apps のアイデア](https://powerusers.microsoft.com/t5/PowerApps-Ideas/idb-p/PowerAppsIdeas)を作成するためのその他の機能強化を提案することもできます。
