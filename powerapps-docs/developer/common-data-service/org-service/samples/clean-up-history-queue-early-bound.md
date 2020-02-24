---
title: 'サンプル: キューの履歴をクリーンアップする (Common Data Service) | Microsoft Docs'
description: このサンプルではキューの履歴のクリーンアップ方法を示します
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 07e6849d7888550338206fd76fec174a0d25fade
ms.sourcegitcommit: 3bf59896a98e5f01289a2489e185f27518aeaec3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/15/2020
ms.locfileid: "2956222"
---
# <a name="sample-clean-up-history-for-a-queue"></a>サンプル: キューの履歴のクリーンアップ

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-clean-up-history-queue-early-bound -->

このサンプルは、非アクティブなアイテムに対して [RemoveFromQueueRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.removefromqueuerequest?view=dynamics-general-ce-9) を使用することで、キューの履歴をクリーンアップする方法を示します。 このコードは、キュー内の完了した通話を検索し、関連するキュー アイテムを削除します。 サンプルは [ここ](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/CleanHistoryQueue) からダウンロードできます。

## <a name="how-to-run-this-sample"></a>このサンプルを実行する方法

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>このサンプルの概要

`RemoveFromQueueRequest` メッセージは、非アクティブなアイテムでキューの履歴をクリーンアップするシナリオで使用することを目的としています。

## <a name="how-this-sample-works"></a>このサンプルがどのように動作するか

[このサンプルの概要](#what-this-sample-does) で説明されているシナリオをシミュレートするために、サンプルは次のことを行います。

### <a name="setup"></a>セットアップ

1. 組織の現在のバージョンをチェックします。
2. キュー インスタンスが作成され、プロパティ値が設定されます。
3. 電話活動インスタンスおよびキュー アイテム インスタンスも作成し、そのプロパティを初期化します。
4. 電話を完了としてマークします。 

### <a name="demonstrate"></a>使用方法

[RemoveFromQueueRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.removefromqueuerequest?view=dynamics-general-ce-9) メッセージを使用して、キューからの非アクティブな電話でのキュー アイテムを取得します。

### <a name="clean-up"></a>クリーン アップ

[セットアップ](#setup) で作成されたレコードを削除するオプションを表示します。 サンプルで作成されるエンティティおよびデータを検証する場合、削除は任意です。 手動でレコードを削除することで同じ結果を得られます。
