---
title: カレンダー スクリーン テンプレート | Microsoft Docs
description: キャンバス アプリのカレンダー スクリーン テンプレートの仕組みを理解し、スクリーンを変更し、アプリの一部として拡張する
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/28/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e4c466a2a090836ff880301f0960302413a3e25e
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3307005"
---
# <a name="overview-of-the-calendar-screen-template-for-canvas-apps"></a>キャンバス アプリのカレンダー スクリーン テンプレートの概要

キャンバス アプリで、Office 365 Outlook アカウントからユーザーの今後のイベントを表示するカレンダー スクリーンを追加します。 ユーザーはカレンダーから日付を選択し、その日のイベントのリストをスクロールできます。 リストに表示されている詳細を変更し、各イベントの詳細を表示する 2 番目のスクリーンを追加し、各イベントの出席者のリストを表示し、その他のカスタマイズを行うことができます。

[メール](email-screen-overview.md)、組織内の[ユーザー](people-screen-overview.md)、およびユーザーが会議に招待するユーザーの[使用可能性](meeting-screen-overview.md)などの、Office 365 とは異なるデータを表示する他のテンプレート ベースのスクリーンを追加することもできます。

この概要では次のことについて説明します。
> [!div class="checklist"]
> * 既定のカレンダー スクリーンの使い方。
> * 変更する方法。
> * アプリに統合する方法。

このスクリーンの既定機能についてさらに詳しく知りたい場合は、[カレンダー スクリーンを参照する](calendar-screen-reference.md) を参照してください。

## <a name="prerequisite"></a>前提条件

[Power Apps でアプリを作成する](../data-platform-create-app-scratch.md) ときに、画面およびその他のコントロールの追加および構成を行う方法に関する知識。

## <a name="default-functionality"></a>既定機能

テンプレートからカレンダースクリーンを追加するには:

1. Power Apps に[サインインし](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)、アプリを作成するか、または Power Apps Studio で既存のアプリを開きます。

    このトピックでは電話アプリについて説明しますが、同じ概念がタブレット PC アプリにも適用されます。

1. リボンの**ホーム** タブで、**新しいスクリーン** > **カレンダー**を選択します。

    既定では、スクリーンは次のようになります。

    ![カレンダー スクリーン](media/calendar-screen/calendar-initial.png)

1. データを表示するには、スクリーンの上部のドロップダウン リストでオプションを選択します。

    ![読み込みが完了した後のカレンダー スクリーン](./media/calendar-screen/calendar-screen.png)

いくつかの役に立つ注意事項があります。

* 既定では今日の日付が選択されており、右上隅のカレンダー アイコンを選択することによって簡単にその日付に戻ることができます。
* 別の日付を選択した場合、円がその周囲に表示され、淡色の長方形 (既定のテーマが適用されている場合は青) が今日の日付の周囲に表示されます。
* 特定の日付に少なくとも 1 つのイベントがスケジュールされている場合、カレンダーでその日付の下に小さい色付きの円が表示されます。
* 1 つまたは複数のイベントがスケジュールされている日付を選択した場合、カレンダーの下のリストにイベントが表示されます。

## <a name="modify-the-screen"></a>スクリーンを変更する

このスクリーンの既定機能は、いくつかの一般的な方法で変更できます。

* [カレンダーを指定します](calendar-screen-overview.md#specify-the-calendar)。
* [イベントに関するさまざまな詳細を表示します](calendar-screen-overview.md#show-different-details-about-an-event)。
* [非ブロックイベントを非表示にします](calendar-screen-overview.md#hide-nonblocking-events)。

スクリーンをさらに変更する場合は、[カレンダー スクリーンを参照](./calendar-screen-reference.md) をガイドとして使用してください。

### <a name="specify-the-calendar"></a>カレンダーを指定する

ユーザーが表示するカレンダーが既にわかっている場合は、アプリを公開する前にそのカレンダーを指定することで、スクリーンを簡素化できます。 この変更により、カレンダーのドロップダウン リストの必要がなくなるため、削除できます。

1. アプリの既定スクリーンの **[OnStart](../controls/control-screen.md)** プロパティを次の数式に設定します。

    ```powerapps-dot
    Set( _userDomain, Right( User().Email, Len( User().Email ) - Find( "@", User().Email ) ) );
    Set( _dateSelected, Today() );
    Set( _firstDayOfMonth, DateAdd( Today(), 1 - Day( Today() ), Days ) );
    Set( _firstDayInView, 
        DateAdd( _firstDayOfMonth, -( Weekday( _firstDayOfMonth) - 2 + 1 ), Days )
    );
    Set( _lastDayOfMonth, DateAdd( DateAdd( _firstDayOfMonth, 1, Months ), -1, Days ) );
    Set( _calendarVisible, false );
    Set( _myCalendar, 
        LookUp( Office365.CalendarGetTables().value, DisplayName = "{YourCalendarNameHere}" )
    );
    Set( _minDate, 
        DateAdd( _firstDayOfMonth, -( Weekday(_firstDayOfMonth) - 2 + 1 ), Days )
    );
    Set( _maxDate, 
        DateAdd(
            DateAdd( _firstDayOfMonth, -( Weekday(_firstDayOfMonth) - 2 + 1 ), Days ),
            40, 
            Days 
        )
    );
    ClearCollect( MyCalendarEvents, 
        Office365.GetEventsCalendarViewV2( _myCalendar.Name, 
            Text( _minDate, UTC ), 
            Text( _maxDate, UTC ) 
        ).value
    );
    Set( _calendarVisible, true )
    ```

    > [!NOTE]
    > この数式は、選択されたカレンダーのドロップダウン リストの **OnSelect** プロパティの既定値から少し編集されています。 コントロールの詳細については、[カレンダー - スクリーンを参照](./calendar-screen-reference.md#calendar-drop-down) のセクションを参照してください。

1. 中かっこを含む `{YourCalendarNameHere}` を、表示するカレンダーの名前 (**カレンダー**など) に置き換えます。

    > [!IMPORTANT]
    > 次の手順では、アプリにカレンダー スクリーンを 1 つだけ追加したことを前提としています。 複数を追加した場合、コントロール名 (**iconCalendar1** など) は異なる値で終わり、それに応じて数式を調整する必要があります。

1. **iconCalendar1** コントロールの **Y** プロパティを次の式に設定します。

    `RectQuickActionBar1.Height + 20`

1. **LblMonthSelected1** コントロールの **Y** プロパティを次の式に設定します。

    `iconCalendar1.Y + iconCalendar1.Height + 20`

1. **LblNoEvents1** コントロールの**テキスト** プロパティを次の値に設定します。

    `"No events scheduled"`

1. **LblNoEvents1** の**表示**プロパティを次の数式に設定します。

    `CountRows(CalendarEventsGallery1.AllItems) = 0 && _calendarVisible`

1. コントロールを削除します。

    - **dropdownCalendarSelection1**
    - **LblEmptyState1**
    - **iconEmptyState1**

1. カレンダー スクリーンが既成スクリーンでない場合は、既定スクリーンからカレンダー スクリーンに移動するボタンを追加して、アプリをテストできるようにします。

    たとえば、空白から作成したアプリにカレンダー スクリーンを追加した場合、**スクリーン 2** に移動する**スクリーン 1** にボタンを追加します。

1. アプリを保存し、次にブラウザーまたはモバイル デバイスでテストします。

### <a name="show-different-details-about-an-event"></a>イベントに関するさまざまな詳細を表示する

既定では、**CalendarEventsGallery** と呼ばれるカレンダーの下のギャラリーは、各イベントの開始時間、期間、件名および場所を表示します。 ギャラリーを構成して [Office 365 コネクタ](https://docs.microsoft.com/connectors/office365/#calendareventclientreceive) がサポートするフィールド (開催者など) を表示できます。

1. **CalendarEventsGallery** で、新規または既存のラベルの**テキスト**プロパティを `ThisItem` にピリオドを付けて設定します。

    IntelliSense には、選択できるフィールドを表示します。

1. 使用するフィールドを選択します。

    ラベルには、指定した情報の種類が表示されます。

### <a name="hide-nonblocking-events"></a>非ブロックイベントを非表示にする

多くのオフィスでは、チームメンバーが会議出席依頼を送信してオフィスから離れる時を互いに通知します。 全員のスケジュールをブロックしないため、要求を送信するユーザーは使用可能性を**解放**に設定します。 いくつかのプロパティを更新することにより、これらのイベントをカレンダーとギャラリーから非表示にすることができます。

1. **CalendarEventsGallery** の**項目**プロパティを次の数式に設定します。

    ```powerapps-dot
    SortByColumns(
        Filter(
            MyCalendarEvents,
            Text( Start, DateTimeFormat.ShortDate ) = 
                Text( _dateSelected, DateTimeFormat.ShortDate ),
            ShowAs <> "Free"
        ),
        "Start"
    )
    ```

    この数式では、**フィルター**機能は選択された日付以外の日付にスケジュールされたイベントだけでなく、使用可能性が**解放**に設定されたイベントも非表示されます。

1. カレンダーで、**サークル**コントロールの**表示**プロパティを次の数式に設定します。

    ```powerapps-dot
    CountRows(
        Filter(
            MyCalendarEvents,
            DateValue( Text(Start) ) = DateAdd( _firstDayInView, ThisItem.Value, Days ),
            ShowAs <> "Free"
        )
    ) > 0 && !Subcircle1.Visible && Title2.Visible
    ```
    この式には、前の数式と同じフィルターが含まれています。 したがって、イベント インジケーターの円は、選択した日付に 1 つまたは複数のイベントがあり、使用可能性が**解放**でない場合にのみ、日付の下に表示されます。

## <a name="integrate-the-screen-into-an-app"></a>スクリーンをアプリに統合する

カレンダー スクリーンは、それ自体が強力なコントロールのバンドルですが、通常は、より大きくより多目的なアプリの一部として最適に実行します。 スクリーンは次のオプションを追加するなど、さまざまな異なる方法でより大きなアプリに統合することができます。

* [イベントの詳細を表示します](calendar-screen-overview.md#view-event-details)。
* [イベントの出席者を表示します](calendar-screen-overview.md#show-event-attendees)。

### <a name="view-event-details"></a>イベントの詳細を表示する

ユーザーが **CalendarEventsGallery** でイベントを選択した場合、そのイベントに関する詳細を表示する別のスクリーンを開くことができます。

> [!NOTE]
> この手順では、動的コンテンツを含むギャラリーのイベントの詳細について説明しますが、別の方法を実行しても同様の結果を達成することができます。 たとえば、代わりに一連のラベルを使用して、デザインのコントロールをさらに行なうことができます。

1. 空白の高さ調整可能なギャラリーおよびカレンダー スクリーンに戻るボタンを含む **EventDetailsScreen** と呼ばれる空白のスクリーンを追加します。

1. 高さ調節可能なギャラリーで、**ラベル** コントロールおよび **HTML テキスト** コントロールを追加し、両方の **AutoHeight** プロパティを **true** に設定します。

    > [!NOTE]
    > Power Apps は各イベントのメッセージ本文を HTML テキストとして取得するため、そのコンテンツを **HTML テキスト** コントロールで表示する必要があります。

1. **HTML テキスト** コントロールの **Y** プロパティを次の式に設定します。

    `Label1.Y + Label1.Height + 20`

1. 必要に応じて、スタイルのニーズに合わせて追加のプロパティを調整します。

    たとえば、**HTML テキスト** コントロールの下に区切り線を追加することができます。

1. 高さ調節可能なギャラリーの**項目**プロパティを次の数式に設定します。

    ```powerapps-dot
    Table(
        { Title: "Subject", Value: _selectedCalendarEvent.Subject },
        { 
            Title: "Time", 
            Value: _selectedCalendarEvent.Start & " - " & _selectedCalendarEvent.End 
        },
        { Title: "Body", Value: _selectedCalendarEvent.Body }
    )
    ```

    この数式は **_selectedCalendarEvent** のフィールド値に設定された動的データのギャラリーを作成し、**CalendarEventsGallery** コントロールでユーザーがイベントを選択するたびに設定されます。 ラベルをさらに追加することにより、このギャラリーを拡張して他のフィールドを含めることができますが、このセットは良い開始点を提供します。

1. ギャラリー項目を配置したら、**レベル** コントロールの**テキスト** プロパティを `ThisItem.Title` に、および **HTML テキスト** コントロールの **HtmlText** プロパティを `ThisItem.Value` に設定します。

1. **CalendarEventsGallery** で、**タイトル**コントロールの **OnSelect** プロパティを次の数式に設定します。

    ```powerapps-dot
    Set( _selectedCalendarEvent, ThisItem );
    Navigate( EventDetailsScreen, None )
    ```

    > [!Note]
    > **_selectedCalendarEvent** 変数を使用する代わりに、**CalendarEventsGallery**.Selected を代わりに使用できます。

### <a name="show-event-attendees"></a>イベントの出席者を表示する

`Office365.GetEventsCalendarViewV2` 操作は、セミコロンで区切られた必須および任意の出席者のセットを含む、各イベントのさまざまなフィールドを取得します。 この手順では、各出席者のセットを解析し、組織内の出席者を特定し、Office 365 プロファイルを取得します。

1. アプリに Office 365 ユーザー コネクタが含まれていない場合は、[追加します](../add-data-connection.md)。

1. 会議出席者の Office 365 プロファイルを取得するには **CalendarEventsGallery** で**タイトル** コントロールの **OnSelect** プロパティを次の数式に設定します。

    ```powerapps-dot
    Set( _selectedCalendarEvent, ThisItem );
    ClearCollect( AttendeeEmailsTemp,
        Filter(
            Split( ThisItem.RequiredAttendees & ThisItem.OptionalAttendees, ";" ),
            !IsBlank( Result )
        )
    );
    ClearCollect( AttendeeEmails,
        AddColumns( AttendeeEmailsTemp, 
            "InOrg",
            Upper( _userDomain ) = Upper( Right( Result, Len( Result ) - Find( "@", Result ) ) )
        )
    );
    ClearCollect( MyPeople,
        ForAll( AttendeeEmails, If( InOrg, Office365Users.UserProfile( Result ) ) ) 
    );
    Collect( MyPeople,
        ForAll( AttendeeEmails,
            If( !InOrg, 
                { DisplayName: Result, Id: "", JobTitle: "", UserPrincipalName: Result }
            )
        )
    )
    ```

次のリストでは、各 **ClearCollect** 操作の動作について説明します。

- ClearCollect(AttendeeEmailsTemp)
    ```powerapps-dot
    ClearCollect( AttendeeEmailsTemp,
        Filter(
            Split( ThisItem.RequiredAttendees & ThisItem.OptionalAttendees, ";" ), 
            !IsBlank( Result)
        )
    );
    ```

    この数式は、必須および任意の出席者を単一の文字列に連結し、次にその文字列を各セミコロンで個々のアドレスに分割します。 次に、数式はそのセットから空白の値をフィルター処理して省き、別の値を **AttendeeEmailsTemp** と呼ばれるコレクションに追加します。

- ClearCollect(AttendeeEmails)
    ```powerapps-dot
    ClearCollect( AttendeeEmails,
        AddColumns( AttendeeEmailsTemp, 
            "InOrg",
            Upper( _userDomain ) = Upper( Right( Result, Len(Result) - Find("@", Result) ) )
        )
    );
    ```
    この数式は、出席者が組織内にいるかどうかを大まかに決定します。 **_userDomain** の定義は、単にアプリを実行しているユーザーのメール アドレスのドメイン URL です。 このリストは、**AttendeeEmailsTemp** コレクションに **InOrg** という名前の追加の true/false の列を作成します。 この列には、**userDomain** が **AttendeeEmailsTemp** の特定の行のメール アドレスのドメイン URL に相当する場合、**true** が含まれます。

    この方法は常に正確であるとは限りませんが、かなり近いものとなります。 たとえば、組織の特定の出席者が Jane@OnContoso.com のようなメール アドレスを持っているのに対して、**_userDomain** は Contoso.com です。 アプリのユーザーと Jane は同じ会社で働いているかもしれませんが、メール アドレスに若干の違いがあります。 このような場合は、次の数式を使用できます。

    `Upper(_userDomain) in Upper(Right(Result, Len(Result) - Find("@", Result)))`

    ただし、この数式は Jane@NotTheContosoCompany.com のようなメールアドレスと Contoso.com のような **_userDomain** と一致しますが、それらの人々は同じ会社で働いていません。

- ClearCollect(MyPeople)

    ```powerapps-dot
    ClearCollect( MyPeople,
        ForAll( AttendeeEmails, 
            If( InOrg, 
                Office365Users.UserProfile( Result )
            )
        )
    );
    Collect( MyPeople,
        ForAll( AttendeeEmails,
            If( !InOrg, 
                { 
                    DisplayName: Result, 
                    Id: "", 
                    JobTitle: "", 
                    UserPrincipalName: Result
                }
            )
        )
    );
    ```
    Office 365 プロファイルを取得するには、[Office365Users.UserProfile](https://docs.microsoft.com/connectors/office365users/#userprofile) または [Office365Users.UserProfileV2](https://docs.microsoft.com/connectors/office365users/#userprofile) 操作を使用する必要があります。 これらの操作では、最初にユーザーの組織内にいる出席者のすべての Office 365 プロファイルを収集します。次に、操作は、組織外からの出席者のためのいくつのフィールドを追加します。 これらの 2 つの項目を個別の操作に分けたのは **ForAll** ループは順序を保証しないからです。 したがって、最初に **ForAll** が組織外からの参加者を収集する可能性があります。 この場合、**MyPeople** のスキーマには **DisplayName**、**ID**、**JobTitle**、および **UserPrincipalName** だけが含まれます。 ただし、UserProfile 操作は、それよりもはるかに豊富なデータを取得します。 そのため、**MyPeople** コレクションでは別のプロファイルの前に Office 365 プロファイルを追加するように強制します。

    > [!NOTE]
    > 1 つの **ClearCollect** 関数だけで、同じことを達成できます。

    ```powerapps-dot
    ClearCollect( MyPeople, 
        ForAll(
            AddColumns(
                Filter(
                    Split(
                        ThisItem.RequiredAttendees & ThisItem.OptionalAttendees, 
                        ";"
                    ), 
                    !IsBlank( Result )
                ), 
                "InOrg", _userDomain = Right( Result, Len( Result ) - Find( "@", Result ) )
            ), 
            If( InOrg, 
                Office365Users.UserProfile( Result ), 
                { 
                    DisplayName: Result, 
                    Id: "", 
                    JobTitle: "", 
                    UserPrincipalName: Result, 
                    Department: "", 
                    OfficeLocation: "", 
                    TelephoneNumber: ""
                }
            )
        )
    )
    ```

この演習を完了するには:

1. **項目**プロパティが **MyPeople** に設定されているギャラリーを含むスクリーンを追加します。

1. **CalendarEventsGallery** の中にある**タイトル** コントロールの **OnSelect** プロパティで、**移動**関数を前の手順で作成したスクリーンに追加します。

## <a name="next-steps"></a>次の手順

* [スクリーンの参照ドキュメントを表示します](calendar-screen-reference.md)。
* [Office 365 Outlook コネクタについての詳細](../connections/connection-office365-outlook.md)。
* [Office 365 ユーザー コネクタについての詳細](../connections/connection-office365-users.md)。
