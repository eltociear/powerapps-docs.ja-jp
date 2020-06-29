---
title: Date および Time 関数 | Microsoft Docs
description: Power Apps での Date および Time 関数の構文と例を含む参照情報
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
ms.openlocfilehash: 01fdccf295dbf21e61790d537f74af562dce69f0
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3305395"
---
# <a name="date-and-time-functions-in-power-apps"></a>Power Apps での Date および Time 関数
日付と時間のコンポーネントを日付/時刻値に変換します。

## <a name="description"></a>内容
**Date** 関数は、個々の年、月、および日の値を日付/時刻値に変換します。  時刻部分は、午前 0 時です。

* 年が 0 と 1899 (を含む) の間の場合は、関数はその値を 1900 に加算して年を計算します。  **70** は **1970** になります。
* 月が 1 未満または 12 を超える場合、結果は指定された年の始めからその月数を減算または加算します。
* 指定された月の日数より日が大きい場合、関数はその日数を月の最初の日に加算し、その後の月から対応する日付を返します。  日が 1 未満の場合、関数は指定された月の最初の日から、その日数に 1 を加えた日数を減算します。

**Time** 関数は、個々の時間、分、および秒の値を日付/時刻値に変換します。  結果には、関連付けられている日付がありません。

文字列を値に変換する方法に関する詳細については、**[DateValue](function-datevalue-timevalue.md)**、**[TimeValue](function-datevalue-timevalue.md)**、および **[DateTimeValue](function-datevalue-timevalue.md)** 関数を参照してください。  

詳細については、[日付および時間の操作](../show-text-dates-times.md) も参照してください。

## <a name="syntax"></a>構文
**Date**( *Year*, *Month*, *Day* )

* *Year* - 必須。  1899 より大きい数値は、絶対値として解釈されます (1980 は 1980 として解釈されます)。0 から 1899 の範囲の数値は、1900 に対する相対値として解釈されます。 (たとえば、80 は 1980 として解釈されます。)
* *Month* - 必須。  1 から 12 の範囲の数値。
* *Day* - 必須。 1 から 31 の範囲の数値。

**Time**( *Hour*, *Minute*, *Second* )

* *Hour* - 必須。  0 (12:00 AM) から 23 (11:00 PM) の範囲の数値。
* *Minute* - 必須。 0 から 59 の範囲の数値。
* *Second* - 必須。 0 から 59 の範囲の数値。

## <a name="examples"></a>例
### <a name="date"></a>Date
ユーザーが **HireYear** という名前のテキスト入力コントロールに **1979**、**HireMonth** という名前のテキスト入力コントロールに **3**、**HireDay** という名前のテキスト入力コントロールに **17** を入力した場合、この関数は **3/17/1979** を返します。

**Date(Value(HireYear.Text), Value(HireMonth.Text), Value(HireDay.Text))**

### <a name="time"></a>Time
ユーザーが **BirthHour** という名前のテキスト入力コントロールに **14**、**BirthMinute** という名前のテキスト入力コントロールに **50**、**BirthSecond** という名前のテキスト入力コントロールに **24** を入力した場合、この関数は **02:50:24 p** を返します。

**Text(Time(Value(BirthHour.Text), Value(BirthMinute.Text), Value(BirthSecond.Text)), "hh:mm:ss a/p")**

