---
title: DateValue、TimeValue、および DateTimeValue 関数 | Microsoft Docs
description: Power Apps での DateValue、TimeValue、および DateTimeValue 関数の参照情報、構文および例
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/08/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 2fc1a91b4468926ee98351f79d7ce2e84133aa46
ms.sourcegitcommit: 7d3caf698d367a56af9e16c43af8005adb9f87cd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2020
ms.locfileid: "3309144"
---
# <a name="datevalue-timevalue-and-datetimevalue-functions-in-power-apps"></a>Power Apps での DateValue、TimeValue、および DateTimeValue 関数

*文字列*の日付、時刻またはその両方を*日付/時刻*値に変換します。

## <a name="description"></a>内容

- **DateValue** 関数は、*日付文字列* (たとえば、"10/01/2014") を*日付/時刻*値に変換します。

- **TimeValue** 関数は、*時刻文字列* (たとえば、"12:15 PM") を*日付/時刻*値に変換します。

- **DateTimeValue** 関数は、*日付および時刻文字列* (たとえば、"January 10, 2013 12:13 AM") を*日付/時刻*値に変換します。

**DateValue** 関数は日付文字列の任意の時刻情報を無視し、および **TimeValue** 関数は時刻文字列の任意の日付情報を無視します。

> [!NOTE]
> DateValue、TimeValue、および DateTimeValue 関数は、既定で現在のユーザーの設定の言語を使用します。 これを上書きして、文字列が適切に解釈されるようにすることができます。 たとえば、"10/1/1920" が "*en*" では *October 1<sup>st</sup>* として、"*fr*" では *January 10<sup>th</sup>* として解釈されます。

日付は、以下の形式のいずれかである必要があります。

- MM/DD/YYYY または MM-DD-YYYY
- DD/MM/YYYY または DD-MM-YYYY
- YYYY/MM/DD または YYYY-MM-DD
- MM/DD/YY または MM-DD-YY
- DD/MM/YY または DD-MM-YY
- DD Mon YYYY
- Month DD, YYYY

数値の日付、月および年コンポーネントから変換するには、[日付](function-date-time.md) を参照してください。 <br>
数値の時間、分および秒コンポーネントから変換するには、[時刻](function-date-time.md) を参照してください。

詳細については、以下を参照してください。

- [日付と時刻の操作](../show-text-dates-times.md).
- [日付/時刻 およびデータの種類](data-types.md#date-time-and-datetime).

## <a name="syntax"></a>構文

**DateValue**( *String* [, *Language* ])<br>
**DateTimeValue**( *String* [, *Language* ])<br>
**TimeValue**( *String* [, *Language* ])

* *String* - 必須。 日付、時刻、または日付と時刻の組み合わせの値を含むテキスト文字列。
* *Language* - オプション。 [Language](function-language.md) 関数の最初の 2 文字で返されるなどの言語文字列。  指定しない場合は、現在のユーザーの設定の言語が使用されます。  

## <a name="examples"></a>例

### <a name="datevalue"></a>DateValue

**Startdate** という名前のテキスト入力コントロールに **10/11/2014** を入力し、次にラベルの [Text](../controls/properties-core.md) プロパティを次の関数に設定する場合:

- ユーザーのロケールの文字列から日付を変換し、長い日付として結果を表示します。

    ```powerapps-dot
    Text( DateValue( Startdate.Text ), DateTimeFormat.LongDate )
    ```

    **en** ロケールとして設定されたデバイスは、ラベルを **Saturday, October 11, 2014** として表示します。
  
    > [!NOTE]
    > **DateTimeFormat** 列挙で複数のオプションを使用できます。 オプションの一覧を表示するには、数式バーでパラメーターの後に続いてドット または ピリオド (**.**) を入力する、または [**Text** 関数の参照](function-text.md) を確認します。

- フランス語ロケールの文字列から日付を変換し、長い日付として結果を表示します。 この例では、月と月の日付は英語とは異なって解釈されます。

    ```powerapps-dot
    Text( DateValue( Startdate.Text, "fr" ), DateTimeFormat.LongDate )
    ```
  
    **en** ロケールに設定されたデバイスは、ラベルを **Monday, November 10, 2014** として表示します。

代わりに **October 20, 2014** を入力した場合:

- ユーザーのロケールの文字列から日付を変換し、2日間の差を日数で計算します

    ```powerapps-dot
    DateDiff( DateValue( Startdate.Text ), Today() )
    ```
  
    **en** ロケールに設定されたデバイスは、ラベルを **9** として表示し、10 月 11 日から 10 月 20 日までの日数を示します。 [DateDiff](function-dateadd-datediff.md) 関数は、差を月、四半期、または年で示すこともできます。

### <a name="datetimevalue"></a>DateTimeValue

**Start** という名前のテキスト入力コントロールに **10/11/2014 1:50:24.765 PM** を入力し、次にラベルの [Text](../controls/properties-core.md) プロパティを次の数式に設定した場合:

- 現在のロケールで日付と時刻両方の文字列を変換します。
 
    ```powerapps-dot
    Text( DateTimeValue( Start.Text ), DateTimeFormat.LongDateTime )
    ```    
    
    **en** ロケールに設定されたデバイスは、ラベルを **October 11, 2014 1:50:24 PM** として表示します。
  
  > [!NOTE]
  > **DateTimeFormat** 列挙で複数のオプションを使用できます。 オプションの一覧を表示するには、数式バーでパラメーターの後に続いてドット または ピリオド (**.**) を入力する、または [**Text** 関数の参照](function-text.md) を確認します。

- フランス語ロケールで日付と時間の両方の文字列を変換します。 月と月の日付は異なって解釈されます。

    ```powerapps-dot
    Text( DateTimeValue( Start.Text, "fr"), DateTimeFormat.LongDateTime )
    ```
  
    **en** ロケールに設定されたデバイスは、ラベルを **Monday, November 10, 2014 1:50:24 PM** として表示します。

- ユーザーのロケールで日付と時間の両方の文字列を変換し、小数の秒で結果を表示します。

    ```powerapps-dot
    Text( DateTimeValue( Start.Text ), "dddd, mmmm dd, yyyy hh:mm:ss.fff AM/PM" )
    ```
  
    **en** ロケールに設定されたデバイスは、ラベルを **October 11, 2014 01:50:24.765 PM** として表示します。
  
    代替策として、**hh:mm:ss.f** または **hh:mm:ss.ff** を指定して、時間を最も近い 10<sup>分</sup> または 100<sup>分</sup> の 1 秒に丸めることができます。

### <a name="timevalue"></a>TimeValue

テキスト入力コントロールに **FinishedAt** という名前を付け、ラベルの [Text](../controls/properties-core.md) プロパティを次の数式に設定します。

```powerapps-dot
If( TimeValue( FinishedAt.Text ) < TimeValue( "5:00:00.000 PM" ), 
    "You made it!", 
    "Too late!"
)
```

- **FinishedAt** コントロールに **4:59:59.999 PM** と入力する場合、ラベルは "*間に合った!*" と表示します
- **FinishedAt** コントロールに **5:00:00.000 PM** と入力する場合、ラベルは "*遅すぎる!*" と表示します
