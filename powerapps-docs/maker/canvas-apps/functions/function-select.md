---
title: Select 関数 | Microsoft Docs
description: Power Apps での Select 関数の構文を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 01/08/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 12e0f7e33487d5a274dea8bf666ed7d539284e92
ms.sourcegitcommit: 6b2961308c41867756ecdd55f55eccbebf70f7f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2020
ms.locfileid: "3307626"
---
# <a name="select-function-in-power-apps"></a>Power Apps の Select 関数
コントロールでのアクションの選択をシミュレートし、**OnSelect** 式を評価します。

## <a name="description"></a>内容
**Select** 関数では、ユーザーがコントロールをクリックまたはタップした場合と同じように、コントロールでのアクションの選択をシミュレートします。 その結果、対象のコントロールでの **OnSelect** 式が評価されます。

**Select** を使用して、アクションの選択を親コントロールに伝達します。 この種類の伝達は、ギャラリーなどでの既定の動作です。 既定では、**[ギャラリー](../controls/control-gallery.md)** コントロールのすべてのコントロールの **OnSelect** プロパティは **Select (Parent)** に設定されています。 これにより、ギャラリー コントロール自体の **OnSelect** プロパティの値を設定でき、ユーザーがギャラリーのどこをクリックまたはタップしたかにかかわらず、その計算式が評価されます。

ギャラリーの 1 つ以上のコントロールでギャラリー自体とは異なるアクションを実行させる場合、それらのコントロールの **OnSelect** プロパティを既定値以外に設定します。 ギャラリー自体と同じアクションを実行させる場合は、ギャラリーのほとんどのコントロールの **OnSelect** プロパティを既定値のままにすることができます。

**Select** は、後の処理のために対象の **OnSelect** をキューに入れますが、この動作は現在の式の評価が完了した後で行われる場合があります。 **Select** によって対象の **OnSelect** がすぐに評価されたり、**Select** が **OnSelect** の評価の完了まで待機したりすることはありません。

複数の画面で **Select** を使用することはできません。

**Select** は、**OnSelect** プロパティを持つコントロールと共にのみ使用できます。

**Select** は、[動作の数式](../working-with-formulas-in-depth.md) でのみ使用できます。

コントロールが直接、または他のコントロールを通じて間接的に、自身を **Select** することはできません。

Select 関数はギャラリーでも使用できます。 たとえば、ギャラリーで選択する行または列や、ギャラリーのその行または列で選択するためのコントロールを指定するために使用できます。 行または列を選択すると、ギャラリーの選択が変更され、ギャラリー コントロールの **OnSelect** 式が評価されます。 行または列内のコントロールが指定されている場合は、子コントロールの **OnSelect** 式が評価されます。 

## <a name="syntax"></a>構文
**Select**(*コントロール*)

* *コントロール* – 必須。  ユーザーの代理として選択するコントロール。

**Select**( *Control, Row or column, Child Control* )

- *コントロール* – 必須。 ユーザーの代理として選択するコントロール。
- *行または列* – 必須ではありません。 ユーザーの代わりに選択するギャラリー コントロールの行または列の数 (1 から開始)。
- *子コントロール* - 必須ではありません。 「コントロール」パラメーターで識別されるコントロールの子コントロールを選択します。 

## <a name="examples"></a>例

- *ボタン*

    ```Select(button1)```

- *ギャラリー* 

    ```Select(Gallery1, 1)```

    ユーザーによる Gallery1 での行 1 または列 1 の選択をシミュレートします。 

- *ギャラリー* 

    ```Select(Gallery1, 1, ChildControl1)```

    ユーザーによる Gallery1 の行 1 または列 1 の ChildConttrol1 の選択をシミュレートします。

#### <a name="basic-usage"></a>基本的な使用方法

1. **[Button](../controls/control-button.md)** コントロールを追加し、別の名前になっている場合は **Button1** に名前を変更します。

1. **Button1** の **OnSelect** プロパティを次の数式に設定します。

    **Notify( "Hello World" )**

1. 同じ画面で、2 つ目の **Button** コントロールを追加し、その **OnSelect** プロパティを次の数式に設定します。

    **Select( Button1 )**

1. Alt キーを押しながら 2 つ目のボタンを選択します。

    通知がアプリケーションの上部に表示されます。 この通知を生成したのは、**Button1** の **OnSelect** プロパティです。

    ![2 つのボタンの OnSelect プロパティの設定と、2 つ目のボタンがクリックされたときの通知を示すアニメーション](media/function-select/basic-select.gif)

#### <a name="gallery-control"></a>ギャラリー コントロール

1. 他のコントロールを含む垂直方向の**[ギャラリー](../controls/control-gallery.md)** コントロールを追加します。

    ![コントロールを含む垂直方向のギャラリーを選択](media/function-select/select-gallery.png)

2. ギャラリーの **OnSelect** プロパティを次の計算式に設定します。
 
    **Notify( "Gallery Selected" )**

3. Alt キーを押しながら、ギャラリーの背景かギャラリー内のコントロールをクリックまたはタップします。

    すべてのアクションで、アプリケーションの上部に **Garllery Selected** 通知が表示されます。

    ギャラリーの **OnSelect** プロパティを使用して、ユーザーがギャラリーの項目をクリックまたはタップしたときに実行する既定のアクションを指定します。

5. 画像コントロールの **OnSelect** プロパティを次の計算式に設定します。

    **Notify( "Image Selected", Success )**

6. Alt キーを押しながら、ギャラリーのさまざまな要素をクリックまたはタップします。

    画像以外のギャラリーのコントロールをクリックまたはタップすると、前と同様に **Gallery Selected** が表示されます。 画像をクリックまたはタップすると、**Image Selected** が表示されます。
 
    ギャラリーで個々のコントロールを使用して、ギャラリーの既定のアクションとは異なるアクションを実行させます。

    ![ギャラリー コントロールの OnSelect プロパティの既定値と、異なるアクションを実行するコントロールを示すアニメーション](media/function-select/gallery-select.gif)

7. 同じ画面で、**ボタン** コントロールを追加し、その **OnSelect** プロパティを次の数式に設定します。

    **Select( Gallery1,2,Image1 )**

8. Alt キーを押しながら、ボタンを選択します。
   
     **Image Selected** 通知がアプリの上部に表示されます。 ボタンのクリックで、ギャラリーの行 2 のイメージの選択がシミュレートされました。  

