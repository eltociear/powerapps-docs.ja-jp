---
title: Power Apps で Mixed Reality コンポーネントを使用する (プレビュー)
description: Power Apps で拡張現実機能を使用して、実際の世界で 3D モデルと 2D 画像を表示および操作し、測定を行い、3D デジタル形状を作成して表示します。
author: iaanw
manager: shellyha
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 5/22/2020
ms.author: iawilt
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d20ccde8e3c5ca07d48ef8c800e76e9e681a06de
ms.sourcegitcommit: 5e195cb09ab43d31c854efdc4e7e8dc9f1955ca4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "3418653"
---
# <a name="add-mixed-reality-components-to-your-canvas-app-preview"></a>Mixed Reality コンポーネントをキャンバス アプリに追加する (プレビュー)

[!INCLUDE [cc-beta-prerelease-disclaimer.md](../../includes/cc-beta-prerelease-disclaimer.md)]

さまざまな Mixed Reality (MR) コンポーネントをキャンバス アプリに追加して、複数の 3D および Mixed Reality シナリオをサポートできます。

コンポーネントは、特定のシナリオのニーズに応えることができるコントロールのグループです。 たとえば、これらの MR コンポーネントを使用して次の点を実行できます:

- 3D コンテンツの表示と操作。
- 3D コンテンツと 2D 画像をカメラからのフィードにオーバーレイする。
- MR 搭載のデバイスを使用して距離、面積、体積を測定する。
- MR オーバーレイを通じて現実世界のスペースを特定する。

コンポーネントの詳細と独自のコンポーネントの作成方法については、[Power Apps component framework のドキュメント](/powerapps/developer/component-framework/custom-controls-overview) をお読みください。


以下の事前構築済みコンポーネントは、Mixed Reality シナリオに使用できます:


- [3D 形式で​​表示](mixed-reality-component-view-3d.md)
- [Mixed Reality で表示する](mixed-reality-component-view-mr.md)
- [Mixed Reality で測定する](mixed-reality-component-measure-distance.md)
- [Mixed Reality で図形を表示する](mixed-reality-component-view-shape.md)

## <a name="prerequisites"></a>前提条件

1. [各アプリの Mixed Reality 機能を有効にする](#enable-the-mixed-reality-features-for-each-app)。
2. Mixed Reality 対応のデバイスが必要です。 任意の [ARCore 対応デバイス](https://developers.google.com/ar/discover/supported-devices) がサポートされ、[特定の Apple iOS デバイス](https://www.apple.com/augmented-reality/) もサポートされます。

### <a name="enable-the-mixed-reality-features-for-each-app"></a>各アプリの Mixed Reality 機能を有効にする

作成するアプリごとに、Mixed Reality 機能を有効にする必要があります:


1. [https://preview.create.powerapps.com](https://preview.create.powerapps.com) の Power Apps Studio で編集するアプリを開きます。


2. トップ メニューから、**ファイル**を選択します。

    ![ファイルの選択](./media/augmented-overview/augmented-overview-file.png "ファイルの選択")

3. **設定**タブに移動し、**詳細設定**を選択し、下にスクロールして **Mixed Reality 機能**オプションを見つけます。 オプションを**オン**に設定します。

    ![Mixed Reality 機能のオプションをオンに設定します](./media/augmented-overview/augmented-enable-mixed-reality.png "Mixed Reality 機能のオプションをオンに設定します")

4. 戻り矢印アイコンを選択して、アプリの編集に戻ります。

    ![戻り矢印アイコンを選択します](./media/augmented-overview/augmented-overview-back.png "戻り矢印アイコンを選択します")

5. **メディア**および **Mixed Reality** で**挿入**ウィンドウを開いて Mixed Reality コンポーネントを表示します。

    ![メディアと Mixed Reality の Mixed Reality コンポーネントを参照してください](./media/augmented-overview/augmented-overview-insert-all.png "メディアと Mixed Reality の Mixed Reality コンポーネントを参照してください")

## <a name="next-steps"></a>次の手順

アプリへのコンポーネントのインストールを開始します:

- **[3D で表示](mixed-reality-component-view-3d.md)** コンポーネントを使用して 3D コンテンツを表示します。
- **[Mixed Reality で表示](mixed-reality-component-view-mr.md)** コンポーネントを使用して、現実世界の画像と 3D コンテンツを表示します。
- **[Mixed Reality で測定](mixed-reality-component-measure-distance.md)** コンポーネントを使用して、距離、面積、体積を測定します。
- **[Mixed Reality で図形表示](mixed-reality-component-view-shape.md)** コンポーネントを使用して、事前定義された 3D 形状を作成して表示します。
