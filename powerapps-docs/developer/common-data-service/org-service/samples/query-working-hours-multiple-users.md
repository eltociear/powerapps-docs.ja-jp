---
title: 'サンプル: 複数ユーザーの作業時間のクエリ (Common Data Service) | Microsoft Docs'
description: このサンプルは、複数のユーザーの作業時間を照会する方法を示します。
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
ms.openlocfilehash: 3694c3180d3183f2fbae44c8e59acbebb6a548b0
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934251"
---
# <a name="sample-query-the-working-hours-of-multiple-users"></a>サンプル: 複数ユーザーの作業時間のクエリ

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-query-working-hours-multiple-users -->

このサンプルは、[QueryMultipleSchedulesRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.querymultipleschedulesrequest?view=dynamics-general-ce-9) メッセージを使用して複数のユーザーの作業時間を取得する方法を示します。 サンプルは [ここ](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23) からダウンロードできます。

このサンプルではシステムに存在しない追加のユーザーが必要です。 サンプルの実行前に、次に **Office 365** で示した**通り**、手動で必要になったユーザーを作成します。 `yourorg` を組織の `OrgName` で置換します。

**名**: Kevin<br/>
**姓**: Cook<br/>
**セキュリティ ロール**: 営業課長<br/>
**ユーザー名**: kcook@yourorg.onmicrosoft.com<br/>

## <a name="how-to-run-this-sample"></a>このサンプルを実行する方法

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>このサンプルの概要

`QueryMultipleScheduleRequest` メッセージは、指定されたパラメーターに適合する空き時間ブロックに対する複数のリソースを検索する必要があるデータが含まれているシナリオで使用するためのものです。

## <a name="how-this-sample-works"></a>このサンプルがどのように動作するか

[このサンプルの概要](#what-this-sample-does) で説明されているシナリオをシミュレートするために、サンプルは次のことを行います。

### <a name="setup"></a>セットアップ

1. 組織の現在のバージョンをチェックします。
2. **Office 365** で手動で作成された現在のユーザーの情報および ユーザーも取得します。

### <a name="demonstrate"></a>使用方法

`QueryMultipleScheduleRequest` メッセージは、現在のユーザーおよび手動で作成されたユーザーの作業時間を取得します。

### <a name="clean-up"></a>クリーン アップ

[セットアップ](#setup) で作成されたレコードを削除するオプションを表示します。 サンプルで作成されるエンティティおよびデータを検証する場合、削除は任意です。 手動でレコードを削除することで同じ結果を得られます。
