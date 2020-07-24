---
title: アプリの作成の概要 | Microsoft Docs
description: キャンバスまたはモデル駆動型モードでアプリを作成し、Common Data Service を組み込む方法に関する概要
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 06/16/2020
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: b92ce2a523c71ac4edc2075756cc9155903d40da
ms.sourcegitcommit: 213c46f7055eb71b9064b0645d8d17cf8eaad179
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/16/2020
ms.locfileid: "3456281"
---
# <a name="overview-of-creating-apps-in-power-apps"></a>Power Apps でのアプリの作成の概要

Power Apps は、ビジネス アプリ向けの生産性の高い開発プラットフォームであり、4 つの主要コンポーネントを備えています。

- キャンバス アプリ
- モデル駆動型アプリ
- ポータル
- Common Data Service

これらのそれぞれについて学習しましょう。

## <a name="canvas-apps"></a>キャンバス アプリ

[キャンバス アプリ](canvas-apps/getting-started.md)は、空白のキャンバスを使用して高度にカスタマイズされたインターフェイスを作成し、200 を超えるデータ ソースの中から選んだソースに接続するというユーザー エクスペリエンスから始まります。 Web、モバイル、タブレット PC アプリケーション用のキャンバス アプリを構築できます。

キャンバス アプリには、ユーザー エクスペリエンスやインターフェイスを自由にアレンジできる柔軟性が備わっています。 アプリのルック アンド フィールの方向性について創造性とビジネス感覚を発揮することができます。

次のように、データが保存されている Microsoft ツールからアプリを構築することができます。

- [SharePoint リストから](canvas-apps/app-from-sharepoint.md#create-an-app-from-within-sharepoint-online)
- [Power BI ダッシュボードから](canvas-apps/embed-powerapps-powerbi.md)

キャンバス アプリの作成は簡単です。Power Apps を使用して、次のようないくつかの方法でアプリを検索したり、作成したりできます。

- [データから](canvas-apps/app-from-sharepoint.md)
- [サンプルから](canvas-apps/open-and-run-a-sample-app.md)
- [Common Data Service ソースから](canvas-apps/data-platform-create-app.md)
- [空白のキャンバスから](canvas-apps/data-platform-create-app-scratch.md)
- [AppSource を介して](../user/app-source.md)

## <a name="model-driven-apps"></a>モデル駆動型アプリ

[モデル駆動型アプリ](model-driven-apps/model-driven-app-overview.md)は、データ モデルから始まります。Common Data Service のコア ビジネス データとプロセスの形状を基に構築し、フォーム、ビューなどのコンポーネントをモデル化します。 モデル駆動型アプリでは、デバイス間の応答性が高い優れた UI を自動的に生成できます。 

モデル駆動型アプリを作成すると、Common Data Service の機能をすべて使用して、フォーム、ビジネス ルール、プロセス フローを短時間で構成できます。 モデル駆動型アプリは Power Apps サイトから作成します。

モデル駆動型アプリの構築は簡単です。以下のトピックから参照してください。

- [アプリの作成](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-app)
- [フォームの作成および設計](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-design-forms)
- [ビューの作成または編集](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-views)
- [システム グラフの作成または編集](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-system-chart)
- [ダッシュボードの作成または編集](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-dashboards)
- [セキュリティの追加](https://docs.microsoft.com/dynamics365/customer-engagement/customize/manage-access-apps-security-roles)
- [ビジネス ロジックの追加](https://docs.microsoft.com/dynamics365/customer-engagement/customize/guide-staff-through-common-tasks-processes)

## <a name="portals"></a>ポータル

[ポータル](portals/overview.md)は、外部向け Web サイトの作成を支援します。この Web サイトにより、組織外のユーザーがさまざまな ID でサインインしたり、Common Data Service でデータを作成および表示したり、匿名でコンテンツを参照したりできるようになります。

次のトピックを使用して、ポータルをすぐに開始できます。

- [スターター ポータルの作成](/powerapps/maker/portals/create-portal)
- [ポータルのライフサイクルについて](/powerapps/maker/portals/admin/portal-lifecycle)
- [ポータル認証](/powerapps/maker/portals/configure/configure-portal-authentication)
- [ポータル用の Power BI 統合](/powerapps/maker/portals/admin/set-up-power-bi-integration)
- [ポータル用の Azure 統合](/powerapps/maker/portals/enable-azure-storage)

## <a name="common-data-service"></a>Common Data Service

[Common Data Service](common-data-service/data-platform-intro.md) は、Power Apps に付属しているデータ プラットフォームです。ビジネス データの格納とモデリングを行うことができます。 Dynamics 365 アプリ (Dynamics 365 Sales、Customer Service、Field Service、Marketing、Project Service Automation など) を構築するためのプラットフォームです。 Dynamics 365 をご利用のお客様の場合、データは既に Common Data Service 内にあります。

Common Data Service を使用して、一連の標準およびユーザー定義*エンティティ*内にデータを安全に格納し、管理できます。また、必要に応じてそれらのエンティティにフィールドを追加できます。

Common Data Service の使用を開始するのは簡単です。 たとえば、次の項目から始めることができます。

- [ユーザー定義エンティティの作成](common-data-service/data-platform-create-entity.md)
- [フィールドの管理](common-data-service/data-platform-manage-fields.md)
- [カスタム オプション セットの作成](common-data-service/custom-picklists.md)
- [ビジネス ルールの作成](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-business-rules-recommendations-apply-logic-form)

## <a name="planning-a-power-apps-app-or-project"></a>Power Apps アプリまたはプロジェクトの計画

初めてのアプリの構築を試してみるのは簡単です。 [30 日間の無料試用プラン](signup-for-powerapps.md)と無料の[コミュニティ プラン](dev-community-plan.md)があるので、ご自身にとって最適なプランを見つけて始めてください。

Power Apps を初めて使用する場合、Power Apps を使用してアイデアを完全に機能するソリューションに変換する方法について学ぶには、[Power Apps プロジェクトの計画](/powerapps/guidance/planning/introduction)から始めてください。


<!--## Canvas and model-driven artifacts

While we merge the experiences of canvas and model-driven apps, these artifacts will be relevant for either canvas apps or model-driven apps.

| Artifact            | App Type     |
|---------------------|--------------|
| Entity > Views      | Model-driven |
| Entity > Forms      | Model-driven |
| Entity > Dashboards | Model-driven |
| Connections         | Canvas       |
| Gateways            | Canvas       |
| Custom connectors   | Canvas       |
| Apps > Import       | Canvas       |

-->

