---
title: Power Apps プロジェクトのデータへのアクセスと保存 | Microsoft Docs
description: Power Apps プロジェクトの設計フェーズの一部として、必要な既存のデータにアクセスする場所と方法を文書化し、作成したデータを保存する場所を決定します。
author: taiki-yoshida
ms.service: powerapps
ms.topic: conceptual
ms.custom: guidance
ms.date: 06/16/2020
ms.author: tayoshi
ms.reviewer: kathyos
ms.openlocfilehash: cb6bf8fee5ede8128e982dd8e34b48801ff89559
ms.sourcegitcommit: 213c46f7055eb71b9064b0645d8d17cf8eaad179
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/16/2020
ms.locfileid: "3461576"
---
# <a name="wheres-the-data"></a>データはどこにあるか?

データを取得して保存するには、3 つの方法があります。

:::row:::
    :::column:::
        ![新しい日付](media/new-data.png "新しい日付")

        **新しいデータ** 既存のビジネス プロセスが紙を使用して行われた場合など、アプリがまだどこにも存在しないデータを作成している場合は、データを Common Data Service または SharePoint カスタム リストに保存することが推奨されます。 
        
        このトピックについては、[データ モデリング: データ構造の設計](data-modeling.md) で議論します。
    :::column-end:::
   :::column:::
        ![既存のシステムからの読み取り/書き込み](media/read-write.png "既存のシステムからの読み取り/書き込み")

       **既存のシステムからの読み取り/書き込み** これは、既存のデータ ベースまたはシステムから最新の情報を取得する必要があるタイプのデータです。 このような場合、必要なときにデータを要求する必要があります。
        
    :::column-end:::
    :::column:::
        ![既存データのコピーの作成](media/copy-data.png "既存データのコピーの作成")

        **データのコピーを作成する** 元のデータを変更または上書きしてはならない状況では、Common Data Service などの別のデータ ストアにデータをコピーできます。 これにより、元のシステムのデータが変更されないことが保証されますが、アプリはそれを使用できます。 このシナリオは、会計システムや収益関連システムでデータを操作する場合に一般的です。

    :::column-end:::
:::row-end:::

## <a name="accessing-existing-data"></a>既存データへのアクセス

Power Apps で作成されたアプリは、既存のデータを使用する 2 つの方法があります。 1 つは、データ ソースに直接接続できるコネクタを使用する方法です。 もう 1 つは、データのスナップ ショットをコピーするデータ フローを使用する方法です。

- **コネクタを使用する**: コネクタは、Power Apps の機能で、SharePoint、SQL サーバー、または Office 365&mdash;などのさまざまなシステムやソース&mdash;に接続し、そこから直接データを取得したりそこに保存できます。 詳細: [Power Apps のキャンバス アプリ コネクタの概要](../../maker/canvas-apps/connections-list.md)

- **データフローの使用**: データフローは Power Apps の機能で、ここで別のシステムから Common Data Service や Azure Data Lake Storage へとデータを抽出、変換、読み込みできます。
コネクタとは異なり、スケジュールされたバッチでデータをフェッチします。 データ ソースからデータをそのまま取得する代わりに、Power Query Onlineを使用して、ターゲット ストレージに保存する前にデータを操作、クレンジング、変換できます。 詳細: [データフローでセルフサービス データを準備する](../../maker/common-data-service/self-service-data-prep-with-dataflows.md)

選択する方法は、使用例とデータの処理方法によって異なります。 次の表に、比較に使用するいくつかの項目を示します。

|   比較する項目     | コネクタ                                   | データフロー                                           |
|-----------------------|----------------------------------------------|----------------------------------------------------|
| データの鮮度     | リアルタイム                                    | 静的またはスナップショット                                 |
| 通信方向             | 双方向                                | 一方向 (原点から Common Data Service へ) |
| 既存のデータを変更しますか？ | 有効                                          | No                                                 |
| 使用例             | 製造オーダー、タイムシート、販売見積 | 顧客マスター、過去の請求書、従業員リスト      |

次の記事で追加の技術情報、[エンタープライズ システムの作業](enterprise-systems.md) を提供します。

## <a name="example-expense-report-data"></a>例: 経費報告データ

私たちの経費報告プロジェクトには、3 種類のデータ ストレージのニーズがそれぞれ含まれています。

- **新しいデータ**: 経費報告書は紙に書かれていたため、経費報告書に記入する従業員が作成したデータ用の新しいストレージ システムが必要です。 そのためのデータ モデルを設計する必要があります。

- **既存のシステムへの書き込み**: 経理チームが費用レポートから財務システムにデータをエクスポートする場合、データ コネクタを使用する必要があります。

- **コピーしたデータ**: 経費レポートには、従業員ID、マネージャー、部門などの Azure Active Directory から調査したデータも含まれています。 元のシステムではそのデータを変更したくありませんが、そのコピーを保持する必要があります。 従業員の上司がレポートを作成した時点で (将来レポートをもう一度見直すときではなく)、その上司と部署を記録したいと考えています。 (部署を変更した、または会社を辞めたということがあるかもしれません。)

> [!div class="nextstepaction"]
> [次のステップ: エンタープライズ システムでの作業](enterprise-systems.md)