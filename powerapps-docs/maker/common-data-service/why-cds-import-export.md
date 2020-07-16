---
title: データのインポートとエクスポート | MicrosoftDocs
ms.custom: ''
ms.date: 06/16/2020
ms.reviewer: Mattp123
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- powerapps
author: mmercuri
ms.author: mmercuri
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 82bf6a94ab1bdbeacec24c4d6ed162b696549a5b
ms.sourcegitcommit: 75efc726828507593b1ae38a456d28e00d27b777
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "3517177"
---
# <a name="importing-and-exporting-data"></a>データのインポートおよびエクスポート

データを Common Data Service にインポートおよびエクスポートするには複数の方法があります。 データフロー、Power Query、Azure Data Factory、Azure Logic Apps、Power Automate を使うことができます。

Dynamics のお客様は、データ エクスポート サービスも使用できます。

## <a name="dataflows"></a>データフロー 

データフローを使用すると、さまざまなソースからのビジネスデータに接続し、データをクリーンアップして変換し、Common Data Service に読み込むことができます。 データフローは、数十の人気のオンプレミスの、クラウド、サービスとしてのソフトウェア (SaaS) データ ソースをサポートしています。

Power Query は、データ ソースを検出、接続、結合、調整して分析のニーズを満たすために使用できるデータ接続テクノロジーです。 Power Query の機能は Excel と Power BI Desktop で使用できます。 

![Common Data Service を使ったデータ フローと Power Query](media/dataflows-power-query-with-cds.png "Common Data Service を使ったデータ フローと Power Query")

詳細: [Power Apps でデータフローを作成して使用する](/powerapps/maker/common-data-service/create-and-use-dataflows) と [Power Query を使用して Common Data Service でエンティティにデータを追加する](/powerapps/maker/common-data-service/data-platform-cds-newentity-pq)

## <a name="azure-data-factory"></a>Azure Data Factory

Data Factory は、ビジュアル環境内で、または独自のコードを記述することによって、抽出、変換、ロード (ETL) プロセスを構築するための低コードまたはコードなしのアプローチを提供するデータ統合サービスです。 

![Data Factory](media/azure-data-factory.png "Data Factory")

Data Factoryを使用すると、Common Data Service と 90 を超えるネイティブで構築され、メンテナンスフリーのコネクタを使用したその他のデータソースを視覚的に統合できます。

![Data Factory ETL](media/azure-data-factory-etl.png "Data Factory ETL")

Common Data Service へのデータの取り込みに加えて、Data Factory は、Databricks でデータを準備、変換、強化し、データを Azure Synapse 分析も使用できます。

## <a name="exporting-data-from-common-data-service"></a>Common Data Service からのデータのエクスポート

別のデータ技術または別の Common Data Service 環境のいずれかへのデータのエクスポートは、データフロー、データファクトリ、Power Query、Power Automate など、データのインポートで言及したものと同じテクノロジーを使用できます。

![Common Data Service データのエクスポート方法](media/export-cds-data.png "Common Data Service データのエクスポート方法")

SQL Server または Azure SQL データベースを対象としている Dynamics のお客様は、データ エクスポート サービスを使用できます。 これは Common Data Service ソリューションとして提供されるアドオンサービスで、お客様が所有する Azure サブスクリプションの SQLデータベース ストアに Common Data Service データを複製する機能を追加します。 対応している対象は、SQL データベースおよび Azure 仮想マシン上の SQL サーバーです。 データ エクスポートは Common Data Service スキーマとデータ全体をインテリジェントに同期処理し、その後、Common Data Service システムで変更 (差分変更) が発生すると、継続的に同期処理します。

### <a name="see-also"></a>関連項目

[あらゆる種類のアプリで作業する](why-cds-any-type-app.md)
