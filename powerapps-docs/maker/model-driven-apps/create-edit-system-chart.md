---
title: Power Apps でモデル駆動型アプリ システム グラフを作成、編集する | MicrosoftDocs
description: グラフを作成または編集する方法を学習する
ms.custom: ''
ms.date: 03/30/2020
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
author: Mattp123
ms.assetid: e02d58f7-6b1c-4a51-b801-a4d9f24729c5
caps.latest.revision: 29
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 426bfaf0ab53e1d896f7e0b098e089c8596ad907
ms.sourcegitcommit: 3c6c5594b73abd5ff438d50f3b579d56cef7241c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2020
ms.locfileid: "3285613"
---
# <a name="create-a-model-driven-app-system-chart"></a>モデル駆動型アプリ システム グラフを作成する

このトピックでは、システム グラフの作成方法について説明します。 システム グラフは、組織所有のグラフであり、アプリを実行しているデータを読み取るためのアクセス権を持つユーザーはだれでも使用できるようになります。 システム グラフを、特定のアプリ ユーザーに割り当てたり共有したりすることはできません。  
  
1. [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインします。  

2. **データ**を展開して**エンティティ**を選択し、目的のエンティティを選択して**グラフ** タブを選択します。  
  
3.  ツール バーで、**グラフの追加** を選択します。  
  
4.  グラフの種類およびデータをグラフに表示する方法を指定します。  
  
    -   *取引先企業ごとの従業員数*など、グラフの名前を入力します。  
  
    -   **フィールドの選択** ドロップダウンで次の作業を行います。 
        - **フィールドの選択** の **系列** 軸ドロップダウンで **従業員数**などのフィールドを選択します。  
        - **フィールドの選択** の **カテゴリ** 軸ドロップダウンで、**取引先企業名** などのフィールドを選択します。
  
    -   *この縦棒グラフには、取引先企業名ごとに従業員数が表示されます* など、グラフの目的を識別できる説明を追加します。 

    > [!div class="mx-imgBorder"] 
    > ![グラフの例](media/sample-chart.png)
  
5.  **保存して閉じる**を選択します。  

## <a name="known-issues"></a>既知の問題  
グラフデザイナーでは、特定の集計フィールドに対する注文の追加はには対応していないため、エラーが発生します。  この挙動の原因と成る計算フィールドは、その他の計算フィールド、関連するエンティティフィールド、またはエンティティのローカルフィールドを使用しています。

## <a name="next-steps"></a>次のステップ  
[ダッシュボードの作成または編集](create-edit-dashboards.md)
