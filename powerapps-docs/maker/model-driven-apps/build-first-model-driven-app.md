---
title: Power Apps を使用して初めてのモデル駆動型アプリを最初から作成する | Microsoft Docs
description: 簡単なモデル駆動型の構築する方法を学習
documentationcenter: ''
author: Mattp123
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 02/05/2019
ms.author: matp
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4c404c8aab419fa4b0445a392d7440c2ab3f099b
ms.sourcegitcommit: cf492063eca27fdf73459ff2f9134f2ca04ee766
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/17/2020
ms.locfileid: "3136149"
---
# <a name="build-your-first-model-driven-app-from-scratch"></a>モデル駆動型アプリを最初から作成する
モデル駆動型アプリの設計は、アプリ開発へのコンポーネントを重視した手法です。 このトピックでは、Power Apps 環境で使える標準エンティティの 1 つを使用してモデル駆動型アプリを作成する方法を簡略化します。

> [!TIP]
> モデル駆動型アプリを構築の詳細は、まず「[モデル駆動型アプリのコンポーネントについて](model-driven-app-components.md)」を参照してください。 

## <a name="sign-in-to-power-apps"></a>Power Apps へのサインイン
[Power Apps](https://make.powerapps.com/) にサインインします。 まだ [!INCLUDE [powerapps](../../includes/powerapps.md)] アカウントを持っていない場合、**無料で使用開始** リンクを選択します。 

## <a name="create-your-model-driven-app"></a>駆動型モデル アプリを作成する

1.    目的の環境を選択するか、[Power Apps 管理センター](https://admin.powerapps.com/) に移動して環境を作成します。

2.  **ホーム** ページで、**空のモデル駆動型アプリ** を選択します。

    > [!div class="mx-imgBorder"] 
    > <img src="media/build-first-model-driven-app/start-from-blank-model-driven.png" alt="Start from blank model" height="429" width="673">

3.  **作成**を選びます。

3.    **新しいアプリの作成** ページで、以下の情報を入力し、**完了** を選択します。 
  - **名前**: *最初のアプリ* などアプリの名前を入力します。 
  - **一意の名前**: 既定では、一意の名前は、 **名前** ボックスで指定した名前をスペースなしで使用し、その前に公開元の接頭辞とアンダースコア(_)を付けます。 例えば *crecf_Myfirstapp*。 詳細: [ソリューション発行者の接頭辞を変更する](../common-data-service/change-solution-publisher-prefix.md)
  - **説明**: *これは最初のアプリです* など、アプリに関する簡単な説明を入力します。
追加のアプリのプロパティについては、「[アプリの作成](create-edit-app.md#create-an-app)」を参照してください。

  > [!div class="mx-imgBorder"] 
  > ![新しいアプリを作成](media/create-new-app.png "新しいアプリを作成")

## <a name="add-components-to-your-app"></a>アプリにコンポーネントを追加する
アプリ デザイナーから、アプリにコンポーネントを追加します。
1.    サイトマップ デザイナーを開くには、**サイト マップ デザイナーを開く** 編集ボタンを選択します。

      > [!div class="mx-imgBorder"] 
      > ![Create-new-sitemap](media/build-first-model-driven-app/new-sitemap.png "サイト マップ デザイナー")

2.    サイトマップ デザイナーで、**新しいサブエリア** を選択し、右側のウィンドウの **プロパティ** タブを選択して、次のプロパティを選択します。
  - **種類**: エンティティ
  - **エンティティ**: 取引先企業

    > [!div class="mx-imgBorder"] 
    > ![サイトマップにコンポーネントを追加する](media/build-first-model-driven-app/sitemap.png "新しいサブエリア")

3.    **保存して閉じる** を選択します。
4.    アプリ デザイナー キャンバスで **フォーム** を選択し、右側のウィンドウの **メイン フォーム** グループで、**取引先企業** フォームを選択します。

      > [!div class="mx-imgBorder"] 
      > ![取引先企業メイン フォーム](media/build-first-model-driven-app/main-form.png "アプリ フォーム")

5.    アプリ キャンバス デザイナーで、**ビュー** を選択し、**アクティブな取引先企業**、**すべての取引先企業**、**自分のアクティブな取引先企業** ビューを選択します。<!-- All checkbox seems to be selected by default -->

      > [!div class="mx-imgBorder"] 
      > ![取引先企業ビュー](media/build-first-model-driven-app/views.png "アプリ ビュー")

6. アプリ デザイナー キャンバスで、**グラフ** を選択し、**業種別取引先企業** グラフを選択します。
7. アプリ デザイナーのツール バーで、**保存**を選択します。

      > [!div class="mx-imgBorder"] 
      > ![アプリ デザイナーのツール バーの保存](media/build-first-model-driven-app/app-designer-toolbar.png "アプリの保存")
 
<!-- ##  Validate your app
This step checks for component dependencies that are required for the app to work, but haven't yet been added to the app. 

1. On the app designer canvas, select the component that indicates a dependency, such as the **Forms** component. Then, on the right-pane select the **Required** tab, expand **Entity Dependencies** and then select all required dependencies. 

    ![Add dependencies](media/build-first-model-driven-app/resolve-dependencies.png)

2. Select **Add Dependencies**.
3. On the app designer toolbar, select **Save**.  -->

## <a name="publish-your-app"></a>アプリを公開する
アプリ デザイナーのツール バーで、**公開**を選択します。

アプリを公開すると、実行したり他のユーザーと共有する準備が整いました。

  > [!div class="mx-imgBorder"] 
  > ![簡単な取引先企業エンティティ アプリ](media/build-first-model-driven-app/accounts-quickstart-app.png "アプリの実行")

## <a name="next-steps"></a>次のステップ
このトピックでは、簡易モデル駆動型アプリを開発しました。 
- アプリを実行したときの外観を確認するには、「[モバイル デバイス上でモデル駆動型アプリを実行](../../user/run-app-client-model-driven.md)」を参照してください。
- アプリを共有する方法について詳しくは、「[モデル駆動型アプリの共有](share-model-driven-app.md)」を参照してください。
- モデル駆動型アプリを構築し始める方法の詳細は、「[モデル駆動型アプリのコンポーネントについて](model-driven-app-components.md)」を参照してください。
