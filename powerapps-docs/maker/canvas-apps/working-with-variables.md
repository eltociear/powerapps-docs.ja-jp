---
title: キャンバス アプリの変数について | Microsoft Docs
description: キャンバス アプリの状態、コンテキスト変数、およびコレクションを操作するための参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 02/07/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d7fb0e386309f207809204d4f9f582aa3aedfe7e
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/13/2020
ms.locfileid: "3308776"
---
# <a name="understand-canvas-app-variables-in-power-apps"></a>Power Apps のキャンバス アプリ変数について

Visual Basic や JavaScript などの他のプログラミング ツールを使用したことがある場合、**変数はどこにあるのか?** という疑問を抱くことでしょう。 Power Apps は少し異なるので、別のアプローチが必要です。 キャンバス アプリをビルドする際に、変数の説明に進む代わりに、**Excel で何をしようとしているか?** を考えます。

他のツールでは、明示的に計算を実行し、その結果を変数に格納していたことでしょう。 しかし、Power Apps と Excel のどちらも、入力データが変更されると自動的に計算式が再計算されるので、通常は変数を作成したり更新したりする必要はありません。 可能な限りこの方法に従うことで、アプリをより簡単に作成、理解、維持することができます。

場合によっては Power Apps で変数を使用する必要があります。これにより[動作の数式](working-with-formulas-in-depth.md) を追加して Excel のモデルを拡張します。 これらの計算式が実行されるのは、ユーザーがボタンを選択したときなどです。 動作の数式の中では、他の計算式で使用する変数を設定すると便利なことがよくあります。

一般的には、変数の使用を避けてください。 ただし、変数を使わないと目的の動作が得られないこともあります。 変数は、値を設定する関数に表示されるとき、暗黙的に作成および型指定されます。 

## <a name="translate-excel-into-power-apps"></a>Excel を Power Apps に変換する

### <a name="excel"></a>Excel

それでは、Excel のしくみを確認しましょう。 セルには、数値や文字列などの値、または他のセルの値に基づく計算式を含めることができます。 ユーザーがセルに別の値を入力すると、新しい値に応じてすべての計算式が自動的に再計算されます。 この動作を実現するためにプログラミングは必要ありません。

次の例では、セル **A3** が計算式 **A1+A2** に設定されています。 もし **A1** または **A2** を変更するなら、**A3** は変更を反映するために自動的に再計算されます。 この動作では、計算式自体の外部でコーディングする必要はありません。

![2 つの数値の合計を再計算する Excel のアニメーション](media/working-with-variables/excel-recalc.gif)

Excel には変数がありません。 計算式が含まれるセルの値は入力内容に基づいて変化しますが、計算式の結果を記憶してそれをセルや他の場所に格納する方法はありません。 セルの値を変更すると、スプレッドシート全体が変更される可能性があり、それ以前に計算された値はすべて失われます。 Excel のユーザーは、セルをコピーして貼り付けることができますが、それはユーザーが手動で制御するものであり、計算式では不可能です。

### <a name="power-apps"></a>Power Apps

Power Apps で作成したアプリは、Excel とほぼ同じように動作します。 セルを更新する代わりに、画面上の任意の場所にコントロールを追加し、計算式で使用するために名前を付けることができます。

たとえば、**Label1** という名前の**[ラベル](controls/control-text-box.md)** コントロールに加えて、**TextInput1** と **TextInput2** という名前の 2 つの**[テキスト入力](controls/control-text-input.md)** コントロールを追加することで、アプリで Excel の動作を複製できます。 その後 **Label1** の **[Text](controls/properties-core.md)** プロパティを **TextInput1 + TextInput2** に設定すると、**TextInput1** と **TextInput2** に含まれているすべての数値の合計が自動的に表示されます。

![Power Apps で 2 つの数値の合計を計算する](media/working-with-variables/recalc1.png)

**Label1** コントロールが選択されていて、**[テキスト](controls/properties-core.md)** 式が画面上部の数式バーに表示されていることに注意してください。 ここで、計算式が **TextInput1 + TextInput2** となっていることがわかります。 Excel ワークブック内のセル間に依存関係が作成されるのと同様に、この計算式によってこれらのコントロール間に依存関係が作成されます。  **TextInput1** の値を変更してみましょう。

![Power Apps で 2 つの数値の合計を再計算するアニメーション](media/working-with-variables/recalc2.gif)

**Label1** の計算式が自動的に再計算され、新しい値が表示されます。

Power Apps では、計算式を使用して、コントロールのプライマリ値だけでなく、書式設定などのプロパティも決定できます。 次の例では、ラベルの **[Color](controls/properties-color-border.md)** プロパティに設定された計算式により、負の値は自動的に赤で表示されます。 **[If](functions/function-if.md)** 関数は Excel と非常によく似ています。

`If( Value(Label1.Text) < 0, Red, Black )`

![条件付き書式のアニメーション](media/working-with-variables/recalc-color.gif)

計算式は、さまざまなシナリオで利用できます。

* デバイスの GPS を使用した場合、**Location.Latitude** と **Location.Longitude** を使用する計算式によって、マップ コントロールに現在の位置を表示できます。  移動すると、マップによって位置が自動的に追跡されます。
* 他のユーザーが[データ ソース](working-with-data-sources.md) を更新できます。  たとえば、チームの他のメンバーが SharePoint リスト内の項目を更新する場合があります。  データ ソースを更新すると、依存するすべての計算式が自動的に再計算され、更新されたデータが反映されます。 この例をさらに進めて、ギャラリーの **[Items](controls/properties-core.md)** プロパティを計算式 **Filter( SharePointList )** に設定すると、新しくフィルター処理された[レコード](working-with-tables.md#records) セットが自動的に表示されます。

### <a name="benefits"></a>給付金

計算式を使用するアプリの作成には多くの利点があります。

* Excel を知っていれば Power Apps もわかります。 モデルと計算式の言語は同じです。
* 別のプログラミング ツールを使用したことがある場合、これらの例を実現するためにどれだけの量のコードが必要になるかを考えてみてください。  Visual Basic では、各テキスト入力コントロールの変更イベント用にイベント ハンドラーを記述する必要があります。  このそれぞれで計算を実行するコードは冗長であり、不一致が生じる可能性がありますし、また、共通のサブルーチンを記述することが必要になる場合もあります。  Power Apps では、1 行の計算式 1 つでこのすべての処理を実行しました。
* **Label1** のテキストがどこから取得されるかを理解するために、**[Text](controls/properties-core.md)** プロパティの計算式を正確に調べます。  ほかに、このコントロールのテキストを変更する方法はありません。  従来のプログラミング ツールでは、プログラムのどこからでも、任意のイベント ハンドラーまたはサブルーチンでラベルの値を変更できました。  これにより、変数がいつどこで変更されたかを追跡するのが難しくなります。
* ユーザーは、スライダー コントロールを変更した後に考えを変えた場合、スライダーを元の値に戻すことができます。  アプリでは以前と変わらず同じコントロールが表示されるため、まるで何も変わっていないかのように見えます。  「what if」を試したり要求したりした場合でも、Excel の場合と同様、派生的な問題は発生しません。  

一般的に、計算式を使用して効果を得ることができれば楽になります。 Power Apps の計算式エンジンをうまく利用しましょう。  

## <a name="know-when-to-use-variables"></a>変数を使用するタイミングを把握する

単純な加算器に変更を加えて、累計機能を備えた昔ながらの計算機のように動作するようにしましょう。 **追加**ボタンを選択すると、数値が累計に加算されます。 **クリア** ボタンを選択すると、累計が 0 にリセットされます。

| 表示 | 内容 |
|----|----|
| <style> img { max-width: none } </style> ![テキスト入力コントロール、ラベルおよび 2 つのボタンを使用したアプリ](media/working-with-variables/button-changes-state-1.png) | アプリが起動すると、累計は 0 になります。<br><br>赤い点は、ユーザーが **77** を入力したテキスト入力ボックス内のユーザーの指を表します。 |
| ![テキスト入力コントロールに 77 が含まれていて、追加ボタンが押されている](media/working-with-variables/button-changes-state-2.png) | ユーザーは**追加**ボタンを選択します。 |
| ![合計は 77 で、さらに 77 が追加されます](media/working-with-variables/button-changes-state-3.png) | 累計に 77 が追加されます。<br><br>ユーザーは**追加**ボタンを選択します。 |
| ![クリアされる前の合計は 154 です。](media/working-with-variables/button-changes-state-4.png) | 77 が累計に再び追加され、結果は154 になります。<br><br>ユーザーは**クリア** ボタンを選択します。 |
| ![合計がクリアされます。](media/working-with-variables/button-changes-state-5.png) | 累計は 0 にリセットされます。 |

ここで作成する計算機では、Excel に存在しない機能であるボタンを使用しています。 このアプリでは、値はユーザーが行う一連の操作によって異なるので、計算式だけを使用して累計を計算することはできません。 代わりに、累計を手動で記録して更新する必要があります。 ほとんどのプログラミング ツールでは、この情報を*変数*に格納します。

場合によっては、アプリが目的の動作を行うために変数が必要になります。  ただし、このアプローチには注意が必要です。

* 累計を手動で更新する必要があります。 この処理は自動再計算では実行されません。
* 累計は、他のコントロールの値に基づいて計算できません。 累計は、ユーザーが**追加**ボタンを選択した回数と、選択したときにテキスト入力コントロールに格納されていた値に依存します。 ユーザーが 77 を入力した後で **追加** を 2 回選択したのか、それとも加算する値に 24 と 130 を指定したのでしょうか? 合計が 154 になった後でその違いを見分けることはできません。
* 合計に対する変更は、異なる経路から生じている可能性があります。 この例では、**追加**ボタンでも**クリア** ボタンでも合計を更新できます。 アプリが期待どおりに動作しない場合、どちらかのボタンに問題の原因があるのでしょうか?

## <a name="use-a-global-variable"></a>グローバル変数を使用する

計算機を作成するには、累計を保持する変数が必要です。 Power Apps で使用できる最も単純な変数は、*グローバル変数*です。  

グローバル変数は次のように機能します。

* **[Set](functions/function-set.md)** 関数を使用して、グローバル変数の値を設定します。  **Set( MyVar, 1 )** では、グローバル変数 **MyVar** の値を **1** に設定します。
* **Set** 関数とともに使用した名前を参照すると、グローバル変数を使用できます。  この場合、**MyVar** は **1** を返します。
* グローバル変数は、文字列、数値、レコード、[テーブル](working-with-tables.md) など、すべての値を保持できます。

それでは、グローバル変数を使用して計算機を作り直してみましょう。

1. **TextInput1** という名前のテキスト入力コントロールと、**Button1**  および  **Button2** という名前の 2 つのボタンを追加します。

2. **Button1** の **[Text](controls/properties-core.md)** プロパティを **"Add"** に設定し、**Button2** の **Text** プロパティを **"Clear"** に設定します。

3. ユーザーが**追加**ボタンを選択して累計を更新するために、**[OnSelect](controls/properties-core.md)** プロパティを次の計算式に設定します。

    **Set( RunningTotal, RunningTotal + TextInput1 )**

    この計算式が単に存在する場合、**+** 演算子により、**RunningTotal** の数値を保持するグローバル変数として設定します。 **RunningTotal** をアプリの任意の場所で参照できます。 ユーザーがこのアプリを開くたびに、**RunningTotal** の初期値は*空白*となります。

    ユーザーが最初に**追加**ボタンを選択し、**[Set](functions/function-set.md)** を実行すると、**RunningTotal** は **RunningTotal + TextInput1** の値に設定されます。

    ![追加ボタンの OnSelect プロパティを Set 関数に設定する](media/working-with-variables/global-variable-1.png)

4. ユーザーが**クリア** ボタンを選択して累計を **0** に設定するために、**[OnSelect](controls/properties-core.md)** プロパティを次の計算式に設定します。

    **Set( RunningTotal, 0 )**

    ![クリア ボタンの OnSelect プロパティを Set 関数に設定する](media/working-with-variables/global-variable-2.png)

5. **[ラベル](controls/control-text-box.md)** コントロールを追加し、**[Text](controls/properties-core.md)** プロパティを **RunningTotal** に設定します。

    この計算式は自動的に再計算され、ユーザーが選択したボタンに基づいて変更される **RunningTotal** の値が表示されます。

    ![ラベルの Text プロパティは変数の名前に設定される](media/working-with-variables/global-variable-3.png)

6. アプリをプレビューし、上記のように計算機が完成しました。 テキスト ボックスに数値を入力して**追加**ボタンを数回クリックします。 準備ができたら、Esc キーを押して作成環境に戻ります。

    ![テキスト入力コントロールは値を示し、ラベルは累計を示します](media/working-with-variables/global-variable-4.png)

7. グローバル変数の値を表示するには、**ファイル** メニューを選択して、左側のウィンドウにある**変数**を選択します。

    ![ファイル メニューの変数オプション](media/working-with-variables/global-variable-file-1.png)

8. 変数がどこで定義され使用されているかを表示するには、その変数を選択します。

    ![変数が使用される場所のリスト](media/working-with-variables/global-variable-file-2.png)

## <a name="types-of-variables"></a>変数の種類

Power Apps には 3 種類の変数があります。

| 変数の種類 | Scope | 内容 | 確立する関数 |
| --- | --- | --- | --- |
| グローバル変数 |App |使い方が最も単純です。 数値、テキスト文字列、ブール値、レコード、テーブルなどを保持し、アプリ内のどこからでも参照できます。 |[**Set**](functions/function-set.md) |
| コンテキスト変数 |画面 |他の言語のプロシージャにパラメーターを渡す場合など、画面に値を渡すのに最適です。 1 つの画面からのみ参照できます。 |[**UpdateContext**](functions/function-updatecontext.md)<br>[**Navigate**](functions/function-navigate.md) |
| コレクション |App |アプリ内のどこからでも参照できるテーブルを保持します。 全体として設定するのではなく、テーブルのコンテンツごとに変更できます。 後で使用するためにローカル デバイスに保存できます。 |[**Collect**](functions/function-clear-collect-clearcollect.md)<br>[**ClearCollect**](functions/function-clear-collect-clearcollect.md) |

## <a name="create-and-remove-variables"></a>変数の作成と削除

**Set**、**UpdateContext**、**Navigate**、**Collect**、または **ClearCollect** 関数で表示される場合、すべての変数は暗黙的に作成されます。 変数とその型を宣言するには、アプリ内の任意の場所でこれらの関数のいずれかにそれを含める必要があります。 これらの関数はいずれも変数を作成しません。変数に値を入力するだけです。 別のプログラミング ツールの場合のように変数を明示的に宣言することはなく、すべての型指定は使用方法から暗黙的に行われます。

たとえば **OnSelect** 式が **Set( X, 1 )** と等しいボタン コントロールがあるとします。 この計算式は、数値型の変数として **X** を確立します。 計算式で **X** を数値として使用し、ボタンを選択する前、アプリを開いた後にその変数の値は*空白*値となります。 ボタンを選択すると、**X** の値は **1** になります。

別のボタンを追加して、**OnSelect** プロパティを **Set (X、"Hello")** に設定すると、型 (テキスト文字列) が以前の **Set** (数値) の型と一致しないためにエラーが発生します。 変数のすべての暗黙的な定義は、型に同意する必要があります。 この場合も、計算式内で **X** に言及したからであり、これらの計算式のいずれかが実際に実行されたためではありません。

変数を削除するには、暗黙的に変数を確立する **Set**、**UpdateContext**、**Navigate**、**Collect**、**ClearCollect** をすべて削除します。 これらの関数がない場合、変数は存在しません。 変数への参照も、エラーが発生するため削除する必要があります。

## <a name="variable-lifetime-and-initial-value"></a>変数の有効期間と初期値

アプリの実行中、すべての変数がメモリに保持されています。 アプリを閉じると、変数に保持されていた値は失われます。

**Patch** 関数または **Collect** 関数を使用して、データ ソースに変数の内容を格納できます。 [**SaveData**](functions/function-savedata-loaddata.md) 関数を使用して、ローカル デバイスのコレクションに値を格納することもできます。

ユーザーがアプリを開くと、すべての変数の初期値は*空白*になります。

## <a name="reading-variables"></a>変数の読み取り

変数の名前を使用してその値を読み取ります。 たとえば、次の計算式で変数を定義できます。

`Set( Radius, 12 )`

次に、数値を使用できる場所ならどこでも **Radius** を使用でき、**12** に置き換えることができます。

`Pi() * Power( Radius, 2 )`

コンテキスト変数にグローバル変数またはコレクションと同じ名前を付けると、コンテキスト変数が優先されます。 ただし、[曖昧性除去演算子](functions/operators.md#disambiguation-operator) **[@Radius]** を使用すると、グローバル変数またはコレクションを引き続き参照できます。

## <a name="use-a-context-variable"></a>コンテキスト変数を使用する

グローバル変数の代わりにコンテキスト変数を使用した計算機の作成方法を説明します。

コンテキスト変数のしくみは次のとおりです。

* コンテキスト変数を暗黙的に確立および設定するには、**[UpdateContext](functions/function-updatecontext.md)** 関数または **[Navigate](functions/function-navigate.md)** 関数を使用します。 アプリが起動すると、すべてのコンテキスト変数の初期値は*空白*になります。
* コンテキスト変数は、レコードを使用して更新します。 他のプログラミング ツールでは、一般的に、「x = 1」のように、代入には「=」を使用します。 コンテキスト変数の場合は、代わりに **{ x: 1 }** を使用します。 コンテキスト変数を使用する場合は、レコード構文なしで直接その名前を使用します。
* **[Navigate](functions/function-navigate.md)** 関数を使用して画面を表示する場合は、コンテキスト変数を設定することもできます。 画面が一種のプロシージャまたはサブルーチンと考えられる場合、この方法は他のプログラミング ツールでのパラメーターの引き渡しに似ています。
* **[Navigate](functions/function-navigate.md)** を除き、コンテキスト変数は、名前を取得する場所である単一の画面のコンテキストに制限されます。 このコンテキスト以外でコンテキスト変数を使用または設定することはできません。
* コンテキスト変数では、文字列、数値、レコード、[テーブル](working-with-tables.md) など、任意の値を保持できます。

それでは、コンテキスト変数を使用して計算機を作り直してみましょう。

1. **TextInput1** という名前のテキスト入力コントロールと、**Button1**  および  **Button2** という名前の 2 つのボタンを追加します。

2. **Button1** の **[Text](controls/properties-core.md)** プロパティを **"Add"** に設定し、**Button2** の **Text** プロパティを **"Clear"** に設定します。

3. ユーザーが**追加**ボタンを選択して累計を更新するために、**[OnSelect](controls/properties-core.md)** プロパティを次の計算式に設定します。

    **UpdateContext( { RunningTotal: RunningTotal + TextInput1 } )**

    この計算式が単に存在する場合、**+** 演算子により、数値を保持するコンテクスト変数として **RunningTotal** を設定します。 **RunningTotal** をこの画面の任意の場所で参照できます。 ユーザーがこのアプリを開くたびに、**RunningTotal** の初期値は*空白*となります。

    ユーザーが **追加**ボタンと **[UpdateContext](functions/function-updatecontext.md)** を初めて選択するときに、**RunningTotal** は **RunningTotal + TextInput1** の値に設定されます。

    ![追加ボタンの OnSelect プロパティ](media/working-with-variables/context-variable-1.png)

4. ユーザーが**クリア** ボタンを選択して累計を **0** に設定するために、**[OnSelect](controls/properties-core.md)** プロパティを次の計算式に設定します。

    **UpdateContext( { RunningTotal: 0 } )**

    ここでも、**[UpdateContext](functions/function-updatecontext.md)** を計算式 **UpdateContext( { RunningTotal: 0 } )** で使用します。

    ![クリア ボタンの OnSelect プロパティ](media/working-with-variables/context-variable-2.png)

5. **[ラベル](controls/control-text-box.md)** コントロールを追加し、**[Text](controls/properties-core.md)** プロパティを **RunningTotal** に設定します。

    この計算式は自動的に再計算され、ユーザーが選択したボタンに基づいて変更される **RunningTotal** の値が表示されます。

    ![ラベルの Text プロパティ](media/working-with-variables/context-variable-3.png)

6. アプリをプレビューすると、上記のように計算機が完成しました。 テキスト ボックスに数値を入力して**追加**ボタンを数回クリックします。 準備ができたら、Esc キーを押して作成環境に戻ります。

    ![テキスト入力コントロールは値を示し、ラベルは累計を示します](media/working-with-variables/context-variable-4.png)

7. 画面に移動する際にコンテキスト変数の値を設定できます。 これはある画面から別の画面に「コンテキスト」または「パラメーター」を渡すのに役立ちます。 このテクニックを説明するには、画面を挿入し、ボタンを挿入して、**OnSelect** プロパティをこの計算式に設定します。

    **Navigate( Screen1, None, { RunningTotal: -1000 } )**

    ![ボタンの OnSelect プロパティ](media/working-with-variables/context-variable-5.png)

    Alt キーを押したままこのボタンを選択して**Screen1** を表示し、コンテキスト変数 **RunningTotal** を -1000 に設定します。

    ![Screen1 が開いている](media/working-with-variables/context-variable-6.png)

8. コンテキスト変数の値を表示するには、**ファイル** メニューを選択して、左側のウィンドウで**変数**を選択します。

    ![ファイル メニューの変数オプション](media/working-with-variables/context-variable-file-1.png)

9. コンテキスト変数が定義され使用される場所を表示するには、そのコンテキスト変数を選択します。

    ![変数が使用される場所のリスト](media/working-with-variables/context-variable-file-2.png)

## <a name="use-a-collection"></a>コレクションの使用

最後に、コレクションを使用した計算機の作成方法を説明します。  コレクションは、変更が容易なテーブルを保持しているため、この計算機に値が入力されたときに、それぞれの値を「紙テープ」に記録するようにします。

コレクションのしくみは次のとおりです。

* コレクションを作成および設定するには、**[ClearCollect](functions/function-clear-collect-clearcollect.md)** 関数を使用します。  代わりに **[Collect](functions/function-clear-collect-clearcollect.md)** 関数を使用できますが、実質的には、古い変数を置き換えるのではなく別の変数が必要になります。  
* コレクションは一種のデータ ソース、すなわちテーブルです。 コレクションの単一の値にアクセスするには、**[First](functions/function-first-last.md)** 関数を使用し、結果のレコードから 1 つのフィールドを抽出します。 **[ClearCollect](functions/function-clear-collect-clearcollect.md)** で単一の値を使用した場合、これは次の例のように **Value** フィールドになります。<br>
**First(** *VariableName* **).Value**

コレクションを使用して計算機を作り直してみましょう。

1. **TextInput1** という名前の**[テキスト入力](controls/control-text-input.md)** コントロールと、**Button1** および **Button2** という名前の 2 つのボタンを追加します。

2. **Button1** の **[Text](controls/properties-core.md)** プロパティを **「Add」** に設定し、**Button2** の **Text** プロパティを**Clear**に設定します。

3. ユーザーが**追加**ボタンを選択して累計を更新するために、**[OnSelect](controls/properties-core.md)** プロパティを次の計算式に設定します。

    **Collect( PaperTape, TextInput1.Text )**

    この計算式が単に存在する場合、 **PaperTape** をテキスト文字列の単一列テーブルを保持するコレクションとして確立します。 **PaperTape** をこのアプリの任意の場所で参照できます。 ユーザーがこのアプリを開くたびに、**PaperTape** は空のテーブルになります。

    この計算式を実行すると、コレクションの末尾に新しい値が追加されます。 1 つの値を追加しているため、**Collect** によってその値は単一列テーブルに自動的に配置され、 列の名前は **Value** になります。この値は後で使用します。

    ![追加ボタンの OnSelect プロパティ](media/working-with-variables/papertape-1.png)

4. ユーザーが **クリア** ボタンを選択したときに紙テープを消去するには、**[OnSelect](controls/properties-core.md)** プロパティを次の計算式に設定します。

    **Clear( PaperTape )**

    ![クリア ボタンの OnSelect プロパティ](media/working-with-variables/papertape-2.png)

5. 累計を表示するために、ラベルを追加し、**[Text](controls/properties-core.md)** プロパティを次の計算式に設定します。

    **Sum( PaperTape, Value )**

    ![ラベルの Text プロパティ](media/working-with-variables/papertape-3.png)

6. 計算機を実行するために、F5 キーを押してプレビューを開き、テキスト入力コントロールに数値を入力して、ボタンを選択します。

    ![テキスト入力コントロールは値を示し、ラベルは累計を示します](media/working-with-variables/papertape-run-1.png)

7. 既定のワークスペースに戻るには、Esc キーを押します。

8. 紙テープを表示するには、**データ テーブル** コントロールを挿入し、その **[Items](controls/properties-core.md)** プロパティを次の計算式に設定します。

    **PaperTape**

    右側のウィンドウで、**値**列を選択し、表示します。

    ![コレクションに追加された値を示すデータ テーブル](media/working-with-variables/papertape-4.png)

9. コレクション内の値を確認するために、**ファイル** メニューの**コレクション**を選択します。

    ![PaperTape コレクションのプレビュー](media/working-with-variables/papertape-file.png)

10. コレクションを保存したり取得したりするには、さらに 2 つのボタン コントロールを追加し、その **Text** プロパティを**読み込み**と**保存**にします。 **読み込み**ボタンの **OnSelect** プロパティを次の計算式に設定します。

     **Clear( PaperTape ); LoadData( PaperTape, "StoredPaperTape", true )**

     **LoadData** によって格納された値はコレクションの末尾に追加されるため、最初にコレクションをクリアする必要があります。

     ![Load ボタンの OnSelect プロパティ](media/working-with-variables/papertape-5.png)

11. **保存**ボタンの **OnSelect** プロパティを次の計算式に設定します。

     **SaveData( PaperTape, "StoredPaperTape" )**

     ![保存ボタンの OnSelect プロパティ](media/working-with-variables/papertape-6.png)

12. F5 キーを押してもう一度プレビューを表示し、テキスト入力コントロールに数値を入力してボタンを選択します。 **保存**ボタンを選択します。 アプリを閉じて再読み込みし、**読み込み**ボタンを選択してコレクションを再読み込みします。

> [!NOTE]
> **SaveData** と **LoadData** 関数は Power Apps モバイルで使用できますが、Power Apps Studio または Power Apps のWeb プレーヤーでは使用できません。