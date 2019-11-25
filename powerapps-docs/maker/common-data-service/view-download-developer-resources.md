---
title: PowerApps および Common Data Service の開発者リソースの表示またはダウンロード | MicrosoftDocs
description: PowerApps および Common Data Service の開発者リソースおよびサービス エンドポイント URL を検索する
keywords: ''
ms.date: 09/25/2019
ms.service: powerapps
ms.custom: ''
ms.topic: article
ms.assetid: e200d242-ff3f-48e5-af32-aed050e02441
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: ae293843c38e7077580effd1c7670762cec91e1e
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "2700436"
---
# <a name="view-or-download-developer-resources"></a>開発者リソースの表示またはダウンロード

このページには、開発者のリソースと、作業中の特定のインスタンスに関する情報があります。 

## <a name="view-the-developer-resources-page-for-your-environment"></a>環境の開発者リソース ページを表示する

1. PowerApps ポータルで、![設定ボタン](../../administrator/media/settings-button-nav-bar.png) [設定] ボタンを選択し、**高度なカスタマイズ** を選択します。

    ![高度なカスタマイズ](media/advanced-customizations-menu.png)

1. **高度なカスタマイズ** パネル内で、**開発者リソース** リンクを選択します。<br />![開発者リソース リンク](media/developer-resources-link.png)

## <a name="getting-started"></a>はじめに 

このセクションには、開発者がリソースを見つけることができるリンクを提供します。 次のリソースを使用できます。


|リンク |説明|
|---------|---------|
|[デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=551006)|PowerApps と Common Data Service の開発者ドキュメントはここから参照できます。|
|[PowerApps コミュニティ/フォーラム](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1)|PowerApps コミュニティで質問して回答します。|
|[NuGetパッケージ](https://www.nuget.org/profiles/crmsdk)|SDK アセンブリをプロジェクトに追加するには NuGet パッケージを検出します。|
|[ツールのダウンロード](/powerapps/developer/common-data-service/download-tools-nuget)|必要なツールは NuGet からダウンロードできます。 最新バージョンを取得する際にこのページの PowerShell スクリプトを使用します。|
|[サンプル コード](https://go.microsoft.com/fwlink/?LinkId=553007)|PowerApps サンプルの GitHub リポジトリ。|
|[開発者向けの概要](https://go.microsoft.com/fwlink/?LinkId=550995)|開発者の概要について説明するトピックにリンクします。|

## <a name="connect-your-apps-to-this-instance-of-common-data-service"></a>Common Data Service のこのインスタンスにアプリを接続する

このセクションには、Common Data Service インスタンスに接続するために必要な情報を提供します。

### <a name="instance-web-api"></a>インスタンスの Web API

これは、インスタンスの Web API の URL です。 Web API は OData v4 RESTful API です。 また、インスタンスで使用できるメタデータおよび操作を説明するサービス ドキュメントもダウンロードできます。 詳細: [開発者ドキュメント: Common Data Service Web API の使用](/powerapps/developer/common-data-service/webapi/overview)

### <a name="organization-service"></a>組織のサービス

これは、インスタンスの組織サービスの SOAP エンドポイントの URL です。
ここでは、このサービスについての WSDL をダウンロードできますが、通常、CrmSvcUtil.exe コード生成ツールを使用して .NET プロジェクトのエンティティ クラスを構築します。 詳細: 
- [開発者ドキュメント: コード生成ツール (CrmSvcUtil.exe) を使用して事前バインド型エンティティ クラスを生成する](/powerapps/developer/common-data-service/org-service/generate-early-bound-classes)
- [開発者ドキュメント: 組織サービスを使用したデータまたはメタデータの読み取りと書き込み](/powerapps/developer/common-data-service/org-service/overview)

### <a name="instance-reference-information"></a>インスタンス参照情報

この情報はインスタンスについて独自に説明しています。 GUID **ID** と**一意の名前**があります。
この情報は、インスタンスと共に Azure 拡張を使用するときに必要です。
詳細: [開発者ドキュメント: Dynamics 365 の Azure 拡張機能](/dynamics365/customer-engagement/developer/azure-extensions)

## <a name="connect-your-apps-to-the-common-data-service-discovery-service"></a>アプリを Common Data Service 探索サービスに接続する

ユーザーは複数の Common Data Service 環境にアクセスできる場合があるので、探索サービスでは、ユーザーがユーザーの資格情報に基づいてアクセスできる使用可能な環境を取得できます。

### <a name="discovery-web-api"></a>検出 Web API

これは、インスタンスで使用するための探索サービスの RESTful OData v4 バージョンのエンドポイント アドレスです。 サービス ドキュメントはここでダウンロードできます。
詳細情報: [開発者ドキュメント: Web API を使用して組織の URL を検出する](/powerapps/developer/common-data-service/webapi/discover-url-organization-web-api)


### <a name="discovery-service"></a>探索サービス

これは、インスタンスで使用するための探索サービスの SOAP バージョンのエンドポイント アドレスです。 サービス ドキュメントはここでダウンロードできます。
詳細情報: [開発者ドキュメント: 探索サービスを使用して組織の URL を検出する](/dynamics365/customer-engagement/developer/org-service/discover-url-organization-organization-service)
  
