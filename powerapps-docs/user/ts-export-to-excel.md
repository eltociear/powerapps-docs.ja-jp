---
title: Excel へのエクスポートに関するトラブルシューティング | MicrosoftDocs
description: Excel へのエクスポートに関するトラブルシューティング
ms.date: 06/30/2020
ms.service:
- dynamics-365-sales
ms.topic: article
author: udaykirang
ms.author: udag
manager: shujoshi
ms.openlocfilehash: 8a1796d906b947b2ad14fa31cc1caceef2ab5fc5
ms.sourcegitcommit: 44a0db26e7fa3a1525f6238ac222385321c0e65c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/30/2020
ms.locfileid: "3519440"
---
# <a name="troubleshoot-export-to-excel"></a>Excel へのエクスポートに関するトラブルシューティング

## <a name="data-disappears-after-i-refresh-the-imported-excel-file"></a>インポートした Excel ファイルを更新した後にデータが消える

**問題**

**Excel へエクスポート** コマンドを使用してローカル コンピューターにファイルをエクスポートした後、ファイルを開いて **データ** の **すべて更新** を選択しました。 データが消えて、ワークブックが空白で表示されます。

**解決**

この問題は、アクセスしているデータがパスワードで保護されており、Excel ファイルが外部データソースにパスワードを送信できない場合に発生します。 この問題を解決するには、Web クエリを編集して保存する必要があります。

1. Excel ファイルで、**データ** > **クエリと接続** を選択します。

    > [!div class="mx-imgBorder"]
    > ![データを選択し、クエリと接続を選択します](media/ts-e2e-select-queries-connections.png "データを選択し、クエリと接続を選択します")

    **クエリと接続** ウィンドウがウィンドウの右側に開きます。

    > [!div class="mx-imgBorder"]
    > ![クエリと接続ペイン](media/ts-e2e-queries-connections-pane.png "クエリと接続ペイン")

2. **接続** タブを右クリックして、**Query_from_Microsoft_CRM** クエリを右クリックして、**プロパティ** を選択します。

    > [!div class="mx-imgBorder"]
    > ![プロパティを選択する](media/ts-e2e-select-properties-from-query.png "プロパティを選択する")

    **プロパティの接続** ウィンドウが開きます。

3. **説明** タブで、**クエリの編集** を選択します。

    > [!div class="mx-imgBorder"]
    > ![クエリの編集の選択](media/ts-e2e-select-edit-query.png "クエリ編集を選択する")

4. **Go** を選択します。

    > [!div class="mx-imgBorder"]
    > ![エラー メッセージ](media/ts-e2e-error-message.png "エラー メッセージ")

5. 表示されるエラーメッセージで、**OK**、**インポート** を選択します。

6. **Web クエリの編集** ウィンドウを閉じて、データを更新します。
