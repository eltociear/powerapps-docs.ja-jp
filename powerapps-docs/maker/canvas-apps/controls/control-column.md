---
title: '列コントロール: リファレンス | Microsoft Docs'
description: このトピックでは Microsoft Power Apps の列コントロールに関する情報を提供します。
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/05/2017
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 6fcf4d94677a21f013734fedc8a4db70955f40b9
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3306131"
---
# <a name="column-control-in-power-apps"></a>Power Apps での列コントロール
[**データ テーブル**](control-data-table.md) コントロールの単一フィールドに表示エクスペリエンスを提供します。

## <a name="description"></a>内容
[**データ テーブル**](control-data-table.md) コントロールでは表形式でデータセットを表示し、その表形式の各列は**列**コントロールによって表されます。 **列**コントロールは、アプリ メーカーが列の外観と動作をカスタマイズするために使用できるプロパティを提供します。

## <a name="capabilities"></a>機能
### <a name="now-available"></a>入手可能
* **列**コントロールの幅を変更します。
* **列**コントロールのテキストを変更します。
* **列**コントロールの値をクリックまたはタップして移動します。

### <a name="not-yet-available"></a>現時点では利用不可
* **列**コントロールのスタイルをカスタマイズします。

### <a name="known-issues"></a>既知の問題
* **表示**プロパティは、まだ機能していません。

## <a name="properties"></a>プロパティ​​
* **DisplayName** – 列のヘッダーに表示されるテキスト。
  
  > [!NOTE]
  > このプロパティの名前は、間もなく **HeaderText** に変更されます。
  > 
  > 
* **IsHyperlink** – ハイパーリンクであることを示すために、列のデータに下線を付けるかどうかを示す値。
* [**幅**](properties-size-location.md) – **列**コントロールの左端と右端間の距離。

## <a name="examples"></a>例
### <a name="resize-a-column"></a>列のサイズを変更する
1. 空白のタブレット アプリを作成します。
2. **挿入**タブで、**データ テーブル**をクリックまたはタップしてから、画面全体をカバーするように**データ テーブル** コントロールのサイズを変更します。
3. 右側のウィンドウで、**データ ソースが選択されていません**の右側にある下矢印をクリックまたはタップしてから、**データ ソースの追加**をクリックまたはタップします。
4. 接続の一覧で、Common Data Service データベースの接続をクリックまたはタップします。
5. エンティティの一覧で、**アカウント**をクリックまたはタップしてから、**接続**をクリックまたはタップします。
   
    **データ テーブル** コントロールが初期化され、一連の既定のフィールドが表示されます。
6. **氏名**列をクリックまたはタップします。
   
    ![選択された列コントロール](./media/control-column/pre-resize-column.png)
7. 右側にある装飾をドラッグして、フィールドのサイズを変更します。
   
    ![サイズ変更された列コントロール](./media/control-column/post-resize-column.png)


## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
### <a name="screen-reader-support"></a>スクリーン リーダー サポート
* **DisplayName** が存在する必要があります。
