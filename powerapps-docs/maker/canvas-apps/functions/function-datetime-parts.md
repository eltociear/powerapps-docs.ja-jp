---
title: Day、Month、Year、Hour、Minute、Second、および Weekday 関数 | Microsoft Docs
description: Power Apps での Day、Month、Year、Hour、Minute、Second、および Weekday 関数の構文と例を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/25/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 571ec9d9b18be623a60bedfc3ac04e8ed8e46b33
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3305372"
---
# <a name="day-month-year-hour-minute-second-and-weekday-functions-in-power-apps"></a>Power Apps での Day、Month、Year、Hour、Minute、Second、および Weekday 関数
日付/時刻値の個々のコンポーネントを返します。

## <a name="description"></a>内容
**Day** 関数は、日付/時刻値の日のコンポーネントを 1 から 31 の範囲で返します。

**Month** 関数は、日付/時刻値の月のコンポーネントを 1 から 12 の範囲で返します。

**Year** 関数は、1900 で始まる日付/時刻値の年のコンポーネントを返します。

**Hour** 関数は、日付/時刻値の時間のコンポーネントを 0 (12:00 AM) から 23 (11:00 PM) の範囲で返します。

**Minute** 関数は、日付/時刻値の分のコンポーネントを 0 から 59 の範囲で返します。

**Second** 関数は、日付/時刻値の秒のコンポーネントを 0 から 59 の範囲で返します。

**Weekday** 関数は、日付/時刻値の曜日を返します。  既定では、結果は 1 (日曜日) から 7 (土曜日) の範囲です。  Microsoft Excel Weekday 関数コード、または StartOfWeek リスト値を使用して別の範囲を指定できます。

| Excel コード | StartOfWeek リスト | 内容 |
| --- | --- | --- |
| **1**、**17** |**StartOfWeek.Sunday** |1 (日曜日) から 7 (土曜日) までの数値。  既定。 |
| **2**, **11** |**StartOfWeek.Monday** |1 (月曜日) から 7 (日曜日) までの数値。 |
| **3** |**StartOfWeek.MondayZero** |0 (月曜日) から 6 (日曜日) までの数値。 |
| **12** |**StartOfWeek.Tuesday** |1 (火曜日) から 7 (月曜日) までの数値。 |
| **13** |**StartOfWeek.Wednesday** |1 (水曜日) から 7 (火曜日) までの数値。 |
| **14** |**StartOfWeek.Thursday** |1 (木曜日) から 7 (水曜日) までの数値。 |
| **15** |**StartOfWeek.Friday** |1 (金曜日) から 7 (木曜日) までの数値。 |
| **16** |**StartOfWeek.Saturday** |1 (土曜日) から 7 (金曜日) までの数値。 |

すべての関数は数値を返します。

詳細については、[日付と時間の操作](../show-text-dates-times.md) を参照してください。

## <a name="syntax"></a>構文
**Day**( *DateTime* )<br>**Month**( *DateTime* )<br>**Year**( *DateTime* )<br>**Hour**( *DateTime* )<br>**Minute**( *DateTime* )<br>**Second**( *DateTime* )

* *DateTime* - 必須。  操作する日付/時刻値。  

**Weekday**( *DateTime* [, *WeekdayFirst* ] )<br>

* *DateTime* - 必須。  操作する日付/時刻値。 
* *WeekdayFirst* - オプション。  週の開始日を指定する Excel コード。  指定しない場合は、1 (日曜日が最初) が使用されます。

## <a name="examples"></a>例
次の例で、現在の時刻は **2015 年 4 月 9 日木曜日**の**午後 3 時 59 分 37 秒**です。

| 計算式 | 内容 | 結果 |
| --- | --- | --- |
| **Year(&nbsp;Now()&nbsp;)** |現在の時刻と日付の年のコンポーネントを返します。 |2015 |
| **Month(&nbsp;Now()&nbsp;)** |現在の時刻と日付の月のコンポーネントを返します。 |4 |
| **Day(&nbsp;Now()&nbsp;)** |現在の時刻と日付の日のコンポーネントを返します。 |9 |
| **Hour(&nbsp;Now()&nbsp;)** |現在の時刻および日付の時間のコンポーネントを返します。 |15 |
| **Minute(&nbsp;Now()&nbsp;)** |現在の時刻および日付の分のコンポーネントを返します。 |59 |
| **Second(&nbsp;Now()&nbsp;)** |現在の時刻および日付の分のコンポーネントを返します。 |37 |
| **Weekday(&nbsp;Now()&nbsp;)** |週の既定の開始を日曜日として使用して、現在の時刻と日付の曜日のコンポーネントを返します。 |5 |
| **Weekday(&nbsp;Now(),&nbsp;14&nbsp;)** |週の開始として木曜日を指定する Excel コードを使用して、現在の時刻と日付の曜日のコンポーネントを返します。 |1 |
| **Weekday(&nbsp;Now(),&nbsp;StartOfWeek.Wednesday&nbsp;)** |週の開始として水曜日を指定する **StartOfWeek** リストを使用して、現在の時刻と日付の曜日のコンポーネントを返します。 |2 |

