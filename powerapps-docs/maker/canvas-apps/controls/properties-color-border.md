---
title: 色と境界線のプロパティ | Microsoft Docs
description: BorderColor、HoverBorderColor、および PressedBorderColor などのプロパティに関する参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/25/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 69b15887894bba576364ced8bab9f47eceeb8f96
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3305878"
---
# <a name="color-and-border-properties-in-power-apps"></a>Power Apps の色と境界線のプロパティ

## <a name="overview"></a>概要

ユーザーの操作方法に基づいて、コントロールのスタイルを構成します。

色は多くの方法で指定できます。

- [**Color**](../functions/function-colors.md) 列挙: 次の例のように、カスケード スタイル シートから色の名前を指定します。

  - **Color.Red**
  - **Color.Indigo**

- [**ColorValue**](../functions/function-colors.md) 関数: 次の例のように、カスケード スタイル シートおよび 16 進数コード (**#**) から色の名前などのテキスト文字列を指定します。

  - **ColorValue( "AliceBlue" )**
  - **ColorValue( "#ff00ff" )**

- [**ColorFade**](../functions/function-colors.md) 関数: 次の例のように、完全な黒 (-100%) から完全な白 (100%) へ色をフェードさせる方法を指定します。

  - **ColorFade( Color.Red, 50% )**

- [**RGBA**](../functions/function-colors.md) 関数: 次の例のように、赤、緑、および青のコンポーネントを 0 から 255 の間で指定し、アルファ チャネルを 0% (完全な透明) から 100% (完全な不透明) の間で指定します。

  - **RGBA( 255, 0, 255, 25% )**

色のプロパティは、その他の色のプロパティを参照することもできます。 たとえば、**Label.PressedColo** は、式 **Label1.Color** に設定でき、あるプロパティから別のプロパティへの変更を自動的にカスケードします。

## <a name="normal"></a>正常

通常、コントロールを操作していないときに、これらのプロパティは有効です。

**BorderColor** – コントロールの境界線の色。

- **[画像の追加](control-add-picture.md)**、**[オーディオ](control-audio-video.md)**、**[ボタン](control-button.md)**、**[カメラ](control-camera.md)**、**[カード](control-card.md)**、**[チェック ボックス](control-check-box.md)**、**[縦棒グラフ](control-column-line-chart.md)**、**[日付の選択](control-date-picker.md)**、**[表示フォーム](control-form-detail.md)**、**[ドロップ ダウン](control-drop-down.md)**、**[編集フォーム](control-form-detail.md)**、**[エクスポート](control-export-import.md)**、**[ギャラリー](control-gallery.md)**、**[HTML テキスト](control-html-text.md)**、**[画像](control-image.md)**、**[インポート](control-export-import.md)**、**[ラベル](control-text-box.md)**、**[折れ線グラフ](control-column-line-chart.md)**、**[リスト ボックス](control-list-box.md)**、**[マイク](control-microphone.md)**、**[PDF ビューアー](control-pdf-viewer.md)**、**[ペン入力](control-pen-input.md)**、**[円グラフ](control-pie-chart.md)**、**[ラジオ](control-radio.md)**、**[評価](control-rating.md)**、**[スライダー](control-slider.md)**、**[テキスト入力](control-text-input.md)**、**[タイマー](control-timer.md)**、**[トグル](control-toggle.md)**、**[ビデオ](control-audio-video.md)** の各コントロールに適用されます。

**BorderStyle** – コントロールの境界線が**実線**、**破線**、**点線**、または**なし**かどうか。

- **[画像の追加](control-add-picture.md)**、**[オーディオ](control-audio-video.md)**、**[ボタン](control-button.md)**、**[カメラ](control-camera.md)**、**[カード](control-card.md)**、**[チェック ボックス](control-check-box.md)**、**[縦棒グラフ](control-column-line-chart.md)**、**[日付の選択](control-date-picker.md)**、**[表示フォーム](control-form-detail.md)**、**[ドロップ ダウン](control-drop-down.md)**、**[編集フォーム](control-form-detail.md)**、**[エクスポート](control-export-import.md)**、**[ギャラリー](control-gallery.md)**、**[HTML テキスト](control-html-text.md)**、**[画像](control-image.md)**、**[インポート](control-export-import.md)**、**[ラベル](control-text-box.md)**、**[折れ線グラフ](control-column-line-chart.md)**、**[リスト ボックス](control-list-box.md)**、**[マイク](control-microphone.md)**、**[PDF ビューアー](control-pdf-viewer.md)**、**[ペン入力](control-pen-input.md)**、**[円グラフ](control-pie-chart.md)**、**[ラジオ](control-radio.md)**、**[評価](control-rating.md)**、**[スライダー](control-slider.md)**、**[テキスト入力](control-text-input.md)**、**[タイマー](control-timer.md)**、**[トグル](control-toggle.md)**、**[ビデオ](control-audio-video.md)** の各コントロールに適用されます。

**BorderThickness** – コントロールの境界線の太さ。

- **[画像の追加](control-add-picture.md)**、**[オーディオ](control-audio-video.md)**、**[ボタン](control-button.md)**、**[カメラ](control-camera.md)**、**[カード](control-card.md)**、**[チェック ボックス](control-check-box.md)**、**[縦棒グラフ](control-column-line-chart.md)**、**[日付の選択](control-date-picker.md)**、**[表示フォーム](control-form-detail.md)**、**[ドロップ ダウン](control-drop-down.md)**、**[編集フォーム](control-form-detail.md)**、**[エクスポート](control-export-import.md)**、**[ギャラリー](control-gallery.md)**、**[HTML テキスト](control-html-text.md)**、**[画像](control-image.md)**、**[インポート](control-export-import.md)**、**[ラベル](control-text-box.md)**、**[折れ線グラフ](control-column-line-chart.md)**、**[リスト ボックス](control-list-box.md)**、**[マイク](control-microphone.md)**、**[PDF ビューアー](control-pdf-viewer.md)**、**[ペン入力](control-pen-input.md)**、**[円グラフ](control-pie-chart.md)**、**[ラジオ](control-radio.md)**、**[評価](control-rating.md)**、**[スライダー](control-slider.md)**、**[テキスト入力](control-text-input.md)**、**[タイマー](control-timer.md)**、**[トグル](control-toggle.md)**、**[ビデオ](control-audio-video.md)** の各コントロールに適用されます。

**Color** – コントロールのテキストの色。

- **[画像の追加](control-add-picture.md)**、**[ボタン](control-button.md)**、**[チェック ボックス](control-check-box.md)**、**[縦棒グラフ](control-column-line-chart.md)**、**[日付の選択](control-date-picker.md)**、**[ドロップ ダウン](control-drop-down.md)**、**[エクスポート](control-export-import.md)**、**[HTML テキスト](control-html-text.md)**、**[インポート](control-export-import.md)**、**[ラベル](control-text-box.md)**、**[折れ線グラフ](control-column-line-chart.md)**、**[リスト ボックス](control-list-box.md)**、**[マイク](control-microphone.md)**、**[ペン入力](control-pen-input.md)**、**[円グラフ](control-pie-chart.md)**、**[ラジオ](control-radio.md)**、**[テキスト入力](control-text-input.md)**、**[タイマー](control-timer.md)** の各コントロールに適用されます。

**Fill** – コントロールの背景色。

- **[画像の追加](control-add-picture.md)**、**[オーディオ](control-audio-video.md)**、**[ボタン](control-button.md)**、**[カード](control-card.md)**、**[チェック ボックス](control-check-box.md)**、**[日付の選択](control-date-picker.md)**、**[表示フォーム](control-form-detail.md)**、**[ドロップ ダウン](control-drop-down.md)**、**[編集フォーム](control-form-detail.md)**、**[エクスポート](control-export-import.md)**、**[ギャラリー](control-gallery.md)**、**[HTML テキスト](control-html-text.md)**、**[アイコン](control-shapes-icons.md)**、**[画像](control-image.md)**、**[インポート](control-export-import.md)**、**[ラベル](control-text-box.md)**、**[リスト ボックス](control-list-box.md)**、**[マイク](control-microphone.md)**、**[PDF ビューアー](control-pdf-viewer.md)**、**[ペン入力](control-pen-input.md)**、**[ラジオ](control-radio.md)**、**[評価](control-rating.md)**、**[画像](control-screen.md)**、**[シェイプ](control-shapes-icons.md)**、**[テキスト入力](control-text-input.md)**、**[タイマー](control-timer.md)**、**[トグル](control-toggle.md)**、**[ビデオ](control-audio-video.md)** の各コントロールに適用されます。

## <a name="focused"></a>フォーカスがある

次のプロパティは、コントロールにフォーカスがある場合に効力があります。

**FocusedBorderColor** – コントロールにフォーカスがあるときのコントロールの境界線の色です。

**FocusedBorderThickness** – フォーカスがあるときのコントロールの境界線の太さです。

- これらのプロパティは、**[画像の追加](control-add-picture.md)**、**[添付ファイル](control-attachments.md)**、**[オーディオ](control-audio-video.md)**、**[ボタン](control-button.md)**、**[カメラ](control-camera.md)**、**[チェック ボックス](control-check-box.md)**、**[コンボ ボックス](control-combo-box.md)**、**[日付の選択](control-date-picker.md)**、**[ドロップ ダウン](control-drop-down.md)**、**[エクスポート](control-export-import.md)**、**[ギャラリー](control-gallery.md)**、**[アイコン](control-shapes-icons.md)**、**[イメージ](control-image.md)**、**[インポート](control-export-import.md)**、**[ラベル](control-text-box.md)**、**[リスト ボックス](control-list-box.md)**、**[マイク](control-microphone.md)**、**[ラジオ](control-radio.md)**、**[評価](control-rating.md)**、**[シェイプ](control-shapes-icons.md)**、**[スライダー](control-slider.md)**、**[テキスト入力](control-text-input.md)**、**[タイマー](control-timer.md)**、**[トグル](control-toggle.md)**、および **[ビデオ](control-audio-video.md)** の各コントロールに適用されます。

## <a name="disabled"></a>無効

次のプロパティは、コントロールが無効なときに効力があります。  **[Disabled](properties-core.md)** プロパティが *true* に設定されている場合、コントロールを無効にできます。

**DisabledBorderColor** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロールの境界線の色。

- **[画像の追加](control-add-picture.md)**、**[ボタン](control-button.md)**、**[チェック ボックス](control-check-box.md)**、**[縦棒グラフ](control-column-line-chart.md)**、**[日付の選択](control-date-picker.md)**、**[ドロップ ダウン](control-drop-down.md)**、**[エクスポート](control-export-import.md)**、**[HTML テキスト](control-html-text.md)**、**[画像](control-image.md)**、**[インポート](control-export-import.md)**、**[ラベル](control-text-box.md)**、**[折れ線グラフ](control-column-line-chart.md)**、**[リスト ボックス](control-list-box.md)**、**[マイク](control-microphone.md)**、**[PDF ビューアー](control-pdf-viewer.md)**、**[円グラフ](control-pie-chart.md)**、**[ラジオ](control-radio.md)**、**[スライダー](control-slider.md)**、**[テキスト入力](control-text-input.md)**、**[タイマー](control-timer.md)**、**[トグル](control-toggle.md)** の各コントールに適用されます。

**DisabledColor** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロール内のテキストの色。

- **[画像の追加](control-add-picture.md)**、**[ボタン](control-button.md)**、**[チェック ボックス](control-check-box.md)**、**[日付の選択](control-date-picker.md)**、**[ドロップ ダウン](control-drop-down.md)**、**[エクスポート](control-export-import.md)**、**[インポート](control-export-import.md)**、**[ラベル](control-text-box.md)**、**[リスト ボックス](control-list-box.md)**、**[マイク](control-microphone.md)**、**[ラジオ](control-radio.md)**、**[テキスト入力](control-text-input.md)**、**[タイマー](control-timer.md)** の各コントロールに適用されます。

**DisabledFill** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロールの背景色。

- **[画像の追加](control-add-picture.md)**、**[ボタン](control-button.md)**、**[チェック ボックス](control-check-box.md)**、**[日付の選択](control-date-picker.md)**、**[ドロップ ダウン](control-drop-down.md)**、**[エクスポート](control-export-import.md)**、**[HTML テキスト](control-html-text.md)**、**[画像](control-image.md)**、**[インポート](control-export-import.md)**、**[ラベル](control-text-box.md)**、**[リスト ボックス](control-list-box.md)**、**[マイク](control-microphone.md)**、**[ラジオ](control-radio.md)**、**[テキスト入力](control-text-input.md)**、**[タイマー](control-timer.md)** の各コントロールに適用されます。

## <a name="hover"></a>ホバー

次のプロパティは、ユーザーがコントロール上にマウス ポインターを重ねたときに効力があります。

**HoverBorderColor** – ユーザーがコントロール上にマウス ポインターを重ねているときのコントロールの境界線の色。

- **[画像の追加](control-add-picture.md)**、**[ボタン](control-button.md)**、**[チェック ボックス](control-check-box.md)**、**[縦棒グラフ](control-column-line-chart.md)**、**[ドロップ ダウン](control-drop-down.md)**、**[エクスポート](control-export-import.md)**、**[HTML テキスト](control-html-text.md)**、**[画像](control-image.md)**、**[インポート](control-export-import.md)**、**[ラベル](control-text-box.md)**、**[折れ線グラフ](control-column-line-chart.md)**、**[リスト ボックス](control-list-box.md)**、**[マイク](control-microphone.md)**、**[PDF ビューアー](control-pdf-viewer.md)**、**[円グラフ](control-pie-chart.md)**、**[スライダー](control-slider.md)**、**[テキスト入力](control-text-input.md)**、**[タイマー](control-timer.md)**、**[トグル](control-toggle.md)** の各コントロールに適用されます。

**HoverColor** – ユーザーがコントロールにマウス ポインターを重ねているときのコントロール内のテキストの色。

- **[画像の追加](control-add-picture.md)**、**[ボタン](control-button.md)**、**[チェック ボックス](control-check-box.md)**、**[ドロップ ダウン](control-drop-down.md)**、**[エクスポート](control-export-import.md)**、**[インポート](control-export-import.md)**、**[ラベル](control-text-box.md)**、**[リスト ボックス](control-list-box.md)**、**[マイク](control-microphone.md)**、**[ラジオ](control-radio.md)**、**[テキスト入力](control-text-input.md)**、**[タイマー](control-timer.md)** の各コントロールに適用されます。

**HoverFill** – ユーザーがコントロールにマウス ポインターを重ねているときのコントロールの背景色。

- **[画像の追加](control-add-picture.md)**、**[ボタン](control-button.md)**、**[チェック ボックス](control-check-box.md)**、**[ドロップ ダウン](control-drop-down.md)**、**[エクスポート](control-export-import.md)**、**[アイコン](control-shapes-icons.md)**、**[画像](control-image.md)**、**[インポート](control-export-import.md)**、**[ラベル](control-text-box.md)**、**[リスト ボックス](control-list-box.md)**、**[マイク](control-microphone.md)**、**[ラジオ](control-radio.md)**、**[シェイプ](control-shapes-icons.md)**、**[テキスト入力](control-text-input.md)**、**[タイマー](control-timer.md)** の各コントロールに適用されます。

## <a name="pressed"></a>押下

次のプロパティは、ボタンまたはイメージ コントロールが押されているときに効力があります。

**PressedBorderColor** – ユーザーがコントロールをタップまたはクリックしたときのコントロールの境界線の色。

- **[画像の追加](control-add-picture.md)**、**[ボタン](control-button.md)**、**[チェック ボックス](control-check-box.md)**、**[縦棒グラフ](control-column-line-chart.md)**、**[ドロップ ダウン](control-drop-down.md)**、**[エクスポート](control-export-import.md)**、**[アイコン](control-shapes-icons.md)**、**[画像](control-image.md)**、**[インポート](control-export-import.md)**、**[ラベル](control-text-box.md)**、**[折れ線グラフ](control-column-line-chart.md)**、**[リスト ボックス](control-list-box.md)**、**[マイク](control-microphone.md)**、**[PDF ビューアー](control-pdf-viewer.md)**、**[円グラフ](control-pie-chart.md)**、**[シェイプ](control-shapes-icons.md)**、**[スライダー](control-slider.md)**、**[テキスト入力](control-text-input.md)**、**[タイマー](control-timer.md)**、**[トグル](control-toggle.md)** の各コントロールに適用されます。

**PressedColor** – ユーザーがコントロールをタップまたはクリックしたときのコントロール内のテキストの色。

- **[画像の追加](control-add-picture.md)**、**[ボタン](control-button.md)**、**[チェック ボックス](control-check-box.md)**、**[ドロップ ダウン](control-drop-down.md)**、**[エクスポート](control-export-import.md)**、**[インポート](control-export-import.md)**、**[ラベル](control-text-box.md)**、**[リスト ボックス](control-list-box.md)**、**[マイク](control-microphone.md)**、**[ラジオ](control-radio.md)**、**[テキスト入力](control-text-input.md)**、**[タイマー](control-timer.md)** の各コントロールに適用されます。

**PressedFill** – ユーザーがコントロールをタップまたはクリックしたときのコントロールの背景色。

- **[画像の追加](control-add-picture.md)**、**[ボタン](control-button.md)**、**[チェック ボックス](control-check-box.md)**、**[ドロップ ダウン](control-drop-down.md)**、**[エクスポート](control-export-import.md)**、**[画像](control-image.md)**、**[インポート](control-export-import.md)**、**[ラベル](control-text-box.md)**、**[リスト ボックス](control-list-box.md)**、**[マイク](control-microphone.md)**、**[ラジオ](control-radio.md)**、**[テキスト入力](control-text-input.md)**、**[タイマー](control-timer.md)** の各コントロールに適用されます。

## <a name="selection"></a>選択

次のプロパティは、ユーザーがコントロール内の項目を選択したときに効力があります。

**SelectionColor** – リスト内で選択された項目のテキストの色、またはペン コントロールの選択ツールの色。

- **[ドロップ ダウン](control-drop-down.md)**、**[リスト ボックス](control-list-box.md)**、および **[ペン入力](control-pen-input.md)** の各コントロールに適用されます。

**SelectionFill** – 選択された項目、またはリストの項目、またはペン コントロールの選択領域の背景色。

- **[ドロップ ダウン](control-drop-down.md)** コントロールと **[リスト ボックス](control-list-box.md)** コントロールに適用されます。