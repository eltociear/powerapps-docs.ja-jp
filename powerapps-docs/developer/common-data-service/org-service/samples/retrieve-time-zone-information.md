---
title: 'サンプル: タイム ゾーン情報の取得 (Common Data Service) | Microsoft Docs'
description: このサンプルでは、タイム ゾーン情報を取得する方法を示します
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
ms.openlocfilehash: ed38ac3b9b699e8ec71b1c145434907055e00f30
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749295"
---
# <a name="sample-retrieve-time-zone-information"></a>サンプル: タイム ゾーン情報の取得

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-retrieve-time-zone-information -->

このサンプルでは、タイム ゾーン情報を取得する方法を示します。 サンプルは [ここ](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RetrieveTimeZone) からダウンロードできます。

## <a name="how-to-run-this-sample"></a>このサンプルを実行する方法

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>このサンプルの概要

`RetrieveAllTimeZonesForLocale` メソッドは、すべてのタイム ゾーンを取得するために現在のロケール ID を使用するシナリオで使用するためのものです。

## <a name="how-this-sample-works"></a>このサンプルがどのように動作するか

[このサンプルの概要](#what-this-sample-does) で説明されているシナリオをシミュレートするために、サンプルは次のことを行います。

### <a name="setup"></a>セットアップ

1. 組織の現在のバージョンをチェックします。

### <a name="demonstrate"></a>使用方法

1. `RetrieveCurrentUSerSettings` メソッドは、現在のユーザーのタイムゾーン コードとロケール ID を取得します。
2. `RetrieveAllTimeZonesForLocale` メソッドは、現在のロケール ID を使用してすべてのタイム ゾーンを取得します。
3. `GetTimeZoneCodeByLocaleAndName` メソッドは、名前とロケール ID によりタイム ゾーンを取得します。
4. `RetrieveTimeZoneById` メソッドは、ID によりタイム ゾーンを取得します。
5. `RetrieveTimeZonesLessThan50` メソッドは、50 未満のタイム ゾーンを取得します。
6. `RetrieveLocalTimeFromUTCTime` メソッドは、UTC 時間からローカル時間を取得します。
7. `RetrieveUTCTimeFromLocalTime` メソッドは、ロケール時間から UTC 時間を取得します。

### <a name="clean-up"></a>クリーン アップ

1. [セットアップ](#setup) で作成されたサンプル データを削除するためのオプションを表示します。

    サンプルで作成されるエンティティおよびデータを検証する場合、削除は任意です。 手動でレコードを削除することで同じ結果を得られます。
