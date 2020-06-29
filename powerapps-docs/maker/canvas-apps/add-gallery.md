---
title: キャンバス アプリの項目の一覧を表示する | Microsoft Docs
description: ギャラリーを使用して、キャンバス アプリの項目の一覧を表示し、条件を指定して一覧をフィルター処理します。
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 09/28/2017
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 09b8f728d175edb598ee832be11cf3329d166ae7
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3306545"
---
# <a name="show-a-list-of-items-in-power-apps"></a>Power Apps の項目の一覧の表示

キャンバス アプリに**[ギャラリー](controls/control-gallery.md)** コントロールを追加して、任意のデータ ソースからの項目の一覧を表示します。 このトピックでは、データ ソースとして Excel を使用します。 **[テキスト入力](controls/control-text-input.md)** コントロールのフィルター条件に一致する項目のみを表示するように**ギャラリー** コントロールを構成して、一覧をフィルター処理します。

## <a name="prerequisites"></a>前提条件

- Power Apps に[コントロールを追加および構成](add-configure-controls.md) する方法について説明します。

- サンプル データの設定:
    1. [この Excel ファイル](https://az787822.vo.msecnd.net/documentation/get-started-from-data/FlooringEstimates.xlsx) をダウンロードして、チュートリアルのサンプル データを取得します。

    2. Excel ファイルを OneDrive for Business などの[クラウド ストレージ アカウント](connections/cloud-storage-blob-connections.md) にアップロードします。

- 空のアプリを開く:
    1. [Power Apps にサインインします](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。

    1. **自分のアプリを作成する**で、**キャンバス アプリを一から作成**を選択します。

    1. アプリに名前を指定し、**電話**を選択し、**作成**を選択します。

    1. **Power Apps Studio へようこそ**のダイアログ ボックスが表示されたら、**スキップ**を選択します。

    1. Excel ファイル内の **FlooringEstimates** テーブルへの[接続を追加](add-data-connection.md) します。

## <a name="add-a-gallery-to-a-blank-screen"></a>空白のスクリーンにギャラリーを追加する

1. **挿入**タブで、**ギャラリー**を選択してから、**縦**を選択します。

    ![縦方向のギャラリーの追加](./media/add-gallery/gallery-dropdown.png)

1. 右側のウィンドウの**プロパティ** タブで、**Items** の一覧を開いてから、**Flooring Estimates** を選択します。

    ![床材の見積もり](./media/add-gallery/select-layout.png)

1. (オプション) **レイアウト**の一覧で、別のオプションを選択します。

## <a name="add-a-gallery-in-a-screen"></a>スクリーンにギャラリーを追加する

1. **ホーム** タブで、**新しいスクリーン** > **リスト スクリーン**を選択します。

    **ギャラリー** コントロールおよび検索バーなどのコントロールを含むスクリーンが表示されます。

1. ギャラリーの **Items** プロパティを `FlooringEstimates` に設定します。

    **ギャラリー** コントロールに、サンプル データが表示されます。

    ![データの表示](./media/add-gallery/show-data-default.png)

## <a name="add-a-control-to-the-gallery-control"></a>ギャラリー コントロールにコントロールを追加する
他のカスタマイズを行う前に、**ギャラリー** コントロールのレイアウトが、必要なものに最も近いことを確認します。 そこから、**ギャラリー** テンプレートをさらに変更できます。これによって、**ギャラリー** コントロールでのすべてのデータの表示方法が決まります。

1. **ギャラリー** コントロールの下部付近を選択してから、左上隅にある鉛筆アイコンを選択して、テンプレートを選択します。

    ![ギャラリー テンプレートの編集](./media/add-gallery/edit-item.png)

2. テンプレートを選択した状態で、**[ラベル](controls/control-text-box.md)** コントロールを追加し、テンプレート内の他のコントロールと重ならないように、追加したコントロールを移動し、サイズを変更します。

    ![ラベルの追加](./media/add-gallery/add-text-box.png)

3. ギャラリーを選択してから、右側のウィンドウの**プロパティ** タブで、**フィールド**の横にある**編集**を選択します。

4. この手順で先に追加したラベルを選択して、**データ** ウィンドウで強調表示されたリストを開きます。

    ![ドロップダウン リストを開く](./media/add-gallery/open-dropdown.png)

5. このリストで**価格**をクリックまたはタップします。

    **ギャラリー** コントロールに新しい値が表示されます。

    ![最終ギャラリー](./media/add-gallery/final-gallery.png)

## <a name="filter-and-sort-a-gallery"></a>ギャラリーのフィルター処理と並べ替え
**ギャラリー** コントロールの **[Items](controls/properties-core.md)** プロパティにより、表示する項目が決まります。 この手順では、フィルター条件に基づいて表示されるレコードとその順序も決定するように、そのプロパティを構成します。

![検索ボックスと並べ替えアイコン](./media/add-gallery/text-search-box.png)

1. **ギャラリー** コントロールの **[Items](controls/properties-core.md)** プロパティを次の数式に設定します。

    ```powerapps-dot
    Sort
        (If
            (IsBlank(TextSearchBox1.Text),
            FlooringEstimates,
            Filter(
                FlooringEstimates,
                TextSearchBox1.Text in Text(Name)
            )
        ),
        Name,
        If(
            SortDescending1,
            SortOrder.Descending,
            SortOrder.Ascending
        )
    )
    ```

    この数式内の関数について詳しくは、[数式のリファレンス](formula-reference.md) をご覧ください。

1. 検索ボックスをダブルクリックし、そこに製品名の一部またはすべてを入力します。

    フィルター条件を満たすアイテムのみが表示されます。

1. Alt キーを押しながら、並べ替えアイコンを 1 回以上選択して、並べ替え順を切り替えます。

    レコードは、製品名に基づいてアルファベット順の昇順と降順を切り替えます。

## <a name="highlight-the-selected-item"></a>選択した項目を強調表示する
**ギャラリー** コントロールの **TemplateFill** プロパティをこの例に似た数式に設定しますが、必要に応じて異なる色を指定できます。

**If(ThisItem.IsSelected, LightCyan, White)**

## <a name="change-the-default-selection"></a>既定の選択を変更する
**ギャラリー** コントロールの **Default** プロパティを、既定で選択するレコードに設定します。 たとえば、**FlooringEstimates** データ ソースの 5 番目の項目を指定できます。

**Last(FirstN(FlooringEstimates, 5))**

この例では、**FlooringEstimates** データ ソースの **Hardwood** カテゴリにある、最初の項目を指定します。

**First(Filter(FlooringEstimates, Category = "Hardwood"))**

## <a name="next-steps"></a>次の手順
[フォーム](working-with-forms.md) と[数式](working-with-formulas.md) を使用する方法について説明します。
