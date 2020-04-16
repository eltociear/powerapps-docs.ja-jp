---
title: Web API を使用した Common Data Service への認証 (Common Data Service) | Microsoft Docs
description: Web API を使用して認証を管理するさまざまな異なる方法について
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: 767f39d4-6a8e-48f0-bf7d-69ea1191acef
caps.latest.revision: 8
author: JimDaly
ms.author: jdaly
manager: annbe
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 85dbea11497c05393c1376f53318ae8a50e22930
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155111"
---
# <a name="authenticate-to-common-data-service-with-the-web-api"></a>Web API を使用して Common Data Service への認証


[Common Data Service で OAuth を使用する](../authenticate-oauth.md) の説明に従って、OAuth を使用する必要があります。

Web API を使用して認証を管理するのに入力するコードは、展開の種類およびコードがある場所によって異なります。  
  
### <a name="authenticate-with-javascript-in-web-resources"></a>Web リソースの JavaScript で認証する  

HTML Web リソース、フォーム スクリプト、またはリボン コマンドで JavaScript と共に Web API を使用する場合、認証用のコードを含める必要はありません。 これらのサポート案件ごとにユーザーは既にアプリケーションによって認証されており、認証はアプリケーションによって管理されています。  

JavaScript を使用して単一のページ アプリケーション (SPA) を作成する場合は、[OAuth を使用するクロス オリジン リソース共有を使用して単一ページのアプリケーションへ接続する](../oauth-cross-origin-resource-sharing-connect-single-page-application.md) に説明されている adal.js ライブラリを使用できます。  
  
### <a name="see-also"></a>関連項目
 
[Common Data Service Web API の使用](overview.md)<br />
[Web API の種類および操作](web-api-types-operations.md)<br />
[Web API を使用して演算を実行する](perform-operations-web-api.md)<br />
[Common Data Service で OAuth を使用する](../authenticate-oauth.md)<br />
[OAuth を使用するクロス オリジン リソース共有を使用して、単一のページ アプリケーションに接続する](../oauth-cross-origin-resource-sharing-connect-single-page-application.md)
