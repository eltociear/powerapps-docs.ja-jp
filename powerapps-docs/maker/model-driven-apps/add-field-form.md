---
title: Power Apps におけるモデル駆動型アプリ フォームへのフィールドの追加 | MicrosoftDocs
ms.custom: ''
ms.date: 05/04/2020
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
ms.assetid: 29499887-6e7b-44a1-86a7-eaad33f3075d
caps.latest.revision: 30
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: dcf292660c89e55ec83739c4dba662ff4cf7bff4
ms.sourcegitcommit: 52b7f59e271437e86ffff226fb6c1982bf7f08b1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "3332487"
---
# <a name="add-a-field-to-a-model-driven-app-form"></a>フィールドをモデル駆動型アプリ フォームに追加する 

標準エンティティの Power Apps フォームが組織のビジネス要件を満たさない場合、既存のフィールドを変更または新しいフィールドを追加してフォームをカスタマイズできます。 これはフォームの既存のフィールドの編集と似ていますが、特定のビジネス シナリオを解決するためにはフィールドを追加するほうが良い場合があります。

このトピックでは、フィールドをフォームに追加します。   
  
1.  [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインします。  

2.  **データ**を展開して**エンティティ**を選択し、目的のエンティティを選択して**フォーム** タブを選択します。  

3.  一覧で、種類が**メイン**のフォームを開いて編集します。  
  
4.  このフォームでは、フィールドの追加先のセクションをクリックし **フィールド** ウィンドウで、フォームに追加するフィールドをダブルクリックします。  
  
    > [!TIP]
    >  フォームでオプション セット フィールドを追加すると、オプション セット値を含むドロップダウン リストに 2 つの値のみ表示できます。 このリストの他の値を見るにはスクロールする必要があります。 スクロールせずに 3 つ以上の値を表示する場合は、フォームのオプション セット フィールドの下で 1 つ以上の**スペーサー**コントロールを追加します。 各**スペーサー**コントロールは 1つ の追加オプション セット値にスペースを提供します。 たとえば、スクロールしないでドロップダウン リストで 4 つ値を表示するには、2 つの**スペーサー**コントロールをフォームのオプション セット フィールドの下に追加します。  
  
5.  編集中のフォームのカスタマイズを公開するには、フォームをオープンして **公開** をクリックします。 
  
6.  フォームの編集が終了したら **保存して閉じる** をクリックします。  
  
> [!IMPORTANT]
>  統一インターフェイスでフィールド レベルのセキュリティを設定する場合、フィールド レベルのセキュリティ規則を使用して必須フィールドに読み取り専用を設定することはお勧めしません。  レコードが作成されると、保存パイプラインは必須フィールドの読み取り専用設定を無視して、レコードを保存します。 ロールベースのセキュリティを使用して、エンティティを読み取り専用に設定することをお勧めします。 これにより、レコードの作成または保存時に競合が発生しなくなります。
  
  
> [!NOTE]
>  カスタマイズを公開すると、標準システム操作を干渉する可能性があります。 ユーザーへの影響が最小限に留まるように公開することが推奨されます。

  
## <a name="next-steps"></a>次のステップ  
 
 [フォームの作成および設計](create-design-forms.md)
