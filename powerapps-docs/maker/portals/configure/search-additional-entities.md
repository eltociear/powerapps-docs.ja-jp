---
title: Power Apps ポータルの追加エンティティに対するグローバル検索 | MicrosoftDocs
description: ポータルで追加エンティティに対するグローバル検索がどのように機能するかを説明します。
author: sandhangitmsft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 04/28/2020
ms.author: sandhan
ms.reviewer: tapanm
ms.openlocfilehash: 1404b91fe6380d85dc93bc513ad3185dc2c91501
ms.sourcegitcommit: c12260f372ad2cc48d3146be570d2088c9ef1d86
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2020
ms.locfileid: "3494067"
---
# <a name="walkthrough-configuring-additional-entitiesforglobalsearch"></a>チュートリアル: グローバル検索の追加エンティティの構成  

## <a name="overview"></a>概要

検索機能の追加エンティティを有効にできます。 追加エンティティの検索を構成するには、この記事で説明される追加のアクションが必要になります。

グローバル検索の追加エンティティを構成する場合は、次の考慮事項が適用されます:

- 追加エンティティの検索用 [サイト設定](#site-setting-for-additional-entities) が有効になっていることを確認します。
- 検索を有効にする追加のエンティティの **ポータル検索**という名前のビューを作成します。 詳細: [グローバル検索で検索可能なフィールド](search.md#fields-searchable-in-global-search)
- 読み取り特権、および検索結果に表示されるレコードの適切なスコープを提供する**エンティティのアクセス許可**が作成されていることを確認します。
- エンティティのアクセス許可を必要な **Web ロール**に関連付けます。
- エンティティの匿名検索を許可する場合は、エンティティのアクセス許可を**匿名 Web ロール**に関連付ける必要があります。
- 検索結果を表示する [検索結果ページ](#results-page-for-additional-entities) を構成します。

上記の明示的な構成により、グローバル検索で誤ってレコードが使用可能になることはありません。

### <a name="site-setting-for-additional-entities"></a>追加エンティティのサイト設定

検索用に追加のエンティティを構成する際、サイト設定 **Search/EnableAdditionalEntities** が必要になります。

> [!IMPORTANT]
> **Search/EnableAdditionalEntities** は、追加のエンティティの検索を明示的に有効にするためのものです。 検索機能を使用する場合、主な検索サイト設定**検索/有効**を **true** に設定する必要があります。

既定のエンティティの検索構成と同様に、他の関連サイト設定も構成できます。 たとえば、**検索/フィルター** 設定を使用して、追加のエンティティを構成し、ドロップダウン フィルター オプションをグローバル検索に追加できます。 詳細: [サイト設定](search.md#related-site-settings)

### <a name="results-page-for-additional-entities"></a>追加エンティティの結果ページ

検索結果ページは、```<entitylogicalname>_SearchResultPage``` という名前の**サイト マーカー**経由で構成されます。

たとえば、エンティティの論理名が *nwind_products* の場合、サイト マーカーは ```nwind_products_SearchResultPage``` になります。 サイト マーカーの値は、その検索結果が選択されたときに開くページです。 既定では、レコード ID は *ID* クエリ文字列のパラメータで検索結果ページに渡されます。

検索結果ページにエンティティ フォームがあること、または検索結果の詳細を表示するロジックが記述されていることを確認してください。

## <a name="walkthrough---configure-search-for-additional-entities-with-sample-database"></a>チュートリアル - サンプル データベースで追加エンティティの検索を構成する

次のチュートリアルでは、Common Data Service で使用できるサンプル データベース **Northwind** の**受注製品**エンティティの検索を有効にする方法を説明します。

サンプル データベースの詳細については、[Northwind Traders データベースとアプリをインストールする](../../canvas-apps/northwind-install.md) を参照してください。

> [!TIP]
> *nwind_products* エンティティ名とエンティティの論理名を置き換えることで、選択したエンティティを使用してチュートリアルを実行できます。

## <a name="step-1-add-or-update-search-site-settings"></a>手順 1: 検索サイト設定を追加または更新する

1. [Power Apps](https://make.powerapps.com) にサインインします。

1. ポータルが存在する適切な環境にいることを確認してください。

1. 左側のナビゲーション ウィンドウで**アプリ**を選択し、 **ポータル管理** モデル駆動型アプリを見つけます。  

    ![ポータル管理](media/search-additional-entities/portal-management.png "ポータル管理")

    >[!NOTE]
    > Dynamics 365 アプリケーションがインストールされている環境にいる場合、ポータル管理アプリは **Dynamics 365ポータル**という名前になる場合があります。

1. **ポータル管理**アプリを選択して開いてから、左側のナビゲーション ウィンドウで**サイト設定** に移動します。

1. 新しい設定 **Search/EnableAdditionalEntities** を作成し、その値を **true** に設定します。

    ![EnableAdditionalEntities のサイト設定](media/search-additional-entities/enableadditionalentitiessearch-sitesetting.png "EnableAdditionalEntities のサイト設定")

1. **検索/フィルター**設定を作成または更新し、値  **Products:nwind_products** を追加します。

    ![サイト設定の検索/フィルター](media/search-additional-entities/search-filters.png "サイト設定の検索/フィルター")

## <a name="step-2-create-or-verify-the-portal-search-view"></a>手順 2: ポータル検索ビューを作成または確認する

> [!NOTE]
> 次の手順では、[Northwind Traders ソリューション](../../canvas-apps/northwind-install.md) をインストールする必要があります。 別のエンティティを使用する場合は、適切なソリューションまたは既定のソリューションを使用します。

1. [Power Apps](https://make.powerapps.com) に移動し、左側のナビゲーション ウィンドウから**ソリューション**を選択します。

1. **Northwind Traders** を選択します。

    ![ソリューションの選択](media/search-additional-entities/select-solution.png "ソリューションの選択")

1. **受注製品**エンティティを検索します。

    ![受注製品エンティティ](media/search-additional-entities/order-product.png "受注製品エンティティ")

1. **受注製品**エンティティを選択してから、**ビュー**を選択します。

    ![ビュー](media/search-additional-entities/views.png "ビュー ")

1. ビュー リストに**ポータル検索**が表示されていることを確認します。

    ![ポータル検索ビュー](media/search-additional-entities/portal-search.png "ポータル検索ビュー")

    ポータル検索ビューがまだ存在しない場合は、**ビューの追加**を選択し、**ポータル検索**として名前を入力してから、**作成**を選択します。

    ![ビューの追加](media/search-additional-entities/add-view.png "ビューの追加")

    ![ポータル検索ビューの追加](media/search-additional-entities/portal-search-view.png "ポータル検索ビューの追加")

1. 検索用に適切な列がビューに追加されていることを確認します。

    ![列を追加する](media/search-additional-entities/add-columns.png "列を追加する")

1. ビューを編集した場合は、必ず**保存**を選択してから、続行する前に**公開**します。

    ![保存して公開](media/search-additional-entities/save-publish.png "ビューを保存して公開")

## <a name="step-3-create-entity-permissions"></a>手順 3: エンティティのアクセス許可を作成する

1. [Power Apps](https://make.powerapps.com) にサインインします。

1. 左側のナビゲーション ウィンドウで**アプリ**を選択してから、 **ポータル管理** モデル駆動型アプリを選択して開きます。  

1. 左のナビゲーション ウィンドウで、**エンティティのアクセス許可**を選択します。

1. **新規**を選択します。

    ![新しいエンティティのアクセス許可レコード](media/search-additional-entities/new-entity-permission.png "[新しいエンティティのアクセス許可レコード")

1. **Northwind 製品すべて読み取り**として名前を入力してから、適切な**スコープ**および**読み取り**特権を選択します。

    この例では、**グローバル** スコープは **nwind_products** エンティティに提供されています。

    ![スコープと読み取り権限](media/search-additional-entities/scope-read.png "スコープと読み取り権限")

1. **保存して閉じる**を選択します。

1. **Northwind 製品すべて読み取り**を選択して開きます。

1. **Web ロール** セクションまで下方向にスクロールしてから、**既存の Web ロールの追加**を選択します。

    ![既存の Web ロールの追加](media/search-additional-entities/add-existing-web-role.png "既存の Web ロールの追加")

1. **認証されたユーザー**を検索してから、**追加**を選択します:

    ![認証されたユーザーの追加](media/search-additional-entities/add-authenticated-users.png "認証されたユーザーの追加")

## <a name="step-4-add-a-webpage"></a>手順 4: Web ページを追加する

1. [Power Apps](https://make.powerapps.com) に移動してから、左側のナビゲーション ウィンドウで**アプリ**を選択します。

1. ポータルの**その他のコマンド** (…) を選択してから、**編集**を選択して Power Apps Studio でポータルを開きます。

1. 左上隅のメニューから**新しいページ**を選択してから、ページの**空白**レイアウトを選択します。

    ![新しいページ](media/search-additional-entities/new-page.png "新しいページ")

1. Web ページ名を**受注製品**として入力します。 このページは、検索結果ページとして構成されます。

1. 左側のナビゲーション ウィンドウで**コンポーネント**を選択してから、この Web ページの**フォーム** コンポーネントを追加します。

    ![フォーム コンポーネントの追加](media/search-additional-entities/form-component.png "フォーム コンポーネントの追加")

1. ワークスペースの右側にある**既存のものを使用**オプションを選択し、**nwind_products** エンティティの**製品の表示**フォームを選択してから、**モード**を**読み取り専用**に設定します。

    ![モードの設定](media/search-additional-entities/mode.png "モードの設定")

## <a name="step-5-add-a-site-marker-for-the-search-results-details-page"></a>手順 5: 検索結果の詳細ページにサイト マーカーを追加する

1. [Power Apps](https://make.powerapps.com) にサインインします。

1. 左側のナビゲーション ウィンドウで**アプリ**を選択し、 **ポータル管理** モデル駆動型アプリを選択して開きます。  

1. 左側のナビゲーション ウィンドウから**サイト マーカー**を選択します。

1. **新規**を選択してから、次の詳細を使用して新しいサイト マーカーを作成します:

    - **名前:** **nwind_products_SearchResultPage**
    - **ページ:** **受注製品**
    
    ![新しいサイト マーカー](media/search-additional-entities/new-site-marker.png "新しいサイト マーカー")

## <a name="step-6-rebuild-the-search-index"></a>手順 6: 検索インデックスを再作成する

1. 管理者 Web ロールが割り当てられているユーザー アカウントを使用してポータルを参照します。

1. アドレス バーの URL に **/_services/about** を追加してから、**入力**を選択します。

   ![_services_about ページ](media/search-additional-entities/services-about.png "_services_about ページ")

1. [キャッシュのクリア](https://docs.microsoft.com/powerapps/maker/portals/admin/clear-server-side-cache)を選びます。

1. キャッシュをクリアした後、[検索インデックスの再作成](search.md#rebuild-full-search-index) を選択します。

## <a name="step-7-verify-that-global-search-works-with-the-custom-entity"></a>手順 7: グローバル検索がユーザー定義エンティティで機能することを確認する

1.  *認証済み* **Web ロール** が割り当てられたユーザーでポータルを参照します。

1. 検索ツールバーまたは検索ページに移動して、既知のレコードを検索します。

   たとえば、検索キーワード **ノースウィンド クラムチャウダー**を使用して、**nwind_products** エンティティに関連付けられている結果を表示します。

   ![検索結果](media/search-additional-entities/search-results.png "検索結果")

## <a name="next-steps"></a>次のステップ

[グローバル検索からのエンティティの削除](search.md#remove-an-entity-from-global-search)

### <a name="see-also"></a>関連項目

[関連サイトの設定の検索](search.md#related-site-settings)