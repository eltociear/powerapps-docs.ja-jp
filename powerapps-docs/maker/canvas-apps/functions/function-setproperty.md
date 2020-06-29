---
title: SetProperty 関数 | Microsoft Docs
description: Power Apps テスト スタジオでの SetProperty 関数の構文を含む参照情報
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/19/2018
ms.author: aheneay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: dac65ed25a9e286b056cf3c1408554ca79ea3e11
ms.sourcegitcommit: 6b2961308c41867756ecdd55f55eccbebf70f7f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2020
ms.locfileid: "3307580"
---
# <a name="setproperty-function-in-power-apps-test-studio"></a>Power Apps テスト スタジオでの SetProperty 関数

SetProperty 関数を使うと、ユーザーがコントロールで値を入力または設定した場合と同様に、入力コントロールとの対話をシミュレートできます。 この関数は、Power Apps テスト スタジオでテストを記述している場合にのみ使用できます。 SetProperty 関数を使うと、次のプロパティを設定できます。

## <a name="syntax"></a>構文

*SetProperty(Control Property, value)*

- *Control Property* – 必須。 ユーザーに代わって設定するコントロールのプロパティ。
- *Value* – 必須。 ユーザーに代わって設定するプロパティの値。 

## <a name="examples"></a>例

| コントロール​​   | プロパティ  | 式の例
| :- | :- | :-
| TextInput | テキスト  | ```SetProperty(TextInput1.Text, "Sample text")```
| RichTextEditor    | HtmlText  | ```SetProperty(RichTextEditor1.HtmlText, "<p>Sample text</p>")```
| 切り替え    | 値 | ```SetProperty(Toggle1.Value, false)```
| チェックボックス  | 値 | ```SetProperty(Checkbox1.Value, false)```
| スライダー    | 値 | ```SetProperty(Slider1.Value, 10)```
| 評価    | 値 | ```SetProperty(Rating1.Value, 5)```
| DatePicker    | SelectedDate  | ```SetProperty(DatePicker1.SelectedDate, Date(2020,3,10))```
| ラジオ | 選択済み  | ```SetProperty(Radio1.Selected, "Yes")```
| ラジオ | SelectedText | ```SetProperty(Radio1.SelectedText, "Yes")```
| ドロップダウン | 選択済み | ```SetProperty(Dropdown1.Selected, {Value:"Sample value"})```
| ドロップダウン | SelectedText | ```SetProperty(Dropdown1.SelectedText, {Value:"Sample value"})```
| コンボ ボックス | 選択済み | ```SetProperty(Dropdown1.Selected, {Value:"Sample value"})```
| コンボ ボックス | SelectedItems | ```SetProperty(ComboBox1.SelectedItems, Table({Value:"Sample value"},({Value:"Sample value"}))```
| listbox | 選択済み | ```SetProperty(Listbox1.Selected, {'Value':"Sample value"})```
| listbox | SelectedItems | ```SetProperty(Listbox1.SelectedItems, Table({Value:"Sample value"},({Value:"Sample value"}))```

### <a name="see-also"></a>関連項目

[Test Studio の概要](../test-studio.md) <br>
[Test Studio の操作](../working-with-test-studio.md)