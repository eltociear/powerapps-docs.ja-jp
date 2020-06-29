---
title: 'HTML テキスト コントロール: リファレンス | Microsoft Docs'
description: プロパティとサンプルを含む、HTML テキスト コントロールに関する情報
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/25/2016
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a49cfef13cb7c52c972ab67287cd4e886d981cb0
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3306039"
---
# <a name="html-text-control-in-power-apps"></a>Power Apps での HTML テキスト コントロール
テキストを表示し、書式設定のための HTML タグを変換するボックス。

## <a name="description"></a>内容
**HTML テキスト** コントロールは、プレーン テキストや数値を表示するだけでなく、HTML タグ (改行なしスペースなど) の変換も行います。

## <a name="key-properties"></a>主要なプロパティ
**[色](properties-color-border.md)** – コントロールのテキストの色。

**[フォント](properties-text.md)** – テキストを表示するフォントのファミリーの名前。

**HtmlText** – HTML テキスト コントロールに表示される、HTML タグを含む可能性のあるテキスト。

## <a name="additional-properties"></a>追加のプロパティ
**[BorderColor](properties-color-border.md)** – コントロールの境界線の色。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線が**実線**、**破線**、**点線**、または**なし**かどうか。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さ。

**[DisplayMode](properties-core.md)** – コントロールがユーザー入力を許可するか (**編集**)、データのみを表示するか (**表示**)、または無効にするか (**無効**) どうか。

**[DisabledBorderColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロールの境界線の色。

**[DisabledFill](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロールの背景色。

**[塗りつぶし](properties-color-border.md)** – コントロールの背景色。

**[高さ](properties-size-location.md)** – コントロールの上端と下端間の距離。

**[HoverBorderColor](properties-color-border.md)** – ユーザーがコントロール上にマウス ポインターを重ねているときのコントロールの境界線の色。

**[OnSelect](properties-core.md)** – ユーザーがコントロールをタップまたはクリックする場合のアプリの反応方法。

**[PaddingBottom](properties-size-location.md)** – コントロール内のテキストとそのコントロールの下端間の距離。

**[PaddingLeft](properties-size-location.md)** – コントロール内のテキストとそのコントロールの左端間の距離。

**[PaddingRight](properties-size-location.md)** – コントロール内のテキストとそのコントロールの右端間の距離。

**[PaddingTop](properties-size-location.md)** – コントロール内のテキストとそのコントロールの上端間の距離。

**[サイズ](properties-text.md)** – コントロールに表示されるテキストのフォント サイズ。

**[ツールヒント](properties-core.md)** – ユーザーがコントロールにカーソルを置くときに表示される説明テキスト。

**[表示](properties-core.md)** – コントロールが表示されるか非表示になるか。

**[幅](properties-size-location.md)** – コントロールの左端と右端間の距離。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離。

## <a name="related-functions"></a>関連する関数
[**Find**( *FindString*, *WithinString* )](../functions/function-find.md)

## <a name="example"></a>例
1. **[ラベル](control-text-box.md)** コントロールを追加して**ソース**という名前を付け、その **[テキスト](properties-core.md)** プロパティを次の文字列に設定します:

"\<p>\&nbsp;非常に \&quot;深い\&quot; グローバリゼーションおよびローカライズを実行しました。\<p>"

[コントロールの追加、名前付け、構成](../add-configure-controls.md) についてはこちらをご覧ください。

1. **HTML テキスト** コントロールを追加し、その **HtmlText** プロパティを次の値に設定します:<br>
   **Source.Text**
   
     **HTML テキスト** コントロールは **[ラベル](control-text-box.md)** コントロールと同じテキストを表示しますが、タグを適切な文字に変換します。


## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
**HTML テキスト**は対話型のためのものではありません。 テキストの表示目的にのみ使用する必要があります。

### <a name="color-contrast"></a>色のコントラスト
次の間には適切な色のコントラストが必要です:
* **[Color](properties-color-border.md)** と **[Fill](properties-color-border.md)**
* カスタム色とその背景を含むテキスト

### <a name="screen-reader-support"></a>スクリーン リーダー サポート
* **HtmlText** が存在する必要があります。

### <a name="keyboard-support"></a>キーボードのサポート
* **HtmlText** には、`<button>`、`<a>`、または`<input>`などの対話型の要素を含めることはできません。 Power Apps の **[TabIndex](properties-accessibility.md)** システムでは、**HtmlText** 内の要素は考慮されません。
