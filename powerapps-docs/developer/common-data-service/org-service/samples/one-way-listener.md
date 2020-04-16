---
title: 'サンプル: 一方向リスナー (Common Data Service) | Microsoft Docs'
description: このサンプルは、アプリケーションがメッセージが一方向エンドポイントにポストされると常に実行するリモート サービス プラグインを登録する方法を示します。
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
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
ms.openlocfilehash: 5e588160d35ccc86155134584b4031eb795e4191
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155723"
---
# <a name="sample-one-way-listener"></a>サンプル: 一方向リスナー

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-one-way-listener -->

このサンプルでは、`Azure Service Bus` リスナーを一方向エンドポイント契約に対して記述する方法を示します。 サンプルは [ここ](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/OneWayListeners) からダウンロードできます。

このサンプル リスナー アプリケーションによって登録されるリモート サービス プラグインは、メッセージが `Azure Service Bus` の一方向エンドポイントにポストされると常に実行します。 このプラグインが実行するとき、メッセージに含まれる実行コンテキストの内容をコンソールに出力します。 
