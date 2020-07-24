---
title: Common Data Service に接続する | Microsoft Docs
description: Power Apps で Common Data Service に接続し、このデータベースを利用してアプリを構築する方法について説明します。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/04/2020
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 227482b383acd3117cc78eddf97698ffa9146698
ms.sourcegitcommit: 56c8c7cc64695ccb00e0d021c9f98cf70b69b4a2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2020
ms.locfileid: "3308155"
---
# <a name="connect-to-common-data-service"></a>Common Data Service への接続

## <a name="overview"></a>概要

Common Data Service でビジネス データを安全に格納し、Power Apps で機能豊富なアプリを構築して、ユーザーがそのデータを管理できるようにします。 Power Automate、Power BI、および Dynamics 365 からのデータを含むソリューションにそのデータを統合することもできます。

既定では、Common Data Service コネクタは、アプリの現在の環境でのデータに接続します。 アプリが別の環境に移動すると、コネクタは新しい環境のデータに接続します。 この動作は、単一環境を使用するアプリ、または ALM プロセスに従って開発からテスト、運用に移行するアプリに適しています。

Common Data Service コネクタを使用してデータ ソースを追加する場合、環境を変更し、1 つ以上のエンティティを選択できます。 既定では、 アプリは、現在の環境でのデータに接続します。

![既定の環境](media/connection-common-data-service/common-data-service-connection-change-environment.png)

**変更**を選択する場合、現在の環境の代わりに、または現在の環境に加えて、別の環境からデータを取得できるように指定できます。

![その他の環境](media/connection-common-data-service/common-data-service-connection-select-environment.png)

選択した環境の名前がエンティティの一覧に表示されます。

![新しい環境](media/connection-common-data-service/common-data-service-connection-after-change-environment.png)

Common Data Service コネクタは、Dynamics 365 Connector よりも堅牢で、機能パリティに近づいています。

### <a name="common-data-service-and-the-improved-data-source-experience"></a>Common Data Service および強化されたデータ ソース エクスペリエンス

2019 年 11 月より前に Common Data Service コネクタを使用してキャンバス アプリを作成した場合、Common Data Service の最新バージョンの利点がない可能性があります。 詳細と接続のアップグレードについては、[Common Data Service 接続の改善](../use-native-cds-connector.md) をお読みください。