---
title: ユーザー定義のヘルプ ページを作成する | MicrosoftDocs
description: UCI でユーザー定義のヘルプ ページを作成する
ms.custom: ''
ms.date: 09/13/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: ''
caps.latest.revision: ''
author: matthewbolanos
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0ba852565acee10fc4c853eb185f552df6399fc9
ms.sourcegitcommit: d98dd90a7dda11f434a13a7f8976459856d6142b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/29/2020
ms.locfileid: "3093909"
---
# <a name="create-guided-help-for-your-unified-interface-app"></a>統一インターフェイスアプリのガイド付きヘルプを作成する

[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

カスタム ヘルプ ウィンドウとガイド付きタスクを使用して、統一インターフェイス アプリケーションに、自社組織に合わせたカスタムの製品内ヘルプ機能を提供します。 ユーザー定義のヘルプ ウィンドウを使用して、リッチテキスト、コンテンツリンク、イメージ、およびビデオリンクを含むエンティティ、フォーム、および言語固有のヘルプとガイダンスを提供します。 

> [!IMPORTANT]
> ユーザー定義のヘルプ ウィンドウには、従来のWebクライアントアプリケーションで使用されていた学習パスガイド付き学習機能を置き換えます。

## <a name="custom-help-panes-and-learning-path"></a>ユーザー定義のヘルプ ウィンドウと学習パス
ユーザー定義のヘルプウィンドウの新しいガイド付きヘルプの実装は、以前の学習パスガイド付きヘルプ機能とは異なります。 どちらの機能でも、アプリケーションのユーザー定義ヘルプを作成できます。 ただし、カスタム ヘルプ ウィンドウは、最も一般的なガイド付きヘルプ シナリオに最適化されています。   

ユーザー定義のヘルプ ウィンドウには、学習パスでは使用できない次の主要機能があります。 
- 箇条書きや番号付けなどの形式を問わないリッチテキスト。
- 視覚的にリンクされたコーチ マークとヘルプバルーン。
- プライベートソースを含む、さらなるビデオソースのオプション。
- ソリューションの一部として Common Data Service にヘルプコンテンツを保存します。 

ユーザー定義のヘルプ ウィンドウには、学習パスでは使用することができない次の主要機能があります。 
- 連続したヘルプバルーン。
- ロールに基づいたヘルプ ページ。
- スマートフォンなどのデバイスのフォーム ファクターごとのヘルプ ページ。 

## <a name="prerequisites"></a>前提条件 
ユーザー定義のヘルプ ウィンドウを作成するには、以下が必要になります: 
- バージョン 9.1.0.10300 またはそれ以降。
- **ヘルプ ページ** 特権に対するグローバル作成、読み取り、書き込み、削除、追加、および追加のアクセス許可。 既定では、システム管理者とシステムカスタマイザの両方のセキュリティ ロールがこの特権を持っています。  
- [ご利用の環境で、ユーザー定義のヘルプ ウィンドウを有効にしている必要があります。](#enable-custom-help-panes-for-your-environment)

## <a name="enable-custom-help-panes-for-your-environment"></a>ご利用の環境で、ユーザー定義のヘルプ ウィンドウを有効にする
1. モデル駆動形アプリを開き、コマンド バーの **設定** ![設定](../model-driven-apps/media/powerapps-gear.png) > **詳細設定**を選びます。
2. **設定** > **システム** > **管理** に移動します。  
3. **管理**ページで、**システム設定**を選択します。
4. **全般** タブの **ユーザー定義ヘルプのURL設定**で、 **ユーザー定義ヘルプ ウィンドウ と ガイド付きタスクを有効にする** に **はい** を選択し、 **OK**を選択します。

    > [!div class="mx-imgBorder"] 
    > ![ユーザー定義ヘルプ ウィンドウを有効にする](media/enable-custom-help-panes.png "ユーザー定義ヘルプ ウィンドウを有効にする")

> [!IMPORTANT]
> ユーザー定義ヘルプ ウィンドウ、または ユーザー定義ヘルプを有効にすることができますが、同時にこの両方を有効にすることはできません。 **ユーザー定義可能なエンティティにユーザー定義のヘルプを使用する** および **URL にパラメーターを追加する** が両方とも **いいえ**に設定されていることを確認します。  
 
## <a name="context-sensitive-custom-help"></a>状況に依存するユーザー定義のヘルプ
各ヘルプ ウィンドウには、次のコンテキストにごとに固有となります: 
- アプリケーション 
- エンティティ
- [フォーム] 
- Language   

## <a name="help-pane-navigation"></a>ヘルプ ウィンドウのナビゲーション
既定では、ヘルプペインは開いたままであり、別のフォームに移動しても、最初にで開いたヘルプコンテンツに表示されます。 これにより、ユーザーをアプリのさまざまな部分に誘導する際に、ヘルプコンテンツをそのまま残すことができます。 

### <a name="to-author-help-pane-content"></a>ヘルプ ウィンドウの内容を作成する
1.  ヘルプ ウィンドウを表示するには、モデル駆動形アプリを開き、コマンド バーの **ヘルプ**を選択します。 

    ![ヘルプ](media/help-command.png)   
2.  ヘルプ ウィンドウで、縦に並んだ省略記号を選択し **編集**を選択します。 

    ![ヘルプを編集する](media/help-edit-command.png)
    
    ヘルプ ウィンドウが編集モードになり、ヘルプウィンドウのタイトルにカーソルが置かれます。
3.  編集ウインドウから、以下のタスクを実行することが出来ます: 
    - ヘルプ ウィンドウの領域に直接文字を入力します。 
    - 太字、斜体、取り消し線、リストの作成などのリッチテキストコマンドを使用して、テキストに書式を設定します。 
    - **挿入** タブを選択して、セクション、ビデオ、イメージ、リンク、コーチマーク、およびバルーンヘルプを追加します。 
<!-- confirm the image is safe for use
    > [!div class="mx-imgBorder"] 
    > ![Custom help pane edit](media/custom-help-pane-edit.png)  -->
4.  変更を保存するには、 **保存**を選択します。  

### <a name="free-form-text"></a>自由形式のテキスト
テキストは、ヘルプ ウィンドウ内のどこにでも配置できます。 各セクションの前、あるいは後に、自由形式のテキストを入力します。 テキストでは、太字、斜体、下線、および取り消し線のフォント形式に対応しています。 切り取り、コピー、貼り付けが使用でき、同様に複数段階の取り消しも使用できます。 

### <a name="bullets-and-numbered-lists"></a>箇条書きと番号付きリスト
行頭文字または段落番号のアイコンを選択すると、現在の行が行頭文字または段落番号の付いた行に切り替わります。 リスト内で複数の行を選択している場合は、各行が箇条書きまたは番号付きになります。 リスト内の行のサブ番号のタブおよびインデント。  

### <a name="sections"></a>セクション
セクションは折りたたみ可能なテキストボックスです。  リンクまたは自由形式のテキストを挿入できます。 セクションを使用して、類似したアイテムをグループ化します。 セクションは、既定で開いた状態にすることも、折りたたまれた状態にすることこともできます。 

### <a name="video-and-static-images"></a>ビデオおよび静止画像
ヘルプウィンドウには、ビデオや静止画像を挿入できます。 ビデオと画像は、インターネット上のコンテンツへのリンクとなります。 ユーザー定義のヘルプ ウィンドウには、ビデオとイメージファイルをヘルプペインに保存されません。 ヘルプ ウィンドウが開くと、ユーザー定義のウィンドウでは、リンクからコンテンツが表示されます。 企業のプライベートコンテンツを参照する場合は、 Microsoft Stream ビデオへのリンクを使用できます。 

> [!TIP]
> 必要なビデオまたはイメージのリンクURLをコピーして、ヘルプペインに貼り付けるてください。 

ユーザー定義のヘルプ ウィンドウには、次のビデオソースに対応しています。
- Microsoft Stream (非公開コンテンツの使用) 
- YouTube
- Facebook
- Vimeo


### <a name="links"></a>リンク
Webサイトへのリンクは、同じウィンドウで開くことも(既定)、別のウィンドウで開くこともできます。 既存のヘルプページにリンクする機能は、まだ使用できません。   

### <a name="balloons-and-coach-marks"></a>バルーンとコーチマーク
バルーンとコーチマークを使用して、特定のUI要素を指定できます。 バルーンにはテキストを含めることができます。 コーチマークは、コーチポインターで要素を強調表示します。 複数のUI要素を順番に表示するには、ユーザーが選択できるリストにリンクを集めます。 以下に例を示します:

1. 指示またはコメントを含む最初のUI要素にリンクする。
2. 2番目のUI要素への指示またはコメント付きのリンクをする。
3. 3番目のUI要素への指示またはコメント付きのリンクをする。

ユーザーは、要素を順番に選択することも、特定の要素に戻ってハイライト表示することもできます。

## <a name="solutions-and-custom-help-pane-content"></a>ソリューションとユーザー定義ヘルプ ウィンドウのコンテンツ
すべてのヘルプコンテンツは、ソリューションの一部として Common Data Service のヘルプページコンポーネントに保存されます。 ソリューションをある環境から別の環境 (テスト環境から本番環境など) に移動する場合、ヘルプレコードをエクスポートしてソリューションに含むように定義することができます。 これにより、ヘルプコンテンツが別の環境に移動しても、ソリューションの機能と同期させることができます。 ソリューションの一部として、ユーザー定義のヘルプ ウィンドウは、ソリューションの標準的なアプリケーション ライフサイクル管理 (ALM) 機能をすべてサポートします。

### <a name="moving-content-via-solutions"></a>ソリューションによるコンテンツの移動
既定では、すべての新しいヘルプ ページが既定のソリューションで表示されます。 コンテンツを別の環境に移動する場合は、まず既存のヘルプページを非管理ソリューションに追加してからエクスポートします。 管理されていないソリューションにヘルプページを追加するには、次の手順に従ってください:

1. アンマネージド ソリューションに移動します。
2. コマンド バーの省略記号にて **クラシックに切り替える** を選択します。
3. **既存を追加**を選択します。
4. **ヘルプページ**を選択します。
5. 追加するヘルプページを選択し、**はい** を選択します。

> [!NOTE]
> 現在、最新のソリューションエクスプローラーでは、アンマネージド ソリューションに既存のヘルプ ウィンドウを追加することはできません。 


## <a name="help-page-documentation-automation"></a>ヘルプページのドキュメントの自動化
ソースコード管理システムにコンテンツをバックアップまたは保存することができます。 また、翻訳ツールやチェッカーなどのドキュメント自動化ツールをヘルプ ウィンドウのコンテンツで使用することもできます。 ユーザー定義のヘルプ ウィンドウ のデータは Common Data Service に直接保存され、エクスポートやインポートがすることができます。  

ユーザー定義のヘルプ ウィンドウはユーザー定義のXML形式に対応しています。 この形式については、以下で説明します。 詳細: [ユーザー定義のヘルプXMLの定義](#custom-help-xml-definition)  

エクスポートすると、各ヘルプページは個別のファイルとしてエクスポートされます。   

## <a name="frequently-asked-questions"></a>よくあるご質問
ここでは、カスタムヘルプページに関するよくある質問について説明します。 

### <a name="are-custom-help-pages-the-same-as-customizable-help"></a>ユーザー定義のヘルプページはユーザー定義可能なヘルプと同じですか?

カスタムヘルプウィンドウとガイド付きタスクは、システム設定の **ユーザー定義のヘルプURLを設定する** セクションのオプションです。 ユーザー定義のヘルプ ウィンドウとガイド付きタスクを使用すると、ユーザー定義可能なヘルプ ウィンドウがユーザーのフォームのすぐ横に表示されます。  このシステム設定セットのユーザー定義のヘルプセクションの他のオプションは、ユーザー定義のすることが可能なヘルプ機能で構成されています。 これにより、既定のアプリのヘルプを上書きして、ユーザーに別のURLを指定したヘルプを表示させることができます。 または、高度にカスタマイズされたエンティティーのヘルプを上書きして、ワークフローをより適切に記述することができます。

ユーザー定義することが可能なヘルプの詳細については、 [ユーザー定義のヘルプを有効化し、使用する](../model-driven-apps/use-customizable-help.md) を参照してください。


### <a name="how-do-i-migrate-my-data-from-learning-path-to-custom-help-pages"></a>学習パスからユーザー定義のヘルプ ページにデータを移行する方法 
学習パスには、ヘルプウィンドウと連番化されたヘルプバルーンの2種類のヘルプがあります。 連番化されたヘルプバルーンの場所は、従来のWebクライアントUIと完全に統合されており、新たなユーザー定義のヘルプウィンドウには移動できません。  

ガイド付きヘルプのテキストの量によっては、学習パスのユーザーインターフェイスから新しいユーザー定義のヘルプウィンドウのユーザーインターフェイスに情報を直接コピーする方が簡単な場合があります。 ただし、学習パスのヘルプコンテンツをエクスポートすることもできます。  最も簡単な方法は、 **学習パス** > **ライブラリの内容** > **ローカライズ** > **エクスポート** 機能を使用して、コンテンツをエクスポートします。 必要なレコードを選択してエクスポートします。 これにより、ヘルプ ウィンドウ と ガイド付きタスクごとに XLIFF ファイルが作成されます。  次に、一般に公開されている XLIFF エディタまたは XLIFF から HTML への変換ツールを使用してコンテンツを取得します。 

## <a name="custom-help-xml-definition"></a>ユーザー定義ヘルプXMLの定義
このセクションでは、ユーザー定義ヘルプXMLの定義について説明します。 

### <a name="pphml"></a>PPHML

```
<pphml>
    <h1>FAQ</h1>
    <collapsible title="What is PPHML?">
        <p>PPHML is a domain specific language for help content. It is used to create help content that includes elements such as images, videos, balloons, coach marks, etc.</p>
    </collapsible>
    <collapsible title="What does PPHML stand for?">
        <p>PPHML stands for Power Platform Help Markup Language</p>
    </collapsible>
</pphml>
```

#### <a name="definition-and-usage"></a>定義と使用法

`<pphml>` 要素は、これがPPHML文書であることをヘルプ ブラウザに伝達します。

`<pphml>` 要素は、PPHML文書のルートを表します。

`<pphml>` 要素は、その他すべてのPPHML要素の器となります。

### <a name="title"></a>タイトル
ヘルプページにタイトルを表示します。

```
<h1>This will be displayed at the top of the help page</h1>
```

#### <a name="definition-and-usage"></a>定義と使用法
**`<h1>`** 要素は、ヘルプページのタイトルを定義します。

`<h1>` これは `<pphml>` 内の最初の要素である必要があります。

### <a name="image"></a>イメージ
ヘルプページに画像を表示します。

```
<img src="smiley.gif" alt="Smiley face" title="Smiley face"/>
```

#### <a name="definition-and-usage"></a>定義と使用法
**`<img>`** 要素は、ヘルプページに画像を埋め込みます。

#### <a name="attributes"></a>属性
- `src`: 画像のURLを指定します。 この属性は必須です。

- `title`: 画像と一緒に表示するタイトルを指定します。通常は、上にマウスポインタを置いたときに表示されるツールチップです。

- `alt`: 画像の代替テキストを指定します。 このテキストはスクリーン リーダーで使用されます。

### <a name="video"></a>ビデオ
ヘルプページにビデオを表示します。

```
<video src="https://www.youtube.com/watch?v=WSWmn7WM3i4" />
```

#### <a name="definition-and-usage"></a>定義と使用法

**`<video>`** 要素は、チュートリアルやトレーニングムービーなどのビデオをヘルプページに埋め込みます。

##### <a name="supported-sources"></a>対応しているソース

- Microsoft Stream
- YouTube
- Facebook
- Vimeo

#### <a name="attributes"></a>属性
- `src`: ビデオのURLを指定します。 この属性は必須です。

- `allowFullScreen`: ユーザーがビデオを全画面表示に切り替えることができるかどうかを指定します。 使用できる値は 「True」 または 「false」です。 この属性は、ビデオソースによっていは対応していない場合があります。

- `autoplay`: ヘルプページが読み込めれるとすぐにビデオの再生を開始するように指定します。 使用できる値は 「True」 または 「false」です。 この属性は、ビデオソースによっていは対応していない場合があります。

- `startTime`: ビデオの再生を開始するポイントを秒単位で指定します。

### <a name="paragraph"></a>段落
ヘルプページに段落を表示します。

```
<p>This is some text in a paragraph.</p>
```

#### <a name="definition-and-usage"></a>定義と使用法
**`<p>`** 要素は段落を定義します。

段落内のテキストは、以下の方法で装飾できます:
- `<strong>` 要素で太字になります
- `<em>` 要素で斜体になります
- `<del>` 要素で取り消し線を引きます
- `<u>` 要素で下線を引きます

これらの装飾は組み合わせることができます。 たとえば、太字で下線付きのテキストを作成することができます。

### <a name="bulleted-list"></a>箇条書きリスト
ヘルプページに箇条書きリストを表示します。

```
<ul>
    <li>Coffee</li>
    <li>Tea</li>
    <li>Milk</li>
</ul>
```

#### <a name="definition-and-usage"></a>定義と使用法
**`<ul>`** 要素は箇条書きリストを定義します。

`<ul>` 要素を `<li>` 要素とともに使用して、箇条書きリストを作成します。

### <a name="numbered-list"></a>番号付きリスト
ヘルプページに番号付きリストを表示します。

```
<ol>
    <li>First step</li>
    <li>Second step</li>
    <li>Third step</li>
</ol>
```

#### <a name="definition-and-usage"></a>定義と使用法
**`<ol>`** 要素は、順序付けられた(番号付き)リストを定義します。
`<ol>` タグを `<li>` 要素とともに使用して、箇条書きリストを作成します。

### <a name="collapsible"></a>折りたたみ
ヘルプページに折りたたみ可能なセクションを表示します。

```
<collapsible title="This is a Section">
    <p>This is a paragraph inside a section</p>
    <img src=smiley.gif" title="This is an image inside a section" />
</collapsible>
```

#### <a name="definition-and-usage"></a>定義と使用法
**`<collapsible>`** 要素は、ユーザーが必要に応じて表示または非表示にできるコンテンツのセクションを定義します。

#### <a name="attributes"></a>属性
- `collapsed`: 最初に該当のセクションを折りたたむか展開するかを指定します。 指定できる値は、「True」(折りたたむ)または「false」(展開する)です。

### <a name="link"></a>リンク
ヘルプページにリンクを表示します。

新しいブラウザーウィンドウで開くWebサイトへのリンク:

```
<a href="https://www.microsoft.com" target="_blank">Microsoft Home Page</a>
```

別のヘルプページへのリンク:

```
<a href="./LearnMore">Learn More</a>
```

#### <a name="definition-and-usage"></a>定義と使用法
`<a>` タグは、ユーザがヘルプページからWebサイトまたは別のヘルプページに移動できるようにするリンクを定義します。

#### <a name="attributes"></a>属性

- `href`: 移動先のWebサイトまたはヘルプページのURLを指定します。 この属性は必須です。
- `target`: リンクされたURLを開く場所を指定します。
   - 存在しない、または `_self`の場合、リンクは別のヘルプページへのものとみなされ、ヘルプ ブラウザで開かれます。
   - `_blank` の場合、リンクが新しいブラウザウィンドウで開きます。
   - `_top` の場合、リンクが現在のブラウザウィンドウで開きます。
   - 値が `iframe`の名称の場合、リンクはその iframe で開かれます。

### <a name="coach-mark"></a>コーチマーク
ヘルプページにコーチマークを表示します。

```
<coachmark target="#my-html-button">Click to highlight the HTML element with id [my-html-button]</coachmark>
```

#### <a name="definition-and-usage"></a>定義と使用法
コーチマークは、ヘルプブラウザをホストするアプリケーションのUIの特定の点にユーザーの注意を引きつける目的で使用できる対話型の要素です。

#### <a name="attributes"></a>属性

- `target`: [CSS セレクター](https://www.w3schools.com/cssref/css_selectors.asp) は、コーチマークが表示されるHTML要素を指定します。 この属性は必須です。

### <a name="balloon"></a>バルーン
ヘルプページにバルーンを表示します。

```
<balloon target="#my-html-button" title="This button submits the form" details="Please click this button to continue and submit the form">Click to show a balloon over the HTML element with id [my-html-button]</balloon>
```

#### <a name="definition-and-usage"></a>定義と使用法
バルーンは、ヘルプブラウザをホストするアプリケーションのUIでユーザーがアクションを実行するのに役立つ対話型の要素です。

#### <a name="attributes"></a>属性
- `target`: CSS セレクターは、バルーンリンクが表示されるHTML要素を指定します。 この属性は必須です。
- `title`: バルーンのタイトルを指定します。
- `details`: バルーン内に表示するコンテンツを指定します。


