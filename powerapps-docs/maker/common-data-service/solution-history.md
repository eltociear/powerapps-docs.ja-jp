---
title: ソリューションの履歴の表示 | MicrosoftDocs
description: ソリューションの履歴の表示方法に関する説明 | MicrosoftDocs
keywords: ''
ms.date: 04/20/2020
ms.service: powerapps
ms.custom: ''
ms.topic: article
ms.assetid: ''
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: ''
topic-status: Drafting
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 75880ec6d29dbb8e9fa9e5f1c2ef4f9721a479ce
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/21/2020
ms.locfileid: "3276015"
---
# <a name="view-the-history-of-a-solution"></a>ソリューションの履歴の表示
Power Apps の**ソリューション**領域からソリューションの操作の詳細を表示できます。 操作は、ソリューションのインポート、エクスポート、またはアンインストールのいずれかです。 ソリューションの履歴はソリューション バージョン、ソリューション発行者、操作などの一部の情報を、操作の開始時刻と終了時刻、および操作の状態の表示されます。

## <a name="view-solution-history"></a>ソリューション履歴表示
1.  [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインします。
2.  左側のナビゲーション ウィンドウで、**ソリューション**を選択し、目的のソリューションを選択してから、コマンド バーの**履歴の表示**を選択します。 

    履歴が表示されます。 

    > [!div class="mx-imgBorder"] 
    > ![](media/solution-history.png "Solution history")

ソリューションの操作を選択して**情報ページ**を表示します。 各ソリューションの履歴記録は読み取り専用であり、**詳細情報**領域に以下のものを含みます。
-   **名前**. ソリューションの一意名。 
-   **開始時間**。 操作が開始した時間。
-   **終了時刻**: 操作が終了した時間。
-   **バージョン**. このソリューションのバージョンです。
-   **発行者** 操作が関連付けられている発行者の名前を入力します。 
-   **操作**。 インポート、エクスポート、または削除のような操作です。 
-   **サブ操作**: 既存のソリューションへの新しいソリューションのインポートまたは更新などの操作の種類を示します。
-   **結果**。  成功 または 失敗 など、操作の結果。

 > [!div class="mx-imgBorder"] 
 > ![](media/solution-history-details.png "Solution history details")

### <a name="view-solution-operation-error-details"></a>ソリューションの操作エラーの詳細表示 
**詳細情報**領域の下にある**詳細**領域にはソリューションに関する追加情報があり、ソリューションの操作に失敗した場合、情報には以下のものが含まれます。 
- 操作から返されたエラーの**エラー コード**。 
- 操作の失敗の根本的な原因を診断するのに役立つ**例外メッセージ**。 ソリューション依存エラーを含む一部のエラーは、問題の診断を簡単におこなうための ソリューション階層 へのリンクも含まれることがあります。 
- **活動ID** は、Microsoft カスタマ サポートに問い合わせる必要があるケースに有用です。

### <a name="see-also"></a>関連項目
[ソリューションの階層の表示](solution-layers.md)  <br />
[ソリューションの概要](solutions-overview.md) 


