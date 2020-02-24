---
title: 'サンプル: 接続ロールの作成 (Common Data Service) | Microsoft Docs'
description: このサンプルでは、つながりロールの作成方法を説明します。
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
ms.openlocfilehash: ab669bca920aee564a2ad0b8fe3fee06ad06165e
ms.sourcegitcommit: 3bf59896a98e5f01289a2489e185f27518aeaec3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/15/2020
ms.locfileid: "2956218"
---
# <a name="sample-create-a-connection-role"></a>サンプル: つながりロールの作成

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-create-connection-role-early-bound -->

このサンプルは、取引先企業および取引先担当者に対して使用できるつながりロールの作成方法を示します。 サンプルは [ここ](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ConnectionRole) からダウンロードできます。

## <a name="how-to-run-this-sample"></a>このサンプルを実行する方法

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>このサンプルの概要

このサンプルは、取引先企業および取引先担当者に対して使用できるつながりロールの作成方法を示します。

## <a name="how-this-sample-works"></a>このサンプルがどのように動作するか

[このサンプルの概要](#what-this-sample-does) で説明されているシナリオをシミュレートするために、サンプルは次のことを行います。

### <a name="setup"></a>セットアップ

組織の現在のバージョンをチェックします。

### <a name="demonstrate"></a>使用方法

1. いくつかの匿名型を定義し、可能なつながりプロパティ値の範囲を定義します。
2. 取引先企業および取引先担当者のつながりロールを作成します。
3. 取引先企業および取引先担当者エンティティに対するつながりロールのオブジェクトの種類のレコードを作成します。

### <a name="clean-up"></a>クリーン アップ

[セットアップ](#setup) でレコードを削除するためのオプションを表示します。 サンプルで作成されるエンティティおよびデータを検証する場合、削除は任意です。 手動でレコードを削除することで同じ結果を得られます。
