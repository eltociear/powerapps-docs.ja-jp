---
title: Power Apps ポータルを使用した代替キーを定義する | MicrosoftDocs
description: Power Apps ポータルを使用した代替キーを定義する方法
ms.custom: ''
ms.date: 05/31/2018
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
ms.openlocfilehash: 6b34d999b06e756bac246213412fb955c433c8eb
ms.sourcegitcommit: 4b6f187c9501332f9acca5978fa326621f2980e5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/22/2020
ms.locfileid: "3394288"
---
# <a name="define-alternate-keys-using-power-apps-portal"></a>Power Apps ポータルを使用した代替キーを定義する

[Power Apps ポータル](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) では、 Common Data Serviceを使用してエンティティの代替キーを簡単に確認、作成することができます。

ポータルでは一般的なオプションのほどんとを構成できますが、特定のオプションはソリューション エクスプローラーを使用してのみ設定できます。 <br />詳細: 
- [レコードを参照する代替キーの定義](define-alternate-keys-reference-records.md)
- [ソリューション エクスプローラーを使用した代替キーの定義](define-alternate-keys-solution-explorer.md)

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
2. 代替キーを作成するには、**エンティティの保存**をクリックします。

> [!NOTE]
> 代替キーはすぐに使用できません。 エンティティを保存して代替キーをサポートするデータベースのインデックスを作成すると、システム ジョブが開始されます。

## <a name="delete-an-alternate-key"></a>代替キーの削除

[代替キーを表示](#view-alternate-keys)しているとき、削除するキーを選択し、コマンド バーから **Delete キー**を選択します。

### <a name="see-also"></a>関連項目

[レコードを参照する代替キーの定義](define-alternate-keys-reference-records.md)<br />
[ソリューション エクスプローラーを使用した代替キーの定義](define-alternate-keys-solution-explorer.md)<br />
[開発者向けドキュメント: エンティティの代替キーを定義](/dynamics365/customer-engagement/developer/define-alternate-keys-entity)
