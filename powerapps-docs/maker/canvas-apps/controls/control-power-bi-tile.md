---
title: 'Power BI タイル コントロール: リファレンス | Microsoft Docs'
description: 各種プロパティとサンプルを含む、Power BI タイル コントロールに関する情報
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 07/07/2016
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 959f8eaee539febbb7c00441453da9bab23a1812
ms.sourcegitcommit: 263a12aefa72a3d73e07b2660bf1e89eba532a16
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "3309374"
---
# <a name="power-bi-tile-control-in-power-apps"></a>Power Apps での Power BI タイル コントロール

アプリ内の [Power BI](https://powerbi.microsoft.com) タイルを表示するコントロール。

Power BI を持っていない場合は? [サインアップ](https://docs.microsoft.com/power-bi/service-self-service-signup-for-power-bi)。

## <a name="description"></a>内容

アプリ内の **[Power BI タイル](https://docs.microsoft.com/power-bi/service-dashboard-tiles)** を表示することにより、既存のデータ分析とレポートを活用します。 オプション パネルの**データ** タブで **ワークスペース**、**ダッシュボード**、および**タイル** プロパティを設定することにより、表示するタイルを指定します。

## <a name="sharing-and-security"></a>共有とセキュリティ

Power BI コンテンツを含むアプリを共有するときは、アプリ自体だけでなく、タイルの取得元である [ダッシュボード](https://docs.microsoft.com/power-bi/service-how-to-collaborate-distribute-dashboards-reports) も共有する必要があります。 さもなければ、アプリを開いたユーザーにも Power BI コンテンツは表示されません。 Power BI コンテンツを含むアプリには、そのコンテンツに対するアクセス許可が適用されます。

## <a name="performance"></a>パフォーマンス

アプリ内に同時に 4 つ以上の Power BI タイルを読み込むことは推奨されません。 **LoadPowerBIContent** プロパティを設定することにより、タイルの読み込みとアンロードを制御できます。

## <a name="pass-a-parameter"></a>渡すパラメーター

アプリから単一のパラメーターを渡すことにより、Power BI タイルに表示される結果をフィルター処理できます。 ただし、サポートされているのは文字列値と等価演算子のみであり、テーブル名または列名にスペースが含まれていると、フィルターが機能しない場合があります。

単一のフィルター値を渡すには、次の構文に従って **TileURL** プロパティの値を変更します:

```
"https://app.powerbi.com/embed?dashboardId=<DashboardID>&tileId=<TileID>&config=<SomeHash>"
```

その値に、次の構文を追加します:

```
&$filter=<TableName>/<ColumnName> eq '<Value>'
```

パラメータでは、タイルの発生元であるレポートのデータセットの値をフィルター処理します。 ただし、フィルタリング機能には次の制限があります:

- 適用できるフィルターは 1 つのみです。
- `eq` 演算子のみがサポートされています。
- フィールド タイプは文字列でなければなりません。

Power BI レポートで計算フィールドを使用して、他の値のタイプを文字列に変換するか、複数のフィールドを 1 つに組み合わせることができます。

## <a name="key-properties"></a>主要なプロパティ

**ワークスペース** – タイルの取得元である Power BI ワークスペース。

**ダッシュボード** – タイルの取得元である Power BI ダッシュボード。

**タイル** – 表示する Power BI タイルの名前。

**LoadPowerBIContent** – true に設定すると、Power BI コンテンツが読み込まれて表示されます。 false に設定すると、Power BI コンテンツはアンロードされ、メモリが解放されてパフォーマンスが最適化されます。

## <a name="additional-properties"></a>追加のプロパティ

**[BorderColor](properties-color-border.md)** – コントロールの境界線の色。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線が**実線**、**破線**、**点線**、または**なし**かどうか。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さ。

**[DisplayMode](properties-core.md)** – コントロールがユーザー入力を許可するか (**編集**)、データのみを表示するか (**表示**)、または無効にするか (**無効**) どうか。

**[高さ](properties-size-location.md)** – コントロールの上端と下端間の距離。

**[OnSelect](properties-core.md)** – ユーザーがコントロールをタップまたはクリックする場合のアプリの反応方法。 既定では、タイルに関連付けられた Power BI レポートが開きます。

**TileUrl** – Power BI サービスからタイルが要求される URL。 URL にパラメーターを追加することで、Power BI タイルに単一のパラメーターを渡すことができます (例: … & "&$filter=Town/Province eq '" & ListBox1.Selected.Abbr & "'")。 パラメーターでは等価演算子のみを使用できます。

**[表示](properties-core.md)** – コントロールが表示されるか非表示になるか。

**[幅](properties-size-location.md)** – コントロールの左端と右端間の距離。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離。

## <a name="example"></a>例

1. **挿入**タブで、**コントロール** メニューを開いてから、**Power BI タイル** コントロールを追加します。

    [コントロールの追加および構成](../add-configure-controls.md) についてはこちらをご覧ください。

2. オプション パネルの**データ** タブで、**ワークスペース**設定の**マイ ワークスペース**をクリックまたはタップします。

3. ダッシュボードの一覧でダッシュボードを選択してから、タイルの一覧でタイルを選択します。

    コントロールでは、Power BI タイルを表示します。

## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン

**Power BI タイル**は、Power BI コンテンツのコンテナーです。 アクセシビリティ対応のコンテンツを作成する方法については、[Power BI のアクセシビリティに関するヒント](https://docs.microsoft.com/power-bi/desktop-accessibility) を参照してください。

Power BI コンテンツにタイトルがない場合は、**[ラベル](control-text-box.md)** コントロールを使用して見出しを追加し、スクリーン リーダーをサポートすることを検討してください。 ラベルは、Power BI タイルの直前に配置することができます。
