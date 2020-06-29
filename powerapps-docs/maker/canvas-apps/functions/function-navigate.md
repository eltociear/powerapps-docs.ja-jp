---
title: Back および Navigate 関数 | Microsoft Docs
description: Power Apps での Navigate および Back 関数の構文と例を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/07/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 52687996c29c488b49b46616e095a03fbb90ad01
ms.sourcegitcommit: 8e76afb331745f1da929a39e831634680dfa6008
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2020
ms.locfileid: "3347028"
---
# <a name="back-and-navigate-functions-in-power-apps"></a>Power Apps の Back および Navigate 関数

表示される画面を変更します。

## <a name="overview"></a>概要

ほとんどのアプリには、複数の画面が含まれます。  **Back** および **Navigate** 関数を使用して、表示する画面を変更します。 たとえば、ユーザーがボタンを選択したときに別の画面を表示する場合は、**Navigate** 関数が含まれた数式に、ボタンの **[OnSelect](../controls/properties-core.md)** プロパティを設定します。 その数式では、画面の切り替わり方コントロールするのに、**Fade** などのビジュアルの切り替えを指定することができます。  

**Back** および **Navigate** は、表示される画面のみを変更します。 現在表示されていない画面は、バックグラウンドで引き続き動作します。 他の画面上のコントロールのプロパティを参照する数式を作成できます。 たとえば、いずれかの画面上のスライダーの値を変更した後、数式内でその値を使用する別の画面に移動し、新しい画面にどのように影響するかを決定することができます。 ユーザーは元の画面に戻り、スライダーの値が保持されていることを確認できます。

ユーザーが画面間を移動したとき、[Context 変数](../working-with-variables.md#use-a-context-variable) も保持されます。 **Navigate** を使用して、数式で表示される画面に 1 つ以上のコンテキスト変数を設定できます。これは、画面外からコンテキスト変数を設定する唯一の方法です。 画面にパラメーターを渡すのに、この方法を使用できます。 別のプログラミング ツールを使用した場合、この方法はプロシージャにパラメーターを渡すのに似ています。

いずれかの関数は、[動作の数式](../working-with-formulas-in-depth.md)内でのみ使用できます。

## <a name="navigate"></a>Navigate

最初の引数で、表示する画面の名前を指定します。  

 2 番目の引数で、前の画面がどのように新しい画面に変化するかを指定します:

| 切り替えの引数 | 内容 | デモ |
| --- | --- | --- |
| **ScreenTransition.Cover** |新しい画面は、現在の画面を覆うためにスライドしてビューに表示され、右から左に移動します。 | ![画面切り替えはアニメーションを覆う](media/function-navigate/cover.gif) |
| **ScreenTransition.CoverRight** |新しい画面は、現在の画面を覆うためにスライドしてビューに表示され、左から右に移動します。 | ![画面切り替えは右のアニメーションを覆う](media/function-navigate/coverright.gif) |
| **ScreenTransition.Fade** |現在画面がフェードアウトし、新しい画面が表示されます。 | ![画面切り替えはアニメーションからフェードする](media/function-navigate/fade.gif) |
| **ScreenTransition.None** (既定) |新しい画面は現在の画面をすばやく置き換えます。 | ![画面切り替えはアニメーションを表示しない](media/function-navigate/none.gif) |
| **ScreenTransition.UnCover** | 現在の画面が右から左にスライドして表示されなくなり、新しい画面が表示されます。 | ![画面切り替えはアニメーションを表示する](media/function-navigate/uncover.gif) |
| **ScreenTransition.UnCoverRight** | 現在の画面が左から右にスライドして表示されなくなり、新しい画面が表示されます。 | ![画面切り替えは右のアニメーションを表示する](media/function-navigate/uncoverright.gif) |

**Navigate** を使用して、新しい画面の[コンテキスト 変数](../working-with-variables.md#use-a-context-variable) を作成または更新できます。 省略可能な 3 番目の引数として、[列](../working-with-tables.md#columns) 名としてのコンテキスト変数の名前とコンテキスト変数の新しい値を含む[レコード](../working-with-tables.md#records) を渡します。  このレコードは、**[UpdateContext](function-updatecontext.md)** 関数で使用するレコードと同じです。

前の画面の**[OnHidden](../controls/control-screen.md)** プロパティ、新しい画面の**[OnVisible](../controls/control-screen.md)** プロパティ、あるいはその両方を設定して、切り替え時の追加を変更します。 **App.ActiveScreen** プロパティが更新され、変更が反映されます。

**Navigate** は通常は **true** を返しますが、エラーが発生した場合は **false** を返します。

ナビゲーション用の Context 変数は、[画面間を移動する](../add-screen-context-variables.md#add-navigation) 記事で説明されています。

## <a name="back"></a>Back

**Back** 関数は、最後に表示された画面に戻ります。

各 **Navigate** の呼び出しは、アプリは表示された画面と切り替えを追跡します。 連続する **Back** を呼び出して、ユーザーがアプリを開始したときに表示された画面にすべての方法を返すことができます。

**Back** 関数が実行されると、既定では逆遷移が使用されます。 たとえば、画面が **CoverRight** 遷移を返して表示される場合、**Back** は戻るのに **UnCover** (左にある) を使用します。  **Fade** および **None** は独自の逆です。 特定の遷移を強制するのに、オプションの引数を **Back** に渡します。

**Back** は通常は **true** を返しますが、ユーザーがアプリを起動してから別の画面に移動していない場合は **false** を返します。

## <a name="syntax"></a>構文

**Back** ( [ *遷移* ] )

* *遷移* -任意。 現在の画面と前の画面の間で使うビジュアルの切り替えです。 この記事で既に説明した、この引数の有効な値の一覧を参照してください。 既定では、画面が戻る切り替えは、表示された切り替えの逆になります。

**Navigate**( *Screen* [, *Transition* [, *UpdateContextRecord* ] ] )

* *Screen* - 必須。 表示する画面。
* *遷移* -任意。  現在の画面と次の画面の間で使うビジュアルの切り替えです。 この記事で既に説明した、この引数の有効な値の一覧を参照してください。 既定値は **None** です。
* *UpdateContextRecord* - 省略可能。  1 つ以上の列の名前と、各列に対する値を含んだレコードです。 このレコードは、**[UpdateContext](function-updatecontext.md)** 関数に渡されたときのように、新しい画面の[コンテキスト変数](../working-with-variables.md#use-a-context-variable) を更新します。

## <a name="examples"></a>例

| 計算式 | 内容 | 結果 |
| --- | --- | --- |
| **Navigate( Details )** |切り替えやコンテキスト変数の値の変更なしで **詳細** 画面を表示します。 |**詳細** 画面がすぐに表示されます。 |
| **Navigate( Details, ScreenTransition.Fade )** |**フェード** の切り替えを使って **詳細** 画面を表示します。  コンテキスト変数の値は変更されません。 |現在の画面がフェード アウトして、**詳細** 画面が表示されます。 |
| **Navigate( Details, ScreenTransition.Fade, {&nbsp;ID:&nbsp;12&nbsp;} )** |**フェード** の切り替えを使って **詳細** 画面を表示します。また、**ID** コンテキスト変数の値を **12** に更新します。 |**Details** 画面を表示するのに現在の画面がフェード アウトし、画面上のコンテキスト変数 **ID** が **12** に設定されます。 |
| **Navigate( Details, ScreenTransition.Fade, {&nbsp;ID:&nbsp;12&nbsp;,&nbsp;Shade:&nbsp;Color.Red&nbsp;} )** |**フェード** の切り替えを使って **詳細** 画面を表示します。 コンテキスト変数 **ID** の値を **12** に更新し、コンテキスト変数 **Shade** の値を **Color.Red** に更新します。 |現在の画面がフェード アウトして、**詳細** 画面が表示されます。 **Details** 画面上のコンテキスト変数 **ID** が **12** に設定され、コンテキスト変数 **Shade** が **Color.Red** に設定されます。 **Details** 画面上のコントロールの **Fill** プロパティを **Shade** に設定した場合、そのコントロールは赤色で表示されます。 |
| **Back()** | 既定の戻り値の切り替えを使用して、前の画面を表示します。 | 現在の画面が表示された切り替え効果の逆の切り替えを、前の通して画面を表示します。 |
| **Back( ScreenTransition.Cover )** |  **Cover** 切り替えを使用して、前の画面を表示します。 | 現在の画面が表示された切り替え効果に関係なく、前の画面を **Cover** 切り替えによって表示します。 |

### <a name="step-by-step"></a>ステップ バイ ステップ

1. 空白のアプリを作成します。

1. 2 番目の画面を追加します。

    アプリには 2 つの空白の画面が含まれています: **Screen1** および **Screen2**。

1. **Screen2** の **Fill** プロパティを `Gray` 値に設定します。

1. **Screen2** でボタンを追加し、**[OnSelect](../controls/properties-core.md)** プロパティを次の数式に設定します:

    ```powerapps-dot
    Navigate( Screen1, ScreenTransition.Cover )
    ```

1. **Alt** キーを押しながら、ボタンを選択します。

    左側をカバーする切り替えを通して、白い背景で **Screen1** が表示されます。

1. **Screen1** で、ボタンを追加し、**OnSelect** プロパティを次の数式に設定します:

    ```powerapps-dot
    Back()
    ```

1. **Alt** キーを押しながら、ボタンを選択します。

    2番目の画面は、右側に表示されている切り替え (**Cover** の逆) を通して、背景を灰色で表示します。

1. 各画面のボタンを繰り返し選択して、前後にバウンスします。

[別の例](../add-screen-context-variables.md)

### <a name="see-also"></a>関連項目

[コンテキスト変数の使用](../working-with-variables.md#use-a-context-variable)
