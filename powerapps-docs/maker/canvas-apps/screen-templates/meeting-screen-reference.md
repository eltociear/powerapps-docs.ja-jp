---
title: キャンバス アプリのミーティング スクリーン テンプレートの参照 | Microsoftドキュメント
description: Power Apps でのキャンバス アプリのミーティング スクリーン テンプレートに関する仕組みの詳細を理解する
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 01/03/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 66cf9ae4cc16ba8004775ba86db3f5497fb99937
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3307189"
---
# <a name="reference-information-about-the-meeting-screen-template-for-canvas-apps"></a>キャンバス アプリのミーティング スクリーン テンプレートに関する参照情報

Power Apps でのキャンバス アプリの場合、ミーティング スクリーン テンプレートの重要な各コントロールがスクリーン全体の既定機能にどのように貢献するかを理解します。 この詳細は、動作の数式およびコントロールがユーザー入力にどのように応答するかを決定する他のプロパティの値を表示します。 このスクリーン既定機能の概要については、[ミーティング スクリーンの概要](meeting-screen-overview.md) を参照してください。

このトピックは、一部の重要なコントロールに注目し、それらのコントロールのさまざまなプロパティ (**Items** および **OnSelect** など) に設定する式または数式ついて説明しています。

* [招待タブ (LblInviteTab)](#invite-tab)
* [スケジュール タブ (LblScheduleTab)](#schedule-tab)
* [テキスト検索ボックス](#text-search-box)
* [追加アイコン (AddIcon)](#add-icon)
* [ユーザーがギャラリーを参照する](#people-browse-gallery) (+ 子コントロール)
* [ミーティング ユーザー ギャラリー](#meeting-people-gallery) (+ 子コントロール)
* [ミーティングの日付ピッカー (MeetingDateSelect)](#meeting-date-picker)
* [ミーティング期間ドロップダウン (MeetingDurationSelect)](#meeting-duration-drop-down)
* [ミーティング時間 ギャラリーを検索する](#find-meeting-times-gallery) (+ 子コントロール)
* [部屋がギャラリーを参照する](#room-browse-gallery) (+ 子コントロール)
* [バック シェブロン (RoomsBackNav)](#back-chevron) (テナントに部屋リストがない場合は表示されない場合があります)
* [アイコンを送信](#send-icon)

## <a name="prerequisite"></a>前提条件

[Power Apps でアプリを作成する](../data-platform-create-app-scratch.md) ときに、画面およびその他のコントロールの追加および構成を行う方法に関する知識。

## <a name="invite-tab"></a>招待タブ

   ![LblInviteTab コントロール](media/meeting-screen/meeting-invite-text.png)

* プロパティ: **Color**<br>
    値: `If( _showDetails, LblRecipientCount.Color, RectQuickActionBar.Fill )`

    **_showDetails** は、**LblInviteTab** コントロールまたは **LblScheduleTab** コントロールが選択されているかどうかを決定するために使用される変数です。 **_showDetails** の値が **true** であれば、**LblScheduleTab** が選択され、値が **false** であれば、**LblInviteTab** が選択されます。 つまり、**_showDetails** の値が **true** (このタブは選択*されない*) の場合、タブの色は **LblRecipientCount** の色と一致します。 それ以外の場合は、**RectQuickActionBar** のフィル値と一致します。

* プロパティ: **OnSelect**<br> 
    値: `Set( _showDetails, false )`

    **_showDetails** 変数を **false** に設定します。つまり、招待タブのコンテンツが表示され、**スケジュール**タブのコンテンツは非表示です。

## <a name="schedule-tab"></a>スケジュール​​ タブ

   ![LblInviteTab コントロール](media/meeting-screen/meeting-schedule-text.png)

* プロパティ: **Color**<br>
    値: `If( !_showDetails, LblRecipientCount.Color, RectQuickActionBar.Fill )`

    **_showDetails** は、**LblInviteTab** コントロールまたは **LblScheduleTab** コントロールが選択されているかどうかを決定するために使用される変数です。 true であれば、**LblScheduleTab** が選択され、false の場合は、**LblInviteTab** 選択されます。 つまり、**_showDetails** の値が true (このタブは選択*される*) の場合、タブの色は **RectQuickActionBar** フィル値と一致します。 それ以外の場合は、**LblRecipientCount** の色の値と一致します。

* プロパティ: **OnSelect**<br>
    値: `Set( _showDetails, true )`

    **_showDetails** 変数を **true** に設定します。つまり、スケジュール タブ のコンテンツは表示され、招待タブのコンテンツが非表示です。

## <a name="text-search-box"></a>テキスト検索ボックス

   ![TextSearchBox コントロール](media/meeting-screen/meeting-search-box.png)

<!--Include description of text search box control?-->

画面の他のいくつかのコントロールは、以下で依存関係があります:

* ユーザーがテキストの入力を開始すると、**PeopleBrowseGallery** が表示されます。
* ユーザーが有効な電子メール アドレスを入力すると、**AddIcon** が表示されます。
* ユーザーが **PeopleBrowseGallery** 内のユーザーを選択すると、検索内容はリセットされます。

## <a name="add-icon"></a>アイコンの追加

   ![AddIcon コントロール](media/email-screen/email-add-icon.png)

このコントロールを使用すると、ユーザーは組織内に存在しないアプリ ユーザーを、作成中のミーティング用受信者リストに追加できます。

* プロパティ: **Visible**<br>
    値: コントロールが表示されるために、すべて **true** と評価されることを確認する 3 つの論理:

    ```powerapps-dot
    !IsBlank( TextSearchBox.Text ) &&
        IsMatch( TextSearchBox.Text, Match.Email ) &&
        Not( Trim( TextSearchBox.Text ) in MyPeople.UserPrincipalName )
    ```

  行ごとに、このコード ブロックは、**AddIcon** コントロールが以下の場合にのみ表示されます:

  * **TextSearchBox** にテキストが含まれています。
  * **TextSearchBox** のテキストは、有効なメール アドレスです。
  * **TextSearchBox** のテキストは、**MyPeople** コレクションにまだ存在していません。

* プロパティ: **OnSelect**<br> 
    値: ユーザーを出席者リストに追加する**収集**ステートメント、使用可能なミーティング時間を更新するステートメント、およびいくつかの変数トグル:

    ```powerapps-dot
    Collect( MyPeople,
        { 
            DisplayName: TextSearchBox.Text, 
            UserPrincipalName: TextSearchBox.Text, 
            Mail: TextSearchBox.Text
        }
    );
    Concurrent(
        Reset( TextSearchBox ),
        Set( _showMeetingTimes, false ),
        UpdateContext( { _loadMeetingTimes: true } ),
        Set( _selectedMeetingTime, Blank() ),
        Set( _selectedRoom, Blank() ),
        Set( _roomListSelected, false ),
        ClearCollect( MeetingTimes, 
            AddColumns(
                'Office365'.FindMeetingTimes(
                    { 
                        RequiredAttendees: Concat(MyPeople, UserPrincipalName & ";")
                        MeetingDuration: MeetingDurationSelect.Selected.Minutes,
                        Start: Text( DateAdd( MeetingDateSelect.SelectedDate, 8, Hours ), UTC ),
                        End: Text( DateAdd( MeetingDateSelect.SelectedDate, 17, Hours ), UTC ),
                        MaxCandidates: 15, 
                        MinimumAttendeePercentage:1, 
                        IsOrganizerOptional: false, 
                        ActivityDomain: "Work"
                    }
                ).MeetingTimeSuggestions,
                "StartTime", MeetingTimeSlot.Start.DateTime, 
                "EndTime", MeetingTimeSlot.End.DateTime
            )
        )
    );
    UpdateContext( { _loadingMeetingTimes: false } );
    Set( _showMeetingTimes, true )
    ```

  このコントロールを選択すると、有効なメール アドレスが (有効なメール アドレスが **TextSearchBox** に入力された場合にのみ表示されます) **MyPeople** コレクション (このコレクションは出席者リストです) に追加され、新しいユーザー エントリで利用可能なミーティング時間を更新します。

  低レベルで、このコードはブロックします:
  1. メール アドレスを **MyPeople** コレクションに収集し、メールアドレスを **DisplayName**、**UserPrincipalName**、および**メール**フィールドへ収集します。
  1. **TextSearchBox** コントロールのコンテンツをリセットします。
  1. **_showMeetingTimes** 変数を **false** に設定します。 この変数は、選択された出席者がミーティングを開く時間を表示する **FindMeetingTimesGallery** の可視性をコントロールします。
  1. **_loadMeetingTimes** コンテキスト変数を **true** に設定します。 この変数によって、**_LblTimesEmptyState** などの読み込み状態のコントロール表示を切替え、データが読み込まれていることをユーザーに表示して、読み込み状態を設定します。
  1. **_selectedMeetingTime** を **Blank()** に設定します。 **_selectedMeetingTime** は、**FindMeetingTimesGallery** コントロールから選択されたレコードです。 別の出席者を追加すると、**_selectedMeetingTime** の以前の定義ではその出席者を利用できないかもしれないので、ここをブランクにします。
  1. **_selectedRoom** を **Blank()** に設定します。 **_selectedRoom** は、**RoomBrowseGallery** から選択された部屋のレコードです。 部屋の空室状況は、**_selectedMeetingTime** 値から決定されます。 その値が空白になると、**_selectedRoom** 値は無効になるため、空白である必要があります。
  1. **_roomListSelected** を **false** に設定します。 この行はすべての人に適用できるわけではありません。 Office では、さまざまな「部屋リスト」でグループ化できます。 部屋リストがある場合、このスクリーンはそれを考慮に入れており、最初に部屋リストを選択し、そのリスト内から部屋を選択できます。 **_roomListSelected** 値は、ユーザー (部屋リストのみのテナント内で) が、部屋リストまたは部屋リストのセット内の部屋を表示するかを決定するものです。 **false** に設定して、ユーザーに新しい部屋リストを再選択するように強制します。
  1. [Office365.FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times) 操作を使用して、参加者が利用可能なミーティング時間を決定して収集するします。 この操作は成功です:
      * 選択した各ユーザーの **UserPrincipalName** を *RequiredAttendees* パラメーターへ。
      * **MeetingDurationSelect** .Selected.Minutes を *MeetingDuration* パラメーターへ。
      * MeetingDateSelect.SelectedDate + 8 時間を *Start* パラメーターへ。 既定では、カレンダー コントロールの完全な日付/時刻は選択した日付の午前 12 時なので、8 時間が追加されます。 通常の営業時間内に、空室状況を取得したい場合があります。 通常の作業開始時間は午前 8 時です。
      * **MeetingDateSelect**.SelectedDate + 17 時間を *End* パラメーターへ。 午前 12 時 + 17 = 午後 5 時なので、17 時間が追加されます。 通常の作業終了時間は午後 5 時です。
      * *15* を *MaxCandidates* パラメーターへ。 つまり操作により、選択した日付の使用可能な上位 15 時間のみを戻します。 これは、8 時間の作業日に 30 分のチャンクが 16 しかなく、30 分のミーティングがこのスクリーンで設定できる最小のミーティングであるため、理にかなっています。
      * *1* を *MinimumAttendeePercentage* パラメーターへ。 基本的に、参加者がいない場合を除いて、ミーティング時間が取得されます。
      * **false** を *IsOrganizerOptional* パラメーターへ。 アプリ ユーザーは、このミーティングのオプションの参加者ではありません。
      * 「仕事」を *ActivityDomain* パラメーターへ。 つまり、取得される時間は通常の稼働時間内のものだけです。
  1. **ClearCollect** 関数は、「StartTime」と「EndTime」という 2 つの列も追加します。 これにより、戻されたデータが簡略化されます。 
  利用可能な開始時間と終了時間を含むフィールドは、**MeetingTimeSlot** フィールドです。 このフィールドは、開始および終了レコードを含むレコードで、それぞれの提案の **DateTime** と **TimeZone** 値です。 このレコードのネストを取得する代わりに、「StartTime」列と「EndTime」列を、これらの **Start > DateTime** および **End > DateTime** 値をコレクションの表面にもたらす **MeetingTimes** コレクションに追加します。
  1. これらの機能がすべて完了すると、**_loadingMeetingTimes** 変数は **false** と設定され、読み込み状態を削除し、**_showMeetingTimes** は **true** と設定され、**FindMeetingTimesGallery** と表示されます。

## <a name="people-browse-gallery"></a>ユーザー参照ギャラリー

   ![PeopleBrowseGallery コントロール](media/meeting-screen/meeting-browse-gall.png)

* プロパティ: **Items**<br>
    値: 
    ```powerapps-dot
    If( !IsBlank( Trim( TextSearchBox.Text ) ), 
        'Office365Users'.SearchUser( { searchTerm: Trim(TextSearchBox.Text), top: 15 } )
    )
    ```

このギャラリーのアイテムは、[Office365.SearchUser](https://docs.microsoft.com/connectors/office365users/#searchuser) 操作からの検索結果により設定されます。 操作は、検索語句として `Trim(**TextSearchBox**)` のテキストを受け取り、その検索に基づいて上位 15 件の結果を戻します。
  
**TextSearchBox** は、スペースでのユーザー検索が無効であるため、**Trim** 関数に囲われています。 `Office365Users.SearchUser` 操作は、ユーザーが検索する前に検索結果を取得するとパフォーマンスが低下するため、`If(!IsBlank(Trim(TextSearchBox.Text)) ... )` 機能で囲われています。

### <a name="people-browse-gallery-title"></a>ユーザー参照ギャラリー タイトル

   ![PeopleBrowseGallery Title コントロール](media/meeting-screen/meeting-browse-gall-title.png)

* プロパティ: **Text**<br>
    値: `ThisItem.DisplayName`

    ユーザーの表示名を Office 365 プロフィールから表示します。

* プロパティ: **OnSelect**<br>
    値: ユーザーを出席者リストに追加する**収集**ステートメント、使用可能なミーティング時間を更新するステートメント、およびいくつかの変数トグル:

    ```powerapps-dot
    Concurrent(
        Reset( TextSearchBox ),
        Set( _selectedUser, ThisItem ),
        If( Not( ThisItem.UserPrincipalName in MyPeople.UserPrincipalName ), 
            Collect( MyPeople, ThisItem ); 
            Concurrent(
                Set( _showMeetingTimes, false ),
                UpdateContext( { _loadMeetingTimes: true } ),
                Set( _selectedMeetingTime, Blank() ),
                Set( _selectedRoom, Blank() ),
                Set( _roomListSelected, false ),
                ClearCollect( MeetingTimes, 
                    AddColumns(
                        'Office365'.FindMeetingTimes(
                            {
                                RequiredAttendees: Concat( MyPeople, UserPrincipalName & ";" ),
                                MeetingDuration: MeetingDurationSelect.Selected.Minutes,
                                Start: Text( DateAdd( MeetingDateSelect.SelectedDate, 8, Hours ), UTC ),
                                End: Text( DateAdd( MeetingDateSelect.SelectedDate, 17, Hours ), UTC ),
                                MaxCandidates: 15, 
                                MinimumAttendeePercentage: 1, 
                                IsOrganizerOptional: false, 
                                ActivityDomain: "Work"
                            }
                        ).MeetingTimeSuggestions,
                        "StartTime", MeetingTimeSlot.Start.DateTime, 
                        "EndTime", MeetingTimeSlot.End.DateTime
                    )
                )
            );
            UpdateContext( { _loadingMeetingTimes: false } );
            Set( _showMeetingTimes, true )
        )
    )
    ```

    高レベルでは、このコントロールを選択すると、ユーザーを **MyPeople** コレクション (参加者リスト アプリのストレージ) に追加し、新しいユーザーの追加に基づいて、利用可能なミーティングを更新します。

    このコントロールの選択は、**AddIcon** コントロールの選択と非常に似ています; 唯一の違いは、`Set(_selectedUser, ThisItem)` ステートメントと操作の実行順序です。 そのため、この議論はそれほど深くありません。 より完全な説明については、[AddIcon コントロール](#add-icon) セクションをお読みください。

    このコントロールを選択すると、**TextSearchBox** がリセットされます。 次に、選択が **MyPeople** コレクションに無い場合、次のコントロールを確認ください:
    1. **_loadMeetingTimes** 状態を **true** に、**_showMeetingTimes** 状態を **false** に設定し、**_selectedMeetingTime** と **_selectedRoom** 変数を空白にし、**MyPeople** コレクション への新しい追加で、**MeetingTimes** コレクションを更新します。 
    1. **_loadMeetingTimes** 状態を **false** に、**_showMeetingTimes** を **true** に設定します。 選択がすでに **MyPeople** コレクションにある場合、**TextSearchBox** のコンテンツのみリセットします。

## <a name="meeting-people-gallery"></a>ミーティング ユーザー ギャラリー

   ![MeetingPeopleGallery コントロール](media/meeting-screen/meeting-people-gall.png)

* プロパティ: **Items**<br>
    値: `MyPeople`

    **MyPeople** コレクションとは、**PeopleBrowseGallery Title** コントロールで初期化または追加されたユーザーのコレクションです。

* プロパティ: **Height**<br>
    値: ギャラリーを最大高さ 350 まで拡大できるロジック:

    ```powerapps-dot
    Min( 
        76 * RoundUp( CountRows( MeetingPeopleGallery.AllItems ) / 2, 0 ),
        350
    )
    ```

  
   このギャラリーの高さは、ギャラリー内のアイテムの数に合わせて調整されます。最大の高さは 350 です。 計算式では、**MeetingPeopleGallery** の単一行の高さ 76 を取り、次に行数を掛けます。 **WrapCount** プロパティが 2 に設定されているため、実際の行の数は `RoundUp(CountRows(MeetingPeopleGallery.AllItems) / 2, 0)` です。

* プロパティ: **ShowScrollbar**<br>
    値: `MeetingPeopleGallery.Height >= 350`

    ギャラリーの最大高さが (350) に達すると、スクロール バーが表示されます。

### <a name="meeting-people-gallery-title"></a>ミーティング ユーザー ギャラリー タイトル

   ![MeetingPeopleGallery Title コントロール](media/meeting-screen/meeting-people-gall-title.png)

* プロパティ: **OnSelect**<br>
    
    値: `Set(_selectedUser, ThisItem)`
    
    **_selectedUser** 変数を、**MeetingPeopleGallery** で選択した項目に設定します。

### <a name="meeting-people-gallery-iconremove"></a>ミーティング ユーザー ギャラリー iconRemove

   ![MeetingPeopleGallery iconRemove コントロール](media/meeting-screen/meeting-people-gall-delete.png)

* プロパティ: **OnSelect**<br>
    値: **削除**ステートメントで出席者リストからユーザーを削除、**収集**ステートメントで利用可能なミーティング時間を更新、およびいくつかの変数トグル:

    ```powerapps-dot
    Remove( MyPeople, LookUp( MyPeople, UserPrincipalName = ThisItem.UserPrincipalName ) );
    Concurrent(
        Reset( TextSearchBox ),
        Set( _showMeetingTimes, false ),
        UpdateContext( { _loadMeetingTimes: true } ),
        Set( _selectedMeetingTime, Blank() ),
        Set( _selectedRoom, Blank() ),
        Set( _roomListSelected, false ),
        ClearCollect( MeetingTimes, 
            AddColumns(
                'Office365'.FindMeetingTimes(
                    {
                        RequiredAttendees: Concat( MyPeople, UserPrincipalName & ";" ), 
                        MeetingDuration: MeetingDurationSelect.Selected.Minutes,
                        Start: Text( DateAdd( MeetingDateSelect.SelectedDate, 8, Hours ), UTC ), 
                        End: Text( DateAdd( MeetingDateSelect.SelectedDate, 17, Hours ), UTC ),
                        MaxCandidates: 15, 
                        MinimumAttendeePercentage: 1, 
                        IsOrganizerOptional: false, 
                        ActivityDomain: "Work"
                    }
                ).MeetingTimeSuggestions,
                "StartTime", MeetingTimeSlot.Start.DateTime, 
                "EndTime", MeetingTimeSlot.End.DateTime
            )
        )
    );
    UpdateContext( { _loadingMeetingTimes: false } );
    Set( _showMeetingTimes, true )
    ```

  高いレベルでは、このコントロールを選択すると出席者リストからその人物が削除され、人物の削除に基づいて利用可能なミーティング時間が更新されます。

  上記コードの最初の行の後、このコントロールの選択は、**AddIcon** コントロールの選択とほぼ同じです。 そのため、この議論はそれほど深くありません。 より完全な説明については、[AddIcon コントロール セクション](#add-icon) をお読みください。

  コードの最初の行で、選択した項目が **MyPeople** コレクションから削除されます。 次のコードで:
  1. **TextSearchBox** リセットして、**MyPeople** コレクションからの選択を削除します。 
  1. **_loadMeetingTimes** 状態を **true** に、**_showMeetingTimes** 状態を **false** に設定し、**_selectedMeetingTime** と **_selectedRoom** 変数を空白にし、**MyPeople** コレクション への新しい追加で、**MeetingTimes** コレクションを更新します。 
  1. **_loadMeetingTimes** 状態を **false** に、**_showMeetingTimes** を **true** に設定します。

## <a name="meeting-date-picker"></a>ミーティング時間の選択

   ![MeetingDateSelect コントロール](media/meeting-screen/meeting-datepicker.png)

* プロパティ: **DisplayMode**<br>
    値: `If( IsEmpty(MyPeople), DisplayMode.Disabled, DisplayMode.Edit )`

    少なくとも 1 人の出席者が **MyPeople** コレクションに追加されるまで、ミーティングの日付を選択することはできません。

* プロパティ: **OnChange**<br>
    値: `Select( MeetingDateSelect )`

    選択した日付を変更すると、実行するコントロールの **OnSelect** プロパティにあるコードがトリガーとなります。

* プロパティ: **OnSelect**<br>
    値: **収集**ステートメントで利用可能なミーティング時間を更新、およびいくつかの変数トグル:
  
    ```powerapps-dot
    Concurrent(
        Reset( TextSearchBox ),
        Set( _showMeetingTimes, false ),
        UpdateContext( { _loadingMeetingTimes: true } ),
        Set( _selectedMeetingTime, Blank() ),
        Set( _selectedRoom, Blank() ),
        Set( _roomListSelected, false ),
        ClearCollect( MeetingTimes, 
            AddColumns(
                'Office365'.FindMeetingTimes(
                    {
                        RequiredAttendees: Concat( MyPeople, UserPrincipalName & ";" ), 
                        MeetingDuration: MeetingDurationSelect.Selected.Minutes,
                        Start: Text( DateAdd( MeetingDateSelect.SelectedDate, 8, Hours ), UTC ), 
                        End: Text( DateAdd( MeetingDateSelect.SelectedDate, 17, Hours ), UTC ),
                        MaxCandidates: 15, 
                        MinimumAttendeePercentage: 1, 
                        IsOrganizerOptional: false, 
                        ActivityDomain: "Work"
                    }
                ).MeetingTimeSuggestions,
                "StartTime", MeetingTimeSlot.Start.DateTime, 
                "EndTime", MeetingTimeSlot.End.DateTime
            )
        )
    );
    UpdateContext( { _loadingMeetingTimes: false } );
    Set( _showMeetingTimes, true )
    ```

  高レベルでは、このコントロールを選択すると、利用可能なミーティング時間が更新されます。 ユーザーが日付を変更すれば、その日の出席者の空き状況を反映するために、利用可能なミーティング時間の更新が必要です。

  イニシャルの**収集**ステートメントを除いて、これは **AddIcon** コントロールの **OnSelect** 機能と同じです。 そのため、この議論はそれほど深くありません。 より完全な説明については、[AddIcon コントロール](#add-icon) セクションをお読みください。

  このコントロールを選択すると、**TextSearchBox** がリセットされます。 それから: 
  1. **_loadMeetingTimes** 状態を **true** に、**_showMeetingTimes** 状態を **false** に設定し、**_selectedMeetingTime** と **_selectedRoom** 変数を空白にし、新しい日付を選択して **MeetingTimes** コレクションを更新します。 
  1. **_loadMeetingTimes** 状態を **false** に、**_showMeetingTimes** を **true** に設定します。

## <a name="meeting-duration-drop-down"></a>ミーティング期間ドロップダウン

   ![MeetingDateSelect コントロール](media/meeting-screen/meeting-timepicker.png)

* プロパティ: **DisplayMode**<br>
    値: `If( IsEmpty(MyPeople), DisplayMode.Disabled, DisplayMode.Edit )`

    少なくとも 1 人の出席者が **MyPeople** コレクションに追加されるまで、ミーティングの期間を選択することはできません。

* プロパティ: **OnChange**<br>
    値: `Select(MeetingDateSelect1)`

    選択した期間を変更すると、実行する **MeetingDateSelect** コントロールの **OnSelect** プロパティにあるコードがトリガーとなります。

## <a name="find-meeting-times-gallery"></a>ミーティング時間ギャラリーを見つける

   ![FindMeetingTimesGallery コントロール](media/meeting-screen/meeting-time-gall.png)

* プロパティ: **Items**<br>
    値: `MeetingTimes`

    潜在的なミーティング時間のコレクションは、[Office365.FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times) 操作から取得します。

* プロパティ: **Visible**<br>
    値: `_showMeetingTimes && _showDetails && !IsEmpty( MyPeople )`

    ギャラリーは、**_showMeetingTimes** が **true** に設定され、**LblScheduleTab** コントロールを選択し、少なくとも 1 人の出席者がミーティングに追加されている場合にのみ、表示されます。

### <a name="find-meeting-times-gallery-title"></a>ミーティング時間ギャラリー タイトルを見つける

   ![FindMeetingTimesGallery Title コントロール](media/meeting-screen/meeting-time-gall-title.png)

* プロパティ: **Text**<br>
    値: ユーザーのローカル時間で表示される開始時間の変換:

    ```powerapps-dot
    Text(
        DateAdd(
            DateTimeValue( ThisItem.StartTime ),
            - TimeZoneOffset(), 
            Minutes
        ),
        DateTimeFormat.ShortTime
    )
    ```

  **StartTime** の取得された値は、UTC 形式です。 [ UTC から現地時間に変換する](../functions/function-dateadd-datediff.md#converting-from-utc) には、**DateAdd** 関数が適用されます。
  [テキスト機能](../functions/function-text.md#datetime) は、最初の引数として日付/時刻を受け取り、2 番目の引数に基づいてフォーマットします。 **ThisItem.StartTime** の現地時間変換にパスし、**DateTimeFormat.ShortTime** として表示します。

* プロパティ: **OnSelect**<br>
    値: 複数の**収集**ステートメントでミーティング室とその提案された空室状況の収集だけでなく、いくつかの可変トグルと同様に:

    ```powerapps-dot
    Set( _selectedMeetingTime, ThisItem );
    UpdateContext( { _loadingRooms: true } );
    If( IsEmpty( RoomsLists ),
        ClearCollect( RoomsLists, 'Office365'.GetRoomLists().value) );
    If( CountRows( RoomsLists ) <= 1,
        Set( _noRoomLists, true );
        ClearCollect( AllRooms, 'Office365'.GetRooms().value );
        Set( _allRoomsConcat, Concat( FirstN( AllRooms, 20 ), Address & ";" ) );
        ClearCollect( RoomTimeSuggestions, 
            'Office365'.FindMeetingTimes(
                {
                    RequiredAttendees: _allRoomsConcat, 
                    MeetingDuration: MeetingDurationSelect.Selected.Minutes,
                    Start: _selectedMeetingTime.StartTime & "Z", 
                    End: _selectedMeetingTime.EndTime & "Z", 
                    MinimumAttendeePercentage: "1",
                    IsOrganizerOptional: "false", 
                    ActivityDomain: "Unrestricted"
                }
            ).MeetingTimeSuggestions
        );
        ClearCollect( AvailableRooms, 
            AddColumns(
                AddColumns(
                    Filter( 
                        First( RoomTimeSuggestions ).AttendeeAvailability,
                        Availability="Free"
                    ), 
                    "Address", Attendee.EmailAddress.Address
                ), 
                "Name", LookUp( AllRooms, Address = Attendee.EmailAddress.Address ).Name 
            )
        );
        ClearCollect( AvailableRoomsOptimal, 
            DropColumns(
                DropColumns( AvailableRooms, "Availability" ), 
                "Attendee" 
            )
        ),
        Set( _roomListSelected, false) 
    );
    UpdateContext( {_loadingRooms: false} )
    ```

  高レベルでは、このコード ブロックは会議のために選択された日時に基づいて、部屋リストを持たないユーザーが利用できるミーティング室を収集します。 それ以外の場合は、単に部屋のリストを取得します。

  低レベルで、このコードはブロックします:
  1. **_selectedMeetingTime** を選択した項目に設定します。 これは、その期間中に利用可能な部屋を見つけるために使用されます。
  1. 読み込み状態変数 **_loadingRooms** を **true** に設定し、読み込み状態をオンにします。
  1. **RoomsLists** コレクションが空の場合、ユーザーのテナントの部屋リストを取得して、**RoomsLists** コレクションに保存します。
  1. ユーザーに部屋リストがない場合、または部屋リストが 1 つある場合:
      1. **noRoomLists** 変数が **true** に設定されると、変数は **RoomBrowseGallery** コントロールに表示されている項目を決定するために使用されます。
      1. `Office365.GetRooms()` 操作は、テナントの最初の 100 部屋を取得するために使用されます。 これらは **AllRooms** コレクションに保存されます。
      1. **_allRoomsConcat** 変数は、**AllRooms** コレクションの部屋の最初の 20 件のメール アドレスの文字列に設定されます。 これは、[Office365.FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times) が 1 回の操作で 20 人のオブジェクトの利用可能な時間を検索することに制限されています。
      1. **RoomTimeSuggestions** コレクションは、[Office365.FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times) を使い、**_selectedMeetingTime** 変数からの時間値に基づいて、**AllRooms** コレクションの最初の 20 部屋の空室状況を取得します。 `& "Z"` は、**DateTime** 値を適切にフォーマットするために使用されます。
      1. **AvailableRooms** が作成されます。 これは単に 2 つの列が追加された出席者の空き状況の **RoomTimeSuggestions** コレクション: 「住所」と「名前」です。 「アドレス」は部屋のメールアドレス、「名前」は部屋の名前です。
      1. そして、**AvailableRoomsOptimal** コレクションが作成されます。 これは「Availability」および「Attendee」列が削除された **AvailableRooms** コレクションです。 これを行うと、**AvailableRoomsOptimal** および **AllRooms** のスキーマに一致します。 これにより、**RoomBrowseGallery** の **Items** プロパティ内で両コレクションを使用できます。
      1. **_roomListSelected** が **false** に設定されます。
  1. 読み込み状態の **_loadingRooms** は他のすべてが実行を終了すると、**false** に設定されます。

## <a name="room-browse-gallery"></a>部屋の観覧ギャラリー

   ![RoomBrowseGallery コントロール](media/meeting-screen/meeting-rooms-gall.png)

* プロパティ: **Items**<br>
    値: ユーザーが部屋リストを選択したか、テナントに部屋リストがあるかによって、論理的には同じスキーマの 2 つの内部コレクションに設定されます。

    ```powerapps-dot
    Search(
        If( _roomListSelected || _noRoomLists, AvailableRoomsOptimal, RoomsLists ),
        Trim(TextMeetingLocation1.Text), 
        "Name", 
        "Address"
    )
    ```

  このギャラリーでは、**_roomListSelected** または **_noRoomLists** が **true** の場合、**AvailableRoomsOptimal** コレクションが表示されます。 それ以外の場合は、**RoomsLists** コレクションが表示されます。 これらのコレクションのスキーマが同一であるため、これを行うことができます。

* プロパティ: **Visible**<br>
    値: ```_showDetails && !IsBlank( _selectedMeetingTime ) && !_loadingRooms```

    ギャラリーは、前の 3 つのステートメントが次のように評価された場合にのみ、**true** と表示されます。

### <a name="roombrowsegallery-title"></a>RoomBrowseGallery Title

   ![RoomBrowseGallery Title コントロール](media/meeting-screen/meeting-rooms-gall-title.png)

* プロパティ: **OnSelect**<br>
    値: 論理的にバインドされた**収集**と**設定**ステートメントのセットは、ユーザーが部屋リストや部屋を表示しているかによって、トリガーされる場合とトリガーされない場合があります。

    ```powerapps-dot
    UpdateContext( { _loadingRooms: true } );
    If( !_roomListSelected && !noRoomLists,
        Set( _roomListSelected, true );
        Set( _selectedRoomList, ThisItem.Name );
        ClearCollect( AllRooms, 'Office365'.GetRoomsInRoomList( ThisItem.Address ).value );
        Set( _allRoomsConcat, Concat( FirstN( AllRooms, 20 ), Address & ";" ) );
        ClearCollect( RoomTimeSuggestions, 
            'Office365'.FindMeetingTimes(
                {
                    RequiredAttendees: _allRoomsConcat, 
                    MeetingDuration: MeetingDurationSelect.Selected.Minutes,
                        Start: _selectedMeetingTime.StartTime & "Z", 
                    End: _selectedMeetingTime.EndTime & "Z", 
                    MinimumAttendeePercentage: "1",
                    IsOrganizerOptional: "false", 
                    ActivityDomain: "Unrestricted"
                }
            ).MeetingTimeSuggestions
        );
        ClearCollect( AvailableRooms, 
            AddColumns(
                AddColumns(
                    Filter(
                        First( RoomTimeSuggestions ).AttendeeAvailability, 
                        Availability = "Free"
                    ),
                    "Address", Attendee.EmailAddress.Address 
                ), 
                "Name", LookUp( AllRooms, Address = Attendee.EmailAddress.Address ).Name
            )
        );
        ClearCollect( AvailableRoomsOptimal, 
            DropColumns(
                DropColumns( AvailableRooms, "Availability" )
            ), 
            "Attendee" )
        ),
        Set( _selectedRoom, ThisItem )
    );
    UpdateContext( {_loadingRooms: false} )
    ```

  このコントロールを選択したときに発生するアクションは、ユーザーが現在一連の部屋リストや部屋を表示しているかによって異なります。 前者の場合、このコントロールを選択すると、選択した部屋リストから、選択した時間に利用可能な部屋が取得されます。 後者の場合、このコントロールを選択すると、**_selectedRoom** 変数が選択した項目に変更します。 上記のステートメントは、[**FindMeetingTimesGallery Title**](#find-meeting-times-gallery) に**選択**ステートメントに非常に似ています。

  低レベルで、前のコードはブロックします:
  1. **_loadingRooms** を **true** に設定して、部屋の読み込み状態をオンにします。
  1. 部屋リストが選択されているかどうか、およびテナントに部屋リストがあるかどうかを確認します。 その場合:
      1. **_roomListSelected** を **true** に、**_selectedRoomList** を選択した項目に設定します。
      1. **_allRoomsConcat** 変数は、**AllRooms** コレクションの部屋の最初の 20 件のメール アドレスの文字列に設定されます。 これは、[Office365.FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times) 操作が 1 回の操作で 20 人のオブジェクトの利用可能な時間を検索することに制限されています。
      1. **RoomTimeSuggestions** コレクションは、[Office365.FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times) 操作を使い、**_selectedMeetingTime** 変数からの時間値に基づいて、**AllRooms** コレクションの最初の 20 部屋の空室状況を取得します。 その `& "Z"` は、**DateTime** 値を適切にフォーマットするために使用されます。
      1. **AvailableRooms** が作成されます。 これは単に 2 つの列が追加された出席者の空き状況の **RoomTimeSuggestions** コレクション: 「住所」と「名前」です。 「アドレス」は部屋のメールアドレス、「名前」は部屋の名前です。
      1. そして、**AvailableRoomsOptimal** コレクションが作成されます。 これは「Availability」および「Attendee」列が削除された **AvailableRooms** コレクションです。 これを行うと、**AvailableRoomsOptimal** および **AllRooms** のスキーマに一致します。 これにより、**RoomBrowseGallery** の **Items** プロパティ内で両コレクションを使用できます。
      1. **_roomListSelected** が **false** に設定されます。
  1. 読み込み状態の **_loadingRooms** は他のすべてが実行を終了すると、**false** に設定されます。

## <a name="back-chevron"></a>バック シェブロン

   ![RoomsBackNav コントロール](media/meeting-screen/meeting-back.png)

* プロパティ: **Visible**<br>
    値: `_roomListSelected && _showDetails`

    このコントロールは、両方の部屋リストが選択されている場合にのみ表示され、**スケジュール**タブが選択されます。

* プロパティ: **OnSelect**<br>
    値: `Set( _roomListSelected, false )`

    **_roomListSelected** に **false** と設定されているときは、**RoomBrowseGallery** コントロールを変更し、**RoomsLists** コレクションからの項目を表示します。

## <a name="send-icon"></a>アイコンを送信

   ![IconSendItem コントロール](media/meeting-screen/meeting-send-icon.png)

* プロパティ: **DisplayMode**<br>
    値: アイコンが編集可能になる前に、ユーザーに特定のミーティング詳細を入力させるロジック。
    
    ```powerapps-dot
    If( Len( Trim( TextMeetingSubject1.Text ) ) > 0
        && !IsEmpty( MyPeople ) && !IsBlank( _selectedMeetingTime ),
        DisplayMode.Edit, DisplayMode.Disabled
    )
    ```
  アイコンは、ミーティングの件名が入力されていて、ミーティングに少なくとも 1 人の出席者がいて、ミーティングの時間が選択されている場合にのみ選択できます。 それ以外の場合は、無効になります。

* プロパティ: **OnSelect**<br>

    値: 選択した出席者にミーティング招集を送信し、すべての入力フィールドをクリアするコード:

    ```powerapps-dot
    Set( _myCalendarName, LookUp( 'Office365'.CalendarGetTables().value, DisplayName = "Calendar" ).Name );
    Set( _myScheduledMeeting, 
        'Office365'.V2CalendarPostItem( _myCalendarName,
            TextMeetingSubject1.Text, 
            Text(DateAdd(DateTimeValue( _selectedMeetingTime.StartTime), -TimeZoneOffset(), Minutes) ),
            Text(DateAdd(DateTimeValue( _selectedMeetingTime.EndTime), -TimeZoneOffset(), Minutes) ),
            {
                RequiredAttendees: Concat( MyPeople, UserPrincipalName & ";" ) & _selectedRoom.Address, 
                Body: TextMeetingMessage1.Text, 
                Location: _selectedRoom.Name, 
                Importance: "Normal", 
                ShowAs: "Busy", 
                ResponseRequested: true
            }
        )
    );
    Concurrent(
        Reset( TextMeetingLocation1 ),
        Reset( TextMeetingSubject1 ),
        Reset( TextMeetingMessage1 ),
        Clear( MyPeople ),
        Set( _selectedMeetingTime, Blank() ),
        Set( _selectedRoomList, Blank() ),
        Set( _selectedRoom, Blank() ),
        Set( _roomListSelected, false )
    )
    ```
  
  低レベルで、このコードはブロックします:
  1. **_myCalendarName** を「カレンダー」の **DisplayName** を使い、[Office365.CalendarGetTables()](https://docs.microsoft.com/connectors/office365/#get-calendars) 操作のカレンダーに設定
  1. ユーザーは [Office365.V2CalendarPostItem](https://docs.microsoft.com/connectors/office365/#create-event--v2-) 操作を使用してスクリーン全体を作成したさまざまな選択から、すべての入力値を使用してミーティングをスケジュールします。
  1. ミーティングの作成に使用されるすべての入力フィールドと変数をリセットします。

> [!NOTE]
> 領域によっては、必要なカレンダーに「カレンダー」の表示名がない場合がある Outlook に移動して、カレンダーのタイトルを確認し、アプリに適切な変更を加えます。

## <a name="next-steps"></a>次の手順

* [このスクリーンに関する詳細情報](./meeting-screen-overview.md)
* [Power Apps での Office 365 Outlook コネクタについての詳細](../connections/connection-office365-outlook.md)
* [Power Apps での Office 365 ユーザー コネクタについての詳細](../connections/connection-office365-users.md)
