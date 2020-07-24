---
title: キャンバス アプリを編集する | Microsoft Docs
description: Power Apps でキャンバス アプリの編集とセッションのロックを行うシナリオについて、詳細な手順を示します。
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/30/2020
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 2f3b3de61278fe8a75104fe74cea5b95a2b185a6
ms.sourcegitcommit: b75b29d58adf1547c9fcd3ddd1f14f69fb7f572b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/02/2020
ms.locfileid: "3330430"
---
# <a name="edit-a-canvas-app-in-power-apps"></a>Power Apps でキャンバス アプリを編集する

自分で作成した、または**共同所有者**のアクセス許可を持つキャンバス アプリを編集します。 Power Apps Studio でアプリを編集できます。 

別の場所で編集するために開かれているアプリを編集しようとすると、自分または別のユーザーがそのアプリを既に開いているという通知メッセージが表示されます。

## <a name="edit-an-app"></a>アプリの編集

1. [Power Apps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインします。

1. 左側のナビゲーション ウィンドウで、**アプリ**を選択します。

    ![アプリの一覧](./media/edit-app/file-apps.png "アプリの一覧")

1. アプリを選択します。

1. 上部メニューから**編集**を選択します。 また、アプリの "**...**" (その他のコマンド) を選択し、ドロップダウン メニューから**編集**を選択します。

    ![アプリの編集](./media/edit-app/edit-app.png "アプリの編集")

編集するアプリが表示されない場合は、正しい環境を選択していることを確認してください。

![環境の選択](./media/edit-app/select-environment.png "環境の選択")

## <a name="collaborate-on-an-app"></a>アプリでの共同作業

アプリは他のユーザーと共有できます。 アプリの**共同所有者**なら誰でも編集できます。 アプリで共同作業する場合は、次のシナリオを検討してください。

### <a name="edit-an-app-already-being-edited"></a>編集中のアプリを編集する

一度に 1 人のユーザーのみがアプリを編集できます。

他のユーザーが既に編集中であるアプリを編集しようとすると、次のメッセージが表示されます。

![別のユーザーがアプリを開いています](./media/edit-app/applock-otheruser.png "別のユーザーがアプリを開いています")

他のユーザーがアプリを閉じるまで、またはそのユーザーのセッションがタイムアウトするまで、作業を進めることはできません。

### <a name="edit-an-app-across-multiple-sessions"></a>複数のセッションでアプリを編集する

既に編集用に開いているアプリがあるとします。 次に、別のデバイスまたは別のブラウザー ウィンドウで編集するためにアプリを開こうとします。 この場合、次のメッセージが表示されます。

![同じユーザーによって、編集のために既にアプリは開かれています](./media/edit-app/applock-selfuser.png "同じユーザーによって、編集のために既にアプリは開かれています")

前のセッションを上書きすることはできますが、保存していないすべての変更が失われる可能性があります。

## <a name="next-steps"></a>次の手順

[画面](add-screen-context-variables.md)、[コントロール](add-configure-controls.md)、または[データ接続](add-data-connection.md)を追加する方法の詳細について学びます。
