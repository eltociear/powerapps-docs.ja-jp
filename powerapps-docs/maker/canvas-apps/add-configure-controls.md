---
title: キャンバス アプリ コントロールを追加および構成する | Microsoft Docs
description: ツールバー、プロパティ タブ、数式バーなどからキャンバス アプリ コントロールを直接追加および構成するための詳細な手順です。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/25/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ae33122d140b6c13f744acb292362d8ec804233e
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3306591"
---
# <a name="add-and-configure-a-canvas-app-control-in-power-apps"></a>Power Apps でキャンバス アプリ コントロールを追加および構成する

キャンバス アプリへのさまざまな UI 要素の追加や、要素の外観と動作の構成を、ツールバー、**プロパティ** タブ、数式バーなどから直接行います。 これらの UI 要素はコントロールと呼ばれ、構成する内容はプロパティと呼ばれます。

## <a name="prerequisites"></a>前提条件

1. Power Apps ライセンスをまだ持っていない場合は、[サインアップ](../signup-for-powerapps.md) した後に[サインイン](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) します。
1. **自分のアプリを作成する**で、**空白の状態からキャンバス アプリを作成**にカーソルを置いて、**このアプリの作成**を選択します。
1. クイック ツアーの開始を求められたら、**次**を選択して Power Apps インターフェイスの基本事項について確認します (または**スキップ**を選択します)。

    クイック ツアーは後からいつでも開始できます。画面の右上隅の疑問符アイコンを選択し、**Take the intro tour (クイック ツアーの開始)** を選択してください。

## <a name="add-and-select-a-control"></a>コントロールの追加および選択

**挿入**タブで、次のいずれかの手順を実行します。

- **ラベル**または**ボタン**を選択して、これらの種類のコントロールを 1 つ追加します。
- コントロールのカテゴリを選択し、追加するコントロールの種類を選択します。

たとえば、**新しいスクリーン**を選択してから**空白**を選択して、アプリに空白のスクリーンを追加します。 (スクリーンは、他の種類のコントロールを含むことができるコントロールの種類です。)

![スクリーンの追加](./media/add-configure-controls/add-screen.png)

新しいスクリーンの名前は **Screen2** で、左側のナビゲーション ウィンドウに表示されます。 このウィンドウには、アプリ内のコントロールの階層一覧が表示されるため、各コントロールを簡単に見つけて選択できます。

![一覧の Screen2](./media/add-configure-controls/list-screen2.png)

この一覧がどのように機能するかを示すには、**挿入**タブの**ラベル**を選択します。新しいコントロールが階層一覧の **Screen2** の下に表示されます。

![一覧の Screen2](./media/add-configure-controls/add-label.png)

スクリーンでは、6 つのハンドルが付いたボックスが既定でラベルを囲んでいます。 その種類のボックスは、選択されたコントロールを囲みます。 スクリーン (ラベルの外側) をクリックまたはタップしてスクリーンを選択すると、ボックスがラベルから消えます。 ラベルを再度選択するには、ラベルをクリックまたはタップするか、コントロールの階層一覧で名前をクリックまたはタップします。

> [!IMPORTANT]
> コントロールを構成する前に、コントロールを選択する必要があります。

## <a name="rename-a-control"></a>コントロール名の変更

コントロールの階層一覧で、名前を変更するコントロールの上にカーソルを置き、表示される省略記号ボタンを選択してから、**名前の変更**を選択します。 次に、一意の覚えやすい名前を入力して、アプリの作成を容易にします。

![コントロール名の変更](./media/add-configure-controls/rename-control.png)

## <a name="delete-a-control"></a>コントロールの削除

コントロールの階層一覧で、削除するコントロールの上にカーソルを置き、表示される省略記号ボタンを選択してから、**削除**を選択します。 スクリーンではないコントロールを削除するには、キャンバスでコントロールを選択してから、 Del キーを押します。

![コントロールの削除](./media/add-configure-controls/delete-control.png)

## <a name="reorder-screens"></a>スクリーンの並べ替え

コントロールの階層一覧で、上または下に移動するスクリーンにカーソルを置いて、表示される省略記号ボタンを選択し、次に**上へ移動**または**下へ移動**を選択します。

![スクリーンの並べ替え](./media/add-configure-controls/reorder-screen.png)

> [!NOTE]
> アプリを開くと、通常、コントロールの階層一覧の一番上のスクリーンが最初に表示されます。 ただし、**[OnStart](controls/control-screen.md)** プロパティを **[Navigate](functions/function-navigate.md)** 関数を含む式に設定して、別のスクリーンを指定することができます。

## <a name="move-and-resize-a-control"></a>コントロールの移動とサイズ変更

コントロールを移動するには、コントロールを選択して、中央にカーソルを合わせ四方向矢印が表示されたら、コントロールを別の場所にドラッグします。

![コントロールの移動](./media/add-configure-controls/move-control.png)

コントロールのサイズを変更するには、コントロールを選択し、選択ボックスのハンドルにカーソルを合わせて両方向矢印を表示してから、ハンドルをドラッグします。

![コントロールの移動](./media/add-configure-controls/resize-control.png)

> [!NOTE]
> 後で説明するように、数式バーの**[X](controls/properties-size-location.md)**、**[Y](controls/properties-size-location.md)**、**[Height](controls/properties-size-location.md)**、および**[Width](controls/properties-size-location.md)** プロパティの任意の組み合わせを変更することで、コントロールを移動してサイズを変更することもできます。

## <a name="change-the-text-of-a-label-or-a-button"></a>ラベルまたはボタンのテキストを変更する

ラベルまたはボタンを選択し、コントロールに表示されるテキストをダブルクリックして、必要なテキストを入力します。

![テキストを変更する](./media/add-configure-controls/change-text.png)

> [!NOTE]
> 後で説明するように、数式バーの **[Text](controls/properties-core.md)** プロパティを変更することによって、このテキストを変更することもできます。

## <a name="configure-a-control-from-the-toolbar"></a>ツールバーからコントロールを構成する

ツールバーからコントロールを構成することにより、コントロールを直接構成する場合よりも幅広いオプションを指定できます。

たとえば、ラベルを選択し、**ホーム** タブを選択して、ラベルのテキストのフォントを変更します。

![フォントの変更](./media/add-configure-controls/change-font.png)

## <a name="configure-a-control-from-the-properties-tab"></a>プロパティ タブでコントロールを構成する

**プロパティ** タブを使用することにより、ツールバーからコントロールを構成する場合よりも幅広いオプションを指定できます。

たとえば、コントロールを選択してから、**Visible** プロパティを変更することで、コントロールを表示または非表示にすることができます。

![表示方法の設定](./media/add-configure-controls/set-visibility.png)

## <a name="configure-a-control-in-the-formula-bar"></a>数式バーでコントロールを構成する

コントロールをツールバーから、または**プロパティ** タブで直接構成する代わりに、プロパティの一覧でプロパティを選択してから数式バーで値を指定すると、コントロールを構成できます。 この方法により、プロパティをアルファベット順に検索したり、より多くの種類の値を指定したりできます。

たとえば、ラベルを選択して、次の方法で構成できます。

- プロパティの一覧の **X** または **Y** を選択してから、数式バーに別の数を指定して、移動します。

    ![X プロパティを設定する](./media/add-configure-controls/x-property.png)

- プロパティの一覧の **X** または **Y** を選択してから、数式バーに別の数を指定して、サイズを変更します。

    ![Height プロパティを設定する](./media/add-configure-controls/height-property.png)

- プロパティの一覧の **Text** を選択してから、数式バーのリテラル文字列、式、または数式の任意の組み合わせを指定することでテキストを変更します。

    - リテラル文字列は引用符で囲まれ、入力したとおりに表示されます。 **"Hello, world"** はリテラル文字列です。

        ![Text プロパティをリテラル文字列に設定する](./media/add-configure-controls/literal-string.png)

    - 式には関数が含まれておらず、多くの場合、別のコントロールのプロパティに基づいています。 **Screen1.Height** は、**Screen1** の高さを表す式です。

        ![Text プロパティを式に設定する](./media/add-configure-controls/expression.png)

    - 数式には、1 つまたは複数の関数が含まれます。 **Now** 関数はローカル タイム ゾーンの現在の日付と時刻を返し、**Text** 関数は日付、時刻、通貨などの値をフォーマットします。

        ![Text プロパティを数式に設定する](./media/add-configure-controls/formula.png)

        数式は通常、この例よりもはるかに複雑であるため、データの更新、並べ替え、フィルタリング、およびその他の操作を実行できます。 詳細については、[数式のリファレンス](formula-reference.md) を参照してください。

## <a name="next-steps"></a>次の手順

- [スクリーン](add-screen-context-variables.md)、[リスト](add-list-box-drop-down-list-radio-button.md)、[ギャラリー](add-gallery.md)、[フォーム](add-form.md)、および[グラフ](use-line-pie-bar-chart.md) のような一般的なコントロールを構成するための手順を説明します。
- 各種類のコントロールに関する参照情報は、[コントロールのリファレンス](reference-properties.md) を参照してください。
