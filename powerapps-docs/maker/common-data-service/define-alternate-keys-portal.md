---
title: Power Apps ポータルを使用した代替キーを定義する | MicrosoftDocs
description: Power Apps ポータルを使用した代替キーを定義する方法
ms.custom: ''
ms.date: 06/11/2020
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 86f2f1d700c978ab3400395b6c7c71a21ca08841
ms.sourcegitcommit: 3bc94ac014b12d2b04a1af598d38b875e9e5dc2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2020
ms.locfileid: "3444237"
---
# <a name="define-alternate-keys-using-power-apps-portal"></a>Power Apps ポータルを使用した代替キーの定義

[Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) Common Data Service でエンティティの代替キーを簡単に表示、作成する方法を提供します。 代替キーの使用に関する詳細については、[レコードの参照に使用する代替キーを定義する](define-alternate-keys-reference-records.md) を参照してください。

Power Apps では最も一般的なオプションを設定できますが、特定のオプションはソリューション エクスプローラを使用してのみ設定できます。 詳細: [ソリューション エクスプローラーを使用した代替キーの定義](define-alternate-keys-solution-explorer.md)

> [!IMPORTANT]
> 代替キーで使用されるフィールド内のデータに /,<,>,*,%,&,:,\ などの文字が含まれている場合は、get アクションまたは patch アクションは機能しません。 一意性のみを必要とする場合はこの方法も使用することができますが、これらのキーをデータ統合の一部として使用する必要がある場合は、これらの文字を持つデータを持たないフィールド上でキーを作成するのが最善です。

## <a name="view-alternate-keys"></a>代替キーを表示

1. [Power Apps ポータル](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) から、**データ** > **エンティティ** を選択し、表示したいフィールドを含むエンティティを選択します。
2. **キー**を選択すると、定義された代替キーのリストが表示されます。

   > [!div class="mx-imgBorder"] 
     > ![代替キーを表示](media/view-alternate-keys-portal.png)

## <a name="create-an-alternate-key"></a>代替キーの作成

1. [代替キーを表示](#view-alternate-keys)しているとき、**キーを追加**を選択します。
2. パネルを使用して**表示名**を設定し、代替キーの作成に使用するフィールドを選択します。

    **名前**フィールドは、表紙名に基づいて設定されます。

    ![代替キー定義の例](media/alternate-key-account-number-sic-code.png)

1. **完了**を選択してパネルを閉じます。
2. 代替キーを作成するには、**エンティティの保存**を選択します。

> [!NOTE]
> 代替キーはすぐに使用できません。 エンティティを保存して代替キーをサポートするデータベースのインデックスを作成すると、システム ジョブが開始されます。

## <a name="delete-an-alternate-key"></a>代替キーの削除

[代替キーを表示](#view-alternate-keys)しているとき、削除するキーを選択し、コマンド バーから **Delete キー**を選択します。

### <a name="see-also"></a>関連項目

[開発者向けドキュメント: エンティティの代替キーを定義](/dynamics365/customer-engagement/developer/define-alternate-keys-entity)
