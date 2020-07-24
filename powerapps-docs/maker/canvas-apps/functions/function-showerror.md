---
title: Notify 関数 | Microsoft Docs
description: Power Apps での Notify 関数の構文と例を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 02/28/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9a4facf4689ed09e7628411f1c55739f8980336f
ms.sourcegitcommit: 129d004e3d33249b21e8f53e0217030b5c28b53f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2020
ms.locfileid: "3308040"
---
# <a name="notify-function-in-power-apps"></a>Power Apps の Notify 関数
バナー メッセージをユーザーに表示します。

## <a name="description"></a>内容
**Notify** 関数を使用すると、画面の上部に現在表示されている内容の上に重ねて、バナー メッセージがユーザーに表示されます。  通知は、ユーザーがそれを閉じるか、別の通知で置き換えられるか、またはタイムアウトの期限が切れるまで、既定で 10 秒に設定されています。

メッセージの種類に応じて適切な色とアイコンが使用されます。   種類は、関数の 2 つ目の引数で指定します。

| NotificationType 引数 | 内容 |
| --- | --- |
| **NotificationType.Error** | メッセージをエラーとして表示します。 |
| **NotificationType.Information** (既定) | メッセージを情報提供として表示します。  |
| **NotificationType.Success** | メッセージを成功として表示します。 |
| **NotificationType.Warning** | メッセージを警告として表示します。 |

アプリの作成中と、エンド ユーザーがアプリを使用しているときの両方でメッセージが表示されます。

**Notify** は、[動作の数式](../working-with-formulas-in-depth.md) 内でのみ使用できます。

**Notify** は [**IfError**](function-iferror.md) 関数と組み合わせて、エラーを検出し、カスタム エラー メッセージを使って報告することができます。

Power Apps では、**Notify** と全く異なるメカニズムを使用してプッシュ通知を送信することもできます。  詳細については、[Power Apps で通知を送信する](../add-notifications.md) を参照してください。

**Notify** は、常に *true* を返します。

注: この関数は、以前は **ShowError** という名前で、エラー メッセージのみを表示できました。

## <a name="syntax"></a>構文
**Notify**( *Message* [, *NotificationType* [ , *Timeout* ] ] )

* *Message* – 必須。  ユーザーに表示するメッセージ。
* *NotificationType* – 省略可能。  上の表の表示できるメッセージの種類。  既定は **NotificationType.Information** です。  
* *Timeout* – 省略可能。  通知を自動的に閉じる前に待機するミリ秒数。  既定値は 10 秒 (または 10000 ミリ秒) です。  *タイムアウト*が 0 の場合、通知は無期限に表示されます。

## <a name="examples"></a>例

### <a name="step-by-step"></a>手順

1. 画面に**ボタン** コントロールを追加します。

2. **ボタン**の **OnSelect** プロパティを数式に設定します。　

    ```powerapps-dot
    Notify( "Hello, World" )
    ```

3. クリックするか、ボタンを押します。  

    ボタンがクリックされるたびに、**Hello, World** というメッセージが情報提供としてユーザーに表示されます。  ユーザーがこのメッセージを閉じないようにするか、もう一度ボタンを押すようにしないと、10 秒 (既定のタイムアウト) で自動的に閉じます。

    ![作成環境で、Button.OnSelect により Notify が呼び出され、その結果ユーザーに対して青色のバナー メッセージで "Hello, World" のメッセージが表示されている図](media/function-showerror/hello-world.png)

4. エラーを示すようにメッセージの種類を変更します。  次の数式に 2 つ目の引数を追加します。

    ```powerapps-dot
    Notify( "Hello, World", NotificationType.Error )
    ```

5. クリックするか、ボタンを押します。

    これで、ボタンがクリックされるたびに、**Hello, World** というメッセージがエラーとしてユーザーに表示されます。  ユーザーがこのメッセージを閉じないようにするか、もう一度ボタンを押すようにしないと、10 秒 (既定のタイムアウト) で自動的に閉じます。

    ![作成環境で、Button.OnSelect により Notify が呼び出され、その結果ユーザーに対して赤色のバナー メッセージで "Hello, World" のメッセージが表示されている図](media/function-showerror/hello-world-error.png)

4. 警告を示すようにメッセージの種類を変更します。  次の式の 2 つ目の引数を変更します。

    ```powerapps-dot
    Notify( "Hello, World", NotificationType.Warning, 4000 )
    ```

5. クリックするか、ボタンを押します。

    これで、ボタンがクリックされるたびに、**Hello, World** というメッセージが警告としてユーザーに表示されます。  ユーザーがこのメッセージを閉じないようにするか、ボタンをもう一度押すようにしないと、4 秒 (4000 ミリ秒) で自動的に閉じます。

    ![作成環境で、Button.OnSelect により Notify が呼び出され、その結果ユーザーに対してオレンジ色のバナー メッセージで "Hello, World" のメッセージが表示されている図](media/function-showerror/hello-world-warning.png)

4. 成功を示すようにメッセージの種類を変更します。  次の式の 2 つ目の引数を変更します。

    ```powerapps-dot
    Notify( "Hello, World", NotificationType.Success, 0 )
    ```

5. クリックするか、ボタンを押します。

    これで、ボタンがクリックされるたびに、**Hello, World** というメッセージが成功としてユーザーに表示されます。  タイムアウト時間が **0** の場合、通知はユーザーによって、またはボタンをもう一度押すことによってのみ閉じられます。

    ![作成環境で、Button.OnSelect により Notify が呼び出され、その結果ユーザーに対して緑色のバナー メッセージで "Hello, World" のメッセージが表示されている図](media/function-showerror/hello-world-success.png)
