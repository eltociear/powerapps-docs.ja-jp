---
title: 'エクスポート コントロールおよびインポート コントロール: リファレンス | Microsoft Docs'
description: プロパティとサンプルを含む、エクスポート コントロールおよびインポート コントロールに関する情報
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/09/2020
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 5d5144db3147defa43c5e11cb169a6ebc9b02105
ms.sourcegitcommit: a02b20113164acb11955d27ef4ffa421ee0fba9d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2020
ms.locfileid: "3308201"
---
# <a name="export-control-and-import-control-in-power-apps"></a>Power Apps でのエクスポート コントロールおよびエクスポート コントロール
ローカル ファイルにデータをエクスポートするコントロールと、そのデータを Power Apps 内の別のアプリにインポートするコントロール。

## <a name="description"></a>内容
同じデータを使用する複数のアプリを作成しても、これら以外のアプリとはそのデータを共有しない場合には、**エクスポート** コントロールと**インポート** コントロールを使用してデータをエクスポートおよびインポートできます。 データをエクスポートすると、別のコンピューターにコピー可能な圧縮ファイルが作成されますが、このファイルは、Power Apps 以外のプログラムでは読み取ることはできません。

## <a name="warning"></a>警告
アプリでこの機能を有効にすると、セキュリティの脆弱性にさらされ、データが漏洩する可能性があります。  認定済みの信頼できるファイルのみをインポートし、エクスポートするデータは機密情報または取扱いに注意が必要なもの以外のみとすることをお勧めします。

## <a name="limitations"></a>制限
エクスポート機能は、Web ブラウザーではサポートされていません。

## <a name="key-properties"></a>主要なプロパティ
**データ** – ローカル ファイルにエクスポートするコレクションの名前。

* **データ** プロパティは、**エクスポート** コントロールで使用できますが、**インポート** コントロールでは使用できません。

**[OnSelect](properties-core.md)** – ユーザーがコントロールをタップまたはクリックする場合のアプリの反応方法。

## <a name="additional-properties"></a>追加のプロパティ
**[配置](properties-text.md)** – コントロールの水平方向の中心に対するテキストの位置。

**[BorderColor](properties-color-border.md)** – コントロールの境界線の色。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線が**実線**、**破線**、**点線**、または**なし**かどうか。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さ。

**[色](properties-color-border.md)** – コントロールのテキストの色。

**[DisplayMode](properties-core.md)** – コントロールがユーザー入力を許可するか (**編集**)、データのみを表示するか (**表示**)、または無効にするか (**無効**) どうか。

**[DisabledBorderColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロールの境界線の色。

**[DisabledColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロール内のテキストの色。

**[DisabledFill](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロールの背景色。

**[塗りつぶし](properties-color-border.md)** – コントロールの背景色。

**[FocusedBorderColor](properties-color-border.md)** – コントロールがフォーカスされているときのコントロールの境界線の色。

**[FocusedBorderThickness](properties-color-border.md)** – コントロールがフォーカスされているときのコントロールの境界線の太さ。

**[フォント](properties-text.md)** – テキストを表示するフォントのファミリーの名前。

**[FontWeight](properties-text.md)** – コントロール内のテキストの太さ: **太字**、**中太**、**標準**、または**細字**。

**[高さ](properties-size-location.md)** – コントロールの上端と下端間の距離。

**[HoverBorderColor](properties-color-border.md)** – ユーザーがコントロール上にマウス ポインターを重ねているときのコントロールの境界線の色。

**[HoverColor](properties-color-border.md)** – ユーザーがコントロールにマウス ポインターを重ねているときのコントロール内のテキストの色。

**[HoverFill](properties-color-border.md)** – ユーザーがコントロールにマウス ポインターを重ねているときのコントロールの背景色。

**[斜体](properties-text.md)** – コントロール内のテキストを斜体にするかどうか。

**[パディング](properties-size-location.md)** – インポートまたはエクスポート ボタンのテキストと、そのボタンの端との間の距離。

**[PressedBorderColor](properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロールの境界線の色。

**[PressedColor](properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロール内のテキストの色。

**[PressedFill](properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロールの背景色。

**[RadiusBottomLeft](properties-size-location.md)** – コントロールの左下隅を丸める度合い。

**[RadiusBottomRight](properties-size-location.md)** – コントロールの右下隅を丸める度合い。

**[RadiusTopLeft](properties-size-location.md)** – コントロールの左上隅を丸める度合い。

**[RadiusTopRight](properties-size-location.md)** – コントロールの右上隅を丸める度合い。

**[サイズ](properties-text.md)** – コントロールに表示されるテキストのフォント サイズ。

**[Strikethrough](properties-text.md)** – コントロールに表示されるテキストに取り消し線を付けるかどうか。

**[TabIndex](properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序。

**[テキスト](properties-core.md)** – コントロールに表示されるテキスト、またはユーザーがコントロールに入力するテキスト。

**[下線](properties-text.md)** – コントロールに表示されるテキストの下に線を引くかどうか。

**[VerticalAlign](properties-text.md)** – コントロールの垂直方向の中心に対するコントロール上でのテキストの位置。

**[表示](properties-core.md)** – コントロールが表示されるか非表示になるか。

**[幅](properties-size-location.md)** – コントロールの左端と右端間の距離。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離。

## <a name="example"></a>例
1. **[ボタン](control-button.md)** コントロールを追加し、**[OnSelect](properties-core.md)** プロパティに次の式を設定します: <br>
   ```
   ClearCollect(Products, {Name:"Europa", Price:"10.99"}, {Name:"Ganymede", Price:"12.49"}, {Name:"Callisto", Price:"11.79"})
   ```
   詳細については、[コントロールの追加、名前付け、および構成](../add-configure-controls.md)、**[ClearCollect](../functions/function-clear-collect-clearcollect.md)** や [その他の関数](../formula-reference.md) をお読みください。
2. F5 キーを押し、**[ボタン](control-button.md)** コントロールを選択してから、Esc キーを押します。
3. **エクスポート** コントロールを追加し、**データ** プロパティに**製品**を設定します。
4. F5 キーを押し、**エクスポート** コントロールを選択してファイル *Data.zip* をダウンロードします。
5. **保存**を選択してから、Esc キーを押して既定のワークスペースに戻ります。
6. 新規または既存のアプリに、**インポート** コントロールを追加し、**MyData** という名前を付け、**[OnSelect](properties-core.md)** プロパティに次の式を設定します:<br>
   **Collect(ImportedProducts, MyData.Data)**
7. F5 キーを押して **MyData** を選択してから、エクスポートしたファイルを選択し、**開く**を選択します。
8. Esc キーを押して**ファイル** メニューの**コレクション**を選択し、エクスポートしたデータが現在のアプリに存在することを確認します。


## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
**エクスポート**と**インポート**は特殊なボタンなので、**[ボタン](control-button.md)** と同じガイドラインが適用されます。
