---
title: ポータルの制御フロー タグを使用する | MicrosoftDocs
description: ポータルで利用可能な制御フロー タグについて説明します。
author: gitanjalisingh33msft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: gisingh
ms.reviewer: tapanm
ms.openlocfilehash: 152024ed73b8d7972cd58242c15f9d91507f9607
ms.sourcegitcommit: c12260f372ad2cc48d3146be570d2088c9ef1d86
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2020
ms.locfileid: "3490277"
---
# <a name="control-flow-tags"></a>制御フロー タグ

フロー タグの管理は、特定の条件に基づいて実行する必要があるコード ブロックおよび表示する必要があるコンテンツを決定します。 条件は、利用可能な[Liquid の演算子](liquid-operators.md)を使用してビルド、または単に[指定された値の真偽](liquid-conditional-operators.md)に基づきビルドされます。  

## <a name="if"></a>if

特定の条件を満たす場合コード ブロックを実行します。

```
{% if user.fullname == 'Dave Bowman' %}

Hello, Dave.

{% endif %}
```

## <a name="unless"></a>unless

if と似ていますが、特定の条件が満た**ない**場合にのみコード ブロックを実行します。

```
{% unless page.title == 'Home' %}

This is not the Home page.

{% endunless %}
```

## <a name="elsifelse"></a>elsif/else

if または unless ブロックにさらなる条件を追加します。

```
{% if user.fullname == 'Dave Bowman' %}

Hello, Dave.

{% elsif user.fullname == 'John Smith' %}

Hello, Mr. Smith.

{% else %}

Hello, stranger.

{% endif %}
```

## <a name="casewhen"></a>case/when

変数を複数の値と比較するためにスイッチ文を作成し、値ごとに別のコード ブロックを実行します。

```
{% case user.fullname %}

{% when 'Dave Bowman' %}

Hello, Dave.

{% when 'John Smith' %}

Hello, Mr. Smith.

{% else %}

Hello, stranger.

{% endcase %}
```

### <a name="see-also"></a>関連項目

[反復タグ](iteration-tags.md)<br>
[変数タグ](variable-tags.md)<br>
[テンプレート タグ](template-tags.md)<br>
[Power Apps common data service エンティティ タグ](portals-entity-tags.md)
