---
title: 'Microsoft Stream ビデオ コントロール: リファレンス | Microsoft Docs'
description: 各種プロパティとサンプルを含む Microsoft Stream ビデオ コントロールに関する情報
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 11/26/2019
ms.author: fikaradz
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 00c13a3b57cce0f7c8831b0932f7e17bbb32efe7
ms.sourcegitcommit: 212bd841595db0d6f41002f7ff9a1c8eb33a0724
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "3307511"
---
# <a name="microsoft-stream-video-control-in-power-apps"></a>Power Apps の Microsoft Stream ビデオ コントロール
Microsoft Stream の動画とチャネル用の動画プレーヤー。

## <a name="description"></a>内容
コントロールにより、アプリ ユーザーは動画を再生したり、Microsoft Stream のサービスからチャネルを通して閲覧することができます。

## <a name="limitations"></a>制限
現在、コントロールは Power Apps 用の Windows ネイティブ プレーヤーではサポートされていません。  Android および iOS Power Apps プレーヤーと同様に Web ブラウザーでも正常に動作します。

## <a name="key-properties"></a>主要なプロパティ
**StreamUrl** – コントロールに表示される Microsoft Stream の動画またはチャネルの URL。

**ShowControls** – 動画再生コントロールがエンド ユーザーに表示されるかどうか。

## <a name="additional-properties"></a>追加のプロパティ
**[AccessibleLabel](properties-accessibility.md)** – スクリーン リーダー用のラベル。 ビデオまたはオーディオ クリップのタイトルである必要があります。

**AutoStart** – ユーザーがオーディオまたはビデオ コントロールを含む画面に移動したときに、自動的にクリップの再生を開始するかどうかを指定します。

**[BorderColor](properties-color-border.md)** – コントロールの境界線の色。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線が**実線**、**破線**、**点線**、または**なし**かどうか。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さ。

**[DisplayMode](properties-core.md)** – コントロールがユーザー入力を許可するか (**編集**)、データのみを表示するか (**表示**)、または無効にするか (**無効**) どうか。

**[塗りつぶし](properties-color-border.md)** – コントロールの背景色。

**[FocusedBorderColor](properties-color-border.md)** – コントロールがフォーカスされているときのコントロールの境界線の色。

**[FocusedBorderThickness](properties-color-border.md)** – コントロールがフォーカスされているときのコントロールの境界線の太さ。

**[高さ](properties-size-location.md)** – コントロールの上端と下端間の距離。

**StartTime** – クリップの再生が開始するとき、オーディオまたはビデオ クリップの開始後の時刻。

**[TabIndex](properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序。

**[ツールヒント](properties-core.md)** – ユーザーがコントロールにカーソルを置くときに表示される説明テキスト。

**[表示](properties-core.md)** – コントロールが表示されるか非表示になるか。

**[幅](properties-size-location.md)** – コントロールの左端と右端間の距離。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離。

## <a name="example"></a>例

### <a name="play-an-audio-or-video-file-from-microsoft-stream"></a>Microsoft Stream からオーディオまたは動画ファイルを再生する

1. **ファイル** メニューで**挿入**を選択し、**メディア** ドロップダウン メニューを開きます。 
2. メディア コントロールの一覧から **Microsoft Stream** を選択します。

    ![Microsoft Stream](./media/control-stream-video/stream-icon.png "Microsoft Stream")

3. 左側の **Stream URL** プロパティ内に動画のリンクを貼り付けます。

    ![StreamUrl プロパティのカスタマイズ](./media/control-stream-video/stream-url.png "StreamUrl プロパティのカスタマイズ")

4. F5 キーを押して、追加したコントロールの再生ボタンを選択します。

    > [!NOTE]
   > **Microsoft Stream** で動画を再生するには認証が必要です。 アプリのユーザーに必要なアクセス許可があることを確認します。
5. Esc キーを押してプレビュー モードを終了します。

## <a name="browser-considerations"></a>ブラウザーの考慮事項

### <a name="ios"></a>iOS
Power Apps の iOS プレーヤーは、アプリに埋め込まれた動画の直接再生をサポートしません。  動画を視聴するには、Stream アイコンをクリックして、動画プレーヤーを全画面モードで起動します。

### <a name="safari"></a>Safari

Safari ブラウザーでアプリ内の Microsoft Stream 動画を表示するには、[サイト間の追跡を禁止](https://support.apple.com/guide/safari/sfri40732/mac) オプションをオフにする必要があります。

## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
### <a name="audio-and-video-alternatives"></a>オーディオおよびビデオの代替手段
* ユーザーが自分のペースでマルチメディアを視聴できるように、**ShowControls** を true にする必要があります。 これにより、ユーザーはビデオ プレーヤーでクローズド キャプションや全画面モードを切り替えることもできます。
* クローズド キャプションがビデオに対して指定されている必要があります。
 * 次のいずれかの方法を使用して、オーディオまたはビデオのトランスクリプトを提供することを検討してください:
  1. **[ラベル](control-text-box.md)** にテキストを挿入し、マルチメディア プレーヤーの隣に配置します。 必要に応じて、テキストの表示を切り替える **[ボタン](control-button.md)** を作成します。
  2. 別の画面にテキストを挿入します。 画面に移動する **[ボタン](control-button.md)** を作成し、マルチメディア プレーヤーの隣にボタンを配置します。
  3. 説明が短い場合は、**[AccessibleLabel](properties-accessibility.md)** に配置できます。

### <a name="color-contrast"></a>色のコントラスト
次の間には適切な色のコントラストが必要です:
* **[FocusedBorderColor](properties-color-border.md)** と外側の色
* **[塗りつぶし](properties-color-border.md)** とマルチメディア プレーヤー コントロール (塗りつぶしが表示される場合)

ビデオ コンテンツに色のコントラストの問題がある場合は、クローズド キャプションまたはトランスクリプトを提供します。

### <a name="screen-reader-support"></a>スクリーン リーダー サポート
* **[AccessibleLabel](properties-accessibility.md)** が存在する必要があります。

### <a name="keyboard-support"></a>キーボードのサポート
* **[TabIndex](properties-accessibility.md)** を 0 以上にして、キーボード ユーザーがそこに移動できるようにする必要があります。
* フォーカス インジケーターは明確に表示する必要があります。 これを実現するには **[FocusedBorderColor](properties-color-border.md)** および **[FocusedBorderThickness](properties-color-border.md)** を使用します。
* **AutoStart** は、キーボード ユーザーが再生をすばやく停止するのが難しい場合があるので、false である必要があります。
