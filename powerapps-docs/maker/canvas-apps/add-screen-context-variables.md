---
title: キャンバス アプリにスクリーンを追加し、スクリーン間を移動する | Microsoft Docs
description: Power Apps でキャンバス アプリにスクリーンを追加し、次へおよび戻る矢印を使用してスクリーン間を移動する
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 02/03/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: cbe6173c94f001874b126a5b8ecb1bdf9ad21b70
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3306476"
---
# <a name="add-a-screen-to-a-canvas-app-and-navigate-between-screens"></a>キャンバス アプリにスクリーンを追加し、スクリーン間を移動する

複数のスクリーンがあるキャンバス アプリを作成し、ユーザーがスクリーン間を移動する方法を追加します。

## <a name="add-and-rename-a-screen"></a>スクリーンの追加および名前の変更

1. **ホーム**タブで、**新しいスクリーン**を選択し、次に追加するスクリーンの種類を選択します。

    ![ホーム タブのスクリーン追加のオプション](./media/add-screen-context-variables/add-screen.png)

2. 右側のウィンドウで、(**プロパティ** タブのすぐ上にある) スクリーンの名前を選択し、次に**ソース**を入力します。

    ![既定のスクリーンの名前を変更する](./media/add-screen-context-variables/name-source-screen.png)

3. 別のスクリーンを追加し、**ターゲット**という名前を付けます。

    ![左側のナビゲーション バーの 2 つのスクリーン](./media/add-screen-context-variables/two-screens-in-nav.png)

## <a name="reorder-screens"></a>スクリーンの並べ替え

左側のナビゲーション バーで、上または下に移動するスクリーンにカーソルを置いて、表示される省略記号ボタンを選択し、次に**上へ移動**または**下へ移動**を選択します。

![スクリーンの並べ替え](./media/add-screen-context-variables/reorder-screen.png)

> [!NOTE]
> アプリを開くと、通常、コントロールの階層一覧の一番上のスクリーンが最初に表示されます。 ただし、**[OnStart](controls/control-screen.md)** プロパティを **[Navigate](functions/function-navigate.md)** 関数を含む式に設定して、別のスクリーンを指定することができます。

## <a name="add-navigation"></a>ナビゲーションの追加

1. **ソース** スクリーンが選択された状態で、**挿入**タブを開き、**アイコン**を選択し、次に**次の矢印**を選択します。  

    ![挿入タブの図形オプション](./media/add-screen-context-variables/add-next-arrow.png)

2. (オプション) 矢印を移動して、スクリーンの右下隅に表示されるようにします。

3. 矢印が選択された状態で、**アクション** タブを選択し、次に**移動**を選択します。

    矢印の **[OnSelect](controls/properties-core.md)** プロパティが、自動的に**移動**関数に設定されます。

    ![移動関数に設定された OnSelect プロパティ](./media/add-screen-context-variables/onselect-default.png)

    ユーザーが矢印を選択すると、**ターゲット** スクリーンがフェードインします。

4. **ターゲット**スクリーンで、**戻る矢印**を追加し、その **[OnSelect](controls/properties-core.md)** プロパティをこの数式に設定します。

    `Navigate(Source, ScreenTransition.Fade)`

5. Alt キーを押しながら、各スクリーンの矢印を選択してスクリーン間を切り替えます。

## <a name="more-information"></a>詳細

[スクリーン コントロールのリファレンス](controls/control-screen.md)