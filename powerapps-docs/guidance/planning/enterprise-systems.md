---
title: データ設計 - エンタープライズ システムで作業をする | Microsoft Docs
description: この記事を読んで、Power Apps プロジェクトのエンタープライズ システムと統合する際に考慮すべきいくつかのことを理解してください。
author: taiki-yoshida
ms.service: powerapps
ms.topic: conceptual
ms.custom: guidance
ms.date: 06/16/2020
ms.author: tayoshi
ms.reviewer: kathyos
ms.openlocfilehash: e71c2225cb1c196b6b1e5fa002cf519428b4669d
ms.sourcegitcommit: 213c46f7055eb71b9064b0645d8d17cf8eaad179
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/16/2020
ms.locfileid: "3461585"
---
# <a name="working-with-enterprise-systems"></a>エンタープライズ システムの操作

SAP や Oracle などの既存のエンタープライズ システムを使用して統合する必要がある場合は、IT 管理チームまたはシステム担当のチームに協力とサポートを要請する必要があります。

技術的な役割を担っていない場合でも、このセクションを読んで、エンタープライズ システムと統合する際に考慮する必要があることを理解してください。

## <a name="frequency-and-time-of-data-integration"></a>データ統合の頻度と時間

他のシステムと統合を行う際には、統合の頻度を考慮し、統合にタイムゾーンを横断する使用例がある場合には、タイムゾーンを考慮する必要があります。
統合の頻度は、データ量とビジネスにおける時間に関する要件という2つの側面によって変わります。

## <a name="method-of-integrating-with-enterprise-systems"></a>エンタープライズ システムとの統合方法

エンタープライズ システムと統合するには、いくつかの方法があります。

- **データベース**統合は、データベースとの直接的な統合を行います。 これには、データを公開するリスクがあるため、外部システムと統合する際には一般的な方法ではありません。

- **API** 統合は、API を使用してシステムと統合する方法です。 大半の Web システムでは、統合に使用する API を提供していますが、提供されていない場合もあります。

- **ファイル** 統合は、ファイルを使用してシステムと統合する方法です。 1つのシステムでデータ ファイルをエクスポートします。 このファイルは、CSV、TSV、XML、またはその他の形式の場合があります。 統合するシステムは、新しいファイルを検出するか、タイマーで定期的にスキャンして新しいファイルの存在を確認し、エクスポートしたファイルをインポートするように設定されています。 このメソッドは、データベースや API を介してデータソースに直接アクセスできない場合に使用されます。

## <a name="connecting-to-on-premises-systems"></a>オンプレミスのシステムに接続する

オンプレミスのデータ ゲートウェイを使用すると、アプリやサービスをインターネットに公開されていないシステムに安全に接続することができます。 設定はインストーラーを使用するので簡単ですが、考慮すべきいくつかの要素があります。

- データセンターまたはサーバーの場所のネットワーク帯域幅

- データ ソースのデータベース チューニング

- オンプレミス システムのサーバー仕様

- データ送信量と頻度

### <a name="network-bandwidth-of-the-datacenter-or-server-location"></a>データセンターまたはサーバーの場所のネットワーク帯域幅

アプリの速度は、オンプレミスのデータセンター、またはサーバーとクラウドサービス間のネットワーク帯域幅が十分かどうかによって異なります。 多数のユーザーが同時にアプリを使用する場合、十分な帯域幅がないと、アプリの応答が遅くなります。 詳細: [Web アプリケーションの要件](https://docs.microsoft.com/power-platform/admin/web-application-requirements)

ネットワーク速度を調べるには、Microsoft Store の[ネットワーク速度テスト](https://www.microsoft.com/p/network-speed-test/9wzdncrfhx52)(無料)や、モデル駆動型アプリ専用の[診断ツール](https://docs.microsoft.com/power-platform/admin/verify-network-capacity-throughput-clients)を利用してください。

### <a name="database-tuning-of-the-data-source"></a>データ ソースのデータベース チューニング

特に大量のデータを含むデータ ソースに接続する場合は、データベースのチューニングも重要な役割を果たします。 使用したことのない方法でデータを使用するアプリを作成した場合、問題が発生しやすくなります。

例えば、既存の顧客管理システムでは、姓名・名・メールアドレスで検索するように最適化されているが、電話番号で検索するアプリを新規作成した場合を例としてあげます。 アプリの効率的な検索に役立てるために、データにはインデックス付けをしていません。

インデックスを作成すると、アプリでの検索を高速化できます。インデックスがない場合は、データの検索とクエリには時間がかかります。 データ ソースの IT チームに連絡して、データへのアクセス方法とインデックスの追加方法について話し合う必要があるかもしれません。 SQL Server でのインデックス作成についての詳細については、[SQL Server のインデックスのアーキテクチャとデザイン ガイド](https://docs.microsoft.com/sql/relational-databases/sql-server-index-design-guide?view=sql-server-ver15)を参照してください。

### <a name="server-specification-of-on-premises-systems"></a>オンプレミス システムのサーバー仕様

考慮すべきもう1つの側面は、オンプレミスのゲートウェイを処理するサーバーの仕様です。 アプリに同時にアクセスするユーザーが多すぎる場合は、サーバーがすべてのリクエストに対応できない可能性があります。 このような状況では、オンプレミスのゲートウェイを複数のサーバーに設定してクラスタを形成することを検討する必要があります。 詳細情報 : [オンプレミス データ ゲートウェイの高可用性クラスターと負荷分散の管理](https://docs.microsoft.com/data-integration/gateway/service-gateway-high-availability-clusters)

### <a name="volume-and-frequency-of-data-transmission"></a>データ送信量と頻度

大量のリクエストに対しては、データフローなどのアプローチを使用することで、オンプレミスのデータとの統合を可能にしつつ、より優れたパフォーマンスを提供することができます。

> [!div class="nextstepaction"]
> [次の手順 : データ モデリング](data-modeling.md)
