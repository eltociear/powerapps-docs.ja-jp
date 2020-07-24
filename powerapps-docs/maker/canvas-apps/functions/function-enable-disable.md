---
title: Enable および Disable 関数 | Microsoft Docs
description: Power Apps での Enable および Disable 関数の構文と例を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: af1522934bcfee13c00950a3686583393699d0ad
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3305303"
---
# <a name="enable-and-disable-functions-in-power-apps"></a>Power Apps での Enable および Disable 関数
[信号](signals.md) をオンまたはオフにします。

## <a name="overview"></a>概要
一部の信号は頻繁に変更する場合があり、アプリはその度に再計算する必要があります。  長い期間にわたって急速に変化すると、デバイスのバッテリが消耗することがあります。 これらの関数を使用して、手動で信号をオンまたはオフにすることができます。

信号が使用されてない場合は、自動的にオフになります。

## <a name="description"></a>内容
**Enable** および **Disable** 関数は、それぞれ、信号をオンおよびオフにします。

これらの関数は、現在**[場所](signals.md)** 信号でのみ有効です。

これらの関数には、戻り値がありません。 これらは、[動作の数式](../working-with-formulas-in-depth.md) 内でのみ使用できます。

## <a name="syntax"></a>構文
**Enable**( *Signal* )<br>**Disable**( *Signal* )

* *信号* - 必須。  オンまたはオフするための信号。

