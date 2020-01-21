---
title: 'サンプル: データ マップのエクスポートおよびインポート (Common Data Service) | Microsoft Docs'
description: このサンプルでは、データ マップを作成し、エクスポートする方法を示しています。
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: samples
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: c87fb5601d01eaffb832c2b9b9452a3925ac2097
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934291"
---
# <a name="sample-export-and-import-a-data-map"></a>サンプル: データ マップのエクスポートおよびインポート

このサンプルは、 Common Data Service でインポート マップ (データ マップ) を作成し、それを XML 形式のデータとしてエクスポートしてから、変更したマッピングをインポートし、そのインポート済みのマッピングに基づいて新しいインポート マップ Common Data Service を作成する方法を示します。 サンプルは[ここ](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ExportImportDataMap)からダウンロードできます。

## <a name="how-to-run-this-sample"></a>このサンプルを実行する方法

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>このサンプルの概要

`BulkDeleteRequest` メッセージは、一括削除要求を作成する必要があるデータが含まれているシナリオで使用するためのものです。

## <a name="how-this-sample-works"></a>このサンプルがどのように動作するか

[このサンプルの概要](#what-this-sample-does) で説明されているシナリオをシミュレートするために、サンプルは次のことを行います。

### <a name="setup"></a>セットアップ

1. 組織の現在のバージョンをチェックします。 
2. `CreateImportMapping` メソッドは、インポート マッピング レコードを作成します。
3. `RetrieveMappingXML` メソッドは、作成されたマッピングをエクスポートします。
4. `ChangeMappingName` メソッドは、名前属性を変更するために xml を解析します。

### <a name="clean-up"></a>クリーン アップ

[セットアップ](#setup) で作成されたサンプル データを削除するためのオプションを表示します。 サンプルで作成されるエンティティおよびデータを検証する場合、削除は任意です。 手動でレコードを削除することで同じ結果を得られます。


### <a name="see-also"></a>関連項目

[データのインポート](../../import-data.md)<br />
[ソース ファイルのインポートを準備する](../../prepare-source-files-import.md)<br />
[インポート用データ マップの作成](../../create-data-maps-for-import.md)<br />
[インポート用の変換マッピングの追加](../../add-transformation-mappings-import.md)<br />
[データ インポートの構成](../../configure-data-import.md)<br />
[データ インポートの実行](../../run-data-import.md)<br />
[データ インポート エンティティ](../../data-import-entities.md)<br />
[サンプル: 複雑なデータ マップを使用してデータをインポートする](import-data-complex-data-map.md)<br />
