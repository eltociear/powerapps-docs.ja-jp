---
title: ソリューション内でキャンバス アプリを作成する | Microsoft Docs
description: Power Apps で、ソリューション内でキャンバス アプリを作成して、アプリを別の環境にデプロイできるようにする
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: article
ms.custom: canvas
ms.reviewer: ''
ms.date: 10/23/2018
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 679dab28c49d71e8f28a9ace047b9481c4d53cc2
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3306614"
---
# <a name="create-a-canvas-app-from-within-a-solution"></a>ソリューション内からキャンバス アプリを作成する

たとえば、アプリを別の環境にデプロイする場合は、ソリューション内からアプリを作成します。 ソリューションには、アプリだけでなく、カスタマイズされたエンティティ、オプション セット、およびその他のコンポーネントを含めることができます。 ソリューション内からアプリやその他のコンポーネントを作成し、ソリューションをエクスポートして、別の環境にインポートすることで、さまざまな方法で環境をすばやくカスタマイズできます。

ソリューションの詳細については、[ソリューションの概要](../common-data-service/solutions-overview.md) を参照してください。

## <a name="prerequisite"></a>前提条件

このトピックの手順を実行するには、Common Data Service データベースを含む環境に切り替える必要があります。

## <a name="create-a-solution"></a>ソリューションの作成

アプリを作成する、またはアプリをリンクするソリューションが既にある場合は、この手順をスキップできます。

1. Power Apps に[サインイン](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) して、必要に応じて適切な環境に切り替えます。

    - ソリューション内からアプリを作成する場合は、Common Data Service データベースを含む環境に切り替えます。
    - 既存のアプリをソリューションにリンクする場合は、そのアプリを含む環境に切り替えます。

1. 左のナビゲーション バーで、**ソリューション**を選択します。

    > [!div class="mx-imgBorder"]
    > ![左のナビゲーション バーにあるソリューションのオプション](./media/add-app-solution/left-nav.png "左のナビゲーション バーにあるソリューションのオプション")

1. タイトル バーの下のバナーで、**新しいソリューション**を選択します。

    > [!div class="mx-imgBorder"]
    > ![バナーの新規ソリューションのオプション](./media/add-app-solution/banner-new-solution.png "バナーの新規ソリューションのオプション")

1. 表示されるウィンドウで、表示名、発行元、およびソリューションのバージョンを指定します。

    > [!div class="mx-imgBorder"]
    > ![新しいソリューションのオプション](./media/add-app-solution/configure-new-solution.png "新しいソリューションのオプション")

    指定した表示名に基づいて名前 (スペースなし) が自動的に生成されますが、必要に応じて生成された名前をカスタマイズできます。 これらの領域に特定のニーズがない場合は、環境には既定の発行元、バージョンには **1.0** を指定できます。

1. 左上隅にある**保存して閉じる**を選択します。

    > [!div class="mx-imgBorder"]
    > ![新しいソリューションの保存](./media/add-app-solution/save-new-solution.png "新しいソリューションの保存")

## <a name="create-a-canvas-app-in-a-solution"></a>ソリューション内でキャンバス アプリを作成する

ソリューション内から空のキャンバス アプリを作成することができます。 ソリューション内から 3 画面アプリを自動的に生成したり、テンプレートやサンプル アプリをカスタマイズしたりすることはできません。

1. Power Apps に[サインイン](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) します。

1. 必要に応じて、キャンバス アプリを作成するソリューションを含む環境に切り替えます。

1. 左のナビゲーション バーで、**ソリューション**を選択します。

    > [!div class="mx-imgBorder"]
    > ![左のナビゲーション バーにあるソリューションのオプション](./media/add-app-solution/left-nav.png "左のナビゲーション バーにあるソリューションのオプション")

1. ソリューションの一覧で、キャンバス アプリを作成するソリューションを選択します。

1. タイトル バーの下のバナーで、**新着** > **アプリ** > **キャンバス アプリ**を選択して、作成するアプリのフォーム ファクター (携帯電話またはタブレット) を選択します。

    > [!div class="mx-imgBorder"]
    > ![ソリューションでアプリを作成するためのオプション](./media/add-app-solution/new-option.png "ソリューションでアプリを作成するためのオプション")

    Power Apps Studio は、別のブラウザー タブに空白のキャンバスで開きます。

1. アプリを作成して (または少なくとも 1 つの変更を加えて)、変更を保存します。

1. ソリューションを選択したブラウザー タブで、**完了**を選択してソリューションのコンポーネントの一覧を更新します。

    > [!div class="mx-imgBorder"]
    > ![完了ボタン](./media/add-app-solution/done-button.png "完了ボタン")

    新しいアプリが、そのソリューションのコンポーネントの一覧に表示されます。 アプリへの変更を保存すると、ソリューションに含まれているバージョンに反映されます。

## <a name="link-an-existing-canvas-app-to-a-solution"></a>既存のキャンバス アプリをソリューションにリンクする

アプリをソリューションにリンクする場合は、両方が同じ環境にあり、アプリがソリューション内から作成されている必要があります。

1. Power Apps に[サインイン](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) します。

1. 必要に応じて、アプリをリンクするソリューションを含む環境に切り替えます。

1. 左のナビゲーション バーで、**ソリューション**を選択します。

    > [!div class="mx-imgBorder"]
    > ![左のナビゲーション バーにあるソリューションのオプション](./media/add-app-solution/left-nav.png "左のナビゲーション バーにあるソリューションのオプション")

1. ソリューションの一覧で、アプリをリンクするソリューションを選択します。

1. タイトル バーの下のバナーで、**既存の追加** > **アプリ** > **キャンバス アプリ**を選択します。

    > [!div class="mx-imgBorder"]
    > ![既存のアプリをリンクするためのバナーのオプション](./media/add-app-solution/add-existing.png "既存のアプリをリンクするためのバナーのオプション")

    この環境のソリューション内で作成されたキャンバス アプリの一覧が表示されます。

1. アプリの一覧からソリューションにリンクするアプリを選択して、**追加**を選択します。

    > [!div class="mx-imgBorder"]
    > ![追加ボタン](./media/add-app-solution/add-button.png "\[Add\] (追加) ボタン")

## <a name="known-limitations"></a>既知の制限

既知の制限については、[Power Apps ソリューションを使用する](../common-data-service/use-solution-explorer.md#known-limitations) を参照してください。 

## <a name="next-steps"></a>次の手順

- その他のアプリ、およびエンティティ、フロー、ダッシュボードなどの[その他のコンポーネント](../common-data-service/use-solution-explorer.md) をソリューションに作成またはリンクします。
- 別の環境や AppSource にデプロイできるように[ソリューションをエクスポート](../common-data-service/import-update-export-solutions.md) します。
