---
title: スクロール スクリーンをキャンバス アプリに追加する| Microsoft Docs
description: Power Apps で、スクリーンがキャンバス アプリで一度に表示できるより多くの種類のコンテンツを表示するようにユーザーがスクロールできるスクリーンを作成します。
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/25/2016
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: de0aba95b4bb5c3a308b0b86b739302dc0dc70e3
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3306499"
---
# <a name="add-a-scrolling-screen-to-a-canvas-app-in-power-apps"></a>Power Apps でスクロール スクリーンをキャンバス アプリに追加する

キャンバス アプリで、ユーザーがスクロールしてさまざまな項目を表示できるスクリーンを作成します。 たとえば、ユーザーがスクロールすると表示できるデータを複数のグラフで表示する電話アプリを作成します。

セクションに複数のコントロールを追加すると、それが電話アプリであるかまたはタブレット PC アプリであるかに関係なく、コントロールはそのセクション内で相対位置を維持します。 スクリーンのサイズおよび表示方向によってセクションの配置方法を決めることができます。  

[!INCLUDE [app-customization-requirements](../../includes/app-customization-requirements.md)]

## <a name="create-a-scrolling-screen"></a>スクロール スクリーンを作成する

1. **ホーム**タブで、**新しいスクリーン**をクリックまたはタップします。

    ![アプリにスクリーンを追加するオプション][1]

2. **ホーム** タブで、**レイアウト**をクリックまたはタップし、次に無限スクロールのキャンバスを追加するオプションをクリックまたはタップします。  
   
    ![無限スクロールのキャンバスを追加するオプション][2]
   
    キャンバスが追加されます。  
   
    ![既定で表示される無限スクロールのキャンバスのスクリーン][3]

## <a name="add-elements"></a>要素を追加する
それでは、キャンバスにコントロールをいくつか追加して、スクロール スクリーンの動作を確認しましょう。

1. 追加したキャンバスで、**挿入タブから項目を追加**をクリックまたはタップします。
   
    ![][4]
2. **挿入**タブで、**グラフ**をクリックまたはタップし、次に**縦棒グラフ**をクリックまたはタップします。
   
    ![縦棒グラフを追加するオプション][5]
   
    縦棒グラフはスクリーンの最初のカードに表示されます。  
   
    ![既定の縦棒グラフ][7]
3. **挿入**タブで、**テキスト**をクリックまたはタップし、次に**ペン入力**をクリックまたはタップします。  
   
    ![ペン コントロールを追加するオプション][8]
4. グラフの下部にペン コントロールを移動し、ペン コントロールのサイズを変更してカードの下部を含めます。  
   
    ![ペン コントロールを移動し、サイズを変更する][9]

## <a name="add-a-section"></a>セクションの追加
それでは、別のコントロールで別のカードを追加してみましょう。

1. スクリーンの下部の近くで**セクションの追加**をクリックまたはタップします。  
   
    ![セクションを追加するオプション][10]
   
    新しいカードがスクリーンに追加されます。  
   
    ![既定のセクションの下の新しいカード][11]
2. カードが選択されている状態のまま、**挿入**タブに移動し、**グラフ**をクリックまたはタップし、次に**折れ線グラフ**をクリックまたはタップします。
   
    新しいグラフが大きすぎて他のコントロールとはスクリーンに表示されません。  
   
    ![新しいカードの下部に追加された折れ線グラフ][12]
3. F5 キーを押して (または右上隅近くの再生アイコンをクリックまたはタップして) プレビュー モードを開きます。
   
    ![プレビュー モードを開く](./media/add-scrolling-screen/open-preview.png)
4. 下にスクロールして、新しい折れ線グラフを表示します。  
   
    ![プレビューに折れ線グラフが表示されます][13]

[1]: ./media/add-scrolling-screen/add-screen.png
[2]: ./media/add-scrolling-screen/add-canvas.png
[3]: ./media/add-scrolling-screen/default-canvas.png
[4]: ./media/add-scrolling-screen/insert-visual.png
[5]: ./media/add-scrolling-screen/add-chart.png
[7]: ./media/add-scrolling-screen/default-chart.png
[8]: ./media/add-scrolling-screen/add-pen.png
[9]: ./media/add-scrolling-screen/move-resize-pen.png
[10]: ./media/add-scrolling-screen/add-section.png
[11]: ./media/add-scrolling-screen/new-card.png
[12]: ./media/add-scrolling-screen/add-line-chart.png
[13]: ./media/add-scrolling-screen/line-chart-preview.png
