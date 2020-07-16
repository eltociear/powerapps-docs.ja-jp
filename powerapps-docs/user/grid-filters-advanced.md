---
title: 詳細グリッド フィルターを使用して個人用ビューを作成する | MicrosoftDocs
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 06/24/2020
ms.author: mkaur
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 9e2b19e1d38522bd073919afa37ef81feb2256df
ms.sourcegitcommit: 47fb5b8a3580ea13a93eded76c2c79394490d9f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/24/2020
ms.locfileid: "3502207"
---
# <a name="edit-or-create-personal-views-using-advanced-grid-filters"></a>詳細グリッド フィルターを使用して個人用ビューを編集または作成する 

詳細フィルター オプションを使用して、自分にとって重要なレコードを表示する個人用ビューを作成します。 詳細フィルター オプションを使用すると、単純なものから複雑なものまで、さまざまなビューを作成できます。 また、グループ化された条件や入れ子になった条件をフィルターに追加することもできます。


> [!NOTE]
> - 詳細フィルター オプションは、英語版でのみ使用できます。 今後のリリースで、より多くの言語をサポートする予定です。
> - Queues エンティティの高度なフィルター オプションが機能せず、次のエラーメッセージが表示されます：このビューのフィルター条件を表示できません。
> - 統一インターフェイスのグリッドでは、現在のビュー定義に基づいた列フィルターが事前入力されません。
> - Power Apps で作成されたパブリックビューで、**データを含む**、または**データを含まない**フィルターを含むものは、詳細検索で保存されたビューのリストには表示されません。

個人用ビューを作成して保存すると、**自分のビュー** の下の個人用ビューの一覧に表示されます。

> [!div class="mx-imgBorder"]
> ![個人用ビュー](media/my_peronsal_view.png "個人用ビュー")


## <a name="see-the-current-view-definition"></a>現在のビュー定義を確認する

現在のビューに適用されているフィルターを確認するには、ビューを選択して、**フィルター** ![フィルター アイコン](media/commandbar_filter_icon.png "フィルターアイコン") を選択します。 これにより式ビルダーが開き、既定のビュー定義が表示されます。

> [!div class="mx-imgBorder"] 
> ![現在のビュー定義](media/current_view_def.gif "この画像は、ビューのフィルターを表示する方法を示しています")

## <a name="add-conditions-to-filters"></a>フィルターに条件を追加する

1. 現在のビューを編集してさらにフィルターを追加するには、ビューを選択して、**フィルター** ![フィルター アイコン](media/commandbar_filter_icon.png "フィルターアイコン") を選択します。
2. **詳細フィルター** 画面で、式ビルダーを使用してフィルターに条件を追加します。 条件を追加する方法の詳細については、[フィルターに条件を追加する](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-edit-view-filters#add-conditions-to-a-filter) をご覧ください。
3. 終了したとき、**適用** を選択します。 

   > [!div class="mx-imgBorder"] 
   > ![フィルターの追加](media/add_filters.gif "この画像は、式ビルダーを使用してフィルターを追加する方法を示しています")

### <a name="add-grouped-or-nested-conditions"></a>グループ化された条件または入れ子になった条件を追加する

さらにデータをドリルダウンするために、グループ化された条件または入れ子になった条件をフィルターに追加することができます。 詳細については、[グループ条件をフィルターに追加する](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-edit-view-filters#add-a-group-condition-to-a-filter) をご覧ください。

   > [!div class="mx-imgBorder"] 
   > ![グループまたは入れ子になった条件を追加する](media/group_condition.gif "この画像では、グループ化された条件または入れ子になった条件をフィルターに追加する方法を示します")

### <a name="clear-filters"></a>フィルターをクリアします

適用されたフィルターをクリアして、ビューを元の定義に戻すには、**フィルターのクリア** ![フィルターのクリア アイコン](media/clear_filter_icon.png "フィルターのクリア アイコン") を選択します。

### <a name="save-your-personal-view"></a>個人用ビューを保存する

ビュー名の横のアスタリスクは、そのビューがまだ保存されていないことを示します。 

   > [!div class="mx-imgBorder"] 
   > ![未保存のビュー](media/unsaved_view.png "未保存のビュー")

1. 個人用ビューを保存するには、コマンド バーの **その他** ![その他アイコン](media/commandbar_more_icon.png "その他アイコン") を選択します。 
2. **ビューの作成** > **フィルターを新しいビューとして保存する** の順に選択します。
3. **新しいビューとして保存** ダイアログ ボックスで、ビューの名前と説明を入力し、**保存** を選択します。
4. **自分のビュー** の下の個人用ビューの一覧に、そのビューが表示されます。

   > [!div class="mx-imgBorder"] 
   > ![個人用ビューを保存する](media/save_personal_view.gif "この画像は、個人用ビューを保存する方法を示しています")


   
