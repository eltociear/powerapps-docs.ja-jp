---
title: データ レイクへのエクスポート | MicrosoftDocs
description: エンティティデータを Power Appsの Azure データレイクにエクスポートする方法を解説します
ms.custom: ''
ms.date: 04/27/2020
ms.reviewer: Mattp123
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- powerapps
author: sabinn-msft
ms.assetid: ''
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: b8b0ab15720130e7624d31ea40fa7a73a4fe4f8f
ms.sourcegitcommit: 8728546925c570541bebc1ac7a24227651e8f65f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "3463472"
---
# <a name="export-entity-data-to-azure-data-lake-storage-gen2"></a>エンティティデータを Azure Data Lake Storage Gen2 にエクスポートする

Data Lake サービスへのエクスポートは、Common Data Service から Azure Data Lake Storage Gen2 へデータを継続的にエクスポートするためのパイプラインとして機能します。 Data Lake サービスへのエクスポートは、災害復旧機能を備えたスケーラブルな高可用性を提供することにより、エンタープライズ ビッグデータの分析用に設計されています。 データは Common Data Model のフォーマットで保存されます。これにより、アプリと展開間で意味上の一貫性が提供されます。 

![データ レイクへのエクスポートの概要](media/export-data-lake-overview.png "Data Lake にエクスポートの概要")

Data Lake にエクスポート には、次の機能が実装されています: 

- Common Data Service 環境を Azure サブスクリプション内の Data Lake Storage Gen2 にリンクまたはリンク解除します。 
- Data Lake Storage Gen2 へのエンティティの継続的なレプリケーション。
- 初期書込み、それに続くデータとメタデータの増分書込み。 
- 標準エンティティとカスタム エンティティ両方のレプリケーション。 
- (CrUD) トランザクションの作成、更新、削除のレプリケーション。 
- 大規模な分析シナリオの継続的なスナップショット更新。 
- Power BI、Azure Data Factory、Azure Databricks、Azure Machine Learning などの、メタデータの検出、およびデータの作成者と利用者間の相互運用性を促進します。

## <a name="how-data-and-metadata-are-exported"></a>データとメタデータのエクスポート方法

Data Lake サービスへのエクスポートは、エンティティ データとメタデータの初期および増分の書き込みに対応しています。 Common Data Service でのデータまたはメタデータの変更は、追加アクションなしで自動的にデータレイクにプッシュされます。 これはプル操作ではなく、プッシュ操作です。 更新間隔を設定することなく、変更がエクスポート先にプッシュされます。 

標準エンティティとカスタム エンティティの両方をエクスポートすることができます。 Common Data Service の変更追跡のエンティティ属性は、データが最初に抽出されてから、または最後に同期されてからどのデータが変更されたかを検出することによって、データの同期を効率の良い方法で維持します。 

すべての作成、更新、削除作業は、Common Data Service から Data Lake へとエクスポートされます。 たとえば、ユーザーが Common Data Service のアカウント エンティティ レコードを削除すると、トランザクションは宛先のデータ レイクに複製されます。

## <a name="prerequisites"></a>前提条件

Common Data Service のデータをデータ レイクにエクスポートする前に、Azure Storage v2 (汎用 v2) ストレージ アカウントを作成して構成する必要があります。 

 [Azure Storage アカウントの作成](/azure/storage/blobs/data-lake-storage-quickstart-create-account)  に記載の手順に従い、以下の要件に留意してください: 

- ストレージのアカウントの所有者権限が付与されている必要があります。 
- ストレージ タイプを **Storagev2 (汎用v2)** に設定します。 
- ストレージのアカウントは **階層型名前空間** の機能を有効にしておく必要があります。 

 レプリケーションの設定にgeo 冗長ストレージへの読み取りアクセス権を指定しておくことを推奨します。 詳しくは [読み取りアクセスのgeo 冗長ストレージ](/azure/storage/common/storage-redundancy-grs#read-access-geo-redundant-storage)を参照してください

>   ![ストレージ アカウント のプロパティ](media/storage-account-properties.png "ストレージ アカウント のプロパティ")

> [!NOTE]
> - ストレージ アカウントは、Power Apps のテナントと同じ Azure Active Directory (Azure AD) テナントに作成する必要があります。  
> - ストレージ アカウントは、機能を使用する Power Apps 環境と同じリージョンに作成する必要があります。  
> - Common Data Service 環境を Azure Data Lake Storage Gen2 にリンクするには、Common Data Service 管理者である必要があります。 
> - エクスポートが可能となっているのは、変更の追跡が有効になっているエンティティのみです。 

## <a name="select-and-export-common-data-service-entity-data-to-azure-data-lake-storage-gen2"></a>Common Data Service エンティティ データを選択して、Azure Data Lake Storage Gen2 にエクスポートする

1. [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインし、**データ** を展開して、**エンティティ** を選択します。 
2. コマンドバーで、**データ レイクへエクスポートする**を選択し、続いて **データ レイクへエクスポートする** ページの、**データレイクへの新しいリンク**を選択します。 
3. 以下の設定を選び、続いて **次へ** を選択します。 
   - **サブスクリプション**。 Azure のサブスクリプションを選択します。 
   - **リソース - グループ**。 Storage v2 (汎用 v2) ストレージ アカウントを含むリソース グループを選択します。
   - **ストレージ アカウント**。 エクスポートに使用する、Storage v2 (汎用 v2) ストレージ アカウントを選択します。 

    > [!NOTE]
    > Common Data Service 環境の Data Lake へのリンクの一部として、Data Lake へエクスポートのサービスアクセス権を自分のストレージ アカウントへ付与します。 [Azure Data Lake Storage アカウントの作成および構成の前提条件](#prerequisites) およびストレージ アカウントの所有者ロールを自分に付与する方法、に従うことを確認してください。 さらに、 Power Platform データフローのサービスへのアクセス権を自分のストレージ アカウントに付与します。 詳細: [データフローでセルフサービス データを準備する](self-service-data-prep-with-dataflows.md)。  

4. データ レイクにエクスポートするエンティティを選択し、**保存**を選択します。 エクスポートが可能となっているのは、変更の追跡が有効になっているエンティティのみです。 詳細については、 [エンティティの変更追跡を有効化する](/dynamics365/customer-engagement/admin/enable-change-tracking-control-data-synchronization) を参照してください

   > [!div class="mx-imgBorder"] 
   > ![エクスポートするエンティティの選択](media/export-data-lake-select-entity.png "エクスポートするエンティティの選択")

Common Data Service 環境は Azure Data Lake Storage Gen2 アカウントにリンクされています。 Azure ストレージ アカウントのファイル システムは、データ レイクに複製するように選択された各エンティティーのフォルダーとともに作成されます。 

> [!NOTE]
> エクスポートによってデータ レイク サービスにエクスポートされたデータは、Azure Data Lake Storage Gen2 によって暗号化されて保存されます。 さらに、BLOB ストレージ内の一時データも暗号化されて保存されます。 Azure Data Lake Storage Gen2 の暗号化は、データの保護、エンタープライズ セキュリティ ポリシー、規制コンプライアンス要件の順守に役立ちます。 詳細: [Azure データ保存時の暗号化]( /azure/security/fundamentals/encryption-atrest)

## <a name="manage-entity-data-to-the-data-lake"></a>データレイクへのエンティティデ ータを管理する

サブスクリプションで Azure Data Lake Storage Gen2 へのデータ エクスポートを設定後、次の2つの方法のいずれかで、データ レイクへのエンティティ データのエクスポートを管理できます: 

- Power Apps メーカー ポータルの **データレイクへのエクスポート** 領域で、 コマンドバーで **エンティティを管理する** を選択し、1つ以上のリンクされたエンティティを追加、削除します。
- Power Apps のメーカーポータルの **エンティティ** 領域で、 **…** を選択します エンティティの横に位置する、エンティティ データをエクスポートするリンクされたデータ レイクを選択します。 

   ![エクスポートのエンティティを選択](media/select-entity-export.png "エクスポートのエンティティを選択")

リンクされているすべてのエンティティのリンクを解除するには、Power Apps メーカー ポータルの **データ レイクへのエクスポート** 領域で、**データ レイク のリンク解除** を選択します。

## <a name="view-your-data-in-azure-data-lake-storage-gen2"></a>Azure Data Lake Storage Gen2 でデータを表示する

1. [Azure](https://portal.azure.com) にサインインし、ストレージ アカウントを選択してから、左端のナビゲーション ウィンドウで **ストレージ エクスプローラー** を選択します。 
2. **ファイル システム**を展開し、続いて commondataservice-*environmentName*-org-*Id* を選択します。 

model.json ファイルは、名前とバージョンとともに、データ レイクにエクスポートされたエンティティのリストを含んでいます。 model.json ファイルには、初期同期状態と同期完了時間も含まれています。 

データ レイクにエクスポートされた各エンティティに対して、スナップショット コマンド区切り (CSV 形式) ファイルを含むフォルダーが表示されます。
   > [!div class="mx-imgBorder"] 
   > ![データ レイクのエンティティ データ](media/entity-data-in-lake.png "データ レイクのエンティティ データ") 

### <a name="continuous-snapshot-updates"></a>スナップショットの継続的な更新

Common Data Serviceデータは、トランザクションの作成、更新、削除を通じて継続的に変更できます。 スナップショットは、定期的に (この場合は 1 時間ごとに) 更新されるデータの読み取り専用コピーを提供します。 これにより、任意の時点で、データ分析の利用者がレイクのデータを確実に消費できるようになります。

![スナップショットの継続的な更新](media/snapshot-updates.png "スナップショットの継続的な更新")

エンティティが初期エクスポートの一部として追加されると、エンティティ データがデータ レイクに対応するフォルダー配下の entity.csv ファイルに書き込まれます。 これは T1 サイクル間隔で、*エンティティ*-T1.csv&mdash;という名前のスナップショット読み取り専用ファイル、例えば Account-T1.csv や Contacts-T1.csv&mdash;など、が作成されます。 さらに、これらのスナップショット ファイルをポイントするように model.json ファイルが更新されます。 model.json を開くと、スナップショットの詳細を表示できます。 

次に、データ レイクの Account.csv パーティション ファイルとスナップショット フォルダーの例を示します。

![アカウント エンティティのスナップショット](media/export-data-lake-account-snapshots.png "アカウント エンティティのスナップショット") 

Common Data Service の変更は、トリクル フィード エンジンを使用して、対応する CSV ファイルに継続的にプッシュされます。 これは T2 サイクル間隔で、別のスナップショットが取得されます。 *エンティティ*-T2.csv&mdash;例えば、Accounts-T2.csv や Contacts-T2.csv (エンティティに変更があると仮定) &mdash;、および model.json は新しいスナップショット ファイルに更新されます。 T2 以降のスナップショット データを表示する新しいユーザーは、新しいスナップショット ファイルに送信されます。 これにより、元のスナップショット ビューアは古いスナップショット T1 ファイルで引き続き動作し、新しいビューアは最新の更新を読み取ることができます。 これは、下流プロセスの実行時間が長い場合に役立ちます。 

model.json ファイルの例を次に示します。このファイルは、常に最新のタイムスタンプ付きアカウント スナップショッ トファイルを示します。 

![サンプル スナップショット model.json ファイル](media/sample-snapshot-json.png "サンプル スナップショット model.json ファイル") 

## <a name="transporting-an-export-to-data-lake-configuration-across-environments"></a>環境間での Data Lake にエクスポート 設定の転送

Power Apps では、ソリューションを利用して、アプリケーションおよびコンポーネントをある環境から別の環境に転送したり、既存のアプリケーションに一連のカスタマイズを適用したりします。 Data Lake にエクスポート 設定をソリューション対応にするには、Data Lake Coreにエクスポート ソリューションを環境に読み込みます。 これにより、Data Lake にエクスポート 設定の配布、バックアップ、復元などの基本的なアプリケーション ライフサイクル管理 (ALM) 機能が有効になります。 

### <a name="import-the-export-to-data-lake-core-solution"></a>Export to データ レイク Core ソリューションをインポートする

1.  Power Apps メーカー ポータルから、Data Lake にエクスポート 設定を配布する環境を選択します。
2.  左端のナビゲーション ウィンドウで、**ソリューション** を選択し、**AppSource を開く** を選択し、**Data Lake Core にエクスポート** という名称のソリューションを検索して、ソリューションをインポートします。

### <a name="add-an-export-to-data-lake-configuration-to-a-solution"></a>Data Lake にエクスポート 設定をソリューションに追加する

> [!IMPORTANT]
> Data Lake にエクスポート 設定を追加する前に、前述の Data Lake Core にエクスポート ソリューションをインストールする必要があります。 

1.  Power Apps メーカー ポータルから、Data Lakeにエクスポート 設定を配布する環境を選択し、左端のナビゲーション ウィンドウで、**ソリューション** を選択します。 
2.  **新しいソリューション** を選択し、名前を入力して公開元を選択してから、バージョン番号を指定します。  
3.  前述の手順で作成したソリューションを開き、**既存の追加** > **その他** > **データレイク構成へのエクスポート**を選択します。 
4.  リンクされたデータ レイク構成を選択し、続いて **追加** を選択します。 
5.  **ソリューション** 領域にて、ソリューションを選択し、コマンド バーで **エクスポート** を選択します。 
6.  **エクスポートする前に** ウィンドウで、 **公開する** を選択してエクスポートする前にすべての変更を公開し、続いて **次へ**を選択します。 

### <a name="import-the-solution-that-contains-the-export-to-data-lake-configuration"></a>Data Lake にエクスポート 設定を含むソリューションをインポートする

ソリューションのインポートを実行する環境で、Power Apps メーカー ポータル **ソリューション** 領域でソリューションをインポートします。 

#### <a name="verify-the-export-to-data-lake-configuration"></a>Data Lake にエクスポート 設定を確認する

Data Lake にエクスポート 設定をインポートした環境の Power Apps メーカー ポータルから、他の環境から転送したエンティティに加えて、リンクされたデータ レイクが表示されていることを確認します。

> [!div class="mx-imgBorder"] 
> ![インポートされた Data Lake にエクスポート エンティティ](media/imported-export-entities.png "インポートされた Data Lake にエクスポート エンティティ") 

### <a name="see-also"></a>関連項目

[ブログ: Azure データ レイク に CDS データをエクスポートする](https://powerapps.microsoft.com/blog/exporting-cds-data-to-azure-data-lake-preview/)
