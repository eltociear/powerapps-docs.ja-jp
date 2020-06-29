---
title: 'PDF ビューアー コントロール: リファレンス | Microsoft Docs'
description: プロパティとサンプルを含む、PDF ビューアー コントロールに関する情報
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/10/2020
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a8136fc1ce04ed696aeb68af7139d1b538dd879e
ms.sourcegitcommit: af653cd30f5879fea97a594d458d355fe18f4834
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/11/2020
ms.locfileid: "3309213"
---
# <a name="pdf-viewer-control-experimental-in-power-apps"></a>Power Apps での PDF ビューアー コントロール (試験段階)
PDF ファイルの内容を表示する試験段階のコントロール。

## <a name="description"></a>内容
PDF ファイルのテキスト、グラフィック、他の内容を表示するには、この種類のコントロールを追加し、その**ドキュメント** プロパティを表示するファイルの二重引用符で囲んだ URL に設定します。

## <a name="limitations"></a>制限
1. Power Apps のセキュリティ アーキテクチャでは、HTTP ではなく HTTPS リンクのみをサポートする PDF ビューアーが必要です。  

2. **ドキュメント** プロパティは PDF ファイルに直接リンクする必要があります。 ドキュメントのサーバー リダイレクトまたは HTML ビューはサポートされていません。

3. ドキュメントをホストするサーバーは認証を必要としません。

4. 制限付きのクロス オリジン リソース共有 (CORS) 設定のあるサーバーにドキュメントが存在する場合、アプリで PDF ドキュメントを表示できない場合があります。 この問題を解決するには、PDF ドキュメントをホストするサーバーが powerapps.com からのクロス オリジン要求を許可する必要があります。

アプリ ユーザーは、外部ブラウザーで PDF ドキュメントを開くことにより、これらの制限を回避できます。コントロールがドキュメントを開けない場合にはメッセージが表示されます。 このオプションはすべての外部ドキュメントのコントロール メニューでも使用できます。

## <a name="key-properties"></a>主要なプロパティ
**ドキュメント** – 二重引用符で囲んだ PDF ファイルの URL。

## <a name="additional-properties"></a>追加のプロパティ
**ActualZoom** – コントロールの実際の拡大率で、**ズーム** プロパティで要求された拡大率と異なる場合があります。

**[BorderColor](properties-color-border.md)** – コントロールの境界線の色。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線が**実線**、**破線**、**点線**、または**なし**かどうか。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さ。

**CurrentFindText** – 現在使用されている検索語句。

**CurrentPage** – 実際に表示されている PDF ファイルのページ番号。

**[DisplayMode](properties-core.md)** – コントロールがユーザー入力を許可するか (**編集**)、データのみを表示するか (**表示**)、または無効にするか (**無効**) どうか。

**[DisabledBorderColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロールの境界線の色。

**[塗りつぶし](properties-color-border.md)** – コントロールの背景色。

**FindNext** – ドキュメントで **FindText** の次のインスタンスを検索します。

**FindPrevious** – ドキュメントで **FindText** の前のインスタンスを検索します。

**FindText** – ドキュメント内で検索する検索語句。

**[高さ](properties-size-location.md)** – コントロールの上端と下端間の距離。

**[HoverBorderColor](properties-color-border.md)** – ユーザーがコントロール上にマウス ポインターを重ねているときのコントロールの境界線の色。

**[OnSelect](properties-core.md)** – ユーザーがコントロールをタップまたはクリックする場合のアプリの反応方法。

**OnStateChange** – コントロールの状態が変化するときのアプリの反応方法。

**[PaddingBottom](properties-size-location.md)** – コントロール内のテキストとそのコントロールの下端間の距離。

**[PaddingLeft](properties-size-location.md)** – コントロール内のテキストとそのコントロールの左端間の距離。

**[PaddingRight](properties-size-location.md)** – コントロール内のテキストとそのコントロールの右端間の距離。

**[PaddingTop](properties-size-location.md)** – コントロール内のテキストとそのコントロールの上端間の距離。

**ページ** – 表示するページ番号。

**PageCount** – ドキュメントのページ数。

**[PressedBorderColor](properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロールの境界線の色。

**ShowControls** – オーディオ プレイヤーまたはビデオ プレイヤーに再生ボタンと音量スライダーなどが表示されるかどうか、およびペン コントロールに描画、削除、クリアなどのアイコンが表示されるかどうか。

**[ツールヒント](properties-core.md)** – ユーザーがコントロールにカーソルを置くときに表示される説明テキスト。

**[表示](properties-core.md)** – コントロールが表示されるか非表示になるか。

**[幅](properties-size-location.md)** – コントロールの左端と右端間の距離。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離。

**Zoom** – カメラからの画像、または PDF ビューアーでのファイルの表示を拡大する割合です。

## <a name="example"></a>例

**PDF ビューアー** コントロールを追加し、その**ドキュメント** プロパティを、この例のように二重引用符で囲んだ PDF の URL に設定します。

  **"https://blog.mozilla.org/security/files/2015/05/HTTPS-FAQ.pdf"**

コントロールには PDF ファイルが表示されます。

[コントロールの追加および構成](../add-configure-controls.md) についてはこちらをご覧ください。

## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン

**PDF ビューアー**はまだ実験段階にあるため、PDF ドキュメントのすべてのアクセシビリティ機能がサポートされているわけではありません。 そのため、**ShowControls** を **true**に設定して、ユーザーが外部アプリケーションでドキュメントを開けるようにする必要があります。

[WCAG 2.0](https://www.w3.org/TR/WCAG-TECHS/pdf.html) および [PDF/UA](https://www.pdfa.org/pdfua-the-iso-standard-for-universal-accessibility/) 標準を使用してアクセスできる PDF ドキュメントを作成する方法について説明します。

### <a name="screen-reader-support"></a>スクリーン リーダー サポート
* PDF ドキュメントにタイトルがない場合は、**[ラベル](control-text-box.md)** を使用して見出しを追加することを検討してください。 見出しは **PDF ビューアー**の直前に配置できます。
