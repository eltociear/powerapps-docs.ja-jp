---
title: 'サンプル: 保存されたクエリの検証と実行（Common Data Service）| Microsoft Docs'
description: このサンプルでは、保存済みクエリを検証して実行する方法を示しています。
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
ms.openlocfilehash: ba1bd8e9cef6cbfc30e6289a20c6d79114d156f9
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155507"
---
# <a name="sample-validate-and-execute-a-saved-query"></a>サンプル: 保存済みクエリの検証および実行

<!-- Needs supporting conceptual topic 
https://docs.microsoft.com/dynamics365/customer-engagement/developer/org-service/sample-validate-execute-saved-query
-->
このサンプルでは、[IOrganizationService.ValidateSavedQueryRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.validatesavedqueryrequest?view=dynamics-general-ce-9) メッセージを使用して FetchXML クエリを検証し、続いて [IOrganizationService.ExecuteByIdSavedQueryRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.executebyidsavedqueryrequest?view=dynamics-general-ce-9) メッセージ使用してクエリを実行する方法を示します。 サンプルは [ここ](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ValidateandExecuteSavedQuery) からダウンロードできます。

## <a name="how-to-run-this-sample"></a>このサンプルを実行する方法

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]


## <a name="what-this-sample-does"></a>このサンプルの概要

`ValidateSavedQueryRequest` クラスは、保存済みクエリ (ビュー) を検証する必要があるデータが含まれているシナリオで使用するためのものです。 

`ExecuteByIdSavedQueryRequest` クラスは、指定された ID を持つ、保存済みクエリ (ビュー) を実行する必要があるデータが含まれているシナリオで使用するためのものです。

## <a name="how-this-sample-works"></a>このサンプルがどのように動作するか

[このサンプルの概要](#what-this-sample-does) で説明されているシナリオをシミュレートするために、サンプルは次のことを行います。

### <a name="setup"></a>セットアップ

1. 組織の現在のバージョンをチェックします。
1. `Account` メソッドは 3 つの取引先企業のレコードを作成します。
1. `SavedQuery` メソッドは、保存済みクエリを作成します。
1. `UserQuery` メソッドは、ユーザー クエリを作成します。


### <a name="demonstrate"></a>使用方法
1. `ValidateSavedQueryRequest` メソッドは有効な要求を作成されます。
1. `ExecuteByIdSavedQueryRequest` メソッドは、保存済みクエリを実行します。

### <a name="clean-up"></a>クリーン アップ

サンプルで作成されたすべてのデータを削除するためのオプションを表示します。 サンプルで作成されるデータを検証する場合、削除は任意です。 手動でデータを削除することで同じ結果を得られます。
