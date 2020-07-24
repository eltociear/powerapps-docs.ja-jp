---
title: '円グラフ コントロール: リファレンス | Microsoft Docs'
description: プロパティとサンプルを含む、円グラフ コントロールに関する情報
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
ms.openlocfilehash: 4b7125da14cc315595a305d97d710766fcc8ff3e
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3306016"
---
# <a name="pie-chart-control-in-power-apps"></a>Power Apps での円グラフ コントロール
互いに比較した相対値を表示するコントロール。

## <a name="description"></a>内容
左端の列にラベルを含み、左から 2 番目の列に値を含むテーブルの相対的なデータを表示する場合は、**円グラフ** コントロールを追加します。

このコントロールは、3 つのコントロールを含むグループ化されたコントロールです: タイトルの **[ラベル](control-text-box.md)**、グラフのグラフィック、および**凡例**。

## <a name="chart-key-properties"></a>グラフの主要なプロパティ
**[項目](properties-core.md)** – ギャラリー、リスト、グラフなどのコントロールに表示されるデータのソース。

**ShowLabels** – 円グラフに各ウェッジに関連付けられた値を表示するかどうか。

## <a name="additional-chart-properties"></a>追加のグラフ プロパティ
**[BorderColor](properties-color-border.md)** – コントロールの境界線の色。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線が**実線**、**破線**、**点線**、または**なし**かどうか。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さ。

**[色](properties-color-border.md)** – コントロールのテキストの色。

**[DisplayMode](properties-core.md)** – コントロールがユーザー入力を許可するか (**編集**)、データのみを表示するか (**表示**)、または無効にするか (**無効**) どうか。

**[DisabledBorderColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロールの境界線の色。

**展開** – 円グラフ内のウェッジ間の距離。

**[フォント](properties-text.md)** – テキストを表示するフォントのファミリーの名前。

**[高さ](properties-size-location.md)** – コントロールの上端と下端間の距離。

**[HoverBorderColor](properties-color-border.md)** – ユーザーがコントロール上にマウス ポインターを重ねているときのコントロールの境界線の色。

**ItemBorderColor** – 円グラフ内の各ウェッジの周りの境界線の色。

**ItemBorderThickness** – 円グラフ内の各ウェッジの周りの境界線の太さ。

**ItemColorSet** – グラフ内の各データ ポイントの色です。

**LabelPosition** – ウェッジに相対的な円グラフ内のラベルの場所。

**[OnSelect](properties-core.md)** – ユーザーがコントロールをタップまたはクリックする場合のアプリの反応方法。

**[PressedBorderColor](properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロールの境界線の色。

**[サイズ](properties-text.md)** – コントロールに表示されるテキストのフォント サイズ。

**[TabIndex](properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序。

**[表示](properties-core.md)** – コントロールが表示されるか非表示になるか。

**[幅](properties-size-location.md)** – コントロールの左端と右端間の距離。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離。

## <a name="related-functions"></a>関連する関数
[**Max**( *DataSource*, *ColumnName* )](../functions/function-aggregates.md)

## <a name="example"></a>例
1. **[ボタン](control-button.md)** コントロールを追加し、**[OnSelect](properties-core.md)** プロパティに次の式を設定します:<br>
   **Collect(Revenue2015, {製品:"Europa", 売上:27000}, {製品:"Ganymede", 売上:26300}, {製品:"Callisto", 売上:29200})**
   
    [コントロールの追加および構成](../add-configure-controls.md) についてはこちらをご覧ください。
   
    **[Collect](../functions/function-clear-collect-clearcollect.md)** 関数または [その他の関数](../formula-reference.md) については、各関連記事を参照してください。
2. F5 キーを押して、**[ボタン](control-button.md)** コントロールをクリックまたはタップしてから、Esc キーを押して既定のワークスペースに戻ります。
3. **円グラフ** コントロールを追加し、その **[項目](properties-core.md)** プロパティを **Revenue2015** に設定します。
   
    **円グラフ** コントロールには、他の製品に関連した製品ごとの売上データが表示されます。


## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
### <a name="color-contrast"></a>色のコントラスト
次の間には適切な色のコントラストが必要です:
* **ItemColorSet** の各項目
* **ItemColorSet** の各項目と背景色
* **[色](properties-color-border.md)** と背景色

### <a name="screen-reader-support"></a>スクリーン リーダー サポート
* タイトルとして機能するグラフのグラフィックの直前には、**[ラベル](control-text-box.md)** が必要です。

    > [!NOTE]
  > グラフのグラフィックと**凡例**はスクリーン リーダー ユーザーには表示されません。 代わりに、データの表形式が表示されます。 また、グラフ内のデータを選択するボタンを切り替えることもできます。

### <a name="low-vision-support"></a>弱視のサポート
* **凡例**が必要です。
* **ShowLabels** を **true** に設定することを検討してください。 これにより、視力に障碍のあるユーザーは個々の円スライスが何を表すかを素早く判断できるようになります。
* **LabelPosition** を **LabelPosition.Outside** に設定することを検討してください。 これにより、より一貫した色のコントラストになるので、ラベルの読みやすさが向上します。

### <a name="keyboard-support"></a>キーボードのサポート
* **[TabIndex](properties-accessibility.md)** を 0 以上にして、キーボード ユーザーがそこに移動できるようにする必要があります。

    > [!NOTE]
  > キーボード ユーザーがグラフに移動すると、グラフ内のデータを選択するボタンを切り替えることができます。
