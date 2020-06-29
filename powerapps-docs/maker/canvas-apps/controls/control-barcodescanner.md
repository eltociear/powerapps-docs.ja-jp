---
title: 'Web バーコード スキャナー コントロール: リファレンス | Microsoft Docs'
description: プロパティとサンプルを含む、バーコード スキャナー コントロールに関する情報
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
ms.openlocfilehash: a116d812f8be7d8c1fb15ba2b05805536240084c
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3306269"
---
# <a name="web-barcode-scanner-control-experimental-in-power-apps"></a>Power Apps での Web バーコード スキャナー コントロール (試験段階)

従来のバーコード スキャナー コントロールは廃止されましたが、Web ブラウザーでコードをスキャンするのに役立つ場合があります。

## <a name="description"></a>内容

ユーザーがすべてのデバイスでバーコードをスキャンできるように、コントロールではアプリにカメラ フィードを表示します。 パフォーマンス低下のためコントロールは廃止され、モバイル **[バーコード スキャナー](control-new-barcode-scanner.md)** コントロールがこのコントロールに代わるものです。

## <a name="key-properties"></a>主要なプロパティ

**バーコード スキャナー** – 複数のバーコード スキャナーを備えるデバイスで、アプリが使用するバーコード スキャナーの数値 ID。

## <a name="additional-properties"></a>追加のプロパティ

**[AccessibleLabel](properties-accessibility.md)** – スクリーン リーダー用のラベル。

**[BorderColor](properties-color-border.md)** – コントロールの境界線の色。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線が**実線**、**破線**、**点線**、または**なし**かどうか。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さ。

**[DisplayMode](properties-core.md)** – コントロールがユーザー入力を許可するか (**編集**)、データのみを表示するか (**表示**)、または無効にするか (**無効**) どうか。

**[高さ](properties-size-location.md)** – コントロールの上端と下端間の距離。

**ShowLiveBarcodeDetection** – バーコード検出の状態を示す視覚的な手掛かりが表示されるかどうか。 黄色の四角形は、検査されている領域を表します。 四角形内の緑色の線は、バーコードの識別に成功したことを示します。

**ストリーム** – **StreamRate** プロパティに基づいて自動的に更新された画像。

**StreamRate** – **ストリーム** プロパティの画像を更新する頻度 (ミリ秒単位)。  この値の範囲は、100 (0.1 秒) から 3,600,000 (1 時間) です。

**テキスト** – スキャナーによって最後に識別されたバーコードの値。

**[ツールヒント](properties-core.md)** – ユーザーがコントロールにカーソルを置くときに表示される説明テキスト。

**[表示](properties-core.md)** – コントロールが表示されるか非表示になるか。

**[幅](properties-size-location.md)** – コントロールの左端と右端間の距離。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離。

## <a name="related-functions"></a>関連する関数

[**Patch**( *DataSource*、*BaseRecord*、*ChangeRecord* )](../functions/function-patch.md)

## <a name="example"></a>例

### <a name="add-photos-to-an-image-gallery-control"></a>画像ギャラリー コントロールに写真を追加する

1. **バーコード スキャナー** コントロールを追加し、**Mybarcode scanner** と名前を付ける

    [コントロールの追加、名前付け、構成](../add-configure-controls.md) についてはこちらをご覧ください。

1. **ラベル** コントロールを追加し、その出力をバーコード スキャナーの**テキスト** プロパティに設定します。

1. **BarcodeType** プロパティで設定される種類のバーコードをスキャンします。

    ラベルにはスキャンしたバーコードが表示されます。

## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン

### <a name="video-alternatives"></a>ビデオの代替手段

* **[テキスト](properties-core.md)** をバーコード スキャナーの**テキスト**に設定した **[ラベル](control-text-box.md)** を追加することを検討してください。 バーコード スキャナーは識別されたバーコード値を表示しないため、上記のようにすると視覚障碍を持つユーザーだけでなく、誰でもスキャナーにアクセスできるようになります。

### <a name="screen-reader-support"></a>スクリーン リーダー サポート

* **[AccessibleLabel](properties-accessibility.md)** が存在する必要があります。

    > [!NOTE]
  > 新しいバーコードが検出されると、スクリーン リーダーから通知されます。 値は通知されません。 バーコードが表示されている限り、スクリーン リーダーから同じバーコードがまだ識別中であることが 5 秒ごとにユーザーに通知されます。
