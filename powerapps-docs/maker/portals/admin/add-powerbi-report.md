---
title: Power BI レポートまたはダッシュボードをポータルの Web ページに追加 | MicrosoftDocs
description: ポータルの Web ページへ Power BI レポートまたはダッシュボードを追加するための手順。
author: neerajnandwana-msft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 05/13/2019
ms.author: nenandw
ms.reviewer: tapanm
ms.openlocfilehash: e32b83dd3f667b4035a0b029af5c2c64f5e10d38
ms.sourcegitcommit: 2fd873a1ea17f419f6194714efffa47a9bd00c2e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "3506871"
---
# <a name="add-a-power-bi-report-or-dashboard-to-a-web-page-in-portal"></a>Power BI レポートまたはダッシュボードをポータルの Web ページに追加

[powerbi](../liquid/portals-entity-tags.md#powerbi) Liquid タグを使用して、Power BI レポートまたはダッシュボードをポータルの Web ページへ追加できます。 Web ページの**コピー**フィールドまたは Web テンプレートの**ソース**フィールドにタグを追加できます。 Power BI の新しいワークスペースに、作成した Power BI レポートやダッシュボードを追加する場合、*powerbi* タグの認証の種類を  **powerbiembedded** として指定する必要があります。

> [!TIP]
> この記事では、*powerbi* のリキッド タグを使用して Power BI レポートやダッシュボードを追加する方法について説明します。 ポータルスタジオを使用して、 **Power BI コンポーネント**を Web ページに追加するには、[ポータル スタジオを使用して Power BI コンポーネントを Web ページに追加する](../compose-page.md#add-power-bi) に移動します。

たとえば、次のようなものです。 

```
{% powerbi authentication_type:"powerbiembedded" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

> [!NOTE]
> powerbi Liquid タグの認証の種類として AAD を指定した場合、安全な Power BI レポートやダッシュボードをポータルの Web ページに追加する前に、必要なユーザーと共有する必要があります。 詳細: [Power BI ワークスペースの共有](https://docs.microsoft.com/power-bi/service-how-to-collaborate-distribute-dashboards-reports#collaborate-with-coworkers-in-an-app-workspace) と [Power BI ダッシュボードとレポートの共有](https://docs.microsoft.com/power-bi/service-share-dashboards)。

## <a name="get-the-path-of-a-dashboard-or-report"></a>ダッシュボードまたはレポートのパスを取得します。

1.  [Power BI](https://powerbi.microsoft.com/) にサインインします。

2.  ポータルで埋め込むダッシュボードまたはレポートを開きます。

3.  アドレス バーから URL をコピーします。

    > [!div class=mx-imgBorder]
    > ![Power BI ダッシュボードのパスを取得する](../media/powerbi-dashboard-url.png "Power BI ダッシュボードのパスを取得する")

## <a name="get-the-id-of-a-dashboard-tile"></a>ダッシュボード タイルの ID を取得

1.  [Power BI](https://powerbi.microsoft.com/) にサインインします。

2.  ポータルでタイルを埋め込むダッシュボードを開きます。

3.  タイルをポイントし、**その他のオプション**を選択してから、**フォーカス モードで開く**を選択します。

    > [!div class=mx-imgBorder]
    > ![フォーカス モードで Power BI ダッシュボード タイルを開く](../media/powerbi-dashboard-tile-focus.png "フォーカス モードで Power BI ダッシュボード タイルを開く")

4.  アドレス バーで URL からのタイル ID をコピーします。 タイル ID は /tiles/ の後ろの値です。

    > [!div class=mx-imgBorder]
    > ![Power BI ダッシュボード タイル ID](../media/powerbi-dashboard-tile-id.png "Power BI ダッシュボード タイル ID")


### <a name="see-also"></a>関連項目

- [ポータル スタジオを使用して、Power BI コンポーネントを Web ページに追加する](../compose-page.md#add-power-bi)
- [Power BI 統合の設定](set-up-power-bi-integration.md)
- [Power BIの Liquid タグ](../liquid/portals-entity-tags.md#powerbi)
