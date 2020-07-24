---
title: プッシュ通知を送信する | Microsoft Docs
description: Power Apps でネイティブ プッシュ通知をアプリに送信する方法を説明します。
author: kavishi
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/21/2020
ms.author: kaagar
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 76f74a9d52f0a3957bda37b825eb8be849cd97ef
ms.sourcegitcommit: 4b6f187c9501332f9acca5978fa326621f2980e5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/22/2020
ms.locfileid: "3394376"
---
# <a name="send-a-push-notification-in-power-apps"></a>Power Apps でプッシュ通知を送信する
プッシュ通知は、主に、アプリのユーザーの注意を促し、および重要なタスクに優先順位を付けるようにするため、コンシューマおよびビジネス シナリオにおいてモバイル アプリで使用されます。 Power Apps では Power Apps 通知コネクタを使用して通知を送信できます。 Power Apps で作成したアプリに、ネイティブ プッシュ通知を送信できます。 通知の種類は、今後追加される予定です。

![プッシュ通知の外観の例](./media/add-notifications/pic1-notification-screenshot.png)

次のような場合、アプリにプッシュ通知を追加します。

* ユーザーが情報をすぐに知る必要があります。
* 事前に読み込まれたコンテキストで、アプリを使用してユーザーが重要なタスクを完了する必要があります。
* 特定のサイクル間隔でユーザーの注意を促す必要がある、またはユーザーが特定のコンテキストでアプリを起動する必要があります。

> [!NOTE]
> プッシュ通知を受信するには、各ユーザーが Power Apps モバイルでアプリを一度開いているか、または [Dynamics 365](https://home.dynamics.com/) の AppSource からアプリを取得している必要があります。

## <a name="before-you-start"></a>開始する前
**共同作成者**のアクセス許可を持っているアプリで、Power Apps の通知接続を追加します。 まだアプリを持っていない場合は、すぐに[テンプレートから作成](get-started-test-drive.md) して、既定より必要なアクセス許可を取得することができます。 そのチュートリアルとこのチュートリアルでは、ケース管理のテンプレートに基づいたアプリを使用します。

## <a name="send-a-notification-from-a-flow"></a>フローから通知を送信する
> [!NOTE]
> フローからプッシュ通知をトリガーする場合、現在一度に通知を送信できるのは 1 人のユーザーまたはセキュリティ グループだけです。

1. [Power Automate](https://flow.microsoft.com) で、プッシュ通知が送信されるタイミングを指定するトリガーを作成します。

    たとえば、Common Data Service でレコードが**サポート案件**エンティティに追加されるときに通知を送信する場合があります。

    ![Common Data Service トリガーでフローを作成するスクリーンショット](./media/add-notifications/pic4-step1-flowupdated.png)
2. **Power Apps 通知**コネクタを使用してフローのアクションを作成し、通知を送信するアプリの**アプリ ID** を入力します。

    シナリオを反映するため、接続の名前を変更することもできます。

    ![これらのプッシュ通知を受信する Power Apps への接続の作成のスクリーンショット](./media/add-notifications/pic5-step2-create-connection.jpg)
3. (オプション) アプリが開いたときに (ユーザーがプッシュ通知をタップした後)、アプリにパラメーターを渡します。

    この例では、選択した取引先担当者の**サポート案件 ID** および**初期所有者**フィールドを渡します。

    ![プッシュ通知にオプションのパラメーターを渡しているスクリーンショット](./media/add-notifications/pic6-step3-configure-notif.jpg)

## <a name="send-a-notification-from-an-app"></a>アプリから通知を送信する
プッシュ通知を、あるアプリから別の、または同じアプリに送信できます。

1. [Power Apps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) で、プッシュ通知を送信するアプリに移動します。
2. **詳細**タブで、アプリの**アプリ ID** をコピーします。

    ![アプリ ID を取得する](./media/add-notifications/grab-id.png)
3. **接続**タブで、Power Apps 通知コネクタへの接続を作成し、および前の手順からのアプリ ID を貼り付けます。

    ![接続の作成](./media/add-notifications/create-connection.png)
4. トリガー アプリへの接続を追加します。

    この例では、トリガー アプリと同じアプリを使用します。 ケースを再び割り当てるユーザーは、新しいケース所有者へのプッシュ通知もトリガーします。

    ![つながりの追加](./media/add-notifications/add-connection.png)
5. プッシュ通知接続から、**SendPushNotification** メソッドを呼び出します。

    この例では、フォームで **OnSuccess** プロパティを使用してこの通知をトリガーします。

    ![Power Apps 数式](./media/add-notifications/powerapps-function.png)

## <a name="load-a-specific-page-and-context-when-a-user-taps-the-notification"></a>ユーザーが通知をタップしたときに、特定のページおよびコンテキストを読み込む
### <a name="pass-parameters"></a>パラメーターを渡す
プッシュ通知は、アプリに特定のパラメーターを渡すことができます。 たとえば、**サポート案件 ID** の値を読み取るには、*Param("CaseID")* を使用します。 このパラメーターをすばやく識別するには、アプリに**ラベル** コントロールを追加します。 そのコントロールの**テキスト** プロパティを **Param("CaseID")** に設定します。 ユーザーが**すべてのアプリ** リストからアプリを開いた場合、値は空です。 ユーザーがデバイス上で別の場所からアプリを開いた場合、値は **サポート案件 ID** の値に設定されます。

### <a name="set-the-start-page"></a>開始ページを設定する
アプリが開くとすぐに、たとえば、**サポート案件の詳細**ページを開くようにアプリを設定することができます。

1. **タイマー** コントロールを追加し、および、その **OnTimerEnd** プロパティを次の数式に設定します。
   <br>**Navigate(EditCase, ScreenTransition.None)**
2. (オプション) **表示**プロパティを **false** に設定して、**タイマー** コントロールを非表示にします。
3. スクリーンの **OnVisible** プロパティを **Timer.Start()** に設定します。

> [!TIP]
> 通知用のアプリで一意の開始ページを作成することをお勧めします。
> 
> 1. アプリがまだ開いていない空のページを作成し、**テキスト入力**コントロールを追加し、およびその **timer.Duration** の値を設定します。
> 2. アプリを作成する場合は、タイマーをゼロ以外の値に設定します。 アプリを公開する準備ができたら、すぐにタイマーがトリガーされるように、値を **0** に設定します。

## <a name="syntax"></a>構文

| 件名 | 内容 |
| --- | --- |
| SendPushNotification |通知の接続設定で指定されたアプリに、プッシュ通知を送信します。 |

### <a name="parameters"></a>パラメーター

| 件名 | 種類​​ | 内容 |
| --- | --- | --- |
| 受信者 |文字列配列、必須 |以下のリスト: <ul> <li>ユーザーまたはセキュリティ グループのメール アドレス</li> <li>Azure Active Directory のユーザーまたはセキュリティ グループのオブジェクト ID</li></ul> |
| メッセージ |文字列、必須 |プッシュ通知のメッセージの本文。 |
| openApp |ブール値、オプション |ユーザーがプッシュ通知をタップしたときにアプリを開くかどうか。 |
| パラメーター |パラメーター、オプション |通知と渡すキー値のパラメーター。 特定のページを開き、および特定の状態を読み込むため、アプリでさらに処理することができます。 |

### <a name="sample-formulas"></a>サンプルの数式
基本の通知を送信します。

```powerapps-dot
PowerAppsNotification.SendPushNotification(
    {
        recipients: ["f60ccf6f-7579-4f92-967c-2920473c966b", "72f988bf-86f1-41af-91ab-2d7cd011db47"],
        message: "A new case was assigned to you."
    }
)
```

アプリを開き、特定のパラメーターを渡す通知を送信します。

```powerapps-dot
PowerAppsNotification.SendPushNotification(
    {
        recipients: ["email1@contoso.com", "email2@contoso.com"],
        message: "message in the notif toast",
        params: Table({key:"notificationKey", value:"The value for notificationKey"}),
        openApp: true
    }
)
```

## <a name="known-limitations"></a>既知の制限
* 現時点では、通知は Windows Phone の Power Apps モバイルに表示されません。
* 現時点では、Web ブラウザーでのみアプリを実行するユーザーにはプッシュ通知を提供していません。
* 通知は、特定のアプリ アイコンの代わりに汎用の Power Apps アイコンを表示します。
* Power Automate を使用する場合、プッシュ通知を一度に 1 人の受信者にだけ送信することができます。
* プッシュ通知は、モデル駆動型アプリでは現在対応していません。 

参照情報については、[Power Apps 通知の参照](https://docs.microsoft.com/connectors/powerappsnotification/) をご覧ください。

