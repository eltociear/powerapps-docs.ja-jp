---
title: キャンバス アプリでフローを開始する | Microsoft Docs
description: ユーザーによるボタンの選択などのイベントがキャンバス アプリで発生した後に 1 つ以上のタスクを実行するフローを作成します。
author: stepsic-microsoft-com
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/07/2018
ms.author: stepsic
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a4e19b4b261bb489dd5c63e4393452a500ab3df9
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3307258"
---
# <a name="start-a-flow-in-a-canvas-app"></a>キャンバス アプリでフローを開始する

Power Automate を使用して、キャンバス アプリ内でイベントが発生したときに 1 つ以上のタスクを実行するロジックを作成できます。 たとえば、ボタンを構成して、ユーザーがそれを選択したら、SharePoint リストの項目の作成、メールや会議出席依頼の送信、クラウドへのファイルの追加といったことを、すべて行うことができます。 フローを開始するようにアプリ内の任意のコントロールを構成でき、フローの実行は Power Apps を閉じた場合も続けられます。

> [!NOTE]
> ユーザーがアプリ内からフローを実行する場合、そのユーザーには、フローで指定されているタスクを実行する権限が必要です。 そうでない場合、フローは失敗します。

## <a name="prerequisites"></a>前提条件

- Power Apps に[サインアップ](../signup-for-powerapps.md)します。
- [コントロールを構成する](add-configure-controls.md) 方法を確認しておきます。

## <a name="create-a-flow"></a>フローの作成

1. [Power Apps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインします。

1. 左側のナビゲーション バーで、**ビジネス ロジック**、**フロー**の順に選択します。

1. **マイ フロー** ページの左上隅で、**新規**、**一から作成**の順に選択します。

    ![テンプレートを使用せずにフローを作成するオプション](./media/using-logic-flows/create-from-blank.png)

1. 表示されるページの下部で、**数百もの接続とトリガーを検索**を選択します。

1. 検索ボックスに **PowerApps** と入力してから、**PowerApps** アイコンを選択します。

    ![Power Apps トリガーを作成する](./media/using-logic-flows/set-trigger.png)
    
1. 次のページで Power Apps アイコンを再度選択し、**新しいステップ**を選択します。

1. **コネクタとアクションを検索する**のボックスで、次の例のようにフローのアクションを指定します。

   1. ボックスに **SharePoint** と入力し、**アクション**下のリストにある**品目の作成**を選択します。

       ![SharePoint 項目を作成するオプション](./media/using-logic-flows/create-sharepoint-item.png)

   1. メッセージが表示されたら、SharePoint に接続するための資格情報を指定します。

   1. **サイトのアドレス** ボックスに、リストを含む SharePoint Online サイトの URL を入力するか貼り付けます。

       > [!NOTE]
       > リストの名前を URL に追加しないでください。

   1. **リスト名**ボックスで、使用するリストを指定します。
   
       ![リストを指定する](./media/using-logic-flows/list-fields.png)

   1. リストのフィールドの入力ボックス (たとえば、**タイトル**) を選択し、動的コンテンツ ウィンドウで**さらに表示**を選択して、**Power Apps で確認する**を選択します。 

       ![タイトル フィールドに Power Apps で確認パラメーターを追加する](./media/using-logic-flows/ask-in-powerapps.png)

1. (オプション) 指定したアドレスに承認のメールを送信したり、別のデータ ソースに関連するエントリを作成するなど、1 つ以上の追加手順を指定します。

1. 左上隅の近くで、フローの名前を入力するか貼り付けて、右上隅の**保存**を選択します。

## <a name="add-a-flow-to-an-app"></a>アプリへのフローの追加
1. 左側のナビゲーション バーで**作成**を選択します。

1. **空白からのキャンバス アプリ** タイルにカーソルを置いて、**このアプリを作成**を選択します。

1. **[テキスト入力](controls/control-text-input.md)** コントロールを追加し、**RecordTitle** という名前を付けます。

1. **[Button](controls/control-button.md)** コントロールを追加し、**RecordTitle** の下に移動します。

1. **[Button](controls/control-button.md)** コントロールを選択した状態で、**アクション** タブの**フロー**を選択します。

    ![アクション タブのフロー オプション](./media/using-logic-flows/action-tab.png)

1. 表示されたウィンドウで、前の手順で作成したフローを選択します。

    > [!NOTE]
   > 作成したフローが選べない場合は、フローを作成した環境に Power Apps が設定されているかどうかを確認します。

    ![カスタマイズ ウィンドウからフローを追加する](./media/using-logic-flows/add-flow-from-pane.png)

1. 数式バーで、自動的に追加された数式の末尾に **RecordTitle.Text)** と入力するか貼り付けます。

    ![フローを含む OnSelect プロパティ](./media/using-logic-flows/onselect-with-flow.png)

## <a name="test-the-flow"></a>フローをテストする
1. **テキスト入力**コントロールをダブルクリックし、テキストを入力または貼り付けます。

1. Alt キーを押しながら、**[Button](controls/control-button.md)** コントロールを選択します。

    指定したリストに、タイトルとして指定したテキストを含む SharePoint アイテムが作成されます。 フローの実行時にリストが開いていたときは、変更内容を表示するためにブラウザー ウィンドウを更新する必要があります。
