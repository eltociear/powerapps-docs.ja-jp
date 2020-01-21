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
ms.openlocfilehash: 0a6b20686f4e02afff576eb54133d061e4b82f18
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934211"
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

`QueryByAttribute` メソッドは、QueryByAttribute を使用してクエリを作成します。

### <a name="clean-up"></a>クリーン アップ

サンプルで作成されたすべてのデータを削除するためのオプションを表示します。 サンプルで作成されるデータを検証する場合、削除は任意です。 手動でデータを削除することで同じ結果を得られます。
