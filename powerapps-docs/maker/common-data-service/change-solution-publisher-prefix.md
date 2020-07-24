---
title: ソリューション発行者の概要 | MicrosoftDocs
ms.custom: ''
ms.date: 02/03/2020
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
author: Mattp123
ms.assetid: ece684h8-ad40-4bfa-975a-3e5bafb854aa
caps.latest.revision: 55
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 516f4a35cf7d31c45df011b7685ade1526246582
ms.sourcegitcommit: c6906775005aec98973b1f5c3dbe5924aff6d26e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2020
ms.locfileid: "3341280"
---
# <a name="solution-publisher-overview"></a>ソリューション発行者の概要

作成したアプリや加えたカスタマイズもソリューションの一部です。 すべてのソリューションには発行者がいます。 ソリューションを作成する際に発行元を指定します。 

ソリューション発行者とは、アプリの開発者を意味します。 このため、分かりやすいソリューション発行者を作成する必要があります。 ソリューションの発行者は、Power Apps の **ソリューション** エリアで **設定** を選択すると確認できます。

ソリューション発行者の詳細については、「[ソリューション発行者](/power-platform/alm/solution-concepts-alm#solution-publisher)」を参照してください。

## <a name="create-a-solution-publisher"></a>ソリューション発行者の作成
1.  Power Apps ポータルで、 **ソリューション**を選択します。 
2.  コマンドバーで、**新しいソリューション** を選択し、右側のウインドウの **発行元** ドロップ ダウン リストから **+発行元** を選択します。 
    > [!div class="mx-imgBorder"] 
    > <img src="media/create-new-pubisher.png" alt="Create a new publisher" height="738" width="400">
3.  **新しい発行元** のフォームで、必要な情報とオプション情報を入力します。 
   - **表示名**: 発行元の表示名称を入力します。 
   - **名前**. 発行元の一意の名称を入力します。 
   - **接頭辞**:  お好みの発行元の接頭辞を入力します。 
   -    **オプション値の接頭辞**。 このフィールドは、発行元の接頭辞に基づいた番号を生成します。 この番号は、オプション セットにオプションを追加する際に使用し、オプションを追加するのに使用したソリューションを識別する助けとなります。 
   - **取引先担当者の詳細**。 オプションで、連絡先と住所の情報を追加できます。
4. **保存して閉じる**を選択します。

## <a name="change-a-solution-publisher"></a>ソリューションの発行元を変更する
管理されていないソリューションの発行者を変更するには、次の手順に従ってください:
1.  Power Appsポータルで、 **ソリューション** を選択し、 **…** を選択します 変更するソリューションの **設定** を選択します。 
2.  **ソリューション設定** ウィンドウで、 **発行元の編集** を選択します。 
3.  **表示名称** と **接頭辞** フィールドの値を変更します。 **オプション値の接頭辞** フィールドは、発行元の接頭辞に基づいた番号を生成します。 この番号は、オプション セットにオプションを追加する際に使用し、オプションを追加するのに使用したソリューションを識別する助けとなります。 
4.  接頭辞に加えて、 **連絡先** セクションのソリューション発行者の表示名称、連絡先情報、アドレスを変更することもできます。 
5.  **保存して閉じる**を選択します。

### <a name="see-also"></a>関連項目
[ソリューションの作成](create-solution.md)