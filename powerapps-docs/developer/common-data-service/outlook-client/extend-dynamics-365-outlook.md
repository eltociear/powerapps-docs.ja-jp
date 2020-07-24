---
title: Dynamics 365 for Outlook の拡張 (Common Data Service) | Microsoft Docs
description: Dynamics 365 for Outlook を使うと、ユーザーはオフラインでサーバーに接続していない状態でも、データと対話することができます。 Common Data Service は、カスタム コードから Web サービス オフラインを呼び出すことによってソリューションをオフラインのシナリオを拡張する機能を備えています。 また、SDK アセンブリで、同期、オフラインとオンラインの切り替え、 Dynamics 365 for Outlook クライアントの状態の検証など、Outlookの基本的なアクションに対するプログラム的なサポートが提供されています。 オフラインのプログラムでは、 ASP.NET Development Server を使用します。
ms.custom: ''
ms.date: 04/07/2020
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: sriharibs
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8c8fc40f7a02d6b636b29758cd0964084b8e9333
ms.sourcegitcommit: 6acc6ac7cc1749e9681d5e55c96613033835d294
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "3238263"
---
# <a name="extend-dynamics-365-for-outlook"></a>Dynamics 365 for Outlook を拡張する

> [!IMPORTANT]
> 2020 年 3 月以降は、レガシー版 Dynamics 365 for Outlook（Outlook COM アドインとも呼ばれます）は非推奨となります。 2020 年 10 月 1 日までに、最新版の [Dynamics 365 App for Outlook](https://docs.microsoft.com/dynamics365/outlook-app/overview) に移行する必要があります。 マイクロソフトは、2020 年 10 月 1 日までは Outlook COM アドインのサポート、セキュリティ、その他の重要な更新の提供を継続します。
> 
> スムーズな移行を行うための詳細情報と手順については、[Dynamics 365 for Outlook (COM アドイン) ハンドブック](https://aka.ms/OutlookCOMPlaybook) をダウンロードしてください。

Dynamics 365 for Outlook を使うと、ユーザーはオフラインでサーバーに接続していない状態でも、データと対話することができます。 Common Data Service は、カスタム コードから Web サービス オフラインを呼び出すことによってソリューションをオフラインのシナリオを拡張する機能を備えています。 また、 <xref:Microsoft.Crm.Outlook.Sdk> アセンブリで、同期、オフラインとオンラインの切り替え、 Dynamics 365 for Outlook の状態の検証など、Outlookの基本的なアクションに対するプログラム的なサポートが提供されています。 オフラインのプログラムでは、 ASP.NET Development Server を使用します。  
  
 Dynamics 365 では、管理者がユーザーのフィルターをカスタマイズして管理できるようにする機能を備えています。 フィルターのテンプレートは、Dynamics 365 for Outlook のエンティティの同期の開始点を提供します。 フィルターは、オフライン対応の Dynamics 365 ソリューションのために Outlook および SQL Server 2008 Express Edition に同期するエンティティ コレクションを決定します。  
  
## <a name="in-this-section"></a>このセクションの内容

[オフラインと Outlook のフィルターおよびテンプレート](offline-outlook-filters-templates.md)<br />  
[サンプル: Outlook フィルターの取得](sample-create-retrieve-outlook-filters.md)<br />  
[サンプル: Outlook メソッドの使用](sample-outlook-methods.md)<br />
  
## <a name="related-sections"></a>関連セクション

<!-- TODO:
[Extend Dynamics 365](extend-dynamics-365-server.md)<br />
[Supported Extensions for Dynamics 365](supported-extensions.md)<br />
[The Metadata and Data Models in Dynamics 365](metadata-data-models.md)<br />
[Extend Dynamics 365 on the server](extend-dynamics-365-server.md)<br />
[Extend Dynamics 365 on the client](extend-client.md)<br />
[Customize Dynamics 365 applications](customize-dev/customize-applications.md)<br />
[Package and distribute extensions using solutions](package-distribute-extensions-use-solutions.md)<br />
[Integrate Dynamics 365 with SharePoint](integration-dev/integrate-sharepoint.md)<br />
 -->
<xref href="Microsoft.Dynamics.CRM.savedquery?text=savedquery EntityType" /><br />
[SavedQuery エンティティ](../reference/entities/savedquery.md)<br />
  

