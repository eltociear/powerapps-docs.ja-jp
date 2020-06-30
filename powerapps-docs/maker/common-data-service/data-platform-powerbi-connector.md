---
title: Common Data Service コネクタを使用して PowerBI レポートを作成する | Microsoft Docs
description: Common Data Service コネクタを使用して Power BI Desktop からデータに接続する。
author: Mattp123
manager: kvivek
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 05/26/2020
ms.author: matp
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 1f2d62a618b12935a37f507eb2d691b86c01f1fe
ms.sourcegitcommit: 8a8ec297eccf3b4233031f7548b5c99f0f1d7c41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/27/2020
ms.locfileid: "3405695"
---
# <a name="create-a-power-bi-report-using-the-common-data-service-connector"></a>Common Data Service コネクタを使用して Power BI レポートを作成する
Common Data Service を使用すると、 Power BI Desktop を使用してデータに直接接続し、レポートを作成してPower BIに発行することができます。 Power BI からは、ダッシュボードでレポートを利用したり、他のユーザーと共有したり、 Power BI のモバイル アプリでクロス プラットフォームでアクセスすることができます。

![Power BI Desktop](./media/data-platform-cds-powerbi-connector/PBIDesktop.png "Power BI Desktop")

## <a name="prerequisites"></a>前提条件

Common Data Service で  Power BI を使用するには、以下の項目が必要となります :

* Power BI Desktop をダウンロードしてインストールします。これはローカル コンピュータで動作する無料のアプリケーションです。 Power BI desktopは [こちら](https://powerbi.microsoft.com/desktop/)でダウンロードできます。
* Common Data Service 環境はエンティティー内のデータにアクセスするための読み取り権限とポータルへのアクセス権限を持っています。

## <a name="finding-your-common-data-service-environment-url"></a>Common Data Service 環境のURL を選択します。

1. [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) を開き、接続する環境を選択し、右上隅にある**設定**を選択し、続いて**高度な設定**を選択します。

   <!-- ![Common Data Service Environment](./media/data-platform-cds-powerbi-connector/CDSEnv1.png "Common Data Service Environment") -->

2. 開いた新しいブラウザタブで、URL のルート部分をコピーします。 これは、環境固有の URL です。 URL の形式は、**https://yourenvironmentid.crm.dynamics.com/** のようになります。 残りの URL はコピーしないでください。 Power BI レポートの作成時に使用できるよう、どこか便利な場所に保管してください。

    > [!div class="mx-imgBorder"] 
    > ![Common Data Service 環境 URL](./media/data-platform-cds-powerbi-connector/CDSEnv3.png "Common Data Service 環境 URL")

## <a name="connecting-to-common-data-service-from-power-bi-desktop"></a>Power BI Desktop から Common Data Service に接続する

1. **Power BI Desktop** を開きます。 **ファイル** > **データの取得**を選択し、続いて **データを取得してスタートする** を選択して、Power BI Desktop で使用するデータソースの完全なリストを開きます。

    <!-- ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport1.png "Power BI Desktop") -->

2. **検索** ボックスで*一般* と入力し、**Common Data Service** を選択します。続いて **接続**を選択します。

    > [!div class="mx-imgBorder"] 
    > ![Common Data Service に接続する Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport2.png "Power BI Desktop を Common Data Service に接続します")

3. 表示された **Common Data Service** ダイアログ ボックスで、Common Data Service 環境に URL を**サーバーの URL**ボックスに貼り付け、**OK**を選択します。 Power Apps や Common Data Service に接続する際に使用したものと同じ認証情報を使用してサインインを促される場合があります。 **接続** を選択します。

   <!-- ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport3.png "Power BI Desktop") -->

4. **ナビゲーター** は、2 つのフォルダーにグループ化された環境に対して使用可能なすべてのエンティティを表示します。 

    * エンティティ - 環境で作成された、またはインポートした標準エンティティおよびユーザー定義のエンティティです。
    * システム - システム エンティティを含む、環境内のすべてのエンティティが含まれます。

   <!-- ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport4.png "Power BI Desktop") -->

5. **取引先企業** のエンティティを選択し、右ウィンドウでデータのプレビューを表示します。 **読み込み** を選択します。

    > [!div class="mx-imgBorder"] 
    > ![取引先企業エンティティ レコードの読み込み](./media/data-platform-cds-powerbi-connector/CreateReport5.png "取引先企業エンティティ レコードの読み込み")

6. エンティティがレポートに読み込まれ、レポートの作成を開始や、前述の手順を繰り返してエンティティを追加することもできます。 たとえば、**フィールド** ウィンドウで、**名前**を選択し、続いて**numberofemployees**を選択します。 **視覚化**ウィンドウで、**円グラフ**を選択します。 これにより、レポート キャンバスに新たな視覚化が追加されます。 

    > [!div class="mx-imgBorder"] 
    > ![Power BI Desktop の資格化](./media/data-platform-cds-powerbi-connector/CreateReport7.png "Power BI Desktop の視覚化")


## <a name="using-option-sets"></a>オプション セットの使用

オプション セットは、アプリやフローでユーザーに値のドロップダウン リストを提供する目的でエンティティで使用されます。 Power BI コネクタを使用している場合、オプション セット フィールドは 2 つの列として示され、一意の値と表示値の両方を表示します。

たとえば、ApprovalStatus というエンティティのオプション セットの場合、Power BI に 2 つのフィールドが表示されます。

* ApprovalStatus - オプション セットの各アイテムに対する一意の整数値を示します。フィルター適用時の補助であり、後で表示名を変更しても影響を受けません。
* ApprovalStatus_display - アイテムのフレンドリ表示名を示し、一般的にテーブルまたはグラフのオプションを表示する場合に使用されます。

    |ApprovalStatus|ApprovalStatus_Display|
    |---------|---------|
    1|[提出済み]
    2|レビュー中
    3|承認済み
    4|拒否済み

## <a name="navigating-relationships"></a>ナビゲーションの関連付け

Common Data Service の関連付けには GUID フィールドを使用する 2 つのエンティティ間で、Power BI desktop 内での関連付けを作成する必要があります。これは他のフィールドとのあいまいさ、または重複が存在する場合のある作成レコードに対して関連付けが作成されていることを確認する目的で、システムが生成する一意の識別子です。 Power BI Desktop の関連付けの管理については、 [こちら](https://docs.microsoft.com/power-bi/desktop-create-and-manage-relationships) をご覧ください。

関連付けは自動的に作成される場合もありますが、レポートを作成する際にレビューを行い、正しい関連付けが確立されているかどうかを確認することができます。

* エンティティの検索フィールドには、関連エンティティのレコードの GUID が含まれます。
* 関連エンティティには、GUID を含む "[EntityName]ID" 形式のフィールドがあります。たとえば、Accountid または MyCustomEntityid などがあります
* Power BI desktop の関連付け管理機能を使用して、検索フィールドと関連エンティティの ID フィールド間で新たな関連付けを作成します。


## <a name="next-steps"></a>次のステップ
* [エンティティでのフィールドの管理](data-platform-manage-fields.md)
* [エンティティ間での関連付けの定義](data-platform-entity-lookup.md)


