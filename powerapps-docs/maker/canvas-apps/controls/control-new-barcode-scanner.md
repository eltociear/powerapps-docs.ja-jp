---
title: 'バーコード スキャナー コントロール: リファレンス | Microsoft Docs'
description: プロパティとサンプルを含む、バーコード スキャナー コントロールに関する情報
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 11/25/2018
ms.author: chmoncay
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d2499a597295147cea1b39bb18fee2cbb056b413
ms.sourcegitcommit: ebb4bb7ea7184e31dc95f0c301ebef75fae5fb14
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/03/2020
ms.locfileid: "3309006"
---
# <a name="barcode-scanner-control-for-canvas-apps"></a>キャンバス アプリのバーコード スキャナー コントロール

Android または iOS デバイスでバーコード、QR コード、およびデータ マトリックス コードをスキャンします。 Web ブラウザーではサポートされていません。

## <a name="description"></a>内容

コントロールは、Android または iOS デバイスでネイティブのスキャナーを開きます。 スキャナーは、ビューにあるバーコード、QR コード、データ マトリックス コードを自動的に検出します。 このコントロールでは、Web ブラウザーでのスキャンをサポートしていません。

## <a name="key-properties"></a>主要なプロパティ

**値** – 最後にスキャンされたコードのテキスト値を含む出力プロパティ。

**タイプ** – 最後にスキャンされたコードのタイプを含む出力プロパティ。

**OnScan** – バーコードが正常にスキャンされたときのアプリの応答方法。

**OnCancel** – ユーザーがバーコードのスキャンをキャンセルするときのアプリの応答方法。

**BarcodeType** - スキャンするバーコード タイプ。 複数のバーコード タイプを連結することにより、それらを対象にできます。 例: BarcodeType.Code128 & BarcodeType.Code39  **既定: 自動**

**PreferFrontCamera** - 利用可能な場合、前面カメラをスキャンに使用するかどうか。

**FlashlightEnabled** - スキャナーを開くときに、懐中電灯が自動的に有効になるかどうか。

## <a name="additional-properties"></a>追加のプロパティ

**テキスト** - スキャナーを起動するボタンに表示されるテキスト。

**[BorderColor](properties-color-border.md)** – コントロールの境界線の色。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線が**実線**、**破線**、**点線**、または**なし**かどうか。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さ。

**[DisplayMode](properties-core.md)** – コントロールがユーザー入力を許可するか (**編集**)、データのみを表示するか (**表示**)、または無効にするか (**無効**) どうか。

**[高さ](properties-size-location.md)** – スキャナーをアクティブ化するボタンの高さ。

**[ツールヒント](properties-core.md)** – ユーザーがコントロールにカーソルを置くときに表示される説明テキスト。

**タイプ** – 最後に成功したスキャンで検出されたコードのタイプ。

**[表示](properties-core.md)** – コントロールが表示されるか非表示になるか。

**[幅](properties-size-location.md)** – スキャナーをアクティブ化するボタンの幅。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離。

## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
**[ボタン](control-button.md)** コントロール用の同じガイドラインが**バーコード スキャナー** コントロールに適用されます。それはスキャンを起動するボタンであるためです。

### <a name="visual-alternatives"></a>視覚化の代替手段
* バーコード スキャナーは、スキャン結果を表示しないボタンです。 **[ラベル](control-text-box.md)** コントロールでスキャン結果を表示することを検討してください。 ラベルの **[テキスト](properties-core.md)** プロパティをバーコード スキャナーの**値**プロパティに設定します。 ラベルの **[ライブ](properties-accessibility.md)** プロパティを**ポライト**に設定して、スクリーン リーダー ユーザーに変更が通知されるようにします。 この変更により、スキャンした値は、視覚的な機能に関係なく、すべてのユーザーがアクセスできるようになります。

* 視覚や動作に障碍のあるユーザーは、バーコードにカメラをポイントしたくない場合があります。 ユーザーがバーコードを入力するため、**[テキスト入力](control-text-input.md)** コントロールなどの別の形式の入力を追加することを検討してください。

## <a name="barcode-availability-by-device"></a>デバイス別のバーコードの可用性

| バーコードの種類 | Android | iOS |
|--------------|:-------:|:---:|
|QR_CODE|✔|✔|
|DATA_MATRIX|✔|✔|
|UPC_A|✔|✔|
|UPC_E|✔|✔|
|EAN_8|✔|✔|
|EAN_13|✔|✔|
|CODE_39|✔|✔|
|CODE_93|✔|✔|
|CODE_128|✔|✔|
|CODABAR|✔|✖|
|ITF|✔|✔|
|RSS14|✔|✖|
|PDF_417|✔|✔|
|RSS_EXPANDED|✔|✖|
|MSI|✖|✖|
|AZTEC|✔|✔|

**注意:** PDF_417 および AZTEC は自動モードではサポートされていません
