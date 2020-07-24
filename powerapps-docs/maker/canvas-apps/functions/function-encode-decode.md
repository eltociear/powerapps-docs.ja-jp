---
title: EncodeUrl および PlainText 関数 | Microsoft Docs
description: Power Apps での EncodeUrl  および PlainText 関数の構文と例を含む参照情報
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
ms.openlocfilehash: 259ab99ca38a472fda5c8cd8cdf99533a5f5dfc2
ms.sourcegitcommit: 80120b59d440bb7a3ddca93cd51154607f749f6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "3307879"
---
# <a name="encodeurl-and-plaintext-functions-in-power-apps"></a>Power Apps での EncodeUrl および PlainText 関数
文字列をエンコードおよびデコードします。

## <a name="description"></a>内容
**EncodeUrl** 関数は、URL 文字列をエンコードし、特定の英数字以外の文字を % および 16 進数で置き換えます。  

**PlainText** 関数は、次のような特定のタグを適切な記号に変換して、HTML および XML タグを削除します。

* **&amp;nbsp;**
* **&amp;quot;**

これらの関数からの戻り値は、エンコードまたはデコードされた文字列です。 この関数は、すべての HTML と XML タグを削除するというわけではありません。 

## <a name="syntax"></a>構文
**EncodeUrl**( *String* )

* *String* - 必須。  エンコードする URL。

**PlainText**( *String* )

* *String* - 必須。 HTML および XML タグが削除される文字列。

## <a name="examples"></a>例
テキスト ギャラリー に RSS フィードを表示し、次に そのギャラリーのラベルの **[Text](../controls/properties-core.md)** プロパティを **ThisItem.description** に設定する場合、ラベルには次の例のように生の HTML または XML コードが表示されることがあります。

```html
    <p>We have done an unusually&nbsp;&quot;deep&quot; globalization and localization.</p>
```

ラベルの **[Text](../controls/properties-core.md)** プロパティを **PlainText(ThisItem.description)** に設定する場合、次の例のようなテキストが表示されます。

```
    We have done an unusually "deep" globalization and localization.
```