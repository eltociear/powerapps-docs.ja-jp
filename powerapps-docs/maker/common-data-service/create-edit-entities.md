---
title: Common Data Service でエンティティ間の関連付けの作成と編集をする | MicrosoftDocs
description: エンティティの作成および編集する方法に関する説明
ms.custom: ''
ms.date: 04/16/2019
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
ms.openlocfilehash: ba8fe12a9ecffa0ffb1116546d2bfe9ab2c62ac8
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "2758065"
---
# <a name="create-and-edit-entities-in-common-data-service"></a>Common Data Serviceでエンティティを作成、編集する

ユーザー定義エンティティを作成する場合は、その前に、既存のエンティティの使用が要件を満たしているかどうかを確認します。 詳細: [新しいメタデータを作成するか既存のメタデータを使用するか](create-edit-metadata.md#create-new-metadata-or-use-existing-metadata)

エンティティを作成するために使用できる 2 つのデザイナーがあります:

|デザイナー| 説明|
|--|--|
|[PowerApps ポータル](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|簡単な優れたエクスペリエンスを提供しますが、一部の特殊な設定は使用できません。<br />詳細: <br />[チュートリアル: PowerApps でのコンポーネントがあるユーザー定義エンティティの作成](/powerapps/maker/common-data-service/create-custom-entity)<br />[PowerApps ポータルを使用してエンティティを作成、編集する](create-edit-entities-portal.md)|
|ソリューション エクスプローラー|簡単ではありませんが、一般的な要件が少ない割に柔軟性が高くなっています。 <br />詳細 [ソリューション エクスプローラーを使用してエンティティを作成および編集する](create-edit-entities-solution-explorer.md)|

> [!NOTE]
> 以下を使用して、環境にエンティティを作成することもできます:
> - エンティティの定義を含むソリューションをインポートします。
> - Power Query を使用して、新しいエンティティを作成しデータを入力します。 詳細については、 [Power Query を使用して Common Data Service のエンティティにデータを追加する](/powerapps/maker/common-data-service/data-platform-cds-newentity-pq)を参照してください。
> - 開発者は[メタデータ サービス](/powerapps/developer/common-data-service/use-web-services#metadata-services)を使用してプログラムを作成できます。


## <a name="entity-options-not-available-in-the-powerapps-portal"></a>PowerApps ポータルで使用できないエンティティ オプション

このトピックの情報は、使用できるデザイナーの選択に役立ちます。 次のいずれかの要件に対処する必要がない限り、  PowerApps ポータルを使用してエンティティを作成することができます。

- カスタマイズの接頭辞を制御する

  作成するユーザー定義エンティティの名前の一部はカスタマイズの接頭辞です。 これは、作業中のソリューションの発行者に基づいて設定されます。 カスタマイズの接頭辞に注意を払う場合は、カスタマイズの接頭辞がこのエンティティに対して必要な接頭辞であるアンマネージド ソリューションで作業するようにします。 詳細: [ソリューション発行者の接頭辞を変更する](change-solution-publisher-prefix.md)。

- 組織所有エンティティを作成する

  既定では、 PowerApps ポータルは、 **ユーザーまたはチーム** が所有するエンティティを作成します。 **組織**の所有権を設定するには、ソリューション エクスプローラーを使用します。 詳細情報: [エンティティの所有権](types-of-entities.md#entity-ownership)

- アクティビティ エンティティの作成

  活動エンティティは、カレンダーにエントリを作成できるアクションを追跡するエンティティに関する特別な種類です。 詳細: [活動エンティティ](types-of-entities.md#activity-entities)。

- ユーザー定義エンティティのアイコンを変更する

  既定では、モデル駆動型アプリのすべてのユーザー定義エンティティは同じアイコンを使用します。 カスタム エンティティに必要なアイコンのイメージ Web リソースを作成できます。 詳細:  [カスタム エンティティのアイコンを変更する](../model-driven-apps/change-custom-entity-icons.md) 

- 有効にすることができるのは、次のプロパティ変更です:

  [!INCLUDE [cc_entity-set-once-options-table](../../includes/cc_entity-set-once-options-table.md)]

- 次のプロパティのいずれかを変更します:

  |オプション   |説明  |
  |---------|---------|
  |**アクセス チーム**|このエンティティのチーム テンプレートを作成します。 |
  |**簡易作成を許可**|このエンティティの**簡易作成フォーム**を作成して公開すると、ナビゲーション ウィンドウの**作成**ボタンを使用して新しいレコードを作成するオプションを使用できます。 詳細情報: [フォームの作成と設計](../model-driven-apps/create-design-forms.md)<br /><br /> これがユーザー定義活動エンティティに対して有効になると、ナビゲーション ウィンドウの**作成**ボタンを使用するときに、ユーザーが定義した活動が活動エンティティのグループに表示されます。 ただし、活動は簡易作成フォームをサポートしていないので、カスタム エンティティ アイコンをクリックしたときは、メイン フォームが使用されます。|
  |**このエンティティが表示される領域**|Web アプリケーションでこのエンティティを表示するために利用可能なサイトマップ領域の 1 つを選択します。 これはモデル駆動型アプリには適用されません。|
  |**監査**|監査が組織に対して有効になっている場合、エンティティ レコードの変化を時系列で取得することができます。 エンティティの監査を有効にすると、そのエンティティのすべてのフィールドの監査も有効になります。 監査を有効にするフィールドを選択またはクリアできます。|
  |**変更履歴**|データが最初に抽出されてから、または最後に同期されてからどのデータが変更されたかを検出することによって、効率の良いデータ同期を可能にします。  |
  |**色**|モデル駆動型アプリでエンティティに使用する色を設定します。|
  |**ドキュメント管理**|組織のドキュメント管理を有効にするための他のタスクの実行が完了すると、この機能を有効にすることによって、このエンティティは SharePoint との統合に関与できるようになります。 |
  |**重複データ検出**|重複データ検出が組織に対して有効になっている場合、このオプションを有効にすることによって、このエンティティの重複データ検出ルールを作成できます。|
  |**モバイルの有効化**|このエンティティを、Dynamics 365 for phones と Dynamics 365 for tablets のアプリで使用できるようにします。 また、このエンティティを**モバイルでは読み取り専用**にすることも選択できます。<br /><br /> エンティティのフォームで、Dynamics 365 for phones と Dynamics 365 for tablets のアプリでサポートされていない拡張機能が必要な場合は、この設定を使用して、これらのエンティティのデータをモバイル アプリ ユーザーが編集できないようにします。|
  |**Phone Express の有効化**|このエンティティを、Dynamics 365 for phones アプリで使用できるようにします。|
  |**差し込み印刷**|差し込み印刷でこのエンティティを使用できます。|
  |**Dynamics 365 for Outlookのオフライン機能**|Dynamics 365 for Outlook アプリケーションがネットワークに接続されていないときに、このエンティティー内のデータ使用の可否。|
  |**Dynamics 365 for Outlookの閲覧ウィンドウ**|Dynamics 365 for Outlook アプリケーションの閲覧ウィンドウにおけるエンティティの表示の有無。|
  |**カスタム ヘルプを使用する**|有効にした場合、ヘルプ URL を設定して、ユーザーがアプリケーションのヘルプ ボタンをクリックしたときに表示されるページをコントロールします。 これを使用して、エンティティの企業プロセスに特有のガイダンスを提供します。|


### <a name="see-also"></a>関連項目

[ソリューション エクスプローラーを使用してエンティティを作成および編集する](create-edit-entities-solution-explorer.md)<br />
[チュートリアル: PowerApps でのコンポーネントがあるユーザー定義エンティティの作成](/powerapps/maker/common-data-service/create-custom-entity)<br />
[エンティティの編集](edit-entities.md)<br />
[開発者ドキュメント: ユーザー定義エンティティを作成する](/dynamics365/customer-engagement/developer/org-service/create-custom-entity)
