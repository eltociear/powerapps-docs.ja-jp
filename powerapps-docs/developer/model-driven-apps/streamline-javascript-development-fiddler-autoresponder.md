---
title: Fiddler の AutoResponder を使用したスクリプト Web リソース開発 (model-driven apps) | Microsoft Docs
description: JavaScript Web リソースのローカル デバッグのために、Fiddler で AutoResponder を設定して使用する方法について説明します。
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: shilpas
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: c663432ec70fb474900bc949e55f198236878b76
ms.sourcegitcommit: b5ab419dad4e9d64a5e6610641363b0d7487930a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2020
ms.locfileid: "3465552"
---
# <a name="script-web-resource-development-using-fiddler-autoresponder"></a>Fiddler の AutoResponder を使用したスクリプト Web リソース開発

JavaScript Web リソースの開発およびデバッグ中に、[Telerik の Fiddler](https://www.telerik.com/fiddler) を使用すると、Web リソースのコンテンツをモデル駆動型アプリ インスタンスにアップロードして毎回公開するのではなく、ローカル ファイルからのコンテンツで置き換えることができます。 Fiddler で AutoResponder を設定するには、以下の手順を使用します。

## <a name="install-and-configure-fiddler"></a>Fiddler のインストールおよび構成

1. Fiddler を[ダウンロード](https://www.telerik.com/download/fiddler)してインストールします。
1. Fiddler を開いて、メニュー バーから、**ツール**に移動し、**オプション**を選択します。
2. HTTPS トラフィックをキャプチャして、復号化するように、ダイアログ ボックスで **HTTPS** タブを選択して、**HTTPS 接続をキャプチャ**および **HTTPS トラフィックを復号化**チェック ボックスをオンにします。<br />
 ![[HTTP] タブでマークの付いたチェックボックスをオンにする](media/fiddler-https-options.png "[HTTP] タブでマークの付いたチェックボックスをオンにする")</br>
3. **OK** をクリックしてダイアログ ボックスを閉じます。

> [!NOTE]
> この設定を有効にするのが初めての場合は、Fiddler は証明書をインストールするように要求します。 新しい設定が有効になるように、証明書をインストールして、Fiddler を再起動します。<br />
> 過去に Fiddler を実行しており、`NET::ERR_CERT_AUTHORITY_INVALID` エラーが発生した場合は、**HTTPS** タブで**操作**ボタンをクリックし、**すべての証明書をリセット**を選択します。 これによっても、新しい証明書をインストールするよう要求する複数のプロンプトが表示されます。

## <a name="configure-autoresponder"></a>AutoResponder の構成

1. Dynamics 365 インスタンスでデバッグするページを開きます。
2. 左下隅にある**キャプチャ**ボタンをクリックして、Fiddler トレース キャプチャを開始します。
   ![[キャプチャ] ボタンをクリックして HTTPS トラフィックのキャプチャを開始する](media/fiddler-start-capturing.png "[キャプチャ] ボタンをクリックして HTTPS トラフィックのキャプチャを開始する")</br>

   > [!NOTE]
   > 特定のホストからの HTTPS トラフィックのみキャプチャする場合は、**フィルター**タブの**ホスト**領域にある **-ホスト フィルターなし-** ドロップダウンで、メニューから**次のホストのみ表示**を選択して、トラフックを表示するドメインのリストをセミコロンで区切って入力します。 詳細: [フィルターの参照](https://docs.telerik.com/fiddler/KnowledgeBase/Filters)。
   > ![Fiddler UI に表示されるトラフィックをフィルター](media/fiddler-filter-traffic.png "Fiddler UI に表示されるトラフィックをフィルター")

3. テストするスクリプトを読み込むのに必要な操作を実行します。 同じ**キャプチャ**ボタンをもう一度クリックして、キャプチャを停止できます。
4. 左側のウィンドウからトレース ログ セッションを選択して、AutoResponder をセットアップするファイルを検索します。<br /> たとえば、デバッグするコードが `new_testscript.js` という名前の JavaScript Web リソース内にある場合、**検索**ボタンを使用して、**セッションを検索**ダイアログ ボックス開き、その Web リソースの名前を検索します。 <br />![Fiddler でセッションを検索する](media/fiddler-find-sessions.PNG)<br />検索条件と一致する行が左側のウィンドウに強調表示されるのがわかります。
5. その行を選択します。 右側のウィンドウで、**AutoResponder** タブを選択します。 <br /> ![[AutoResponder] タブを選択する](media/fiddler-auto-responder.png)
6. **AutoResponder** タブで、**有効化ルール**および**一致しない要求のパススルー**チェック ボックスを選択します。<br />
   ![強調表示された 2 つのチェックボックスを選択する](media/fiddler-select-checkbox.png "強調表示された 2 つのチェックボックスを選択する")<br />
7. ターゲット ファイルに関連するセッションがまだ選択されていることを確認してから、**AutoResponder** セクションの**ルールの追加**ボタンをクリックします。 これによって、新しいエントリがルール テーブルに追加されます。<br />
   ![新しいルールの追加](media/fiddler-add-rule.png "新しいルールの追加")
8. ルールを選択すると、下部の**ルール エディター**の先頭行にファイルに関連するセッション URL が入力され、`EXACT:` のような文字列が接頭辞として付加されます。<br />
   その後、一致する文字列を編集して簡略化できます。 Web リソースでは、最後に発行されたバージョンが応答に含まれていることを確認するために、URL には URL またはクエリ文字列で生成された値が含まれます。 `EXACT` 値が次のように表示されることを確認するでしょう。<br />
    ```
    EXACT:https://<org URL>/%7B636556138760000160%7D/WebResources/new_testscript.js?    ver=-1229805553
    ```<br />
    You can simplify this to remove the generated values and use this instead:<br />
    ```
    /WebResources/new_testscript.js
    ```<br />
   The bottom row is left blank. Type the path to your local file on your disk on this bottom row and <strong>Save</strong>.<br />
   ![Add path to your local file in Rule editor](media/fiddler-save-rule.png "Add path to your local file in Rule editor")<br />


By following the above steps, Fiddler is configured to listen to the requests and responds with the local file instead of passing the request over the network.

## Update and test your code

1. Apply changes to your local file.
2. Start Fiddler trace capture again and go back to your browser and hard reload the page with empty cache.
3. In the browser developer tools you can see that the file that is now received will be the local one.
4. Continue repeating this process while updating your code until you get the results you require.


## See Also

[Web resources](web-resources.md)<br />
[Client scripting using JavaScript](client-scripting.md)
