---
title: 'ペン入力コントロール: リファレンス | Microsoft Docs'
description: プロパティとサンプルを含む、ペン入力コントロールに関する情報
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
ms.openlocfilehash: a5645f2f0d515d7eca125f3cd89ecff0c63cfa51
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/13/2020
ms.locfileid: "3308431"
---
# <a name="pen-input-control-in-power-apps"></a>Power Apps でのペン入力コントロール
ユーザーが画像の領域を描画、削除、強調表示できるコントロール。

## <a name="description"></a>内容
ユーザーはこのコントロールをホワイトボードのように使用して、図を描いたり、入力したテキストに変換可能な文字を書いたりできます。

## <a name="key-properties"></a>主要なプロパティ
**画像** – エンド ユーザーによって描画された画像を表す出力プロパティ。

**[色](properties-color-border.md)** – 入力ストロークの色。

**モード** – このコントロールは **描画**または**削除**モードです。  選択モードは非推奨になりました。

## <a name="additional-properties"></a>追加のプロパティ
**[AccessibleLabel](properties-accessibility.md)** – スクリーン リーダー用のラベル。 コントロールの目的だけでなく、代替の入力方法についての説明にも使用できます。

**[BorderColor](properties-color-border.md)** – コントロールの境界線の色。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線が**実線**、**破線**、**点線**、または**なし**かどうか。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さ。

**[DisplayMode](properties-core.md)** – コントロールがユーザー入力を許可するか (**編集**)、データのみを表示するか (**表示**)、または無効にするか (**無効**) どうか。

**[塗りつぶし](properties-color-border.md)** – コントロールの背景色。

**[高さ](properties-size-location.md)** – コントロールの上端と下端間の距離。

**入力** – **非推奨。** 入力で、マウス、ペンまたはタッチ入力がサポートされるかどうか。  既定値 (7) では 3 つすべてがサポートされます。

**[OnSelect](properties-core.md)** – ユーザーがコントロールをタップまたはクリックする場合のアプリの反応方法。

**[SelectionColor](properties-color-border.md)** – リスト内で選択された項目のテキストの色、またはペン コントロールの選択ツールの色。

**SelectionThickness** – ペン入力コントロールの選択ツールの太さ。

**ShowControls** – オーディオ プレイヤーまたはビデオ プレイヤーに再生ボタンと音量スライダーなどが表示されるかどうか、およびペン コントロールに描画、削除、クリアなどのアイコンが表示されるかどうか。

**[サイズ](properties-text.md)** – コントロールに表示されるテキストのフォント サイズ。

**[ツールヒント](properties-core.md)** – ユーザーがコントロールにカーソルを置くときに表示される説明テキスト。

**[表示](properties-core.md)** – コントロールが表示されるか非表示になるか。

**[幅](properties-size-location.md)** – コントロールの左端と右端間の距離。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離。

## <a name="related-functions"></a>関連する関数
[**Collect**( *CollectionName*, *DatatoCollect* )](../functions/function-clear-collect-clearcollect.md)

## <a name="example"></a>例
### <a name="create-a-set-of-images"></a>一連の画像を作成する
1. **ペン入力**コントロールを追加し、**MyDoodles** という名前を付け、**ShowControls** プロパティを **true** に設定します。
   
    [コントロールの追加、名前付け、構成](../add-configure-controls.md) についてはこちらをご覧ください。
2. **[ボタン](control-button.md)** コントロールを追加し、**MyDoodles** の下に移動し、**[ボタン](control-button.md)** コントロールの **[テキスト](properties-core.md)** プロパティを **追加**と表示するように設定します。
3. **[ボタン](control-button.md)** コントロールの **[OnSelect](properties-core.md)** プロパティを次の数式に設定します:<br>
   **Collect(Doodles, {Sketch:MyDoodles.Image})**
4. **画像ギャラリー** コントロールを追加し、**[ボタン](control-button.md)** コントロールの下に移動し、**画像ギャラリー**の幅を表示項目が 3 つになるまで縮小します。
5. **画像ギャラリー** コントロールの **[項目](properties-core.md)** プロパティを **Doodles** に設定してから、F5 キーを押します。
6. **MyDoodles** で画像を描画してから、**[ボタン](control-button.md)** コントロールをクリックまたはタップします。
   
    描画した画像が、**画像ギャラリー** コントロールに表示されます。
7. (オプション) **ペン入力** コントロール内で描画した画像を消去するアイコンをクリックまたはタップし、別の画像を描画してから、**[ボタン](control-button.md)** コントロールをクリックまたはタップします。
8. **画像ギャラリー** コントロールで、**[画像](control-image.md)** コントロールの **[OnSelect](properties-core.md)** プロパティを次の数式に設定します:<br>
   **Remove(Doodles, ThisItem)**
9. **画像ギャラリー** コントロール内の画像をクリックまたはタップすることにより、その画像を削除します。

**[SaveData](../functions/function-savedata-loaddata.md)** 関数を使用して画像をローカルに保存するか、**[パッチ](../functions/function-patch.md)** 関数を使用してデータ ソースに保存します。


## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
### <a name="color-contrast"></a>色のコントラスト
次の間には適切な色のコントラストが必要です:
* **[BorderColor](properties-color-border.md)** とコントロールの外側の色 (境界線がある場合)
* **[塗りつぶし](properties-color-border.md)** とコントロールの外側の色 (境界線がある場合)

### <a name="screen-reader-support"></a>スクリーン リーダー サポート
* **[AccessibleLabel](properties-accessibility.md)** が存在する必要があります。

    > [!IMPORTANT]
  > スクリーン リーダー ユーザーは**ペン入力**にアクセスできません。 常に入力の代替形式を提供してください。 たとえば、スケッチが必要な場合は、ユーザーが画像をアップロードできるように、**[画像の追加](control-add-picture.md)** コントロールの追加を検討してください。 両方の方法を提供すると、ユーザーがより快適な方法を選択できるようになります。

### <a name="keyboard-support"></a>キーボードのサポート

> [!IMPORTANT]
> キーボード ユーザーは**ペン入力**にアクセスできません。 常に入力の代替形式を提供してください。 たとえば、署名が必要な場合は、ユーザーが名前を入力できるように **[テキスト入力](control-text-input.md)** を追加することを検討してください。 両方の方法を提供すると、ユーザーがより快適な方法を選択できるようになります。
