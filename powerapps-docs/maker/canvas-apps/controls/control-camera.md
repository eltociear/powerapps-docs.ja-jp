---
title: 'カメラ コントロール: リファレンス | Microsoft Docs'
description: プロパティとサンプルを含む、カメラ コントロールに関する情報
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 04/07/2020
ms.author: chmoncay
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 59c0f85dd71c9dc512e348d6d8ee9686d6945fa1
ms.sourcegitcommit: 6acc6ac7cc1749e9681d5e55c96613033835d294
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "3309098"
---
# <a name="camera-control-in-power-apps"></a>Power Apps でのカメラ コントロール

ユーザーがデバイスのカメラを使用して画像を撮影することを可能にするコントロール。

## <a name="description"></a>内容

**カメラ** コントロールを使用して、デバイスのカメラで画像をキャプチャします。  デバイスにはカメラが必要であり、ユーザーはアプリがカメラを使用することを許可する必要があります。 カメラ コントロールは、Web ブラウザーでの実行時にサポートされます。

直前にキャプチャした画像は、**写真**プロパティを通じて利用できます。 このプロパティを使用すると、画像は次のようになります:

- **画像コントロールで表示されます。** [画像](control-image.md) コントロールを使用して、キャプチャした画像を表示します。 詳細については、 [例](#examples) を参照してください。  
- **一時的に変数またはコレクションに保存されます。**  [設定](../functions/function-set.md) または [収集](../functions/function-clear-collect-clearcollect.md) 関数を使用して、 変数またはコレクションに画像を保存します。  コレクション内の複数の画像を同時に使用する場合には、デバイスのメモリが限られているため注意が必要です。 [SaveData](../functions/function-savedata-loaddata.md) および [LoadData](../functions/function-savedata-loaddata.md) 関数を使用して、画像をデバイスのローカル ストレージと [オフラインのシナリオ](../offline-apps.md) に移動します。
- **データベースに格納されます。**  [パッチ](../functions/function-patch.md) 関数を使用して、画像をデータベースに保存します。
- **base64 でエンコードされたテキスト文字列として送信されます。**  [JSON](../functions/function-json.md) 関数を使用して、画像を base64 エンコードします。

**ストリーム**、**StreamRate**、および **OnStream** プロパティを使用して、タイマーで画像を自動的にキャプチャします。たとえば、毎分画像をスナップしてタイムラプス シーケンスを作成します。

キャプチャされたメディアは、テキスト文字列 URI によって参照されます。 詳細については、[データ型ドキュメント](../functions/data-types.md#uris-for-images-and-other-media) をお読みください。

カメラ コントロールによって生成される画像は、通常カメラの最大解像度ではありません。 最大解像度の画像が必要な場合は、[画像の追加](control-add-picture.md) コントロールを使用してください。

## <a name="key-properties"></a>主要なプロパティ

**AvailableDevices** – デバイスで使用可能なカメラのテーブル。

テーブルには 2 つの列が含まれます: 
- **カメラ** プロパティで使用される *ID* 番号 
- カメラを識別するデバイスによって提供される*名前*。 一部のプラットフォームには、カメラを見つけるのに役立つ*前*または*後*が含まれる場合があります。

*注意*: テーブルのすべてのデバイスがアプリで使用できるとは限りません。  一部は、特定の目的を対象とした特殊なドライバーまたはアプリケーションである場合があります。  

**カメラ** – 使用するカメラの数値 ID。  複数のカメラを備えたデバイスで役立ちます。  

**OnStream** – **ストリーム** プロパティが更新された場合のアプリの反応方法。

**写真** – ユーザーが画像の撮影時にキャプチャされる画像。 

**ストリーム** – **StreamRate** プロパティに基づいて自動的に更新された画像。

**StreamRate** – **ストリーム** プロパティの画像を更新する頻度 (ミリ秒単位)。 この値の範囲は、100 (0.1 秒) から 3,600,000 (1 時間) です。

## <a name="additional-properties"></a>追加のプロパティ

[AccessibleLabel](properties-accessibility.md) – スクリーン リーダー用のラベル。 画像撮影の目的を説明する必要があります。

[BorderColor](properties-color-border.md) – コントロールの境界線の色。

[BorderStyle](properties-color-border.md) – コントロールの境界線が**実線**、**破線**、**点線**、または**なし**かどうか。

[BorderThickness](properties-color-border.md) – コントロールの境界線の太さ。

**明るさ** – ユーザーが画像で認識する可能性のある光量。

**コントラスト** – ユーザーが画像内の似た色をどれだけ容易に区別できるか。

[DisplayMode](properties-core.md) – コントロールがユーザー入力を許可するか (**編集**)、データのみを表示するか (**表示**)、または無効にするか (**無効化**)。

[FocusedBorderColor](properties-color-border.md) – コントロールがフォーカスされているときのコントロールの境界線の色。

[FocusedBorderThickness](properties-color-border.md) – コントロールがフォーカスされているときのコントロールの境界線の太さ。

[高さ](properties-size-location.md) – コントロールの上端と下端間の距離。

[OnSelect](properties-core.md) – ユーザーがコントロールをタップまたはクリックする場合のアプリの反応方法。

[TabIndex](properties-accessibility.md) – 他のコントロールと比較したキーボード ナビゲーションの順序。

[Tooltip](properties-core.md) – ユーザーがコントロールにカーソルを置くときに表示される説明テキスト。

[表示](properties-core.md) – コントロールが表示されるか非表示になるか。

[幅](properties-size-location.md) – コントロールの左端と右端間の距離。

[X](properties-size-location.md) – コントロールの左端とその親コンテナまたはスクリーンの左端との間の距離。

[Y](properties-size-location.md) – コントロールの上端と親コンテナまたはスクリーンの上端との間の距離。

## <a name="examples"></a>例

これらの例では、カメラ付きのデバイスが必要です。 アプリをテストするには、ブラウザーからアクセスできる Web カメラを使用します。 またはアプリを保存して iOS またはカメラ付き Android デバイスに読み込みます。

### <a name="simple-display-of-a-captured-picture"></a>キャプチャした画像の簡単な表示

1. **カメラ** コントロールを [追加](../add-configure-controls.md) します。

1. 要求された場合は、アプリがデバイスのカメラを使用することを許可します。

1. [**画像**](../controls/control-image.md) コントロールを追加します。

1. **画像**コントロールの**画像**プロパティを次の数式に設定します:

    ```powerapps-dot
    Camera1.Photo
    ```

    > [!NOTE]
    > 必要に応じて、カメラ コントロール名を *Camera1* に置き換えます。

1. F5 キーを押してアプリをプレビューします。

1. カメラ コントロールを選択またはタップして画像を撮影します。 画像コントロールに結果が表示されます。

### <a name="add-pictures-to-an-image-gallery-control"></a>画像ギャラリー コントロールへの画像の追加

1. **カメラ** コントロールを追加して、**MyCamera** という名前を付け、その [OnSelect](properties-core.md) プロパティを次の数式に設定します:

    ```powerapps-dot
    Collect( MyPix, MyCamera.Photo )
    ```

    詳細情報:

    - [コントロールの追加、名前付け、構成する方法](../add-configure-controls.md)
    - については、[収集](../functions/function-clear-collect-clearcollect.md) 関数または [その他の関数](../formula-reference.md) をお読みください。

1. F5 キーを押した後、**MyCamera** を選択またはタップして画像を撮影します。

1. [垂直ギャラリー](control-gallery.md) コントロールを追加します。 その後、[画像](control-image.md) コントロール、テンプレート、および**画像ギャラリー** コントロール自体のサイズを画面内に収まるようにサイズ変更します。

1. **画像ギャラリー** コントロールの [項目](properties-core.md) プロパティを次の数式に設定します:
 
    ```powerapps-dot
    MyPix
    ```

1. ギャラリーで、**画像**コントロールの [画像](properties-visual.md) プロパティを次の数式に設定します:

    ```powerapps-dot   
    ThisItem.Url
    ```

    撮影した画像が**画像ギャラリー** コントロールに表示されます。

1. 必要な枚数の画像を撮影してから、Esc キーを押して既定のワークスペースに戻ります。

1. (オプション) **画像ギャラリー** コントロールで**画像**コントロールの **OnSelect** プロパティを次の数式に設定します:

    ```powerapps-dot
    Remove( MyPix, ThisItem )
    ```

1. F5 キーを押してから、画像を選択して削除します。

[SaveData](../functions/function-savedata-loaddata.md) 関数を使用して画像をローカルに保存するか、[パッチ](../functions/function-patch.md) 関数を使用してデータ ソースを更新します。

### <a name="change-the-active-camera-from-a-drop-down"></a>有効なカメラをドロップ ダウンから変更する

1. **カメラ** コントロールを [追加](../add-configure-controls.md) します。

1. 要求された場合は、アプリがデバイスのカメラを使用することを許可します。
    
1. [ドロップ ダウン](control-drop-down.md) コントロールを [追加](../add-configure-controls.md) します。

1. ドロップ ダウンの**項目**プロパティを次のように設定します:

    ```powerapps-dot
    Camera1.AvailableDevices
    ```

    > [!NOTE]
      > 必要に応じて、カメラ コントロール名を *Camera1* に置き換えます。
    
1. カメラの**カメラ** プロパティを次のように設定します: 

    ```powerapps-dot
    Dropdown1.Selected.Id
    ```

    > [!NOTE]
      > 必要に応じて、ドロップダウン コントロール名を *Camera1* に置き換えます。

1. F5 キーを押してから、ドロップダウンから項目を選択してカメラを変更します。

## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン

カメラ コントロールは、カメラ フィードを示し、画像を撮影するボタンとしても機能します。 そのため、ボタンと同様のアクセシビリティの考慮事項があります。

### <a name="video-alternatives"></a>ビデオの代替手段

視覚障碍があるユーザー向けに、代替の入力形式を追加することを検討してください。 たとえば、[画像の追加](control-add-picture.md) を使用して、ユーザーはデバイスから画像をアップロードできます。

### <a name="color-contrast"></a>色のコントラスト

[FocusedBorderColor](properties-color-border.md) と外側の色との間に適切な色コントラストが必要です。

### <a name="screen-reader-support"></a>スクリーン リーダー サポート

[AccessibleLabel](properties-accessibility.md) が存在する必要があります。

### <a name="keyboard-support"></a>キーボードのサポート

- [TabIndex](properties-accessibility.md) を 0 以上にして、キーボード ユーザーがそこに移動できるようにする必要があります。

- フォーカス インジケーターは明確に表示する必要があります。 [FocusedBorderColor](properties-color-border.md) および [FocusedBorderThickness](properties-color-border.md) を使用して、フォーカス インジケーターの可視性を更新します。
