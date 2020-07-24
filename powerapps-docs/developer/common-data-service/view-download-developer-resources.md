---
title: Power Apps および Common Data Service の開発者リソースの表示またはダウンロード | MicrosoftDocs
description: Power Apps および Common Data Service の開発者リソースおよびサービス エンドポイント URL を検索する
keywords: ''
ms.date: 04/09/2020
ms.service: powerapps
ms.custom: ''
ms.topic: article
ms.assetid: e200d242-ff3f-48e5-af32-aed050e02441
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: pehecke
ms.suite: ''
ms.tgt_pltfrm: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: bd3b907411d0e43b572908204aeff9c64069ed15
ms.sourcegitcommit: cbaf5ba8b6435796a538ece2da5cc172c0781fad
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2020
ms.locfileid: "3254401"
---
# <a name="view-or-download-developer-resources"></a>開発者リソースの表示またはダウンロード

このページには、開発者向けリソースと、作業中の特定のインスタンスに関する情報があります。 

## <a name="view-the-developer-resources-page-for-your-environment"></a>環境の開発者リソース ページを表示する

1. [Power Apps](https://make.powerapps.com) にサインインして、右上隅で環境を選択します。

1. 右上隅の**設定**ボタンを選択してから、**詳細設定**を選択します。

    ![高度なカスタマイズ](media/advanced-customizations-menu.png)

1. **設定**ページで、**設定**の横にあるドロップダウン矢印を選択してから、**カスタマイズ**を選択します。

    ![カスタマイズの選択](media/dev-customization.png)

1. **カスタマイズ** ページで、**開発者リソース**を選択し、開発者向けのリソースを含むページを表示します。

    ![開発者リソース ページ](media/developer-resources-page.png)

次のセクションでは、開発者リソース ページで使用可能な情報について説明します。

## <a name="getting-started"></a>はじめに 

このセクションには、開発者がリソースを見つけることができるリンクを提供します。 次のリソースを使用できます。


|リンク |説明|
|---------|---------|
|[ディベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=551006)|開発者用ドキュメントのメイン エントリ ポイント。|
|[開発者フォーラム](https://go.microsoft.com/fwlink/?LinkId=550993)|他の開発者にして質問して答えをもらいます。|
|[SDK NuGet パッケージ](https://go.microsoft.com/fwlink/?LinkId=550994)|SDK アセンブリをプロジェクトに追加するには NuGet パッケージを検出します。|
|SDK のダウンロード|Microsoft ダウンロード センターで SDK パッケージをダウンロードとして出荷することはなくなりました。 代わりに、SDK アセンブリとツールは [NuGet パッケージ](https://go.microsoft.com/fwlink/?LinkId=550994) として使用可能です。 この記事の PowerShell スクリプトを使用して、SDK ツールの最新バージョンを取得します: [NuGet からツールをダウンロード](https://docs.microsoft.com/powerapps/developer/common-data-service/download-tools-nuget)|
|[サンプル コード](https://go.microsoft.com/fwlink/?LinkId=553007)|使用できるコード サンプルの一覧。|
|[開発者向けの概要](https://go.microsoft.com/fwlink/?LinkId=550995)|開発者の概要について説明するトピックにリンクします。|


## <a name="connect-your-apps-to-this-instance-of-common-data-service"></a>Common Data Service のこのインスタンスにアプリを接続する

このセクションには、Common Data Service インスタンスに接続するために必要な情報を提供します。

### <a name="instance-web-api"></a>インスタンスの Web API

これは、インスタンスの Web API の URL です。 Web API は OData v4 RESTful API です。 また、インスタンスで使用できるメタデータおよび操作を説明するサービス ドキュメントもダウンロードできます。 詳細: [開発者ドキュメント: Common Data Service Web API の使用](/powerapps/developer/common-data-service/webapi/overview)

### <a name="organization-service"></a>組織のサービス

これは、インスタンスの組織サービスの SOAP エンドポイントの URL です。
ここでは、このサービスについての WSDL をダウンロードできますが、通常、CrmSvcUtil.exe コード生成ツールを使用して .NET プロジェクトのエンティティ クラスを構築します。 詳細: 
- [開発者ドキュメント: コード生成ツール (CrmSvcUtil.exe) を使用して事前バインド型エンティティ クラスを作成する](/powerapps/developer/common-data-service/org-service/generate-early-bound-classes)
- [開発者ドキュメント: 組織サービスの使用](/powerapps/developer/common-data-service/org-service/overview)

### <a name="instance-reference-information"></a>インスタンス参照情報

この情報はインスタンスについて独自に説明しています。 GUID **ID** と**一意の名前**があります。
この情報は、インスタンスと共に Azure 拡張を使用するときに必要です。
詳細: [Azure 統合](/powerapps/developer/common-data-service/azure-integration)

## <a name="connect-your-apps-to-the-common-data-service-discovery-service"></a>アプリを Common Data Service 探索サービスに接続する

ユーザーは複数の Common Data Service 環境にアクセスできる場合があるので、探索サービスでは、ユーザーがユーザーの資格情報に基づいてアクセスできる使用可能な環境を取得できます。

### <a name="discovery-web-api"></a>検出 Web API

これは、インスタンスで使用するための探索サービスの RESTful OData v4 バージョンのエンドポイント アドレスです。 サービス ドキュメントはここでダウンロードできます。
詳細情報: [開発者ドキュメント: Web API を使用して組織の URL を検出する](/powerapps/developer/common-data-service/webapi/discover-url-organization-web-api)


### <a name="discovery-service"></a>探索サービス

これは、インスタンスで使用するための探索サービスの SOAP バージョンのエンドポイント アドレスです。 サービス ドキュメントはここでダウンロードできます。
詳細情報: [開発者ドキュメント: 組織サービスを使用して組織の URL を検出する](/powerapps/developer/common-data-service/org-service/discovery-service)
  
  

