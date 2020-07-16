---
title: SharePoint リストの検索列からの選択肢を含むドロップダウン リストの使用方法 | Microsoft Docs
description: この記事では、アプリのドロップダウン リストを使用して、SharePoint リストの検索列の選択肢を表示する方法について説明します。
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
ms.openlocfilehash: f4e98dc6e5e50dc5cdd4096dbe8c89d08725bc80
ms.sourcegitcommit: 8728546925c570541bebc1ac7a24227651e8f65f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "3463841"
---
# <a name="how-to-use-drop-down-list-with-choices-from-lookup-column-in-a-sharepoint-list"></a>SharePoint リストで検索列からの選択肢を含むドロップダウン リストを使用するには?

このシナリオ記事では、SharePoint リストで検索列からの選択肢を含むドロップダウン リストの使用方法について説明します。

## <a name="prerequisites"></a>前提条件

- SharePoint リストに接続する SharePoint コネクタを使用してアプリを作成しておく必要があります。
- SharePoint リストは、別の列の値を持つ検索列で構成される必要があります。

## <a name="scenario-details"></a>シナリオの詳細

SharePoint では他のリストやライブラリからの値を使用する検索列を使用できます。

そのような列をキャンバス アプリのフィールドとして使用する場合、選択肢のあるドロップダウン リストを使用できます。

ドロップダウン リストの選択肢を使用するには、関数 [Choices](../functions/function-choices.md) を使用する必要があります。 例えば、`Choices([@'Vehicle registration'].Vehicle_x0020_type)` は、SharePoint リスト **車両登録** と列 **車両のタイプ** を使用して、車両タイプを検索します。

## <a name="example"></a>例

1. [Power Apps](https://make.powerapps.com) にサインインします。

1. 新しいアプリを [作成](../app-from-sharepoint.md) するか、既存のアプリを [編集](../edit-app.md) します。

    > [!NOTE]
    > 前提条件で説明されているように、アプリが SharePoint 接続を使用し、SharePoint リストに接続していることを確認します。

1. 左側のペインから **+** (挿入) を選択します。

1. **ドロップダウン** を選択します。

    ![ドロップダウンの挿入](./media/scenarios-choice-to-lookup/insert-drop-down.png "ドロップダウンの挿入")

1. **アイテム** プロパティを次の式で更新します:

    `Choices([@'Vehicle registration'].Vehicle_x0020_type)`

    **車両登録** を SharePoint リストの名前に、**車両のタイプ** をリスト内の検索列の名前に置き換えます。

    ![Choices 式](./media/scenarios-choice-to-lookup/choices-formula.png "Choices 式")

1. アプリを再生するか、キーボードの **Alt** キーを押して、ドロップダウンを選択します。

    ![ドロップダウンの選択肢](./media/scenarios-choice-to-lookup/drop-down-choices.png "ドロップダウンの選択肢")

### <a name="see-also"></a>関連項目

- Power Apps の [数式のリファレンス](../formula-reference.md)
- Power Apps の [コントロールのリファレンス](../reference-properties.md)
