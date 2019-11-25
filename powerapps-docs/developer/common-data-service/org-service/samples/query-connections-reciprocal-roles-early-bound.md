---
title: 'サンプル: 相互ロールによる接続のクエリ (Common Data Service) | Microsoft Docs'
description: このサンプルは、相互関係ロールによりつながりを照会する方法を示します。
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
ms.openlocfilehash: 35237064a89309f2345e92122479ad059369a495
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749309"
---
# <a name="sample-query-connections-by-reciprocal-roles"></a>サンプル: 相互ロールによるつながりの照会

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-query-connections-reciprocal-roles-early-bound -->

このサンプルは、一致ロールを作成し、特定のロールの一致ロールを検索する方法を示します。 サンプルは [ここ](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/QueryByReciprocalRole) からダウンロードできます。

## <a name="how-to-run-this-sample"></a>このサンプルを実行する方法

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>このサンプルの概要

このサンプルは、一致ロールを作成し、特定のロールの一致ロールを検索する方法を示します。

## <a name="how-this-sample-works"></a>このサンプルがどのように動作するか

[このサンプルの概要](#what-this-sample-does) で説明されているシナリオをシミュレートするために、サンプルは次のことを行います。

### <a name="setup"></a>セットアップ
1. 組織の現在のバージョンをチェックします。
2. いくつかの匿名型を定義し、可能なつながりプロパティ値の範囲を定義します。
3. `ConnectionRole` は、主要なロール インスタンスを作成します。
4. `ConnectionRoleObjectTypeCode` は、取引先企業および取引先担当者エンティティに対するつながりロールのオブジェクトの種類のレコードを作成します。
5. `AssociateRequest` により、つながりロールが関連付けられます。

### <a name="demonstrate"></a>使用方法

1. `QueryExpression` は、このロールを相互ロールとして登録しているすべてのつながりロールを取得します。

### <a name="clean-up"></a>クリーン アップ

1. [セットアップ](#setup) でレコードを削除するためのオプションを表示します。
    サンプルで作成されるエンティティおよびデータを検証する場合、削除は任意です。 手動でレコードを削除することで同じ結果を得られます。
