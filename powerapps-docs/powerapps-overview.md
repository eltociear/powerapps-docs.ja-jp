---
title: Power Apps とは  | Microsoft Docs
description: Power Apps の概要を示し、エンド ユーザー、アプリ メーカー、管理者、プロの開発者による Power Apps の使い方について説明します。
author: KumarVivek
manager: annbe
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 06/30/2020
ms.author: kvivek
ms.reviewer: kvivek
ms.openlocfilehash: 681848e19df79d8822a113fe4c7262cf8ba76621
ms.sourcegitcommit: a2b5f47d66f04bce013232f053164d411fa19110
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "3529709"
---
# <a name="what-is-power-apps"></a>Power Apps とは

Power Apps は、ビジネス ニーズに合ったカスタム アプリを構築するために短時間でアプリケーションを開発できる環境を提供する、アプリ、サービス、コネクタ、およびデータ プラットフォームのスイートです。 Power Apps を使用すると、基盤データ プラットフォーム ([Common Data Service](/powerapps/maker/common-data-service/data-platform-intro)) *または* さまざまなオンラインおよびオンプレミス データ ソース (SharePoint、Excel、Office 365、Dynamics 365、SQL Server など) の *いずれか* に格納されているビジネス データに接続するカスタム ビジネス アプリをすばやく構築できます。 

![Power Apps](media/PowerApps-intro.png "Power Apps")

Power Apps を使用して構築されたアプリでは、充実したビジネス ロジックとワークフローの機能を利用して、手動のビジネス プロセスをデジタルの自動化プロセスに変換することができます。 また、Power Apps によって構築されたアプリはレスポンシブ デザインのため、ブラウザーやモバイル デバイス (携帯電話またはタブレット) でシームレスに実行できます。 Power Apps では、コードを記述しなくても機能が充実したカスタムのビジネス アプリを構築できるため、カスタムのビジネス アプリ構築を "民主化" できます。

Power Apps では、開発者は拡張性の高いプラットフォームを使用して、プログラムでデータとメタデータを操作したり、ビジネス ロジックを適用したり、カスタム コネクタを作成したり、外部データを統合したりできます。

詳細については、YouTube の [Power Apps チャンネル](https://www.youtube.com/channel/UCGfWR2ekfRFckLjev6eQYLg) を参照してください。

## <a name="power-apps-for-app-makerscreators"></a>アプリのメーカー/作成者のための Power Apps

Power Apps を使用すると、**キャンバス**、**モデル駆動型**、**ポータル** という 3 種類のアプリを作成できます。 詳細: [Power Apps でのアプリの作成の概要](maker/index.md)。

アプリを作成するには、[make.powerapps.com](https://make.powerapps.com) から始めます。

- **Power Apps Studio** はキャンバス アプリの作成に使用されているアプリ デザイナーです。 このアプリ デザイナーでは、Microsoft PowerPoint のスライド デッキ作成に近い感覚でアプリを作成できます。 詳細: [データからのアプリの生成](/powerapps/maker/canvas-apps/data-platform-create-app)  

- モデル駆動型用の **アプリ デザイナー** では、サイトマップを定義し、コンポーネントを追加してモデル駆動型アプリを作成できます。 詳細: [アプリ デザイナーを使用してモデル駆動型アプリを設計する](maker/model-driven-apps/design-custom-business-apps-using-app-designer.md)

アイデアをアプリに変換する準備はできましたか? ここから開始: [Power Apps プロジェクトの計画](/powerapps/guidance/planning/introduction)

## <a name="power-apps-for-app-users"></a>アプリ ユーザー向け Power Apps

自分作成したアプリ、またはを他の誰かが作成し共有したアプリを、ブラウザーやモバイル デバイス (スマートフォンやタブレット) で実行できます。 詳細: [アプリの検索と実行](user/index.md)

## <a name="power-apps-for-admins"></a>管理者向け Power Apps

Power Apps 管理者は、**Power Platform 管理センター** ([admin.powerplatform.microsoft.com](https://admin.powerplatform.microsoft.com)) を使用して、環境の作成と管理、リアルタイムでのセルフヘルプ レコメンデーションと Power Apps と Power Automate のサポートの取得、Common Data Service 分析の表示を行うことができます。 詳細: [Power Platform の管理](/power-platform/admin/admin-guide)

> [!NOTE] 
> 管理者は、**Power Apps 管理センター** ([admin.powerapps.com](https://admin.powerapps.com)) を使用して、環境、ユーザー、ロール、データ損失防止ポリシーを作成し、管理できます。


## <a name="power-apps-for-developers"></a>開発者向け Power Apps

開発者は、ビジネス アプリの作成とカスタマイズを拡張するコードを記述できるアプリの作成者です。 開発者はコードを使用してデータやメタデータの作成、Azure 関数、プラグイン、ワークフロー拡張を使用したサーバー側ロジックの適用、JavaScript を使用したクライアント側ロジックの適用、仮想エンティティと Webhook を使用した外部データとの統合、カスタム コネクタのビルド、統合ソリューションを作成するためのアプリの Web サイト エクスペリエンスへの組み込みを行うことができます。 詳細: [開発者向け Power Apps](/powerapps/#pivot=home&panel=developer)

## <a name="power-apps-and-dynamics-365"></a>Power Apps と Dynamics 365

Dynamics 365 Sales、Dynamics 365 Customer Service、Dynamics 365 Marketing などの Dynamics 365 アプリケーションでも、データを格納してセキュリティ保護するため、Power Apps で利用されている基盤のデータ プラットフォーム (Common Data Service) が使用されます。 これにより Power Apps と Common Data Service を使用して、統合することなく、すでに Dynamics 365 で使用されているコア ビジネス データに直接アプリを構築することができます。 詳細: [Dynamics 365 と Common Data Service](maker/common-data-service/data-platform-intro.md#dynamics-365-and-common-data-service)

## <a name="try-power-apps-for-free"></a>無料で Power Apps を試す

[30 日間の試用版](maker/signup-for-powerapps.md)、または [コミュニティ プラン](maker/dev-community-plan.md) にサインアップすることで、Power Apps を無料で試すことができます。

## <a name="purchase-power-apps"></a>Power Apps の購入

Power Apps の購入を決定した場合は、詳細をこちらでご覧ください: [Power Apps を購入する](/power-platform/admin/signup-for-powerapps-admin)。

## <a name="power-apps-us-government-plans"></a>Power Apps 米国政府機関プラン

Power Apps US Government は、米国政府機関向けのいくつかのプランで構成されており、米国公的機関の独自の進化し続ける要件に対応しています。 Power Apps GCC の環境は、edRAMP High、DoD DISA IL2、および刑事司法制度に対する要件 (CJI データ タイプ) を含め、クラウド サービスに対する政府の要件への準拠を提供します。 詳細: [Power Apps US Government](/power-platform/admin/powerapps-us-government)
