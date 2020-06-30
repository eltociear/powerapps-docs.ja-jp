---
title: Power Apps ポータルを使用してエンティティを作成、編集する | MicrosoftDocs
description: Power Apps ポータルを使用してエンティティを作成および編集する方法について
ms.custom: ''
ms.date: 05/30/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
author: Mattp123
ms.assetid: fa04f99d-a5f9-48cb-8bfb-f0f50718ccee
caps.latest.revision: 41
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 924fd4107a330a82f3efdbe8ac2f934dffa1bf19
ms.sourcegitcommit: 4b6f187c9501332f9acca5978fa326621f2980e5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/22/2020
ms.locfileid: "3394684"
---
# <a name="create-and-edit-entities-using-power-apps-portal"></a>Power Apps ポータルを使用してエンティティを作成、編集する

[Power Apps ポータル](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) では、  Common Data Service のエンティティを簡単に作成、編集することができます。

ポータルでは一般的なオプションのほどんとを構成できますが、特定のオプションはソリューション エクスプローラーを使用してのみ設定できます。 詳細: 
- [Common Data Serviceでエンティティを作成、編集する](create-edit-entities.md)
- [ソリューション エクスプローラーを使用してエンティティを作成および編集する](create-edit-entities-solution-explorer.md)

## <a name="view-entities"></a>エンティティの表示

1. [Power Apps ポータル](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) から、**データ** > **エンティティ** を選択します。

    > [!div class="mx-imgBorder"] 
    > ![エンティティの表示](media/view-entities-portal.png)

一覧の次のビューを使用して表示されたエンティティをフィルター処理できます。 

  > [!div class="mx-imgBorder"] 
    > ![エンティティ ビュー](media/entity-views-portal.png)

 |ビュー|説明|
 |--|--|
 |**すべて**| すべてのエンティティを表示します|
 |**マネージド**| 管理エンティティと標準エンティティのみを表示します|
 |**ユーザー定義**|ユーザー定義エンティティのみ表示します|
 |**既定**|標準エンティティのみ表示します |

それらに適用される **タグ** によってエンティティをグループ化するために **グループ** を選択することもできます。

## <a name="create-an-entity"></a>エンティティの作成

[エンティティを表示](#view-entities)しながら、メニュー バーで **新しいエンティティ** を選択します。 これには、[新しいエンティティ] パネルが開きます。

  > [!div class="mx-imgBorder"] 
    > ![新しいエンティティ パネル](media/new-entity-panel.png)

以下のフィールドにデータを入力

|フィールド|説明|
|--|--|
|**表示名**|これは、アプリに表示されるエンティティの単数形の名前です。 これは後で変更できます。|
|**表示名の複数形**|これは、アプリに表示されるエンティティの複数形の名前です。 これは後で変更できます。|
|**名前**|このフィールドは、ユーザーが入力する**表示名**に基づいて事前設定されます。 これには、 Common Data Service ソリューション発行者のカスタマイズ接頭辞が含まれます。 エンティティが保存されたら、これを変更できません。|
|**プライマリ名**|これは、この時点で表示される唯一のフィールドです。| フィールドの **表示名** または **名前** を変更したい場合は編集してください。
|**表示名**|これは、レコードのメインのわかりやすいテキスト識別子です（通常は名前または番号）。 このフィールドの値は、ユーザーがレコードを一覧から選択する必要がある場合に表示されます。
|**名前**|このフィールドは、ユーザーが入力する**表示名**に基づいて事前設定されます。 これには、 Common Data Service ソリューション発行者のカスタマイズ接頭辞が含まれます。 エンティティが保存されたら、これを変更できません。|

**添付ファイルを有効にする**を選択し、このエンティティのレコードにメモとファイルを追加します。

**その他の設定**を選択します。 これらの設定は、エンティティのオプションです。

|フィールド|説明|
|--|--|
|**説明**|エンティティの目的を示すわかりやすい説明を入力してください。|
|**エンティティの種類と所有権**|エンティティのタイプを活動エンティティに切り替えて、タスク管理をするエンティティを作成します。 **所有権** の種類によって、レコードを操作できるユーザーが決まります。|
|**共同作業**|さまざまな機能を有効化することで、ユーザーがより簡単に共同作業できるようになります。|
|**設定の作成と更新**|フォームの簡易作成を有効にして、アプリに合理化されたデータ入力のエクスペリエンスを提供できます。 重複検出では、重複検出ポリシーを設定し、重複を検出する規則を作成できます。 変更の追跡により、効率的にデータの同期を維持できます。|
|**Dynamics 365 for Outlook**|このエンティティが Outlook でどのように表示されるかを構成します。|

**作成** を選択して続行します。**新しいエンティティ** パネルが閉じてフィールドの一覧が表示されます。

エンティティの **プライマリ名** フィールドがフィールドの一覧に表示されます。 フィールドの **表示名** または **名前** を変更する場合は、**プライマリ名** フィールドを選択して編集します。 既定値は、以下に表示されます。

  > [!div class="mx-imgBorder"] 
    > ![[プライマリ名] パネル](media/primary-name-panel.png)

## <a name="edit-an-entity"></a>エンティティの編集

[エンティティを表示](#view-entities)しているときに、編集するエンティティを選択します。

エンティティの **表示名**、 **表示名の複数形** 、**説明** を編集する場合は、メニューから **設定** を選択します。

  > [!div class="mx-imgBorder"] 
    > ![エンティティ設定](media/entity-settings-portal.png)

他の項目については、タブから選択します。

### <a name="fields"></a>フィールド

詳細については、[フィールドの作成および編集](create-edit-fields.md)を参照してください

### <a name="relationships"></a>関係

「[エンティティ間の関連付けの作成と編集](create-edit-entity-relationships.md)」を参照

### <a name="business-rules"></a>業務ルール

「[フォームにロジックを適用するために業務ルールおよびビジネス レコメンデーションを作成する](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md)」を参照

### <a name="views"></a>[ビュー]

「[ビューの作成または編集](../model-driven-apps/create-edit-views.md)」を参照

### <a name="forms"></a>フォーム

「[フォームの作成および設計](../model-driven-apps/create-design-forms.md)」を参照

### <a name="dashboards"></a>ダッシュボード

「[ダッシュボードの作成または編集](../model-driven-apps/create-edit-dashboards.md)」を参照

### <a name="charts"></a>グラフ

「[システム グラフの作成](../model-driven-apps/create-edit-system-chart.md)」を参照

### <a name="keys"></a>キー

「[レコードを参照する代替キーの定義](define-alternate-keys-reference-records.md)」を参照

### <a name="data"></a>データ

エンティティ内のデータを表示します。
エンティティの使用できるビューから選択したり、すべてのフィールドを表示するには、**ビューの選択** メニューを使用します。

  > [!div class="mx-imgBorder"] 
    > ![ビューの選択](media/entity-data-select-view.png)

そのほかのデータを表示するには、フォームの下部の **次のページ** と **前のページ** コマンドを使用します。

## <a name="delete-an-entity"></a>エンティティの削除

システム管理者のセキュリティ ロールを持つユーザーとして、管理ソリューションの一部でないユーザー定義エンティティを削除できます。  
  
> [!IMPORTANT]
>  ユーザー定義エンティティを削除すると、そのエンティティのデータを保存しているデータベース テーブルが削除され、それらのテーブルに含まれるすべてのデータが失われます。 ユーザー定義エンティティと上位下位の関連付けのある関連レコードも削除されます。 上位下位の関連付けの詳細については、「[エンティティ間の関連付けの作成と編集](create-edit-entity-relationships.md)」を参照してください。  
  
> [!NOTE]
> 削除されたエンティティからのデータを回復する唯一の方法は、エンティティが削除される前の時点からデータベースを復元します。 詳細については、「[インスタンスのバックアップと復元](/dynamics365/customer-engagement/admin/backup-restore-instances)」を参照してください。

[エンティティを表示](#view-entities)した状態で、エンティティを選択し、メニューから **エンティティの削除** を選択します。

  > [!div class="mx-imgBorder"] 
    > ![Power Apps ポータルを使用してエンティティを削除する](media/delete-entity-powerapps-portal.png)

削除を防止する依存関係がエンティティにする場合は、エラー メッセージが表示されます。 依存関係を特定および削除するには、ソリューション エクスプローラーを使用する必要があります。 詳細については、「[エンティティの依存関係の特定](create-edit-entities-solution-explorer.md#identify-entity-dependencies)」を参照してください

### <a name="see-also"></a>関連項目

[Common Data Serviceでエンティティを作成、編集する](create-edit-entities.md)<br />
[ソリューション エクスプローラーを使用してエンティティを作成および編集する](create-edit-entities-solution-explorer.md)


