---
title: Relate および Unrelate 関数 | Microsoft Docs
description: Power Apps での Relate および Unrelate 関数の構文と例を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 01/22/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e2b1d0e8ab264b9576c18aa7d5803be30c4a45e1
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3304751"
---
# <a name="relate-and-unrelate-functions-in-power-apps"></a>Power Apps での Relate および Unrelate 関数

一対多または多対多のリレーションシップを通じて 2 つのエンティティのレコードの関連付け、および関連付け解除を行います。

## <a name="description"></a>内容

**Relate** 関数は、2 つのレコードを Common Data Service の一対多または多対多のリレーションシップを通じてリンクします。 **Unrelate** 関数は、このプロセスを無効にし、リンクを削除します。

一対多の関連付けの場合、多のエンティティに一のエンティティのレコードを指す外部キー フィールドがあります。 **Relate** はこのフィールドが一のエンティティの特定のレコードを指すように設定し、**Unrelate** はこのフィールドを*空白*に設定します。 **Relate** が呼び出されたときフィールドがすでに設定されている場合、既存のリンクは失われ、新しいリンクが選択されます。 このフィールドは、[**Patch**](function-patch.md) 関数または **[編集フォーム](../controls/control-form-detail.md)** コントロールを使用して設定することもでき、**Relate** 関数を使用する必要はありません。

多対多の関連付けの場合、レコードをリンクするシステムは、非表示の結合の表を保持します。 この結合の表に直接アクセスすることはできず、1 対多のプロジェクションを通してのみ読み取ることができ、**Relate** および **Unrelate** 関数を通して設定します。 どちらの関連エンティティにも外部キーはありません。

最初の引数で指定したエンティティのデータは更新されて変更が反映されますが、2 番目の引数で指定したエンティティのデータは更新されません。 そのデータは、**[Refresh](function-refresh.md)** 関数を使用して手動で更新することにより、操作の結果が表示されます。

これらの関数はレコードの作成または削除を行いません。 既に存在する 2 つのレコードを関連付けるか、または関連付けを解除するだけです。

これらの関数は、[動作の数式](../working-with-formulas-in-depth.md) 内でのみ使用できます。

> [!NOTE]
> これらの関数はプレビュー機能の一部であり、それらの動作は**リレーショナル データ、オプション セット、および CDS のその他の新機能**の機能が有効になっている場合のみ利用可能です。 これは、新しいアプリに対して既定で有効になっているアプリ レベルの設定です。 この機能の切り替えを検索するには、**ファイル** メニューを開き、**アプリの設定**を選択した後、**詳細設定**を選択します。 お客様のフィードバックは弊社にとって非常に重要です。ご意見を [Power Apps コミュニティ フォーラム](https://powerusers.microsoft.com/t5/Expressions-and-Formulas/bd-p/How-To) にお寄せください。

## <a name="syntax"></a>構文

**Relate**( *Entity1RelatedTable*, *Entity2Record* )

* *Entity1RelatedTable* - 必須。 *Entity1* のレコードに対して、一対多または多対多の関連付けを通して関連付けられた *Entity2* のレコードのテーブル。
* *Entity2Record* - 必須。 関連付けに追加される *Entity2* のレコード。

**Unrelate**( *Entity1RelatedTable*, *Entity2Record* )

* *Entity1RelatedTable* - 必須。 *Entity1* のレコードに対して、一対多または多対多の関連付けを通して関連付けられた *Entity2* のレコードのテーブル。
* *Entity2Record* - 必須。 関連付けから削除される *Entity2* のレコード。

## <a name="examples"></a>例

[Power Apps ポータルのエンティティ ビューアー](../../common-data-service/create-edit-entities-portal.md) に表示されている次の関連付けを含む**製品**エンティティを検討してください。

| リレーションシップの表示名 | 関連エンティティ | 関連付けの種類 |
| --- | --- |
| 製品の予約 | 予約 | 一対多 |
| Product &harr; Contact | 取引先担当者  | 多対多 |

**製品**および**予約**は、1 対多の関連付けで関連付けられています。  **予約**エンティティの最初のレコードを**製品**エンティティの最初のレコードと関連付けます。

`Relate( First( Products ).Reservations, First( Reservations ) )`

これらのレコード間の関連付けを削除します。

`Unrelate( First( Products ).Reservations, First( Reservations ) )`

レコード間の関連付けが変更されただけで、レコードの作成または削除は行われませんでした。

**製品**および**取引先担当者**は、多対多の関連付けで関連付けられています。  **取引先担当者**エンティティの最初のレコードを**製品**エンティティの最初のレコードと関連付けます。

`Relate( First( Products ).Contacts, First( Contacts ) )`

多対多の関連付けは対称なので、これを反対方向で行うこともできます。

`Relate( First( Contacts ).Products, First( Products ) )`

これらのレコード間の関連付けを削除します。

`Unrelate( First( Products ).Contacts, First( Contacts ) )`

または、

`Unrelate( First( Contacts ).Products, First( Products ) )`

関連するレコードの選択に対して**ギャラリー**および**コンボ ボックス**のあるアプリを使用するエンティティに対するこれらの操作についてを正確に説明します。

これらの例は、環境にインストールされているサンプル データによって異なります。 [サンプル データを含む試用環境を作成する](../../model-driven-apps/overview-model-driven-samples.md#get-sample-apps) または [既存の環境にサンプル データを追加する](../../model-driven-apps/overview-model-driven-samples.md#install-or-uninstall-sample-data) のいずれかです。

### <a name="one-to-many"></a>一対多

#### <a name="relate-function"></a>**Relate** 関数

最初に、製品に関連付けられている予約の表示および再割り当てを行う簡単なアプリを作成します。

1. [空白からタブレット アプリ](../data-platform-create-app-scratch.md) を作成します。

1. **ビュー** タブで、**データ ソース**を選択します。

1. **データ** ウィンドウで、**データ ソースの追加** > **Common Data Service** > **製品** > **接続**を選択します。  

    製品エンティティは、上で読み込まれたサンプル データの一部です。

     ![製品エンティティをデータ ソースとして追加する](media/function-relate-unrelate/products-connect.png)

1. **挿入**タブで、ブランクで縦方向の **[ギャラリー](../controls/control-gallery.md)** コントロールを追加します。

1. 追加したコントロールに **Gallery1** という名前が付けられていることを確認し、画面の左側いっぱいになるように移動させ、サイズを変更します。

1. **プロパティ** タブで、**Gallery1** の**アイテム** プロパティに**製品**を、その**レイアウト**に**画像とタイトル**を設定します。

    ![ProductsGallery の構成](media/function-relate-unrelate/products-gallery.png)

1. **Gallery1** で、**ラベル** コントロールに **Title1** という名前が付けられていることを確認し、その**テキスト** プロパティに **ThisItem.Name** と設定します。

    ![Gallery1 のラベルを構成する](media/function-relate-unrelate/products-title.png)

1. 画面を選択して、次のアイテムが **Gallery1** に挿入されるのを回避します。  ブランクで縦方向の 2 番目の**ギャラリー** コントロールを追加し、**Gallery2** という名前が付けられていることを確認します。

    **Gallery2** に **Gallery1** でユーザーが選択した製品の予約が表示されます。

1. 画面の右上の領域いっぱいになるように、**Gallery2** を移動し、サイズを変更します。

1. (オプション) 次の図が示すように、青色の**ラベル** コントロールを **Gallery2** の上に追加します。

1. 数式バーで、**Gallery2** の **Items** プロパティに **Gallery1.Selected.Reservations** と設定します。

    ![Gallery2 のアイテムの構成](media/function-relate-unrelate/reservations-gallery.png)

1. プロパティ ウィンドウで、**Gallery2** の **Layout** に **Title** と設定します。

    ![Gallery2 のレイアウトの構成](media/function-relate-unrelate/reservations-gallery-right.png)

1. **Gallery2** で、**[コンボ ボックス](../controls/control-combo-box.md)** コントロールを追加し、**ComboBox1** と名前が付けられていることを確認した後、**Gallery2** のその他のコントロールをブロックすることを避けるように移動させ、サイズを変更します。

1. **プロパティ** タブで、**ComboBox1** の **Items** プロパティに **Products** と設定します。

    ![Items プロパティを Products に設定する](media/function-relate-unrelate/reservations-combo-right.png)

1. **プロパティ** タブを下方向へスクロールし、**ComboBox1** の **Allow multiple selection** プロパティを **Off** に設定します。

    ![Allow multiple selection を Off に設定する](media/function-relate-unrelate/reservations-singleselect-right.png)

1. 数式バーで、**ComboBox1** の **DefaultSelectedItems** プロパティを **ThisItem.'Product Reservation'** に設定します。

    ![ReserveCombo の DefaultSelectedItems を設定する](media/function-relate-unrelate/reservations-combo.png)

1. **Gallery2** で、**NextArrow2** の **OnSelect** プロパティをこの式に設定します。

    ```powerapps-dot
    Relate( ComboBox1.Selected.Reservations, ThisItem )
    ```

    ユーザーがこのアイコンを選択すると、現在の予約はユーザーが **ComboBox1** で選択した製品に変更されます。

    ![NextArrow2 を構成する](media/function-relate-unrelate/reservations-relate.png)

1. F5 キーを押して、プレビュー モードでアプリをテストします。

このアプリを使用して、ユーザーは予約を 1 つの製品から別の製品に移動できます。 製品の予約について、ユーザーは **ComboBox1** の異なる製品を選択することができ、**NextArrow2** を選択してその予約を変更します。

![一対多のアプリで Relate 関数をデモンストレーションする](media/function-relate-unrelate/reservations-reassign.gif)

#### <a name="unrelate-function"></a>**Unrelate** 関数

この時点で、関連付けを 1 つのレコードから別のレコードに移動できますが、関連付けを完全に削除することはできません。 **Unrelate** 関数を使用して、すべての商品から予約レコードとの接続を解除することができます。

1. **ビュー** タブで、**データ ソース**を選択します。

1. **データ** ウィンドウで、**データ ソースの追加** > **Common Data Service** > **予約** > **接続**を選択します。

1. **Gallery2** で、**NextArrow2** の **OnSelect** 式をこの式に設定します。

    ```powerapps-dot
    If( IsBlank( ComboBox1.Selected ),
        Unrelate( Gallery1.Selected.Reservations, ThisItem ),
        Relate( ComboBox1.Selected.Reservations, ThisItem )
    );
    Refresh( Reservations )
    ```
    ![右側のアイコンの構成](media/function-relate-unrelate/reservations-relate-unrelate.png)

1. **Gallery2** を Ctrl-C キーを押してクリップボードにコピーします。

1. Ctrl-V キーを押して **Gallery2** の複製を同じ画面に貼り付け、画面の右下の領域に移動させます。

1. (オプション) **Gallery2** の上にラベルを追加した場合、そのラベルに対して前の 2 つの手順を繰り返します。

1. **Gallery2** の複製に **Gallery2_1** という名前が付けられていることを確認し、その **Items** プロパティをこの式に設定します。

    ```powerapps-dot
    Filter( Reservations, IsBlank( 'Product Reservation' ) )
    ```

    委任の警告が表示されますが、この例ではデータが少量なので問題になりません。

    ![Gallery2_1 の Items プロパティを設定する](media/function-relate-unrelate/reservations-lost.png)

これらの変更により、ユーザーは、製品を予約していない取引先担当者に対する **ComboBox1** の選択をクリアできます。 製品を予約していない取引先担当者は、ユーザーが各取引先担当者を製品に割り当てることのできる **Gallery2_1** に表示されます。

   ![一対多のアプリで Relate および Unrelate 関数をデモンストレーションする](media/function-relate-unrelate/reservations-lostandfound.gif)

### <a name="many-to-many"></a>多対多

#### <a name="create-a-many-to-many-relationship"></a>多対多の関連付けを作成する

サンプル データには多対多の関連付けは含まれていませんが、製品エンティティと取引先担当者エンティティ間で作成することができます。 ユーザーは各製品を複数の取引先担当者に関連付け、また各取引先担当者を複数の製品に関連付けることができます。

1. [このページ](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) から、左側のナビゲーション バーの**データ**を選択し、**エンティティ**を選択します。

    ![エンティティの一覧を開く](media/function-relate-unrelate/entity-list.png)

1. エンティティ フィルターを変更して、すべてのエンティティを含めます。

    既定では、サンプル エンティティは表示されません。

    ![エンティティ フィルターを削除する](media/function-relate-unrelate/entity-all.png)

1. 下方向へスクロールして、**製品**エンティティを開き、**関連付け**を選択します。

    ![製品エンティティの関連付けタブ](media/function-relate-unrelate/entity-relationships.png)

1. **関連付けの追加** > **多対多**を選択します。

    ![多対多の関連付けを追加する](media/function-relate-unrelate/entity-manytomany.png)

1. 関連付ける**取引先担当者**エンティティを選択します。

    ![取引先担当者エンティティを選択する](media/function-relate-unrelate/entity-contact.png)

1. **完了** > **エンティティの保存**を選択します。

    ![製品エンティティの関連付けの一覧](media/function-relate-unrelate/entity-done.png)

#### <a name="relate-and-unrelate-contacts-with-one-or-more-products"></a>取引先担当者を 1 つ以上の製品と関連付ける、またはその関連付けを解除する

このトピックで以前に作成したアプリに似た別のアプリを作成しますが、新しいアプリは多対多の関連付けを提供します。 各取引先担当者は、1 つの製品だけの代わりに、複数の製品を予約できます。

1. タブレット用の空白のアプリで、このトピックの [最初の手順](#one-to-many) で説明したように、**Gallery1** を作成します。

1. 空白で縦方向の別の**ギャラリー** コントロールを追加し、**Gallery2** と名前が付けられていることを確認した後、画面の右上隅に移動します。

    このトピックの後半で、**Gallery2** の下に**コンボ ボックス** コントロールを追加します。

1. 数式バーで、**Gallery2** の **Items** プロパティを **Gallery1.Selected.Contacts** に設定します。

    ![ContactsGallery の構成](media/function-relate-unrelate/contacts-gallery.png)

1. **プロパティ** タブで、**レイアウト**を**画像とタイトル**に設定します。

    ![ContactsGallery の構成](media/function-relate-unrelate/contacts-gallery-right.png)

1. **Gallery2** で、**ラベル** コントロールに **Title2** という名前が付けられていることを確認し、その**テキスト** プロパティに **ThisItem.'Full Name'** と設定します。

    この手順を完了して取引先担当者を製品に割り当てるまで、そのコントロールにはテキストは表示されません。

    ![取引先担当者名の表示](media/function-relate-unrelate/contacts-title.png)

1. **NextArrow2** を削除し、**キャンセル** アイコンを挿入した後、**icon1** と名前が付けられていることを確認します。

1. **キャンセル** アイコンの **OnSelect** プロパティを次の式に設定します: 

    ```powerapps-dot
    Unrelate( Gallery1.Selected.Contacts, ThisItem )
    ```

    ![キャンセル アイコンの構成](media/function-relate-unrelate/contacts-unrelate.png)

1. **ビュー** タブで、**データ ソース**を選択します。

1. **データ** ウィンドウで、**データ ソースの追加** > **Common Data Service** > **取引先担当者** > **接続**を選択します。

1. **Gallery2** の下で、**コンボ ボックス** コントロールを追加し、**ComboBox1** と名前が付けられていることを確認した後、その **Items** プロパティを**取引先担当者**に設定します。

    ![コンボ ボックスの Items プロパティを構成する](media/function-relate-unrelate/contacts-combo.png)

1. **プロパティ** タブで、**Allow multiple selection** を**オフ**に設定します。

    ![コンボ ボックスの Layout プロパティを構成する](media/function-relate-unrelate/contacts-combo-right.png)

1. **追加**アイコンを挿入し、**OnSelect** プロパティに次の数式を設定します: 

    ```powerapps-dot
    Relate( Gallery1.Selected.Contacts, ComboBox1.Selected )
    ```

    ![追加アイコンの構成](media/function-relate-unrelate/contacts-relate.png)

このアプリを使用すると、ユーザーは一連の取引先担当者を自由に各製品に関連付けたり、関連付けを解除したりできます。

- 製品に取引先担当者を追加するには、画面下部のコンボ ボックスで取引先担当者を選択し、次に**追加**アイコンを選択します。
- 製品から取引先担当者を削除するには、その取引先担当者の**キャンセル** アイコンを選択します。

    一対多とは異なり、多対多の関連付けにより、ユーザーは同じ取引先担当者を複数の製品に関連付けることができます。

![多対多のアプリで Relate および Unrelate 関数をデモンストレーションする](media/function-relate-unrelate/contacts-relate-unrelate.gif)

#### <a name="in-reverse-relate-and-unrelate-products-with-multiple-contacts"></a>逆に、製品を複数の取引先担当者に関連付けたり、関連付けを解除したりする

多対多の関連付けは対称です。 サンプルを拡張して製品を取引先担当者に追加し、2 つの画面間で切り替えて、関連付けをいずれかの方向から表示することができます。

1. **Screen1** の **OnVisible** プロパティを、**Refresh (製品)** に設定します。

    一対多または多対多の関連付けを更新する場合、**Relate** または **Unrelate** 呼び出しの最初の引数のエンティティのデータのみ更新されます。 このアプリの画面間で切り替えるには、2 番目を手動で更新する必要があります。

    ![OnVisible プロパティを Refresh 関数に設定する](media/function-relate-unrelate/contacts-refresh.png)

1. **Screen1** を複製します。

    複製には **Screen1_1** という名前が付けられ、取引先担当者側から関連付けを見るベースが作られます。

    ![画面の複製](media/function-relate-unrelate/contacts-duplicate.png)

1. リバース ビューを作成するには、**Screen1_1** のコントロール上の数式を変更します。

    - Screen1_1.OnVisible = `Refresh( Contacts )`
    - Gallery1_1.Items = `Contacts`
    - Title1_1.Text = `ThisItem.'Full Name'`
    - Label1_1.Text = `"Selected Contact Products"`
    - Gallery2_1.Items = `Gallery1_1.Selected.Products`
    - Title2_1.Text = `ThisItem.Name`
    - Icon1_1.OnSelect = `Unrelate( Gallery1_1.Selected.Products, ThisItem )`
    - ComboBox1_1.Items = `Products`
    - Icon2_1.OnSelect = `Relate( Gallery1_1.Selected.Products, ComboBox1_1.Selected )`

    結果は前の画面類似していますが、**取引先担当者**側からの関連付けから作成されています。

    ![取引先担当者から始まる多対多の関係を表示する](media/function-relate-unrelate/reverse-screen.png)

1. **上下の矢印**のアイコンを挿入し、その設定 **OnSelect** プロパティを **Navigate( Screen1, None )** に設定します。  数式 **Navigate( Screen1_1, None )** を使用して、同じことを **Screen1** に行います。

    ![画面間のナビゲーションの追加](media/function-relate-unrelate/reverse-navigate.png)

この新しい画面により、ユーザーは製品に取引先担当者を追加し、取引先担当者のビューに切り替えて、関連する製品を表示することができます。 関連付けは 2 つの画面間で対称的であり、また共有されます。

![どちらの側からも多対多の関連付けを実証する](media/function-relate-unrelate/contacts-reverse.gif)
