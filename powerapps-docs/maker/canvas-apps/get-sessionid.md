---
title: セッション ID またはキャンバス アプリ ID を取得する | Microsoft Docs
description: Power Apps でのトラブルシューティングのためにセッション ID またはキャンバス アプリ ID を取得する方法
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 06/18/2018
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: bad3f118da62d0c4eb6c0873aa6aed03516a9085
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3306752"
---
# <a name="get-a-session-id-or-a-canvas-app-id"></a>セッション ID またはキャンバス アプリ ID を取得する
Power Apps で作成したキャンバス アプリに問題が発生した場合、問題のセッション ID、アプリ ID、またはその両方を Microsoft に提供すると、問題をより効果的にトラブルシューティングできます。

## <a name="get-the-session-id"></a>セッション ID を取得する

### <a name="when-editing-an-app"></a>アプリケーションを編集する場合
1. 左上隅にある**ファイル**を選択します。

1. **取引先企業** を選択します。

1. **診断**で、**セッションの詳細**を選択します。

    ![Power Apps Studio からセッション ID を取得する](media/get-sessionid/studio.png)

### <a name="when-running-an-app-in-a-browser"></a>アプリをブラウザーで実行する場合
1. 右上隅にある歯車アイコンを選択します。

1. **セッションの詳細**を選択します。

    ![ブラウザーからセッション ID を取得する](media/get-sessionid/browser.png)

### <a name="when-running-an-app-on-a-phone-or-a-tablet"></a>アプリを携帯電話またはタブレット PC で実行する場合
1. 右にスワイプします。

1. **セッションの詳細**をタップします。

    ![ブラウザーからセッション ID を取得する](media/get-sessionid/mobile.png)

### <a name="when-running-an-embedded-app-or-form"></a>埋め込みのアプリまたはフォームを実行する場合
1. 次の手順のいずれかを実行します。

    - Alt キーを押しながら、アプリまたはフォームを右クリックします。
    - アプリまたはフォームを、2 本の指で 1 から 2 秒間タップして離します。

1. **セッションの詳細**を選択します。

    ![埋め込みのアプリからセッション ID を取得する](media/get-sessionid/embedded.png)

## <a name="get-an-app-id"></a>アプリ ID を取得する
1. [Power Apps にサインインします](https://powerapps.microsoft.com)。

1. 左の端にある**アプリ**を選択します。

1. トラブルシューティングするアプリの省略記号 ( **. . .** ) を選択して、**詳細**を選択します。

    ![アプリの詳細に移動する](./media/get-sessionid/details.png)

    そのアプリの**詳細**ウィンドウの下部に、アプリ ID が表示されます。

    ![詳細からアプリ ID をコピーする](./media/get-sessionid/app-id.png)
