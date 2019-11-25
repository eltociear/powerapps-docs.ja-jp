---
title: 'サンプル: QueryByAttribute クラスを使用した複数取得(Common Data Service) | Microsoft Docs'
description: このサンプルは、QueryByAttribute クラスの使用方法を示しています
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
ms.openlocfilehash: 4b545431853a3f6ca66ce5906f6d6ff69edde1db
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749294"
---
# <a name="sample-retrieve-multiple-with-the-querybyattribute-class"></a>サンプル: QueryByAttribute クラスを使用した複数取得

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/org-service/sample-retrieve-multiple-querybyattribute-class -->

このサンプルでは、[RetrieveMultiple](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.retrievemultiple?view=dynamics-general-ce-9) メソッドで [QueryByAttribute](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.query.querybyattribute?view=dynamics-general-ce-9) を取得する方法を示します。 サンプルは [ここ](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RetrieveMultipleQueryByAttribute) からダウンロードできます。

## <a name="how-to-run-this-sample"></a>このサンプルを実行する方法

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]


## <a name="what-this-sample-does"></a>このサンプルの概要

`QueryByAttribute` クラスは、一連の属性と値ペアとして記述されたクエリを含むシナリオで使用するためのものです。

## <a name="how-this-sample-works"></a>このサンプルがどのように動作するか

[このサンプルの概要](#what-this-sample-does) で説明されているシナリオをシミュレートするために、サンプルは次のことを行います。

### <a name="setup"></a>セットアップ

1. 組織の現在のバージョンをチェックします。
1. `Account` メソッドは 2 つの取引先企業のレコードを作成します。

### <a name="demonstrate"></a>使用方法

1. `QueryByAttribute` メソッドは、QueryByAttribute を使用してクエリを作成します。

### <a name="clean-up"></a>クリーン アップ

1. サンプルで作成されたすべてのデータを削除するためのオプションを表示します。

サンプルで作成されるデータを検証する場合、削除は任意です。 手動でデータを削除することで同じ結果を得られます。
