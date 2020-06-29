---
title: テンプレートからキャンバス アプリを作成する | Microsoft Docs
description: Power Apps テンプレートに基づいて自動的にキャンバス アプリを作成するための詳細な手順です。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/29/2020
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d64b1ef3f6d885093fc9f89ecf31b785c07ea6bd
ms.sourcegitcommit: 370ca6097c2a47ef2b750ac9abbd4ee6d295bf9d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "3307741"
---
# <a name="create-a-canvas-app-from-a-template-in-power-apps"></a>Power Apps でテンプレートからキャンバス アプリを作成する

予算を追跡、休暇のスケジュール設定など、特定のシナリオ用のテンプレートに基づいて自動的にキャンバス アプリを作成し、そのアプリを実行して既定の動作を理解します。

テンプレートからアプリを作成するには、テンプレートのサンプル データを格納するクラウド ストレージ アカウント (DropBox、OneDrive、Google Drive など) が必要です。

Power Apps のライセンスがない場合は、 [無料で新規登録](../signup-for-powerapps.md) することができます。

## <a name="create-an-app"></a>アプリの作成

1. [Power Apps](https://make.powerapps.com) にサインインします。

1. 左側のナビゲーションで **アプリ**を選択します。 **新しいアプリ**のドロップダウン メニューを選択し、**キャンバス**を選択します。

    ![新しいキャンバス アプリ](./media/get-started-test-drive/new-canvas-app.png)

    これは新規タブの、[Power Apps Studio](https://docs.microsoft.com/powerapps/powerapps-overview#power-apps-for-app-makerscreators) で開きます。

1. **アプリ テンプレート** タイルで、**携帯電話レイアウト**または**タブレット PC レイアウト**を選択します。

    ![テンプレート タイルからのアプリ](./media/get-started-test-drive/template-tile.png)

1. テンプレートの一覧で、いずれかのテンプレートを選択し、右下隅にある**使用**を選択します。

    ![Power Apps テンプレートを開く](./media/get-started-test-drive/open-template.png)

    新しいタブで Power Apps Studio が開き、アプリが作成されます。

    > [!NOTE]
    > **使用**ボタンが無効になっている場合は、アプリのデータ ソースが選択されていることを確認します。 下部にある**選択**を選択すると、データ ソースを選択できます。
    >
    > ![データ ソースの選択](./media/get-started-test-drive/choose-data-source.png)

## <a name="run-the-app"></a>アプリの実行
テンプレートからアプリが既定のワークスペースに開きます。カスタマイズに伴うほとんどの作業は、このワークスペースで行うことになります。 アプリに変更を加える前に、**プレビュー** モードでアプリの動作を詳しく見てみましょう。

1. F5 キーを押して (または、右上隅にある右矢印をクリックまたはタップして)、**プレビュー** モードでアプリを開きます。

    ![プレビュー モードを開始するためのボタン](./media/get-started-test-drive/open-preview.png)

    アプリには、アプリの機能を示すサンプル データが設定されています。 たとえば、Cost Estimator アプリには、予定を作成するためのデータのほか、特定の大きさの部屋に特定の床材を設置する際にかかるコストを見積もるためのサンプル データが含まれています。

4. サンプル データを作成、更新、削除して、アプリの既定の動作を探索し、クラウド ストレージ アカウント内のデータに変更が反映されていることを確認します。

    たとえば、Cost Estimator アプリで予定を作成したり、コストの見積もりを作成したりします。

5. Esc キーを押して (または、右上隅の **X** アイコンをクリックして)、既定のワークスペースに戻ります。

## <a name="next-steps"></a>次の手順
1. Ctrl-S キーを押してアプリに名前を付けたら、**保存**をクリックまたはタップしてクラウドにアプリを保存します。

1. 組織内の他のユーザーと[アプリを共有](share-app.md) します。

> [!IMPORTANT]
> アプリを共有する前に、その相手となるユーザーがデータにアクセスできることを確認してください。 たとえば、クラウド ストレージ アカウント内の [Excel ファイルやその他のファイルを共有](share-app-data.md) する必要があります。
