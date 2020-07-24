---
title: Remove および RemoveIf 関数 | Microsoft Docs
description: Power Apps での Remove および RemoveIf 関数の構文と例を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/04/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f6674c112749758ecbaeab8c86727b4685615ef1
ms.sourcegitcommit: 0c92e85f95f3baa04cce140c96e53d5d86d685c0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "3333458"
---
# <a name="remove-and-removeif-functions-in-power-apps"></a>Power Apps の Remove および RemoveIf 関数
[データ ソース](../working-with-data-sources.md) から [レコード](../working-with-tables.md#records) を削除します。

## <a name="description"></a>内容
### <a name="remove-function"></a>Remove 関数
**Remove** 関数を使用して、1 つまたは複数の特定のレコードをデータ ソースから削除します。  

[コレクション](../working-with-data-sources.md#collections) の場合には、レコード全体が一致している必要があります。 レコードのコピーすべてを削除する場合には、**All** 引数を使用します。この引数を使用しなかった場合には、レコードのコピーが 1 つだけ削除されます。

### <a name="removeif-function"></a>RemoveIf 関数
**RemoveIf** 関数を使用して、1 つの条件または一連の条件に基づき、1 つまたは複数のレコードを削除します。 各条件について、結果が **true** または **false** になるものであれば、どのような数式でも指定できます。また、データ ソースの [列](../working-with-tables.md#columns) を、名前を使って参照することもできます。 各条件はレコードごとに個別に評価され、すべての条件が **true** と評価された場合にそのレコードが削除されます。

**Remove** と **RemoveIf** は、変更後のデータ ソースを [テーブル](../working-with-tables.md) として返します。 これらの関数は、いずれも [動作の数式](../working-with-formulas-in-depth.md) 内でのみ使用できます。

また、**[Clear](function-clear-collect-clearcollect.md)** 関数を使用して、コレクションのすべてのレコードを削除することもできます。

### <a name="delegation"></a>委任
[!INCLUDE [delegation-no](../../../includes/delegation-no.md)]

## <a name="syntax"></a>構文
**Remove**( *DataSource*, *Record1* [, *Record2*, ... ] [, **All** ] )

* *DataSource* – 必須。 削除の対象となるレコードが含まれるデータ ソース。
* *Record(s)* – 必須。 削除する 1 つまたは複数のレコード。
* **All** – オプション。 コレクションでは、同じレコードが複数存在することがあります。  レコードのコピーをすべて削除するために、**All** 引数を追加できます。

**Remove**( *DataSource*, *Table* [, **All** ] )

* *DataSource* – 必須。 削除の対象となるレコードが含まれるデータ ソース。
* *Table* – 必須。 削除するレコードのテーブル。
* **All** – オプション。 コレクションでは、同じレコードが複数存在することがあります。  レコードのコピーをすべて削除するために、**All** 引数を追加できます。

**RemoveIf**( *DataSource*, *Condition* [, ... ] )

* *DataSource* – 必須。 削除の対象となるレコードが含まれるデータ ソース。
* *Condition(s)* – 必須。 削除の対象とするレコードについて評価結果が **true** となる数式。  数式では、*DataSource* の列名を使用できます。  複数の *Condition* を指定する場合、削除の対象とするレコードについて、評価結果がすべて **true** となる必要があります。

## <a name="examples---single-formulas"></a>例 - 単一の数式

ここで紹介する例では、**IceCream** という名前のデータ ソースの 1 つ以上のレコードを削除します。このデータ ソースは次のテーブルのデータから始まります。

![](media/function-remove-removeif/icecream.png)

#### <a name="create-a-collection-with-sample-records"></a>サンプル レコードを含むコレクションを作成する

このデータでコレクションを作成します。

1. [**Button**](../controls/control-button.md) コントロールを挿入します。
1. ボタン コントロールの **OnSelect** プロパティを次の式に設定します。

    ```powerapps-dot
    ClearCollect( IceCream,
                  { ID: 1, Flavor: "Chocolate",  Quantity: 100 },
                  { ID: 2, Flavor: "Vanilla",    Quantity: 200 },
                  { ID: 3, Flavor: "Strawberry", Quantity: 300 }
    )
    ```
1. [Alt キーを押しながら](../keyboard-shortcuts.md#alternate-behavior)、ボタンを選択します。


#### <a name="remove-sample-records-from-collection-using-a-formula"></a>数式を使用してコレクションからサンプル レコードを削除する

| 計算式 | 内容 | 結果 |
| --- | --- | --- |
| **Remove(&nbsp;IceCream,<br>First(&nbsp;Filter(&nbsp;IceCream,&nbsp;Flavor="Chocolate"&nbsp;)&nbsp;) )** |データ ソースの **Chocolate** レコードを削除します。 |<style> img {最大幅: なし} </style> ![](media/function-remove-removeif/icecream-no-chocolate.png)<br><br>**IceCream** データ ソースの内容が変更されました。 |
| **Remove(&nbsp;IceCream,<br>First(&nbsp;Filter(&nbsp;IceCream,&nbsp;Flavor="Chocolate"&nbsp;)&nbsp;) First(&nbsp;Filter(&nbsp;IceCream,&nbsp;Flavor="Strawberry"&nbsp;)&nbsp;) )** |データ ソースから 2 つのレコードを削除します。 |![](media/function-remove-removeif/icecream-only-vanilla.png)<br><br>**IceCream** データ ソースの内容が変更されました。 |
| **RemoveIf(&nbsp;IceCream, Quantity&nbsp;>&nbsp;150 )** |**Quantity** の値が **150** よりも大きいレコードを対象として削除を実行します。 |![](media/function-remove-removeif/icecream-only-chocolate.png)<br><br>**IceCream** データ ソースの内容が変更されました。 |
| **RemoveIf(&nbsp;IceCream, Quantity&nbsp;>&nbsp;150, Left(&nbsp;Flavor,&nbsp;1&nbsp;) = "S" )** |**Quantity** の値が 150 よりも大きく、**Flavor** が **S** で始まるレコードを対象として削除を実行します。 |![](media/function-remove-removeif/icecream-no-strawberry.png)<br><br><br>**IceCream** データ ソースの内容が変更されました。 |
| **RemoveIf(&nbsp;IceCream, true )** |データ ソースからすべてのレコードを削除します。 |![](media/function-remove-removeif/icecream-empty.png)<br><br>**IceCream** データ ソースの内容が変更されました。 |

## <a name="examples---remove-button-outside-a-gallery"></a>例 - ギャラリーの外のボタンを削除する

この例では、[**ギャラリー** コントロール](../controls/control-gallery.md) を使用してテーブル内のレコードを一覧表示します。 次に、**Remove** 関数を使用して、アイテムを選択して削除します。  

### <a name="prepare-for-sample-data"></a>サンプル データの準備

この例では、*サンプル アプリとデータ*で使用可能な Common Data Service の**取引先担当者**エンティティを使用します。 [環境を作成する](https://docs.microsoft.com/power-platform/admin/create-environment#create-an-environment-with-a-database) とき、*サンプル アプリおよびデータ*を展開できます。 代わりに、その他のデータ ソースを使用することもできます。

### <a name="remove-button-outside-a-gallery"></a>ギャラリーの外のボタンを削除する

この例では、ギャラリーの外の*ボタン*を使用してアイテムを削除します。

1. 電話レイアウトを使用して、[新しい空白のキャンバス アプリ](../data-platform-create-app-scratch.md) を作成します。

    ![電話レイアウトを使用して、新しい空白のキャンバス アプリを作成する](media/function-remove-removeif/gallery-new.png)

1. 左側のウィンドウから、**挿入**を選択します。

1. **垂直ギャラリー**を選択します。 <br>
    **ギャラリー** コントロールが画面に追加されます。

    ![挿入ツール ウィンドウを使用して、垂直ギャラリー コントロールを追加する](media/function-remove-removeif/gallery-add.png)

1. 使用可能なデータ ソースからデータ ソースを選択できるデータ ソースを選択するよう要求されます。 <br>
    たとえば、**取引先担当者**エンティティを選択して、*サンプル データ*を使用します。  

    ![ギャラリーに表示する取引先担当者エンティティを選択する](media/function-remove-removeif/gallery-datasource.png)

    ギャラリーには、このエンティティからアイテムが表示されます。 

    ![取引先担当者エンティティを表示するギャラリーが追加されました](media/function-remove-removeif/gallery-data.png)

1. 左側のウィンドウから [**ボタン**](../controls/control-button.md) コントロールを挿入します。
    
    ![挿入ツール ウィンドウを使用して、ボタン コントロールを追加する](media/function-remove-removeif/gallery-addbutton.png)

1. 追加されたボタンをギャラリー アイテムの下に移動します。

    ![ボタンの移動](media/function-remove-removeif/move-button-down.png)

1. ボタンのテキスト プロパティを*レコードを削除*に更新します。 使用したいテキストを使用することもできます。

    ![ボタンの名前を変更する](media/function-remove-removeif/button-text.png)

1. このボタン コントロールの **OnSelect** プロパティを次の式に設定します。

    ```powerapps-dot
    Remove( Contacts, Gallery1.Selected )
    ```

    ![ボタン コントロールの OnSelect プロパティを設定する](media/function-remove-removeif/gallery-button-onselect.png)

    ギャラリー コントロールにより、**Selected** プロパティを使用し、現在選択されているレコードが使用可能になります。 **Remove** 関数はこの選択されたレコードを参照し、削除します。

1. 右上の *Play* ボタンを使用するか、またはキーボードの *F5* キーを押して、アプリをプレビューします。

    ![アプリのプレビュー](media/function-remove-removeif/preview-app.png)

1. この例の *Nancy* のレコードなど、 削除するレコードを選択します。

    ![レコードの選択](media/function-remove-removeif/select-nancy-record.png)

1. **レコードの削除**を選択します。

    ![削除された Nancy レコードがない取引先担当者のギャラリー](media/function-remove-removeif/gallery-activatebutton.png)

    ボタンを選択すると、選択したレコードが削除されます (この例では、Nancy のレコード)。

1. アプリのプレビューを閉じます。

    > [!TIP]
    > *Play* ボタンまたは *F5* キーを使用してアプリのプレビューを使用する代わりに、[*Alt キー*](../keyboard-shortcuts.md#alternate-behavior) を使用して、代替動作を使用することもできます。

## <a name="examples---trash-can-icon-inside-a-gallery"></a>例 - ギャラリー内のごみ箱のアイコン

この例では、ギャラリー内に配置された*アイコン*を使用してアイテムを削除します。

### <a name="create-a-collection-with-sample-data"></a>サンプル データを含むコレクションを作成する

既に [サンプル データを準備](#prepare-for-sample-data) している場合、この手順をスキップして、[ギャラリー内のごみ箱のアイコン](#trash-can-icon-inside-a-gallery) に移動します。

1. 画面に [**ボタン**](../controls/control-button.md) コントロールを追加します。
1. **OnSelect** プロパティを次の式に設定します。

    ```powerapps-dot
    ClearCollect( SampleContacts, 
          { 'Full Name': "Yvonne McKay (sample)",      'Primary Email': "someone_a@example.com" },
          { 'Full Name': "Susanna Stubberod (sample)", 'Primary Email': "someone_b@example.com" },
          { 'Full Name': "Nancy Anderson (sample)",    'Primary Email': "someone_c@example.com" },
          { 'Full Name': "Maria Campbell (sample)",    'Primary Email': "someone_d@example.com" },
          { 'Full Name': "Robert Lyon (sample)",       'Primary Email': "someone_e@example.com" },
          { 'Full Name': "Paul Cannon (sample)",       'Primary Email': "someone_f@example.com" },
          { 'Full Name': "Rene Valdes (sample)",       'Primary Email': "someone_g@example.com" } 
    )
    ```
1. [Alt キーを押しながら](../keyboard-shortcuts.md#alternate-behavior)、ボタンを選択します。

次の例で使用できるサンプル コレクションが作成されます。

### <a name="trash-can-icon-inside-a-gallery"></a>ギャラリー内のごみ箱のアイコン

1. 電話レイアウトを使用して、[新しい空白のキャンバス アプリ](../data-platform-create-app-scratch.md) を作成します。

    ![電話レイアウトを使用して、新しい空白のキャンバス アプリを作成する](media/function-remove-removeif/gallery-new.png)

1. 左側のウィンドウから、**挿入**を選択します。

1. **垂直ギャラリー**を選択します。 <br>
    **ギャラリー** コントロールが画面に追加されます。

    ![挿入ツール ウィンドウを使用して、垂直ギャラリー コントロールを追加する](media/function-remove-removeif/gallery-add.png)

1. 使用可能なデータ ソースからデータ ソースを選択できるデータ ソースを選択するよう要求されます。 <br>
    たとえば、**取引先担当者**エンティティを選択して、*サンプル データ*を使用します。  

    ![ギャラリーに表示する取引先担当者エンティティを選択する](media/function-remove-removeif/gallery-datasource.png)

    [コレクション](#create-a-collection-with-sample-data) を作成した場合、代わりにコレクションを選択してください。

    ![取引先担当者のサンプル コレクション](media/function-remove-removeif/sample-contacts.png)

1. ギャラリーの最初のアイテム内でコントロールを選択します。 <br>
    
    次の手順でアイテムがギャラリーのテンプレート外ではなく、ギャラリーのテンプレート内に挿入されるようにするには、次に進む前にこの手順に従ってください。
    
    ![ギャラリーの先頭レコードを選択する](media/function-remove-removeif/gallery-select-template.png)

1. 左側のウィンドウから**アイコンの追加**を選択します。 <br>
    
    ![挿入ツール ウィンドウを使用して、アイコン コントロールを追加する](media/function-remove-removeif/gallery-addicon.png)

    > [!NOTE]
    > **アイコンの追加**により、ギャラリーの左側に **+** を挿入すると、ギャラリー内の各アイテムごとに複製されます。 

1. 最初のアイテムにおいて、アイコンを画面の右側に移動します。

    ![アイコンの移動](media/function-remove-removeif/move-icon.png)

1. アイコンの **Icon** プロパティを選択し、次の式に設定して、アイコン画像をごみ箱アイコンとして更新します。

    ```powerapps-dot 
    Icon.Trash
    ```
    
    > [!NOTE]
    > **アイコン。** 接頭辞は、数式をアクティブに編集しているときにのみ表示されます。

    ![アイコンをごみ箱アイコンに変更する](media/function-remove-removeif/gallery-icontrash.png)

1. **OnSelect** プロパティを次の式に設定します。

    ```powerapps-dot
    Remove( [@Contacts], ThisItem )
    ```

    > [!NOTE]
    > *取引先担当者*エンティティを使用するサンプル データのあるこの例では、[グローバル曖昧性除去演算子](operators.md#disambiguation-operator) **[@**...**]** を使用し、*一対多*の関連付けとの競合を回避する必要があります。 SharePoint のリストまたは SQL Server などのデータ ソースを使用する場合、*グローバル曖昧性除去演算子*の使用は必須ではありません。

    ![ごみ箱アイコンに対する OnSelect](media/function-remove-removeif/gallery-onselect.png)

1. 右上の *Play* ボタンを使用するか、またはキーボードの *F5* キーを押して、アプリをプレビューします。

1. たとえば、*Maria* のように、レコードの横にあるごみ箱アイコンを選択します。

    ![取引先担当者の 1 つが削除されたギャラリー](media/function-remove-removeif/gallery-activateicon.png)

    レコードは削除されました。

    ![削除されたレコード](media/function-remove-removeif/deleted-record.png)

1. アプリのプレビューを閉じます。
