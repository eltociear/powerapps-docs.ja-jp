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
ms.openlocfilehash: aa5d3437b87c0671436146a3ba2365c4e1d127a1
ms.sourcegitcommit: a94b56525667015d4439a082873c2262a61b25a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/16/2020
ms.locfileid: "3456004"
---
# <a name="interactive-map-component-preview"></a>インタラクティブ マップ コンポーネント (プレビュー版)

[!INCLUDE [cc-beta-prerelease-disclaimer.md](../../includes/cc-beta-prerelease-disclaimer.md)]

データ ソースからエンティティの物理的な位置を表示したり、新しい物理的な位置を入力することで、キャンバス アプリに動的マッピング機能を簡単に導入できます。

パン、チルト、ズーム、ドラッグしてマップ ビューの中央に配置します。 縮小すると、ズームアウトすると、マーカーはオプションでクラスタ化され、データの密なグループを表します。 

ユーザーの現在地は、モバイル デバイス、または Web エクスペリエンスの地図上に表示することもできます。 

地図コンポーネントは、道路と航空写真にも対応しています。

![コンポーネントのマップ](./media/augmented-geospatial/geospatial-map-component.png "コンポーネントのマップ")

コンポーネントを使用するには、使用する各アプリケーションに対して [各アプリの地理空間機能を有効にする](geospatial-overview.md#enable-the-geospatial-features-for-each-app)ことに加えて、[環境の地理空間機能を有効にする](geospatial-overview.md#enable-the-geospatial-features-for-the-environment)必要があります。

また、[地理空間のコンポーネントを使用する前提条件](geospatial-overview.md#prerequisites)も確認してください。

## <a name="use-the-component"></a>コンポーネントを使用する

他の任意のコントロールまたはコンポーネントの場合と同じように、コンポーネントをアプリに挿入します。

[Power Apps studio](https://create.powerapps.com)で編集をするアプりを開いた状態で :

1. **挿入**タブを開きます。
2. **メディア**を拡大します。
3. **マップ** コンポーネントを選択し、アプリの画面の中央に配置するか、ドラッグして画面上の任意の場所に配置します。
4. (任意) 現在地の通知を求めるウィンドウで**許可**を選択します。 これにより、コンポーネントはユーザーの現在地を表示することができます。

    ![現在地を知ることに求めるウィンドウで強調表示を許可する](./media/geospatial/address-allow.png "現在地を知ることに求めるウィンドウで強調表示を許可する")

多くのプロパティを使用してコンポーネントを変更できます。

### <a name="properties"></a>プロパティ​​

以下のプロパティは、コンポーネントの**プロパティ** ペインで定義、設定することができます。

![プロパティ ペインの横に表示されるマップ コンポーネント](./media/augmented-geospatial/geospatial-controls.png "プロパティ ペインの横に表示されるマップ コンポーネント")

一部のプロパティは、**プロパティ** ペインの **詳細** タブの**その他のオプション** セクションでのみ利用可能です。

| プロパティ | 内容 | 種類​​ | Location |
| - | - | - | - |
| データ ソース (Items) | データ ソース (table) は、読み込まれた時にマップ上のピンとして表示される、事前に定義された経度と緯度のセットをリスト表示します。 *ItemAddresses*、*ItemLongitudes*、*ItemLatitudes*、*ItemLabels* を使用して、データ内の各カラムをマッピングします。 | 適用なし | プロパティ​​ |
| 既定の場所を使用 | ユーザーが設定した既定の場所でマップを初期化するかどうか。 | Boolean | プロパティ​​ |
| 既定の経度 | **既定のの場所を使用する**が有効になっている場合に、マップが読み込まれた際の経度を指定します。 | 浮動小数点数 | プロパティ​​ |
| 既定の緯度 | **既定のの場所を使用する**が有効になっている場合に、マップが読み込まれた際の緯度を指定します。 | 浮動小数点数 | プロパティ​​ |
| 既定のズーム レベル | **既定のの場所を使用する**が有効になっている場合に、マップが読み込まれた際のズーム レベルを指定します。 | Integer | プロパティ​​ |
| 現在の場所を表示する | マップにユーザーの現在地を表示するかどうか (権限がある場合)。 | Boolean | プロパティ​​ |
| 衛星ビュー | マップのスタイルが衛星ビューか道路ビューか。 | Boolean | プロパティ​​ |
| 集合化ピン | マップ ピンがクラスタ化されているかどうか。 | Boolean | プロパティ​​ |
| ズーム コントロール | ズーム コンポーネントがマップに表示されるかどうか。 | Boolean | プロパティ​​ |
| コンパス コントロール | コンパス コンポーネントがマップに表示されるかどうか。 | Boolean | プロパティ​​ |
| ピッチ コントロール | ピッチ コンポーネントがマップに表示されるかどうか。 | Boolean | プロパティ​​ |
| ピンの色 | ピンの色。 | カラー ピッカー | プロパティ​​ |
| マップのピンの最大数 | マップに表示されるピンの最大数。 | Integer | プロパティ​​ |
| ItemsLabels | ピンのラベルとして使用する文字列を含むアイテムの列。 | TableName.ColumnName | 詳細設定 |
| ItemsAddresses | ピンの位置を表す文字列を含むアイテムの列。 **ItemsLongitudes** または **ItemsLatitudes** では動作しません。 | TableName.ColumnName | 詳細設定 |
| ItemsLongitudes | データ ソースのテーブル内の列の名前と、ピンの経度の位置を表す浮動小数点数。 **ItemsAddresses** では動作しません。 | TableName.ColumnName | 詳細設定 |
| ItemsLatitudes | データ ソースのテーブル内の列の名前と、ピンの緯度の位置を表す浮動小数点数。 **ItemsAddresses** では動作しません。 | TableName.ColumnName | 詳細設定 |
| Items_Items | ピンを使用してマップにプロットするすべてのレコードを含む、データ ソースのテーブルの名前です。 それぞれの行には、各行のラベル、経度、緯度の入力が必要です。 | TableName | 詳細設定 |

### <a name="additional-properties"></a>追加のプロパティ

**[BorderColor](./controls/properties-color-border.md)** – コントロールの境界線の色です。

**BorderRadius** – コントロールの境界線の半径です。

**[BorderStyle](./controls/properties-color-border.md)** – コントロールの境界線が**実線**、**破線**、**点線**、**なし**かどうかを表わします。

**[BorderThickness](./controls/properties-color-border.md)** – コントロールの境界線の太さです。

**[色](./controls/properties-color-border.md)** – コントロールのテキストの色です。

**[DisplayMode](./controls/properties-core.md)** – コントロールがユーザーの入力を許可するか (**編集**)、データのみを表示するか (**表示**)、または無効にするか (**無効**) どうかを表わします。

**[高さ](./controls/properties-size-location.md)** – コントロールの上端と下端間の距離です。

**[TabIndex](./controls/properties-accessibility.md)** – キーボード ナビゲーションの順序です。

**[ヒント](./controls/properties-core.md)** – ユーザーがコントロールにカーソルを置いた際に表示される説明テキストです。

**透明性** -コンポーネントの透明度をパーセントで表わします。

**[表示](./controls/properties-core.md)** – コントロールが表示されるか非表示になるかを表わします。

**[Width](./controls/properties-size-location.md)** – コントロールの左端と右端の間の距離です。

**[X](./controls/properties-size-location.md)** – コントロールの左端とその親コンテナー (コントロールに親コンテナーがない場合は、画面) の左端間の距離です。

**[Y](./controls/properties-size-location.md)** – コントロールの上端とその親コンテナー (コントロールに親コンテナーがない場合は、画面) の上端間の距離です。

## <a name="other-geospatial-components"></a>その他の地理空間コンポーネント

入力時の動的な住所提案を表示するには、**[住所入力](geospatial-component-input-address.md)** コンポーネントを使用してください。
