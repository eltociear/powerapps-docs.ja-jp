---
title: Exit 関数 | Microsoft Docs
description: Power Apps での Exit 関数の構文と例を含む参照情報
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
ms.openlocfilehash: 6bb2e0c63e64614cb097bc64e5fcefc16efe6694
ms.sourcegitcommit: 0c92e85f95f3baa04cce140c96e53d5d86d685c0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "3333106"
---
# <a name="exit-function-in-power-apps"></a>Power Apps での Exit 関数
現在実行しているアプリを終了し、オプションで現在のユーザーをサインアウトします。

## <a name="description"></a>内容
**Exit** 関数は、現在実行しているアプリを終了します。 ユーザーはアプリの一覧に戻ります。 その後、ユーザーは開く別のアプリを選択できます。  

**Exit** は以降の数式の評価を停止します。 **Exit** の後に[セミコロン演算子](operators.md) で連鎖された関数の呼び出しは実行されません。   

任意の *Signout* 引数を使用して、現在のユーザーを Power Apps から サインアウトできます。 *Signout* は、ユーザー セキュリティを確保するためデバイスを共有する場合、役に立ちます。

アプリを作成中の **Exit** の呼び出しで、ユーザーは終了またはサインアウトされません。  ただし、残りの数式の評価は停止します。

**Exit** は [動作の数式](../working-with-formulas-in-depth.md) 内でのみ使用できます。

## <a name="syntax"></a>構文
**Exit**( [*Signout*] )

* *Signout* – オプション. *true* の場合、Power Apps から現在のユーザーをサインアウトするブール値。  既定は *false* で、ユーザーはサインインしたままです。

## <a name="examples"></a>例

| 計算式 | 内容 | 
| --- | --- | 
| **Exit()** | 現在のアプリを終了し、ユーザーがサインインしたままにします。  ユーザーはアプリの一覧に戻ります。  |
| **Exit(&nbsp;true&nbsp;)** | 現在のアプリを終了し、ユーザーがサインアウトします。ユーザーはアプリを実行する前に、認証情報を使用して再びサインインする必要があります。 | 


