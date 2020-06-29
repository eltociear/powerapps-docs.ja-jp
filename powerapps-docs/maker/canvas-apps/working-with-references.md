---
title: レコード参照とポリモーフィック検索について | Microsoft Docs
description: キャンバス アプリでレコード参照とポリモーフィック検索を操作する
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 09/14/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f44d28ab57bb012f1cb4a847920a4cf0597e3b68
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2019
ms.locfileid: "3304015"
---
# <a name="understand-record-references-and-polymorphic-lookups-in-canvas-apps"></a>キャンバス アプリでのレコード参照とポリモーフィック検索について

学校で研究論文を書いたとき、おそらく最後に参考文献の一覧を提供したことでしょう。 使用した実際の背景資料のコピーではなく、Web リンク、本のタイトルと著者、またはその他の情報を含めて、他の誰かが元のソースを追跡できるようにしました。 さまざまな種類の情報源を単一のリストに合わせ、オーディオ録音の横に新聞記事があり、それぞれに適切な引用向けの固有の詳細情報があります。 たとえば、Wikipedia の記事には多くの場合、[参照の長いリスト](https://en.wikipedia.org/wiki/Microsoft#References)が含まれます。

キャンバス アプリでは、多くの場合データ ソースからダウンロードしたレコードのコピーを使用します。 [**LookUp**](functions/function-filter-lookup.md) および [**Filter**](functions/function-filter-lookup.md) 関数や [**Gallery**](controls/control-gallery.md) コントロールの **Selected** プロパティを使用して、必要な特定のレコードを識別します。 **Filter** または **Selected** からのすべてのレコードは同じエンティティの種類になるため、単純な .*Field* 表記のフィールドを使用できます。 多くの場合これらのコピーには参照情報が含まれているため、[**Patch**](functions/function-patch.md) 関数を使用して元のソースを更新します。

キャンバス アプリも*レコード参照*をサポートします。 研究論文の参照と同様に、レコード参照はレコードの完全なコピーを含まないものを指します。 このような参照は、任意のエンティティのレコードを参照できます。 また、研究論文の参考文献と同様に、異なるエンティティからのレコードを単一の列に混在できます。

レコード参照の多くの操作は、レコードの操作と同じです。 レコード参照を相互に比較したり、完全なレコードと比較したりできます。 完全なレコードを備えたルックアップと同じように、レコード参照の値を **Patch** 関数で設定できます。

重要な使用方法の違いが 1 つあります: レコード参照のフィールドに直接アクセスするには、それが参照するエンティティを最初に確立する必要があります。 これは、キャンバス アプリでは、数式を記述するときにすべての種類を認識している必要があるためです。 アプリが実行されるまでレコード参照の種類を認識しないと、単純な .*Field* 表記を直接使用することはできません。 まず、[**IsType**](functions/function-astype-istype.md) 関数を使用してからを使用してエンティティの種類を動的に決定してから、[**AsType**](functions/function-astype-istype.md) 関数の結果で .*Field* 表記を使用する必要があります。

*エンティティの種類*は、エンティティの各レコードのスキーマを指します。 各エンティティには、異なる名前とデータ型を備えた一連のフィールドがあります。 エンティティの各レコードはその構造を継承します; 2 つのレコードが同じエンティティからのものである場合、それらには同じエンティティの種類があります。

## <a name="polymorphic-lookups"></a>ポリモーフィック検索

Common Data Service はレコード間の関連付けをサポートします。 **取引先企業**エンティティの各レコードには、**取引先担当者**エンティティのレコードへの**取引先責任者**検索フィールドがあります。 検索は**取引先担当者**のレコードのみを参照できますが、たとえば**チーム** エンティティのレコードを参照することはできません。 検索に使用できるフィールドを常に認識しているため、この最後の詳細は重要です。

Common Data Service では、セット内の任意のエンティティからのレコードを参照できるポリモーフィック検索もサポートしています。 たとえば、**所有者**フィールドは、**ユーザー** エンティティまたは**チーム** エンティティのレコードを参照できます。 異なるレコードの同じ検索フィールドは、異なるエンティティのレコードを参照できます。 この場合、使用できるフィールドを常に認識しているとは限りません。

キャンバス レコード参照は、Common Data Service でポリモーフィック検索を操作するために設計されました。 また、このコンテキスト以外でもレコード参照を使用することもができます。これが 2 つの概念の違いです。

次のセクションでは、**所有者**検索で作業することにより、これらの概念について調べ始めます。

## <a name="show-the-fields-of-a-record-owner"></a>レコード所有者のフィールドを表示する

Common Data Service のすべてのエンティティには**所有者**フィールドが含まれます。 このフィールドは削除できず、別のフィールドを追加することもできません。それには常に値が必要です。

**取引先企業**エンティティでそのフィールドを表示するには:

1. [この Power Apps サイト](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)を開きます。
1. 左側のナビゲーション バーで、**データ** > **エンティティ**を選択します。
1. エンティティの一覧で、**取引先企業**を選択します。
1. 右上隅で、フィルターの一覧 (既定で**既定**に設定される) を開いてから、**すべて**を選択します。
1. **所有者**フィールドが表示されるまで下にスクロールします。

 > [!div class="mx-imgBorder"]
 > ![取引先企業エンティティの所有者フィールド](media/working-with-references/owner-field.png)

この検索フィールドは、**チーム** エンティティまたは**ユーザー** エンティティのいずれかからのレコードを参照できます。 これらのエンティティのすべてのレコードに**所有者**へのアクセス許可があるわけではありません; 問題が発生した場合は、サポートされているロールを確認してください。

この図は、**取引先企業**エンティティがデータ ソースとしてアプリに追加された、**取引先企業**の簡単なギャラリーを示します。

> [!div class="mx-imgBorder"]
> ![Gallery コントロールに表示される取引先企業](media/working-with-references/accounts-gallery.png)

> [!IMPORTANT]
> このトピック全体にわたって、図には Common Data Service に付属するサンプルデータの一部ではない名前やその他の値が表示されます。 この手順では、特定の結果に対するコントロールの構成方法を正確に示しますが、エクスペリエンスは組織のデータに基づいて異なります。

ギャラリーで各取引先企業の所有者を表示するため、数式 **ThisItem.Owner.Name** を使用する場合があるかもしれません。 ただし、**チーム** エンティティの名前フィールドが**チーム名**になり、**ユーザー** エンティティの名前フィールドが**氏名**になります。 アプリを実行するまで、アプリがどの種類の検索を使用しているかを認識せず、**取引先企業**エンティティのレコード間によって異なります。

この差異に適応できる数式が必要です。 **所有者**がなり得るエンティティの種類のデータ ソースも追加する必要があります (この場合、**ユーザー**と**チーム**)。 次の 3 つのデータ ソースをアプリに追加します:

> [!div class="mx-imgBorder"]
> ![データ ウィンドウの取引先企業、チーム、およびユーザー エンティティ](media/working-with-references/accounts-datasources.png)

これらのデータ ソースを配置して、次の数式を使用してユーザーまたはチームの名前のいずれかを表示します:

```powerapps-dot
If( IsType( ThisItem.Owner, [@Teams] ),
    "Team: " & AsType( ThisItem.Owner, [@Teams] ).'Team Name',
    "User: " & AsType( ThisItem.Owner, [@Users] ).'Full Name' )
```

> [!div class="mx-imgBorder"]
> ![表示された所有者フィールドで Gallery コントロールに表示されるアカウント](media/working-with-references/accounts-displayowner.png)

この数式では、**IsType** 関数は、**チーム** エンティティに対する**所有者**フィールドをテストします。 そのエンティティの種類の場合、**AsType** 関数はそれを**チーム** レコードにキャストします。 この時点では、*.Field* 表記を使用することにより、**チーム名**を含む、**チーム** エンティティのすべてのフィールドにアクセスできます。 **所有者**が**チーム** エンティティのレコードではないことを **IsType** が判別する場合、**所有者**フィールドは必須であるため (*空白*ではない)、そのフィールドは**ユーザー** エンティティのレコードである必要があります。

**[@Teams]** および **[@Users]** の[グローバル曖昧性除去演算子](functions/operators.md#disambiguation-operator)を使用して、グローバル エンティティの種類を使用していることを確認します。 この場合は必要ありませんが、良い習慣ともなります。 一対多のリレーションシップは、ギャラリーのレコード スコープで競合することがよくありますが、この操作を行うことで混乱を回避できます。

レコード参照の任意のフィールドを使用するには、最初に特定のエンティティの種類にキャストする **AsType** 関数を使用する必要があります。 使用するエンティティの種類がシステムで認識されていないため、**所有者**フィールドから直接フィールドにアクセスすることはできません。

**所有者**フィールドがリクエストされているエンティティの種類と一致しない場合、**AsType** 関数がエラーを返すため、**IfError** 関数を使用してこの数式を簡略化できます。 まず、試験的な機能**数式レベルのエラー管理**を有効にします:

> [!div class="mx-imgBorder"]
> ![数式レベルのエラー管理を有効にするよう試験的に切り替える](media/working-with-references/accounts-iferror.png)

次に、前の数式を次の式に置き換えます:

```powerapps-dot
IfError(
    "Team: " & AsType( ThisItem.Owner, [@Teams] ).'Team Name',
    "User: " & AsType( ThisItem.Owner, [@Users] ).'Full Name' )
```

## <a name="filter-based-on-an-owner"></a>所有者に基づいてフィルター処理する

これで、レコード参照の作業で最も難しい部分を完了しました。 その他の使用事例は、レコードのフィールドにアクセスしないため、より簡単になります。 この時点で、このセクションで説明するフィルター処理を行います。

ギャラリーの上に **Combo box** コントロールを追加し、新しいコントロールの次のプロパティを設定します:

- **Items**: `Users`
- **SelectMultiple**: `false`

> [!div class="mx-imgBorder"]
> ![Items プロパティをユーザーに設定して、ギャラリーの上に追加したコンボ ボックス コントロール](media/working-with-references/filter-insert-combobox.png)

このコンボ ボックスから選択した特定のユーザーによりギャラリーをフィルター処理するには、ギャラリーの **Items** プロパティをこの数式に設定します:

```powerapps-dot
Filter( Accounts, Owner = ComboBox1.Selected )
```

> [!div class="mx-imgBorder"]
> ![コンボ ボックス コントロールで設定された値に基づいてフィルター処理されたギャラリー](media/working-with-references/filter-accounts.png)

> [!IMPORTANT]
> このトピックの手順は、手順を正確に実行すれば正確です。 ただし、コントロール名が異なる場合、その名前でコントロールを参照する任意の数式は失敗します。 同じ種類のコントロールを削除して追加する場合、コントロールの名前の最後にある番号が変わります。 エラーを示す任意の数式については、すべてのコントロールの正しい名前が含まれていることを確認してください。

レコード参照を他のレコード参照または完全なレコードと比較しているため、**IsType** または **AsType**を使用する必要はありません。 アプリは **ComboBox1.Selected** のエンティティの種類を認識します。それが**ユーザー** エンティティから派生しているためです。 所有者がチームである取引先企業は、フィルター条件と一致しません。

ユーザーまたはチームのいずれかによるフィルタリングをサポートすることにより、少し手の込んだものを取得できます。

1. ギャラリーをサイズ変更してコンボ ボックスを移動することにより、画面の上部にスペースを作り、[**Radio** コントロール](controls/control-radio.md)をギャラリーの上に挿入してから、次のプロパティを新しいコントロールに設定します:

    - **Items**: `[ "All", "Users", "Teams" ]`
    - **Layout**: `Layout.Horizontal`

1. **Combo box** コントロールについては、次のプロパティを設定します (コンボ ボックスが表示されない場合は、ラジオ コントロールの**ユーザー**を選択します):

    - **Visible**: `Radio1.Selected.Value = "Users"`

1. **Combo box** コントロールをコピーして貼り付け、コピーをオリジナルの上に直接移動してから、コピーに対する次のプロパティを設定します:

    - **Items**: `Teams`
    - **Visible**: `Radio1.Selected.Value = "Teams"`

    アプリは、ラジオ コントロールの状態に応じて、一度に 1 つのコンボ ボックスのみを表示します。 これらは互いに直接上部にあるため、内容を変更するコントロールと同じように表示されます。

1. 最後に、**Gallery** コントロールの **Items** プロパティを次の数式に設定します:

    ```powerapps-dot
    Filter( Accounts,
        Radio1.Selected.Value = "All"
        Or (Radio1.Selected.Value = "Users" And Owner = ComboBox1.Selected)
        Or (Radio1.Selected.Value = "Teams" And Owner = ComboBox1_1.Selected)
    )
    ```

    > [!div class="mx-imgBorder"]
    > ![すべてのレコードまたは特定のユーザーやチームを表示しているフィルター処理されたギャラリー](media/working-with-references/filter-combobox.png)

これらの変更により、すべてのレコードを表示したり、ユーザーまたはチームのいずれかに基づいてそれらをフィルター処理できます。

> [!div class="mx-imgBorder"]
> ![ラジオ コントロールとコンボ ボックスに基づいて異なるフィルター処理された結果を示しているアニメーション](media/working-with-references/filter-allthree.gif)

数式は完全に委任可能です。 ラジオ ボタンの値を比較する部分はすべてのレコード間で一定であり、フィルターの残りの部分が Common Data Service に送信される前に評価されます。

所有者の種類でフィルター処理する場合は、**IsType** 関数を使用できますが、まだ委任可能ではありません。

> [!div class="mx-imgBorder"]
> ![IsType を使用して所有者の種類でフィルター処理する](media/working-with-references/filter-bytype.png)

## <a name="update-the-owner-by-using-patch"></a>Patch を使用して所有者を更新する

他の検索と同じ方法で**所有者**フィールドを更新できます。 現在選択されている取引先企業の所有者を最初のチームに設定するには:

```powerapps-dot
Patch( Accounts, Gallery1.Selected, { Owner: First( Teams ) } )
```

アプリは **First( Teams )** の種類を認識するため、このアプローチは通常の検索と変わりません。 代わりに最初のユーザーが必要な場合は、その部分を **First( Users )** に置き換えます。 **Patch** 関数は、**所有者**フィールドがこれら 2 つのエンティティの種類のいずれかに設定できることを認識します。

この機能をアプリに追加するには:

1. **ツリー ビュー** ウィンドウで、**Radio** コントロールと 2 つの **Combo box** コントロールを同時に選択します。

1. 省略記号メニューで、**これらの項目をコピーする**を選択します。

    > [!div class="mx-imgBorder"]
    > ![ツリー ビューを使用している複数のコントロールのコピー](media/working-with-references/patch-copy.png)

1. 同じメニューで、**貼り付け**を選択します。

    > [!div class="mx-imgBorder"]
    > ![ツリー ビューを使用している複数のコントロールの貼り付け](media/working-with-references/patch-paste.png)

1. コピーしたコントロールをギャラリーの右側に移動します。

    > [!div class="mx-imgBorder"]
    > ![ギャラリーの右側に移動したコピーされたコントロール](media/working-with-references/patch-position.png)

1. コピーした **Radio** コントロールを選択してから、次のプロパティを変更します:

    - Items: `[ "Users", "Teams" ]`
    - 既定値: `If( IsType( Gallery1.Selected.Owner, Users ), "Users", "Teams" )`

    > [!div class="mx-imgBorder"]
    > ![ラジオ コントロールから削除されたすべての選択肢](media/working-with-references/patch-noall.png) 

1. **Radio** コントロールで**ユーザー**を選択して、ユーザーを一覧表示する **Combo box** コントロールが表示されるようにします。

1. 表示される **Combo box** コントロールを選択してから、**DefaultSelectedItems** プロパティを次の式に設定します:

    ```powerapps-dot
    If( IsType( Gallery1.Selected.Owner, Users ),
        AsType( Gallery1.Selected.Owner, Users ),
        Blank()
    )
    ```

    > [!div class="mx-imgBorder"]
    > ![ユーザー コンボ ボックスに対する既定のプロパティ セット](media/working-with-references/patch-default-users.png)

1. **Radio** コントロールで**チーム**を選択して、チームを一覧表示する **Combo box** コントロールが表示されるようにします。

1. **Radio** コントロールを選択して、ユーザーに非表示の **Combo box** コントロールから選択肢を取り除きます。

1. 表示されるチーム用 **Combo box** コントロールを選択してから、その **DefaultSelectedItems** プロパティを次の式に設定します:

    ```powerapps-dot
    If( IsType( Gallery1.Selected.Owner, Teams ),
        AsType( Gallery1.Selected.Owner, Teams ),
        Blank()
    )
    ```

    > [!div class="mx-imgBorder"]
    > ![チーム コンボ ボックスに対する既定のプロパティ セット](media/working-with-references/patch-default-teams.png)

1. **Button** コントロールを挿入し、**Combo box** コントロールの下に移動してから、ボタンの **Text** プロパティを `"Patch Owner"` に設定します。

1. ボタンの **OnSelect** プロパティを次の数式に設定します:

    ```powerapps-dot
    Patch( Accounts, Gallery1.Selected,
        { Owner: If( Radio1_1.Selected.Value = "Users",
                ComboBox1_2.Selected,
                ComboBox1_3.Selected ) } )
    ```

    > [!div class="mx-imgBorder"]
    > ![Button コントロールの数式セット](media/working-with-references/patch-button.png)

コピーされた **Radio** および **Combo box** コントロールには、ギャラリーで現在選択されている取引先企業の所有者が表示されます。 同じコントロールを使用して、ボタンを選択することにより、取引先企業の所有者を任意のチームまたはユーザーに設定できます:

> [!div class="mx-imgBorder"]
> ![ユーザーまたはチームいずれかの所有者のパッチを示すアニメーション](media/working-with-references/patch-allthree.gif)

## <a name="show-the-owner-by-using-a-form"></a>フォームを使用して所有者を表示する

ユーザー定義カードを追加して、フォーム内の**所有者**フィールドを表示できます。 現時点で、フォーム コントロールを使用してフィールドの値を変更することはできません。

1. **Edit form** コントロールを挿入してから、サイズ変更して右下隅に移動します。

1. 画面の右側にある**プロパティ** タブで、**データ ソース**の一覧を開いてから、**取引先企業**を選択します。

    > [!div class="mx-imgBorder"]
    > ![空白値を持つ追加フィールドを示すフォーム コントロール](media/working-with-references/form-insert.png)  

1. フォームの **Item** プロパティを `Gallery1.Selected` に設定します。

    > [!div class="mx-imgBorder"]
    > ![ギャラリーで選択した項目から入力された追加フィールドを示すフォーム コントロール](media/working-with-references/form-item.png)

1. 画面の右側にある**プロパティ** タブで、**フィールドの編集**を選択します。

1. **フィールド** ウィンドウで、省略記号を選択してから、**ユーザー定義カードの追加**を選択します。

    > [!div class="mx-imgBorder"]
    > ![ユーザー定義カードを追加するコマンド](media/working-with-references/form-customcard.png)

    新しいカードがフォーム コントロールの下部に表示されます。

1. カードを必要に応じてサイズ変更して、すべてのテキストを表示します。

    > [!div class="mx-imgBorder"]
    > ![挿入されたユーザー定義カード、空白](media/working-with-references/form-inserted-customcard.png)

1. **Label** コントロールをユーザー定義カードに挿入してから、ラベルの **Text** プロパティをギャラリーで使用した数式に追加します:

    ```powerapps-dot
    If( IsType( ThisItem.Owner, Teams ),
        "Team: " & AsType( ThisItem.Owner, Teams ).'Team Name',
        "User: " & AsType( ThisItem.Owner, Users ).'Full Name' )
    ```

    > [!div class="mx-imgBorder"]
    > ![ラベル コントロールの所有者フィールドを示すユーザー定義カード](media/working-with-references/form-displayowner.png)

ギャラリーでの選択ごとに、レコードの所有者を含む、取引先企業のその他のフィールドがフォームに表示されます。 **パッチ** ボタンを使用して所有者を変更する場合、フォーム コントロールもその変更を表示します。

> [!div class="mx-imgBorder"]
> ![ギャラリーの変更に応答するフォーム コントロールを示すアニメーション](media/working-with-references/form-allthree.gif)

## <a name="show-the-fields-of-a-customer"></a>顧客のフィールドを表示する

Common Data Service では、**顧客**検索フィールドは、**所有者**によく似た別のポリモーフィック検索です。

**所有者**はエンティティごと 1 つに制限されていますが、エンティティには 0、1、またはそれ以上の**顧客**検索フィールドを含めることができます。 **取引先担当者**システム エンティティには、**顧客**検索フィールドである**会社名**フィールドが含まれています。

> [!div class="mx-imgBorder"]
> ![必須ではない顧客データ型として会社名フィールドを示す取引先担当者エンティティ](media/working-with-references/customer-companyname.png)

新しいフィールドの**顧客**データ型を選択することにより、別の**顧客**検索フィールドをエンティティに追加できます。

![フィールド作成時のデータ型の一覧からの顧客データ型](media/working-with-references/customer-datatype.png)

**顧客**検索フィールドは、**取引先企業**エンティティまたは**取引先担当者**エンティティのいずれかからのレコードを参照できます。 これらのエンティティで **IsType** および **AsType** 関数を使用するので、今はそれらをデータ ソースとして追加する良い機会です (**チーム**と**ユーザー**はそのままにしておきます)。

> [!div class="mx-imgBorder"]
> ![データ ウィンドウの取引先企業、チーム、ユーザー、および取引先担当者エンティティ](media/working-with-references/customer-datasources.png)

**顧客**および**所有者**フィールドの処理は非常に似ているので、文字通りアプリをコピー (**ファイル** > **名前を付けて保存**、次に別の名前を指定します) して、次の簡単な置き換えを実行できます:

| 場所 | **所有者**のサンプル | **顧客**のサンプル |
|----------|-----------|------------------|
| 全体 | **所有者** | **'顧客名'** |
| 全体 | **ユーザー** | **取引先企業** |
| 全体 | **チーム** | **取引先担当者** |
| ギャラリーの **Items** プロパティ | **取引先企業** | **取引先担当者** |
| フォームの **Items** プロパティ | **取引先企業** | **取引先担当者** |
| ボタンの **OnSelect** プロパティでの<br>**パッチ**の最初の引数 | **取引先企業** | **取引先担当者** |
| フィルター ラジオの **Items** プロパティ | **[&nbsp;"すべて"、&nbsp;"ユーザー"、&nbsp;"チーム"&nbsp;]** | **[&nbsp;"すべて"、&nbsp;"取引先企業"、&nbsp;"取引先担当者"&nbsp;]** |
| パッチ ラジオの **Items** プロパティ | **[ "ユーザー"、"チーム" ]** | **[ "取引先企業"、"取引先担当者" ]** |
| コンボ ボックスの**表示可能**プロパティ | **"ユーザー"** と **"チーム"** | **"取引先企業"** と **"取引先担当者"** |

たとえば、新しいギャラリーには次の **Items** プロパティが必要です:

```powerapps-dot
Filter( Contacts,
    Radio1.Selected.Value = "All"
    Or (Radio1.Selected.Value = "Accounts" And 'Company Name' = ComboBox1.Selected)
    Or (Radio1.Selected.Value = "Contacts" And 'Company Name' = ComboBox1_1.Selected)
)
```

> [!div class="mx-imgBorder"]
> ![簡単な変更が適用された所有者アプリから派生した顧客アプリ](media/working-with-references/customer-simple-update.png)

**顧客**と**所有者**間の 2 つの重要な違いにより、ギャラリーやフォーム内の数式への更新が必要になります:

1. **取引先企業**と**取引先担当者**間の一対多の関連付けは、これらのエンティティの種類を名前で参照するときに優先されます。 **取引先企業**の代わりに、**\[\@Accounts]** を使用し、**取引先担当者**の代わりに、**\[\@Contacts]** を使用します。 [グローバル曖昧性除去演算子](functions/operators.md#disambiguation-operator)を使用して、**IsType** および **AsType** のエンティティの種類を参照していることを確認します。 この問題は、ギャラリーとフォーム コントロールのレコード コンテキストにのみ存在します。

1. **所有者**フィールドには値が必要ですが、**顧客**フィールドは*空白*になります。 種類名なしで正しい結果を表示するには、[**IsBlank** 関数](functions/function-isblank-isempty.md)を使用してこのケースをテストし、代わりに空のテキスト文字列を表示します。

これらの変更はいずれも同じ数式で行われ、フォームのユーザー定義カードと、ギャラリーのラベルコントロールの **Text** プロパティでも表示されます:

```powerapps-dot
If( IsBlank( ThisItem.'Company Name' ), "",
    IsType( ThisItem.'Company Name', [@Accounts] ),
        "Account: " & AsType( ThisItem.'Company Name', [@Accounts] ).'Account Name',
    "Contact: " & AsType( ThisItem.'Company Name', [@Contacts] ).'Full Name'
)
```

> [!div class="mx-imgBorder"]
> ![ギャラリーでサブタイトル ラベル コントロールの Text プロパティへの更新](media/working-with-references/customer-update.png)

これらの変更により、**取引先担当者**エンティティの**会社名**フィールドを表示して変更できます。

> [!div class="mx-imgBorder"]
> ![取引先担当者の選択により他のコントロールとフォームがどう変更されるかを示すアニメーション](media/working-with-references/customer-allthree.gif)

## <a name="understand-regarding-lookup-fields"></a>関連検索フィールドについて

**関連**検索フィールドは、このトピック内ですでに作業したフィールドとは少し異なります。 このトピックの前半で説明したパターンを適用することから始め、次に他のテクニックを学びます。

**FAX** エンティティで簡単に始めることができます。 このエンティティには、**取引先企業**、**取引先担当者**、およびその他のエンティティを参照できる、ポリモーフィック**関連**検索フィールドがあります。 **顧客**用のアプリを取得し、**FAX** 用にそれを変更できます。

| 場所 | **顧客**のサンプル | **FAX** のサンプル |
|----------|-----------|------------------|
| 全体 | **'顧客名'** | **関連** |
| ギャラリーの **Items** プロパティ | **取引先担当者** | **FAX** |
| フォームの **Items** プロパティ | **取引先担当者** | **FAX** |
| ボタンの **OnSelect** プロパティでの<br> **パッチ**の最初の引数 | **取引先担当者** | **FAX** |

もう一度、データ ソースを追加する必要があります: 今回は **FAX** 用です。 **ビュー** タブで、**データソース**を選択します:

> [!div class="mx-imgBorder"]
> ![取引先企業、チーム、ユーザー、取引先担当者、および FAX エンティティを示すデータ ウィンドウ](media/working-with-references/faxes-datasources.png)

**関連**の重要な違いは、それが**取引先企業**および**取引先担当者**に限定されないということです。 実際にはエンティティの一覧は、ユーザー定義エンティティで拡張できます。 ほとんどのアプリはこの点に変更を加えなくても対応できますが、ギャラリーとフォームのラベルの数式を更新する必要があります:

```powerapps-dot
If( IsBlank( ThisItem.Regarding ), "",
    IsType( ThisItem.Regarding, [@Accounts] ),
        "Account: " & AsType( ThisItem.Regarding, [@Accounts] ).'Account Name',
    IsType( ThisItem.Regarding, [@Contacts] ),
        "Contacts: " & AsType( ThisItem.Regarding, [@Contacts] ).'Full Name',
    ""
)
```

> [!div class="mx-imgBorder"]
> ![関連検索の字幕コントロール用に更新された Text プロパティ](media/working-with-references/regarding-label.png)

これらの変更を加えた後、**所有者**および**顧客**検索を実行したように**関連**検索を使用します。

> [!div class="mx-imgBorder"]
> ![ギャラリーの項目の選択により他のコントロールとフォームがどう変更されるかを示すアニメーション](media/working-with-references/regarding-allthree.gif)

## <a name="understand-regarding-relationships"></a>関連の関連付けについて

関連には多対一の関連付けが含まれるため、**関連**は**所有者**および**顧客**とは異なります。 定義上、逆の一対多の関係により、**First( Accounts ).Faxes** と記述できます。

エンティティ定義をバックアップして見てみましょう。 Common Data Service では、**FAX**、**タスク**、**電子メール**、**メモ**、**電話**、**レター**、**チャット**などは[*活動*](../../developer/common-data-service/activity-entities.md)として指定されます。 独自の[ユーザー定義活動エンティティ](../../developer/common-data-service/custom-activities.md)を作成することもできます。 活動エンティティを表示または作成すると、その設定が**詳細設定**に表示されます。

![エンティティ作成時の活動エンティティ設定](media/working-with-references/activity-entitytype.png)

他のエンティティは、エンティティの設定で*活動タスク*として有効になっている場合、活動エンティティに関連付けることができます。 **取引先企業**、**取引先担当者**、および他の多くの標準エンティティがそのように指定されています (この場合も、**詳細設定**で)。

![エンティティ作成時の活動タスク設定](media/working-with-references/activity-entityuse.png)

すべての活動エンティティと活動タスク エンティティには、暗黙の関連付けがあります。 画面の上部でフィルターを**すべて**に変更し、**FAX** エンティティを選択してから、**関連付け**タブを選択する場合、**関連**検索のターゲットであるすべてのエンティティが表示されます。

> [!div class="mx-imgBorder"]
> ![関連多対一の関連付けを示す FAX エンティティの関連付け](media/working-with-references/activity-manytoone.png)

**取引先企業**エンティティの関連付けを表示する場合、**関連**検索フィールドのソースであるすべてのエンティティが表示されます。

> [!div class="mx-imgBorder"]
> ![関連一対多の関連付けを示す取引先企業エンティティの関連付け](media/working-with-references/activity-onetomany.png)

どういう意味ですか ?

- 数式を記述するとき、活動エンティティの一覧が固定されておらず、独自に作成できることを考慮する必要があります。 数式は、予期しなかった活動エンティティを適切に処理する必要があります。
- 活動タスクおよび活動には、一対多の関連付けがあります。 取引先企業に関連するすべての FAX を簡単に要求できます。

アプリでこの概念を調べるには:

1. 別の画面を追加します。

    > [!div class="mx-imgBorder"]
    > ![空白画面を挿入する](media/working-with-references/activitypointer-newscreen.png)

1. ギャラリー コントロールを挿入し、サイズ変更してから、画面の左側に移動します。

1. 画面の右側にある**プロパティ** タブで、ギャラリーの **Items** を**取引先企業**に設定します。

    > [!div class="mx-imgBorder"]
    > ![プロパティ ウィンドウで Items を取引先企業に設定する](media/working-with-references/activitypointer-accounts.png)

1. ギャラリーのレイアウトを**タイトル**に設定してから、タイトル フィールドを**取引先企業名**に設定します。

    > [!div class="mx-imgBorder"]
    > ![プロパティ ウィンドウでギャラリー コントロールのレイアウトをタイトルに設定する](media/working-with-references/activitypointer-account-name.png)

1. 2 つ目のギャラリーを追加し、サイズ変更してから、画面の右側に移動します。

1. 新しいギャラリーの **Items** プロパティを `Gallery2.Selected.Faxes` に設定します。

    この手順では、指定した取引先企業に対するフィルター処理された FAX の一覧を返します。

    > [!div class="mx-imgBorder"]
    > ![FAX を表示するギャラリーの Items プロパティを設定する](media/working-with-references/activitypointer-faxes.png)

1. ギャラリーのレイアウトを**タイトルとサブタイトル**に設定してから、タイトル フィールドを**件名**フィールド (小文字で**件名 (subject)** の場合がある) を表示するように設定します。

    > [!div class="mx-imgBorder"]
    > ![タイトルを件名フィールドに設定する](media/working-with-references/activitypointer-subject.png)

取引先企業の一覧で項目を選択すると、FAX の一覧にはその取引先企業のみの FAX が表示されます。

> [!div class="mx-imgBorder"]
> ![FAX の一覧を操作する取引先企業ギャラリーでの選択を示すアニメーション](media/working-with-references/activitypointer-allthree.gif)

## <a name="activity-entity"></a>活動エンティティ

前のセクションで説明したように、取引先企業のすべての FAX を表示できます。 ただし、FAX、電子メール メッセージ、電話、その他のやり取りを含む、取引先企業のすべての活動を表示することもできます。

後者のシナリオでは、**活動**エンティティを使用します。 右上隅で**すべて**をオンにして、エンティティの一覧からフィルターを削除することにより、このエンティティを表示できます。

> [!div class="mx-imgBorder"]
> ![活動エンティティを示すエンティティの一覧](media/working-with-references/activitypointer-entity.png)

**活動**エンティティは特別です。 レコードを **FAX** エンティティに追加するたびに、システムではすべての活動エンティティに共通のフィールドを持つ**活動**エンティティのレコードも作成されます。 これらのフィールドのうち、**件名**は最も興味深いものの 1 つです。

前の例の 1 行だけを変更することで、すべての活動を表示できます。 `Gallery2.Selected.Faxes` を `Gallery2.Selected.Activities` に置き換えます。

> [!div class="mx-imgBorder"]
> ![2 番目のギャラリーの Items プロパティの変更、FAX から活動への変更](media/working-with-references/activitypointer-gallery.png)

レコードは**活動**エンティティから取得されますが、それでも **IsType** 関数を使用してそれらの活動の種類を識別できます。 この場合も、エンティティの種類で **IsType** を使用する前に、データ ソースを追加する必要があります。

> [!div class="mx-imgBorder"]
> ![IsType 関数に必要なすべてのエンティティを示すデータ ウィンドウ](media/working-with-references/activity-datasources.png)

この式を使用すると、ギャラリー内のラベル コントロールにレコードの種類を表示できます。

```powerapps-dot
If( IsType( ThisItem, [@Faxes] ), "Fax",
    IsType( ThisItem, [@'Phone Calls'] ), "Phone Call",
    IsType( ThisItem, [@'Email Messages'] ), "Email Message",
    IsType( ThisItem, [@Chats] ), "Chat",
    "Unknown"
)
```

> [!div class="mx-imgBorder"]
> ![テキスト プロパティを数式に設定して FAX、電話、その他の活動の情報を表示する](media/working-with-references/activitypointer-type.png)

**AsType** を使用して特定の種類のフィールドにもアクセスできます。 たとえば、次の数式は各活動の種類を決定し、電話の場合は**電話番号**エンティティからの電話番号と通話の方向を表示します:

```powerapps-dot
If( IsType( ThisItem, [@Faxes] ), "Fax",
    IsType( ThisItem, [@'Phone Calls'] ),
       "Phone Call: " &
       AsType( ThisItem, [@'Phone Calls'] ).'Phone Number' &
       " (" & AsType( ThisItem, [@'Phone Calls'] ).Direction & ")",
    IsType( ThisItem, [@'Email Messages'] ), "Email Message",
    IsType( ThisItem, [@Chats] ), "Chat",
    "Unknown"
)
```

> [!div class="mx-imgBorder"]
> ![電話の詳細情報を含む拡張されたテキスト プロパティ](media/working-with-references/activitypointer-phonecall.png)

その結果、アプリは活動の完全なリストを表示します。 **件名**フィールドは、数式で考慮されるかどうかに関係なく、すべての種類の活動に対して表示されます。 知っている活動の種類については、種類名および各活動に関する種類固有の情報を表示できます。

> [!div class="mx-imgBorder"]
> ![さまざまな種類の活動に関する情報を示す完成した画面](media/working-with-references/activitypointer-complete.png)

## <a name="notes-entity"></a>メモ エンティティ

ここまでで、**関連**のすべての例は活動に基づきましたが、**メモ** エンティティは別のケースを表します。

エンティティを作成する際に、添付ファイルを有効にできます。

> [!div class="mx-imgBorder"]
> ![エンティティの作成時に添付ファイルとメモを有効にする](media/working-with-references/notes-entity.png)

添付ファイルを有効にするためのチェックボックスをオンにすると、次の図が**取引先企業**エンティティを示すように、**メモ** エンティティとの**関連**の関連付けが作成されます。

> [!div class="mx-imgBorder"]
> ![一対多の関連付けを介してメモへの関連付けを示す取引先企業エンティティ](media/working-with-references/notes-relationships.png)

この違い以外は、活動を使用するのと同じ方法で**関連**検索を使用します。 添付ファイルが有効になっているエンティティには、この例のように、**メモ**への一対多の関連付けがあります:

`First( Accounts ).Notes`

> [!NOTE]
> 現時点で、**関連**検索は**メモ** エンティティでは利用できません。 **関連**フィールドに基づいて読み取りまたはフィルター処理することはできませんし、**パッチ**を使用してフィールドを設定することもできません。
>
> ただし、逆に**メモ**の一対多の関連付けは利用できるため、添付ファイルが有効になっているレコードのメモの一覧をフィルター処理できます。 [**Relate**](functions/function-relate-unrelate.md) 関数を使用してレコードの**メモ** テーブルにメモも追加できますが、この例のように、最初にメモを作成する必要があります。
>
>`Relate( ThisItem.Notes, Patch( Notes, Defaults( Notes ), { Title: "A new note" } ) )`

## <a name="activity-parties"></a>活動パーティ

現時点で、キャンバス アプリは活動パーティーをサポートしていません。