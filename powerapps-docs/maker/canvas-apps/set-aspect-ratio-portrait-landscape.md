---
title: キャンバス アプリの画面サイズと向きを変更する | Microsoft Docs
description: Power Apps でキャンバス アプリの画面サイズと向きなどの設定を変更するための詳しい手順
author: emcoope-MSFT
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/30/2020
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8ee60fb5fc8b681f70a591adb0f7a82b1fe687d4
ms.sourcegitcommit: b75b29d58adf1547c9fcd3ddd1f14f69fb7f572b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/02/2020
ms.locfileid: "3330298"
---
# <a name="change-screen-size-and-orientation-of-a-canvas-app-in-power-apps"></a>Power Apps でキャンバス アプリの画面のサイズと向きを変更する

キャンバス アプリは、その画面のサイズと向きを変更することでカスタマイズできます。

## <a name="change-screen-size-and-orientation"></a>画面のサイズと表示方向の変更

1. [Power Apps](https://make.powerapps.com) にサインインします。
1. アプリを開き、[編集](edit-app.md) を行います。
1. **ファイル**メニューを選択します。
1. **設定**を選択します。
1. **画面サイズ + 向き**を選択します。

    ![アプリの画面のサイズと向きを変更するためのオプション](./media/set-aspect-ratio-portrait-landscape/size-orientation.png "画面サイズ + 向きのオプション")

1. **向き**の一覧で、**縦**または**横**を選択します。 <br> 

    ![電話レイアウトの向き](./media/set-aspect-ratio-portrait-landscape/phone-layout-orientation.png "電話レイアウトの向き")

1. (タブレット アプリのみ) **アスペクト比**で、次のいずれかの手順を実行します:

    - このアプリのターゲット デバイスと一致する比率を選択します。
    - **カスタム**を選び、独自のサイズを設定してから、50 - 3840 の幅と 50 - 2160 の高さを指定します。

    ![タブレット アプリの縦横比の変更](./media/set-aspect-ratio-portrait-landscape/aspect-tablet.png "タブレットのアスペクト比")
    
    > [!NOTE]
    > **サイズ**は、**タブレット**レイアウトのアプリのみで利用可能です。

1. **全体表示**で、**オン**または**オフ**を指定します。

    ![全体表示](./media/set-aspect-ratio-portrait-landscape/scale-to-fit.png "全体表示")

    この設定は既定でオンになっているため、デバイスの使用可能なスペースに合わせてアプリ画面のサイズが変更されます。 この設定がオンの場合、アプリの **Width** プロパティは **DesignWidth** と一致し、アプリの **Height** は **DesignHeight** と一致します。

    この設定をオフにすると、アプリは実行されているデバイスのアスペクト比に合わせて調整され、利用可能なすべてのスペースを占有します。 アプリはスケールされないため、画面にさらに多くの情報を表示できます。

    この設定をオフにすると、**アスペクト比をロック**は自動的にオフになり、無効になります。 さらに、全ての画面の **Width** プロパティが `Max(App.Width, App.DesignWidth)` に設定され、**Height** プロパティは `Max(App.Height, App.DesignHeight)` に設定されるので、アプリが実行されているウィンドウのサイズを追跡できるようにします。 この変更により、さまざまなデバイスとウィンドウのサイズに対応するアプリを作成できます。 詳細: [レスポンシブ レイアウトを作成する](create-responsive-layout.md)

1. **縦横比を固定する**で、**オン**または**オフ**を指定します。

    ![縦横比を固定](./media/set-aspect-ratio-portrait-landscape/lock-aspect-ratio.png "縦横比を固定")

    この設定がオンの場合、アプリはデバイスに関係なく、手順 2 と 3 で指定した画面の向きとアスペクト比を保持します。 たとえば、Web ブラウザーで実行されている電話アプリでは、電話の比率を保持し、ウィンドウを塗りつぶす代わりに両側に暗いバーを表示します。

    この設定がオフの場合、アプリは実行されているデバイスのアスペクト比に合わせて調整されます (必要であれば UI は歪みます)。

1. **向きを固定する**で、**オン**または**オフ**を指定します。

    ![向きを固定する](./media/set-aspect-ratio-portrait-landscape/lock-orientation.png "向きを固定する")

    アプリの向きを固定すると、指定した向きがアプリで保持されます。 画面の向きが異なるデバイスでアプリが実行されている場合、アプリの表示は正しく行われず、望ましくない結果が表示される可能性があります。 アプリの向きの固定を解除すると、アプリが実行されているデバイスの画面の向きに合うように自動的に調整されます。

    **実験的機能**で、**詳細設定**の**埋め込みの外観を最適化する**を有効にして、アプリの向きを変更することもできます。 この左上の機能を使用すると、アプリが埋め込まれているときにアプリが配置され、ホスティング キャンバスの背景色が白に変更されます。

    ![埋め込みのエクスペリエンス](./media/set-aspect-ratio-portrait-landscape/embedding-experience.png "埋め込みのエクスペリエンス")

1. アプリを[保存して公開](save-publish-app.md)します。

## <a name="next-step"></a>次のステップ

[キャンバス アプリのレスポンシブ レイアウトの作成](create-responsive-layout.md)