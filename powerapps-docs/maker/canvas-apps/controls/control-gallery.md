---
title: 'ギャラリー コントロール: リファレンス | Microsoft Docs'
description: プロパティとサンプルを含む、ギャラリー コントロールに関する情報
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/16/2020
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ca48ccaf4aca72301d3a8b7f2eb79885d7c7cdf5
ms.sourcegitcommit: 6acc6ac7cc1749e9681d5e55c96613033835d294
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "3309121"
---
# <a name="gallery-control-in-canvas-apps"></a>キャンバス アプリのギャラリー コントロール

その他のコントロールが含まれており、一連のデータを表示するコントロール。

## <a name="description"></a>内容

**ギャラリー** コントロールにデータ ソース内のさまざまなレコードを表示できます。各レコードにさまざまなタイプのデータを含めることができます。 たとえば、**ギャラリー** コントロールを使用して、各連絡先の名前、住所、電話番号を含む連絡先情報を表示する各項目に複数の連絡先を表示します。

各データ フィールドは、**ギャラリー** コントロール内の個別のコントロールに表示されます。 さらに、それらのコントロールをテンプレートで構成できます。 テンプレートがギャラリー内の最初の項目として表示されます:

- 水平/横方向の**ギャラリー** コントロールの左端。
- 垂直/縦方向の**ギャラリー** コントロールの上部。 

テンプレートで加えた変更は、**ギャラリー** コントロール全体に反映されます。

ギャラリーで画像やテキストを表示する事前定義されたテンプレート、および高さが可変の項目のギャラリーを利用できます。

## <a name="limitations"></a>制限

ユーザーが、すべての項目が読み込まれる前に**伸縮可能な高さ**ギャラリーコントロールをスクロールする場合、データの読み込みが完了すると、現在表示されている項目が押し出されて表示されなくなる場合があります。 この問題を回避するには、**伸縮可能な高さ**バリアントの代わりに、標準の**ギャラリー** コントロールを使用します。

## <a name="key-properties"></a>主要なプロパティ

[既定](properties-core.md) – アプリの起動時に、ギャラリーで選択されるデータ ソースからの項目またはレコード。

[項目](properties-core.md) – ギャラリー、リスト、グラフなどのコントロールに表示されるデータのソース。

**Selected** – 選択された項目です。

## <a name="additional-properties"></a>追加のプロパティ

[AccessibleLabel](properties-accessibility.md) – スクリーン リーダー用のギャラリーのラベル (含まれている項目ではない)。 項目の一覧について説明する必要があります。

**AllItems** – ギャラリーのテンプレートの一部である追加のコントロール値を含む、ギャラリーのすべての項目。

[BorderColor](properties-color-border.md) – コントロールの境界線の色。

[BorderStyle](properties-color-border.md) – コントロールの境界線が**実線**、**破線**、**点線**、または**なし**かどうか。

[BorderThickness](properties-color-border.md) – コントロールの境界線の太さ。

**DelayItemLoading** - 画面が最初に読み込まれるまで、項目 (行) の読み込みを遅延させます。

[DisplayMode](properties-core.md) – コントロールがユーザー入力を許可するか (**編集**)、データのみを表示するか (**表示**)、または無効にするか (**無効化**)。

[塗りつぶし](properties-color-border.md) – コントロールの背景色。

[高さ](properties-size-location.md) – コントロールの上端と下端間の距離。

**ItemAccessibleLabel** – スクリーン リーダー用の各ギャラリー項目のラベル。 各アイテムについて説明する必要があります。

**LoadingSpinner** (**なし**、**コントロール**または**データ**) - なしの場合、スピナーは表示されません。 コントロール時 | 空の行が表示されるレンダリング パスが発生すると、データ、スピナーが表示されます。

**LoadingSpinnerColor** - スピナーを読み込む塗りつぶしの色。  既定では、BorderColor に設定されています。

**NavigationStep** – **ShowNavigation** プロパティが **true** に設定され、ユーザーがそのギャラリーの両端にあるナビゲーション矢印を選択する場合、ギャラリーをどの程度スクロールするか。

**選択可能** – ギャラリー項目を選択できるかどうか。 **true** に設定した場合、スクリーン リーダーはギャラリーを選択可能なリストとして識別します。 さらに、項目を選択することにより選択します。 **false** に設定した場合、スクリーン リーダーはギャラリーを通常のリストとして識別し、項目を選択しても選択されません。

**ShowNavigation** – ギャラリーの各端に矢印を表示し、矢印の選択によりギャラリー内の項目をユーザーがスクロールできるようにするかどうか。

**ShowScrollbar** – ユーザーがャラリーにカーソルを置くときにスクロールバーが表示されるかどうか。

**スナップ** – ユーザーがギャラリーをスクロールするとき、次の項目が完全に表示されるように自動的にスナップするかどうか。

**TemplateFill** – ギャラリーの背景色。

**TemplatePadding** – ギャラリー内の項目間の距離。

**TemplateSize** – 垂直/縦向きのギャラリーのテンプレートの高さ。 または、水平/横向きのギャラリーのテンプレートの幅。

**移行** – ユーザーがギャラリー内の項目にカーソルを置くときの視覚効果 (**ポップ**、**プッシュ**、または**なし**)。

[表示](properties-core.md) – コントロールが表示されるか非表示になるか。

[幅](properties-size-location.md) – コントロールの左端と右端間の距離。

**WrapCount** – 水平または垂直レイアウトに合わせて行または列ごとに表示される項目の数。

[X](properties-size-location.md) – コントロールの左端とその親コンテナまたはスクリーンの左端との間の距離。

[Y](properties-size-location.md) – コントロールの上端と親コンテナまたはスクリーンの上端との間の距離。

## <a name="related-functions"></a>関連する関数

[Filter( *DataSource*, *式* )](../functions/function-filter-lookup.md)

[リセット(*コントロール*)](../functions/function-reset.md) - ギャラリーを初期状態にリセットします。 初期状態には、最初の項目へのスクロールと、最初の項目または存在する場合はデフォルトの選択が含まれます。 

  > [!NOTE]
  > **リセット** コントロールは、ギャラリーのすべての子を再帰的にリセットしません。

## <a name="examples"></a>例

### <a name="show-and-filter-data"></a>データを表示およびフィルター処理する

- [テキストの表示](control-text-box.md#show-data-in-a-gallery)
- [画像の表示](control-image.md#show-a-set-of-images-from-a-data-source)
- [リスト オプションを選択してデータのフィルター処理](control-drop-down.md#example)
- [スライダーを調整してデータのフィルター処理](control-slider.md#example)

### <a name="get-data-from-the-user"></a>ユーザーからデータを取得する

- [テキストの取得](control-text-input.md#collect-data)
- [画像の取得](control-add-picture.md#add-images-to-an-image-gallery-control)
- [写真の取得](control-camera.md#examples)
- [サウンドの取得](control-microphone.md#examples)
- [図面の取得](control-pen-input.md#create-a-set-of-images)

## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン

### <a name="color-contrast"></a>色のコントラスト

ギャラリー項目内のどこかをクリックするとその項目が選択される場合、次の間に適切な色のコントラストが必要です:

- [BorderColor](properties-color-border.md) とギャラリーの外側の色 (境界線がある場合)。
- [塗りつぶし](properties-color-border.md) とギャラリーの外側の色 (境界線がない場合)。

### <a name="screen-reader-support"></a>スクリーン リーダー サポート

- [AccessibleLabel](properties-accessibility.md) が存在する必要があります。

    > [!NOTE]
    > ギャラリー内の項目が変更されると、スクリーン リーダーから通知されます。 **AccessibleLabel** についても通知されます。 これによって通知のコンテキストがわかるので、同じ画面上に複数のギャラリーがある場合にはさらに重要です。

- ギャラリー項目に複数のコントロールが含まれている場合は、**ItemAccessibleLabel** を使用してギャラリー項目のコンテンツを表示します。

- ユーザーにギャラリー項目を選択させる場合は、**選択可能**の値を **true** に設定します。 それ以外の場合は、その値を **false** に設定します。

- ギャラリー項目に複数のコントロールが含まれている場合は、**ItemAccessibleLabel** を使用してギャラリー項目のコンテンツの概要を提供します。

- ユーザーがギャラリー項目を選択するようになっているかどうかに応じて、**選択可能**を適切に設定する必要があります。

### <a name="keyboard-support"></a>キーボードのサポート

- **ShowScrollbar** を **true** に設定することを検討してください。 ほとんどのタッチ画面を持つデバイスでは、スクロールが始まるまでスクロール バーは表示されません。
- ギャラリー項目内のどこかをクリックするとその項目が選択されるようになっている場合、キーボード ユーザーがギャラリー項目を選択できる方法も必要です。 たとえば、**OnSelect** プロパティが **Select(Parent)** に設定されている [ボタン](control-button.md) を追加します。

    > [!NOTE]
  > ギャラリーの外部のコントロールは、ギャラリー内のキーボード ナビゲーション順には考慮されません。 ギャラリー内の [TabIndex](properties-accessibility.md) コントロールがスコープされます。 詳細については、[アクセシビリティのプロパティ](properties-accessibility.md) を参照してください。
