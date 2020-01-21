---
title: 'サンプル: 絶対 URL およびサイト コレクション URL の取得 (Common Data Service) | Microsoft Docs'
description: このサンプルは、SharePoint の場所の絶対 URL とサイト コレクション URL を取得する方法を示します。
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
ms.openlocfilehash: 43929bf09ee211596c6a2043be48a796c387e5e9
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934235"
---
# <a name="sample-retrieve-absolute-url-and-site-collection-url-of-a-location-record"></a>サンプル: 場所レコードの絶対 URL およびサイト コレクション URL の取得

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/integration-dev/sample-retrieve-absolute-url-and-site-collection-url-of-a-location-record -->

このサンプルは、[RetrieveAbsoluteAndSiteCollectionUrlRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.retrieveabsoluteandsitecollectionurlrequest?view=dynamics-general-ce-9) メッセージを使用して SharePoint サーバー絶対 URL とサイト コレクション URL を取得する方法を示します。

## <a name="how-to-run-this-sample"></a>このサンプルを実行する方法

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>このサンプルの概要

`RetrieveAbsoluteAndSiteCollectionUrlRequest` メッセージは、SharePoint の場所レコードの絶対 URL およびサイト コレクションを取得するために必要なデータを含むシナリオで使用するためのものです。

## <a name="how-this-sample-works"></a>このサンプルがどのように動作するか

[このサンプルの概要](#what-this-sample-does) で説明されているシナリオをシミュレートするために、サンプルは次のことを行います。

### <a name="setup"></a>セットアップ

1. 組織の現在のバージョンをチェックします。 
1. `CreateRequireRecords` メソッドは、サンプルで使用するエンティティ レコードを作成します。

### <a name="demonstrate"></a>使用方法

`RetrieveAbsoluteAndSiteCollectionUrlRequest` は、SharePoint のレコードの絶対 URL とサイト コレクション URL を取得するために使用されます。

### <a name="clean-up"></a>クリーン アップ

[セットアップ](#setup) で作成されたレコードを削除するオプションを表示します。 サンプルで作成されるエンティティおよびデータを検証する場合、削除は任意です。 手動でレコードを削除することで同じ結果を得られます。
