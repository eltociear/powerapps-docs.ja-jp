---
title: SQL を使用したデータのクエリ (Common Data Service)| Microsoft Docs
description: SQL を使用して Common Data Service エンティティ データをクエリする方法について説明します。
ms.custom: ''
ms.date: 05/26/2020
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: pehecke
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 69dc9c3c5986468fc47710c2d980857f547bacb9
ms.sourcegitcommit: 1c205fc6ea1d85778c1ceeb164d1867f512e5d91
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "3431855"
---
# <a name="use-sql-to-query-data-preview"></a>SQL を使用してデータを照会する (プレビュー)

[!INCLUDE[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

SQL データ接続は、Common Data Service エンドポイントで使用できます。 SQL 接続は、ターゲットの Common Data Service 環境のエンティティ データへの読み取り専用アクセスを提供します。 これにより、エンティティ データ テーブルに対して SQL クエリを記述して実行できます。 テーブルの列は、エンティティの属性データを提供します。 データのカスタムビューは提供されていません。

> [!IMPORTANT]
> - これはプレビュー機能であり、すべての地域で利用できるわけではありません。
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)]
> - この機能を有効にする手順は、次を参照してください: [Power BI Desktop でエンティティ データを表示する](/powerapps/maker/common-data-service/view-entity-data-power-bi)、および[機能設定を管理する](/power-platform/admin/settings-features) (TDSエンドポイント設定を参照)。

## <a name="applications-support"></a>アプリケーション サポート

Power Apps (https://make.powerapps.com) の **Power BI で分析**オプション (**データ** > **エンティティ** > **Power BI で分析**) を使用して、SQL 接続機能により Power BI Desktop でデータを分析できます。 詳細: [Power BI Desktop でのエンティティ データの表示](/powerapps/maker/common-data-service/view-entity-data-power-bi)

> [!NOTE]
> ターゲット環境で Common Data Service SQL接続機能が有効になっている場合は、以下を実行します :
> 1. Power Apps にサインインし、左側のナビゲーション ウィンドウで、**データ**を展開して**エンティティ**を選びます。
> 2. コマンドバーに **Power BIで分析を行う** ボタンが表示されます。 このボタンが表示されない場合、環境にはまだこの機能が実装されていないことを意味します。

Common Data Service エンドポイントの SQL 接続で、[SQL Server Management Studio](/sql/ssms/download-sql-server-management-studio-ssms) (SSMS) バージョン 18.4 以降を使用することもできます。 SQL データ接続で SSMS を使用する例を以下に示します。

![拡張アカウント テーブル](media/ssms-table-expanded.PNG)

## <a name="security-and-authentication"></a>セキュリティおよび認証

Common Data Service エンドポイントの SQL接続は、データ アクセスに Common Data Service セキュリティモデルを使用します。 Common Data Service でユーザーがアクセスできるすべてのエンティティのデータを取得できます。

Azure Active Directory 認証のみサポートしています。 SQL 認証と Windows 認証はサポートされていません。 以下は、SSMS で SQL 接続にログオンする方法の例です。 サーバー名は、組織アドレス URL の後にコンマと 5558 のポート値が続くことに注意してください。

![接続ダイアログ](media/ssms-connect-dialog.PNG)

## <a name="example-entity-data-queries"></a>エンティティ データ クエリの例

以下は、SSMS で構成されるクエリのいくつかの例です。 最初の画像は、エイリアスと結果の順序を使用した簡単なクエリを示しています。

```tsql
select top 5 a.name as [VIP customer], a.address1_postalcode as [ZIP code] from account a order by a.address1_postalcode desc
```

![エイリアスと順序を使用した簡単なクエリ](media/ssms-simple-query.PNG)

次のクエリは、JOIN を示しています。

```tsql
select name, fullname from account a inner join contact c on a.primarycontactid = c.contactid
```

![JOIN を使用した別のクエリ](media/ssms-join-query.PNG)

## <a name="supported-operations-and-data-types"></a>サポートされている操作とデータ型

サポートされている SQL 操作のリストは次のとおりです。

- バッチ処理
- 選択
- 集計関数 (例、Count() および Max() 関数)
- UNION および JOIN
- フィルタリング

これは読み取り専用の SQL データ接続であるため、データを変更しようとする操作 (例、INSERT、UPDATE) は機能しません。 Common Data Service オプション セットは、結果セットでは \<OptionSet\>  の名前と \<OptionSet\> のラベルとして表されます。

以下の Common Data Service データ型は SQL 接続では対応していません : `binary`、`image`、`ntext`、`sql_variant`、`varbinary`、`virtual`、`HierarchyId`、`managedproperty`、`file`、`xml`、`partylist`、`timestamp`。

> [!TIP]
> `partylist` 属性は、代わりに以下のように `activityparty` テーブルに結合して問い合わせを行うことができます。
> 
> ```tsql
> select act.activityid, act.subject, string_agg([to].partyidname, ', ')
> from activitypointer as act
> left outer join activityparty as [to] on act.activityid = [to].activityid and [to].participationtypemask = 2
> group by act.activityid, act.subject
> ```

### <a name="see-also"></a>関連項目

[FetchXML の使用によるクエリの作成](use-fetchxml-construct-query.md)
