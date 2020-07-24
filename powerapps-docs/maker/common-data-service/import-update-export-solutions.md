---
title: ソリューションのインポート | MicrosoftDocs
description: Power Apps でソリューションをインポートする方法について
ms.custom: ''
ms.date: 05/26/2020
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: Mattp123
ms.assetid: 56363ea3-ea76-4311-9b7a-b71675e446fb
caps.latest.revision: 57
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: b8475b0d347dabfab0fd1ce71b8a25fbbbd9d0c6
ms.sourcegitcommit: 909948d219c3c61d617f13aceb355e1d5bcb0b55
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2020
ms.locfileid: "3432889"
---
# <a name="import-solutions"></a>ソリューションのインポート 

この記事の手順を使用して、ソリューションを手動でインポートできます。 信頼できるソースから取得したソリューションのみをインポートする必要があります。 カスタマイズには、外部ソースにデータを送信できるコードが含まれている場合があります。   
 
> [!NOTE]
> - プラグイン アセンブリを含むソリューションをインポートするには、**プラグイン アセンブリ** エンティティの **作成** 権限が必要です。 既定では、システム管理者のセキュリティ ロールにはこの権限がありますが、システム カスタマイザー のセキュリティ ロールにはありません。 
> - 管理ソリューションをインポートすると、すべてのコンポーネントの変更が公開された状態で環境に反映されます。 ただし、アンマネージド ソリューションをインポートすると、変更は下書き状態でインポートされるため、アクティブにするには公開する必要があります。 
> - 組織に正常なアプリケーション ライフサイクル管理 (ALM) を実装するには、ソース管理システムを使用してソリューションを格納およびコラボレーションし、ソリューションのインポート プロセスを自動化することを検討してください。 詳細: Power Platform ALMガイドの [ALMの基本](/power-platform/alm/basics-alm)。

**アンマネージド** ソリューションをインポートする場合:
- そのソリューションのすべてのコンポーネントを環境に追加し、ソリューションを削除してコンポーネントを削除することはできません。 アンマネージド ソリューションを削除すると、ソリューション コンテナーのみが削除されます。
- これには、すでにカスタマイズしたコンポーネントが含まれており、インポート済みアンマネージド ソリューションのカスタマイズによってカスタマイズが上書きされます。 これを元に戻すことはできません。

ソリューションをインポートするには:

1.  [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインし、左側のナビゲーションから**ソリューション**を選択します。  
  
2.  コマンド バーで **インポート** を選択します。  

    > [!div class="mx-imgBorder"]  
    > ![ソリューションのインポート](media/solution-import.png "ソリューションのインポート") 
  
3.  **ソリューション パッケージの選択** ページで、**参照** を選択し、インポートするソリューションが含まれている圧縮 (.zip または .cab) ファイルを検索します。 
  
4.  **次へ**を選択します。  
  
5.  ソリューションについての情報が表示されます。 **インポート**を選択します。  
  
6. インポートが完了するまで、数分待つ必要がある場合があります。 結果を表示し、**閉じる**を選択します。  
  
 公開が必要な変更をインポートした場合、それらを使用可能にする前に、カスタマイズを公開する必要があります。 
  
 インポートが正常に完了しない場合、キャプチャされたエラーまたは警告のレポートが表示されます。 インポートが失敗した原因に関する詳細をキャプチャするために、**ログ ファイルのダウンロード**を選択します。 インポートの失敗の最も一般的な原因は、ソリューションに必要なコンポーネントが含まれていなかったことです。  
  
 ログ ファイルをダウンロードするとき、Office Excel を使用して XML ファイルを開き、内容を表示します。  
  
> [!NOTE]
>  アクティブなルーティング規則セットを編集することはできません。 したがって、同じ ID のルールが既に存在する環境にアクティブなルーティング規則セットを組み込むソリューションをインポートする場合、インポートは失敗します。 詳細情報: [サポート案件を自動的にルーティングするルールを作成する](https://docs.microsoft.com/dynamics365/customer-engagement/customer-service/create-rules-automatically-route-cases)  
  
<a name="BKMK_UpdateSolutions"></a>   

### <a name="see-also"></a>関連項目
[ソリューションの更新](update-solutions.md) <br />
[エクスポート ソリューション](export-solutions.md) <br />
[変更の公開](create-solution.md#publish-changes)

