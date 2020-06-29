---
title: Office 365 Outlook の接続の概要 | Microsoft Docs
description: Power Apps への Office 365 Outlook の接続に関する参照情報 (例を含む)
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 10/20/2017
ms.author: lanced
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1886514d036fe2b64ae82712128b14e19189fc73
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3306384"
---
# <a name="connect-to-office-365-outlook-from-power-apps"></a>Power Apps から Office 365 Outlook に接続する
![Office 365 Outlook](./media/connection-office365-outlook/office365icon.png)

Office 365 Outlook に接続すると、メール メッセージの表示、送信、削除、返信、その他のタスクを実行できます。

コントロールを追加して、アプリでこれらの機能を実行できます。 たとえば、メールの宛先、件名、本文などの情報を要求する**テキスト入力**コントロールを追加したり、メールを送信する**ボタン** コントロールを追加したりできます。

このトピックでは、Office 365 Outlook を接続として追加する方法、アプリに Office 365 Outlook をデータ ソースとして追加する方法、および他のコントロールでこのデータを使う方法について説明します。

> [!IMPORTANT]
> 現時点で、カレンダー操作では定期的なイベントがサポートされていません。

[!INCLUDE [connection-requirements](../../../includes/connection-requirements.md)]

## <a name="connect-to-office-365-outlook"></a>Office 365 Outlook に接続する
1. [データ接続を追加](../add-data-connection.md) して、**Office 365 Outlook** を選択します:  
   
    ![Office 365 への接続](./media/connection-office365-outlook/add-office.png)
2. **接続**を選択します。サインインが求められた場合は、職場のアカウントを入力します。

Office 365 Outlook 接続が作成され、アプリに追加されます。 これにより、接続を使用できるようになりました。

## <a name="show-messages"></a>メッセージを表示する
1. **挿入**メニューで、**ギャラリー**を選択してから、**テキスト ギャラリー** コントロールを選択します。
2. その **[項目](../controls/properties-core.md)** プロパティを次の式に設定します:  
   
    `Office365.GetEmails({fetchOnlyUnread:false})`
   
    設定の変更後、**レイアウト**を**タイトル、サブタイトル、本文**に変更します。
    
    ギャラリー コントロールに、電子メールの一部が自動的に設定されます。
    
3. ギャラリーで、最初のラベルの**テキスト** プロパティを `ThisItem.From` に設定します。 2 つ目のラベルを `ThisItem.Subject` に設定します。 3 つ目のラベルを `ThisItem.BodyPreview` に設定します。 ラベルのサイズを変更することもできます。
   
    ギャラリー コントロールが、新しいプロパティで自動的に設定されます。
4. この機能には、省略可能なパラメーターがいくつかあります。 ギャラリーの**項目**プロパティを、次のいずれかの式に設定します:
   
    `Office365.GetEmails({fetchOnlyUnread:false})`  
    `Office365.GetEmails({fetchOnlyUnread:false, top:2})`  
    `Office365.GetEmails({folderPath:"Sent Items", fetchOnlyUnread:false, top:2})`  
    `Office365.GetEmails({folderPath:"Sent Items", fetchOnlyUnread:false, top:2, searchQuery:"powerapps"})`  
    `Office365.GetEmails({folderPath:"Deleted Items", fetchOnlyUnread:false, top:2, skip:3})`

## <a name="send-a-message"></a>メッセージを送信する
1. **挿入**メニューで、**テキスト**を選択してから、**テキスト入力**を選択します。
2. 上記の手順を 2 回繰り返して 3 つのボックスを作成します。次に、作成した 3 つのボックスを一列に配置します。  
   
    ![3 つのボックスを一列に配置](./media/connection-office365-outlook/threetextinput.png)
3. コントロールの名前を次のように変更します:  
   
   * **inputTo**
   * **inputSubject**
   * **inputBody**
4. **挿入**メニューで、**コントロール**を選択してから、**ボタン**を選択します。 その **[OnSelect](../controls/properties-core.md)** プロパティを次の式に設定します:  
   
    `Office365.SendEmail(inputTo.Text, inputSubject.Text, inputBody.Text)`
5. ボタンを他のすべてのコントロールの下に表示されるように移動し、**[テキスト](../controls/properties-core.md)** プロパティを **"メールの送信"** に設定します。
6. F5 キーを押すか、プレビュー ボタン (![プレビュー ボタン](./media/connection-office365-outlook/preview.png)) を選択します。 有効なメール アドレスを **inputTo** に入力し、他の 2 つの**テキスト入力**コントロールに適当なテキストを入力します。
7. **メールの送信**を選択してメッセージを送信します。 既定のワークスペースに戻るには、Esc キーを押します。

## <a name="send-a-message-with-an-attachment"></a>添付ファイル付きのメッセージを送信する
たとえば、ユーザーがデバイスのカメラを使用して写真を撮影し、その写真を添付ファイルとして送信するアプリを作成できます。 ユーザーは、他のさまざまな種類のファイルを電子メール アプリに添付することもできます。

メッセージに添付ファイルを追加するには、前のセクションの手順に従いますが、添付ファイルを指定するにはパラメーターを追加します (ボタンの **OnSelect** プロパティを設定するとき)。 このパラメーターはテーブルとして構成されており、ここで各添付ファイルの最大 3 つのプロパティを指定します:

* 件名
* ContentBytes
* @odata.type

> [!NOTE]
> @odata.type プロパティを指定できる添付ファイルは 1 つだけです。また、このプロパティは空の文字列に設定できます。

この例では、写真は **file1.jpg** として送信されます:

`Office365.SendEmail(inputTo.Text, inputSubject.Text, inputBody.Text, {Attachments:Table({Name:"file1.jpg", ContentBytes:Camera1.Photo, '@odata.type':""})})`

この例では、写真の他に、オーディオ ファイルが送信されます。

`Office365.SendEmail(inputTo.Text, inputSubject.Text, inputBody.Text, {Attachments:Table({Name:"file1.jpg", ContentBytes:Camera1.Photo, '@odata.type':""}, {Name:"AudioFile", ContentBytes:microphone1.audio })})`

## <a name="delete-a-message"></a>メッセージを削除する
1. **挿入**メニューで、**ギャラリー**を選択してから、**テキスト ギャラリー** コントロールを選択します。
2. その **[項目](../controls/properties-core.md)** プロパティを次の式に設定します:  
   
    `Office365.GetEmails({fetchOnlyUnread:false})`
   
    ギャラリー コントロールに、電子メールの一部が自動的に設定されます。
3. ギャラリーで、最初のラベルの**テキスト** プロパティを `ThisItem.Id` に設定します。 2 つ目のラベルを `ThisItem.Subject` に設定します。 3 つ目のラベルを `ThisItem.Body` に設定します。
4. ギャラリーで最初のラベルを選び、名前を **EmailID** に変更します。
   
    ![1 つ目のラベルの名前変更](./media/connection-office365-outlook/renameheading.png)
5. ギャラリーで 3 つ目のラベルを選択し、**ボタン** (**挿入**メニュー) を追加します。 ボタンの **OnSelect** プロパティを次の式に設定します:  
   
    `Office365.DeleteEmail(EmailID.Text)`
6. F5 キーを押すか、プレビュー ボタンを選択します (![[プレビュー] ボタン](./media/connection-office365-outlook/preview.png))。 ギャラリーでメールの 1 つを選択し、ボタンをクリックします。 
    
    > [!NOTE]
    > 選択したメールが受信トレイから削除されます。 慎重に選んでください。
7. 既定のワークスペースに戻るには、Esc キーを押します。

## <a name="mark-a-message-as-read"></a>メッセージを開封済みにする
このセクションでは「[メッセージを削除する](connection-office365-outlook.md#delete-a-message)」と同じコントロールを使います。

1. ボタンの **OnSelect** プロパティを次の式に設定します:  
   
    `Office365.MarkAsRead(EmailID.Text)`
2. F5 キーを押すか、プレビュー ボタンを選択します (![[プレビュー] ボタン](./media/connection-office365-outlook/preview.png))。 未開封の電子メールの 1 つを選択してから、ボタンをクリックします。
3. 既定のワークスペースに戻るには、Esc キーを押します。

## <a name="helpful-links"></a>便利なリンク
* すべての機能とそのパラメーターの一覧については、[Office 365 Outlook の参照](https://docs.microsoft.com/connectors/office365connector/) を参照してください。
* [使用可能な接続](../connections-list.md) をすべて参照してください。  
* [接続を管理する](../add-manage-connections.md) 方法についてご確認ください。

