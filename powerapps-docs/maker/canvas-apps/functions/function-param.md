---
title: Launch および Param 関数 | Microsoft Docs
description: 構文と例を含むキャンバス アプリの Launch および Param 関数の参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/20/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 6dd5e41eebcc1b047f52656332ade2c644d9284f
ms.sourcegitcommit: 4b6f187c9501332f9acca5978fa326621f2980e5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/22/2020
ms.locfileid: "3394104"
---
# <a name="launch-and-param-functions-in-power-apps"></a>Power Apps の Launch および Param 関数

Web ページまたはキャンバス アプリを起動し、起動パラメーターへのアクセスを提供します。

## <a name="launch"></a>Launch

Web ページまたはキャンバス アプリを起動します。  関数は次のものをサポートしています。

- **Address** (必須)、Web ページの URL またはキャンバス アプリのアプリ ID。
- **Parameters** (オプション) Web ページまたはキャンバス アプリに渡す名前付きの値。  キャンバス アプリでは、[**Param**](#param) 関数によってパラメーターを読み込みます。
- **Target** (オプション)、Web ページまたはキャンバス アプリを起動するブラウザー タブ。

**Launch** は、[動作の数式](../working-with-formulas-in-depth.md) 内でのみ使用できます。

### <a name="address"></a>アドレス

Web ページは URL アドレスを介して起動されます。  たとえば、次のようなものです。

```powerapps-dot
Launch( "https://bing.com" )
```  

**Web リンク**または**アプリ ID**を使用してキャンバス アプリを起動できます。 アプリのこれらの値を検索するには、次を実行してください。

1. [Power Apps](https://make.powerapps.com) に移動します。
1. 左側のナビゲーション ウィンドウから、**アプリ**を選択します。
1. アプリを選択します。
1. 上部メニューから**詳細**を選択します。 <br> また、**...** (**その他のコマンド**) を選択し、ドロップダウン メニューから**詳細**を選択します。

    ![アプリの詳細オプション](media/function-param/portal-details.png "アプリの詳細オプション")

1. **Web リンク**または**アプリ ID** をコピーします。
    
    ![Web リンクとアプリ ID を含むアプリの詳細](media/function-param/portal-links.png "Web リンクとアプリ ID を含むアプリの詳細")

**Web リンク**はすべての Web ページで使用することができ、キャンバス アプリを起動できます。  **Launch** 関数を使用することもできます。

**アプリ ID** は **Launch** 関数で使用できますが、先頭に `/providers/Microsoft.PowerApps/apps/` を付ける必要があります。  たとえば、次のようなものです。

```powerapps-dot
Launch( "/providers/Microsoft.PowerApps/apps/f342faaf-5f82-4ace-a64b-7c1b01499231" )
```

デバイス上のネイティブ アプリを直接起動することはできません。 特定の Web サイトにオプションを提供するためのカスタム URL スキームのインストール、または Web ブラウザーへの登録を行うネイティブ アプリなど、一部のプラットフォームでは間接的なオプションが利用可能な場合があります。

### <a name="parameters"></a>パラメーター

**Launch** は Web ページまたはキャンバス アプリにパラメーターを渡すことができます。 パラメーターは 2 つの方法で提供されます。

- 名前値のペアの引数リスト。 たとえば、次のようなものです。

    ```powerapps-dot
    Launch( "http://bing.com/search", "q", "Power Apps", "count", 1 )
    ```

- フィールド値のレコード。 たとえば、次のようなものです。

    ```powerapps-dot
    Launch( "http://bing.com/search", { q: "Power Apps", count: 1 } )
    ```

    このフォームにより、名前と値の関連付けが明確になり、操作が簡単になります。 オプションの *LaunchTarget* 引数をサポートする唯一のフォームです。

> [!NOTE]
> 現在、パラメーターのレコード オプションは**プレビュー段階**で、間もなくすべてのリージョンでリリースされます。 プレビュー機能の詳細については、[実験、プレビュー、および廃止された Power Apps の機能について](../working-with-experimental-preview.md) に移動してください。

アドレスおよびパラメーターは渡される前に URL エンコードされ、[**EncodeUrl**](function-encode-decode.md) 関数が使用されたかのように英数字以外の文字および `%` と 16 進数で置き換えられます。

Web ページを起動するとき、パラメーターの [クエリ文字列](https://en.wikipedia.org/wiki/Query_string) が URL アドレスの最後に含められます。  **Launch** に提供される追加のパラメーターすべては、クエリ文字列の最後に追加されます。 キャンバス アプリの起動時は、クエリ文字列は機能しません。

### <a name="target"></a>対象

> [!NOTE]
> 現在、*LaunchTarget* 引数は**プレビュー段階**で、間もなくすべてのリージョンでリリースされます。 プレビュー機能の詳細については、[実験、プレビュー、および廃止された Power Apps の機能について](../working-with-experimental-preview.md) に移動してください。

*LaunchTarget* 引数を使用して、Web ページまたはアプリを開くターゲット ブラウザー ウィンドウを指定します。  次の **LaunchTarget** 列挙値またはカスタムウィンドウ*名*のいずれかを使用します。

| LaunchTarget&nbsp;enum | 内容 | 
| --- | --- | 
| **Blank** | Web ページまたはアプリは、新しいウィンドウまたはタブで開かれます。 |
| **セルフ** | Web ページまたはアプリは、現在のウィンドウまたはタブを置き換えます。 |
| *名前* | 列挙値の代わりに、独自のテキスト文字列を使用してウィンドウまたはタブに*名前*を付けます。*自分*は、**Launch** 関数でのみ使用される内部専用の名前です。 ユーザーに表示されるウィンドウのタイトルには影響せず、照合もしません。  指定された*名前*のウィンドウまたはタブは既に存在しているので、その内容は置き換えられます。 それ以外の場合、新しいウィンドウまたはタブが作成されます。  *name* は、アンダースコア文字で始まることはできません。 |

**Blank** は 、**Self** と *name* が利用可能なオプションとして設定されている Web ブラウザで実行されている場合、既定の列挙型です。 モバイル プレーヤーでは、*name* が利用可能なオプションとして設定されている Web ページでは、**Blank** が既定となり、現在のキャンバス アプリは常に別のキャンバス アプリに置き換えられます。

> [!NOTE]
> - *LaunchTarget* は、埋め込み型のシナリオ  (Power BI や SharePoint など) では **Blank** 以外の値に対応しておらず、予期せぬ動作につながる可能性があります。 将来的には、この挙動が更新される可能性もありますが、依然としてエラーとなる可能性もあります。
> - *LaunchTarget*列挙名は移行中です。 現在は **Blank** と **Self** を使用することができますが、これらの名称は将来的に変更される予定です。 **Self** は、新しい **Self** キーワードが導入されると、**'Self'** に中間的に変更されます。 この競合を回避するにあたって、予想される名前は **New** と **Replace** です。 これらの変更が発生すると、アプリでは自動的に更新されます。 既存の数式を手動で更新する必要はありません。

### <a name="security-zones"></a>セキュリティ ゾーン

Internet Explorer およびクラシック Microsoft Edge では、セキュリティ設定が呼び出しアプリ以上の場合にのみ、**Launch** 関数は Web サイトまたはキャンバス アプリを開きます。

たとえば、**Launch** 関数を**信頼済みサイト** セキュリティ ゾーンで実行するアプリに追加する場合、関数を開きたい Web サイトまたはアプリが (**制限付きサイト**ではなく) **信頼済みサイト**または**ローカル イントラネット** ゾーンにあることを確認してください。 詳細については、[Internet Explorer 11 のセキュリティとプライバシーの設定を変更する](https://support.microsoft.com/help/17479/windows-internet-explorer-11-change-security-privacy-settings) を参照してください。  

## <a name="param"></a>Param

**Param** 関数は、アプリに渡されたパラメーターをアプリの起動時に取得します。 名前付きパラメーターが渡されていなかった場合、**Param** は*空白*を返します。

- 別のキャンバス アプリからキャンバス アプリを起動する場合、**Launch** 関数に *Parameter* 引数を使用します。  パラメーターの名前と値は自動的に URL エンコードされます。
- Web ページからキャンバス アプリを起動する場合、パラメーターを [キャンバス アプリの Web リンク](#address) の [クエリ文字列](https://en.wikipedia.org/wiki/Query_string) に追加します。  これには、クエリ文字列がすでに `tenantId` に対して開始されていると仮定した `&parametername=parametervalue` を追加することが含まれます。  たとえば、`&First%20Name=Vicki&category=3` を追加すると、値が `"Vicki"` の `First Name` と値が `"3"` (値の型は*テキスト*) の `category` の 2 つのパラメーターを渡します。  空白または特殊文字が含まれている場合、[**EncodeURL**](function-encode-decode.md) 関数の使用と同じように、パラメーターの名前および値を URL エンコードする必要があります。
- Param 名は大文字と小文字が区別されます。  
- Param 名および値は、アプリで使用できるように自動的に URL デコードされます。
- パラメーターに数値が含まれている場合でも、**Param** から返される型は常にテキスト文字列になります。  その他の型への変換は自動的に行われるか、または明示的に数値に変換する [**Value**](function-value.md) 関数などの、明示的な変換を使用します。

## <a name="syntax"></a>構文

**Launch**( *Address* [, *ParameterName1*, *ParameterValue1*, ... ] )

* *Address* – 必須。  起動する Web ページのアドレスまたはアプリ ID。
* *ParameterName(s)* – 省略可能。  パラメーター名。
* *ParameterValue(s)* – 省略可能。  アプリまたは Web ページに渡す、対応するパラメーター値。

**Launch**( *Address*, { [ *ParameterName1*: *ParameterValue1*, ... ] } [, *LaunchTarget* ] )

* *Address* – 必須。  起動する Web ページのアドレスまたはアプリ ID。
* *ParameterName(s)* – 省略可能。  パラメーター名。
* *ParameterValue(s)* – 省略可能。  アプリまたは Web ページに渡す、対応するパラメーター値。
* *LaunchTarget* – 省略可能.  **LaunchTarget** 列挙値またはカスタム*名*。  

**Param**( *ParameterName* )

* *ParameterName* - 必須。  アプリに渡されるパラメーターの名前。

## <a name="examples"></a>例

### <a name="simple-launch"></a>簡単な起動

#### <a name="from-a-canvas-app-to-a-web-page"></a>キャンバス アプリから Web ページへ。

| 計算式 | 内容 |
| ------- | ----------- |
| **Launch(&nbsp;"http://bing.com/search",&nbsp;<br>"q",&nbsp;"Power&nbsp;Apps",&nbsp;"count",&nbsp;1&nbsp;)** | Web ページ **http://bing.com/search?q=Power%20Apps&count=1** を開きます。  新しいウィンドウまたはブラウザー タブが開かれます。 |  
| **Launch(&nbsp;"http://bing.com/search",&nbsp;<br>{&nbsp;q:&nbsp;"Power&nbsp;Apps",&nbsp;count:&nbsp;1&nbsp;}&nbsp;)** | 同等のレコード表記を使用している前の例と同じです。  新しいウィンドウまたはブラウザー タブが開かれます。 | 
| **Launch(&nbsp;"http://bing.com/search",&nbsp;<br>{&nbsp;q:&nbsp;"Power&nbsp;Apps",&nbsp;count:&nbsp;1&nbsp;},&nbsp;<br>LaunchTarget.Self&nbsp;)** | 前の例と同じで、Web ブラウザーで実行している場合、現在のウィンドウまたはタブを結果で置き換えます。 | 
| **Launch(&nbsp;"http://bing.com/search",&nbsp;<br>{&nbsp;q:&nbsp;"Power&nbsp;Apps",&nbsp;count:&nbsp;1&nbsp;},&nbsp;<br>"Search&nbsp;Results"&nbsp;)** | 前の例と同じように、**検索結果**という名前のウィンドウまたはタブのコンテンツを作成または置換します。 |

#### <a name="from-a-canvas-app-to-a-canvas-app"></a>キャンバス アプリからキャンバス アプリへ

必要に応じて、アプリ ID、画面名、およびレコード番号を更新します。

```powerapps-dot
Launch( "/providers/Microsoft.PowerApps/apps/YOUR-APP-ID",
        { Navigate: "Second Screen", Record: 34 }
)
```

#### <a name="from-a-web-page-to-a-canvas-app"></a>Web ページからキャンバス アプリへ

必要に応じて、アプリ ID、テナント ID、画面名、およびレコード番号を更新します。

```html
<html><body>
    <a href="https://apps.powerapps.com/play/YOUR-APP-ID?tenantId=YOUR-TENANT-ID&Navigate=Second%20Screen&Record=34">
        Launch canvas app
    </a>
</body></html>
```

### <a name="simple-param"></a>単純な Param

上記の [Web ページから](#from-a-web-page-to-a-canvas-app) または [別のキャンバス アプリから](#from-a-canvas-app-to-a-canvas-app) キャンバス アプリを起動する簡単な起動例は、Param 関数の簡単な例を示しています。

| 計算式 | 内容 | 結果 |
| ------- | ----------- |-------|
| **Param(&nbsp;"Navigate"&nbsp;)** | **Navigate** パラメーターはアプリの起動時に指定され、返されます。 | 「2 番目の画面」 |
| **Param(&nbsp;"Record"&nbsp;)** | **Record** パラメーターはアプリの起動時に指定されます。  **Launch** 関数に数字として渡されても、**Param** からの結果は、暗黙的または明示的にその他の型に変換できるテキスト文字列になります。  | 「34」 |
| **Param(&nbsp;"User"&nbsp;)**  | **User** パラメーターが指定されていません。  [**IsBlank**](function-isblank-isempty.md) 関数でテスト可能な *blank* 値が返されます。 | *空白* |

### <a name="step-by-step-examples-for-launch-and-param"></a>Launch および Param の例

**製品ショーケース** タブレット レイアウト テンプレートは、次の例で使用されました。 このテンプレートを使用してアプリを作成するには、[アプリの作成](../get-started-test-drive.md) の記事の手順に従い、**製品ショーケース** テンプレートを選択します。 自分のアプリを使用することもできます。

#### <a name="example---launch"></a>例 - Launch

1. [Power Apps](https://make.powerapps.com) に移動します。
1. 左側のナビゲーション ウィンドウから、**アプリ**を選択します。
1. アプリを選択し、**編集**を選択します。
1. メニューから**挿入**を選択し、**ラベル**を選択します。
1. ラベルを画面右下に移動します。
1. 右側のプロパティ ウィンドウから、**色**を*白*に選択し、**境界線の太さ**を *1* に設定します。
1. 右側から **Text** プロパティを選択し、テキストを *Surface タブレット ニュース*として入力します。
1. 左上のプロパティ リストから、**OnSelect** を選択します。
1. 数式を ```Launch("https://www.bing.com/news/search","q","Microsoft Surface tablets")``` と入力します。 その他の使用したい URL、パラメーター、およびキーワードを使用することもできます。

    ![起動例](media/function-param/launch-example-onselect.png "起動例")

1. アプリを保存し、公開します。
1. アプリを再生します。
1. **Surface タブレット ニュース**のラベルを選択し、*Microsoft Surface tablets* のキーワードでニュース検索を開始します。

> [!TIP]
> スケーラビリティのために、Launch 関数に手動で入力したキーワードを [変数](../working-with-variables.md) で置き換えることができます。

#### <a name="example---param"></a>例 - Param

1. [Power Apps](https://make.powerapps.com) に移動します。
1. 左側のナビゲーション ウィンドウから、**アプリ**を選択します。
1. アプリを選択し、**編集**を選択します。
1. メニューから**挿入**を選択し、**ラベル**を選択します。
1. ラベルを画面右下に移動します。
1. 左上からラベルの **Text** プロパティを選択します。
1. 数式を ```Param("browser")``` と入力します。 使用したい異なるパラメーターを使用することもできます。

    ![Param の例](media/function-param/param-example.png "Param の例")

1. アプリを保存し、公開します。
1. [Power Apps](https://make.powerapps.com) からアプリの [Web リンク](#address) をコピーします。
1. 新しいブラウザーを開きます。
1. ブラウザーにアプリの Web リンクを貼り付けて、最後に ```&browser=Microsoft%20Edge``` を追加します。

    ![Web アドレス](media/function-param/param-example-web-address.png "Web アドレス")

1. アプリが起動するとき、ラベルに渡されたパラメーター値が表示されます。

    ![Param のラベル例](media/function-param/param-example-label.png "Param のラベル例")

1. アプリ プレーヤーを閉じ、アプリを編集します。
1. 左側のナビゲーションのツリー ビューから**アプリ**を選択します。
1. 左上の **OnStart** プロパティを選択します。
1. 数式を ```If(Param("screen")="techspecs",Navigate(TechSpecs,Fade))``` として入力します。  

    ![ナビゲーションの Param の例](media/function-param/param-example-screen.png "ナビゲーションの Param の例")

    [OnStart](object-app.md#onstart-property) プロパティの [If 関数](function-if.md) は、パラメーターが特定の値に等しいかどうかをチェックします。この場合、値は *techspecs* です。 一致する場合、アプリは *TechSpecs* 画面に移動します。

    > [!NOTE]
    > **Product Showcase** アプリのテンプレートを使用していない場合、Navigate 関数の **TechSpecs** 画面名を、自分のアプリの画面名で置き換えます。

1. アプリを保存し、公開します。
1. 新しいブラウザーを開きます。
1. ブラウザーにアプリの Web リンクを貼り付けて、最後に ```&screen=techspecs``` を追加します。

    ![TechSpecs 画面の Web アドレス](media/function-param/param-example-web-address-techspecs.png "TechSpecs 画面の Web アドレス")

1. アプリは、**TechSpecs** または Navigate 関数で入力した画面で直接起動します。

### <a name="see-also"></a>関連項目

[キャンバス アプリの数式のリファレンス](../formula-reference.md)
