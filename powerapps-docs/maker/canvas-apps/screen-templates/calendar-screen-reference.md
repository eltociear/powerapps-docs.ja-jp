---
title: キャンバス アプリのカレンダー スクリーン テンプレートの参照 | Microsoftドキュメント
description: Power Apps でキャンバス アプリのカレンダー スクリーン テンプレートの仕組みの詳細を理解する。
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/28/2020
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e85994e65c9712992ca9813e9cb5d8706aa8d080
ms.sourcegitcommit: c0b694f53af1cd35dce135be9e4e0924ac35608d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2020
ms.locfileid: "3352176"
---
# <a name="reference-information-about-the-calendar-screen-template-for-canvas-apps"></a>キャンバス アプリのカレンダー スクリーン テンプレートに関する参照情報

Power Apps でのキャンバス アプリの場合、カレンダー スクリーン テンプレートの重要な各コントロールがスクリーン全体の既定機能にどのように貢献するかを理解します。 この詳細は、動作の数式およびコントロールがユーザー入力にどのように応答するかを決定する他のプロパティの値を表示します。 このスクリーン既定機能の概要については、 [カレンダー スクリーンの概要](calendar-screen-overview.md) を参照してください。

このトピックは、一部の重要なコントロールに注目し、それらのコントロールのさまざまなプロパティ (**Items** および **OnSelect** など) に設定する式または数式ついて説明しています。

- [カレンダー ドロップダウン (dropdownCalendarSelection)](#calendar-drop-down)
- [カレンダー アイコン (iconCalendar)](#calendar-icon)
- [前月のシェブロン (iconPrevMonth)](#previous-month-chevron)
- [翌月のシェブロン (iconNextMonth)](#next-month-chevron)
- [カレンダー ギャラリー (MonthDayGallery) (+ child controls)](#calendar-gallery)
- [イベント ギャラリー (CalendarEventsGallery)](#events-gallery)

## <a name="prerequisite"></a>前提条件

[Power Apps でアプリを作成する](../data-platform-create-app-scratch.md) ときに、画面およびその他のコントロールの追加および構成を行う方法に関する知識。

## <a name="calendar-drop-down"></a>カレンダー ドロップダウン

![dropdownCalendarSelection コントロール](media/calendar-screen/calendar-dropdown.png)

- プロパティ: **アイテム**<br>
    値: `Office365.CalendarGetTables().value`

    この値は、アプリ ユーザーの Outlook カレンダーを取得するコネクタ操作です。 この操作が取得する[値](https://docs.microsoft.com/connectors/office365/#entitylistresponse[table]) が表示されます。

- プロパティ: **OnChange**<br>値: `Select(dropdownCalendarSelection)`

    ユーザーがリストのオプションを選択すると、コントロールの **OnSelect** プロパティの関数が実行されます。

- プロパティ: **OnSelect**<br>
    値: 次のコード ブロックに表示される **If** 関数、およびその後のコード ブロックに表示されるいくつかの追加関数です。

   数式のこの部分は、ユーザーがアプリを開いた後にドロップダウン リストでオプションを初めて選択したときにのみ実行されます:

    ```powerapps-dot
    If( IsBlank( _userDomain ),
        UpdateContext( {_showLoading: true} );
        Set( _userDomain, Right( User().Email, Len( User().Email ) - Find( "@", User().Email ) ) );
        Set( _dateSelected, Today() );
        Set( _firstDayOfMonth, DateAdd( Today(), 1 - Day( Today() ), Days ) );  
        Set( _firstDayInView, DateAdd( _firstDayOfMonth, -(Weekday(_firstDayOfMonth) - 1), Days ) );
        Set( _lastDayOfMonth, DateAdd( DateAdd( _firstDayOfMonth, 1, Months ), -1, Days ) )  
    );
    ```

    上記のコードは、次の変数を定義しています:
    
  - **\_userDomain**: ユーザーのメール アドレスに反映されている、アプリ ユーザーの企業ドメイン。
  - **\_dateSelected**: 今日の日付 (既定)。 カレンダー ギャラリーはこの日付を強調表示し、イベント ギャラリーはその日付にスケジュールされているイベントを表示します。
  - **\_firstDayOfMonth**: 当月の最初の日。 `(Today + (1 - Today)) = Today - Today + 1 = 1` なので、この **DateAdd** 関数は常に月の最初の日を返します。
  - **\_firstDayInView**: カレンダー ギャラリーで表示できる最初の日。 この値は、月が日曜日に開始しない限り、月の最初の日と同じではありません。 前月の週全体が表示されないようにするために、**\_firstDayInView** の値は `_firstDayOfMonth - Weekday(_firstDayOfMonth) + 1` です。
  - **\_lastDayOfMonth**: 当月の最終日は、翌月の最初の日から 1 日を引いた日と同じです。

   **If** 関数の後の関数は、ユーザーがカレンダーのドロップダウン リストでオプションを選択すると実行されます (ユーザーが初めてアプリを開いたときだけではありません) :

    ```powerapps-dot
    Set( _calendarVisible, false );
    UpdateContext( {_showLoading: true} );
    Set( _myCalendar, dropdownCalendarSelection2.Selected );
    Set( _minDate, 
        DateAdd( _firstDayOfMonth, -(Weekday( _firstDayOfMonth ) - 2 + 1), Days )
    );
    Set(_maxDate, 
        DateAdd(
            DateAdd( _firstDayOfMonth, -(Weekday( _firstDayOfMonth ) - 2 + 1), Days ), 
            40, 
            Days
        )
    );
    ClearCollect( MyCalendarEvents, 
        'Office365'.GetEventsCalendarViewV2( _myCalendar.Name, 
            Text( _minDate, UTC ), 
            Text( _maxDate, UTC )
        ).value
    );
    UpdateContext( {_showLoading: false} );
    Set( _calendarVisible, true )
    ```

    上記のコードは、これらの変数および 1 つのコレクションを定義しています:

    - **\_calendarVisible**: 新しい選択が読み込まれている間にカレンダーを表示しないため、**false** に設定します。
    - **\_showLoading**: 新しい選択が読み込まれている間にインジケーターを表示するため、**true** に設定します。
    - **\_myCalendar**: 正しいカレンダーからイベントを取得するため、**カレンダー ドロップダウン** コントロールの現在値に設定します。
    - **\_minDate**: **\_firstDayInView** と同じ値に設定します。 この変数は、Outlook から既に取得され、アプリにキャッシュされているイベントを決定します。
    - **\_maxDate**: カレンダーで表示可能な最後の日に設定します。 数式は、`_firstDayInView + 40` です。 カレンダーには最大 41 日が表示されるため、**\_maxDate** 変数は常に表示可能な最後の日を反映し、Outlook から既に取得され、アプリにキャッシュされているイベントを決定します。
    - **MyCalendarEvents**: 選択したカレンダーからのユーザーのイベントのコレクションに設定します。範囲は **\_minDate** から **\_maxDate** です。
    - **\_showLoading**: **false** に設定; 他のすべてが読み込まれた後、**\_calendarVisible** は **true** に設定されます。

### <a name="color-properties"></a>色のプロパティ

全般的な色のプロパティについては、[Power Apps で色と境界線のプロパティ](../controls/properties-color-border.md) を参照してください。

カレンダー ドロップダウン コントロールの一意の色プロパティ:

- **ChevronBackground** - カレンダー ドロップダウンの背景色。
- **ChevronBackground** - 無効にされたカレンダー ドロップダウンの背景色。
- **ChevronFill** - カレンダー ドロップダウンの塗りつぶしの色。
- **ChevronDisabledFill** - 無効にされたカレンダー ドロップダウンの塗りつぶしの色。
- **ChevronHoverBackground** - ユーザーがマウス ポインターを置いたときのカレンダー ドロップダウンの背景色。
- **ChevronHoverFill** - ユーザーがマウス ポインターを置いたときのカレンダー ドロップダウンの塗りつぶしの色。

## <a name="calendar-icon"></a>カレンダー アイコン

![アイコン カレンダー コントロール](media/calendar-screen/calendar-today-icon.png)

- プロパティ: **OnSelect**<br>
    値: カレンダー ギャラリーを今日の日付にリセットする 4 つの **Set** 関数:

    ```powerapps-dot
    Set( _dateSelected, Today() );
    Set( _firstDayOfMonth, DateAdd( Today(), 1 - Day( Today() ), Days) );
    Set( _firstDayInView, DateAdd(_firstDayOfMonth, -(Weekday( _firstDayOfMonth ) - 2 + 1), Days));
    Set( _lastDayOfMonth, DateAdd( DateAdd( _firstDayOfMonth, 1, Months ), -1, Days ) )
    ```

    上記のコードは、適切なカレンダー ビューを表示するために必要なすべての日付変数をリセットします:

    - **\_dateSelected** は今日にリセットされます。
    - **\_firstDayOfMonth** は今日の月の最初の日にリセットされます。
    - **\_firstDayInView** は今日の月を選択すると、表示可能な最初の日にリセットされます。
    - **\_lastDayOfMonth** は今日の月の最後の日にリセットされます。

    このトピックの[**カレンダー ドロップダウン**](#calendar-drop-down) セクションでは、これらの変数について詳しく説明しています。

## <a name="previous-month-chevron"></a>前月のシェブロン

![iconPrevMonth コントロール](media/calendar-screen/calendar-back.png)

- プロパティ: **OnSelect**<br>値: カレンダー ギャラリーで前月を表示する 4 つの **Set** 関数および **If** 関数:

    ```powerapps-dot
    Set( _firstDayOfMonth, DateAdd( _firstDayOfMonth, -1, Months ) );
    Set( _firstDayInView, 
        DateAdd( _firstDayOfMonth, -(Weekday( _firstDayOfMonth ) - 2 + 1), Days )
    );
    Set( _lastDayOfMonth, DateAdd(DateAdd( _firstDayOfMonth, 1, Months ), -1, Days ) );
    If( _minDate > _firstDayOfMonth,
        Collect( MyCalendarEvents,
            'Office365'.GetEventsCalendarViewV2( _myCalendar.Name,
                Text( _firstDayInView, UTC ), 
                Text( DateAdd( _minDate, -1, Days ), UTC )
            ).value
        );
        Set( _minDate, _firstDayInView )
    )
    ```

    > [!NOTE]
    > **\_firstDayOfMonth**、**\_firstDayInView**、および **\_lastDayOfMonth** の定義は、このトピックの[カレンダー ドロップダウン](#calendar-drop-down) セクションとほぼ同じです。

    上記のコードの最初の 3 行は、ユーザーが前月のシェブロンを選択すると実行されます。 このコードは、適切なカレンダー ビューを表示するために必要な変数を設定します。 残りのコードは、ユーザーが選択したカレンダーに対して今月以前に選択していない場合にのみ実行されます。

    その場合、**\_minDate** は前月が表示されるときに表示される最初の日です。 ユーザーがアイコンを選択する前に、**\_minDate** には当月の 23 日の最小許容値があります。 (3 月 1 日が土曜日になると、3 月の **\_firstDayInView** は 2月 23 日です。) つまり、ユーザーが今月まだ選択していない場合、**\_minDate** は新しい **\_ firstDayOfMonth** より大きく、**If** 関数は **true** に戻ります。 コードが実行され、コレクションおよび変数が更新されます:

    - **MyCalendarEvents** は、[Office365.GetEventsCalendarViewV2](https://docs.microsoft.com/connectors/office365/#get-calendar-view-of-events--v2-) 操作で選択したカレンダーからイベントを取得します。 日付範囲は **\_firstDayInView** 日付および **\_minDate** - 1 です。 **MyCalendarEvents** には既に **\_minDate** 日付のイベントが含まれているため、この新しい日付範囲の最大値はその日付から 1 が差し引かれます。

    - **\_minDate** は現在の **\_firstDayInView** に設定されています。これは、イベントが取得された最初の日付だからです。 ユーザーが前月のシェブロンを選択してこの日付に戻ると、**If** 関数が **false** に戻ります。このビューのイベントは既に **MyCalendarEvents** でキャッシュされているため、コードは実行されません。

## <a name="next-month-chevron"></a>翌月のシェブロン

![iconNextMonth コントロール](media/calendar-screen/calendar-forward.png)

- プロパティ: **OnSelect**<br>
    値: カレンダー ギャラリーで翌月を表示する 4 つの **Set** 関数および **If** 関数:

    ```powerapps-dot
    Set( _firstDayOfMonth, DateAdd( _firstDayOfMonth, 1, Months ) );
    Set( _firstDayInView, 
        DateAdd( _firstDayOfMonth, -(Weekday( _firstDayOfMonth ) - 2 + 1), Days ) );
    Set( _lastDayOfMonth, DateAdd( DateAdd( _firstDayOfMonth, 1, Months ), -1, Days ) );
    If( _maxDate < _lastDayOfMonth,
        Collect( MyCalendarEvents, 
            'Office365'.GetEventsCalendarViewV2( _myCalendar.Name, 
                Text( DateAdd( _maxDate, 1, Days ), UTC ), 
                DateAdd( _firstDayInView, 40, Days )
            ).value
        );
        Set( _maxDate, DateAdd( _firstDayInView, 40, Days) )    
    )
    ```

    > [!NOTE]
    > **\_firstDayOfMonth**、**\_firstDayInView**、および **\_lastDayOfMonth** の定義は、このトピックの[カレンダー ドロップダウン](#calendar-drop-down) セクションとほぼ同じです。

    前のコードの最初の 3 行は、ユーザーが翌月のシェブロンを選択したときに実行され、適切なカレンダービューを表示するために必要な変数を設定します。 残りのコードは、ユーザーが選択したカレンダーに対して今月以前に選択していない場合にのみ実行されます。

    その場合、**\_maxDate** は前月が表示されるときに表示される最後の日です。 ユーザーが翌月のシェブロンを選択する前に、**\_maxDate** には翌月の 13 日の最大許容値があります。 (2 月 1 日がうるう年ではない日曜日になると、**\_maxDate** は 3 月13 日で、**\_firstDayInView** + 40 日です。) つまり、ユーザーが今月まだ選択していない場合、**\_maxDate** は新しい **\_lastDayOfMonth** より大きく、**If** 関数は **true** に戻ります。 コードが実行され、コレクションおよび変数が更新されます:

    - **MyCalendarEvents** は、[Office365.GetEventsCalendarViewV2](https://docs.microsoft.com/connectors/office365/#get-calendar-view-of-events--v2-) 操作で選択したカレンダーからイベントを取得します。 日付範囲は **\_maxDate** + 1 日および **\_firstDayInView** + 40 日です。 **MyCalendarEvents** には既に **\_minDate** 日付のイベントが含まれているため、この新しい日付範囲の最小値はその日付から 1 が追加されます。 **\_firstDayInView** + 40 は、**\_maxDate** の数式なので、範囲の 2 つ目の日付は新しい **\_maxDate** です。

    - **\_maxDate** は現在の **\_firstDayInView** + 40 日に設定されています。これは、イベントが取得された最後の日付だからです。 ユーザーが翌月のシェブロンを選択してこの日付に戻ると、**If** 関数が **false** に戻ります; このビューのイベントは既に **MyCalendarEvents** でキャッシュされているため、コードは実行されません。

## <a name="calendar-gallery"></a>カレンダー ギャラリー

![MonthDayGallery コントロール](media/calendar-screen/calendar-month-gall.png)

- プロパティ: **アイテム**<br>
    値: `[0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,
    20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,41]`
  
  最悪のシナリオでは、カレンダー ビューに 42 日間表示する必要があるため、0 から 41 のセットがカレンダー ギャラリーのアイテムに使用されます。 これは、月の最初が土曜日に発生し、月の最後が日曜日に発生する場合に発生します。 この場合、カレンダーは前月から 6 日を月の最初を含む行に、翌月から 6 日を月の最後を含む行に表示します。 これは 42 の一意の値で、そのうち 30 は選択した月のものです。

- プロパティ: **WrapCount**<br>
    値: `7`

  この値は、週 7 日を反映しています。

### <a name="title-control-in-the-calendar-gallery"></a>カレンダー ギャラリーのタイトル コントロール

![MonthDayGallery タイトル コントロール](media/calendar-screen/calendar-month-text.png)

- プロパティ: **テキスト**<br>
    値: `Day( DateAdd( _firstDayInView, ThisItem.Value, Days ) )`

    **\_firstDayInView** が (**\_firstDayOfMonth** - 平日の値) + 1 と定義されていることを思い出してください。 **\_firstDayInView** が常に日曜日であり、**\_firstDayOfMonth** が常に **MonthDayGallery** の最初の行にあることを示します。 これら 2 つの要素のために、**\_firstDayInView** は常に **MonthDayGallery** の最初のセルにあります。 **ThisItem.Value** は **MonthDayGallery** アイテムのプロパティのセルの番号です。 したがって、**\_firstDayInView** を開始点として、各セルは **\_firstDayInView** + それぞれのセル値の増分を表示します。

- プロパティ: **フィル**<br>
    値: **If** 関数 1 つ:

    ```powerapps-dot
    If( DateAdd( _firstDayInView, ThisItem.Value ) = Today() && 
                DateAdd( _firstDayInView, ThisItem.Value ) = _dateSelected, 
            RGBA( 0, 0, 0, 0 ),
        DateAdd( _firstDayInView, ThisItem.Value) = Today(), 
            ColorFade( Subcircle.Fill, 0.67 ),
        Abs( Title.Text - ThisItem.Value) > 10,
            RGBA( 200, 200, 200, 0.3 ),
        RGBA( 0, 0, 0, 0 )
    )
    ```

  **テキスト** プロパティの説明で説明したように、`DateAdd(_firstDayInView, ThisItem.Value)` は表示されるセルの日を表します。 これを考慮して、上記のコードはこれらの比較を実行します:
  1. セルの値が今日の日付であり、かつこのセルが **\_dateSelected** に相当する場合、フィル値を指定しないでください。
  1. セルの値は今日の日付ですが、**\_dateSelected** に相当しない場合、**ColorFade** フィルを指定してください。
  1. 最後の比較はそれほど明確ではありません。 これは、セルの実際のテキスト値およびセル項目の値 (表示されている番号とアイテム番号) の比較です。<br>

      これをよりよく理解するため、土曜日に始まり日曜日に終わる月である 2018 年 9 月を考慮します。 この場合、カレンダーの最初の行には 8 月 26 日から 31 日および 9 月 1 日が表示され、`Abs(Title.Text - ThisItem.Value) = 26` で 9 月 1 日まで表示されます。 次に `Abs(Title.Text - ThisItem.Value) = 5`。 カレンダーの最後の行まで 5 に留まると、9 月 30 日および 10 月 1 日から 6 日が表示されます。 `Abs(Title.Text - ThisItem.Value)` の中で、9 月 30 日は引き続き 5 ですが、10 月の日付は 35 になります。<br>

      これはパターンです: 前月から表示される日については、`Abs(Title.Text - ThisItem.Value)` が常に表示される最初の日の `Title.Text` 値に等しいものです。 翌月に表示される日については、`Abs(Title.Text - ThisItem.Value)` が常にその月 (この場合は 10 月 1 日) から 1 を引いた最初のセルの **MonthDayGallery** アイテム値に等しいものです。 そして最も重要なのは、現在選択されている月に表示される日については、前の例が示しているように、`Abs(Title.Text - ThisItem.Value)` は常にその月の最初のアイテム値から 1 を引いた値に等しく、5 を超えることはありません。 したがって、数式を `Abs(Title.Text - ThisItem.Value) > 5` として書き込むことが完全に有効です。

      次のステートメントは、日付値が現在選択されている月の範囲外かどうかを確認します。 その場合、**フィル**は部分的に不透明な灰色です。

    > [!NOTE]
    > この最後の比較の有効性を自分で確認するには、**ラベル** コントロールをギャラリーに挿入し、その**テキスト** プロパティをこの値に設定します:<br>`Abs(Title.Text - ThisItem.Value)`。

- プロパティ: **表示する**<br>
    値:

    ```powerapps-dot
    !(
        DateAdd( _firstDayInView, ThisItem.Value, Days ) - 
            Weekday( DateAdd( _firstDayInView, ThisItem.Value,Days ) ) + 1 
        > _lastDayOfMonth
    )
    ```

    上記のステートメントは、現在選択されている月の日が発生しない行にセルがあるかどうかを確認します。 日付値から任意の曜日の平日の値を差し引いて 1 を加えると、その日が存在する行の最初のアイテムが常に返されることを思い出してください。 したがって、このステートメントは、行の最初の日が表示可能な月の最後の日の後かどうかを確認します。 その場合、行全体に翌月の日が含まれているため、表示されません。

- プロパティ: **OnSelect**<br>
    値:  **\_dateSelected** 変数を選択したセルの日付に設定する **Set** 関数:

    ```powerapps-dot
    Set( _dateSelected, DateAdd( _firstDayInView, ThisItem.Value, Days ) )
    ```

### <a name="circle-control-in-the-calendar-gallery"></a>カレンダー ギャラリーの サークル コントロール

![MonthDayGallery サークル コントロール](media/calendar-screen/calendar-month-event.png)

- プロパティ: **表示する**<br>
    値: 選択した日付にイベントがスケジュールされているかどうか、および**サブサークル**と**タイトル** コントロールが表示されるかどうかを決定する数式:

    ```powerapps-dot
    CountRows(
        Filter( MyCalendarEvents, 
            DateValue( Text( Start ) ) = DateAdd( _firstDayInView, ThisItem.Value, Days )
        )
    ) > 0 && !Subcircle.Visible && Title.Visible
    ```

    イベントの**開始**フィールドがそのセルの日付に相当する場合、**タイトル** コントロールが表示されている場合、および**サブサークル** コントロールが表示されていない場合、**サークル** コントロールは表示されます。 つまり、このコントロールは、この日に少なくとも 1 つのイベントが発生し、この日が選択されていない場合に表示されます。 選択された場合、その日のイベントが **CalendarEventsGallery** コントロールに表示されます。

### <a name="subcircle-control-in-the-calendar-gallery"></a>カレンダー ギャラリーの サブサークル コントロール

![MonthDayGallery サブサークル コントロール](media/calendar-screen/calendar-month-selected.png)

- プロパティ: **表示する**<br>
    値:

    ```powerapps-dot
    DateAdd( _firstDayInView, ThisItem.Value ) = _dateSelected && Title.Visible
    ```

  **サブサークル** コントロールは **\_dateSelected** がセルの日付に相当し、**タイトル** コントロールが表示される場合に表示されます。 つまり、このコントロールは、セルが現在選択されている日付である場合に表示されます。

## <a name="events-gallery"></a>イベント ギャラリー

![CalendarEventsGallery コントロール](media/calendar-screen/calendar-events-gall.png)

- プロパティ: **アイテム**<br>
    値: イベントギャラリーを並べ替えてフィルター処理する数式:

    ```powerapps-dot
    SortByColumns(
        Filter( MyCalendarEvents,
            Text( Start, DateTimeFormat.ShortDate ) = Text( _dateSelected, DateTimeFormat.ShortDate )
        ),
        "Start"
    )
    ```

   **MyCalendarEvents** コレクションには、**\_minDate** と **\_maxDate** との間のすべてのイベントが含まれます。 選択した日付のみのイベントを表示するために、**MyCalendarEvents** にフィルター処理が適用され、**\   _dateSelected** に相当する開始日を持つイベントが表示されます。 次に、アイテムは順番に並べるため、開始日で並べ替えられます。

## <a name="next-steps"></a>次の手順

- [このスクリーンに関する詳細情報](./calendar-screen-overview.md)
- [Power Apps での Office 365 Outlook コネクタについての詳細](../connections/connection-office365-outlook.md)
- [Power Apps での Office 365 ユーザー コネクタについての詳細](../connections/connection-office365-users.md)
