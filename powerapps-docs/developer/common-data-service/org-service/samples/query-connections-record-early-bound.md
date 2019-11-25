---
title: 'サンプル: レコードによる接続のクエリ (Common Data Service) | Microsoft Docs'
description: このサンプルは、特定のレコードの接続を照会する方法を示します。
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
ms.openlocfilehash: d0b91e7020db63d71a0cfa8e2bd5d009dbac2f85
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749308"
---
# <a name="sample-query-connections-by-a-record"></a>サンプル: レコードによるつながりの照会 

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-query-connections-record-early-bound -->

このサンプルは、特定のレコードの接続を照会する方法を示します。 1 件の取引先担当者と 2 件の取引先企業の間の接続を作成した後、その取引先担当者の接続を検索します。 サンプルは [ここ](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/QueryByRecord) からダウンロードできます。

## <a name="how-to-run-this-sample"></a>このサンプルを実行する方法

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>このサンプルの概要

このサンプルでは、取引先企業と取引先担当者を作成し、それらの間につながりロールを作成します。 `QueryExpression` は、特定のレコードのつながりを取得します。

## <a name="how-this-sample-works"></a>このサンプルがどのように動作するか

[このサンプルの概要](#what-this-sample-does) で説明されているシナリオをシミュレートするために、サンプルは次のことを行います。

### <a name="setup"></a>セットアップ

1. 組織の現在のバージョンをチェックします。
2. いくつかの匿名型を定義し、可能なつながりプロパティ値の範囲を定義します。
3. `ConnectionRole` はつながりロールを作成します。
4. `ConnectionRoleObjectType` は、取引先企業エンティティに対するつながりロールのオブジェクトの種類のレコードを作成します。 
5. つながりで使用する取引先企業および取引先担当者レコードを数個作成します。

### <a name="demonstrate"></a>使用方法

1. `QueryExpression` は、サンプルで作成された取引先責任者に関連付けられているすべてのつながりを取得します。

### <a name="clean-up"></a>クリーン アップ

1. [セットアップ](#setup) でレコードを削除するためのオプションを表示します。
    サンプルで作成されるエンティティおよびデータを検証する場合、削除は任意です。 手動でレコードを削除することで同じ結果を得られます。
