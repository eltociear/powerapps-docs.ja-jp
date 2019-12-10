---
title: アプリ作成の概要 | Microsoft Docs
description: キャンバス モードまたはモデル駆動型モードのいずれかでアプリを作成し、Common Data Service を組み込む方法の概要
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.date: 12/05/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 79a1a5351bc3fe72a7558697e7cf8e8dfa079ce8
ms.sourcegitcommit: d194d2fa009ca7bfcbe95e5f31473832a130e0a6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74959405"
---
# <a name="overview-of-creating-apps-in-power-apps"></a>Power Apps でのアプリ作成の概要

Power Apps は、ビジネス アプリ向けの生産性の高い開発プラットフォームであり、4 つの主要コンポーネントを備えています。

- [キャンバス アプリ](canvas-apps/getting-started.md)は、ユーザー エクスペリエンスから始まります。空白のキャンバスを使用して高度にカスタマイズされたインターフェイスを作成し、200 種類のデータ ソースのいずれかに接続します。 Web、モバイル、タブレット用のキャンバス アプリを構築できます。
- [モデル駆動型アプリ](model-driven-apps/model-driven-app-overview.md)は、データ モデルから始まります。Common Data Service のコア ビジネス データとプロセスの形状を基に構築し、フォーム、ビューなどのコンポーネントをモデル化します。 モデル駆動型アプリでは、デバイス間の応答性が高い優れた UI を自動的に生成できます。
- [ポータル](portals/overview.md)では、外部向けの Web サイトの作成を開始します。これにより、組織外のユーザーがさまざまな ID でサインインしたり、Common Data Service でデータを作成および表示したり、匿名でコンテンツを参照したりできるようになります。
- [Common Data Service](common-data-service/data-platform-intro.md) は、Power App に付属しているデータ プラットフォームです。ビジネス データの格納とモデリングを行うことができます。 これは Dynamics 365 アプリが構築されているプラ​​ットフォームです。Dynamics をご利用の場合、お客様のデータは既に Common Data Service に格納されています。

初めてのアプリでも構築は簡単で単純です。 30 日間の無料試用プランと無料コミュニティ プランがあるので、最適なプランを見つけて始めてみてください。

## <a name="canvas-apps"></a>キャンバス アプリ

キャンバス アプリでは、ユーザー エクスペリエンスとインターフェイスを希望どおりに柔軟に調整できます。 アプリの外観に自分の創造性とビジネス センスを生かすことができます。

次のように、データが保存されている Microsoft ツールからアプリを構築することができます。

- [SharePoint リストから](canvas-apps/app-from-sharepoint.md#create-an-app-from-within-sharepoint-online)
- [Power BI ダッシュボードから](canvas-apps/embed-powerapps-powerbi.md)

キャンバス アプリの作成は簡単です。Power Apps では、次のようないくつかの方法でアプリを検索したり、作成したりできます。

- [データから](canvas-apps/app-from-sharepoint.md)
- [サンプルから](canvas-apps/open-and-run-a-sample-app.md)
- [Common Data Service ソースから](canvas-apps/data-platform-create-app.md)
- [空白のキャンバスから](canvas-apps/data-platform-create-app-scratch.md)
- [AppSource を介して](../user/app-source.md)

## <a name="model-driven-apps"></a>モデル駆動型アプリ

モデル駆動型アプリを作成すると、Common Data Service の機能をすべて使用して、フォーム、ビジネス ルール、プロセス フローを短時間で構成できます。 モデル駆動型アプリは Power Apps サイトから作成します。

モデル駆動型アプリの構築は簡単です。以下のトピックから参照してください。

- [アプリを作成する](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-app)
- [フォームの作成および設計](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-design-forms)
- [ビューの作成または編集](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-views)
- [システム グラフの作成または編集](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-system-chart)
- [ダッシュボードの表示または編集](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-dashboards)
- [セキュリティの追加](https://docs.microsoft.com/dynamics365/customer-engagement/customize/manage-access-apps-security-roles)
- [ビジネス ロジックの追加](https://docs.microsoft.com/dynamics365/customer-engagement/customize/guide-staff-through-common-tasks-processes)

## <a name="common-data-service"></a>Common Data Service

Common Data Service を使用して、一連の標準エンティティとカスタム エンティティ内にデータを安全に格納して、管理できます。また、必要に応じてそれらのエンティティにフィールドを追加できます。

Common Data Service の使用方法は簡単です。 たとえば、次の項目から始めることができます。

- [カスタム エンティティの作成](common-data-service/data-platform-create-entity.md)
- [フィールドの管理](common-data-service/data-platform-manage-fields.md)
- [カスタム オプション セットの作成](common-data-service/custom-picklists.md)
- [ビジネス ルールを作成する](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-business-rules-recommendations-apply-logic-form)

## <a name="canvas-and-model-driven-artifacts"></a>キャンバスおよびモデル駆動型の成果物

キャンバス アプリとモデル駆動型アプリのエクスペリエンスをマージすると、これらの成果物はキャンバス アプリまたはモデル駆動型アプリのどちらかと関連性を持ちます。

| 成果物            | アプリの種類     |
|---------------------|--------------|
| エンティティ > ビュー      | モデル駆動 |
| エンティティ > フォーム      | モデル駆動 |
| エンティティ > ダッシュボード | モデル駆動 |
| 接続         | キャンバス       |
| ゲートウェイ            | キャンバス       |
| カスタム コネクタ   | キャンバス       |
| アプリ > インポート       | キャンバス       |

アプリの構築後は、チーム メンバーと[共有](canvas-apps/share-app.md)できます。
