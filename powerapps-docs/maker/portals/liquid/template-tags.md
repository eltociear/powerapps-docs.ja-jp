---
title: ポータルでテンプレート タグを使用する | MicrosoftDocs
description: ポータルで使用可能なテンプレート タグについて説明します
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 06/06/2020
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 064980a6189b56b97f2be3dc64929db961e3ba5f
ms.sourcegitcommit: 6f904789d817248eac0a4c9dd0c5fe37dfbb77ad
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2020
ms.locfileid: "3434615"
---
# <a name="template-tags"></a>テンプレート タグ

テンプレート タグは、さまざまな方法でテンプレートの出力を制御し、複数のテンプレートを 1 つの出力にまとめることができます。

## <a name="fetchxml"></a>FetchXML

ユーザーが CDS からデータを照会し、結果をページに表示できるようにします。

> [!NOTE]
> FetchXML を使用したデータのクエリの詳細については、[FetchXML を使用してデータをクエリする](https://docs.microsoft.com/powerapps/developer/common-data-service/use-fetchxml-construct-query)をご覧ください。

```
{% fetchxml resultVariable %}
<!— Fetchxml query -->
...
{% endfetchxml %}
```

### <a name="results-attribute"></a>結果属性

提供された変数の結果属性 (上記のサンプルの "resultVariable"など) は、FetchXML クエリ結果と他のいくつかの属性を保持します。

- *エンティティ*

    この属性には、FetchXML クエリの結果が含まれます。 結果を繰り返して、Web テンプレートで使用できます。

    ```
    <table> 
    {% for entityVariable in resultVariable.results.entities %} 
    <tr> 
    <td>Attribut-1: {{ entityVariable.attribute1 }}</td> 
    <td>Attribut-2: {{ entityVariable.attribute2 }}</td> 
    </tr> 
    {% endfor %} 
    </table> 
    ```

- *EntityName*

    エンティティの論理名を取得します。

- *ExtensionData*

    追加のデータを格納する構造を取得します。

- *MinActiveRowVersion*

    アクティブな行の最小バージョン値を取得します。

- *MoreRecords*

    使用可能なレコードがさらにあるかどうかを取得します。

- *PagingCookie*

    現在のページング情報を取得します。

- *TotalRecordCount*

    コレクション内のレコードの総数を取得します。 <br/>
    クエリが実行されたとき、ReturnTotalRecordCount は true でした。

- *TotalRecordCountLimitExceeded*

    クエリの結果が合計レコード数を超えるかどうかを取得します。

### <a name="xml-attribute"></a>XML 属性

提供された変数 (上記のサンプルの "resultVariable" など) の XML 属性は、Common Data Service からデータを取得するために使用できる結果のクエリを保持します。 この属性は、エンティティ アクセス許可が *fetchxml* タグにどのように適用されるかを理解したい場合にデバッグ目的で役立ちます。  

## <a name="include"></a>include

名前により、1 つのテンプレートの内容を別のテンプレートに含めます。 Power Apps ポータルでは、これ以外のテンプレートのソースは、通常 [Web テンプレート](store-content-web-templates.md)です。 これにより、複数の場所で共通のテンプレートのフラグメントを再利用できます。  

テンプレートが別のテンプレートに含まれている場合、含まれたテンプレートは親のテンプレートで定義された変数にアクセスできます。

`{% include 'My Template' %}`

include タグに、名前の付けられた任意の数のパラメーターを渡すこともできます。 これらは、含まれたテンプレートで変数として定義されます。

`{% include 'My Template' a:x, b:y %}`

## <a name="block"></a>block

テンプレートを継承するために、拡張と組み合わせて使用されます。 使用方法については、拡張を参照してください。

## <a name="extends"></a>extends

テンプレートを継承するために、ブロック タグと組み合わせて使用されます。 これにより、親のレイアウトのオーバーライド指定領域でも、複数のテンプレートで共有レイアウトを使用できす。

Power Apps ポータルでは、タグに提供された親のテンプレート名は、通常 [Web テンプレート](store-content-web-templates.md)の名前を参照します。  

拡張を使用する場合は、テンプレートの最初の内容である必要があり、1 つ以上のブロック タグのみ続けることができます。

親のテンプレートで定義された block がオーバーライドされなかった場合、親のテンプレートの内容 (ある場合) が表示されます。

## <a name="comment"></a>comment

流動テンプレート内の非表示コードをそのままの状態にすることができます。 ブロック内のコンテンツが表示されない場合、内部の流動コードは実行されません。

**コード**

`Hello{% comment %}, {{ user.fullname }}{% endcomment %}. My name is Charles.`

**出力**

`Hello. My name is Charles.`

## <a name="raw"></a>raw

解析および実行せずに、ページの流動コードを出力できます。

**Output**

`Hello, {{ user.fullname }}. My name is Charles.`

## <a name="substitution"></a>代替

ユーザーがヘッダーとフッターのキャッシュを有効にし、特定のセクション出力のキャッシュを避けたい場合、このタグを使用できます。 このタグは、ラップされたコンテンツ ブロックの出力がキャッシュされないヘッダーまたはフッターにコンテンツブロックを提供します。 これは、リクエスト、ページ、言語、日付など、頻繁に更新される可能性のあるオブジェクトをユーザーが使用しているシナリオで役立ちます。 たとえば、[ヘッダーとフッターのキャッシュが有効になっている](../configure/enable-header-footer-output-caching.md)場合にヘッダーとフッターの Web テンプレート ソース コード更新シナリオを参照してください。

> [!TIP]
> [request.url](liquid-objects.md#request) で使用される URL は、任意の要求値にでき、後続の要求に対して [キャッシュ](../configure/enable-header-footer-output-caching.md) を取得します。 request.url の値を正しくするには、置換タグ を使用するか、 ~\{WebFile path} などの部分的な URL を使用するか、または [サイト設定](../configure/configure-site-settings.md) にポータル URL を保存することを検討してください。

### <a name="see-also"></a>関連項目

[制御フロー タグ](control-flow-tags.md)<br>
[反復タグ](iteration-tags.md)<br>
[変数タグ](variable-tags.md)<br>
[Power Apps common data service エンティティ タグ](portals-entity-tags.md)
