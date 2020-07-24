---
title: キャンバス アプリの動作の数式について | Microsoft Docs
description: Power Apps でキャンバス アプリの状態を変更する動作の数式に関する参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/10/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 3402931e6a20fffb68ac9af37f62a2372afc5f57
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3307051"
---
# <a name="understand-behavior-formulas-for-canvas-apps-in-power-apps"></a>Power Apps でのキャンバス アプリの動作の数式について

ほとんどの数式では値を計算します。  Excel のスプレッドシートと同様に、値が変わると再計算が自動的に行われます。  たとえば、**[Label](controls/control-text-box.md)** コントロールの値が 0 未満の場合は値を赤で表示し、それ以外の場合は値を黒で表示できます。 そのため、そのコントロールの **[Color](controls/properties-color-border.md)** プロパティを次の数式に設定します:

**If( Value(TextBox1.Text) >= 0, Color.Black, Color.Red )**

このコンテキストでは、ユーザーが **[Button](controls/control-button.md)** コントロールを選択するとはどういう意味ですか ?  値は変更されていないため、新しく計算する必要はありません。 Excel には、**[Button](controls/control-button.md)** コントロールに相当するものがありません。  

**[Button](controls/control-button.md)** コントロールを選択することによって、ユーザーはアプリの状態を変更する一連のアクションまたは動作を開始します:

* 表示される画面を変更する: **[Back](functions/function-navigate.md)** および **[Navigate](functions/function-navigate.md)** 関数。
* [信号](functions/signals.md)を制御する: **[Enable](functions/function-enable-disable.md)** および **[Disable](functions/function-enable-disable.md)** 関数。
* [データ ソース](working-with-data-sources.md)の項目を更新または削除する: **[Refresh](functions/function-refresh.md)**、**[Update](functions/function-update-updateif.md)**、**[UpdateIf](functions/function-update-updateif.md)**、**[Patch](functions/function-patch.md)**、**[Remove](functions/function-remove-removeif.md)**、**[RemoveIf](functions/function-remove-removeif.md)** 関数。
* [コンテキスト変数](working-with-variables.md#use-a-context-variable)を更新する:  **[UpdateContext](functions/function-updatecontext.md)** 関数。
* [コレクション](working-with-data-sources.md#collections)の項目を作成、更新、または削除する: **[Collect](functions/function-clear-collect-clearcollect.md)**、**[Clear](functions/function-clear-collect-clearcollect.md)**、**[ClearCollect](functions/function-clear-collect-clearcollect.md)** 関数。

これらの関数はアプリの状態を変更するため、自動的に再計算することはできません。 これらは動作の数式と呼ばれる、**[OnSelect](controls/properties-core.md)**、**[OnVisible](controls/control-screen.md)**、**[OnHidden](controls/control-screen.md)**、およびその他の **On...** プロパティの数式で使用できます。

### <a name="more-than-one-action"></a>複数のアクション
実行するアクションのリストを作成するには、セミコロンを使用します。 たとえば、コンテキスト変数を更新してから前の画面に戻ることができます:

* **UpdateContext( { x: 1 } ); Back()**

アクションは、数式で表示される順序で実行されます。  現在の関数が完了しないと、次の関数は開始されません。 エラーが発生した場合、後続の関数が開始されない場合があります。

