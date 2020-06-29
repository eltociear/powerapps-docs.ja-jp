---
title: 'マイク コントロール: リファレンス | Microsoft Docs'
description: プロパティとサンプルを含む、マイク コントロールに関する情報
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
ms.openlocfilehash: 353485baf6726314f6009c57838b3aa68d145fa0
ms.sourcegitcommit: cf492063eca27fdf73459ff2f9134f2ca04ee766
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/17/2020
ms.locfileid: "3308845"
---
# <a name="microphone-control-in-power-apps"></a>Power Apps でのマイク コントロール

アプリのユーザーが自分のデバイスからのサウンドを録音できるようにするコントロール。

## <a name="description"></a>内容

**マイク** コントロールを使用して、デバイスのマイクでオーディオをキャプチャします。  デバイスにはマイクが必要であり、ユーザーはアプリがマイクを使用することを許可する必要があります。  マイク コントロールは、Web ブラウザーでの実行時にサポートされます。  

最近録音されたオーディオ クリップは、**オーディオ** プロパティを通して利用できます。 このプロパティを使用すると、録音されたオーディオは次のようになります:

- **オーディオ コントロールで再生されます。**  [オーディオ](control-audio-video.md) コントロールを使用して録音を聴きます。 詳細については、 [例](#examples) を参照してください。
- **一時的に変数またはコレクションに保存されます。**  [設定](../functions/function-set.md) または [収集](../functions/function-clear-collect-clearcollect.md) 関数を使用して、変数またはコレクションにオーディオ クリップを保存します。  デバイスのメモリが限られているコレクション内の複数のオーディオ クリップに対して、同時に注意が必要です。  [SaveData](../functions/function-savedata-loaddata.md) および [LoadData](../functions/function-savedata-loaddata.md) 関数を使用して、オーディオ クリップをデバイスのローカル ストレージと [オフラインのシナリオ](../offline-apps.md) に移動します。
- **データベースに格納されます。**  [パッチ](../functions/function-patch.md) 関数を使用して、オーディオ クリップをデータベースに保存します。
- **base64 でエンコードされたテキスト文字列として送信されます。**  [JSON](../functions/function-json.md) 関数を使用して、オーディオ クリップを base64 エンコードします。

録音されたオーディオの形式:

- *Android* 用 *3gp* 形式。
- *iOS* 用 *AAC* 形式。
- *Web ブラウザー*用 *OGG* 形式。

キャプチャされたメディアは、テキスト文字列 URI によって参照されます。 詳細については、[データ型ドキュメント](../functions/data-types.md#uris-for-images-and-other-media) をお読みください。

## <a name="key-properties"></a>主要なプロパティ

**オーディオ** – ユーザーがデバイスのマイクで録音するときにキャプチャされるオーディオ クリップ。 

**Mic** – 複数のマイクを備えたデバイスでの、マイクの数値 ID。

**OnStop** – ユーザーがマイク コントロールで録音を終了したときの、アプリの応答方法。

## <a name="additional-properties"></a>追加のプロパティ

[AccessibleLabel](properties-accessibility.md) – スクリーン リーダー用のラベル。 マイクの目的を説明する必要があります。

[BorderColor](properties-color-border.md) – コントロールの境界線の色。

[BorderStyle](properties-color-border.md) – コントロールの境界線が**実線**、**破線**、**点線**、または**なし**かどうか。

[BorderThickness](properties-color-border.md) – コントロールの境界線の太さ。

[色](properties-color-border.md) – コントロールのテキストの色。

[DisplayMode](properties-core.md) – コントロールがユーザー入力を許可するか (**編集**)、データのみを表示するか (**表示**)、または無効にするか (**無効化**)。

[DisabledBorderColor](properties-color-border.md) – コントロールの [DisplayMode](properties-core.md) プロパティが**無効**に設定されている場合のコントロールの境界線の色。

[DisabledColor](properties-color-border.md) – [DisplayMode](properties-core.md) プロパティが **無効**に設定されている場合のコントロール内のテキストの色。

[DisabledFill](properties-color-border.md) – [DisplayMode](properties-core.md) プロパティが**無効**に設定されている場合のコントロールの背景色。

[塗りつぶし](properties-color-border.md) – コントロールの背景色。

[FocusedBorderColor](properties-color-border.md) – コントロールがフォーカスされているときのコントロールの境界線の色。

[FocusedBorderThickness](properties-color-border.md) – コントロールがフォーカスされているときのコントロールの境界線の太さ。

[高さ](properties-size-location.md) – コントロールの上端と下端間の距離。

[HoverBorderColor](properties-color-border.md) – ユーザーがコントロール上にマウス ポインターを重ねているときのコントロールの境界線の色。

[HoverColor](properties-color-border.md) – ユーザーがコントロールにマウス ポインターを重ねているときのコントロール内のテキストの色。

[HoverFill](properties-color-border.md) – ユーザーがコントロールにマウス ポインターを重ねているときのコントロールの背景色。

[画像](properties-visual.md) – 画像、オーディオ、マイク コントロールに表示される画像の名前。

[ImagePosition](properties-visual.md) – 画面またはコントロールのサイズが画像と異なる場合の、画面またはコントロール内の画像の位置 (**画面いっぱい**、**自動調整**、**拡大**、**タイル表示**、または**中央に表示**)。

[OnSelect](properties-core.md) – ユーザーがコントロールを選択する場合のアプリの反応方法。

**OnStart** – ユーザーがマイク コントロールで録音を開始するときの、アプリの応答方法。

[PressedBorderColor](properties-color-border.md) – ユーザーがコントロールを選択するときのコントロールの境界線の色。

[PressedColor](properties-color-border.md) – ユーザーがコントロールを選択するときのコントロール内のテキストの色。

[PressedFill](properties-color-border.md) – ユーザーがコントロールを選択するときのコントロールの背景色。

[リセット](properties-core.md) – コントロールを既定値に戻すかどうか。

[TabIndex](properties-accessibility.md) – 他のコントロールと比較したキーボード ナビゲーションの順序。

[Tooltip](properties-core.md) – ユーザーがコントロールにカーソルを置くときに表示される説明テキスト。

[表示](properties-core.md) – コントロールが表示されるか非表示になるか。

[幅](properties-size-location.md) – コントロールの左端と右端間の距離。

[X](properties-size-location.md) – コントロールの左端とその親コンテナまたはスクリーンの左端との間の距離。

[Y](properties-size-location.md) – コントロールの上端と親コンテナまたはスクリーンの上端との間の距離。

## <a name="examples"></a>例

### <a name="simple-direct-playback"></a>シンプルな直接再生

この例では、**マイク** コントロールを**オーディオ** コントロールに直接接続して、直ちに再生します:

1. **マイク** コントロールをアプリに [追加](../add-configure-controls.md) します。
1. 要求された場合は、アプリがデバイスのマイクを使用することを許可します。
1. **オーディオ** コントロールをアプリに追加します。
1. **オーディオ** コントロールの**メディア** プロパティを式に設定します:

    ```powerapps-dot
    Microphone1.Audio
    ```

    > [!NOTE]
    > 必要に応じて、マイク コントロール名を *Microphone1* に置き換えます。

1. アプリをプレビューします。
1. **マイク** コントロールを選択して録音を開始します。
1. 音声を録音するため読み上げます。
1. **マイク** コントロールを再度選択して録音を終了します。
1. **オーディオ** コントロールを選択して録音を聞きます。  

### <a name="add-sounds-to-a-gallery-control"></a>ギャラリー コントロールにサウンドを追加します

この例では、再生用に個別に選択できるコレクションに格納されたオーディオ クリップのギャラリーを作成します。

1. **マイク** コントロールを [追加](../add-configure-controls.md) します。

1. [Collect](../functions/function-clear-collect-clearcollect.md) 関数を使用して **OnStop** プロパティをこの数式に設定します:

    ```powerapps-dot
    Collect( MySounds, MyMic.Audio )
    ```

1. **ギャラリー** コントロールを追加し、**MyMic** の下に移動します。

1. ギャラリーの [項目](properties-core.md) プロパティを次の数式に設定します:

    ```powerapps-dot
    MySounds
    ```

1. **カスタム ギャラリー** コントロールのテンプレートで、[オーディオ](control-audio-video.md) コントロールを追加します。

1. オーディオ コントロールの**メディア** プロパティをこの数式に設定します:

    ```powerapps-dot
    ThisItem.Url
    ```

1. F5 キーを押してアプリをプレビューします。

1. **MyMic** を選択して録音を開始してから、もう一度選択して録音を終了します。

1. **ギャラリー** コントロールで、**オーディオ** コントロールの再生ボタンを選択して録音を再生します。

1. 必要な数のサウンドを録音してから、Esc キーを押して既定のワークスペースに戻ります。

1. (オプション) **ギャラリー** コントロールのテンプレートで、[ボタン](control-button.md) コントロールを追加します。

1. [OnSelect](properties-core.md) プロパティを次の数式に設定します:

    ```powerapps-dot
    Remove( MySounds, ThisItem )
    ```

1. F5 キーを押してから、**ボタン** コントロールに対応するものを選択して録音を削除します。

[SaveData](../functions/function-savedata-loaddata.md) 関数を使用して録音をローカルに保存するか、[パッチ](../functions/function-patch.md) 関数を使用してデータ ソースを更新します。

## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン

**マイク**は特殊なボタンなので、[ボタン](control-button.md) と同じガイドラインが適用されます。 また、以下の点を考慮してください:

### <a name="audio-alternatives"></a>音声の代替手段

言語障碍があるユーザーまたはマイクがないユーザー向けに、代替形式の入力を追加することを検討してください。 たとえば、[テキスト入力](control-text-input.md) によりユーザーがテキストを入力できるようにします。

### <a name="color-contrast"></a>色のコントラスト

- [標準の色のコントラスト要件](../accessible-apps-color.md) についてお読みください。
- [画像](properties-visual.md) およびボタン テキストとアイコン (該当する場合) 間の適切な色のコントラストを確認します。

### <a name="screen-reader-support"></a>スクリーン リーダー サポート

- [AccessibleLabel](properties-accessibility.md) が存在する必要があります。
