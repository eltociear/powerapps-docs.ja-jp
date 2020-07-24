---
title: キャンバス アプリを Web サイトなどのサービスに統合する | Microsoft Docs
description: Web サイトやその他のサービスにキャンバス アプリを埋め込みます。
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 04/13/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 050633cc9cb89d1a137aea2e087c10a3b1fb4cd7
ms.sourcegitcommit: 81d6996e870b55797372429d66f9b56a7200d154
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2020
ms.locfileid: "3309420"
---
# <a name="integrate-canvas-apps-into-websites-and-other-services"></a>キャンバス アプリを Web サイトなどのサービスに統合する
多くの場合、作成したアプリを、ユーザーが業務を行っている場所で使用できると非常に便利です。 キャンバス アプリを iframe に埋め込むことで、これらのアプリを Power BI または SharePoint などの Web サイトやその他のサービスに統合できます。

このトピックでは、アプリを埋め込むためのパラメーターを設定する方法を説明した後で、Asset Ordering (資産の注文) アプリを Web サイトに埋め込みます。

![埋め込みアプリが表示された Power BI ダッシュボード](./media/embed-apps-dev/embed-dashboard.png)

次の制限事項に注意してください。

- 埋め込みアプリにアクセスできるのは、同じテナント内の Power Apps ユーザーだけです。
- Internet Explorer 11 を使用して Power Apps にアクセスするには、互換表示をオフにする必要があります。

iframe を使用せずに SharePoint Online にキャンバス アプリを統合することもできます。 詳細については、[Power Apps Web パーツを使用する](https://support.office.com/article/use-the-powerapps-web-part-6285f05e-e441-408a-99d7-aa688195cd1c)を参照してください。

## <a name="set-uri-parameters-for-your-app"></a>アプリに URI パラメーターを設定する
アプリを埋め込む場合は、まず Uniform Resource Identifier (URI) のパラメーターを設定して、iframe がアプリの場所を認識できるようにします。 URI の形式は次のとおりです。

```
https://apps.powerapps.com/play/[AppID]?source=iframe
```

> [!IMPORTANT]
> 2019 年 8 月の時点で、URI 形式は https://web.powerapps.com/webplayer から https://apps.powerapps.com/play に変更されました。 新しい URI 形式を使用するように埋め込み iframe を更新してください。 以前の形式への参照は、互換性を確保するために新しい URI にリダイレクトされます。
>
> 以前の形式:
> 
> https\://web.powerapps.com/webplayer/iframeapp?source=iframe&appId=/providers/Microsoft.PowerApps/apps/[AppID]

この URI の \[AppID\] ('[' と ']' を含む) を、対象のアプリの ID に置き換えるだけです。 値を取得する方法は後で説明しますが、その前に、URI で使用できるすべてのパラメーターを以下に示します。

* **[appID]** - 実行するアプリの ID を指定します。
* **tenantid** - ゲスト アクセスをサポートするオプションのパラメーターであり、アプリを開くテナントを決定します。 
* **screenColor** - ユーザーのアプリの読み込みエクスペリエンスを向上するために使用します。 このパラメーターは [RGBA (赤の値、緑の値、青の値、アルファ)](../canvas-apps/functions/function-colors.md) の形式で、アプリが読み込まれるときの画面の色を制御します。 アプリのアイコンと同じ色に設定することをお勧めします。
* **source** - アプリには影響しませんが、埋め込みのソースを示すわかりやすい名前を追加することをお勧めします。
* 最後に、[Param() 関数](../canvas-apps/functions/function-param.md) を使用してカスタム パラメーターを追加すると、その値をアプリで使用できます。 これは `[AppID]?source=iframe&param1=value1&param2=value2` のように、URI の末尾に追加されます。 これらのパラメーターは、アプリの起動時にのみ読み取られます。 それらを変更する必要がある場合は、アプリを再起動する必要があります。 [appid] の後の最初のアイテムのみに 「?」 を付ける必要があることに注意してください。その後、ここに示すように 「&」 を使用します。 

### <a name="get-the-app-id"></a>アプリ ID を取得する
アプリの ID は powerapps.com で調べることができます。 埋め込むアプリに対して次の手順を実行します。

1. [powerapps.com](https://powerapps.microsoft.com) の **アプリ** タブで、省略記号 (**. . .**) をクリックまたはタップします。 そして**詳細**を選択します。
   
    ![アプリの詳細に移動する](./media/embed-apps-dev/details.png)
1. **アプリ ID** をコピーします。
   
    ![詳細からアプリ ID をコピーする](./media/embed-apps-dev/app-id.png)
1. URI の `[AppID]` 値を置き換えます。 資産の注文アプリの場合、URI は次のようになります。
   
    ```
    https://apps.powerapps.com/play/76897698-91a8-b2de-756e-fe2774f114f2?source=iframe
    ```

[Launch()](functions/function-param.md) 関数を使用して Web ページまたはアプリを起動するアプリを Web サイトに埋め込む場合、ブラウザーでポップアップを許可する必要があります。

## <a name="embed-your-app-in-a-website"></a>Web サイトにアプリを埋め込む
アプリの埋め込みは、サイトの HTML コードに iframe を追加することと同じほど (または、Power BI や SharePoint などの iframe をサポートするその他のサービス) 簡単にできるようになりました。

```html
<iframe width="[W]" height="[H]" src="https://apps.powerapps.com/play/[AppID]?source=website&screenColor=rgba(165,34,55,1)" allow="geolocation; microphone; camera"/>
```

iframe の幅と高さの値を指定し、`[AppID]` をアプリの ID で置き換えます。

> [!NOTE]
> `allow="geolocation; microphone; camera"` を iframe HTML コードに含めて、アプリが Google Chrome でこれらの機能を使用できるようにします。

次の図は、サンプルの Contoso 社 Web サイトに埋め込まれた資産の注文アプリを示しています。

![埋め込みアプリが表示された Contoso 社 Web サイト](./media/embed-apps-dev/contoso-website.png)

アプリのユーザーの認証に関して、次の点に注意してください。

- Web サイトが Azure Active Directory (AAD) ベースの認証を使用する場合は、追加のサインインは必要ありません。
- Web サイトが他のサインインのメカニズムを使用する場合や、認証されない場合は、iframe でユーザーに対してサインイン プロンプトが表示されます。 アプリの作成者がアプリをユーザーと共有していれば、ユーザーはサインイン後にアプリを実行できるようになります。

このように、アプリの埋め込みは簡単で有用です。 埋め込みにより、Web サイト、Power BI ダッシュボード、SharePoint ページなど、ユーザーと顧客が業務を行う場所にアプリを配置できます。
