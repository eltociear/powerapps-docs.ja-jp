---
title: 'サンプル: REST リスナー (Common Data Service) | Microsoft Docs'
description: このサンプルでは、Azure Service Bus リスナーを REST エンドポイント契約に対して記述する方法を示します。
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: samples
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 03e5fbf4511a651baccc79ef512d7439a23cee6f
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749303"
---
# <a name="sample-rest-listener"></a>サンプル: REST リスナー

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-rest-listener -->

このサンプルでは、`Azure Service Bus` リスナーを `REST` エンドポイント契約に対して記述する方法を示します。 サンプルは [ここ](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RESTListener) からダウンロードできます。

このサンプルでは、メッセージがサービス バスの `REST` エンドポイントにポストされると常に実行される、リモート サービス プラグインを登録します。 このプラグインは実行されるときにメッセージに含まれる実行コンテキストの内容をコンソールへ出力します。
