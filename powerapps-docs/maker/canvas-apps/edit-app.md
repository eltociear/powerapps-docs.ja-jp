---
title: キャンバス アプリを編集する | Microsoft Docs
description: Power Apps でキャンバスアプリとセッションロックのシナリオを編集する手順について説明します。
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/19/2017
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e68d34d6a8f6b6a115bdd272235e9c5c0f155a2c
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74731560"
---
# <a name="edit-a-canvas-app-in-power-apps"></a>Power Apps でのキャンバスアプリの編集
自分で作成したキャンバス アプリ、所有しているキャンバス アプリ、または "**編集可能**" アクセス許可を持っているキャンバス アプリを編集できます。 アプリは、Power Apps Studio で編集できます。 別の場所で編集するために開かれているアプリを編集しようとすると、自分または別のユーザーがそのアプリを既に開いているという通知メッセージが表示されます。

## <a name="verify-your-permissions"></a>アクセス許可の確認
1. [Power Apps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)にサインインし、 **[ファイル]** メニュー (左端) の **[アプリ]** をクリックまたはタップします。
   
    ![[ファイル] メニューの [アプリ] オプション](./media/edit-app/file-apps.png)

2. アプリ カテゴリ セレクターで、 **[編集可能なアプリ]** をクリックまたはタップします。

    表示された一覧にある任意のアプリを編集することができます。 また、右上隅の近くにある検索ボックスに 1 つ以上の文字を入力して、アプリを検索することもできます。

    > [!NOTE]
    > 編集するアプリがまだ表示されない場合は、右上隅の近くで、正しい環境を選択していることを確認してください。
   
    ![環境の一覧](./media/edit-app/environment-list.png)

1. 編集するアプリの省略記号アイコン (...) をクリックまたはタップします。次に、 **[編集]** をクリックまたはタップします。

## <a name="collaborate-on-an-app"></a>アプリでの共同作業
アプリに対して "**編集可能**" アクセス許可を持つすべてのユーザーが、そのアプリを編集できます。ただし、アプリを編集できるユーザーは一度に 1 人だけです。 他のユーザーが既に編集中であるアプリを編集しようとすると、このメッセージが表示されます。 他のユーザーがアプリを閉じるまで (または、そのユーザーのセッションがタイムアウトするまで)、編集作業を進めることはできません。

![](./media/edit-app/applock-otheruser.png)

また、アプリを編集用に開き、そのアプリを別のデバイスまたは別のブラウザー ウィンドウで開こうとしたときにも、このメッセージが表示されます。 前のセッションをオーバーライドできますが、保存していないすべての変更が失われる可能性があります。

![](./media/edit-app/applock-selfuser.png)

## <a name="next-steps"></a>次のステップ
[画面](add-screen-context-variables.md)、[コントロール](add-configure-controls.md)、または[データ接続](add-data-connection.md)を追加する方法の詳細について学びます。

