---
title: '開発者: Common Data Service のメタデータで作業する際のベスト プラクティスおよびガイダンス | Microsoft Docs'
description: Power Apps で Common Data Service の開発者がメタデータで作業している間のベスト プラクティスおよびガイダンス。
services: ''
suite: powerapps
documentationcenter: na
author: jowells
manager: austinj
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/12/2018
ms.author: jowells
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 9dfc455ce9903c95b78e24b2aba25a5fbe6d8734
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "2883545"
---
# <a name="best-practices-and-guidance-while-working-with-metadata-for-the-common-data-service"></a>Common Data Service  のメタデータで作業している間のベスト プラクティスおよびガイダンス

下の一覧では、Common Data Service 内でのメタデータとの対話および作業に関するすべてのガイダンスとベスト プラクティスを示しています。


|ベスト プラクティス  |説明  |
|---------|---------|
|[公開メタデータの取得](retrieve-published-metadata.md)     |非公開メタデータを取得すると、要求自体の処理にオーバーヘッドが追加され、処理が遅くなるだけでなく、要求者が予期しないメタデータを返す可能性もあります。         |
|[クエリ API によってエンティティの特定の列を取得](retrieve-specific-columns-entity-via-query-apis.md)     |データを取得するために送信されたクエリには、All Columns ではなく、クエリに関連付けられている ColumnSet のインスタンス内の特定の列を含める必要があります。         |

### <a name="see-also"></a>関連項目
[コードを使用してメタデータを扱う](../../metadata-services.md)<br />