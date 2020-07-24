---
title: 'コンボ ボックス コントロール: リファレンス | Microsoft Docs'
description: プロパティとサンプルを含む、コンボ ボックス コントロールに関する情報
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
ms.openlocfilehash: 9193b3d4ba16b5dca10a8dab471eb731f07d56bf
ms.sourcegitcommit: af653cd30f5879fea97a594d458d355fe18f4834
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/11/2020
ms.locfileid: "3309190"
---
# <a name="combo-box-control-in-power-apps"></a>Power Apps でのコンボ ボックス コントロール
ユーザーが、提供された選択肢から選択できるようにするコントロール。  検索と複数選択をサポートしています。

## <a name="description"></a>内容
**コンボ ボックス**コントロールでは、選択する項目を検索できます。  検索は、SearchField プロパティのサーバー側で実行されるので、パフォーマンスが非常に大規模なデータ ソースによって影響を受けることはありません。  

単一選択モードまたは複数選択モードは SelectMultiple プロパティを介して構成されます。

選択する項目を検索するとき、データ ウィンドウのレイアウト設定を変更することで、項目ごとに、1 つのデータ値、2 つの値、または画像および 2 つの値 (個人) の表示を選択できます。

> [!NOTE]
> *数値*で項目を検索する場合、数値を [Text()](https://docs.microsoft.com/powerapps/maker/canvas-apps/functions/function-text) 関数のテキストに変換します。 たとえば、*Text(12345)*。

## <a name="people-picker"></a>ユーザー ピッカー
**コンボ ボックス**をユーザー ピッカーとして使用するには、データ ウィンドウのレイアウト設定から**個人**テンプレートを選択し、ユーザーの下に表示される関連データのプロパティを構成します。

## <a name="key-properties"></a>主要なプロパティ
**[Items](properties-core.md)** – 選択元となるデータのソース。

**DefaultSelectedItems** – ユーザーがコントロールを操作する前に、最初に選択した項目。

**SelectedItems** – ユーザーの操作の結果として選択された項目の一覧。

**SelectMultiple** – ユーザーが、単一の項目または複数の項目を選択できるかどうか。

**IsSearchable** – 選択する前にユーザーが項目を検索できるかどうか。

**SearchFields** - ユーザーがテキストを入力するときに検索されるデータ ソースのデータ フィールド。  複数のフィールドを検索するには、ComboBox1.SearchFields = ["MyFirstColumn", "MySecondColumn"] と設定します

## <a name="additional-properties"></a>追加のプロパティ
**[AccessibleLabel](properties-accessibility.md)** – スクリーン リーダー用のラベル。

**[BorderColor](properties-color-border.md)** – コントロールの境界線の色。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線が**実線**、**破線**、**点線**、または**なし**かどうか。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さ。

**DisplayFields** – 検索によって返される各項目に対して表示されるフィールドの一覧。  プロパティ オプション タブで、データ ウィンドウを介して構成するのが最も簡単です。

**[DisplayMode](properties-core.md)** – コントロールがユーザー入力を許可するか (**編集**)、データのみを表示するか (**表示**)、または無効にするか (**無効**) どうか。

**[FocusedBorderColor](properties-color-border.md)** – コントロールがフォーカスされているときのコントロールの境界線の色。

**[FocusedBorderThickness](properties-color-border.md)** – コントロールがフォーカスされているときのコントロールの境界線の太さ。

**[高さ](properties-size-location.md)** – コントロールの上端と下端間の距離。

**InputTextPlaceholder** – 項目が選択されていない場合、エンドユーザーに表示される説明テキスト。

**OnChange** – ユーザーが選択を変更するときのアプリの応答の仕方。

**OnNavigate** – ユーザーが項目をクリックするときのアプリの応答の仕方。

**[OnSelect](properties-core.md)** – ユーザーがコントロールをタップまたはクリックする場合のアプリの反応方法。

**[TabIndex](properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序。

**[表示](properties-core.md)** – コントロールが表示されるか非表示になるか。

**[幅](properties-size-location.md)** – コントロールの左端と右端間の距離。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離。

## <a name="example"></a>例
1. **挿入**タブで、**コントロール** メニューを開いてから、**コンボ ボックス**を選択します。  

1. 右側のウィンドウの**プロパティ** タブで、**データ ソースの選択**リスト (**項目**の横にある) を開いてから、データ ソースを追加または選択します。

1. 同じタブで、**編集** (**フィールド**の横にある) を選択します。

1. **データ** ウィンドウで、**主要テキスト**リストを開いてから、**コンボ ボックス** コントロールに表示する列を選択します。

1. Alt キーを押しながら、**コンボ ボックス** コントロールを開く下矢印を選択します。

    コントロールには、指定したデータ ソースで指定した列からのデータが表示されます。
    
1. (オプション) 既定で最初のレコードを表示するには、**DefaultSelectedItems** プロパティをこの式に設定し、*DataSource* をデータ ソースの名前に置き換えます:

    `First(DataSource)`

## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
### <a name="color-contrast"></a>色のコントラスト
次の間には適切な色のコントラストが必要です:
* **ChevronFill** と **ChevronBackground**
* **ChevronHoverFill** と **ChevronHoverBackground**
* **SelectionColor** と **SelectionFill**
* **SelectionFill** と **[塗りつぶし](properties-color-border.md)**
* **SelectionTagColor** と **SelectionTagFill**

これは、[標準の色のコントラスト要件](../accessible-apps-color.md) に追加されるものです。

### <a name="screen-reader-support"></a>スクリーン リーダー サポート
* **[AccessibleLabel](properties-accessibility.md)** が存在する必要があります。

    > [!NOTE]
  > タッチ スクリーンでは、スクリーン リーダーのユーザーはコンボ ボックスのコンテンツを順番に移動できます。 コンボ ボックスは、選択したときにコンテンツの表示または非表示を切り替えるボタンとして機能します。

### <a name="keyboard-support"></a>キーボードのサポート
* **[TabIndex](properties-accessibility.md)** を 0 以上にして、キーボード ユーザーがそこに移動できるようにする必要があります。
* フォーカス インジケーターは明確に表示する必要があります。 これを実現するには **[FocusedBorderColor](properties-color-border.md)** および **[FocusedBorderThickness](properties-color-border.md)** を使用します。

    > [!NOTE]
  > タブ キーを押すと、コンボ ボックスに移動したり、コンボ ボックスから移動したりします。 矢印キーを押すと、コンボ ボックスのコンテンツに移動します。 Esc キーは、開いたときにドロップダウンを閉じます。
