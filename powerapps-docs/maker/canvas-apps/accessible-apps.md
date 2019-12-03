---
title: アクセシビリティ対応キャンバス アプリの作成 | Microsoft Docs
description: 障碍を持つユーザーのためにアクセシビリティ対応のキャンバス アプリを作成する方法について説明します
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/03/2018
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 56e5ec7f303706ded114655e5c6d473408e9ddd7
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2019
ms.locfileid: "74680031"
---
# <a name="create-accessible-canvas-apps-in-powerapps"></a>PowerApps でアクセシビリティ対応キャンバス アプリを作成する
アクセシビリティ対応のキャンバス アプリでは、視覚や聴覚などに障碍のあるユーザーが、アプリを正しく使えるように配慮されています。  これは、多くの政府機関や組織にとっての要件というだけではありません。以下のガイドラインに従うことで、能力に関係なくあらゆるユーザーの使いやすさが向上します。

**[アクセシビリティ チェック](accessibility-checker.md)** を使用して、アプリの潜在的なアクセシビリティの問題を確認します。 

## <a name="layout-and-color"></a>レイアウトと色
常識的でシンプルなデザインを採用することで、アプリはすべてのユーザーにとってアクセスしやすいものとなります。  アプリを大幅にカスタマイズする場合は、以下の推奨事項に留意してください。  Power Apps のテーマは、既定でアクセス可能です。
- すべての要素が明確に表示され、テキストが十分なサイズであることを確認します。  すべてのコンテンツを、肉眼で簡単に読んで理解できるようにする必要があります。
- 要素を表示するための項目の可視性プロパティは、使わないでください。  何かを条件付きで表示する必要がある場合は、新しい画面にコンテンツを作成して、そこにユーザーを移動させ、再び戻らせます。
- 入力要素が画面上でラベル付けされていることを確認します。 スクリーン リーダーが読み上げる内容は、 **[AccessibilityLabel](controls/properties-accessibility.md)** プロパティによって定義されます。
- 色をカスタマイズする場合は、テキストと背景のコントラストが 4.5:1 以上になるようにします。  このプロセスを支援するソフトウェア ツールはすぐに使用可能です。
- 上から下に、左から右に読んだときに、レイアウトが論理的な流れに沿っていることを確認します。


## <a name="keyboard-support"></a>キーボードのサポート
アプリのアクセシビリティをテストする場合は、キーボードのみでアプリを使えること、iOS および Android のアクセシビリティ モードで使えること、スクリーン リーダーを有効にして正しく移動できることを確認します。

キーボード ナビゲーション (スクリーン リーダーあり/なし) については、各コントロールの **[TabIndex](controls/properties-accessibility.md)** プロパティを設定することで、Tab キーを使った入力フィールドの移動が論理的な順序に従うようにします。
- ラベル、イメージ、アイコン、シェイプコントロール-これらが対話型の要素 (つまり、ボタン) を表す場合は、TabIndex を0に設定します。装飾的な要素またはテキストである場合は、TabIndex を-1 に設定します。
- タブのインデックスを 0 より大きい値に設定しないでください。

## <a name="screen-reader-support"></a>スクリーン リーダーのサポート
次のソフトウェアの組み合わせは、スクリーンリーダーでのパワーアプリの使用に関してサポートされている推奨事項です。

- **Windows**: Microsoft Edge/ナレーター
- **macOS**: Safari / VoiceOver
- **Android**: Power Apps アプリ/Talkback
- **iOS**: Power Apps アプリ/VoiceOver

スクリーン リーダーを使った体験を満足のいくものにするには、次の操作を実行することをお勧めします。

- すべての入力コントロールの **[AccessibilityLabel](controls/properties-accessibility.md)** プロパティを設定します。
- 画像の **[AccessibilityLabel](controls/properties-accessibility.md)** に適切な説明を設定します。
  - 画像をボタンまたはリンクとしては使わず (つまり装飾用のアイコンとして使う)、画像がスクリーン リーダーによって読み上げられてはならない場合は、 **[AccessibilityLabel](controls/properties-accessibility.md)** を空にするか、または設定しません。
  - 画像またはアイコンをボタンとして使う場合は、 **[TabIndex](controls/properties-accessibility.md)** を 0 に設定し、 **[AccessibilityLabel](controls/properties-accessibility.md)** をリンクの説明に設定します。


## <a name="multimedia"></a>マルチメディア
すべてのビデオに字幕が付いていること、およびすべてのオーディオ録音のトランスクリプトが使用できることを確認します。  **ビデオ**コントロールは、 **ClosedCaptionsUrl**プロパティを使用して、WebVTT 形式のクローズドキャプションをサポートします。

スクリーン リーダーを有効にした場合、**タイマー** では、ボタンのテキストではなく経過した時間がアナウンスされることに注意してください。  不透明度が低くてタイマーが表示されない場合でも、アナウンスをオフにすることはできません。

## <a name="working-with-signatures"></a>署名の使用
PenInput コントロールを使った署名フィールドがある場合は、代わりとなる署名の入力方法を用意する必要があります。  推奨される方法は、ユーザーが名前を入力できる TextInput コントロールを表示することです。  署名の指示が **[AccessibilityLabel](controls/properties-accessibility.md)** プロパティに設定されていること、およびコントロールがペン入力の近く (右またはすぐ下) に配置されていることを確認します。



関連項目:
- [アクセシビリティのプロパティ](controls/properties-accessibility.md)
- [アクセシビリティ チェックを使用](accessibility-checker.md)
- [PowerApps でのアクセシビリティ対応の色](accessible-apps-color.md)
