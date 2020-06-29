---
title: HashTags 関数 | Microsoft Docs
description: Power Apps での HashTags 関数の構文と例を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a88371e9c151ed097d2c86bcb64121c68a6d62d0
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3305096"
---
# <a name="hashtags-function-in-power-apps"></a>Power Apps での HashTags 関数
テキストの文字列からハッシュタグ (# 文字列) を抽出します。

## <a name="description"></a>内容
**HashTags** 関数はハッシュタグの文字列をスキャンします。 ハッシュタグはポンド文字 (#) で始まり、次の組み合わせが続きます。

* 大文字および小文字
* 数字
* アンダースコア
* 通貨記号 ($ など)

**HashTags** は文字列にハッシュタグを含む 1 列の [table](../working-with-tables.md) を返します。  文字列にハッシュタグが含まれていない場合、この関数は 1 列の[空](function-isblank-isempty.md) のテーブルを返します。

## <a name="syntax"></a>構文
**HashTags**( *String* )

* *String* - 必須。  ハッシュタグをスキャンする文字列。

## <a name="examples"></a>例
### <a name="step-by-step"></a>手順
1. **[テキスト入力](../controls/control-text-input.md)** コントロールを追加し、**ツイート**という名前を付けて、次の文を入力します。
   
    **This #app is #AMAZING and can #coUnt123 or #123abc but not #1-23 or #$\*(#\@")**
2. 垂直カスタム ギャラリーを追加し、その **[Items](../controls/properties-core.md)** プロパティを次の関数に設定します。
   
    **HashTags(Tweet.Text)**
3. ギャラリー テンプレートに**[Label](../controls/control-text-box.md)** コントロールを追加します。
   
    ギャラリーには、次のハッシュタグが表示されます。
   
   * **\# アプリ**
   * **\#AMAZING**
   * **\#coUnt123**
   * **\#123abc**
   * **\#1**

