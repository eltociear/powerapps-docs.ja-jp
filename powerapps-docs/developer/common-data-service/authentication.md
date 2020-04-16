---
title: Common Data Service の Web サービスを使用した認証 (Common Data Service) | Microsoft Docs
description: 使用するソフトウェア フレームワークに依存する認証オプションを紹介します。
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: paulliew
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0503114883dd93a2b57d380cf5686853e0315ea8
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156435"
---
# <a name="authentication-with-common-data-service-web-services"></a>Common Data Service の Web サービス を使用した認証

Common Data Service の Web サービスを使用するクライアント アプリケーションを作成する場合、データへアクセスできるようにするための認証が必要です。 認証方法は、使用するソフトウェア フレームワークと、接続する Web サービスによって異なります。

## <a name="net-framework-applications"></a>.NET Framework アプリケーション

クライアント アプリケーションが .NET Framework を使用する場合、2 つのバージョンがあります。

- OAuth
- Office 365

### <a name="oauth"></a>OAuth

OAuthは、OData RESTful Web サービス (Web API および OData グローバル検索サービス) および SOAP Web サービス (組織サービスおよび探索サービス) の*両方*へのアクセスを提供するため、認証に適した手段です。 

OAuth は以下のものをサポートすることも必要です。 
 - 2 要素認証 (2FA) などの条件付きアクセスに対する Azure Active Directory の構成
 - サーバー間認証シナリオを有効にするクライアント シークレットを使用する
 - Single Page Application (SPA) に接続するクロス オリジン リソース共有 (CORS)

詳細: [Common Data Service で OAuth を使用する](authenticate-oauth.md)

### <a name="office-365"></a>Office 365

Office 365 の認証では、SOAP Web サービスのみで .NET Framework SDK アセンブリを使用する必要があります。

Office 365 の認証を使用する場合、OAuth で行うようにアプリケーションを登録する必要はありません。 有効なユーザーに対して、ユーザー プリンシパル名 (UPN) およびパスワードを単に提供する必要があります。

詳しくは：[ .NET Frameworkアプリケーションを使用した認証](authenticate-dot-net-framework.md)、[WS-Trust セキュリティ プロトコルを使用した Office365 認証の運用](authenticate-office365-deprecation.md) を参照してください

## <a name="all-other-software-frameworks"></a>他のすべてのソフトウェア フレームワーク

.NET Framework 以外を使用している場合は、OAuth を使用して認証し、OData RESTful Web サービス (Web API および OData グローバル検索サービス) を使用する必要があります。

詳細: [Common Data Service で OAuth を使用する](authenticate-oauth.md)
