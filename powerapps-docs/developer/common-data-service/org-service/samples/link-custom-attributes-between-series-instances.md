---
title: 'サンプル: 系列とインスタンスとの間のカスタム属性のリンク (Common Data Service) | Microsoft Docs'
description: 系列とインスタンス間のユーザー定義属性のリンク方法をこのサンプルで示します。
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
ms.openlocfilehash: 142600c4e8cc9cc5d959b42670678234245e6f1d
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934283"
---
# <a name="sample-link-custom-attributes-between-series-and-instances"></a>サンプル: 系列とインスタンスとの間のユーザー定義属性のリンク

このサンプルでは、一連の定期的な予定 (`RecurringAppointmentMaster`) 用に作成されたユーザー定義属性を、予定インスタンス (`Appointment`) 用に作成されたユーザー定義属性とリンクさせる方法。 サンプルは [ここ](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/LinkAttributes) からダウンロードできます。

## <a name="what-this-sample-does"></a>このサンプルの概要

`CreateAttributeRequest` メッセージは、ユーザー定義属性を作成するために必要なデータが含まれているシナリオで使用するためのものです。

## <a name="how-this-sample-works"></a>このサンプルがどのように動作するか

[このサンプルの概要](#what-this-sample-does) で説明されているシナリオをシミュレートするために、サンプルは次のことを行います。

### <a name="setup"></a>セットアップ

組織の現在のバージョンをチェックします。

### <a name="demonstrate"></a>使用方法

1. `StringAttributeMetadata` メッセージは、定期的な予定インスタンスのカスタムの文字列属性と予定インスタンスを作成します。
2. `LinkedAttributeId` から、ユーザー定義属性を予定のユーザー属性にリンクします。

### <a name="clean-up"></a>クリーンアップ

[セットアップ](#setup) で作成されたレコードを削除するオプションを表示します。 サンプルで作成されるエンティティおよびデータを検証する場合、削除は任意です。 手動でレコードを削除することで同じ結果を得られます。
