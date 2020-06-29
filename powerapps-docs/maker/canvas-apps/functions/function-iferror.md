---
title: Power Apps での IfError および IsError 関数 | Microsoft Docs
description: Power Apps での IfError および IsError 関数の構文と例を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/04/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: cde72d49ce3fdd742fcbdada31715b24c9cdf486
ms.sourcegitcommit: 0c92e85f95f3baa04cce140c96e53d5d86d685c0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "3333194"
---
# <a name="iferror-and-iserror-functions-in-power-apps"></a>Power Apps での  IfError および IsError 関数

[この記事はプレリリース ドキュメントであり、変更されることがあります。]

エラーを検出し、代替値を提供するか、またはアクションを実行します。

> [!NOTE]
> - IfError および IsError 関数は実験的な機能の一部であり、変更されることがあります。 詳細: [Power Apps での実験的な機能、プレビュー、および非推奨の機能について](../working-with-experimental-preview.md)。
> - この記事で説明する動作は、[詳細設定](../working-with-experimental-preview.md#controlling-which-features-are-enabled) の*数式レベルのエラー管理*の実験的な機能が、オンになっている場合にのみ (既定ではオフ) 使用可能です。
> - お客様のフィードバックは弊社にとって非常に重要です。ご意見を [Power Apps コミュニティ フォーラム](https://powerusers.microsoft.com/t5/Expressions-and-Formulas/bd-p/How-To) にお寄せください。

## <a name="iferror"></a>IfError

**IfError** 関数は、エラーが見つかるまで値をテストします。 関数がエラーを検出した場合、関数は対応する置換値を評価して返し、それ以降のさらに詳しい評価を停止します。  エラーが見つからない場合は、既定値を指定することもできます。  **IfError** の構造は **If** 関数の構造に似ています: **IfError** はエラーをテストし、**If** は **true** をテストします。

**IfError** を使用してエラーを有効な値に置き換えて、下流の計算を続行できるようにします。 たとえば、ユーザー入力がゼロによる除算になる可能性がある場合は、次の関数を使用します。

```powerapps-dot
IfError( 1/x, 0 )
```

`x` の値がゼロの場合 `1/x` はエラーを生成するため、この数式は `0` を返します。  `x` がゼロでない場合、`1/x` が返されます。  

### <a name="stopping-further-processing"></a>以降の処理を停止する

次のように数式を[動作の数式](../working-with-formulas-in-depth.md) で一緒に[チェーン](operators.md) する場合:

```powerapps-dot
Patch( DS1, ... );
Patch( DS2, ... )
```

`DS1` への **Patch** が 失敗しても `DS2` への 2 つ目の [**Patch**](function-patch.md) 関数が試行されます。  エラーの範囲は、連鎖された各数式に制限されます。

**IfError** を使用してアクションを実行し、アクションが成功した場合にのみ処理を続行します。 この例に **IfError** を適用します:

```powerapps-dot
IfError(
    Patch( DS1, ... ), Notify( "problem in the first action" ),
    Patch( DS2, ... ), Notify( "problem in the second action" )
)
```

`DS1` の **Patch** に問題がある場合、1 つ目の **Notify** が実行されます。 `DS2` の 2 つ目の **Patch** を含む以降の処理は行なわれません。 1 つ目の **Patch** が成功した場合、2 つ目の **Patch** が実行されます。  

指定した場合、エラーが検出されない場合は、任意の *DefaultResult* 引数が返されます。  この引数がなければ、最後の*値*引数が返されます。 

最後の例を基にして、**IfError** からの戻り値を照合して問題があったかどうかを特定することができます。

```powerapps-dot
IfError(
    Patch( DS1, ... ), Notify( "problem in the first action" );  false,
    Patch( DS2, ... ), Notify( "problem in the second action" ); false,
    true
)
```

### <a name="type-compatibility"></a>種類の互換性

**IfError** はその引数の 1 つの値を返します。  **IfError** によって返される可能性があるすべての値の種類は互換性がなければなりません。  

最後の例で、**Patch** は *Replacement* 数式または *DefaultResult* で使用されたブール値と互換性のないレコードを返します。 これらの **Patch** 呼び出しからの戻り値が **IfError** によって返されるという状況はないので、これは問題ありません。

> [!NOTE]
> 変更の動作中の間、現在 **IfError** へのすべての引数の種類は互換性がある必要があります。

前述の簡単な例では:

```powerapps-dot
IfError( 1/x, 0 )
```

`1/x` および `0` の種類は、両方ともテキスト文字例であったため互換性がありました。  そうでない場合、2 つ目の引数は最初の引数の種類と一致するように強制されます。

Excel に **#DIV/0!** が表示されます ゼロによる除算が発生すると。

代わりに、次のように **IfError** を検討します。

```powerapps-dot
IfError( 1/x, "#DIV/0!" )
```

上記の数式は機能しません。 テキスト文字列 `"#DIV/0!"` は、最初の引数の種類を **IfError**に強制され、それは数値です。  **IfError** の結果はテキスト文字列を強制できないため、さらに別のエラーとなります。  修正として、最初の引数をテキスト文字列に変換して、**IfError** が常にテキスト文字列を返すようにします。  

```powerapps-dot
IfError( Text( 1/x ), "#DIV/0!" )
```  

上に示すように、*Replacement* または *DefaultResult* がエラーの場合、**IfError** はエラーを返すことができます。

### <a name="errorinfo"></a>ErrorInfo

置換数式の中で、**ErrorInfo** レコードは、見つかったエラーに関する情報を提供します。 このレコードには次のものが含まれます。

| **ErrorInfo** フィールド | 種類​​ | 内容 |
|---------------------|------|-------------|
| **コントロール** | テキスト文字列 | エラーが発生した場所を報告するために使用される現在のコントロールの名前。 |
| **種類** | **ErrorKind** 列挙 (数値) | エラーの分類。 |
| **メッセージ** | テキスト文字列 | エンド ユーザーに表示するのに適した、エラーに関するメッセージ。 |
| **Notify** | Boolean | IfError によってキャッチされなかった場合、エンド ユーザー通知バナーが表示されるべきかどうか。 |
| **プロパティ** | テキスト文字列 | エラーが発生した場所を報告するために使用される現在のプロパティの名前。 |

たとえば、次の数式を [**Button**](../controls/control-button.md) コントロールの **OnSelect** プロパティとして検討します。

```powerapps-dot
IfError( 1/0, Notify( "Internal error: " & ErrorInfo.Control & "." & ErrorInfo.Property ) )
```

上記の数式の例では、ボタンがアクティブ化されると次のバナーを表示します。

![Button コントロールがアクティブ化され、Notify 関数から通知が表示される](media/function-iferror/notify-errorinfo.png)

## <a name="iserror"></a>IsError

**IsError** 関数はエラー値をテストします。  戻り値は、ブール値の *true* または *false* です。

**IsError** を使用すると、エラーの以降の処理が実行されなくなります。

## <a name="syntax"></a>構文

**IfError**( *Value1*, *Replacement1* [, *Value2*, *Replacement2*, ... [, *DefaultResult* ] ] )

* *Value(s)* – 必須。 エラー値をテストする数式。
* *Replacement(s)* – 必須。 評価する数式、および一致する*値*の引数がエラーを返した場合に返される値。
* *DefaultResult* – オプション。  数式にエラーが見つからないかどうかを評価する数式。

**IsError**( *Value* )

* *Value* – 必須。 エラー値をテストする数式。

## <a name="examples"></a>例

### <a name="simple-iferror"></a>簡単な IfError

| 計算式 | 内容 | 結果 |
| --- | --- | --- |
| **IfError( 1, 2 )** |最初の引数は、エラーではありません。 この関数には、チェックする他のエラーおよび既定の戻り値はありません。 関数は、評価された最後の*値*引数を返します。   | 1 |
| **IfError( 1/0, 2 )** | 最初の引数は、(ゼロによる除算のため) エラー値を返します。 関数は 2 番目の引数を評価し、結果として返します。 | 2 |
| **IfError( 10, 20, 30 )** | 最初の引数は、エラーではありません。 関数には、チェックする他のエラーはありませんが、既定の戻り値はあります。 関数は、*DefaultResult* 引数を返します。 | 30 |
| **IfError( 10, 11, 20, 21, 300 )** | 最初の引数 **10** はエラーではないので、関数はその引数の対応する置換である **11** を評価しません。 3 番目の引数 **20** もエラーではないので、関数はその引数の対応する置換である **21** を評価しません。 5 番目の引数 **300** には対応する置換がなく、既定の結果です。 数式にはエラーを含まないため、関数はその結果を返します。 | 300 |
| **IfError( 1/0, Notify( "There was an internal problem" ) )** | 最初の引数は、(ゼロによる除算のため) エラー値を返します。 関数は 2 番目の引数を評価し、ユーザーにメッセージを表示します。 **IfError** の戻り値は **Notify** の戻り値であり、**IfError** の最初の引数 (数値) と同じ種類に強制されます。 | 1 |

### <a name="simple-iserror"></a>簡単な IsError

| 計算式 | 内容 | 結果 |
| --- | --- | --- | 
| **IsError( 1 )** | 引数は、エラーではありません。  | *false* | 
| **IsError( 1/0 )** | 引数が、エラーです。  | *True* | 
| **If( IsError( 1/0 ), Notify( "There was an internal problem" ) )** | **IsError** の引数は、(ゼロによる除算のため) エラー値を返します。 この関数は *true* を返し、これにより **If** が **Notify** 関数でユーザーにメッセージを表示するようになります。 **If** の戻り値は **Notify**の戻り値であり、**If** の最初の引数 (ブール値) と同じ種類に強制されます。 | *True* |

### <a name="step-by-step"></a>手順

1. **[テキスト入力](../controls/control-text-input.md)** コントロールを追加し、既定でその名前が付いていない場合は **TextInput1** という名前を付けます。

1. **[Label](../controls/control-text-box.md)** コントロールを追加し、既定でその名前が付いていない場合は **Label1** という名前を付けます。

1. **Label1** の **Text** プロパティを次の数式に設定します。

    ```powerapps-dot
    IfError( Value( TextInput1.Text ), -1 )
    ```

1. **TextInput1** に、**1234** を入力します。  

    Label1 は Value 関数への有効な入力値として **1234** の値を表示します。

1. **TextInput1** に、**ToInfinity** を入力します。

    Label1 は Value 関数への有効な入力値ではないため **-1** の値を表示します。  Value 関数を IfError で折り返さない場合、エラー値が*空白*として扱われるためラベルには値が表示されません。 

### <a name="see-also"></a>関連項目

[Power Apps 向けの数式のリファレンス](../formula-reference.md)
