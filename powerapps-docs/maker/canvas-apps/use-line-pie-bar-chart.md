---
title: キャンバス アプリでグラフを作成する | Microsoft Docs
description: Power Apps で、データのカテゴリを折れ線グラフ、円グラフ、または縦棒グラフとしてキャンバス アプリに表示します
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/23/2016
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8b5a5366f3de487b7d34d60d989274223340f4e6
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3306890"
---
# <a name="show-data-in-a-line-pie-or-bar-chart-in-power-apps"></a>Power Apps でデータを折れ線グラフ、円グラフ、または縦棒グラフで表示する

折れ線グラフ、円グラフ、および縦棒グラフを使用して、キャンバス アプリにデータを表示します。 グラフを使用する場合、インポートするデータは次の条件に基づいて構造化されている必要があります。

* 各系列が最初の行にある必要があります。
* ラベルが左端の列にある必要があります。

たとえば、データは次のようになっている必要があります。

![][9]

Power Apps 内で、これらのグラフを作成し、使用することができます。 それでは始めましょう。

## <a name="prerequisites"></a>前提条件

* Power Apps に[サインアップ](../signup-for-powerapps.md) し、サインアップに使用した同じ資格情報を使用して[サインイン](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) します。
* [テンプレート](get-started-test-drive.md)から、[データ](get-started-create-from-data.md)から、または[一](get-started-create-from-blank.md)からアプリを作成します。
* Power Apps で[コントロールを構成する](add-configure-controls.md)方法を説明します。
* XML ファイルとしてサンプル データが含まれた [ChartData.zip](https://pwrappssamples.blob.core.windows.net/samples/ChartData.zip) をダウンロードします。 このトピックの手順に従って直接アプリにインポートします。 代替策として、.zip file を解凍し、XML ファイルを開き、[クラウド ストレージ アカウント](connections/cloud-storage-blob-connections.md) に保存します。

## <a name="import-the-sample-data"></a>サンプル データをインポートする
以下の手順では、**ProductRevenue** という名前のコレクションにサンプル データをインポートします。

1. **挿入**タブで **コントロール**を選択し、**インポート**を選択します。  

    ![][11]  

2. コントロールの **[OnSelect](controls/properties-core.md)** プロパティを次の関数に設定します。  

   ```Collect(ProductRevenue, Import1.Data)```

3. F5 を押してプレビュー モードで開き、**データのインポート** ボタンを選択します。

4. **開く**ダイアログ ボックスで、ChartData.zip を選択し、**開く**を選択して、次に Esc を押します。

5. **ファイル** メニュ－で**コレクション**を選択します。

    ProductRevenue コレクションは、インポートしたグラフ データとリストされます。

    ![][1]  

   > [!NOTE]
   > インポート コントロールの目的は、Excel と同様のデータをインポートしてコレクションを作成することです。 インポート コントロールによってデータがインポートされるのは、アプリの作成時とアプリのプレビュー時です。 現在、アプリの発行時には、データはインポートされません。
   >

6. 既定のワークスペースに戻るには、Esc キーを押します。

## <a name="add-a-pie-chart"></a>円グラフを追加する
1. **挿入**タブで**グラフ**を選択し、次に**円グラフ**を選択します。

2. **データのインポート** ボタンの下に円グラフを移動します。

3. 円グラフ コントロールで、円グラフの中心を選択します。   

    ![][10]

4. 円グラフの **[Items](controls/properties-core.md)** プロパティをこちらの式に設定します: `ProductRevenue.Revenue2014`

    ![][2]  

    円グラフに、2014 年の売り上げデータが表示されます。

    ![][3]  

## <a name="add-a-bar-chart-to-display-your-data"></a>縦棒グラフを追加してデータを表示する
次に、この ProductRevenue コレクションを縦棒グラフで使用してみましょう。

1. **ホーム** タブで、スクリーンを追加します。

2. **挿入**タブで**グラフ**を選択し、次に**縦棒グラフ**を選択します。

3. 縦棒グラフの中心を選択します。 縦棒グラフの **[Items](controls/properties-core.md)** プロパティを ```ProductRevenue``` に設定します。

    ![][12]  

    縦棒グラフに、2012 年の売上データが表示されます。

    ![][4]  

4. 縦棒グラフで中央の正方形を選択します。

    ![][5]

5. **グラフ** タブで**系列の数**を選択し、次に数式バーに **3** と入力します。

    ![][6]  

    縦棒グラフに、3 年以上の各製品の売上データが表示されます。

    ![][7]  

[1]: ./media/use-line-pie-bar-chart/productrevenuecollection.png
[2]: ./media/use-line-pie-bar-chart/itemsexpression.png
[3]: ./media/use-line-pie-bar-chart/piechart.png
[4]: ./media/use-line-pie-bar-chart/columnchart.png
[5]: ./media/use-line-pie-bar-chart/columnchartseries.png
[6]: ./media/use-line-pie-bar-chart/columnchartseriesfunction.png
[7]: ./media/use-line-pie-bar-chart/columnchartthreeyears.png
[8]: ./media/use-line-pie-bar-chart/preview.png
[9]: ./media/use-line-pie-bar-chart/tableformat.png
[10]: ./media/use-line-pie-bar-chart/middlepiechart.png
[11]: ./media/use-line-pie-bar-chart/import.png
[12]: ./media/use-line-pie-bar-chart/itemscolumnchart.png
