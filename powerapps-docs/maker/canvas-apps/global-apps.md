---
title: キャンバス アプリにグローバル サポートを組み込む | Microsoft Docs
description: Power Apps を使用して、世界中で使用されるアプリを作成します。
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/25/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: bf43c9bebc0bac2a12ecc19ca22e01aa34394a24
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2019
ms.locfileid: "3304268"
---
# <a name="build-global-support-into-canvas-apps"></a>キャンバス アプリにグローバル サポートを組み込む
Power Apps はグローバル製品です。 さまざまな言語や地域でキャンバス アプリを構築し、使用できます。

アプリの構築中および実行中、Power Apps によって表示されるテキストはさまざまな言語に翻訳されています。  メニュー項目、ダイアログ ボックス、リボン タブ、その他のテキストがお使いの言語で表示されます。  日付や数字の入力と表示にも、お使いの言語と地域が適用されています。  たとえば、世界の一部の地域では **.** (ドットまたはピリオド) が、その他の地域では **,** (コンマ) が小数点として使用されます。  

作成したアプリをグローバル対応にすることもできます。  **[Language](functions/function-language.md)**、**[Text](functions/function-text.md)**、**[Value](functions/function-value.md)**、**[DateValue](functions/function-datevalue-timevalue.md)** やその他の関数を使用して、異なる言語で表示され、入力として使用されるものを調整できます。   

## <a name="language-settings"></a>言語の設定
ネイティブのスタジオまたはネイティブのプレーヤーを使用している場合は、使用する言語がホスト オペレーティング システムによって提供されます。  Windows の場合、これは「すべての設定」、次に「時間と言語」の設定で制御できます。  さらに Windows では、言語設定を上書きして、小数点区切り文字として使用する文字を指定できます。  

Web エクスペリエンスを使用する場合、使用する言語はブラウザーによって提供されます。  多くのブラウザーでは、既定でホスト オペレーティング システムの設定が使用されますが、一部のブラウザーでは手動で言語を設定することもできます。

## <a name="authoring-environment"></a>作成環境
作成環境は、作成者の言語設定に適応します。  さまざまな言語を使用する作成者たちが同じアプリを編集できるように、アプリ自体は言語に依存しない方法で格納されます。

### <a name="names-in-formulas"></a>数式での名前
数式のほとんどの要素は常に英語です。

* 関数名: **If**、**Navigate**、**Collect**、...
* コントロールのプロパティ名: **Screen.Fill**、**Button.OnSelect**、**Textbox.Font**、...
* 列挙名: **Color.Aqua**、**DataSourceInfo.MaxValue**、**FontWeight.Bold**...
* 信号レコード: **Compass.Heading**、**Location. Latitude**、**App.ActiveScreen**、...
* 演算子: **Parent**、**in**、**exactIn**、...

作成環境がローカライズされると、コントロールやその他のオブジェクト名が作成者のネイティブ言語で表示されます。  スペイン語の場合、一部のコントロールは次のように表示されます。

![](media/global-apps/insert-controls-es.png)

アプリに次のいずれかを挿入すると、その名前は既定で英語になります。  これは、コントロールのプロパティ名と、数式の残りの部分との一貫性を保つために行われます。  たとえば、上記で一覧表示されている **Casilla** は **Checkbox1** として挿入されます。  

コントロールの挿入後に、好きな名前に変更できます。  選択した状態では、「コンテンツ」リボンの左側にコントロールの名前が表示されます。  この名前を選択すると、名前を編集できるテキスト ボックスが現れます。

![](media/global-apps/control-rename.png)

必要に応じて、コントロールの名前を **Casilla1** に変更できます。  この場合ブラウザーによって赤い波線が表示されるのは、この名前がスペイン語ではないためであり、問題はありません。

以下のものについて、好きな名前を付けることができます。

* コントロール名
* コレクション名
* コンテキストの変数名

### <a name="formula-separators-and-chaining-operator"></a>数式の区切り記号とチェーン演算子
いくつかの[区切り記号と演算子](functions/operators.md) は、作成者の言語の小数点に基づいて変更されます。

| 作成者の言語の小数点 | Power Apps 小数点 | Power Apps リスト区切り記号 | Power Apps チェーン演算子 |
| --- | --- | --- | --- |
| **.** (ドットまたはピリオド) |**.** (ドットまたはピリオド) |**,** (コンマ) |**;** (セミコロン) |
| **,** (コンマ) |**,** (コンマ) |**;** (セミコロン) |**;;** (二重セミコロン) |

Power Apps のリスト区切り記号の変更は、Excel のリスト区切り記号の変更と一致します。  これにより、次のものが影響を受けます。

* 関数呼び出しの引数。
* [レコード](working-with-tables.md#elements-of-a-table) のフィールド。
* [テーブル](working-with-tables.md#inline-value-tables) のレコード。

たとえば、次の数式を、小数点にドットまたはピリオドを使用する言語および地域 (日本や英国など) で表したとします。

![Power Apps formula If open paren slider1 dot value greater than 12 dot 59 comma notify open paren "Valid!" comma success close paren semi-colon Navigate open paren "NextScreen" comma None close paren comma notify open paren "Invalid, try again" comma error close paren close paren](media/global-apps/operators-dot.png)

次に、フランスやスペインなど、小数点記号にコンマが使用されている言語と地域で、同じ式を表示します。

![Power Apps formula If open paren slider1 dot value greater than 12 comma 59 semi-colon notify open paren "Valid!" semi-colon success close paren double semi-colon Navigate open paren "NextScreen" semi-colon None close paren semi-colon notify open paren "Invalid, try again" semi-colon error close paren close paren](media/global-apps/operators-comma.png)

強調表示は、2 つのバージョン間で変更される演算子を示しています。  プロパティ選択演算子 **.** (ドットまたはピリオド) は、**Slider1.Value** では、小数点が何であろうと常に同じである点に注意してください。

内部的には数式は変更されず、変更されるのは表示方法と作成者による編集方法のみです。  2 つの異なる言語を使用する 2 人の作成者が、それぞれの言語に応じた区切り文字と演算子を見ながら同じ数式を編集することができます。

## <a name="creating-a-global-app"></a>グローバルなアプリの作成
作成したアプリは、さまざまな言語に適応し、世界中のユーザーに優れたユーザー エクスペリエンスを提供することができます。

### <a name="language-function"></a>Language 関数
**[Language](functions/function-language.md)** 関数は、現在のユーザーの言語タグを返します。  たとえば、この関数は英国のユーザーには **"en-GB"** を、ドイツのユーザーには **"de-DE"** を返します。  

特に、**Language** を使用すると、ユーザー向けに翻訳されたテキストを表示できます。  アプリには、アプリの翻訳済みの値のテーブルを含めることができます。

![](media/global-apps/loc-table.png)

その後、次のような数式を使用して、テーブルから翻訳された文字列をプルします。

**LookUp( Table1, TextID = "Hello" && (LanguageTag = Left( Language(), 2 ) || IsBlank( LanguageTag ))).LocalizedText**  

その他の言語に翻訳された文字列は、ご使用の言語での文字列よりも大幅に長くなる可能性があることに注意してください。  多くの場合、ユーザー インターフェイスで文字列を表示するラベルとその他の要素を、対応するために幅を広げる必要があります。

詳細については、**[Language](functions/function-language.md)** 関数のドキュメントを参照してください。

### <a name="formatting-numbers-dates-and-times"></a>数値、日付、および時刻の書式設定
世界各地で、数値、日付、および時刻はさまざまな形式で表記されています。  コンマの意味、小数点以下桁数、および月、日、年の順序は場所によって異なります。   

**[Text](functions/function-text.md)** 関数は、ユーザーの言語設定を使用して数値および日付を書式設定します。

**Text** には、数値や日付をどのように書式設定するかを把握するために、書式設定文字列が必要です。  この書式設定文字列は、以下の 2 つの書式のいずれかである可能性があります。

* **グローバル対応列挙体。**  たとえば、**Text( Now(), DateTimeFormat.LongDate )** のようになります。  この数式は、言語に適切な形式で現在の日付の書式を設定します。  これは、書式設定文字列を指定する場合にお勧めします。
* **カスタム書式設定文字列。**  たとえば、**Text( Now(), "[$-en-US]dddd, mmmm dd, yyyy" )** とすると、言語「en-US」で使用される場合の列挙と同様のテキストが表示されます。  カスタム書式設定文字列の利点は、特定の項目を指定できることです。

カスタム書式設定文字列の前にある「[$-en-US]」は、カスタム書式設定文字列を解釈する言語を **Text** に指示しています。  これが挿入され、既定でユーザーの作成言語になります。  通常、これを変更する必要はありません。  これは、さまざまな言語を使用する作成者が同じアプリを編集するときに便利です。

**Text** に対する 3 つ目の引数は、関数の結果にどの言語を使用するかを指定します。  既定では、現在のユーザーの言語設定です。

詳細については、**[Text](functions/function-text.md)** 関数のドキュメントを参照してください。      

### <a name="reading-numbers-dates-and-times"></a>数値、日付、および時刻の読み取り
ユーザーが指定した数値、日付、および時刻を読み取るための 4 つの関数があります。

* **[Value](functions/function-value.md)**: テキスト文字列の数字を数値に変換します。
* **[DateValue](functions/function-datevalue-timevalue.md)**: 文字列の日付値を日付/時刻値に変換します。  テキスト文字列で指定された時刻は無視されます。
* **[TimeValue](functions/function-datevalue-timevalue.md)**: テキスト文字列の時刻値を日付/時刻値に変換します。  テキスト文字列で指定された日付は無視されます。
* **[DateTimeValue](functions/function-datevalue-timevalue.md)**: テキスト文字列の日付と時刻の値を日付/時刻値に変換します。  

Excel を使用したことがある場合、これらの関数はすべて単一の **Value** 関数にまとめられています。  Power Apps には日付/時刻および数字に個別の型があるため、ここでは分割されます。

これらすべての関数には、同じ引数があります。

* *String, required*: ユーザーからの文字列です。 これには、**Text input** コントロールに入力され、**Text** プロパティによってこのコントロールから読み取られる文字列の種類などがあります。
* *Language, optional*: *文字列* を解釈する言語。  既定では、ユーザーの言語設定です。

たとえば、次のようなものです。

* **Value( "12,345.678", "en-US" )** または **Value( "12,345.678" )** の場合、「en-US」がユーザーの言語であり、計算に使用できる数字 **12345.678** を返します。
* **DateValue( "1/2/01", "es-ES" )** または **DateValue( "1/2/01" )** の場合、「es-ES」がユーザーの言語であり、日付/時刻の値 **2001 年 2 月 1 日深夜**を返します。
* **TimeValue( "11:43:02", "fr-FR" )** または **DateValue( "11:43:02" )** の場合、「fr-FR」がユーザーの言語であり、日付/時刻の値 **1970 年 1 月 1 日 11:43:02** を返します。
* **TimeDateValue( "11:43:02 1/2/01", "de-DE" )** または **DateValue( "11:43:02" )** の場合、「de-DE」がユーザーの言語であり、日付/時刻の値 **2001 年 2 月 1 日 11:43:02** を返します。

詳細については、**[Value](functions/function-value.md)** および **[DateValue、TimeValue、DateTimeValue](functions/function-datevalue-timevalue.md)** 関数に関するドキュメント、および[日付と時刻の処理](show-text-dates-times.md) を参照してください。

### <a name="calendar-and-clock-information"></a>カレンダーと時計の情報
**[Calendar](functions/function-clock-calendar.md)** 関数および **[Clock](functions/function-clock-calendar.md)** 関数は、ユーザーの現在の言語でのカレンダーと時計の情報を提供します。  

特に、これらの関数を使用すると、選択肢が一覧表示された **Dropdown** コントロールが提供されます。  

詳細については、**[Calendar](functions/function-clock-calendar.md)** 関数および **[Clock](functions/function-clock-calendar.md)** 関数のドキュメントを参照してください。
