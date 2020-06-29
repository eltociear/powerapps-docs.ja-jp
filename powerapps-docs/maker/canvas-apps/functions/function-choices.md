---
title: Choices 関数 | Microsoft Docs
description: Power Apps での Choices 関数の構文を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/15/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ab805ec283ca43c96982eb04357ded9aed934a03
ms.sourcegitcommit: 80120b59d440bb7a3ddca93cd51154607f749f6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "3307787"
---
# <a name="choices-function-in-power-apps"></a>Power Apps の Choices 関数
検索列で使用可能な値のテーブルを返します。

## <a name="description"></a>内容
**Choices** 関数は、検索列で使用可能な値のテーブルを返します。  

**Choices** 関数を使用して、ユーザーが選択する選択肢の一覧を提供します。 この関数は、編集フォームで [**コンボ ボックス**](../controls/control-combo-box.md) コントロールと共によく使用されます。

ルックアップの場合、**Choices** が返すテーブルは、ルックアップに関連付けられている外部テーブルと一致します。 **Choices** を使用することにより、追加データ ソースとして外部テーブルを追加する必要がなくなります。 **Choices** は、外部テーブルのすべての列を返します。

**Choices** はテーブルを返すので、[**Filter**](function-filter-lookup.md)、[**Sort**](function-sort.md)、[**AddColumns**](function-table-shaping.md)、その他すべてのテーブル操作関数を使って、テーブルをフィルター、並べ替え、整形できます。 

現時点で、**Choices** を[委任](../delegation-overview.md) することはできません。 この制限によりアプリで問題がある場合は、データ ソースとして外部エンティティを追加し、それを直接使用してください。 

[**ShowColumns**](function-table-shaping.md)、[**Search**](function-filter-lookup.md)、その他のテーブル関数とは異なり、**Choices** は列名を文字列にして二重引用符で囲む必要はありません。 列を直接参照するのと同じように、式を指定します。

列参照は、データ ソースに対して直接行う必要があります。 たとえば、データ ソースが **Accounts** でルックアップが **SLA** の場合、列参照は **Accounts.SLA** になります。 参照は、関数、変数、またはコントロールを経由することはできません。 この例を拡張し、**Accounts** が **Gallery** コントロールにフィードされる場合は、式 **Gallery.Selected.SLA** を使って選択されたアカウントの SLA を参照します。 ただし、この参照はコントロールを経由したので、**Columns** 関数に渡されることはできません。やはり **Accounts.SLA** を使う必要があります。

現時点では、ルックアップ列を使用できるのは SharePoint および Common Data Service のみです。

## <a name="syntax"></a>構文
**Choices**( *column-reference* )

* *column-reference* – 必須。  データ ソースのルックアップ列です。 列名を二重引用符で囲まないでください。 参照は、データ ソースの列に対して直接行う必要があり、関数またはコントロールを経由してはなりません。

## <a name="examples"></a>例

#### <a name="choices-for-a-lookup"></a>ルックアップの選択肢

1. Common Data Service に[データベースを作成](../../../administrator/create-database.md)し、**サンプル アプリとデータを含める**のボックスを選択します。

    **取引先企業**などの多数のエンティティが作成されます。

    **注**: エンティティの名前は、make.powerapps.com では単数形、Power Apps Studio では複数形です。

    ![アプリ用 Common Data Service の 取引先企業エンティティのフィールドのリストの一部、「取引先責任者」がルックアップ フィールドであることの強調表示](media/function-choices/entity-account.png)

    **取引先企業**エンティティには **取引先責任者**の列があり、これは **取引先担当者**エンティティに対するルックアップです。  

    ![Common Data Service の取引先担当者エンティティのフィールドのリストの一部](media/function-choices/entity-contact.png)

    各アカウントについて、取引先担当者が取引先責任者として指定されているか、または取引先責任者が*空白*になっています。

1. **取引先企業**エンティティから[アプリを生成](../data-platform-create-app.md)します。

1. 左端にある画面とコントロールのリストで、**EditScreen1** が表示されるまで下にスクロールし、そのすぐ下にある **EditForm1** を選択します。

    ![左側のナビゲーション バーで、EditScreen1 の EditForm1 を選択する](media/function-choices/select-editform.png)

1. 右側のウィンドウの**プロパティ** タブで**フィールドの編集**を選択します。

    ![データ ウィンドウを開きます](media/function-choices/open-data-pane.png)

1. **フィールド** ウィンドウで、**フィールドの追加**を選択します。

1. **取引先責任者**フィールドを検索し、そのチェックボックスを選択してから、**追加**を選択します。

    ![取引先企業を選択して、データ ウィンドウを開く](media/function-choices/field-list.png)

    **取引先責任者**フィールドは、フォームの下部に表示されます。 フィールドにエラーが表示された場合は、**ビュー** タブで**データ ソース**を選択し、**取引先企業**データ ソースの省略記号 (...) を選択し、**更新**を選択します。

1. (オプション) **取引先責任者**のフィールドをフィールド一覧の下部から先頭にドラッグします。

1. **取引先責任者**のカードで、**コンボ ボックス** コントロールを選択します。

    そのコントロールの **Items** プロパティは、最初の例のように表示名、または 2 番目の例のように論理名で列を識別する式に設定されます。

   - **Choices( Accounts.'Primary Contact' )**
   - **Choices( Accounts.primarycontactid )**

     ![フォーム コントロールを含むキャンバス画面。 取引先責任者カードのコンボ ボックス コントロールが選択されており、式 Choices( Accounts.'Primary Contact') を持つ Items プロパティが表示される](media/function-choices/accounts-primary-contact.png)

1. わかりやすくするため、**Choices** 関数によって返された完全なテーブルを、**Data table** コントロールで確認できます。  **ホーム** タブの**新しい画面**を選択し、**空白**を選択します。

1. **挿入**タブの**データ テーブル**を選択します。

1. **データ テーブル** コントロールの **Items** プロパティを次の数式に設定します。

     **Choices( Accounts.'Primary Contact' )**

1. **データ テーブル** コントロールの中央で、**フィールドを選んでください ...** で始まるリンクを選択してから、表示するフィールド (たとえば、**firstname** および **lastname**) のチェック ボックスを選択します。

     ![データ テーブル コントロールを含むキャンバス画面。 Items プロパティは式 Choices( Accounts.'Primary Contact' ) に設定され、テーブルには取引先担当者エンティティの最初のレコード セットの firstname 列と lastname 列が表示されている](media/function-choices/full-accounts-pc.png)