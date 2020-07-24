---
title: ''
description: ''
author: iaanw
manager: shellha
ms.service: powerapps
ms.topic: conceptual
ms.custom: ce06122020
ms.reviewer: tapanm
ms.date: 6/12/2020
ms.author: iawilt
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a425ad33fbaa947ab95a475dd0df9634fe79155f
ms.sourcegitcommit: a94b56525667015d4439a082873c2262a61b25a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/16/2020
ms.locfileid: "3455876"
---
# <a name="address-input-component-preview"></a>住所入力コンポーネント (プレビュー版)

[!INCLUDE [cc-beta-prerelease-disclaimer.md](../../includes/cc-beta-prerelease-disclaimer.md)]

特にモバイル機器では住所入力の際に、ミスが発生しやすいことから、エラーが発生しやすくなります。 

住所入力コンポーネントを使用すると、入力時に動的な住所候補を表示できます。 このコンポーネントは、ファジー マッチング ロジックを使用して、ユーザーが選択できる複数の住所候補を提案し、&mdash;正確な住所をすばやく簡単に入力できます。

コンポーネントは住所を構造化データとして返し、アプリケーションが都市、通り、自治体、さらには緯度と経度などの情報を抽出できるようにします。 データは多くのロケールや国際でき名住所の形式に適した形式となっています。

コンポーネントを使用するには、使用する各アプリケーションに対して [各アプリの地理空間機能を有効にする](geospatial-overview.md#enable-the-geospatial-features-for-each-app)ことに加えて、[環境の地理空間機能を有効にする](geospatial-overview.md#enable-the-geospatial-features-for-the-environment)必要があります。

また、[地理空間のコンポーネントを使用する前提条件](geospatial-overview.md#prerequisites)も確認してください。

## <a name="use-the-component"></a>コンポーネントを使用する

他の任意のコントロールまたはコンポーネントの場合と同じように、コンポーネントをアプリに挿入します。

[Power Apps Studio](https://create.powerapps.com) で編集用にアプリを開いて:

1. **挿入**タブを開きます。 

2. **入力**を展開する。

3. **住所入力 (プレビュー版)** コンポーネントを選択し、アプリの画面の中央に配置するか、ドラッグして画面上の任意の場所に配置します。

4. (任意) 現在地の通知を求めるウィンドウで**許可**を選択します。 これにより、コンポーネントはユーザーの現在地に応じて結果を絞り込むことができます。

    ![現在地を知ることに求めるウィンドウで強調表示を許可する](./media/geospatial/address-allow.png "現在地を知ることに求めるウィンドウで強調表示を許可する")

多くのプロパティを使用してコンポーネントを変更できます。

### <a name="properties"></a>プロパティ​​

次のプロパティは、**プロパティ**と**詳細**タブのコンポーネント上の**住所入力**ペインにあります。

![プロパティはサイド パネルにあります](./media/geospatial/address-properties.png "プロパティはサイド パネルにあります")

一部のプロパティは、**詳細**タブ、**その他のオプション**セクションにあります。

| プロパティ | 内容 | 種類​​ | Location |
| - | - | - | - |
| 自動入力を有効化する | コンポーネントが住所の提案を提供するかどうか。 | Boolean | プロパティ​​ |
| 検索結果の制限 | コンポーネントで表示する提案住所の数。 | Integer | プロパティ​​ |
| 半径内を検索する | コンポーネントが**緯度**と**経度**のユーザ定義の**半径**内のアドレスを提案するかどうか。 | Boolean | プロパティ​​ |
| 緯度 | 住所候補の地理バイアスに使用する中心点の緯度。 **半径内を検索**をオンにする必要があります。 | 180 から&ndash;180 までの少数 | プロパティ​​ |
| 経度 | 住所候補の地理バイアスに使用する中心点の緯度。 **半径内を検索**をオンにする必要があります。 | 180 から&ndash;180 までの少数 | プロパティ​​ |
| 半径 | 住所の提案を制約する**緯度**と**経度**の半径をメートル単位で指定します。 **半径内を検索**をオンにする必要があります。 | 小数 | プロパティ​​ |
| Language | 住所候補で返す言語 | 文字列 | プロパティ​​ |
| 国のセット | ISO 3166 alpha-2 国コードで、住所の提案を制限する国のコンマ区切りのリスト。 例えば、**US、FR、KW** | 文字列 | プロパティ​​ |

### <a name="additional-properties"></a>追加のプロパティ

**[既定](./controls/properties-core.md)** – ユーザーが変更する前のコントロールの初期値です。

**[テキスト](./controls/properties-core.md)** – コントロールに表示されるテキスト、またはユーザーがコントロールに入力するテキスト。

**[BorderColor](./controls/properties-color-border.md)** – コントロールの境界線の色。

**BorderColor** – コントロールの境界線の半径です。

**[BorderStyle](./controls/properties-color-border.md)** – コントロールの境界線が**実線**、**破線**、**点線**、または**なし**かどうか。

**[BorderThickness](./controls/properties-color-border.md)** – コントロールの境界線の太さ。

**[Color](./controls/properties-color-border.md)** – コントロールのテキストの色。

**[DisplayMode](./controls/properties-core.md)** – コントロールがユーザー入力を許可するか (**編集**)、データのみを表示するか (**表示**)、または無効にするか (**無効**) どうか。

**[DisabledBorderColor](./controls/properties-color-border.md)** – コントロールの **[DisplayMode](./controls/properties-core.md)** プロパティが**無効**に設定されている場合のコントロールの境界線の色。

**[DisabledColor](./controls/properties-color-border.md)** – コントロールの **[DisplayMode](./controls/properties-core.md)** プロパティが**無効**に設定されている場合のコントロール内のテキストの色。

**[DisabledFill](./controls/properties-color-border.md)** – コントロールの **[DisplayMode](./controls/properties-core.md)** プロパティが**無効**に設定されている場合のコントロールの背景色。

**[塗りつぶし](./controls/properties-color-border.md)** – コントロールの背景色。

**[FocusedBorderColor](./controls/properties-color-border.md)** – コントロールにフォーカスがある場合のコントロールの境界線の色です。

**[FocusedBorderThickness](./controls/properties-color-border.md)** – コントロールにフォーカスがある場合のコントロールの境界線の太さです。

**[Font](./controls/properties-text.md)** – テキストを表示するフォントのファミリーの名前。

**[FontWeight](./controls/properties-text.md)** – コントロール内のテキストの太さ: **太字**、**中太**、**標準**、または**細字**。

**[Height](./controls/properties-size-location.md)** – コントロールの上端と下端間の距離。

**HintText** - テキスト入力コントロールが空の場合に表示される薄いグレーのテキストです。

**[HoverBorderColor](./controls/properties-color-border.md)** – ユーザーがコントロールにマウス ポインターを重ねているときのコントロールの境界線の色。

**[HoverColor](./controls/properties-color-border.md)** – ユーザーがコントロールにマウス ポインターを重ねているときのコントロール内のテキストの色。

**[HoverFill](./controls/properties-color-border.md)** – ユーザーがコントロールにマウス ポインターを重ねているときのコントロールの背景色。

**[斜体](./controls/properties-text.md)** – コントロール内のテキストを斜体にするかどうか。

**[LineHeight](./controls/properties-text.md)** – テキストの行間やリスト内の項目間などの&mdash;垂直方向の距離です。

**[OnChange](./controls/properties-core.md)** – ユーザーが (たとえば、スライダーを調整するなどして) コントロールの値を変更した場合のアプリの反応を指定します。

**[PaddingBottom](./controls/properties-size-location.md)** – コントロール内のテキストとそのコントロールの下端間の距離。

**[PaddingLeft](./controls/properties-size-location.md)** – コントロール内のテキストと、そのコントロールの左端間の距離です。

**[PaddingRight](./controls/properties-size-location.md)** – コントロール内のテキストと、そのコントロールの右端間の距離です。

**[PaddingTop](./controls/properties-size-location.md)** – コントロール内のテキストとそのコントロールの上端間の距離。

**[PressedBorderColor](./controls/properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロールの境界線の色。

**[PressedColor](./controls/properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロール内のテキストの色。

**[PressedFill](./controls/properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロールの背景色。

**[サイズ](./controls/properties-text.md)** – コントロールに表示されるテキストのフォント サイズ。

**[Strikethrough](./controls/properties-text.md)** – コントロールに表示されるテキストに取り消し線を付けるかどうか。

**[TabIndex](./controls/properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序。

**[ツールヒント](./controls/properties-core.md)** – ユーザーがコントロールにカーソルを置くときに表示される説明テキスト。

**[下線](./controls/properties-text.md)** – コントロールに表示されるテキストの下に線を引くかどうか。

**[Visible](./controls/properties-core.md)** – コントロールが表示されるか非表示になるか。

**[Width](./controls/properties-size-location.md)** – コントロールの左端と右端の間の距離です。

**[X](./controls/properties-size-location.md)** – コントロールの左端とその親コンテナー (コントロールに親コンテナーがない場合は、画面) の左端間の距離です。

**[Y](./controls/properties-size-location.md)** – コントロールの上端とその親コンテナー (コントロールに親コンテナーがない場合は、画面) の上端間の距離です。

## <a name="other-geospatial-components"></a>その他の地理空間コンポーネント

場所データを視覚化して解釈するには、**[インタラクティブ マップ](geospatial-component-map.md)** コンポーネントを使用します。
