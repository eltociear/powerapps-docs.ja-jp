---
title: モデル駆動型アプリで電子メールを作成するときに電子メール テンプレートを挿入する |Microsoft Docs
description: 電子メールの作成時に、あらかじめ書式設定された電子メール メッセージを挿入します。
ms.date: 04/09/2020
ms.service:
- dynamics-365-sales
ms.topic: article
author: sbmjais
ms.author: shjais
manager: shujoshi
ms.openlocfilehash: 8f5b607375cccd03b3bcea2bd5d50664e7033ae4
ms.sourcegitcommit: 2484ebce6563cfd1c849e1e2f66dd2d29fdb7b64
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2020
ms.locfileid: "81007987"
---
# <a name="insert-an-email-template"></a>電子メール テンプレートを挿入する

電子メール テンプレート (あらかじめ書式設定された電子メール メッセージ) を使用して、電子メール メッセージをすばやく作成して送信することができます。 電子メールの作成中に、コマンド バーで **[テンプレートの挿入]** を選択して、テンプレートを挿入することができます。 使用できるテンプレートの一覧は、 **[電子メール テンプレート]** ウィンドウに表示されます。 **[最近使用した項目]** セクションでは、お客様が最近使用した 4 つのテンプレートが表示されます。 **[すべてのテンプレート]** セクションには、そのままで使用できるすべての電子メール テンプレート (グローバルおよびエンティティ固有) の一覧がアルファベット順に表示されます。 グローバル テンプレートは、ユーザー タイプとして表示されます。 カスタム電子メール テンプレートを作成した場合は、ここでも使用できます。 カスタム電子メール テンプレートの作成については、「[電子メールのテンプレートの作成](https://docs.microsoft.com/power-platform/admin/create-templates-email)」を参照してください。

特定の言語のテンプレートを表示するには、 **[言語]** リストから言語を選択します。 テンプレートを検索するか、リストを参照して選択することができます。 電子メール テンプレートを選択すると、ウィンドウの右側にプレビューが表示されます。 プレビューには内容が表示されるため、ニーズに最も合ったテンプレートを選択できます。 電子メール テンプレートを挿入したら、必要に応じて内容を変更し、電子メールを送信することができます。

> [!NOTE]
> 検索は正規表現をサポートしておらず、テンプレート名でのみ機能します。

**電子メール テンプレートを挿入するには**

1.  電子メール エディターで、コマンド バーの **[テンプレートの挿入]** を選択します。

     > [!div class="mx-imgBorder"]
     > ![[テンプレートの挿入] ボタン](media/insert-email-template-button.png "[テンプレートの挿入] ボタン") 

    **[電子メール テンプレート]** ウィンドウが開きます。

2.  別のロケールのテンプレートを表示するには、 **[言語]** リストから言語を選択します。 テンプレートは、選択した言語に基づいて読み込まれます。    

3.  目的のテンプレートを参照します。 テンプレートを選択し、テンプレートの内容をプレビューします。

4.  必要に応じて、テンプレートの名前の下矢印を選択して、その内容の説明を表示できます。

5.  **[テンプレートの適用]** を選択して、電子メールに内容を挿入します。

     > [!div class="mx-imgBorder"]
     > ![[電子メール テンプレート] ウィンドウ](media/email-templates-window.png "[電子メール テンプレート] ウィンドウ")

より小さい画面サイズのデバイスで電子メール テンプレートを挿入しようとすると、テンプレートを検索して選択するためのオプションのみが表示されます。

> [!div class="mx-imgBorder"]
> ![テンプレートの検索](media/search-template.png "テンプレートの検索") 

### <a name="see-also"></a>関連項目

[強化された電子メールの設定](https://docs.microsoft.com/power-platform/admin/system-settings-dialog-box-email-tab)<br>
[強化された電子メール エクスペリエンスを使用した電子メールの作成と送信](enhanced-email.md)
