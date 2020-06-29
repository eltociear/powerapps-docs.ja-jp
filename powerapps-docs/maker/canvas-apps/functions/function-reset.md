---
title: Reset 関数 | Microsoft Docs
description: Power Apps での Reset 関数の構文と例を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 07/06/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 20109be5e9c77af75409973a32fe46c353d57282
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3304705"
---
# <a name="reset-function-in-power-apps"></a>Power Apps の Reset 関数
ユーザーによる変更を破棄して、コントロールを既定値にリセットします。  

## <a name="description"></a>内容
**Reset** 関数は、コントロールを **Default** プロパティの値にリセットします。  ユーザーによる変更は破棄されます。

[**ギャラリー**](../controls/control-gallery.md) または [**編集フォーム**](../controls/control-form-detail.md) コントロール内のコントロールは、そのコントロールの外部からはリセットできません。  同じギャラリーまたはフォーム内なら、コントロールの数式でコントロールをリセットできます。  [**ResetForm**](function-form.md) 関数を使用して、フォーム内のすべてのコントロールをリセットすることもできます。 

**Reset** 関数を使用することは、入力コントロールの **Reset** プロパティを切り替えるための代替手段であり、一般的に好まれるやり方です。  **Reset** プロパティは、複数の数式で多くのコントロールをまとめてリセットする必要がある場合に適した方法です。  **Reset** プロパティの切り替えは、[**ボタン**](../controls/control-button.md) コントロールで **Reset = Button.Pressed** という数式を使用することにより、または変数で **Reset = MyVar** の **MyVar** を **Button.OnSelect = Set( MyVar, true ); Set( MyVar, false )** という数式を使用して切り替えることにより、行うことができます。    

**Default** プロパティが変更されると、入力コントロールもリセットされます。

**Reset** には戻り値が存在せず、[動作の数式](../working-with-formulas-in-depth.md) 内でのみ使用できます。

## <a name="syntax"></a>構文
**Reset**( *Control* )

* *コントロール* – 必須。 リセットするコントロール。

## <a name="example"></a>例
1. **テキスト入力**コントロールを画面に挿入します。  既定では、コントロール名は **TextInput1** になり、**Default** プロパティは **"Text input"** に設定されます。
2. テキスト ボックスに新しい値を入力します。  
3. **ボタン** コントロールを画面に挿入します。
4. ボタンの **OnSelect** プロパティを **Reset( TextInput1 )** に設定します。
5. ボタンを選択します。  コントロールを最後まで選択して作成している場合でも、ボタンを選択できます。
6. テキスト ボックスの内容が **Default** プロパティの値に戻ります。

