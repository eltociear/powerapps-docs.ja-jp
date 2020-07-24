---
title: Assert 関数 | Microsoft Docs
description: Power Apps テスト スタジオでの Assert 関数の構文を含む参照情報
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/19/2018
ms.author: aheneay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e4319c3685db46f4277109e385a640e744402edc
ms.sourcegitcommit: 6b2961308c41867756ecdd55f55eccbebf70f7f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2020
ms.locfileid: "3307603"
---
# <a name="assert-function-in-power-apps-test-studio"></a>Power Apps テスト スタジオでの Assert 関数

アサーションは、テストにおいて true または false に評価される条件または式です。 式が false を返す場合、テスト ケースは失敗します。 アサーションは、テストまたはテスト ステップの想定される結果を実際の結果に対して検証し、条件が false の場合はテストを失敗させるために使用されます。 アサーションを使用して、アプリ内のコントロール (ラベル値、リスト ボックスの選択、その他のコントロール プロパティなど) の状態を検証できます。  

成功したアサーションと失敗したアサーションの両方に対するアサーション メッセージが、TestCaseResult レコードの Traces テーブルにも含まれます。 

## <a name="syntax"></a>構文

*Assert(expression, message)*

- *Expression* – 必須。 true または false として評価される式。
- *Message* – 必須ではありません。 アサーション エラーを説明するメッセージです。 


## <a name="examples"></a>例

```Assert(lblResult.Text = "Success", "lblResult value Expected : Success , Actual : " & lblResult.Text)```<br>
```Assert(ListBox1.Selected.Value = "Success", "ListBox1 selection Expected : Success,  Actual : " & ListBox1.Selected.Value)```<br>
```Assert(kudosAfterTest = kudosBeforeTest + 1, "Kudos count. Expected : " & kudosBeforeTest + 1  & " Actual :" & kudosAfterTest)```

### <a name="see-also"></a>関連項目

[Test Studio の概要](../test-studio.md) <br>
[Test Studio の操作](../working-with-test-studio.md)
