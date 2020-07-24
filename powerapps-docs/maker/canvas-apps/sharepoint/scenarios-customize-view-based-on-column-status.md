---
title: SharePoint リスト内の列の状態に基づいてアプリ画面をカスタマイズする方法。  | Microsoft Docs
description: この記事では、SharePoint リスト内の列の状態に基づいてアプリ画面をカスタマイズする方法について説明します。
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
ms.openlocfilehash: f0ceda35f7f83512ffa8d0972b8c93a400803eb7
ms.sourcegitcommit: 8728546925c570541bebc1ac7a24227651e8f65f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "3463843"
---
# <a name="how-to-customize-an-app-screen-based-on-column-status-inside-sharepoint-list"></a>SharePoint リスト内の列の状態に基づいてアプリ画面をカスタマイズする方法は?

このシナリオ記事では、SharePoint リスト内の列の状態に基づいてアプリ画面をカスタマイズする方法を説明します。 サポートされているリストまたはライブラリのフォームをカスタマイズしたり、リストやライブラリ用のアプリを作成することもできます。

SharePoint オブジェクトへのアクセスを制限するには、SharePoint 内の詳細な権限を使用します。 ただし、さまざまなデバイスを使用している場合は特に、アプリ画面のすべてのアイテムをスキャンすることが難しくなります。 

最も一般的な問題の 1 つは、権限を使用してアクセスを制御するのではなく、列の状態に基づいてキャンバス アプリ画面のアイテムを制限する方法です。

この方法では、複数の画面を作成して、列の状態に基づいてさまざまな SharePoint オブジェクトを表示することができますが、同時に権限をカスタマイズしたり、リスト全体でアプリ ユーザーを圧倒することはありません。

## <a name="prerequisites"></a>前提条件

- SharePoint リストに接続する SharePoint コネクタを使用してアプリを作成しておく必要があります。
- アプリにアクセスできる 2 つのユーザー アカウント と SharePoint リストをホストするサイトが必要です。
- SharePoint リストとリスト/アイテムのアクセス許可の設定方法についての知識が必要です。

## <a name="scenario-details"></a>シナリオの詳細

SharePoint の特定の列に関数 [フィルター](../functions/function-filter-lookup.md) を使用し、特定の条件でフィルターを適用できます。 このアプローチでは、SharePoint リスト アイテムをフィルタリングして複数の画面を設定できます。

たとえば、すぐに使用できる SharePoint アプリ テンプレート **問題追跡** に基づいて、問題追跡という名前のリストを作成しました。 そして、アプリの画面に **アクティブ** な問題のみを表示するアプリを作成したいとします。 

## <a name="example"></a>例

1. すぐに使用できる SharePoint アプリ テンプレート **問題追跡** に基づいてリストを作成します。

1. 問題アイテムのいくつかのサンプルを作成します。

    ![問題追跡のサンプル アイテム](./media/scenarios-customize-view-based-on-column-status/issue-tracking-list-items.png "問題追跡のサンプル アイテム")

    問題アイテムに *アクティブ* と *終了済み* アイテムの両方があることを確認します。

1. リストをユーザー、例えば Kenny Smith、と共有します。

1. **Power Apps** アプリを選択し、SharePoint のリスト ページから **アプリの作成** を選択します。

    ![アプリの作成](./media/scenarios-customize-view-based-on-column-status/create-app.png "アプリの作成")

1. あなたはスタジオ内のアプリに記載されているすべての問題を見ることができます。

    ![問題のリスト](./media/scenarios-customize-view-based-on-column-status/app-list-of-issues.png "問題のリスト")

    サンプル リストには 2 つのアイテムしかありません。 ただし、問題の数が増えると、問題をスキャンしたり検索したりするのが困難になります。 特に、目的がアクティブな問題のみを表示することである場合。

1. 既定で BrowseGallery1 という名前のアイテム ギャラリーを選択します。

    ![アイテム ギャラリー](./media/scenarios-customize-view-based-on-column-status/select-browse-gallery.png "アイテム ギャラリー")

1. **アイテム** プロパティの式を既定に更新して、問題ステータスのフィルター条件を含めます。

    既定値:

    ```powerapps-dot
    SortByColumns(Filter([@'Issue Tracking'], StartsWith(Title, TextSearchBox1.Text)), "Title", If(SortDescending1, Descending, Ascending))
    ```

    更新先:

    ```powerapps-dot
    SortByColumns(Filter('Issue Tracking', 'Issue Status'.Value = "Active", StartsWith(Title, TextSearchBox1.Text)), "Title", If(SortDescending1, Descending, Ascending))
    ```

    式には次の関数が含まれます:

    - 列をソートする [SortByColumns](../functions/function-sort.md)。
    - アイテムをフィルター処理する [Filter](../functions/function-filter-lookup.md)。
    - 上部の検索ボックスに入力したテキストに基づいて検索できるようにする [StartsWith](../functions/function-startswith.md)。
    - 並べ替えアイコンの選択に基づいてアイテムを並べ替える [If](../functions/function-if.md)。

1. アプリを [保存して公開](../save-publish-app.md) します。

1. 別のユーザーと [アプリを共有](../share-app.md) します。 例、Kenny Smith。

1. アプリを共有したユーザー (この例では Kenny Smith) としてアプリを実行します。

    ![ユーザーが実行するアプリ](./media/scenarios-customize-view-based-on-column-status/user-runs-app.png "ユーザーが実行するアプリ")

同様に、**終了済み** 問題をすべて表示するための別画面など、列の値に基づいてアプリでさまざまな画面を使用できます。

### <a name="see-also"></a>関連項目

- Power Apps の [数式のリファレンス](../formula-reference.md)
- Power Apps の [コントロールのリファレンス](../reference-properties.md)
