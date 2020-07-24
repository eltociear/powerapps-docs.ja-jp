---
title: ポータルの条件付きステップの種類の構成 | MicrosoftDocs
description: ポータルの条件付ステップ タイプを追加およびコンフィギュレーションする指示をします。
author: sandhangitmsft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: sandhan
ms.reviewer: tapanm
ms.openlocfilehash: 8b3ccd9195d74f35cd4665226d5429017db88d0c
ms.sourcegitcommit: c12260f372ad2cc48d3146be570d2088c9ef1d86
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2020
ms.locfileid: "3492262"
---
# <a name="add-a-conditional-step-type"></a>条件付きのステップの種類を追加する

Web フォームのステップは、ステップで式を評価する 'Condition' の種類にすることができます。 式が true として評価されると、次のステップが表示されます。 式が false として評価され、'Next Step If Condition Fails' (失敗時に次のステップへ) が指定されている場合、そのステップが表示されます。 現在のエンティティが、式を評価する対象として使用されます。 レコード ソースは、既定で前のステップのレコード ソースになります。

## <a name="attributes"></a>属性

| 名前                         | 内容                                                                                                                                                                                                                          |
|------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 条件                    | 評価する条件式                                                                                                                                                                                           |
| 条件が失敗した場合の次のステップ | [条件付きのステップの種類] は、ほかと異なり、[次の手順] の検索が 2 つあります。 条件が true として評価される場合、[次のステップ] の既定の検索が尊重されます。 条件が false として評価される場合、次のステップが設定されます。 |

使用可能な演算子は次のとおりです。

| 演算子    | 種類                   |
|---------------|------------------------|
| =, ==         | 次の値に等しい                 |
| !=            | 等しくない             |
| &gt;          | 次の値より大きい           |
| &lt;          | より小さい              |
| &gt;=         | 以上 |
| &lt;=         | 以下    |
| &             | かつ                    |
| \|             | または                     |
| !             | 否定                    |
| =\*、==\*、-= | 類似                   |
| !=\*          | 否定 Like               |

## <a name="format"></a>書式

式の形式は次のとおりです:

\[エンティティ属性の論理名\] \[演算子\] \[値\]

例:

new\_categorycode = 750101

条件には、複数の式を指定できます。 かっこを使用して入れ子になった式をグループ化できます。例:

new\_categorycode = 750101 & gendercode = 2

-   new\_categorycode = 750101 & (gendercode = 2 | gendercode = 3)

-   new\_name = Jane Doe

-   new\_twooptionfield = true

-   new\_twooptionfield = false

### <a name="see-also"></a>関連項目

[ポータルの構成](configure-portal.md)  
[エンティティ フォームの定義](entity-forms.md)  
[ポータルの Web フォームの手順](web-form-steps.md)  
[フォームの読み込みまたはタブの読み込みのステップの種類](load-form-step.md)  
[リダイレクト ステップの種類](add-redirect-step.md)  
[カスタム JavaScript を追加する](add-custom-javascript.md)  

