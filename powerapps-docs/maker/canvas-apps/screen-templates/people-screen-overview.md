---
title: 人物画面のテンプレート | Microsoft Docs
description: キャンバス アプリの人物画面テンプレートの仕組みを理解し、独自の使用に合わせて画面を拡張する方法
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/30/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b530fe0623c72f9df1adda1067638a3d1a1099f1
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3306729"
---
# <a name="overview-of-the-people-screen-template-for-canvas-apps"></a>キャンバス アプリの人物画面テンプレートの概要

キャンバス アプリで、ユーザーが組織内で人物を検索できる人物画面を追加します。 ユーザーは人物の検索、選択、およびコレクションへの追加ができます。 検索結果ギャラリーに表示するデータの種類を変更したり、人物の選択を使用して電子メールを送信したり、その他のカスタマイズを行ったりすることができます。

[メール](email-screen-overview.md)、ユーザーの [カレンダー](calendar-screen-overview.md)、およびユーザーが会議に招待するユーザーの [使用可能性](meeting-screen-overview.md)などの、Office 365 とは異なるデータを表示する他のテンプレート ベースのスクリーンを追加することもできます。

この概要では次のことについて説明します。
> [!div class="checklist"]
> * 既定の人物画面の使用方法。
> * 画面を変更する方法。
> * 画面をアプリに統合する方法。

このスクリーンの既定の機能についてさらに詳しく知りたい場合は、[人物画面のリファレンス](people-screen-reference.md) を参照してください。

## <a name="prerequisite"></a>前提条件

[Power Apps でアプリを作成する](../data-platform-create-app-scratch.md) ときに、画面およびその他のコントロールの追加および構成を行う方法に関する知識。

## <a name="default-functionality"></a>既定機能

テンプレートから人物画面を追加する。

1. Power Apps に[サインインし](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)、アプリを作成するか、または Power Apps Studio で既存のアプリを開きます。

    このトピックでは電話アプリについて説明しますが、同じ概念がタブレット PC アプリにも適用されます。

1. リボンの**ホーム** タブで、**新しいスクリーン** > **人物**を選択します。

    既定では、スクリーンは次のようになります。

    ![最初の人物画面の状態](media/people-screen/people-screen-empty.png)

1. ユーザーの検索を開始するには、上部にあるテキスト入力ボックスを選択し、他のユーザーの名前を入力します。 検索結果はテキスト入力ボックスの下に表示されます。

    ![人物画面検索の状態](media/people-screen/people-browse-gall-full.png)

1. 検索結果から個人を選択すると、**MyPeople** コレクションに追加されます。 検索バーの入力値がリセットされ、選択した人物のコレクションが公開されます。

    ![人物画面の収集結果](media/people-screen/people-people-gall-full.png)

## <a name="modify-the-screen"></a>スクリーンを変更する

[ユーザーに異なるデータを表示する](people-screen-overview.md#show-different-data-for-people) から、この画面の既定の機能を変更することができます。

スクリーンをさらに変更する場合は、[人物画面のリファレンス](./people-screen-reference.md) をガイドとして使用してください。

### <a name="show-different-data-for-people"></a>ユーザーに異なるデータを表示する

この画面では、[Office365Users.SearchUser](https://docs.microsoft.com/connectors/office365users/#searchuser) の操作を使用して、組織内のユーザーを検索します。**UserBrowseGallery** コントロールに表示されるものを超えて、各イベントの追加フィールドを提供します。 ギャラリーでのフィールドの追加または変更は、簡単なプロセスです。

1. **UserBrowseGallery** で、変更するラベルを選択します (もしくはラベルを追加して選択したままにします)。

1. その **Text** プロパティを選択し、数式バーで内容を `ThisItem.` に置き換えます

    IntelliSense には、選択できるフィールドの一覧を表示します。

1. 使用するフィールドを選択します。

    **Text** プロパティは `ThisItem.{FieldSelection}` に更新する必要があります。

## <a name="integrate-the-screen-into-an-app"></a>スクリーンをアプリに統合する

人物画面は、それ自体が強力なコントロールのバンドルですが、通常は、より大きくより多目的なアプリの一部として最適に実行します。 この画面は、[キャッシュされた人物の一覧を使用する](people-screen-overview.md#use-your-cached-list-of-people) などさまざまな方法で、より大きなアプリに統合することができます。

### <a name="use-your-cached-list-of-people"></a>キャッシュされた人物の一覧を使用する

人物画面は、**MyPeople** コレクションで選択した人物をキャッシュします。 ビジネス シナリオが人物検索を呼び出す場合、このコレクションの使用方法を知っておく必要があります。 ここでは、この画面を基本的な電子メール画面に接続し、**MyPeople** コレクション内のユーザーに電子メールを送信する方法について説明します。 また、[電子メール画面](./email-screen-overview.md) が動作する方法について洞察することができます。

1. **ビュー** タブを選択することにより Office 365 Outlook データ ソースをアプリに追加し、**データ ソース** > **データ ソースの追加**を選択して、Office 365 Outlook コネクタを検索します。 検索するために、**新しい接続**を選択する必要があるかもしれません。
1. 人物画面を挿入した後、新しい空白の画面を挿入します。 その画面内に、後ろ向きの矢印アイコン、2 つのテキスト入力ボックス、および送信アイコンを追加します。
1. 画面は **EmailScreen** に、戻る矢印アイコンは **BackIcon** に、1 つのテキスト入力ボックスは **SubjectLine** に、その他は **MessageBody** に、送信アイコンは **SendIcon** に、それぞれ名前を変更します。
1. **BackIcon** の **OnSelect** プロパティを `Back()` に設定します。
1. **SendIcon** の **OnSelect** プロパティを次の数式に設定します。

    ```powerapps-dot
    Office365.SendEmail( 
        Concat( MyPeople, UserPrincipalName & ";" ), 
        SubjectLine.Text, 
        MessageBody.Text 
    )
    ```
    
    ここでは、Outlook コネクタを使用して電子メールを送信しています。 `Concat(MyPeople, UserPrincipalName & ";")` を受信者の一覧として渡します。 この数式は、**MyPeople** コレクション内のすべての電子メールアドレスを、セミコロンで区切られた単一の文字列に連結します。 これは、お気に入りの電子メールクライアントの「To」行にセミコロンで区切られた電子メール アドレスの文字列を書き出すのと違いはありません。
    * `SubjectLine.Text` をメッセージの件名として、`MessageBody.Text` をメッセージの本文として渡しています。
1. 人物画面の右上隅に、**電子メール** アイコンを挿入します。
   アイコンの色をユーザーに合ったものに変更します。
1. **SendIcon** の **OnSelect** プロパティを `Navigate( EmailScreen, None )` に設定します。

    これで、ユーザーの選択、電子メール メッセージの作成、および送信を行うことができる 2 つの画面のアプリができました。 ご自由にテストすることができますが、アプリは **MyPeople** コレクションに追加した全員に電子メールを送信するため、注意する必要があります。

## <a name="next-steps"></a>次の手順

* [スクリーンの参照ドキュメントを表示します](./people-screen-reference.md)。
* [Office 365 Outlook コネクタについての詳細](../connections/connection-office365-outlook.md)。
* [Office 365 ユーザー コネクタについての詳細](../connections/connection-office365-users.md)。
