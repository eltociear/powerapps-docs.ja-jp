---
title: 'ドロップ ダウン コントロール: リファレンス | Microsoft Docs'
description: プロパティとサンプルを含む、ドロップ ダウン コントロールに関する情報
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
ms.openlocfilehash: cc9b12f6cf899d0a57e56eda9fe0dd4bc5ba6c2e
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/13/2020
ms.locfileid: "3308454"
---
# <a name="drop-down-control-in-power-apps"></a>Power Apps でのドロップ ダウン コントロール
ユーザーがそれを開く場合を除き、最初の項目のみを表示するリスト。

## <a name="description"></a>内容
**ドロップ ダウン** コントロールは、特にリストに多数の選択肢が含まれている場合に、画面スペースを節約します。 ユーザーがシェブロンを選択して選択肢を表示しない限り、コントロールが使用するのは 1 行のみです。  コントロールは、最大 500 の項目を表示します。

## <a name="key-properties"></a>主要なプロパティ
**[既定](properties-core.md)** – ユーザーが別の値を指定する前のコントロールの初期値。

**[項目](properties-core.md)** – コントロールに表示される項目を含むデータのソース。 ソースに複数列ある場合、コントロールの**値**プロパティを表示するデータの列に設定します。
  
**値** – コントロールに表示するデータの列 (たとえば、データ ソースに複数の列がある場合)。

**選択済** – 選択された項目を表すデータ レコード。

**AllowEmptySelection** – 項目が選択されていない場合、コントロールが空の選択を表示するかどうか。 アプリ ユーザーは空白の項目を選択することにより、選択をクリアすることもできます。

## <a name="additional-properties"></a>追加のプロパティ
**[AccessibleLabel](properties-accessibility.md)** – スクリーン リーダー用のラベル。

**[BorderColor](properties-color-border.md)** – コントロールの境界線の色。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線が**実線**、**破線**、**点線**、または**なし**かどうか。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さ。

**ChevronBackground** – ドロップダウン リストの下矢印の背景色。

**ChevronFill** – ドロップダウン リストの下向き矢印の色。

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

**SelectedText (非推奨)** – 選択した項目を表す文字列値。

**[SelectionColor](properties-color-border.md)** – リスト内で選択された項目のテキストの色、またはペン コントロールの選択ツールの色。

**[SelectionFill](properties-color-border.md)** – 選択された項目、またはリストの項目、またはペン コントロールの選択領域の背景色。

**[サイズ](properties-text.md)** – コントロールに表示されるテキストのフォント サイズ。

**[Strikethrough](properties-text.md)** – コントロールに表示されるテキストに取り消し線を付けるかどうか。

**[TabIndex](properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序。

**[ツールヒント](properties-core.md)** – ユーザーがコントロールにカーソルを置くときに表示される説明テキスト。

**[下線](properties-text.md)** – コントロールに表示されるテキストの下に線を引くかどうか。

**[表示](properties-core.md)** – コントロールが表示されるか非表示になるか。

**[幅](properties-size-location.md)** – コントロールの左端と右端間の距離。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離。

## <a name="example"></a>例

### <a name="simple-list"></a>シンプルなリスト

1. **ドロップ ダウン** コントロールを追加してから、その **[項目](properties-core.md)** プロパティを次の式に設定します:

    `["Seattle", "Tokyo", "London", "Johannesburg", "Rio de Janeiro"]`

    [コントロールの追加、名前付け、構成](../add-configure-controls.md) についてはこちらをご覧ください。

1. Alt キーを押しながらコントロールの下矢印を選択することにより、リストの項目を表示します。

### <a name="list-from-a-data-source"></a>データ ソースからのリスト
この手順の原則は、[テーブルを提供するデータ ソース](../connections-list.md#tables) すべてに当てはまりますが、これらの手順に正しく従うには、Common Data Service データベースを作成し、サンプル データを追加した環境を開く必要があります。

1. [空のアプリを開き](../data-platform-create-app-scratch.md#open-a-blank-app)、次に [**アカウント** エンティティを指定](../data-platform-create-app-scratch.md#specify-an-entity) します。

1. **ドロップ ダウン** コントロールを追加し、その **[項目](properties-core.md)** プロパティを次の式に設定します:

    `Distinct(Accounts, address1_city)`

    この数式では、**アカウント** エンティティのすべての市区町村が表示されます。 複数のレコードに同じ市区町村がある場合、重複するものは、**[区別](../functions/function-distinct.md)** 関数によりドロップダウン コントロールで非表示となります。

1. (オプション) **ドロップ ダウン** コントロールを**市区町村**に名前変更し、垂直方向の**ギャラリー** コントロールを追加し、ギャラリーの **[項目](properties-core.md)** プロパティをこの数式に設定します:

    `Filter(Accounts, address1_city = Cities.Selected.Value)`

    この **[フィルター](../functions/function-filter-lookup.md)** 関数は、市区町村が**市区町村**コントロールの選択された値と一致する **アカウント** エンティティのレコードのみを表示します。

## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
### <a name="color-contrast"></a>色のコントラスト
次の間には適切な色のコントラストが必要です:
* **ChevronFill** と **ChevronBackground**
* **ChevronHoverFill** と **ChevronHoverBackground**
* **SelectionColor** と **SelectionFill**
* **SelectionFill** と **[塗りつぶし](properties-color-border.md)**

これは、[標準の色のコントラスト要件](../accessible-apps-color.md) に追加されるものです。

### <a name="screen-reader-support"></a>スクリーン リーダー サポート
* **[AccessibleLabel](properties-accessibility.md)** が存在する必要があります。

### <a name="keyboard-support"></a>キーボードのサポート
* **[TabIndex](properties-accessibility.md)** を 0 以上にして、キーボード ユーザーがそこに移動できるようにする必要があります。
* フォーカス インジケーターは明確に表示する必要があります。 これを実現するには **[FocusedBorderColor](properties-color-border.md)** および **[FocusedBorderThickness](properties-color-border.md)** を使用します。
