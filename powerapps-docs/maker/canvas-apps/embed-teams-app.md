---
title: Teams へのアプリの埋め込み | Microsoft Docs
description: Power Appsで作成したアプリを Microsoft Teams に埋め込み、それを共有することができます。
author: matthewbolanos
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/16/2020
ms.author: mabolan
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 088e817c8ef829b340032af577193888079c832a
ms.sourcegitcommit: cf492063eca27fdf73459ff2f9134f2ca04ee766
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/17/2020
ms.locfileid: "3308822"
---
# <a name="embed-an-app-in-teams"></a>Teams へのアプリの埋め込み

作成したアプリは、Microsoft Teams に直接埋め込むことで共有できます。 完了すると、ユーザーは **+** を選択して、アプリを**自分の**チーム チャネルまたは参加しているチームの会話に追加できます。 アプリは、**チームのタブ**の下にタイルとして表示されます。

管理者はアプリをアップロードして、**すべてのタブ セクション**で、テナントの**すべて**のチームに表示されるようにすることができます。 [Microsoft Teams でアプリを共有する](https://docs.microsoft.com/power-platform/admin/embed-app-teams)を参照してください。

> [!NOTE]
> チーム カスタム アプリ ポリシーは、カスタム アプリのアップロードを許可するように設定する必要があります。 アプリを Teams に埋め込むことができない場合は、管理者に問い合わせて[カスタム アプリ設定](https://docs.microsoft.com/MicrosoftTeams/teams-custom-app-policies-and-settings#custom-app-policy-and-settings)がセットアップされているかを確認してください。

## <a name="prerequisites"></a>前提条件

- 有効な [Power Appsライセンス](https://docs.microsoft.com/power-platform/admin/pricing-billing-skus)が必要です。
- アプリを Teams に埋め込むには、[Power Apps を使用して作成された](data-platform-create-app.md)既存のアプリが必要です。

## <a name="download-the-app"></a>アプリをダウンロードする

1. [make.powerapps.com](https://make.powerapps.com) にサインインし、メニューにある**アプリ** を選択します。

    ![アプリ リストの表示](./media/embed-teams-app/file-apps2.png "アプリ リストの表示")

2. Teams で共有するアプリの **その他の操作** (...) を選択し、**Teams に追加**を選択します。

    ![アプリの詳細](./media/embed-teams-app/add-to-teams.png "Teams に追加")

3. Teams に追加のパネルで、**ダウンロード**を選択します。 次に Power Apps は、アプリに既に設定したアプリの説明とロゴを使用して Teams マニフェスト ファイルを生成します。

    ![アプリの詳細](./media/embed-teams-app/download-app.png "アプリをダウンロード")

## <a name="add-the-app-as-a-personal-app"></a>アプリを個人用アプリとして追加する

1. アプリを個人用アプリとして、またはタブとしてチャネルまたは会話に追加するには、左側のナビゲーションで**アプリ**を選択し、**カスタム アプリをアップロード**を選択します。

    > [!NOTE]
    > **カスタム アプリのアップロード**は、Teams 管理者が[カスタム アプリ ポリシー](https://docs.microsoft.com/microsoftteams/teams-app-setup-policies)を作成し、**カスタム アプリのアップロードを許可する**をオンにした場合にのみ表示されます。

    ![アプリをタブとして追加](./media/embed-teams-app/upload-custom-app.png "カスタム アプリのアップロード")

2. **追加**を選択してアプリを個人用アプリとして追加するか、**チームに追加**を選択してアプリを既存のチャネルもしくは会話内のタブとして追加します。

## <a name="publish-the-app-to-the-teams-catalog"></a>アプリを Teams カタログに公開する

管理者であれば、Microsoft Teams カタログに[アプリを公開する](https://docs.microsoft.com/microsoftteams/tenant-apps-catalog-teams)こともできます。

## <a name="use-context-from-teams"></a>Teams のコンテキストを使用する

Teams と緊密に統合されたアプリを構築するには、`Param()` 関数でチームのコンテキスト変数を使用できます。 たとえば、画面の **Fill** プロパティで次の式を使用して、Teams 内のユーザーのテーマに基づいてアプリの背景を変更します。

```
Switch(
        Param("theme"),
        "dark",
        RGBA(
            32,
            31,
            31,
            1
        ),
        "contrast",
        RGBA(
            0,
            0,
            0,
            1
        ),
        RGBA(
            243,
            242,
            241,
            1
        )
    )
```

アプリをテストするには、アプリを公開して、Teams 内で再生します。

Teams の以下のコンテキスト変数がサポートされています。

- ロケール
- channelId
- channelType
- chatId
- groupId
- hostClientType
- subEntityId
- teamId
- teamType
- テーマ
- userTeamRole

> [!NOTE]
> この機能は 2020 年 3 月に追加されました。 これより前にアプリを Teams に埋め込んだ場合、この機能を使用するには、アプリを Teams に再度追加する必要があります。

## <a name="improve-the-performance-of-your-app"></a>アプリのパフォーマンスを向上させる

オプションで、Teams 内にアプリをプリロードして、パフォーマンスを向上させることができます。

1. [make.powerapps.com](https://make.powerapps.com) にサインインし、メニューにある**アプリ** を選択します。

2. Teams で共有するアプリの **その他の操作** (...) を選択し、**設定**を選択します。

3. 設定パネルで、**アプリをプリロードしてパフォーマンスを向上**を**はい**に切り替えます。 その後、アプリはチームに埋め込まれるたびにプリロードされます。

    ![アプリの詳細](./media/embed-teams-app/preload-app.png "アプリをプリロードしてパフォーマンスを向上")

4. 変更を有効にするには、アプリを削除して再度 Teams に追加します。

> [!NOTE]
> これにより、ユーザーは、埋め込みシナリオの認証の進行中に、アプリ ファイルをダウンロードできます。 ただし、ユーザーは認証に成功した後にのみアプリを実行できます。 これにより、認証されていないユーザーはアプリのデータを使用できなくなります。

### <a name="see-also"></a>関連項目

[ようこそMicrosoft Teams](https://docs.microsoft.com/MicrosoftTeams/teams-overview)
