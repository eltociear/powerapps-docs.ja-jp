---
title: 人物画面のテンプレートのリファレンス | Microsoft Docs
description: Power Apps でのキャンバス アプリの人物画面テンプレートに関する仕組みの詳細を理解する
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 1/2/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e4e67b4905003f8134d8f6868671e74fdece3d6b
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3307143"
---
# <a name="reference-information-about-the-people-screen-template-for-canvas-apps"></a>キャンバス アプリの人物画面テンプレートに関する参照情報

Power Apps でのキャンバス アプリの場合、人物画面テンプレートの重要な各コントロールがスクリーン全体の既定機能にどのように貢献するかを理解します。 この詳細は、動作の数式およびコントロールがユーザー入力にどのように応答するかを決定する、他のプロパティの値を表示します。 このスクリーン既定機能の概要については、[人物画面の概要](people-screen-overview.md) を参照してください。

このトピックは、一部の重要なコントロールに注目し、それらのコントロールのさまざまなプロパティ (**Items** および **OnSelect** など) に設定する式または数式ついて説明しています。

* [テキスト検索ボックス](#text-search-box)
* [ユーザー参照ギャラリー](#user-browse-gallery) (+ 子コントロール)
* [追加された人物のギャラリー](#people-added-gallery) (+ 子コントロール)

## <a name="prerequisite"></a>前提条件

[Power Apps でアプリを作成する](../data-platform-create-app-scratch.md) ときに、画面およびその他のコントロールの追加および構成を行う方法に関する知識。

## <a name="text-search-box"></a>テキスト検索ボックス

![TextSearchBox コントロール](media/people-screen/people-search-box.png)

他の 2 つのコントロールは対するか、またはテキスト検索ボックス上で依存関係があります。

* ユーザーがテキストの入力を開始すると、**UserBrowseGallery** が表示されます。
* ユーザーが **UserBrowseGallery** 内のユーザーを選択すると、検索内容はリセットされます。

## <a name="user-browse-gallery"></a>ユーザー参照ギャラリー

![UserBrowseGallery コントロール](media/people-screen/people-browse-gall.png)

* プロパティ: **Items**<br>
    値: ユーザーが入力を開始したときにユーザーを検索するロジック。
    
    ```powerapps-dot
    If( !IsBlank( Trim( TextSearchBox.Text ) ), 
        'Office365Users'.SearchUser(
            {
                searchTerm: Trim( TextSearchBox.Text ), 
                top: 15
            }
        )
    )
    ```
    
このギャラリーのアイテムは、[Office365.SearchUser](https://docs.microsoft.com/connectors/office365users/#searchuser) 操作からの検索結果により設定されます。 操作は、検索語句として `Trim(TextSearchBox)` のテキストを受け取り、その検索に基づいて上位 15 件の結果を戻します。 **TextSearchBox** は、スペースでのユーザー検索が無効であるため、`Trim()` 関数に囲われています。

検索ボックスにユーザーが入力したテキストが含まれている場合に操作を呼び出す必要があるだけなので、`Office365Users.SearchUser` の操作は、`If(!IsBlank(Trim(TextSearchBox.Text)) ... )` 関数でラップされています。 これにより、パフォーマンスが向上します。

### <a name="userbrowsegallery-title-control"></a>UserBrowseGallery Title コントロール

![UserBrowseGallery Title コントロール](media/people-screen/people-browse-gall-title.png)

* プロパティ: **Text**<br>値: `ThisItem.DisplayName`

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

   * **\_selectedUser** 変数を、選択した項目に設定します。
   * **TextSearchBox** の検索語句をリセットします。
   * 選択したアイテムを **MyPeople** コレクションに追加する、アプリ ユーザーが選択したすべてのユーザーのコレクション。

### <a name="userbrowsegallery-profileimage-control"></a>UserBrowseGallery ProfileImage コントロール

![UserBrowseGallery ProfileImage コントロール](media/people-screen/people-browse-gall-image.png)

* プロパティ: **Image**<br>
    値: ユーザーのプロファイル写真を取得するロジック。

    ```powerapps-dot
    If( !IsBlank( ThisItem.Id ) && 
            'Office365Users'.UserPhotoMetadata( ThisItem.Id ).HasPhoto,
        'Office365Users'.UserPhoto( ThisItem.Id )
    )
    ```

**画像**コントロールは、[Office365Users.UserPhoto](https://docs.microsoft.com/connectors/office365users/#get-user-photo--v1-) 操作を使用してユーザーの画像を取得します。 ただし、その前に 2 つのことを確認します。
  
   * ID フィールドが空かそうでないか。 これにより、ギャラリーが検索結果によって設定される前に、**画像**コントロールがユーザーの写真を取得しようとすることを回避します。
   * ユーザーに写真があるかどうか ([Office365Users.UserPhotoMetadata](https://docs.microsoft.com/connectors/office365users/#get-user-photo-metadata) 操作により)。 これにより、ユーザーにプロフィールの画像がない場合に、`Office365Users.UserPhoto` 検索が例外を返すことを回避します。

画像が取得されない場合、**画像**コントロールは空白で、代わりに **iconUser** コントロールが表示されることに注意してください。

## <a name="people-added-gallery"></a>追加されたユーザーのギャラリー

![PeopleAddedGallery コントロール](media/people-screen/people-people-gall.png)

* プロパティ: **Items**<br>
    値: `MyPeople`

これは、**UserBrowseGallery タイトル** コントロールを選択して、初期化または追加されたユーザーのコレクションです。

### <a name="peopleaddedgallery-title-control"></a>PeopleAddedGallery Title コントロール

![PeopleAddedGallery Title コントロール](media/people-screen/people-people-gall-title.png)

* プロパティ: **OnSelect**<br>
    値: `Set( _selectedUser, ThisItem )`

**_selectedUser** 変数を、**EmailPeopleGallery** で選択した項目に設定します。

### <a name="peopleaddedgallery-iconremove-control"></a>PeopleAddedGallery iconRemove コントロール

![PeopleAddedGallery iconRemove コントロール](media/people-screen/people-people-gall-delete.png)

* プロパティ: **OnSelect**<br>
    値: `Remove( MyPeople, LookUp( MyPeople, UserPrincipalName = ThisItem.UserPrincipalName ) )`

**MyPeople** コレクションのレコードを検索します。ここで、**UserPrincipalName** は選択したアイテムの **UserPrincipalName** と一致し、その後、そのレコードをコレクションから削除します。

## <a name="next-steps"></a>次の手順

* [このスクリーンに関する詳細情報](./people-screen-overview.md)。
* [Office 365 Outlook コネクタについての詳細](../connections/connection-office365-outlook.md)。
* [Office 365 ユーザー コネクタについての詳細](../connections/connection-office365-users.md)。
