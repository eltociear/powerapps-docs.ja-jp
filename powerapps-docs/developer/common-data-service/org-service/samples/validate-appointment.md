---
title: 'サンプル: 予定の検証（Common Data Service）| Microsoft Docs'
description: このサンプルは予定の検証方法を示しています。
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
ms.openlocfilehash: 5bcced80e393616801ea4b40a7783daff36a985d
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749274"
---
# <a name="sample-validate-an-appointment"></a>サンプル: 予定の検証

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-validate-appointment -->

このサンプルは、[ValidateRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.validaterequest?view=dynamics-general-ce-9) メッセージを使用して予定を有効にする方法を説明します。 サンプルは [ここ](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ValidateAppointment) からダウンロードできます。

## <a name="how-to-run-this-sample"></a>このサンプルを実行する方法

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>このサンプルの概要

`ValidateRequest` メッセージはシナリオで使用するためのもので、予定またはサービス予定 (サービス活動) に、必要に応じて、活動、期間、およびサイトの有効に使用可能なリソースがあることを確認するために必要なデータが含まれています。

## <a name="how-this-sample-works"></a>このサンプルがどのように動作するか

[このサンプルの概要](#what-this-sample-does) で説明されているシナリオをシミュレートするために、サンプルは次のことを行います。

### <a name="setup"></a>セットアップ

1. 組織の現在のバージョンをチェックします。
2. サンプル取引先担当者および活動関係者のレコードを作成します。
3. サンプル予定を作成します。

### <a name="demonstrate"></a>使用方法

1. 検証する予定を取得します。 
2. `ValidateRequest` メッセージはセットアップ (#setup) で作成した予定を検証します。

### <a name="clean-up"></a>クリーン アップ

1. [セットアップ](#setup) でレコードを削除するためのオプションを表示します。
    サンプルで作成されたエンティティおよびデータを検証する場合、削除は任意です。 手動でレコードを削除することで同じ結果を得られます。
