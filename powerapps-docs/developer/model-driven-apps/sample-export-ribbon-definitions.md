---
title: 'サンプル: リボン定義をエクスポートする (モデル駆動型アプリ) | Microsoft Docs'
description: このサンプルは、リボン定義をエクスポートする方法を示します。 RetrieveApplicationRibbonRequestとRetrieveEntityRibbonRequest メッセージを使用します。
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: shilpas
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: a08a64d2e74298093e7c3b260b00f82d0b5aa51a
ms.sourcegitcommit: 6c73e316f866af6a34619f95a5ac64ad1664b48a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "3326425"
---
# <a name="sample-export-ribbon-definitions"></a>サンプル: リボン定義をエクスポートする

このサンプルでは、リボンの定義をエクスポートする方法を説明します。 ここでは、 [RetrieveApplicationRibbonRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.retrieveapplicationribbonrequest?view=dynamics-general-ce-9) と [RetrieveEntityRibbonRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.retrieveentityribbonrequest?view=dynamics-general-ce-9) メッセージを使用します。 サンプルは [ここ](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ExportRibbonDefinitions) からダウンロードできます。

## <a name="how-to-run-this-sample"></a>このサンプルを実行する方法

[!include[cc-how-to-run-samples](../common-data-service/includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>このサンプルの概要

`RetrieveApplicationRibbonRequest` メッセージは、アプリケーション リボンの内容と動作を定義するデータを取得するために必要なデータが含まれているシナリオで使用することを目的としています。 `RetrieveEntityRibbonRequest` メッセージは、エンティティに関するリボンの定義を取得するために必要なデータが含まれているシナリオで使用することを目的としています。

## <a name="how-this-sample-works"></a>このサンプルがどのように動作するか

[このサンプルは何をするか](#what-this-sample-does) で説明されているシナリオをシミュレートするために、サンプルは次のことを行います:

### <a name="setup"></a>セットアップ

組織の現在のバージョンをチェックします。

### <a name="demonstrate"></a>実際にやってみます

1. `RetrieveApplicationRibbonRequest` メソッドは、アプリケーションのリボンを取得します。
2. `RetrieveEntityRibbonRequest` メソッドは、システム エンティティのリボンを取得します

### <a name="clean-up"></a>クリーンアップ

このサンプルにはクリーンアップは不要です

  
### <a name="see-also"></a>関連項目  
 [コマンドとリボンのカスタマイズ](customize-commands-ribbon.md)   
 [リボンの使用による URL へのパラメーターの受け渡し](pass-parameters-url-by-using-ribbon.md)   
 [リボン コアのスキーマ](ribbon-core-schema.md) [リボン タイプのスキーマ](ribbon-types-schema.md) [リボン WSS のスキーマ](ribbon-wss-schema.md) <xref:Microsoft.Crm.Sdk.Messages.RetrieveApplicationRibbonRequest>   
 <xref:Microsoft.Crm.Sdk.Messages.RetrieveEntityRibbonRequest>
