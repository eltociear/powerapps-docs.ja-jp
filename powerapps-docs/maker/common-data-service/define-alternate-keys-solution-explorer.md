---
title: ソリューション エクスプローラーを使用して代替キーを定義 | MicrosoftDocs
description: ソリューション エクスプローラーを使用して、Common Data Service でレコードの参照に使用できる代替キーを定義する方法を説明します
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
ms.openlocfilehash: c13838bdd957d78552d71636b4a165902154e82c
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2019
ms.locfileid: "2865728"
---
# <a name="define-alternate-keys-using-solution-explorer"></a>ソリューション エクスプローラーを使用した代替キーの定義

ソリューション エクスプローラーでは、Common Data Service の代替キーを表示および作成する方法を提供します。

[Power Apps ポータル](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) ではほとんどの一般的なオプションを構成することができますが、ソリューション エクスプローラーを使用して設定する必要があるオプションもあります。 <br />詳細: 
- [レコードを参照する代替キーの定義](define-alternate-keys-reference-records.md)<br />
- [Power Apps ポータルを使用して代替キーを定義する](define-alternate-keys-portal.md)

## <a name="open-solution-explorer"></a>ソリューション エクスプローラーを開きます

作成する代替キーの名前の一部は、カスタマイズの接頭辞です。 これは、作業中のソリューションの発行者に基づいて設定されます。 カスタマイズの接頭辞に注意を払う場合は、カスタマイズの接頭辞がこのエンティティに対して必要な接頭辞であるアンマネージド ソリューションで作業するようにします。 詳細: [ソリューション発行者の接頭辞を変更する](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="view-alternate-keys"></a>代替キーを表示

1. ソリューション エクスプローラーを開いた状態で、**コンポーネント**下の**エンティティ**を展開し、代替キーを表示するエンティティを選択します。
2. エンティティを展開し**キー**を選択します。

    ![代替キーを表示](media/view-alternate-keys-solution-explorer.png)

## <a name="create-an-alternate-key"></a>代替キーの作成

1. [代替キーを表示](#view-alternate-keys)しているとき、**新規**を選択します。
1. フォームで、**表示名**を入力します。 **名前**フィールドは**表紙名**に基づいて自動挿入されます。 
2. **使用可能な属性**リストから、各属性、**追加**の順に選択して属性を**選択された属性**リストに移動します。
    ![代替キーの作成](media/create-alternate-key-solution-explorer.png)
1. **OK** を選択してフォームを閉じます。

### <a name="optional-view-the-system-job-tracking-creation-of-indexes"></a>(任意) インデックスのシステム ジョブ追跡の作成を表示
1. 新しい代替キーを作成した後に[代替キーを表示](#view-alternate-keys)しているとき、作成したキーの行が表示されます。
2. **システム ジョブ**列には、代替キーをサポートするためにインデックスの作成を監視するシステム ジョブへのリンクがあります。 
    
    このシステム ジョブでは、以下のパターンに従う名前があります。`Create index for {0} for entity {1}`ここで `0` は代替キーの**表示名**であり、`1` はエンティティの名前です。

    システム ジョブへのリンクは、システム ジョブが正常に完了した後は表示されません。 詳細: [システム ジョブの監視と管理](/dynamics365/customer-engagement/admin/monitor-manage-system-jobs)


## <a name="delete-an-alternate-key"></a>代替キーの削除

[代替キーを表示](#view-alternate-keys)しているとき、![削除](media/delete.gif)を選択します。

### <a name="see-also"></a>関連項目

[レコードを参照する代替キーの定義](define-alternate-keys-reference-records.md)<br />
[Power Apps ポータルを使用して代替キーを定義する](define-alternate-keys-portal.md)<br />
[開発者向けドキュメント: エンティティの代替キーを定義](/dynamics365/customer-engagement/developer/define-alternate-keys-entity)
