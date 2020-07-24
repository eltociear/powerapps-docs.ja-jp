---
title: Power BI Desktop でのエンティティ データを表示 (プレビュー) | MicrosoftDocs
description: Power BI Desktop でエンティティ データにアクセスして、表示する方法についてアクセスする方法について説明します
ms.custom: ''
ms.date: 05/26/2020
ms.reviewer: matp
ms.service: powerapps
author: Mattp123
ms.assetid: ''
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 54f23e3b5d390acef99878cdae373b04032a7873
ms.sourcegitcommit: 82fa1758e29fe302f9a252fd9943ace03b7aada0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/03/2020
ms.locfileid: "3427017"
---
# <a name="view-entity-data-in-power-bi-desktop-preview"></a>Power BI Desktop でエンティティ データを表示する (プレビュー)

[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Power BI Desktop を使用して、Common Data Service で表示できます。 環境からアクセスできるエンティティ レコード データは、読み取り専用です。 データ アクセスでは、Power Apps を使用してエンティティ レコード データにアクセスするために使用されるものと同じ Common Data Service セキュリティ モデルを使用します。

> [!IMPORTANT]
> - これはプレビュー機能であり、すべての地域で利用できるわけではありません。
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)]

## <a name="prerequisite"></a>前提条件
このプレビューでは、環境で Common Data Service の表形式データ ストリーム (TDS) エンドポイントを有効にするには、管理者であり、次の手順を実行する必要があります。
    
1. [Power Apps](https://make.powerapps.com/) にサインインして、右上隅で適切な環境を選択します。
      
2. 環境に少なくともバージョン 9.1.0.17437 があることを確認します。 これをおこなうには、ツールバーで **設定** ギアを選択してから、**詳細設定** を選択します。 次に、新しいブラウザタブが開いたら、**設定**ツールバーのギアを選択し、次に **詳細** を選択します。
      
3. TDS エンドポイントを有効にします。 詳細については、[機能設定の管理](/power-platform/admin/settings-features) のトピックで、**TDS エンドポイント (プレビュー)** 設定を参照してください。
          
## <a name="view-entity-data"></a>エンティティ データの表示

1.  [Power Apps](https://make.powerapps.com/) にサインインして、右上隅で適切な環境を選択します。

2.  左側のナビゲーションウィンドウで、**データ**を展開し、**エンティティ**を選択して、次にコマンドバー上の **Power BI で分析**を選択します。

    ご使用の環境の pbids ファイルは、ブラウザーの既定ダウンロード フォルダーにダウンロードされます。
    
    > [!NOTE]
    > Power Apps 環境内に **Power BI で分析**オプションがない場合、SQL 接続機能にまだアクセスできません。

3.  .pbids ファイルを開いて、Power BI Desktop にアクセスします。 Power BI Desktop を持っていない場合は? [今すぐ入手する](https://powerbi.microsoft.com/downloads/)。

4.  pbids ファイルは、Power BI Desktop にロードされています。 **SQL Server データベース** ダイアログ ボックスで、**マイクロソフト アカウント**を選択し、**サインイン**を選択してから、表示されるブラウザ ウィンドウに資格情報を入力します。

    > [!div class="mx-imgBorder"] 
    > ![](media/power-bi-environment-signin.png)

5.  Power BI Desktop の **SQL Server データベース** ダイアログ ボックス内にある**接続**を選択します。

    Power BI Desktop 内の**ナビゲーター** ウィンドウに環境が表示されます。 展開して、分析可能なエンティティ テーブルを表示します。 エンティティを選択して、そのデータを表示します。

    > [!div class="mx-imgBorder"] 
    > ![](media/entity-record-data-displayed.png)

> [!NOTE]
> T-SQL クエリなどの SQL オプションはサポートされていません。

Power BI Desktop の詳細については、[Power BI Desktop の概要](/power-bi/desktop-getting-started) を参照してください。

### <a name="see-also"></a>関連項目
[SQL を使用してデータを照会](../../developer/common-data-service/cds-sql-query.md)
