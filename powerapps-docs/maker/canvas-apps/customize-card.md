---
title: キャンバス アプリでカードをカスタマイズする | Microsoft Docs
description: キャンバス アプリの詳細フォームまたは編集フォームのカードに表示される既定のコントロールを変更する
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/18/2018
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 5bcf1515f72bdce0872f91c64b5ac4fe5028ee2c
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "3303831"
---
# <a name="customize-a-card-in-a-canvas-app"></a>キャンバス アプリでカードをカスタマイズする

基本的なカスタマイズ (カードのロック解除を伴わないカスタマイズ) は、コントロールの変更などによって行います。 高度なカスタマイズは、カードのロックを解除し、既定では利用できないコントロールをカードに追加するなどして行います。

概要については、[データ カードについて](working-with-cards.md)を参照してください。

## <a name="prerequisites"></a>前提条件

- [コントロールを追加して構成する](add-configure-controls.md)方法について学習します。
- このトピックは、概念全般を理解する目的でのみご覧いただいても、これらのトピックの手順を最初に完了して、手順ごとに実行していただいてもかまいません。

    1. [アプリを生成します](data-platform-create-app.md)。
    1. [ギャラリーをカスタマイズします](customize-layout-sharepoint.md)。
    1. [フォームをカスタマイズします](customize-forms-sharepoint.md)。

## <a name="customize-a-locked-card"></a>ロックされたカードのカスタマイズ

この手順では、カードのロックを解除せずに、**[Text-input](controls/control-text-input.md)** コントロールを **[Slider](controls/control-slider.md)** コントロールで置き換えます。

1. 生成してカスタマイズしたアプリで、左側のナビゲーション バーで **EditForm1** を選択し、右側のウィンドウの**プロパティ** タブで**フィールドの編集**を選択します。

1. フィールドのリストで、**従業員数**の下矢印を選択し、**コントロールの種類**下のリストを開きます。

    > [!div class="mx-imgBorder"]
    > ![数値カードのオプションのドロップダウン リスト](./media/customize-card/card-selector.png)

1. **スライダーを編集**を選択します。

    画面に変更内容が反映されます。

    > [!div class="mx-imgBorder"]
    > ![スライダー コントロールと EditForm1](./media/customize-card/add-slider.png)

## <a name="unlock-and-customize-a-card"></a>カードのロック解除とカスタマイズ

この手順では、カードのロックを解除して、追加した**Slider** コントロールの **Max** プロパティを更新します。

1. **EditForm1** で、**従業員数**カードの **Slider** コントロールを選択します。

    > [!div class="mx-imgBorder"]
    > ![スライダーを選択する](./media/customize-card/select-slider.png)

1. 右側のウィンドウにある**詳細設定**タブで、ロック アイコンを選択してカードのロックを解除します。

    > [!div class="mx-imgBorder"]
    > ![カードのロックを解除](./media/customize-card/lock-icon.png)

1. **Slider** コントロールの **Max** プロパティを 10,000 に設定します。

    > [!div class="mx-imgBorder"]
    > ![詳細設定タブの Max プロパティ](./media/customize-card/max-property.png)

    **Slider** コントロールはより正確な値を示します。

    > [!div class="mx-imgBorder"]
    > ![スライダー範囲 : 0-10,000](./media/customize-card/final-slider.png)

## <a name="next-steps"></a>次の手順

これで、アプリを生成し、ギャラリー、フォーム、カードをカスタマイズする方法の基本的な理解を得られたので、[独自のアプリを一から作成する](data-platform-create-app-scratch.md)ことができます。