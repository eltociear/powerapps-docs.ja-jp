---
title: キャンバス アプリの電子メール画面テンプレートの参照 | Microsoft Docs
description: Power Apps でのキャンバス アプリの電子メール画面テンプレートの仕組みの詳細を理解する
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/31/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f173b4898df8853ef31d1660af6efe9298f838b0
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3307281"
---
# <a name="reference-information-about-the-email-screen-template-for-canvas-apps"></a>キャンバス アプリの電子メール画面テンプレートに関する参照情報

Power Apps でのキャンバス アプリの場合、電子メール画面テンプレートの重要な各コントロールがスクリーン全体の既定機能にどのように貢献するかを理解します。 この詳細は、動作の数式およびコントロールがユーザー入力にどのように応答するかを決定する他のプロパティの値を表示します。 このスクリーン既定機能の概要については、[電子メール画面の概要](email-screen-overview.md)を参照してください。

このトピックは、一部の重要なコントロールに注目し、それらのコントロールのさまざまなプロパティ (**Items** および **OnSelect** など) に設定する式または数式ついて説明しています。

* [テキスト検索ボックス](#text-search-box)
* [追加アイコン](#add-icon)
* [ユーザー参照ギャラリー](#people-browse-gallery)
* [電子メール ユーザー ギャラリー](#email-people-gallery) (+ 子コントロール)
* [メール アイコン](#mail-icon)

## <a name="prerequisite"></a>前提条件

[Power Apps でアプリを作成する](../data-platform-create-app-scratch.md) ときに、画面およびその他のコントロールの追加および構成を行う方法に関する知識。

## <a name="text-search-box"></a>テキスト検索ボックス

   ![TextSearchBox コントロール](media/email-screen/email-search-box.png)

画面の他のいくつかのコントロールは、**テキスト検索ボックス** コントロールで依存関係があります。

* ユーザーがテキストの入力を開始すると、**PeopleBrowseGallery** が表示されます。
* ユーザーが有効な電子メール アドレスを入力すると、**AddIcon** が表示されます。
* ユーザーが **PeopleBrowseGallery** 内のユーザーを選択すると、検索内容はリセットされます。

## <a name="add-icon"></a>追加アイコン

   ![AddIcon コントロール](media/email-screen/email-add-icon.png)

**追加アイコン** コントロールを使用すると、アプリ ユーザーは組織内に存在しないユーザーを作成中の受信者リストに追加できます。

* プロパティ: **Visible**<br>
    値: ユーザーが有効な電子メール アドレスを検索ボックスに入力したときにのみコントロールを表示するロジック。

    ```powerapps-dot
    !IsBlank( TextSearchBox.Text ) &&
        IsMatch( TextSearchBox.Text, Match.Email ) &&
        Not( Trim( TextSearchBox.Text ) in MyPeople.UserPrincipalName )
    ```
  行ごとに、前述のコード ブロックは、**追加アイコン** コントロールは以下の場合にのみ表示されると示しています。

    * **TextSearchBox** にテキストが含まれています。
    * **TextSearchBox** のテキストは、有効なメール アドレスです。
    * **TextSearchBox** のテキストは、**MyPeople** コレクションにまだ存在していません。

* プロパティ: **OnSelect**<br>
    値: これを選択すると、有効な電子メール アドレスが **MyPeople** コレクションに追加されます。 このコレクションは、画面で受信者リストとして使用されます。

    ```powerapps-dot
    Collect( MyPeople,
        { 
            DisplayName: TextSearchBox.Text, 
            UserPrincipalName: TextSearchBox.Text, 
            Mail: TextSearchBox.Text
        }
    );
    Reset( TextSearchBox )
    ```
  
  このコード ブロックは、行を **MyPeople** コレクションに追加し、3 つのフィールドに **TextSearchBox** のテキストを入力します。 これらの 3 つのフィールドは、**DisplayName**、**UserPrincipalName**、および **Mail** です。 次に、**TextSearchBox** の内容をリセットします。

## <a name="people-browse-gallery"></a>ユーザー参照ギャラリー

   ![PeopleBrowseGallery コントロール](media/email-screen/email-browse-gall.png)

* プロパティ: **Items**<br>
    値: **TextSearchBox** コントロールに入力された検索テキストの上位 15 件の検索結果。
    
    ```powerapps-dot
    If( !IsBlank( Trim(TextSearchBox.Text ) ), 
        'Office365Users'.SearchUser( {searchTerm: Trim( TextSearchBox.Text ), top: 15} )
    )
    ```

  このギャラリーのアイテムは、[Office365.SearchUser](https://docs.microsoft.com/connectors/office365users/#searchuser) 操作からの検索結果により設定されます。 操作は、検索語句として `Trim(TextSearchBox)` のテキストを受け取り、その検索に基づいて上位 15 件の結果を戻します。
  
  **TextSearchBox** は、スペースでのユーザー検索が無効であるため、`Trim()` 関数に囲われています。 `Office365Users.SearchUser` の操作は、`If(!IsBlank(Trim(TextSearchBox.Text)) ... )` 関数でラップされています。つまり、検索ボックスにユーザーが入力したテキストが含まれている場合のみ操作が実行されます。 これにより、パフォーマンスが向上します。 

### <a name="people-browse-gallery-title-control"></a>ユーザー参照ギャラリー タイトル コントロール

   ![PeopleBrowseGallery Title コントロール](media/email-screen/email-browse-gall-title.png)

* プロパティ: **Text**<br>
    値: `ThisItem.DisplayName`

  ユーザーの表示名を Office 365 プロフィールから表示します。

* プロパティ: **OnSelect**<br>
    値: ユーザーをアプリ レベルのコレクションに追加し、ユーザーを選択するコード。

    ```powerapps-dot
    Concurrent(
        Set( _selectedUser, ThisItem ),
        Reset( TextSearchBox ),
        If( Not( ThisItem.UserPrincipalName in MyPeople.UserPrincipalName ), 
            Collect( MyPeople, ThisItem )
        )
    )
    ```
このコントロールの選択により、3 つのことが同時に実行されます。

   * **_selectedUser** 変数を、選択した項目に設定します。
   * **TextSearchBox** の検索語句をリセットします。
   * **MyPeople** コレクションに選択した項目を追加します。これは、電子メール画面が受信者のセットとして使用する、選択したすべてのユーザーのコレクションです。

## <a name="email-people-gallery"></a>電子メール ユーザー ギャラリー

   ![EmailPeopleGallery コントロール](media/email-screen/email-people-gall.png)

* プロパティ: **Items**<br>
    値: `MyPeople`

  これは、**PeopleBrowseGallery タイトル** コントロールを選択して、初期化または追加されたユーザーのコレクションです。

* プロパティ: **Height**<br>
    値: 現在ギャラリーにあるアイテムの数に基づいて高さを設定するロジック。

    ```powerapps-dot
    Min( 
        ( EmailPeopleGallery.TemplateHeight + EmailPeopleGallery.TemplatePadding * 2) *
            RoundUp(CountRows(EmailPeopleGallery.AllItems) / 2, 0 ),
        304
    )
    ```

  このギャラリーの高さは、ギャラリー内のアイテムの数に合わせて調整されます。最大の高さは 304 です。
  
  **EmailPeopleGallery** の単一行の高さの合計として `TemplateHeight + TemplatePadding * 2` を取り、それを行数で乗算します。 `WrapCount = 2` なので、真の行の数は `RoundUp(CountRows(EmailPeopleGallery.AllItems) / 2, 0)` です。

* プロパティ: **ShowScrollbar**<br>
    値: `EmailPeopleGallery.Height >= 304`
  
  ギャラリーの高さが 304 に達すると、スクロール バーが表示されます。

### <a name="email-people-gallery-title-control"></a>電子メール ユーザー ギャラリー タイトル コントロール

   ![EmailPeopleGallery タイトル コントロール](media/email-screen/email-people-gall-text.png)

* プロパティ: **OnSelect**<br>
    値: `Set(_selectedUser, ThisItem)`

  **_selectedUser** 変数を、**EmailPeopleGallery** で選択した項目に設定します。

### <a name="email-people-gallery-iconremove-control"></a>電子メール ユーザー ギャラリー iconRemove コントロール

   ![MonthDayGallery タイトル コントロール](media/email-screen/email-people-gall-delete.png)

* プロパティ: **OnSelect**<br>
    値: `Remove( MyPeople, LookUp( MyPeople, UserPrincipalName = ThisItem.UserPrincipalName ) )`

  **MyPeople** コレクションのレコードを検索します。ここで、**UserPrincipalName** は 選択したアイテムの **UserPrincipalName** と一致し、そのレコードをコレクションから削除します。

## <a name="mail-icon"></a>メール アイコン

* プロパティ: **OnSelect**<br>
    値: ユーザーの電子メール メッセージを送信するロジック。

    ```powerapps-dot
    Set( _emailRecipientString, Concat( MyPeople, Mail & ";" ) );
    'Office365'.SendEmail( _emailRecipientString, 
        TextEmailSubject.Text,  
        TextEmailMessage.Text, 
        { Importance:"Normal" }
    );
    Reset( TextEmailSubject );
    Reset( TextEmailMessage );
    Clear( MyPeople )
    ```

  電子メール メッセージを送信するには、セミコロンで区切られた電子メール アドレスの文字列が必要です。 上記のコードにより、次のことが行われます。
  1. コードの最初の行は、**MyPeople** コレクションのすべての行から**メール** フィールドを取得し、それらをセミコロンで区切られた単一の電子メール アドレス文字列に連結し、**_emailRecipientString** 変数をその文字列に設定します。

  1. 次に、[Office365.SendEmail](https://docs.microsoft.com/connectors/office365/#sendemail) 操作を使用して、受信者に電子メールを送信します。
    操作には 3 つの必須パラメーターがあります。**宛先**、**件名**、**本文**、および 1 つのオプション パラメーター -- **重要性**です。 上記のコードでは、これらはそれぞれ **_emailRecipientString**、**TextEmailSubject**.Text、**TextEmailMessage**.Text、および**標準**です。
  1. 最後に、**TextEmailSubject** および **TextEmailMessage** コントロールをリセットし、**MyPeople** コレクションをクリアします。

* プロパティ: **DisplayMode**<br>
    値: `If( Len( Trim( TextEmailSubject.Text ) ) > 0 && !IsEmpty( MyPeople ), DisplayMode.Edit, DisplayMode.Disabled )` メールを送信するには、メールの件名にテキストを含める必要があり、受信者 (**MyPeople**) コレクションを空にすることはできません。

## <a name="next-steps"></a>次の手順

* [このスクリーンに関する詳細情報](./email-screen-overview.md)
* [Power Apps での Office 365 Outlook コネクタについての詳細](../connections/connection-office365-outlook.md)
* [Power Apps での Office 365 ユーザー コネクタについての詳細](../connections/connection-office365-users.md)
