---
title: 電子メール画面テンプレート | Microsoft Docs
description: キャンバス アプリの電子メール画面テンプレートの仕組みを理解し、独自の使用に合わせて画面を拡張する
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/29/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 861d343e653a78af685a1e0cb82deb5b2ad59591
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3307327"
---
# <a name="overview-of-the-email-screen-template-for-canvas-apps"></a>キャンバス アプリの電子メール画面テンプレートの概要

キャンバス アプリで、ユーザーが Office 365 Outlook アカウントから電子メールを送信できる電子メール画面を追加します。 ユーザーは組織内の受信者を検索し、外部の電子メール アドレスを追加することもできます。 画像添付サポートの追加、検索ギャラリーに表示されるユーザー データの変更、その他のカスタマイズを行うことができます。

ユーザーの[カレンダー](calendar-screen-overview.md)、組織内の[ユーザー](people-screen-overview.md)、およびユーザーが会議に招待するユーザーの[空き状況](meeting-screen-overview.md)などの、Office 365 とは異なるデータを表示する他のテンプレート ベースの画面を追加することもできます。

この概要では次のことについて説明します。
> [!div class="checklist"]
> * 既定の電子メール画面の使用方法。
> * 変更する方法。
> * アプリに統合する方法。

この画面の既定機能の概要については、[電子メール画面の参照](email-screen-reference.md)をご覧ください。

## <a name="prerequisite"></a>前提条件

[Power Apps でアプリを作成する](../data-platform-create-app-scratch.md) ときに、画面およびその他のコントロールの追加および構成を行う方法に関する知識。

## <a name="default-functionality"></a>既定機能

テンプレートから、電子メール画面を追加します。

1. Power Apps に[サインインし](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)、アプリを作成するか、または Power Apps Studio で既存のアプリを開きます。

    このトピックでは電話アプリについて説明しますが、同じ概念がタブレット PC アプリにも適用されます。

1. リボンの**ホーム** タブで、**新しい画面** > **電子メール**を選択します。

    既定では、スクリーンは次のようになります。

    ![電子メール画面](media/email-screen/email-screen-full.png)

いくつかの役に立つ注意事項があります。

* 組織内のユーザーを検索するには、「宛先」の下のテキスト入力ボックスにユーザーの名前を入力します。
* ユーザーを検索すると、上位 15 件の結果のみが返されます。
* 組織外の電子メール受信者の電子メール アドレスを追加するには、完全で有効な電子メール アドレスを入力し、その右側に表示される 「+」 アイコンを選択します。
* 電子メールを送信するためには、少なくとも 1 人を受信者として追加し、件名を入力する必要があります。
* 電子メールを送信すると、件名行とメッセージ本文の内容、および受信者リストがすべて消去されます。

## <a name="modify-the-screen"></a>スクリーンを変更する

このスクリーンの既定機能は、いくつかの一般的な方法で変更できます。

* [画像添付サポートを追加する](email-screen-overview.md#add-image-attachment-support)
* [ユーザーに異なるデータを表示する](email-screen-overview.md#show-different-data-for-people)

画面をさらに変更する場合は、[電子メール画面の参照](./email-screen-reference.md)をガイドとして使用してください。

> [!IMPORTANT]
> 次の手順では、アプリに電子メール画面を 1 つだけ追加したことを前提としています。 複数を追加した場合、コントロール名 (**iconMail1**など) は異なる数値で終わり、それに応じて数式を調整する必要があります。

### <a name="add-image-attachment-support"></a>画像添付サポートを追加する

これにより、ユーザーは添付ファイルとして単一の画像を電子メール送信できます。

1. **挿入**タブで、**メディア**を選択してから、**画像の追加**を選択します。
1. 新しいコントロールの **Y** プロパティを次の式に設定します。

    `TextEmailMessage1.Y + TextEmailMessage1.Height + 20`
    
1. **AddMediaWithImage** コントロールを挿入し、高さを 210 未満に設定します。
1. コントロール ツリー ビューで、**AddMediaWithImage** > **...** > **再発注** > **送り返す**を選択します。
   これにより、コントロールが **PeopleBrowseGallery** コントロールの前に配置されなくなります。
1. **EmailPeopleGallery** の **Height** プロパティをこの式に変更します。

    ```powerapps-dot
    Min( 
        ( EmailPeopleGallery1.TemplateHeight + EmailPeopleGallery1.TemplatePadding * 2 ) *
            RoundUp( CountRows( EmailPeopleGallery1.AllItems ) / 2, 0 ), 
        304
    )
    ```

1. **EmailPeopleGallery** の **ShowScrollbar** プロパティをこの式に設定します。

    ```EmailPeopleGallery1.Height >= 304```
    
    これにより、最大の高さが **AddMediaWithImage** コントロールをページから押し出すのを防ぎます。
    
1. **iconMail** コントロールの **OnSelect** プロパティを次の式に変更します。

    ```powerapps-dot
    Set( _emailRecipientString, Concat(MyPeople, Mail & ";") );
    If( IsBlank( UploadedImage1 ),
        'Office365'.SendEmail( _emailRecipientString, 
            TextEmailSubject1.Text, 
            TextEmailMessage1.Text, 
            { Importance: "Normal" }
        ),
        'Office365'.SendEmail( _emailRecipientString, 
            TextEmailSubject1.Text, 
            TextEmailMessage1.Text, 
            {
                Importance: "Normal",
                Attachments: Table(
                    {
                        Name: "Image.jpg", 
                        ContentBytes: UploadedImage1.Image
                    }
                )
            }
        )
    );
    Reset( TextEmailSubject1 );
    Reset( TextEmailMessage1 );
    Reset( AddMediaButton1 );
    Clear( MyPeople )
    ```
    
    この式は、アップロードされた画像をチェックします。 何もない場合は、以前と同じ `Office365.SendEmail` の操作を使用します。 画像がある場合は、添付ファイル テーブルに添付ファイルとして追加されます。
    電子メールを送信した後、**AddMediaButton** で追加の**リセット**操作が実行され、アップロードされた画像が削除されます。
> [!NOTE]
> 電子メールに複数の添付ファイルを追加するには、添付ファイル テーブルにレコードを追加します。

### <a name="show-different-data-for-people"></a>ユーザーに異なるデータを表示する

この画面では、[Office365Users.SearchUser](https://docs.microsoft.com/connectors/office365users/#searchuser) の操作を使用して、組織内のユーザーを検索します。**PeopleBrowseGallery** コントロールに表示されるものを超えて、各イベントの追加フィールドを提供します。 ギャラリーでのフィールドの追加または変更は簡単です。

1. **PeopleBrowseGallery** コントロールで、変更するラベルを選択します (もしくはラベルを追加して選択したままにします)。

1. その **Text** プロパティを選択し、数式バーで内容を `ThisItem.` に置き換えます

    IntelliSense には、選択できるフィールドの一覧を表示します。

1. 使用するフィールドを選択します。

    **Text** プロパティが `ThisItem.{FieldSelection}` に更新されます。

## <a name="integrate-the-screen-into-an-app"></a>スクリーンをアプリに統合する

電子メール画面は、それ自体が強力なコントロールのバンドルですが、通常は、より大きくより多目的なアプリの一部として最適に動作します。 この画面は、[カレンダー スクリーンへのリンク](email-screen-overview.md#linking-to-the-calendar-screen)などさまざまな方法で、より大きなアプリに統合することができます。

### <a name="linking-to-the-calendar-screen"></a>カレンダー スクリーンへのリンク

[カレンダー スクリーンの概要](./calendar-screen-overview.md#show-event-attendees)の「イベントの参加者を表示する」のセクションで概説されている手順に従いますが、最後の手順で、**Navigate** 関数を設定して電子メール画面を開きます。 これらの手順を完了すると、**MyPeople** コレクションが設定されます。これにより、ユーザーは選択されたイベントに参加しているユーザーに電子メールを送信できます。

> [!NOTE]
> この電子メールを送信すると、Outlook の実際のイベントとは別の電子メールが送信されます。

## <a name="next-steps"></a>次の手順

* [スクリーンの参照ドキュメントを表示します](./email-screen-reference.md)。
* [Power Apps での Office 365 ユーザー コネクタについての詳細](../connections/connection-office365-users.md)。
* [Power Apps のすべての使用可能な接続を表示する](../connections-list.md).