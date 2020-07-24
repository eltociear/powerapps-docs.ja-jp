---
title: アプリで検索リストをフィルター処理する方法。  | Microsoft Docs
description: この記事では、SharePoint リストからデータを取得するときにアイテムを検索し、アプリでリストをフィルター処理する方法について説明します。
author: emcoope-msft
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/01/2020
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c1d568e4c96011e141aa8c24f89bc104c3a674fe
ms.sourcegitcommit: 8728546925c570541bebc1ac7a24227651e8f65f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "3463845"
---
# <a name="how-to-filter-a-search-list-in-an-app"></a>アプリで検索リストをフィルター処理する方法は?

このシナリオ記事では、キャンバス アプリで検索リストをフィルター処理する方法を説明します。

## <a name="prerequisites"></a>前提条件

- SharePoint リストに接続する SharePoint コネクタを使用してアプリを作成しておく必要があります。
- SharePoint リストは、キャンバス アプリ内のデータをフィルター処理するための複数のリスト アイテムで構成する必要があります。

## <a name="scenario-details"></a>シナリオの詳細

キャンバス アプリでテキスト入力コントロールを使用してテキストを入力し、データ テーブルなどのリストをフィルター処理して、接続された SharePoint リストからリスト アイテムをフィルター処理できます。

テキスト入力を使用して検索し、レコードをフィルター処理する機能を使用するには、関数 [filter](../functions/function-filter-lookup.md) を使用する必要があります。 例えば、`Filter([@Colors], StartsWith(Title, TextInput1.Text))` は SharePoint リスト接続 **色** と列 **タイトル** を使用して、レコードをフィルター処理します。

## <a name="example"></a>例

1. [Power Apps](https://make.powerapps.com) にサインインします。

1. 新しいアプリを [作成](../app-from-sharepoint.md) するか、既存のアプリを [編集](../edit-app.md) します。

    > [!NOTE]
    > 前提条件で説明されているように、アプリが SharePoint 接続を使用し、SharePoint リストに接続していることを確認します。

1. 左側のペインから **+** (挿入) を選択します。

1. **テキスト入力** を選択します。

    ![テキスト入力の挿入](./media/scenarios-filter-search-list/insert-text-input.png "テキスト入力の挿入")

1. 同様に、**データ テーブル** を挿入します。

    ![データ テーブルの挿入](./media/scenarios-filter-search-list/insert-data-table.png "データ テーブルの挿入")

1. データ テーブルの **アイテム** プロパティを次の式で更新します:

    `Filter([@Colors], StartsWith(Title, TextInput1.Text))`

    **色** を SharePoint リストの名前に、**タイトル** をリスト内の列の名前に、**TextInput1** をテキスト入力コントロール名に置き換えます。

    ![フィルター式](./media/scenarios-filter-search-list/filter-formula.png "フィルター式")

1. アプリを再生します。

1. 'B' で始まるアイテムをフィルタリングするには、'B' などのテキストを入力します。

    ![色](./media/scenarios-filter-search-list/colors.png "色")

### <a name="see-also"></a>関連項目

- Power Apps の [数式のリファレンス](../formula-reference.md)
- Power Apps の [コントロールのリファレンス](../reference-properties.md)
