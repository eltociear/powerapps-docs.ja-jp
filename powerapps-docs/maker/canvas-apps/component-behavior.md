---
title: コンポーネントの動作の数式 | Microsoft Docs
description: コンポーネント ベースのアクションが発生するときに、キャンバス アプリで 1 つ以上のタスクを実行します。
author: yifwang
ms.service: powerapps
ms.topic: article
ms.date: 04/24/2020
ms.author: yifwang
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 3d04634096770921d3829f8d6ac456153e485d7f
ms.sourcegitcommit: 943672dad0041d3bab25b44cd8c4d25e88f39b93
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/25/2020
ms.locfileid: "3309650"
---
# <a name="behavior-formulas-for-components"></a>コンポーネントの動作の数式

> [!IMPORTANT]
> この機能は、まだパブリック プレビューにあります。 詳細については [実験的機能とプレビュー機能](working-with-experimental.md) を参照してください。

イベントがコンポーネント インスタンスの変更をトリガーしたときに実行される、[動作の数式](working-with-formulas-in-depth.md) を 1 つ以上指定します。 

たとえば、コンポーネントの **OnReset** プロパティを、初期化を行い入力をクリアする 1 つ以上の数式に設定します。 **Reset** 関数がコンポーネント インスタンスで実行するときに、値をリセットします。

## <a name="onreset"></a>OnReset

コンポーネント マスターを選択して、プロパティのドロップダウン リスト (数式バーの左側) の **OnReset** で、1 つ以上の数式を入力します。

> [!div class="mx-imgBorder"]
> ![OnReset の例](./media/component-behavior/example-onreset.png "OnReset の例")

**OnReset** をテストするには、コンポーネントをリセットするためのコントロールを構成します。 たとえば、この式のボタンの **OnSelect** プロパティ: **リセット** (*ComponentName*)。

### <a name="example---reset-timer"></a>例 - タイマーをリセットする

> [!div class="mx-imgBorder"]
> ![OnReset の例](./media/component-behavior/Resettimer.gif "OnReset の例")

この時間ピッカー コンポーネントでは、時間 _selectedHour および _selectedMinute を表示するために 2 つの変数が使用されます。 ピッカーがリセットされると、これらの変数は既定値は、たとえば 12: 12 にリセットされます。コンポーネントの OnReset プロパティの数式は次のとおりです: **Set(_selectedHour,12); Set(_selectedMinute,12)**

リセットをトリガーするには、画面に移動してコンポーネントのインスタンスを挿入します。 ボタンを追加し、OnReset をトリガーするのに **リセット (TimerComponent_instance)** を呼び出すため、ボタンの OnSelect を構成します。

> [!div class="mx-imgBorder"]
> ![リセット ボタン](./media/component-behavior/reset-button.png "リセット ボタン")

## <a name="update-onreset-using-custom-property"></a>カスタム プロパティを使用して OnReset を更新する

コンポーネントの外部からコンポーネント インスタンスをリセットする以外に、内部から OnReset をトリガーする別のメソッドがあります。 "**値が変化するときに OnReset を発生させる**"は、カスタム入力プロパティを作成するときのオプションです。 コンポーネントの OnReset をトリガーするのに、このプロパティの値を変更できます。 このメソッドは、既定値を簡単に設定およびリセットするように設計されています。 

> ![OnReset の例](./media/component-behavior/property-trigger.png "OnReset の例")

### <a name="example"></a>例

> [!div class="mx-imgBorder"]
> ![OnReset の例](./media/component-behavior/updateordernumber2.gif "OnReset の例")

上記の例は、受注番号の確認および番号の更新を示します。 数値の上下コンポーネントは、受注数を増減するために使用されます。 左側のギャラリーを選択すると、選択したツールの受注番号を表示するため、数値の上下コンポーネントの既定の数がリセットされます。 **値が変化するときに OnReset を発生させる**は、入力が変更するときに既定値をリセットできるようにしました。 

これを行うには、既定のプロパティの **値が変化するときに OnReset を発生させる**を確認します。 コンポーネントの **OnReset** は **Set(_numericValue,'Numeric up down'.DefaultValue)** に設定します。 _numericValue は、現在の受注値の値を格納する変数です。 テキスト入力コントロールの**既定**を、**If(IsBlank(_numericValue), 'Numeric up down'.DefaultValue, _numericValue)** に設定します。

### <a name="see-also"></a>関連項目

- [キャンバス アプリの概要](create-component.md)
- [キャンバス アプリ コンポーネントのライブラリ](component-library.md)
