---
title: 'リスト ボックス コントロール: リファレンス | Microsoft Docs'
description: プロパティとサンプルを含む、リスト ボックス コントロールに関する情報
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/25/2016
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0e55963dfb93e3bfe913b53f90160cb87ed147d8
ms.sourcegitcommit: c0508e233a03ac4846c04d5caae79eccca3e2843
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/15/2020
ms.locfileid: "3309328"
---
# <a name="list-box-control-in-power-apps"></a>Power Apps でのリスト ボックス コントロール
ユーザーが 1 つまたは複数の項目を選択できるリスト。

## <a name="description"></a>内容
**リスト ボックス** コントロールでは、使用可能なすべての選択肢が常に表示されており (**[ドロップ ダウン](control-drop-down.md)** コントロールと異なる)、ユーザーは一度に複数の項目を選択できます (**[ラジオ](control-radio.md)** コントロールと異なる)。

## <a name="key-properties"></a>主要なプロパティ
**[Default](properties-core.md)** – ユーザーが変更する前のコントロールの初期値です。

**[項目](properties-core.md)** – ギャラリー、リスト、グラフなどのコントロールに表示されるデータのソース。

**選択済** – 選択された項目を表すデータ レコード。  既定で選択できる項目は 1 つのみです。  複数の選択した項目が必要な場合は、[コンボ ボックス](control-combo-box.md) コントロールを使用してください。

ギャラリー、リスト、またはグラフを追加すると、既定ではプロパティの一覧に**項目**が表示され、新しいコントロールに表示されるデータを簡単に指定できます。 たとえば、ギャラリーの**項目**プロパティは Salesforce の**取引先企業**テーブル、Excel で作成されクラウドにアップロードされた **在庫**という名前の表、または **ConferenceSpeakers** という名前の SharePoint リストに設定する場合があります。

## <a name="additional-properties"></a>追加のプロパティ
**[AccessibleLabel](properties-accessibility.md)** – スクリーン リーダー用のラベル。

**[BorderColor](properties-color-border.md)** – コントロールの境界線の色。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線が**実線**、**破線**、**点線**、または**なし**かどうか。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さ。

**[色](properties-color-border.md)** – コントロールのテキストの色。

**[DisplayMode](properties-core.md)** – コントロールがユーザー入力を許可するか (**編集**)、データのみを表示するか (**表示**)、または無効にするか (**無効**) どうか。

**[DisabledBorderColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロールの境界線の色。

**[DisabledColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロール内のテキストの色。

**[DisabledFill](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロールの背景色。

**[塗りつぶし](properties-color-border.md)** – コントロールの背景色。

**[FocusedBorderColor](properties-color-border.md)** – コントロールがフォーカスされているときのコントロールの境界線の色。

**[FocusedBorderThickness](properties-color-border.md)** – コントロールがフォーカスされているときのコントロールの境界線の太さ。

**[フォント](properties-text.md)** – テキストを表示するフォントのファミリーの名前。

**[FontWeight](properties-text.md)** – コントロール内のテキストの太さ: **太字**、**中太**、**標準**、または**細字**。

**[高さ](properties-size-location.md)** – コントロールの上端と下端間の距離。

**[HoverBorderColor](properties-color-border.md)** – ユーザーがコントロール上にマウス ポインターを重ねているときのコントロールの境界線の色。

**[HoverColor](properties-color-border.md)** – ユーザーがコントロールにマウス ポインターを重ねているときのコントロール内のテキストの色。

**[HoverFill](properties-color-border.md)** – ユーザーがコントロールにマウス ポインターを重ねているときのコントロールの背景色。

**[斜体](properties-text.md)** – コントロール内のテキストを斜体にするかどうか。

**ItemPaddingLeft** – リストボックス内のテキストと左端の間の距離。

**[LineHeight](properties-text.md)** – たとえば、テキストの行間またはリスト内の項目間などの距離です。

**[OnChange](properties-core.md)** – ユーザーが (たとえば、スライダーを調整するなどして) コントロールの値を変更した場合のアプリの反応を指定します。

**[OnSelect](properties-core.md)** – ユーザーがコントロールをタップまたはクリックする場合のアプリの反応方法。

**[PaddingBottom](properties-size-location.md)** – コントロール内のテキストとそのコントロールの下端間の距離。

**[PaddingLeft](properties-size-location.md)** – コントロール内のテキストとそのコントロールの左端間の距離。

**[PaddingRight](properties-size-location.md)** – コントロール内のテキストとそのコントロールの右端間の距離。

**[PaddingTop](properties-size-location.md)** – コントロール内のテキストとそのコントロールの上端間の距離。

**[PressedBorderColor](properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロールの境界線の色。

**[PressedColor](properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロール内のテキストの色。

**[PressedFill](properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロールの背景色。

**[Reset](properties-core.md)** – コントロールを既定値に戻すかどうかを指定します。

**選択済** – 選択された項目を表すデータ レコード。  既定で選択できる項目は 1 つのみです。  複数の選択した項目が必要な場合は、[コンボ ボックス](control-combo-box.md) コントロールを使用してください。

**SelectedItems** - **読み取り専用**。 複数選択リストボックスの選択された項目のデータテーブルを表します。

**SelectedItemsText** - **読み取り専用**。 複数選択リストボックスの選択された項目テキストのデータテーブルを表します。

**SelectedText (非推奨)** – 選択した項目を表す文字列値。

**[SelectionColor](properties-color-border.md)** – リスト内で選択された項目のテキストの色、またはペン コントロールの選択ツールの色。

**[SelectionFill](properties-color-border.md)** – 選択された項目、またはリストの項目、またはペン コントロールの選択領域の背景色。

**SelectMultiple** – ユーザーがリストボックスの複数の項目を選択できるかどうか。

**[サイズ](properties-text.md)** – コントロールに表示されるテキストのフォント サイズ。

**[Strikethrough](properties-text.md)** – コントロールに表示されるテキストに取り消し線を付けるかどうか。

**[TabIndex](properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序。

**[ツールヒント](properties-core.md)** – ユーザーがコントロールにカーソルを置くときに表示される説明テキスト。

**[下線](properties-text.md)** – コントロールに表示されるテキストの下に線を引くかどうか。

**[表示](properties-core.md)** – コントロールが表示されるか非表示になるか。

**[幅](properties-size-location.md)** – コントロールの左端と右端間の距離。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離。

## <a name="related-functions"></a>関連する関数
[**Distinct**( *DataSource*, *ColumnName* )](../functions/function-distinct.md)

## <a name="example"></a>例
1. **リスト ボックス** コントロールを追加し、**CategoryList** という名前を付け、**[項目](properties-core.md)** プロパティを次の式に設定します:<br>
   **["カーペット","硬木","タイル"]**
   
    [コントロールの追加、名前付け、構成](../add-configure-controls.md) についてはこちらをご覧ください。
   
    ![リスト ボックス内の床のカテゴリ](./media/control-list-box/category-listbox.png)
2. 3 つの **[ドロップ ダウン](control-drop-down.md)** コントロールを追加し、**CategoryList** の下に移動して、**CarpetList**、**HardwoodList**、**TileList** という名前を付けます。
3. 各 **[ドロップ ダウン](control-drop-down.md)** コントロールの **[項目](properties-core.md)** プロパティに、次の値の 1 つを設定します:
   
   * CarpetList: **["Caserta Stone Beige","Ageless Beauty Clay", "Lush II Tundra"]**
   * HardwoodList: **["Golden Teak","Natural Hickory", "Victoria Mahogany"]**
   * TileList: **["Honey Onyx Marble","Indian Autumn Slate", "Panaria Vitality Ceramic"]**
     
     ![ドロップダウン リストの床材の名前](./media/control-list-box/flooring-names.png)
4. 各 **[ドロップ ダウン](control-drop-down.md)** コントロールの **[表示](properties-core.md)** プロパティに、次の値の 1 つを設定します:
   
   * CarpetList: **If("Carpet" in CategoryList.SelectedItems.Value, true)**
   * HardwoodList: **If("Hardwood" in CategoryList.SelectedItems.Value, true)**
   * TileList: **If("Tile" in CategoryList.SelectedItems.Value, true)**
     
     **[If](../functions/function-if.md)** 関数または [その他の関数](../formula-reference.md) の詳細については各関連記事を参照してください。
5. F5 キーを押してから、**CategoryList** で 1 つまたは複数の項目を選択します。
   
    選択に基づいて、適切な **[ドロップ ダウン](control-drop-down.md)** コントロールが表示されます。
   
    ![ドロップダウン リストの床材の名前](./media/control-list-box/selected-lists.png)
6. (オプション) Esc キーを押して既定のワークスペースに戻ります。


## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
### <a name="color-contrast"></a>色のコントラスト
次の間には適切な色のコントラストが必要です:
* **SelectionColor** と **SelectionFill**
* **SelectionFill** と **[塗りつぶし](properties-color-border.md)**
* **[HoverFill](properties-color-border.md)** と **[塗りつぶし](properties-color-border.md)**
* **[PressedFill](properties-color-border.md)** と **[塗りつぶし](properties-color-border.md)**

これは、[標準の色のコントラスト要件](../accessible-apps-color.md) に追加されるものです。

### <a name="screen-reader-support"></a>スクリーン リーダー サポート
* **[AccessibleLabel](properties-accessibility.md)** が存在する必要があります。

### <a name="keyboard-support"></a>キーボードのサポート
* **[TabIndex](properties-accessibility.md)** を 0 以上にして、キーボード ユーザーがそこに移動できるようにする必要があります。
* フォーカス インジケーターは明確に表示する必要があります。 これを実現するには **[FocusedBorderColor](properties-color-border.md)** および **[FocusedBorderThickness](properties-color-border.md)** を使用します。

    > [!NOTE]
  > Tab キーを押すと、**リスト ボックス**に移動またはリスト ボックスから移動します。 矢印キーを押すと、**リスト ボックス**の内容に移動します。
