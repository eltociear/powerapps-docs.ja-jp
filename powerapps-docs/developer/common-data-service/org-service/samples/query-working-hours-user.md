---
title: 'サンプル: ユーザーの作業時間のクエリ (Common Data Service) | Microsoft Docs'
description: このサンプルではユーザーの作業時間を取得する方法を説明します
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
ms.openlocfilehash: 5d2426d63e7c8444c22ea0103979ed8a2812724e
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934247"
---
# <a name="sample-query-the-working-hours-of-a-user"></a>サンプル: ユーザーの作業時間のクエリ

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-query-working-hours-user -->

このサンプルでは [QueryScheduleRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.queryschedulerequest?view=dynamics-general-ce-9) メッセージを使用してユーザーの作業時間を取得する方法を説明します。 サンプルは[ここ](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/QueryWorkingHours
) からダウンロードできます。

## <a name="how-to-run-this-sample"></a>このサンプルを実行する方法

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>このサンプルの概要

`QueryScheduleRequest` メッセージは、指定されたパラメーターに適合する空き時間ブロックに対する指定されたリソースを検索する必要があるデータが含まれているシナリオで使用するためのものです。

## <a name="how-this-sample-works"></a>このサンプルがどのように動作するか

[このサンプルの概要](#what-this-sample-does) で説明されているシナリオをシミュレートするために、サンプルは次のことを行います。

### <a name="setup"></a>セットアップ

組織の現在のバージョンをチェックします。

### <a name="demonstrate"></a>使用方法

1. `WhoAMIRequest` メッセージは、現在のユーザー情報を取得します。
2. `QueryScheduleRequest` メッセージは、現在のユーザーの作業時間を取得します。

### <a name="clean-up"></a>クリーン アップ

[セットアップ](#setup)で作成されたサンプル データを削除するオプションを表示します。 サンプルで作成されるエンティティおよびデータを検証する場合、削除は任意です。 手動でレコードを削除することで同じ結果を得られます。
