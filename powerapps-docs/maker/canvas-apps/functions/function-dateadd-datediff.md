---
title: DateAdd、DateDiff、および TimeZoneOffset 関数 | Microsoft Docs
description: Power Apps での DateAdd、DateDiff、および TimeZoneOffset 関数の構文と例を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/23/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e5c321617f08b6747824757344e3cc61b1abf27b
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/13/2020
ms.locfileid: "3308569"
---
# <a name="dateadd-datediff-and-timezoneoffset-functions-in-power-apps"></a>Power Apps での DateAdd、DateDiff、および TimeZoneOffset 関数
日付/時刻値の差を加算または検索し、ローカル時刻と UTC との間で変換します。

## <a name="description"></a>内容
**DateAdd** 関数は、日付/時刻値に単位数を加算します。 結果は、新しい日付/時刻値です。 負の値を指定して、日付/時刻値から単位数を減算することもできます。

**DateDiff** 関数は、2 つの日付/時刻値の差を返します。 結果は、単位数です。

どちらの関数も、単位は **ミリ秒**、**秒**、**分**、**時間**、**日**、**月**、**四半期**、または**年**にすることができます。  既定では、両方の関数も単位として**日**を使用します。

**TimeZoneOffset** 関数はユーザーのローカル時刻と UTC (協定世界時) の間の分数を返します。   

**TimeZoneOffset** と **DateAdd** を使用して、ユーザーのローカル時刻と UTC (協定世界時) の間で変換できます。  **TimeZoneOffset** を追加するとローカル時刻が UTC に変換され、それを減算 (負を加算) すると UTC からローカル時刻に変換されます。

詳細については、[日付、時刻、および DateTime データの種類](../functions/data-types.md#date-time-and-datetime) および [日付と時刻の操作](../show-text-dates-times.md) も参照してください。

## <a name="syntax"></a>構文
**DateAdd**( *DateTime*, *Addition* [, *Units* ] )

* *DateTime* - 必須。 操作する日付/時刻値。
* *Addition* - 必須。 *DateTime* に*単位*で追加する数値。
* *Units* - オプション。 追加する *Units*の種類: **ミリ秒**、**秒**、**分**、**時間**、**日**、**月**、**四半期**、または**年**。  指定しない場合は、**日**が使用されます。

**DateDiff**( *StartDateTime*, *EndDateTime* [, *Units* ] )

* *StartDateTime* - 必須。 開始の日付/時刻値。
* *EndDateTime* - 必須。 終了の日付/時刻値。
* *Units* - オプション。 追加する *Units*の種類: **ミリ秒**、**秒**、**分**、**時間**、**日**、**月**、**四半期**、または**年**。  指定しない場合は、**日**が使用されます。

**TimeZoneOffset**( [ *DateTime* ] )

* *DateTime* - オプション。  オフセットを返す日付/時刻値。  既定では、現在の日付/時刻が使用されます。

## <a name="examples"></a>例
これらすべての例では、現在の日付および時刻を **2013 年 7 月 15 日、午後 1:02** と想定しています。

### <a name="simple-dateadd"></a>簡易な DateAdd

| 計算式 | 内容 | 結果 |
| --- | --- | --- |
| **Text( DateAdd( Now(), 3 ),<br>"dd-mm-yyyy hh:mm" )** |現在の日付および時刻に 3 日 (既定の単位) を追加します。 |"18-07-2013 13:02" |
| **Text( DateAdd( Now(), 4, Hours ),<br>"dd-mm-yyyy hh:mm" )** |現在の日付および時刻に 4 時間を追加します。 |"15-07-2013 17:02" |
| **Text( DateAdd( Today(), 1, Months ),<br>"dd-mm-yyyy hh:mm" )** |**Today** は時間のコンポーネントを返さないため、現在の日付に 1 か月を、時間なしで追加します。 |"15-08-2013 00:00" |
| **Text( DateAdd( Now(), &#8209;30, Minutes ),<br>"dd-mm-yyyy hh:mm" )** |現在の日付と時刻から 30 分を減算します。 |"15-07-2013 12:32" |

### <a name="simple-datediff"></a>簡易な DateDiff

| 計算式 | 内容 | 結果 |
| --- | --- | --- |
| **DateDiff( Now(), DateValue("1/1/2014") )** |**日**の既定の単位で 2 つの単位の差を返します |170 |
| **DateDiff( Now(), DateValue("1/1/2014"), Months )** |**Months**で 2 つの値の差を返します |6 |
| **DateDiff( Now(), Today(), Minutes )** |現在の日付/時刻と現在の日付のみ (時間なし) の差を分で返します。  **Now** は **Today** よりも後であるため、結果は負になります。 |-782 |

### <a name="converting-to-utc"></a>UTC に変換する
UTC (協定世界時) に変換するには、指定された時刻の **TimeZoneOffset** を追加します。  

たとえば、現在の日付および時刻が太平洋夏時間 (PDT, UTC-7) の **2013 年 7 月 15 日、午後 1:02** であると仮定します。  UTC で現在の時刻を確認するには、以下を使用します。

* **DateAdd( Now(), TimeZoneOffset(), Minutes )**

**TimeZoneOffset** では現在の時刻が既定に設定されるため、引数を渡す必要はありません。

結果を確認するには、*dd-mm-yyyy hh:mm* 形式の **Text** 関数を使用して、**15-07-2013 20:02** を返します。

### <a name="converting-from-utc"></a>UTC から変換する
UTC から変換するには、指定された時刻の **TimeZoneOffset** を (負を加算することによって) 減算します。

たとえば、**2013 年 7 月 15 日、午後 8:02** という UTC の日付と時刻が、**StartTime** という名前の変数に格納されていると仮定します。 ユーザーのタイム ゾーンの時間を調整するには、以下を使用します。

* **DateAdd( StartTime, &minus;TimeZoneOffset( StartTime ), Minutes )**

オフセットを加算するのではなく減算するには **TimeZoneOffset** の前に負の符号を付けることに注意してください。

結果を確認するには、*dd-mm-yyyy hh:mm* の形式で **Text** 関数を使用すると、太平洋夏時間の場合は **15-07-2013 13:02** になります。

