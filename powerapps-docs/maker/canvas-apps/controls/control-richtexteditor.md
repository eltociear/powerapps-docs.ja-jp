---
title: 'リッチ テキスト エディター コントロール: リファレンス | Microsoft Docs'
description: プロパティとサンプルを含む、リッチ テキスト エディター コントロールに関する情報
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: article
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/24/2018
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1c9bbfd724f588dce86c5ba2e620404f554d2bcd
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3305947"
---
# <a name="rich-text-editor-control-in-power-apps"></a>Power Apps でのリッチ テキスト エディター コントロール
エンド ユーザーが WYSIWYG 編集領域内のテキストの書式を設定できるようにします。  出力形式は、HTML です。

## <a name="description"></a>内容
**リッチ テキスト エディター** コントロールにより、アプリのユーザーにテキストの書式設定のための WYSIWYG 編集領域が提供されます。  コントロールの入出力形式は HTML です。

コントロールにより、コピーしたリッチ テキスト (つまり Web ブラウザーまたは Word から) をコントロールに貼り付けることができます。  

コントロールの使用目的はテキストの書式設定であり、入力 HTML の整合性の保持は保証されません。  すべてのスクリプト、スタイル、オブジェクト、その他の潜在的に危険なタグはエディターによって削除されます。  これは、リッチ テキストが Power Apps の外部で作成された場合、作成された製品と同じ同じ外観ではない可能性があることを意味します。

現在サポートされている機能は次のとおりです:
- 太字、斜体、下線
- テキストの色、強調表示色
- テキストのサイズ
- 番号付きリスト、箇条書きリスト
- ハイパーリンク
- 書式設定のクリア

フォーム内のコントロールを使用するには、"複数行テキストの編集" カードを選択し、RTE コントロールを挿入してカスタマイズします。

## <a name="key-properties"></a>主要なプロパティ
**[既定](properties-core.md)** – エディターに表示される最初のテキスト値の入力プロパティ。

**HtmlText** – HTML 形式で作成されたリッチ テキストの出力プロパティ。


## <a name="additional-properties"></a>追加のプロパティ
**[AccessibleLabel](properties-accessibility.md)** – スクリーン リーダー用のラベル。 添付ファイルの目的を説明する必要があります。

**[DisplayMode](properties-core.md)** – コントロールがファイルの追加と削除を許可するかどうか (**編集**)、データの表示のみを許可するか (**表示**)、または無効 (**無効**) にします。

**EnableSpellCheck** – ブラウザーのスペル チェッカーが有効かどうか。 この機能は、ブラウザーのデフォルト言語でのみスペル チェックを提供することに注意してください。  Power Apps for Windows はこのプロパティをサポートしていません。

**[高さ](properties-size-location.md)** – コントロールの上端と下端間の距離。

**[TabIndex](properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序。

**[表示](properties-core.md)** – コントロールが表示されるかどうか。

**[幅](properties-size-location.md)** – コントロールの左端と右端間の距離。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離。


## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
### <a name="screen-reader-support"></a>スクリーン リーダー サポート
* **[AccessibleLabel](properties-accessibility.md)** が存在する必要があります。

### <a name="keyboard-support"></a>キーボードのサポート
* **[TabIndex](properties-accessibility.md)** を 0 以上にして、キーボード ユーザーがそこに移動できるようにする必要があります。

> [!TIP]
> 他のキーボード ショートカットについて理解するには、エディターがフォーカスされている間に **Alt + 0** を使用します。
