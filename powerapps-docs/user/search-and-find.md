---
title: Common Data Service | の検索オプションと検索オプションMicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 10/02/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: c7192b98d3f97a4aba57f58c52b02245cb71b155
ms.sourcegitcommit: 7c46e7ce889e2f1c5352ed2e705b0bb8968f2a89
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/04/2019
ms.locfileid: "71950889"
---
# <a name="compare-search-and-find-options-in-common-data-service"></a>Common Data Service の検索オプションと検索オプションを比較する

Common Data Service でデータを検索するには、次の4つの方法があります。

-   関連性の検索  
  
-   フルテキストクイック検索 (単一エンティティまたはマルチエンティティ)  
  
-   クイック検索 (単一エンティティまたはマルチエンティティ)  

-   高度な検索

> [!NOTE]
> 複数エンティティのクイック検索は、分類された検索とも呼ばれます。 
  
次の表は、使用可能な4つのオプションの簡単な比較を示しています。

|機|[関連性の検索](search-records.md#relevance-search)|[フルテキストクイック検索](search-records.md#start-a-search)|[クイック検索](search-records.md#start-a-search)|[高度な検索](create-edit-or-save-advanced-find-search.md)|  
|-------------------|----------------------|---------------------------|----------------|-------------------|  
|既定で有効になっていますか?|いいえ。 管理者は手動で有効にする必要があります。|いいえ。 管理者は手動で有効にする必要があります。|はい|はい|  
|単一エンティティの検索範囲|エンティティグリッドでは使用できません。 検索結果は、[結果] ページでエンティティによってフィルター処理できます。|エンティティグリッドで使用できます。|エンティティグリッドで使用できます。|エンティティグリッドで使用できます。|  
|複数エンティティの検索範囲|検索できるエンティティの数に上限はありません。 **注:** 検索できるエンティティの数に上限はありませんが、[レコードの種類] フィルターでは、10個のエンティティについてのみデータが表示されます。|エンティティによってグループ化された最大10個のエンティティを検索します。|エンティティによってグループ化された最大10個のエンティティを検索します。|マルチエンティティ検索は使用できません。|  
|検索動作|エンティティ内の任意のフィールド内の検索語句に一致する単語を検索します。|エンティティ内の1つのフィールドで、検索用語内のすべての単語に一致するものを検索します。ただし、これらの単語は、フィールド内の任意の順序で照合できます。|は、"Like" 句を使用した SQL クエリ内のと同じものを検索します。 文字列内で検索するには、検索語句でワイルドカード文字を使用する必要があります。 すべての一致は、検索用語と完全に一致している必要があります。|選択したレコードの種類の検索条件を定義できるクエリビルダー。 また、を使用して、Office Excel にエクスポートするデータを準備して、データを分析、集計、または集計したり、ピボットテーブルを作成してさまざまなパースペクティブからデータを表示したりすることもできます。|  
|検索可能なフィールド|テキストフィールド (1 行のテキスト、複数行のテキスト、参照、オプションセットなど)。 では、数値データ型または日付データ型のフィールドの検索はサポートされていません。|検索可能なすべてのフィールド。|検索可能なすべてのフィールド。|検索可能なすべてのフィールド。|  
|検索結果|検索結果を関連性のある順に1つのリストに返します。|単一エンティティの場合は、エンティティグリッド内の検索結果を返します。 複数のエンティティについては、アカウント、連絡先、潜在顧客などのカテゴリ別にグループ化された検索結果を返します。|単一エンティティの場合は、エンティティグリッド内の検索結果を返します。 複数のエンティティについては、アカウント、連絡先、潜在顧客などのカテゴリ別にグループ化された検索結果を返します。|選択したレコードの種類の検索結果を、指定した列と共に、構成した並べ替え順序で返します。|
|ワイルドカード (*)|単語入力補完でサポートされる末尾のワイルドカード。|先頭のワイルドカードがサポートされています。 既定では、末尾のワイルドカードが追加されます。|先頭のワイルドカードがサポートされています。 既定では、末尾のワイルドカードが追加されます。|サポートされていません。|  