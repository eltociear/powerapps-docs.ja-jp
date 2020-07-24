---
title: Power Platform 用病院緊急時対応サンプル ソリューションの概要 | Microsoft Docs
description: 病院緊急時対応ソリューションの概要を示します。
author: pankajarora-msft
manager: annbe
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 04/23/2020
ms.author: pankar
ms.reviewer: kvivek
ms.openlocfilehash: 4a4993bb7c54126d2161c11da516407c7d9f86b0
ms.sourcegitcommit: 997384ebd01bda4f456f08689e024fb8ca5bf057
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2020
ms.locfileid: "3455384"
---
# <a name="hospital-emergency-response---power-platform-sample-solution"></a>病院緊急時対応 - Power Platform サンプル ソリューション

病院緊急時対応サンプル ソリューションは、医療機関が利用可能なベッドと備品、COVID-19 関連患者、人員配置、退院予定者の状況認識のためのデータを収集するための一連の機能を提供します。 このソリューションでは、重要なデータとインサイトを要約したダッシュボードが提供されるため、リソースの効率的な導入と使用をもたらす情報に基づいた意思決定が可能になります。

> [!div class="mx-imgBorder"] 
> ![病院緊急時対応アプリ](media/conf-ermerg-response-solution-overview.png)

病院緊急時対応ソリューションの主なコンポーネントは次のとおりです:

- **現場スタッフ向けのモバイル アプリ**: 看護師や医師などの現場スタッフは、モバイル アプリを使用して、必要に応じてすばやく情報の表示と入力を行うことができます。
- **病院管理者向け Web アプリ**：病院の管理者はこのアプリを使用して、ソリューションが機能するために必要なシステムデータを追加、管理できます。
- **医療の意思決定者向けのダッシュボード**: ダッシュボードを使用すると、効率的な意思決定に役立つ重要なデータとメトリックをすばやく表示できます。

[!include[cc-lang](includes/cc-lang.md)]


## <a name="demo-quick-overview"></a>デモ: 概要

病院緊急時対応ソリューションの概要をご覧ください。

<br/>

> [!VIDEO https://www.youtube.com/embed/Dg-i3F9G01I]

## <a name="licensing-requirements"></a>ライセンス要件

- Power Apps ライセンス。
- このソリューションの一部として利用可能な Power BI ダッシュボードを使用する場合は、Power BI ライセンス。

ライセンスに関する質問については、最寄りの Microsoft アカウント担当者にお問い合わせください。

関連項目: [Power Platform のライセンスの概要](https://docs.microsoft.com/power-platform/admin/pricing-billing-skus)

## <a name="start-here"></a>ここから開始

|タスク​​  | 対象ユーザー|サーバーベースの統合で使用する各サイトの構成の要件については、「|
|--|--|--|
|サンプル アプリとダッシュボードのダウンロードおよび展開|IT 管理者|[病院緊急時対応アプリをデプロイする](deploy-configure.md)|
|管理アプリを使用してマスター データを追加/管理する|ビジネス管理者|[組織のマスター データを構成、管理する](configure-data-reporting.md#configure-and-manage-master-data-for-your-organization)|
|ダッシュボードを表示して情報分析と意思決定に使用する|ビジネス管理者|[Common Data Service ダッシュボードを表示する](configure-data-reporting.md#view-common-data-service-dashboards)<br/><br/>[Power BI ダッシュボードの表示](configure-data-reporting.md#view-power-bi-dashboard)|
|モバイル アプリを使用して、人工呼吸器、人員配置、退院保留、COVID-19 に関連する患者のデータを追跡します|現場スタッフ|[Hospital Emergency Response モバイル アプリを使用する](use.md)
|管理アプリを使用してモバイル アプリからフィードバックを追跡する|業務管理者、IT 管理者|[アプリ フィードバックの表示および管理](configure-data-reporting.md#view-and-manage-app-feedback)|


## <a name="issues-and-feedback"></a>問題とフィードバック

- 病院緊急時対応サンプル アプリに関する問題を報告するには、<https://aka.ms/emergency-response-issues> にアクセスしてください。

- 病院緊急時対応サンプル アプリに関するフィードバックについては、<https://aka.ms/emergency-response-feedback> にアクセスしてください。

### <a name="disclaimer"></a>免責事項

このアプリはサンプルであり、参照用情報の頒布のみを目的として、Microsoft Power Platform と共に使用することができます。 このアプリは、病気やその他の疾患の診断、治療、軽減、手当て、または防止のために使用することを想定した医療デバイス、臨床サポート、診断ツール、またはその他のテクノロジーとして使用することを意図したものではありません。このアプリをそのような目的のために使用するためのライセンスや権利は、Microsoft によって付与されていません。 このアプリは、専門的な医療のアドバイス、診断、手当て、または判断の代替となるように設計または意図されていないため、そのようには使用しないでください。 お客様は、このアプリのいかなる使用に関しても単独でリスクと責任を負うものとします。 Microsoft は、このアプリまたはアプリと共に提供される関連資料が、何らかの医療目的のために適切であること、また任意の人物の健康や医療に関する要求を満たすことを保証することはしません。 このアプリに含まれているサンプル データは、説明のみを目的としたもので、架空のものです。 実在する名称とは一切関係ありません。
