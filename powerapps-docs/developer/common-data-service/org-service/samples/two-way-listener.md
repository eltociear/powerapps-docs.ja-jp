---
title: 'サンプル: 二方向リスナー (Common Data Service) | Microsoft Docs'
description: このサンプルは双方向エンドポイント コントラクトに対して Azure Service Bus リスナーを記述する方法を示します。
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
ms.openlocfilehash: 66918421cb999ccb3d24764172bbf43062b49f6e
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749282"
---
# <a name="sample-two-way-listener"></a>サンプル: 二方向リスナー

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-two-way-listener -->

このサンプルでは、 `Azure Service Bus` リスナーを二方向エンドポイント契約に対して記述する方法を示します。 サンプルを [ここ](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/TwoWayListener) からダウンロードできます。

このサンプルは `Azure Service Bus` の双方向エンドポイントへメッセージが送信されるとき、常に実行されるリモート サービス プラグインを登録します。 このプラグインは実行されるときにメッセージに含まれる実行コンテキストの内容をコンソールへ出力します。
