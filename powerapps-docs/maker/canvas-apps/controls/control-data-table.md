---
title: 'データ テーブル コントロール: リファレンス | Microsoft Docs'
description: プロパティとサンプルを含む、データ テーブル コントロールに関する情報
author: jasongre
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/05/2017
ms.author: jasongre
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 4eaa58bc7bb27746a574c52fcd49253858a471ca
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3306085"
---
# <a name="data-table-control-in-power-apps"></a>Power Apps でのデータ テーブル コントロール
一連のデータを表形式で表示します。

## <a name="description"></a>内容
**データ テーブル** コントロールには、コントロールが表示する各フィールドの列ヘッダーを含む形式でデータセットが表示されます。 アプリ メーカーとして、表示されるフィールドやその順序を完全にコントロールできます。 **ギャラリー** コントロールと同様、**データ テーブル** コントロールには、選択した行を指す**選択済み**プロパティが保持されます。 したがって、**データ テーブル** コントロールは他のコントロールにリンクできます。

## <a name="capabilities"></a>機能
Power Apps では、2017 年 5 月 5 日に**データ テーブル** コントロールが導入されました。 このセクションでは、サポートされている機能とサポートされていない機能に関する情報を提供します。

### <a name="now-available"></a>入手可能
* **データ テーブル** コントロールのデータは読み取り専用です。
* **データ テーブル** コントロールでは常に単一行が選択されます。
* **データ テーブル** コントロールを接続されたデータ ソースまたはローカル データ ソースにリンクします。
* アプリの実行中に**データ テーブル** コントロールの列幅を調整しますが、変更は保存されません。
* Common Data Service など、この機能を実装したコネクターにリンクすると、一連の既定フィールドが**データ テーブル** コントロールに表示されます。 その後、必要に応じてこれらのフィールドや他のフィールドを表示または非表示にできます。
* 列幅や見出しテキストをカスタマイズします。
* **データ テーブル** コントロールでのハイパーリンクを表示します。
* **データ テーブル** コントロールをコピーして貼り付けます。

### <a name="not-yet-available"></a>現時点では利用不可
* 個々の列のスタイルをカスタマイズします。
* **データ テーブル** コントロールをフォーム コントロールに追加します。
* すべての行の高さを変更します。
* **データ テーブル** コントロールで画像を表示します。
* 関連エンティティからのフィールドを表示します。
* 組み込み機能を使用して列見出しによるデータのフィルター処理および並べ替えをします。
* **データ テーブル** コントロールを**ギャラリー** コントロールに追加します。
* **データ テーブル** コントロールでデータを編集します。
* 複数行を選択します。

### <a name="known-issues"></a>既知の問題
* **Items** プロパティで **FirstN** 関数を使用すると、データが表示されません。

## <a name="key-properties"></a>主要なプロパティ
* [**項目**](properties-core.md) – **データ テーブル** コントロールに表示されるデータのソース。
* **選択済** – **データ テーブル** コントロールで選択された行。

## <a name="other-properties"></a>その他のプロパティ
* [**BorderColor**](properties-color-border.md) – **データ テーブル** コントロールの境界線の色。
* [**BorderStyle**](properties-color-border.md) – **データ テーブル** コントロールの境界線のスタイル。 オプションは、**実線**、**破線**、**点線**、および**なし**です。
* [**BorderThickness**](properties-color-border.md) – **データ テーブル** コントロールの境界線の太さ。
* [**Color**](properties-color-border.md) – すべてのデータ行の既定のテキスト色。
* [**Fill**](properties-color-border.md) – すべてのデータ行の既定の背景色。
* [**フォント**](properties-text.md) – すべてのデータ行の既定のフォント。
* [**FontWeight**](properties-text.md) – すべてのデータ行の既定のフォントの太さ。
* **HeadingColor** – 列見出しのテキストの色。
* **HeadingFill** – 列見出しの背景色。
* **HeadingFont** – 列見出しのフォント。
* **HeadingFontWeight** – 列見出しのフォントの太さ。
* **HeadingSize** – 列見出しのフォント サイズ。
* [**高さ**](properties-size-location.md) – **データ テーブル** コントロールの上端と下端間の距離。
* [**HoverColor**](properties-color-border.md) – マウス ポインターが指している行のテキストの色。
* [**HoverFill**](properties-color-border.md) – マウス ポインターが指している行の背景色。
* **NoDataText** – **データ テーブル** コントロールに表示するレコードがないときに、ユーザーが受け取るメッセージ。
* **SelectedColor** – 選択された行のテキストの色。
* **SelectedFill** – 選択した行の背景色。
* [**サイズ**](properties-text.md) – すべてのデータ行の既定のフォント サイズ。
* [**表示**](properties-core.md) – **データ テーブル** コントロールが表示または非表示になるかを決定する値。
* [**幅**](properties-size-location.md) – **データ テーブル** コントロールの左端と右端間の距離。
* [**X**](properties-size-location.md) – **データ テーブル** コントロールの左端とその親コンテナーの左端 (親コンテナーがない場合は画面の左端) との間の距離。
* [**Y**](properties-size-location.md) – **データ テーブル** コントロールの上端とその親コンテナーの上端 (親コンテナーがない場合は画面の上端) との間の距離。

## <a name="related-functions"></a>関連する関数
* [**Filter(DataSource, 数式)**](../functions/function-filter-lookup.md)(*DataSource*, *数式*)
* [**Search(DataSource、SearchString、列)**](../functions/function-filter-lookup.md)(*DataSource*、*SearchString*、*列*)

## <a name="examples"></a>例
### <a name="basic-usage"></a>基本的な使用方法
1. 空白のタブレット アプリを作成します。
2. **挿入**タブで、**データ テーブル**をクリックまたはタップします。
   
    ![データ テーブル コントロールを画面に追加する](./media/control-data-table/insert-data-table.png)
   
    **データ テーブル** コントロールが画面に追加されます。
3. **データ テーブル** コントロールを **SalesOrderTable** に名前変更し、画面全体をカバーするようにサイズ変更します。
4. 右側のウィンドウで、**データ ソースが選択されていません**のテキストの右側にある下矢印をクリックまたはタップしてから、**データ ソースの追加**をクリックまたはタップします。
   
    ![データ ソースの追加](./media/control-data-table/add-data-to-data-table.png)
5. 接続の一覧で、Common Data Service データベースの接続をクリックまたはタップします。
   
    ![データ ソースの接続を選択する](./media/control-data-table/choose-cds-data-table.png)
6. エンティティの一覧で、**販売注文**をクリックまたはタップしてから、**接続**をクリックまたはタップします。
   
    ![受注エンティティを選択する](./media/control-data-table/choose-so-data-table.png)
   
    **データ テーブル** コントロールが**受注**データ ソースに添付されるようになりました。 その機能をサポートするコネクタを使用しているため、いくつかの初期フィールドが**データ テーブル** コントロールに表示されます。
   
    ![データ テーブル](./media/control-data-table/pre-order-data-table.png)
7. 右側のウィンドウで、1 つ以上のチェック ボックスを選択して、個々のフィールドを表示または非表示にします。
   
    たとえば、**CustomerPurchaseOrderReference** の横にあるチェック ボックスを選択して、このフィールドを非表示にします。
8. 右側のウィンドウで、フィールドを上下にドラッグして、フィールドの順序を変更します。
   
    ![必要に応じてフィールドの順序を変更する](./media/control-data-table/field-re-order-data-table.png)
   
    **SalesOrderTable** コントロールでは、指定した順序でフィールドが表示されます。
   
    ![更新されたデータ テーブル](./media/control-data-table/post-order-data-table.png)

### <a name="restyle-the-header-for-the-data-table-control"></a>データ テーブル コントロールのヘッダーをスタイル変更する
1. **データ テーブル** コントロールが選択されている間に、右側のウィンドウの**詳細**タブをクリックまたはタップします。
2. **HeadingFill** プロパティのフィールドをクリックまたはタップしてから、値を **RGBA(62,96,170,1)** に変更します。
3. **HeadingColor** プロパティのフィールドをクリックまたはタップしてから、値を**白**に変更します。
4. **HeadingSize** プロパティのフィールドをクリックまたはタップしてから、値を **14** に変更します。
   
    ![データ テーブル](./media/control-data-table/restyled-data-table.png)

### <a name="connect-a-data-table-control-to-another-control"></a>データ テーブル コントロールを別のコントロールに接続する
1. **編集フォーム**コントロールを画面に追加します。
2. **データ テーブル**と**編集フォーム** コントロールのサイズを変更して、**データ テーブル** コントロールが画面の左側、**編集フォーム** コントロールが画面の右側の部分に表示されるようにします。
   
    ![同じ画面上のデータ テーブルと編集フォーム](./media/control-data-table/data-table-empty-form.png)
3. **Form1** が選択されている間に、右側のウィンドウで、列の数を **1** に変更します。
4. **Form1** を**受注**データ ソースに接続します。
   
    いくつかの初期フィールドが **Form1** に表示されます。
   
    ![初期フィールドを含む Form1](./media/control-data-table/data-table-disconnected-form.png)
5. 右側のウィンドウで、**詳細**タブをクリックまたはタップします。
6. **Form1** の**項目**プロパティを **SalesOrderTable.Selected** に設定します。
   
    **Form1** には、**データ テーブル** コントロールで選択された行からの情報が表示されます。
   
    ![データ テーブルに接続された編集フォーム](./media/control-data-table/connected-form-data-table.png)


## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
### <a name="color-contrast"></a>色のコントラスト
次の間には適切な色のコントラストが必要です:
* [**色**](properties-color-border.md) と [**塗りつぶし**](properties-color-border.md)
* **HeadingColor** と **HeadingFill**
* **SelectedColor** と **SelectedFill**
* [**HoverColor**](properties-color-border.md) と [**HoverFill**](properties-color-border.md)

これは、[標準の色のコントラスト要件](../accessible-apps-color.md) に追加されるものです。

### <a name="screen-reader-support"></a>スクリーン リーダー サポート
* **NoDataText** が存在する必要があります。
