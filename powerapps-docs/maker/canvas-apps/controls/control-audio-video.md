---
title: 'オーディオとビデオのコントロール: リファレンス | Microsoft Docs'
description: プロパティとサンプルを含む、オーディオとビデオのコントロールに関する情報
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
ms.openlocfilehash: c797f6e9da4a0149638606613280100dcc26ad8a
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3306246"
---
# <a name="audio-and-video-controls-in-power-apps"></a>Power Apps でのオーディオとビデオのコントロール
YouTube でオーディオ ファイル、ビデオ ファイル、またはビデオを再生するコントロール。

## <a name="description"></a>内容
**オーディオ** コントロールでは、ファイルからのサウンド クリップ、**[マイク](control-microphone.md)** コントロールからの録音、またはビデオ ファイルのオーディオ トラックを再生します。

**ビデオ** コントロールでは、ファイルまたは YouTube や Azure Media Services からのビデオ クリップを再生します。  指定した場合、クローズド キャプションをオプションで表示できます。

## <a name="key-properties"></a>主要なプロパティ
**ループ** – オーディオまたはビデオ クリップが、再生終了と同時に先頭から自動的に再生するかどうか。

**Media** – オーディオまたはビデオ コントロールが再生するクリップの ID です。

**ShowControls** – オーディオ プレイヤーまたはビデオ プレイヤーに再生ボタンと音量スライダーなどが表示されるかどうか、およびペン コントロールに描画、削除、クリアなどのアイコンが表示されるかどうか。

## <a name="additional-properties"></a>追加のプロパティ
**[AccessibleLabel](properties-accessibility.md)** – スクリーン リーダー用のラベル。 ビデオまたはオーディオ クリップのタイトルである必要があります。

**AutoPause** – ユーザーが別の画面に移動した場合、オーディオまたはビデオ クリップを自動的に一時停止するかどうかを指定します。

**AutoStart** – ユーザーがオーディオまたはビデオ コントロールを含む画面に移動したときに、自動的にクリップの再生を開始するかどうかを指定します。

**[BorderColor](properties-color-border.md)** – コントロールの境界線の色。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線が**実線**、**破線**、**点線**、または**なし**かどうか。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さ。

**ClosedCaptionsUrl** – ビデオ コントロールのみ。  WebVTT 形式のクローズド キャプション ファイルの URL。  ビデオの URL と キャプションの URL は、どちらも HTTPS である必要があります。 ビデオとキャプションの両方のファイルをホストするサーバーでは、CORS が有効になっている必要があります。

**[DisplayMode](properties-core.md)** – コントロールがユーザー入力を許可するか (**編集**)、データのみを表示するか (**表示**)、または無効にするか (**無効**) どうか。

**[塗りつぶし](properties-color-border.md)** – コントロールの背景色。

**[FocusedBorderColor](properties-color-border.md)** – コントロールがフォーカスされているときのコントロールの境界線の色。

**[FocusedBorderThickness](properties-color-border.md)** – コントロールがフォーカスされているときのコントロールの境界線の太さ。

**[高さ](properties-size-location.md)** – コントロールの上端と下端間の距離。

**[画像](properties-visual.md)** – 画像、オーディオ、マイクのコントロールに表示される画像の名前。

**[ImagePosition](properties-visual.md)** – 画面またはコントロールのサイズが画像と異なる場合の、画面またはコントロール内の画像の位置 (**画面いっぱい**、**自動調整**、**拡大**、**タイル表示**、または**中央に表示**)。

**OnEnd** – オーディオまたはビデオ クリップの再生が終了したときの、アプリの応答方法。

**OnPause** – オーディオまたはビデオ コントロールが再生しているクリップをユーザーが一時停止したときの、アプリの応答方法。

**OnStart** – ユーザーがマイク コントロールで録音を開始するときの、アプリの応答方法。

**一時停止** – メディア再生コントロールが現在一時停止している場合は *true*、それ以外の場合は *false*。

**[Reset](properties-core.md)** – コントロールを既定値に戻すかどうかを指定します。

**Start** – オーディオまたはビデオ クリップを再生するかどうかを指定します。

**StartTime** – クリップの再生が開始するとき、オーディオまたはビデオ クリップの開始後の時刻。

**時刻** – メディア コントロールの現在位置。

**[TabIndex](properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序。

**[ツールヒント](properties-core.md)** – ユーザーがコントロールにカーソルを置くときに表示される説明テキスト。

**[表示](properties-core.md)** – コントロールが表示されるか非表示になるか。

**[幅](properties-size-location.md)** – コントロールの左端と右端間の距離。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離。

## <a name="related-functions"></a>関連する関数
[**First**( *TableName* )](../functions/function-first-last.md)

## <a name="examples"></a>例
### <a name="play-an-audio-or-video-file"></a>オーディオまたはビデオ ファイルを再生する
1. **ファイル** メニューで、**メディア**をクリックまたはタップし、**ビデオ**または**オーディオ**をクリックまたはタップしてから、**参照**をクリックまたはタップします。
2. 使用するファイルを参照してクリックまたはタップしてから、**開く**をクリックまたはタップします。
3. Esc キーを押して既定のワークスペースに戻り、**オーディオ**または**ビデオ** コントロールを追加して、その**メディア** プロパティを追加したファイルに設定します。

    [コントロールの追加および構成](../add-configure-controls.md) についてはこちらをご覧ください。
4. F5 キーを押してから、追加したコントロールの再生ボタンをクリックまたはタップして、クリップを再生します。

    > [!TIP]
   > **ビデオ** コントロールの再生ボタンは、コントロールにカーソルを合わせると表示されます。
5. 既定のワークスペースに戻るには、Esc キーを押します。

### <a name="play-a-youtube-video"></a>YouTube ビデオを再生する
1. **ビデオ** コントロールを追加し、その**メディア** プロパティを二重引用符で囲まれた YouTube ビデオの URL に設定します。
2. F5 キーを押し、**ビデオ** コントロールの再生ボタンをクリックまたはタップして、クリップを再生します。
3. 既定のワークスペースに戻るには、Esc キーを押します。

### <a name="play-a-video-from-azure-media-services"></a>Azure Media Services からビデオを再生する
1. AMS でビデオが公開された後、マニフェスト URL をコピーします。 まだ開始していない場合は、サービスのストリーミング エンドポイントを開始します。
1. **ビデオ** コントロールを追加し、その**メディア** プロパティを、二重引用符で囲まれた AMS ビデオの URL に設定します。
2. F5 キーを押し、**ビデオ** コントロールの再生ボタンをクリックまたはタップして、クリップを再生します。
3. 既定のワークスペースに戻るには、Esc キーを押します。


## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
### <a name="audio-and-video-alternatives"></a>オーディオおよびビデオの代替手段
* ユーザーが自分のペースでマルチメディアを視聴できるように、**ShowControls** を true にする必要があります。 これにより、ユーザーはビデオ プレーヤーでクローズド キャプションや全画面モードを切り替えることもできます。
* クローズド キャプションがビデオに対して指定されている必要があります。
  *  YouTube ビデオの場合、YouTube から提供される作成ツールを使ってキャプションを追加します。
  *  その他のビデオの場合は、WebVTT 形式でキャプションを作成し、それをアップロードして、**ClosedCaptionsUrl** を URL の場所に設定します。 いくつかの制限があります。 ビデオとキャプションをホストしているサーバーは、CORS が有効であり、HTTPS プロトコルを使用してそれらを提供する必要があります。 Internet Explorer ではキャプションは機能しません。
* 次のいずれかの方法を使用して、オーディオまたはビデオのトランスクリプトを提供することを検討してください:
  1. **[ラベル](control-text-box.md)** にテキストを挿入し、マルチメディア プレーヤーの隣に配置します。 必要に応じて、テキストの表示を切り替える **[ボタン](control-button.md)** を作成します。
  2. 別の画面にテキストを挿入します。 画面に移動する **[ボタン](control-button.md)** を作成し、マルチメディア プレーヤーの隣にボタンを配置します。
  3. 説明が短い場合は、**[AccessibleLabel](properties-accessibility.md)** に配置できます。

### <a name="color-contrast"></a>色のコントラスト
次の間には適切な色のコントラストが必要です:
* **[FocusedBorderColor](properties-color-border.md)** と外側の色
* **[画像](properties-visual.md)** とマルチメディア プレーヤー コントロール (該当する場合)
* **[塗りつぶし](properties-color-border.md)** とマルチメディア プレーヤー コントロール (塗りつぶしが表示される場合)

ビデオ コンテンツに色のコントラストの問題がある場合は、クローズド キャプションまたはトランスクリプトを提供します。

### <a name="screen-reader-support"></a>スクリーン リーダー サポート
* **[AccessibleLabel](properties-accessibility.md)** が存在する必要があります。

### <a name="keyboard-support"></a>キーボードのサポート
* **[TabIndex](properties-accessibility.md)** を 0 以上にして、キーボード ユーザーがそこに移動できるようにする必要があります。
* フォーカス インジケーターは明確に表示する必要があります。 これを実現するには **[FocusedBorderColor](properties-color-border.md)** および **[FocusedBorderThickness](properties-color-border.md)** を使用します。
* **AutoStart** は、キーボード ユーザーが再生をすばやく停止するのが難しい場合があるので、false である必要があります。
