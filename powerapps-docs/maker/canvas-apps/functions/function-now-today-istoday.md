---
title: Now、Today、および IsToday 関数 | Microsoft Docs
description: Power Apps での Now、Today、および IsToday 関数の構文と例を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/09/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 43f6dfcff0c4174301eda5cb8dde2067081d91e2
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3304843"
---
# <a name="now-today-and-istoday-functions-in-power-apps"></a>Power Apps の Now、Today、および IsToday 関数
現在の日付と時刻を返し、日付/時刻値が今日かどうかをテストします。

## <a name="description"></a>内容
**Now** 関数は、現在の日付と時刻を日付/時刻値として返します。

**Today** 関数は、現在の日付を日付/時刻値として返します。 時刻部分は、午前 0 時です。 **Today** は、今日の午前 0 時から翌日の午前 0 時までの 1 日を通して同じ値を保持します。

**IsToday** 関数は、日付/時刻値が今日の午前 0 時から翌日の午前 0 時の間の値になっているかどうかをテストします。 この関数は、ブール値 (**true** または **false**) を返します。

これらの関数はすべて、現在のユーザーのローカル時刻を使用します。

詳細については、[日付と時間の操作](../show-text-dates-times.md) を参照してください。

## <a name="volatile-functions"></a>Volatile 関数
**Now** と **Today** は揮発性の関数です。  これらの関数はいずれも、評価されるたびに異なる値を返します。  

データ フロー数式で使用すると、揮発性の関数は、それが表示される数式が再評価される場合に別の値を返すだけです。  数式で何も変更されていない場合、アプリの実行全体を通じて同じ値を返します。

たとえば、**Label1.Text = Now()** であるラベル コントロールは、アプリがアクティブな間は変化しません。  アプリを閉じてからもう一度開いた場合にのみ、新しい値が返ります。

関数は、他の何かが変更された数式の一部である場合に再評価されます。  たとえば、**Label1.Text = DateAdd( Now(), Slider1.Value, Minutes )** であるスライダー コントロールを含むように例を変更した場合、Slider コントロールの値が変化するたびにラベルのテキスト プロパティが再評価されて、現在の時刻が取得されます。

[動作の数式](../working-with-formulas-in-depth.md)を使用すると、動作の数式が評価されるたびに、揮発性関数が評価されます。  例については、以下を参照してください。

## <a name="syntax"></a>構文
**Now**()

**Today**()

**IsToday**( *DateTime* )

* *DateTime* - 必須。  テストする日付/時刻値。

## <a name="examples"></a>例
このセクションの例では、現在の時刻が **2015 年 2 月 12 日**の**午前 3 時 59 分**であり、言語が **en-us** です。

| 計算式 | 内容 | 結果 |
| --- | --- | --- |
| **Text( Now(), "mm/dd/yyyy hh:mm:ss" )** |現在の日付と時刻を取得し、文字列として表示します。 |"02/12/2015 03:59:00" |
| **Text( Today(), "mm/dd/yyyy hh:mm:ss" )** |現在の日付のみを取得し、時刻は午前 0 時としたまま、これを文字列として表示します。 |"02/12/2015 00:00:00" |
| **IsToday( Now() )** |現在の日付と時刻が、今日の午前 0 時から翌日の午前 0 時の間であるかどうかをテストします。 |**True** |
| **IsToday( Today() )** |現在の日付が、今日の午前 0 時から翌日の午前 0 時の間であるかどうかをテストします。 |**True** |
| **Text( DateAdd( Now(), 12 ), "mm/dd/yyyy hh:mm:ss" )** |現在の日付と時刻を取得し、その結果に 12 日を追加し、文字列として表示します。 |"02/24/2015 03:59:00" |
| **Text( DateAdd( Today(), 12 ), "mm/dd/yyyy hh:mm:ss" )** |現在の日付を取得し、その結果に 12 日を追加して、文字列として表示します。 |"02/24/2015 00:00:00" |
| **IsToday( DateAdd( Now(), 12 ) )** |現在の日付と時刻に 12 日を加算した日時が今日の午前 0 時から翌日の午前 0 時の間であるかどうかをテストします。 |**false** |
| **IsToday( DateAdd( Today(), 12 ) )** |現在の日付に 12 日を加算した日付が今日の午前 0 時から翌日の午前 0 時の間であるかどうかをテストします。 |**false** |

#### <a name="display-a-clock-that-updates-in-real-time"></a>リアルタイムで更新される時計を表示する

1. **[Timer](../controls/control-timer.md)** コントロールを追加し、その **Duration** プロパティを **1000** に設定し、**Repeat** プロパティを **true** に設定します。

    タイマーは 1 秒間実行し、自動的に最初からやり直し、そのパターンを続けます。 

1. コントロールの **OnTimerEnd** プロパティを次の式に設定します:

    **Set( CurrentTime, Now() )**

    タイマーが (1 秒ごとに) 最初からやり直すたびに、この式は **CurrentTime** グローバル変数に **Now** 関数の現在の値を設定します。

    ![数式 OnTimerEnd = Set(CurrentTime, Now()) でのタイマー コントロールを含む画面](media/function-now-today-istoday/now-set-currenttime.png)

1. **[Label](../controls/control-text-box.md)** コントロールを追加し、その **Text** プロパティを次の数式に設定します。

    **Text( CurrentTime, LongTime24 )**

    **[Text](function-text.md)** 関数を使用して日付と時刻の形式を設定するか、またはこのプロパティに **CurrentTime** のみを設定して秒を除いた時間と分を表示します。

    ![Text プロパティが Text( CurrentTime, LongTime24) に設定されたラベル コントロールを含む画面](media/function-now-today-istoday/now-use-currenttime.png)

1. F5 キーを押してアプリをプレビューした後、クリックまたはタップしてタイマーを開始します。

    ラベルは、秒の単位まで現在時刻を示し続けます。

    ![4 つの時刻値 (13:50:22、13:50:45、13:51:03 および 13:51:25) を表示する 4 つの画面](media/function-now-today-istoday/now-four-times.png)

1. タイマーの **AutoStart** プロパティを **true** に設定し、**Visible** プロパティを **false** に設定します。

    タイマーは非表示であり、自動的に開始されます。

1. 次の例のように、画面の **[OnStart](../controls/control-screen.md)** プロパティを、有効な値を保持する **CurrentTime** 変数に設定します。

    **Set(CurrentTime, Now())**

    アプリが起動するとすぐに (タイマーがまるまる 1 秒動く前に)、ラベルが表示されます。
