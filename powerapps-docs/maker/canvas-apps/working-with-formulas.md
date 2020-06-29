---
title: キャンバス アプリの数式の使用を始める | Microsoft Docs
description: Power Apps で数式を使用して、キャンバス アプリをカスタマイズします。
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/01/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e2200dece82eea17557de28a64e2bc4d228f4394
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3306936"
---
# <a name="get-started-with-canvas-app-formulas-in-power-apps"></a>Power Apps でキャンバス アプリの数式の使用を始める

(Excel で実行するように) 値を計算してその他のタスクを実行するだけでなく、(アプリが必要とするように) ユーザー入力に応答する数式を使用して、キャンバス アプリを構成します。

* Excel では、たとえばセルに入力しテーブルとグラフを作成する数式を構築します。
* Power Apps では、セルではなくコントロールを構成し、同様の数式を構築します。 さらに、スプレッドシートではなく特定のアプリに適用される数式を構築します。

たとえば、ユーザーがボタンの選択、スライダーの調整、またはその他の入力の指定を実行するときにアプリがどのように応答するかを決定する数式を構築します。 これらの数式により、異なる画面を表示したり、アプリの外部にあるデータ ソースを更新したり、既存のテーブルに存在するデータのサブセットが含まれるテーブルを作成したりできます。

数式は、さまざまなシナリオで利用できます。 たとえば、デバイスの GPS、マップ コントロール、**Location.Latitude** と **Location.Longitude** を使用する数式を使用して、現在の場所を表示できます。 移動すると、マップによって場所が自動的に追跡されます。

このトピックでは、数式に関する作業の概要のみを提供します。 詳細情報や、使用できる関数、演算子、その他の構成要素のリスト全体については、[数式のリファレンス](formula-reference.md)を参照してください。

## <a name="prerequisites"></a>前提条件

* Power Apps に[サインアップ](../signup-for-powerapps.md) し、登録に使用した同じ資格情報を使用して[サインイン](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) します。
* Power Apps で[コントロールを構成する](add-configure-controls.md)方法を説明します。

## <a name="show-a-simple-value"></a>単一の値を表示する

Excel では、**42** という数字や **Hello World** というフレーズなど、特定のデータをセルに打ち込んで入力できます。 このセルには、常に入力したとおりにデータが表示されます。 Power Apps では、同じように変更されないデータを指定できます。このためには、ラベルの **[Text](controls/properties-core.md)** プロパティに目的の一連の文字を二重引用符で囲んで正確に設定します。

1. (画面の左端にある) **ファイル** メニューで**新規**を選択します。
2. **アプリの作成**で、**空のアプリ** タイルの**電話レイアウト**を選択します。

    数式バーは画面の最上部にあります。

    ![数式バー](./media/working-with-formulas/formula-bar.png)

    このバーには、2 つの部分があります:

   * *プロパティの一覧*: 各コントロールと画面には [プロパティのセット](reference-properties.md)があります。  この一覧を使用して特定のプロパティを選択します。  
   * *数式*: このプロパティ用に計算される数式は、[値、演算子、関数](formula-reference.md)で構成されます。

     数式バーでは、選択したコントロール、またはコントロールが選択されていない場合は画面のプロパティを表示して編集できます。  選択されたコントロールの名前は、**コンテンツ** タブで確認できます:

     ![現在選択されたコントロールを表示するコンテンツ バー](./media/working-with-formulas/content-tab-selection.png)

     **コンテンツ** タブで名前をクリックして、選択されているコントロールの名前を変更できます。
3. 画面に **[Label](controls/control-text-box.md)** コントロールを追加します。

    ![追加された TextBox コントロール](./media/working-with-formulas/add-a-label.png)

    ラベルを追加すると、プロパティの一覧に **[Text](controls/properties-core.md)** プロパティが自動的に表示されます。これにより、コントロールに表示されるものを起動させます。 既定では、このプロパティの値は **"Text"** です。  
4. 二重引用符で囲んだ文字列を数式バーに入力することにより、**[Text](controls/properties-core.md)** プロパティの値を **"Hello World"** に設定します。

    ![ラベル "Hello World" を使用する](./media/working-with-formulas/label-hello-world.png)

    入力すると、ラベルにはこの新しい値が反映されます。  入力中に、黄色い感嘆符アイコンが画面に表示される場合があります。 これらのアイコンはエラーを示しますが、有効な値の入力を完了すると、表示されなくなります。 たとえば、両側に二重引用符のない文字列は無効です。

    Excel では、**42** などの数値を表示するには、その数値をセルに入力したり、**=SUM(30,12)** などのその数値を分解する数式を入力したりします。 Power Apps では、ラベルなどのコントロールの **Text** プロパティを **42** または **Sum(30,12)** に設定することで、同じ効果を得ることができます。 ワークシートまたはアプリでの他の変更に関係なく、セルとラベルには常にこの数値が表示されます。

    > [!NOTE]
   > Power Apps では、Excel で実行するように数式の前に等号またはプラス記号を使用することはありません。 数式バーでは、そこに入力したものはすべて既定で数式として処理されます。 さらに、先ほどテキストの文字列を指定したときのように、二重引用符 (") で数式を囲むことはしません。
5. ラベルの **[Text](controls/properties-core.md)** プロパティで、**"Hello World"** を **Sum(1,2,3)** に置き換えます。

    ![部分関数 Sum(1,2,3 を終わりかっこなしで入力すると、エラーが発生します](./media/working-with-formulas/label-sum-partial.png)

    入力中、数式バーはこの関数の説明と必要な引数を表示するのに役立ちます。  **"Hello World"** の末尾の二重引用符と同様に、この数式の末尾のかっこを入力するまで、画面にはエラーを示す黄色い感嘆符が表示されます。

    ![完全な数式 Sum(1,2,3) を使用する](./media/working-with-formulas/label-sum.png)

## <a name="change-a-value-based-on-input"></a>入力に基づいて値を変更する

Excel では、**=A1+A2** とセルに入力すると、セル **A1** と **A2** に含まれる値の合計が表示されます。 これらの値の一方または両方が変更されると、数式が含まれるセルには更新された結果が自動的に表示されます。

![2 つの数値の合計を再計算する Excel のアニメーション](./media/working-with-formulas/excel-recalc.gif)

Power Apps では、コントロールを画面に追加してそのプロパティを設定することで、同様の結果を得ることができます。 この例には、**Label1** と呼ばれるラベル コントロール、および **TextInput1** および **TextInput2** と呼ばれる 2 つの **[Text input](controls/control-text-input.md)** コントロールが表示されます。

![2 つの数値の合計を再計算する Power Apps の図](./media/working-with-formulas/recalc1.png)

テキスト入力コントロールにどのような数値を入力しても、ラベルには常にその数値の合計が表示されます。これは、**[Text](controls/properties-core.md)** プロパティに次の数式が設定されているためです:

`TextInput1 + TextInput2`

![2 つの数値の合計を再計算する Power Apps のアニメーション](./media/working-with-formulas/recalc2.gif)

Excel では、条件付き書式の数式を使用して、たとえば負の値を赤色で表示します。 Power Apps では、計算式を使用して、コントロールのプライマリ値だけでなく、書式設定などのプロパティも決定できます。 次の例では、ラベルの **[Color](controls/properties-color-border.md)** プロパティの数式は、負の値を自動的に赤で表示します。 **[If](functions/function-if.md)** 関数は Excel と非常によく似ています。

`If( Value(Label1.Text) < 0, Red, Black )`

![条件付き書式のアニメーション](media/working-with-variables/recalc-color.gif)

## <a name="change-a-color-based-on-user-input"></a>ユーザー入力に基づいて色を変更する

ユーザーがアプリの外観または動作を変更できるように、数式を使用してアプリを構成できます。 たとえば、フィルターを作成してユーザーが指定するテキストの文字列を含むデータのみを表示したり、データ セット内のある特定の列に基づいて一連のデータをユーザーが並べ替えられるようにしたりできます。 この手順では、1 つ以上のスライダーを調整することにより、ユーザーが画面の色を変更できるようにします。

1. 前の手順からのコントロールを削除するか、前に実行したように空のアプリを作成し、それに 3 つのスライダー コントロールを追加します:

    ![スライダー コントロールの挿入](./media/working-with-formulas/insert-slider.png)
2. 重ならないようにスライダーを配置し、3 つのラベルを追加して、**赤**、**緑**、**青**と表示されるように構成します:

    ![スライダーの配置と各色コンポーネントのラベルの追加](./media/working-with-formulas/three-sliders.png)
3. 各スライダーの **Max** プロパティを 255 に設定します。この値は **[RGBA](functions/function-colors.md)** 関数の色コンポーネントの最大値です。

    **Max** プロパティを**コンテンツ** タブまたはプロパティの一覧で選択することで指定できます:

    ![各スライダーの最大値の変更](./media/working-with-formulas/three-sliders-max.png)
4. 任意のコントロールから離れた場所をクリックして画面を選択してから、画面の **[Fill](controls/properties-color-border.md)** プロパティに次の数式を設定します:<br>**RGBA( Slider1.Value, Slider2.Value, Slider3.Value, 1 )**

    既に説明されているように、**.** 演算子を使用してコントロール プロパティにアクセスします。  **Slider1.Value** は、ユーザーが**最小**値と**最大**値間に配置したスライダーの場所を反映するスライダーの **[Value](controls/properties-core.md)** プロパティを指します。 この数式を入力すると、それに含まれる各コントロールは画面と数式バー間で色分けされます。

    ![画面の背景塗りつぶし色に関する数式の変更 (未完了)](./media/working-with-formulas/three-sliders-partial-rgba.png)

    終わりかっこを入力すると、各スライダーの既定の値 **50** に基づいて、画面の背景が濃い灰色に変わります。 現時点では、数式の入力が完了すると、背景塗りつぶし色の値として計算され使用されます。 プレビューを開く必要なく、既定のワークスペースでアプリを操作できます:

    ![各スライダーの最大値の変更](./media/working-with-formulas/three-sliders-complete-rgba.png)
5. スライダーを調整し、変更が背景色に与える影響を確認します。

    各スライダーを変更すると、**[RGBA](functions/function-colors.md)** 関数を含む数式が再計算され、画面の表示がすぐに変更されます。

    ![画面の背景塗りつぶし色に関する数式の変更 (完了)](./media/working-with-formulas/color-sliders.gif)

## <a name="manage-app-behavior"></a>アプリ動作を管理する

数式は、計算の実行や外観の変更だけでなく、アクションの実行にも利用できます。 たとえば、ボタンの **[OnSelect](controls/properties-core.md)** プロパティを **[Navigate](functions/function-navigate.md)** 関数を含む数式に設定できます。 ユーザーがこのボタンを選択すると、数式で指定する画面が表示されます。

**[Navigate](functions/function-navigate.md)** 関数や **[Collect](functions/function-clear-collect-clearcollect.md)** 関数など一部の関数を、動作の数式でのみ使用できます。  このコンテキスト内のみで関数を使用できる場合、数式のリファレンスが呼び出されます。  

セミコロン (;) で関数を分離する場合、動作の数式で複数のアクションを実行できます。 たとえば、コンテキスト変数を更新し、データ ソースにデータを格納し、最後に別の画面に移動できます。

## <a name="view-a-list-of-properties-by-category"></a>カテゴリ別のプロパティの一覧を表示する

プロパティの一覧では、プロパティがアルファベット順に表示されますが、**表示**タブの**詳細**オプションを選択すると、カテゴリ別に分類されたコントロールのプロパティすべてを表示することもできます。

![詳細ビュー](./media/working-with-formulas/advanced-open.png)

このビュー内で直接数式を編集できます。  ウィンドウの上部にあるコントロール セレクタ―で、操作するコントロールをすばやく見つけることができます。  また、プロパティ検索を使用して、そのコントロールのプロパティをすばやく見つけることができます。

最初に、このビューには最も重要なプロパティが表示されます。  すべてのプロパティを表示するには、ウィンドウの下部にある下向き矢印をクリックします。  各コントロールには、コントロールの動作と外観のあらゆる要素を管理するプロパティの長い一覧があります。 一覧をスクロールしたり、ウィンドウの上部にあるボックスに入力してプロパティを検索したりできます。

## <a name="formula-syntax"></a>数式の構文

数式バーに数式を入力すると、異なる構文要素が異なる色で表示され、読みやすさが向上し、長い数式をより簡単に理解できるようになります。 Power Apps のカラー コードの一覧を示します。

![構文の強調表示](./media/working-with-formulas/syntax-highlighting.png)