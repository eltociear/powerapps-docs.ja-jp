---
title: '縦棒グラフ コントロールと折れ線グラフ コントロール: リファレンス | Microsoft Docs'
description: プロパティとサンプルを含む、縦棒グラフ コントロールと折れ線グラフ コントロールに関する情報
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 10/25/2016
ms.author: chmoncay
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 22bd949dc11171d90a7ed358528c91999c4acc3e
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3306223"
---
# <a name="column-chart-and-line-chart-controls-in-power-apps"></a>Power Apps での縦棒グラフ コントロールと折れ線グラフ コントロール
X 軸と Y 軸からなるグラフとしてデータを表示するコントロール。

## <a name="description"></a>内容
**縦棒グラフ** コントロールと**折れ線グラフ** コントロールはグループ化されたコントロールです。 各グループには 3 つのコントロールが含まれます: タイトルの **[ラベル](control-text-box.md)**、グラフのグラフィック、および**凡例**。

## <a name="chart-key-properties"></a>グラフの主要なプロパティ
**[項目](properties-core.md)** – ギャラリー、リスト、グラフなどのコントロールに表示されるデータのソース。

**NumberOfSeries** – 縦棒グラフまたは折れ線グラフに反映されるデータ列の数。

## <a name="additional-chart-properties"></a>追加のグラフ プロパティ
**[BorderColor](properties-color-border.md)** – コントロールの境界線の色。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線が**実線**、**破線**、**点線**、または**なし**かどうか。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さ。

**[色](properties-color-border.md)** – コントロールのテキストの色。

**[DisabledBorderColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロールの境界線の色。

**[DisplayMode](properties-core.md)** – コントロールがユーザー入力を許可するか (**編集**)、データのみを表示するか (**表示**)、または無効にするか (**無効**) どうか。

**[フォント](properties-text.md)** – テキストを表示するフォントのファミリーの名前。

**GridStyle** – 縦棒グラフまたは折れ線グラフで、X 軸と Y 軸のどちらか一方または両方を表示するか、または両方とも表示しないか。

**[高さ](properties-size-location.md)** – コントロールの上端と下端間の距離。

**[HoverBorderColor](properties-color-border.md)** – ユーザーがコントロール上にマウス ポインターを重ねているときのコントロールの境界線の色。

**ItemColorSet** – グラフ内の各データ ポイントの色です。

**ItemsGap** – 縦棒グラフの縦棒間の距離。

* **ItemsGap** プロパティは、**縦棒グラフ** コントロールでは使用できますが、**折れ線グラフ** コントロールでは使用できません。

**Markers** – 縦棒グラフまたは折れ線グラフで各データ ポイントの値を表示するかどうか。

**MarkerSuffix** – **マーカー** プロパティが **true** に設定されている縦棒グラフで、各値の後ろに表示するテキスト。

* **MarkerSuffix** プロパティは、**縦棒グラフ** コントロールでは使用できますが、**折れ線グラフ** コントロールでは使用できません。

**MinimumBarWidth** – 縦棒グラフの縦棒の最も狭い幅。

* **MinimumBarWidth** プロパティは、**縦棒グラフ** コントロールでは使用できますが、**折れ線グラフ** コントロールでは使用できません。

**[OnSelect](properties-core.md)** – ユーザーがコントロールをタップまたはクリックする場合のアプリの反応方法。

**[PaddingBottom](properties-size-location.md)** – コントロール内のテキストとそのコントロールの下端間の距離。

**[PaddingLeft](properties-size-location.md)** – コントロール内のテキストとそのコントロールの左端間の距離。

**[PaddingRight](properties-size-location.md)** – コントロール内のテキストとそのコントロールの右端間の距離。

**[PaddingTop](properties-size-location.md)** – コントロール内のテキストとそのコントロールの上端間の距離。

**[PressedBorderColor](properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロールの境界線の色。

**SeriesAxisMax** – 縦棒グラフまたは折れ線グラフの Y 軸の最大値。

* **SeriesAxisMax** プロパティは、**縦棒グラフ** コントロールでは使用できますが、**折れ線グラフ** コントロールでは使用できません。

**SeriesAxisMin** – 縦棒グラフの Y 軸の最小値を決定する数値。

* **SeriesAxisMin** プロパティは、**縦棒グラフ** コントロールでは使用できますが、**折れ線グラフ** コントロールでは使用できません。

**[サイズ](properties-text.md)** – コントロールに表示されるテキストのフォント サイズ。

**[TabIndex](properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序。

**[表示](properties-core.md)** – コントロールが表示されるか非表示になるか。

**[幅](properties-size-location.md)** – コントロールの左端と右端間の距離。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離。

**XLabelAngle** – 縦棒グラフまたは折れ線グラフの X 軸の下のラベルの角度。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離。

**YAxisMax** – 折れ線グラフの Y 軸の最大値。

* **YAxisMax** プロパティは、**折れ線グラフ** コントロールでは使用できますが、**縦棒グラフ** コントロールでは使用できません。

**YAxisMin** – 折れ線グラフの Y 軸の最小値。

* **YAxisMin** プロパティは、**折れ線グラフ** コントロールでは使用できますが、**縦棒グラフ** コントロールでは使用できません。

**YLabelAngle** – 折れ線グラフまたは縦棒グラフの Y 軸の横のラベルの角度。

## <a name="related-functions"></a>関連する関数
[**Max**( *DataSource*, *ColumnName* )](../functions/function-aggregates.md)

## <a name="example"></a>例
1. **[ボタン](control-button.md)** コントロールを追加し、**[OnSelect](properties-core.md)** プロパティに次の式を設定します:<br>
   **Collect(Revenue, {Year:"2013", Europa:24000, Ganymede:22300, Callisto:21200}, {Year:"2014", Europa:26500, Ganymede:25700, Callisto:24700},{Year:"2014", Europa:27900, Ganymede:28300, Callisto:25600})**
   
    [コントロールの追加および構成](../add-configure-controls.md) についてはこちらをご覧ください。
   
    **[Collect](../functions/function-clear-collect-clearcollect.md)** 関数または [その他の関数](../formula-reference.md) については、各関連記事を参照してください。
2. F5 キーを押して、**[ボタン](control-button.md)** コントロールをクリックまたはタップしてから、Esc キーを押して既定のワークスペースに戻ります。
3. **縦棒グラフ** コントロールまたは**折れ線グラフ** コントロールを追加し、**[Items](properties-core.md)** プロパティを**売上**に、**NumberOfSeries** プロパティを **3** に設定します。
   
    コントロールには、過去 3 年間の各製品の売上データが表示されます。


## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
### <a name="color-contrast"></a>色のコントラスト
次の間には適切な色のコントラストが必要です:
* **ItemColorSet** の各項目
* **ItemColorSet** の各項目と背景色
* **[色](properties-color-border.md)** と背景色

### <a name="screen-reader-support"></a>スクリーン リーダー サポート
* タイトルとして機能するグラフのグラフィックの直前には、**[ラベル](control-text-box.md)** が必要です。
* グラフのグラフィックの概要を追加することを検討してください。 たとえば、"折れ線グラフは、今年の 3 月から 8 月の売上が着実に増加していることを示しています。"

    > [!NOTE]
  > グラフのグラフィックと**凡例**はスクリーン リーダー ユーザーには表示されません。 代わりに、データの表形式が表示されます。 また、グラフ内のデータを選択するボタンを切り替えることもできます。

### <a name="low-vision-support"></a>弱視のサポート
* 複数の系列が表示されている場合は、**凡例**が必要です。
* **GridStyle** を両方の軸を示す GridStyle.All に設定することを検討してください。 これにより、すべてのユーザーがデータの規模を正確に判断できるようになります。
* **縦棒グラフ**の場合は、**マーカー**を **true** に設定することを検討してください。 これにより、色覚や視力に障碍のあるユーザーが列の値を判断できるようになります。

### <a name="keyboard-support"></a>キーボードのサポート
* **[TabIndex](properties-accessibility.md)** を 0 以上にして、キーボード ユーザーがそこに移動できるようにする必要があります。

    > [!NOTE]
  > キーボード ユーザーがグラフに移動すると、グラフ内のデータを選択するボタンを切り替えることができます。
