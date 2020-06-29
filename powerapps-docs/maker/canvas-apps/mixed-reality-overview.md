---
title: Power Apps で Mixed Reality コンポーネントを使用する (プレビュー)
description: Power Apps で拡張現実機能を使用して、実際の世界で 3D モデルと 2D 画像を表示および操作し、測定を行い、3D デジタル形状を作成して表示します。
author: iaanw
manager: shellyha
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 5/4/2020
ms.author: iawilt
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 2e29e9464241f92132ca3b5a71ad2a18e1a29f39
ms.sourcegitcommit: a5b3871e623cebd7de64a0c386503832a2d04c03
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "3331692"
---
# <a name="add-mixed-reality-components-to-your-canvas-app-preview"></a>Mixed Reality コンポーネントをキャンバス アプリに追加する (プレビュー)

[!INCLUDE [cc-beta-prerelease-disclaimer.md](../../includes/cc-beta-prerelease-disclaimer.md)]

さまざまな Mixed Reality (MR) コンポーネントをキャンバス アプリに追加して、複数の 3D および Mixed Reality シナリオをサポートできます。

コンポーネントは、特定のシナリオのニーズに応えることができるコントロールのグループです。 たとえば、これらの MR コンポーネントを使用して次の点を実行できます:

- 3D コンテンツの表示と操作
- 3D コンテンツと 2D 画像をカメラからのフィードにオーバーレイする
- MR 搭載のデバイスを使用して距離、面積、体積を測定する
- MR オーバーレイを通じて現実世界のスペースを特定する

コンポーネントの詳細と独自のコンポーネントの作成方法については、[Power Apps component framework のドキュメント](/powerapps/developer/component-framework/custom-controls-overview) をお読みください。

> [!NOTE]
> Mixed Reality コンポーネントは現在、実験的なプレビュー機能であり、[Power Apps プレビュー プログラム環境](/power-platform/admin/preview-environments) の [https://preview.create.powerapps.com](https://preview.create.powerapps.com) でのみ使用可能です。

次の事前に構築されたコンポーネントは、Mixed Reality シナリオに使用できます:

- [3D 形式で​​表示](mixed-reality-component-view-3d.md)
- [Mixed Reality で表示する](mixed-reality-component-view-mr.md)
- [Mixed Reality で測定する](mixed-reality-component-measure-distance.md)
- [Mixed Reality で図形を表示する](mixed-reality-component-view-shape.md)

## <a name="prerequisites"></a>前提条件

1. [各アプリの Mixed Reality 機能を有効にする](#enable-the-mixed-reality-features-for-each-app)。
2. Mixed Reality 対応のデバイスが必要です。 任意の [ARCore 対応デバイス](https://developers.google.com/ar/discover/supported-devices) がサポートされ、[特定の Apple iOS デバイス](https://www.apple.com/augmented-reality/) もサポートされます。
3. [Power Apps プレビュープログラム環境](/power-platform/admin/preview-environments) を使用します。

### <a name="enable-the-mixed-reality-features-for-each-app"></a>各アプリの Mixed Reality 機能を有効にする

作成するアプリごとに、Mixed Reality 機能を有効にする必要があります:

1. [https://preview.create.powerapps.com](https://preview.create.powerapps.com) にある Power Apps Studio で、編集するアプリを開きます。

2. トップ メニューから、**ファイル**を選択します。

    ![](./media/augmented-overview/augmented-overview-file.png)

3. **設定**タブに移動し、**詳細設定**を選択し、下にスクロールして **Mixed Reality 機能**オプションを見つけます。 オプションを**オン**に設定します。

    ![](./media/augmented-overview/augmented-enable-mixed-reality.png)

4. 戻り矢印アイコンを選択して、アプリの編集に戻る

    ![](./media/augmented-overview/augmented-overview-back.png)

5. **メディア**および **Mixed Reality** で**挿入**ウィンドウを開いて Mixed Reality コンポーネントを表示します。

    ![](./media/augmented-overview/augmented-overview-insert-all.png)

## <a name="next-steps"></a>次の手順

アプリへのコンポーネントのインストールを開始します:

- **[3D で表示](mixed-reality-component-view-3d.md)** コンポーネントを使用して 3D コンテンツを表示します。
- **[Mixed Reality で表示](mixed-reality-component-view-mr.md)** コンポーネントを使用して、現実世界の画像と 3D コンテンツを表示します。
- **[Mixed Reality で測定](mixed-reality-component-measure-distance.md)** コンポーネントを使用して、距離、面積、体積を測定します。
- **[Mixed Reality で図形表示](mixed-reality-component-view-shape.md)** コンポーネントを使用して、事前定義された 3D 形状を作成して表示します
