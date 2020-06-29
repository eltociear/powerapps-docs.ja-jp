---
title: With 関数 | Microsoft Docs
description: Power Apps での With 関数の構文を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 02/07/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0d1105577459cc447fbd2a14a946ce5651d4d236
ms.sourcegitcommit: 80120b59d440bb7a3ddca93cd51154607f749f6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "3307902"
---
# <a name="with-function-in-power-apps"></a>Power Apps での With 関数
値を計算し、名前付きの値のインライン レコードを含む 1 つの[レコード](../working-with-tables.md#records) に対してアクションを実行します。

## <a name="description"></a>内容

**With** 関数は単一レコードの数式を評価します。  数式は、値を計算したり、操作 (データの変更や接続の操作など) を実行したりできます。  [**ForAll** 関数](function-forall.md) を使用して、レコードのテーブル内のすべてのレコードの数式を評価します。

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

**With** を使用して、複雑な数式を小さな名前の付いたサブ数式に分割することで、複雑な数式を読みやすくします。  これらの名前付きの値は、**With** のスコープに限定された単純なローカル変数のように機能します。  [**UpdateContext** 関数](function-updatecontext.md) で使用されるものと同じインライン レコード構文を **With** で使用できます。  **With** を使用すると、自己完結型で理解しやすく、宣言式のコンテキストで使用できるため、コンテキスト変数やグローバル変数よりも推奨されています。  

**With** を使用して、[**Patch**](function-patch.md) または [**Match**](function-ismatch.md) などの関数によって返されるレコードのフィールドにアクセスします。  **With** は、これらの関数の値を、以降の計算またはアクションで使用するのに十分な時間保持します。  

**With** への*レコード*引数がエラーの場合、そのエラーは関数によって返され、*数式*は評価されません。

## <a name="syntax"></a>構文
**With**( *レコード*、*数式* )

* *Record* – 必須。 実行されるレコード。  名前の値には、インライン構文 `{ name1: value1, name2: value2, ... }` を使用します
* *Formula* – 必須。  *レコード*について評価する数式。  この数式は、*レコード*の任意のフィールドをレコード スコープとして直接参照できます。

## <a name="examples"></a>例

### <a name="simple-named-values"></a>単純な名前付き値

```powerapps-dot
With( { radius: 10, 
        height: 15 },
    Pi() * (radius*radius) * height
)
// Result: 4712.38898038 (as shown in a label control)
```

この例では、名前付き値のレコードを使用して、シリンダーの体積を計算します。  **With** はすべての入力値を一緒にキャプチャするために使用されているため、計算自体から簡単に分離できます。  

### <a name="nested-with"></a>With のネスト

![With 関数を使用した金利計算機](media/function-with/interest-calculator.gif)

```powerapps-dot
With( { AnnualRate: RateSlider/8/100,        // slider moves in 1/8th increments and convert to decimal
        Amount: AmountSlider*10000,          // slider moves by 10,000 increment
        Years: YearsSlider,                  // slider moves in single year increments, no adjustment required
        AnnualPayments: 12 },                // number of payments per year
      With( { r: AnnualRate/AnnualPayments,  // interest rate
              P: Amount,                     // loan amount
              n: Years*AnnualPayments },     // number of payments
            r*P / (1 - (1+r)^-n)             // standard interest calculation
      )
)  
```

この例では、**With** 関数をネストして、[毎月の住宅ローン支払い](https://en.wikipedia.org/wiki/Mortgage_calculator#Monthly_payment_formula) の 2 層計算を作成します。  競合がない限り、すべての外部 **With** の名前付きの値は内部 **With** で使用できます。

スライダー コントロールは 1 ずつしか移動できないため、スライダーを分割または乗算して、効果的にカスタムの増分を作成します。  金利の場合、**RateSlider** は **Max** プロパティを**48** に設定され、1/8 パーセント ポイントの増分の場合は 8 で除算され、0.125% から 6% の範囲をカバーするパーセンテージから小数に変換するには 100 で除算されます。  ローン金額の場合、**AmountSlider** は **Max** プロパティを **60** に設定され、10,000 倍されて、10,000 から 600,000 の範囲をカバーします。

スライダーが移動し、新しいローンの支払いが表示されると、**With** が自動的に再計算されます。  変数は使用されず、スライダーコントロールの **OnChange** プロパティを使用する必要はありません。

このアプリを作成するための詳細な手順は次のとおりです。
1. 新しいアプリを作成します。
2. [**Slider** コントロール](../controls/control-slider.md) を追加して **RateSlider** という名前を付けます。  **Max** プロパティを 48 に設定します。
3. [**Label** コントロール](../controls/control-text-box.md) をスライダーコントロールの左側に追加します。  **Text** プロパティを **"金利:"** に設定します。
3. **Label** コントロール をスライダー コントロールの右側に追加します。  **Text** プロパティを数式 **RateSlider/8 & "&nbsp;%"** に設定します。
3. 別の **Slider** コントロールを追加して **AmountSlider** という名前を付けます。  **Max** プロパティを 60 に設定します。
3. **Label** コントロールをこのスライダー コントロールの左側に追加します。  **Text** プロパティを **"ローン金額:"** に設定します。 
3. **Label** コントロールをこのスライダー コントロールの右側に追加します。  **Text** プロパティを数式 **AmountSlider/8 * 10000** に設定します。
4. 別の **Slider** コントロールを追加して **YearsSlider** という名前を付けます。  **Max** プロパティを 40 に設定します。
3. **Label** コントロールをこのスライダー コントロールの左側に追加します。  **Text** プロパティを **"年数:"** に設定します。 
3. **Label** コントロールをこのスライダー コントロールの右側に追加します。  **Text** プロパティを数式 **YearsSlider** に設定します。
5. **Label** コントロールを追加し、その **Text** プロパティを上記の数式に設定します。
3. **Label** コントロールを最後の Label コントロールの左側に追加します。  **Text** プロパティを **"毎月の定期支払い:"** に設定します。  

### <a name="primary-key-returned-from-patch"></a>パッチから返された主キー

```powerapps-dot
With( Patch( Orders, Defaults( Orders ), { OrderStatus: "New" } ),
      ForAll( NewOrderDetails, 
              Patch( OrderDetails, Defaults( OrderDetails ), 
                     { Order: OrderID,          // from With's first argument, primary key of Patch result
                       Quantity: Quantity,      // from ForAll's NewOrderDetails table
                       ProductID: ProductID }   // from ForAll's NewOrderDetails table
              )
      )
)
```

この例では、レコードを SQL Server の**注文** テーブルに追加します。  次に、**Patch** 関数によって **OrderID** フィールドに返された受注の主キーを使用して、**OrderDetails** テーブルに関連レコードを作成します。  

### <a name="extracted-values-with-a-regular-expression"></a>正規表現で抽出された値

```powerapps-dot
With( 
    Match( "PT2H1M39S", "PT(?:(?<hours>\d+)H)?(?:(?<minutes>\d+)M)?(?:(?<seconds>\d+)S)?" ),
    Time( Value( hours ), Value( minutes ), Value( seconds ) )
)
// Result: 2:01 AM (as shown in a label control, use the Text function to see the seconds)
```

この例では、ISO 8601 期間値から時間、分、秒を抽出し、これらのサブマッチを使用して Date/Time 値を作成します。 

サブマッチには数字が含まれていますが、テキスト文字列のままです。  [**Value**](function-value.md) 関数を使用して、数学的操作を実行する前に数値に変換します。  

