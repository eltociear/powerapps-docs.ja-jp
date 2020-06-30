---
title: 'サンプル: クエリとメタデータの変更の検出 (Common Data Service) | Microsoft Docs'
description: このサンプルは、メタデータの変更をクエリして検出する方法を示しています
ms.custom: ''
ms.date: 05/08/2020
ms.reviewer: nabuthuk
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
ms.openlocfilehash: b702d0717cf13b70fb15ed57aeade2c59eed48b5
ms.sourcegitcommit: 3448869b74152e01a58f61c37d4361d8ae8bb09d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/09/2020
ms.locfileid: "3354198"
---
# <a name="query-and-detect-metadata-changes"></a>メタデータのクエリと変更の検出


このサンプルは、[RetrieveMetadataChangeRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.retrievemetadatachangesrequest?view=dynamics-general-ce-9) を使用して、メタデータの変更を取得して検出する方法を示しています。 サンプルは [ここ](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/MetadataQuery) からダウンロードできます。

## <a name="how-to-run-this-sample"></a>このサンプルを実行する方法

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>このサンプルの概要

`RetrieveMetadataChangeRequest` メッセージは、指定した基準を満たすメタデータ レコードの収集を取得する必要があるデータを含むシナリオで使用するためのものです。 [RetrieveMetadataChangesResponse](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.retrievemetadatachangesresponse?view=dynamics-general-ce-9) は、最後の要求後のメタデータ変更内容に関する情報を戻すために、後からこの要求を使用することができるタイムスタンプ値を返します。

## <a name="how-this-sample-works"></a>このサンプルがどのように動作するか

[このサンプルがおこなうこと](#what-this-sample-does) で説明されているシナリオをシミュレートするには、サンプルは次のことを行います。

### <a name="setup"></a>セットアップ

組織の現在のバージョンをチェックします。

### <a name="demonstrate"></a>実際にやってみます

1. `MetadataFilterExpression` メソッドは、フィルター式を作成して、返されるエンティティを、除外されたエンティティのリストにない非交差のユーザー所有のエンティティに制限します。 
2. `MetadataConditionExpression` メソッドは、オプションセット属性を返します。
3. `MetadataPropertiesExpression`メソッドは、属性に含まれるプロパティを制限します。
4. `LabelQueryExpression`メソッドは、返されるラベルをユーザーの優先する言語のラベルのみに制限します。
5. `RetrieveMetadataChangeRequest` メソッドはクエリのメタデータを取得します。


### <a name="clean-up"></a>クリーンアップ

[セットアップ](#setup) で作成されたサンプル データを削除するためのオプションを表示します。 サンプルで作成されるエンティティおよびデータを検証する場合、削除は任意です。 手動でレコードを削除することで同じ結果を得られます。
