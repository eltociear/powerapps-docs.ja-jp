---
title: ポータルの Liquid の演算子を使用する | MicrosoftDocs
description: ポータルで使用可能な Liquid の演算子について説明します。
author: gitanjalisingh33msft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: gisingh
ms.reviewer: tapanm
ms.openlocfilehash: 08dc5cd0293f6d4a140e420b828bb34b6715add5
ms.sourcegitcommit: c12260f372ad2cc48d3146be570d2088c9ef1d86
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2020
ms.locfileid: "3490137"
---
# <a name="understand-liquid-operators"></a>Liquid の演算子の認識

Liquid は、すべての一般的な論理演算子および比較演算子を使用できます。 これらは、**if**や**unless**などのタグで使用できます。

## <a name="basic-operators"></a>基本演算子

| ==    | 次の値に等しい                          |
|-------|---------------------------------|
| !=    | が次の値と等しくない                  |
| &gt;  | より大きい                    |
| &lt;  | より小さい                       |
| &gt;= | 指定の値以上        |
| &lt;= | 指定の値以下           |
| または    | 条件 A **または**条件 B  |
| および   | 条件 A **および**条件 B |

## <a name="contains"></a>が次の値を含む

contains は、文字列内のサブストリングの有無をテストします。

```
{% if page.title contains 'Product' %}

The title of this page contains the word Product.

{% endif %}
```

contains は、文字列の配列内の文字列の有無もテストできます。

## <a name="startswith"></a>指定の値で始まる

startswith は、文字列が指定のサブストリングで始まるかどうかをテストします。

```
{% if page.title startswith 'Profile' %}

This is a profile page.

{% endif %}
```

## <a name="endswith"></a>指定の値で終わる

endswith は、文字列が指定のサブストリングで終わるかどうかをテストします。

```
{% if page.title endswith 'Forum' %}

This is a forum page.

{% endif %}
```

### <a name="see-also"></a>関連項目

[Web テンプレートを使用したソース コンテンツの保存](store-content-web-templates.md)  
[Liquid の種類](liquid-types.md)  
[条件](liquid-conditional-operators.md)  
[Liquid オブジェクト](liquid-objects.md)  
[Liquid タグ](liquid-tags.md)  
[Liquid フィルター](liquid-filters.md) 