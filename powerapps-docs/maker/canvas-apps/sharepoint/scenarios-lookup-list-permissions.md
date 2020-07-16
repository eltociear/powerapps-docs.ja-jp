---
title: SharePoint サイトからのルックアップ リストでアクセス許可を使用して作業する方法。  | Microsoft Docs
description: この記事では、キャンバスアプリを使用する場合に、SharePoint でルックアップ リストのアクセス許可を設定する方法について説明します。
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
ms.openlocfilehash: 9414794b12970de2434a0dfbd6bba3d470702223
ms.sourcegitcommit: 8728546925c570541bebc1ac7a24227651e8f65f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "3463842"
---
# <a name="how-to-work-with-permissions-in-a-lookup-list-from-sharepoint-site"></a>SharePoint サイトからのルックアップ リストでアクセス許可を使用して作業する方法は?

このシナリオ記事では、SharePoint リストの検索列を使用するフィールドのアクセス許可を設定する方法を説明します。 SharePoint に接続するキャンバス アプリを作成すると、アプリは SharePoint 内で設定されたアクセス許可に従います。 SharePoint 内のさまざまなレベルでの固有のアクセス許可は、キャンバス アプリの画面上にリスト、ライブラリ、アイテムを表示させる際に混乱を招く可能性があります。

このチュートリアルの例では、このような切断された継承を使用して SharePoint に接続するキャンバス アプリで作業する方法を説明しています。

## <a name="prerequisites"></a>前提条件

- SharePoint リストに接続する SharePoint コネクタを使用してアプリを作成しておく必要があります。
- SharePoint リストは、別の列の値を持つ検索列で構成される必要があります。
- アプリにアクセスできる 2 つのユーザー アカウント と SharePoint リストをホストするサイトが必要です。
- SharePoint リストとリスト/アイテムのアクセス許可の設定方法についての知識が必要です。

## <a name="scenario-details"></a>シナリオの詳細

[アクセス許可の継承を停止](https://support.office.com/en-us/article/share-sharepoint-files-or-folders-1fe37332-0f9a-4719-970e-d2578da4941c) するときに SharePoint リストまたはリスト アイテムのアクセス許可をカスタマイズできます。 異なるレベルで継承が切断されている SharePoint サイトにアプリを接続することを検討してください。 ユーザーが意図したとおりに正しい SharePoint オブジェクトにアクセスできない場合、アプリの動作が混乱する可能性があります。 ユーザーがリストを参照し、キャンバス アプリが表示するのと同じアクセス許可でオブジェクトを操作できることを確認します。

## <a name="example"></a>例

1. 1 つのリストが他のリストからのルックアップとして列を使用する 2 つの SharePoint リストを作成します。 このチュートリアルでは、2 つのリストを使用します:

    | リスト​​ | 列
    | - | - |
    | 図形 | - タイトル <br> - 色 (検索列)
    | 色 | - タイトル (図形の色)

     図形リストには色の検索列があります。 この検索列は、値の色のリストの色の列に接続されています。 代わりに独自のリストを使用することもできます。

1. 必要に応じて、サンプル アイテムを作成します:

    | 図形 | Color |
    | - | - |
    | 白丸 | 赤
    | 四角形 | 青
    | 三角形 | 緑

    図形の色は、色のリストの検索列を使用しています。

1. [Power Apps](https://make.powerapps.com) にサインインします。

1. 新しいアプリを [作成](../app-from-sharepoint.md) する。

    ![リスト項目](./media/scenarios-lookup-list-permissions/list-items.png "リスト項目")

1. アプリを [保存して公開](../save-publish-app.md) します。

1. 別のユーザーと [アプリを共有](../share-app.md) します。 例、Kenny Smith。

1. アプリを共有したユーザー (この例では Kenny Smith) としてアプリを実行します。

    ![ユーザー項目](./media/scenarios-lookup-list-permissions/user-items.png "ユーザー項目")

    SharePoint サイト、リスト、またはアイテムがユーザーと共有されていないため、アプリには利用可能なアイテムが表示されません。

1. SharePoint リスト項目にユーザー項目レベルのアクセス許可を付与します。

    ![項目レベルのアクセス許可](./media/scenarios-lookup-list-permissions/item-level-permission.png "項目レベルのアクセス許可")

1. ユーザー (この例では Kenny Smith) としてアプリを更新します。

    ![色のない図形](./media/scenarios-lookup-list-permissions/shape-without-color.png "色のない図形")

    色は別のリストからのものであり、色の列で検索されるため、ユーザー Kenny Smith は色を見ることができません。 Power Apps からアプリへのアクセス許可の変更はありません。

    > [!NOTE]
    > ユーザーが検索列を表示できる場合は、検索列リストのアクセス許可を確認してください。 検索列リストに一意のアクセス許可があり、ユーザーが追加されている場合は、次の手順をスキップできます。

1. 色リストのアクセス許可に移動し、他のユーザー、この例では Kenny Smith、を明示的に追加します。

    ![色リストのアクセス許可](./media/scenarios-lookup-list-permissions/colors-list-permissions.png "色リストのアクセス許可")

1. ユーザー (この例では Kenny Smith) としてアプリを更新します。

    ![検索後のアクセス許可](./media/scenarios-lookup-list-permissions/after-lookup-permissions.png "検索後のアクセス許可")

ご覧のように、リストとルックアップ リストの SharePoint アクセス許可は、アクセス許可の設定方法に応じて、アイテムを直接表示 (または非表示) します。

### <a name="see-also"></a>関連項目

- Power Apps の [数式のリファレンス](../formula-reference.md)
- Power Apps の [コントロールのリファレンス](../reference-properties.md)
