---
title: SetFocus 関数 | Microsoft Docs
description: Power Apps での SetFocus 関数の構文を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 08/23/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 6347a76765fef433880754038d4e098fcb0fd6ee
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3304636"
---
# <a name="setfocus-function-in-power-apps"></a>Power Apps の SetFocus 関数
入力フォーカスを特定のコントロールに移動します。 

## <a name="description"></a>内容
**SetFocus** 関数によって、コントロールへの入力フォーカスが可能になります。  ユーザーのキーストロークがそのコントロールによって受信され、テキスト入力コントロールに入力するか、*入力*キーを押してボタンを選択できるようになります。  ユーザーは、*タブ* キー、タッチ、マウス、またはその他のジェスチャを使用して、入力フォーカス自体を移動することもできます。 *タブ* キーの動作は [**TabIndex** プロパティ](../controls/properties-accessibility.md)によって制御されます。

**SetFocus** 関数を使用してフォーカスを設定します (それぞれの例を以下に示します)。
- 新しく公開または有効化された入力コントロールで、次に来る情報をユーザーに提供し、データ入力が高速化します。
- フォームが検証され、問題のある入力コントロールに焦点を合わせて表示し、すばやく解決策を見出します。
- 画面が表示され、[**画面**](../controls/control-screen.md) の **OnVisible** プロパティを使用して最初の入力コントロールにフォーカスします。

フォーカスが設定されたコントロールは、[**FocusedBorderColor**](../controls/properties-color-border.md) プロパティと [**FocusedBorderThickness**](../controls/properties-color-border.md) プロパティに基づいて視覚的に異なる場合があります。

## <a name="limitations"></a>制限

**SetFocus** は次の場合にのみ使用できます。
- [**ボタン**](../controls/control-button.md) コントロール
- [**アイコン**](../controls/control-shapes-icons.md) コントロール
- [**イメージ**](../controls/control-image.md) コントロール
- [**ラベル**](../controls/control-text-box.md) コントロール
- [**TextInput**](../controls/control-text-input.md) コントロール

[**ギャラリー**](../controls/control-gallery.md) コントロール、[**編集フォーム**](../controls/control-form-detail.md) コントロール、または[コンポーネント](../create-component.md) 内のコントロールにフォーカスを設定することはできません。  **SetFocus** はスクロール可能な画面のコントロールで使用できます。

**SetFocus** 呼び出しを含む計算式と同じ画面のコントロールにのみフォーカスを設定できます。

[**DisplayMode**](../controls/properties-core.md) プロパティが **Disabled** に設定されているコントロールにフォーカスを設定しようとしても、効果はありません。  フォーカスは以前の状態のままになります。

Apple iOS では、**SetFocus** が直接ユーザー操作によって開始された場合のみ、ソフトキーボードが自動的に表示されます。  たとえば、ボタンの **OnSelect** プロパティから呼び出すと、ソフトキーボードが表示されますが、画面の **OnVisible** からの呼び出しは表示されません。 

**SetFocus** は、[動作の数式](../working-with-formulas-in-depth.md) でのみ使用できます。

## <a name="syntax"></a>構文
**SetFocus** (*コントロール*)

* *コントロール* – 必須。  入力フォーカスを付与するコントロール。

## <a name="examples"></a>例

### <a name="focus-on-a-newly-exposed-or-enabled-input-control"></a>新しく公開されたまたは有効になっている入力コントロールにフォーカスを設定する

多くのショッピング カートでは、顧客は配送先住所を請求先住所として使用して、同じ情報を 2 回入力する必要性を軽減することができます。  別の請求先住所が必要な場合は、請求先住所のテキスト入力ボックスを有効にして、データ入力を高速化するためにこれらの新しく有効になったコントロールを顧客に案内するのに役立ちます。  

![カスタムの請求先住所の使用を選択し、結果としてフォーカスが請求先名入力コントロールに移動して、配送先住所との自動同期がオフになるアニメーション](media/function-setfocus/shipping-billing.gif)

ここでは多くの数式が再生されますが、フォーカスを移動する計算式は、**チェック ボックス** コントロールの **OnUncheck** プロパティにあります。

```powerappa-dot
SetFocus( BillingName ) 
```

*タブ* キーを使用して、あるフィールドから別のフィールドにフォーカスをすばやく移動することもできます。  わかりやすく説明するために、*タブ* キーはアニメーションで使用しませんでした。

この例を作成するには、次のようにします。
1. 新しいアプリを作成します。
1. 「送付先住所」、「名前:」、「住所:」、「請求先住所」、「名前:」、「住所:」というテキストが付いた [**ラベル** コントロール](../controls/control-text-box.md) を追加して、アニメーションに示されているように配置します。
1. [**テキスト入力**コントロール](../controls/control-text-input.md)を追加し、その名前を **ShippingName** に変更します。
1. [**テキスト入力**コントロール](../controls/control-text-input.md) を追加し、その名前を **ShippingName** に変更します。
1. [**チェックボックス** コントロール](../controls/control-check-box.md) を追加し、名前を **SyncAddresses** に変更します。
1. このコントロールの **Text** プロパティを、`"Use Shipping address as Billing address"` 計算式に設定します。
1. [**テキスト入力**コントロール](../controls/control-text-input.md) を追加し、その名前を **BillingName** に変更します。
1. コントロールの **Default** プロパティを `ShippingName` 数式に設定します。
1. このコントロールの **DisplayMode** プロパティを `If( SyncAddresses.Value, DisplayMode.View, DisplayMode.Edit )` 数式に設定します。  これにより、チェック ボックス コントロールの状態に基づいて、このコントロールが自動的に有効または無効になります。
1. [**テキスト入力**コントロール](../controls/control-text-input.md)を追加し、その名前を **BillingAddress** に変更します。
1. このコントロールの **Default** プロパティを `ShippingAddress` 数式に設定します。
1. このコントロールの **DisplayMode** プロパティを `If( SyncAddresses.Value, DisplayMode.View, DisplayMode.Edit )` 数式に設定します。  これにより、チェック ボックス コントロールの状態に基づいて、このコントロールが自動的に有効または無効になります。
1. チェック ボックスの **Default** プロパティを `true` 式に設定します。  これにより、送付先住所と同じ値を使用する請求先住所が既定で使用されます。
1. チェック ボックスの **OnCheck** プロパティを `Reset( BillingName ); Reset( BillingAddress )` 計算式に設定します。  ユーザーが送付先住所と請求先住所の同期を選択した場合、請求先住所フィールドのユーザー入力がすべてクリアされ、それぞれの **Default** プロパティで対応する送付先住所フィールドから値を取得します。
1. チェック ボックスの **OnUncheck** プロパティを `SetFocus( BillingName )` 計算式に設定します。  ユーザーが別の請求先住所を選択した場合、請求先住所の最初のコントロールにフォーカスが移動します。  これらのコントロールは、**DisplayMode** プロパティによって既に有効になっています。

### <a name="focus-on-validation-issues"></a>検証の問題に焦点を当てる

> [!NOTE]
> この例は、**Edit form** コントロールのように見えますが、残念ながらこのコントロールでは **SetFocus** はまだサポートされていません。  代わりに、この例では、スクロール可能な画面を使用して入力コントロールをホストしています。

フォームを検証する際、問題が発生した場合だけでなく、問題が発生したフィールドにユーザーを移動する場合にもメッセージを表示すると役立ちます。  問題のフィールドが画面の外にスクロールされ、表示されない場合は、特に便利です。

![データ入力フォームを検証し、メッセージが表示されるだけでなく、画面からスクロールされていても、問題のある入力コントロールに入力フォーカスを設定するアニメーション。](media/function-setfocus/scrollable-screen.gif)

このアニメーションでは、すべてのフィールドが適切に入力されるまで、検証ボタンが繰り返し押されます。  マウス ポインターは画面の上部から下に移動しないことに注意してください。   代わりに **SetFocus** 関数は、次の数式で注意が必要なコントロールに入力フォーカスを移動しました。

```powerapps-dot
If( IsBlank( Name ), 
        Notify( "Name requires a value", Error ); SetFocus( Name ),
    IsBlank( Street1 ), 
        Notify( "Street Address 1 requires a value", Error ); SetFocus( Street1 ),
    IsBlank( Street2 ), 
        Notify( "Street Address 2 requires a value", Error ); SetFocus( Street2 ),
    IsBlank( City ), 
        Notify( "City requires a value", Error ); SetFocus( City ),
    IsBlank( County ), 
        Notify( "County requires a value", Error ); SetFocus( County ),
    IsBlank( StateProvince ), 
        Notify( "State or Province requires a value", Error ); SetFocus( StateProvince ),
    IsBlank( PostalCode ), 
        Notify( "Postal Code requires a value", Error ); SetFocus( PostalCode ),
    IsBlank( Phone ), 
        Notify( "Contact Phone requires a value", Error ); SetFocus( Phone ),
    Notify( "Form is Complete", Success )
)
```

この例を作成するには、次のようにします。
1. 新しい、空の電話アプリを作成します。
1. **挿入**メニューの**新しい画面**を選択し、次に**スクロール可能**を選択します。
1. 画面の中央セクションで、**テキスト入力**コントロールを追加し、**名前**、**番地 1**、**番地 2**、**市区町村**、**郡**、**州**、**郵便番号**、**電話番号**を入力します。 各フィールドに**ラベル** コントロールを追加して、フィールドを識別します。  すべてのコントロールを収めるのに十分な長さでない場合は、セクションのサイズを変更することが必要になる場合があります。
1. スクロール可能なセクションの上のチェックマーク [**アイコン** コントロール](../controls/control-shapes-icons.md) を画面の上部に追加します。  
1. アイコン コントロールの **OnSelect** プロパティを、上記で指定した `If( IsBlank( ...` の数式に設定します。

### <a name="focus-when-displaying-a-screen"></a>画面を表示する時にフォーカスを移動する

> [!NOTE]
> この例は、**Edit form** コントロールのように見えますが、残念ながらこのコントロールでは **SetFocus** はまだサポートされていません。  代わりに、この例では、スクロール可能な画面を使用して入力コントロールをホストしています。

入力コントロールを公開する場合と同様に、データ入力画面を表示する場合は、データ入力の速度を上げるために最初の入力コントロールに集中すると便利です。

![データ入力画面を表示する場合に SetFocus を使用するおよび SetFpcus を使用しないを並べて比較したアニメーション](media/function-setfocus/visible-setfocus.gif)

このアニメーションでは、左側のデータ入力画面には **SetFocus** が使用されていません。  表示時に、フォーカスのある入力コントロールはありません。ユーザーはタブ、タッチ、マウスを使用するか、あるいは他の方法で**名前**フィールドにフォーカスを設定してから、値を入力する必要があります。

右側には、次の数式に設定されたデータ入力画面の **OnVisible** プロパティとまったく同じアプリがあります。

```powerapps-dot
SetFocus( Name )
```

これにより、フォーカスが**名前**フィールドに自動的に設定されます。  ユーザーは、事前の操作を必要とせずに、フィールド間の入力とタブ移動をすぐに開始できます。

この例を作成するには、次のようにします。
1. 上記の「検証の問題に焦点を当てる」アプリを作成します。
1. この画面で、**OnVisible** プロパティを `SetFocus( Name )` 数式に設定します。
1. 2 番目の画面を追加します。
1. [**ボタン** コントロール](../controls/control-button.md) を追加します。
1. このコントロールの **OnSelect** プロパティを `Navigate( Screen1 )` 数式に設定します。
1. この画面からアプリをプレビューします。  ボタンを押します。  **OnVisible** 式が評価され、**名前**フィールドが自動的にフォーカスされます。
