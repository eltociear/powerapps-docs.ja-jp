---
title: Azure ソリューションの Dynamics 365 データとの連携 (Common Data Service)| Microsoft Docs
description: ServiceBusPlugin プラグインには、Dynamics 365 メッセージ実行コンテキストを Azure Service Bus にポストするビジネス ロジックが含まれます。 このプラグインを使用するには、Azure Service Bus ソリューション エンドポイントとプラグインのステップを登録する必要があります。 このステップでは、コア Dynamics 365 操作によって処理されるメッセージとエンティティのどの組み合わせによって、プラグインの実行がトリガーされるかが定義されます。 ServiceBusPlugin は非同期に実行されるようにのみ登録できます。
keywords: ''
ms.date: 06/01/2019
ms.service: powerapps
ms.topic: article
ms.assetid: 1ef66369-71c9-3b89-ac1a-09d523ca737b
author: JimDaly
ms.author: jdaly
manager: ryjones
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 949717fbf33ee27e77ce81672fd66c2920a15bf2
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748915"
---
# <a name="work-with-common-data-service-data-in-your-azure-solution"></a>Azure ソリューションの Common Data Service データとの連携

`ServiceBusPlugin` という名前の内部プラグインが Common Data Service (CDS) で提供されます。 プラグインには、 CDS メッセージ実行コンテキストを Azure Service Bus に投稿するビジネス ロジックが含まれます。 このプラグインを使用するには、Azure Service Bus ソリューション エンドポイントとプラグインのステップを登録する必要があります。 このステップでは、コア CDS 操作によって処理されるメッセージおよびエンティティの組み合わせによって、実行するプラグインがトリガーされるかが定義されます。 `ServiceBusPlugin` は非同期に実行されるようにのみ登録できます。 詳細については、「[チュートリアル: プラグイン登録ツールを使用した Azure 対応プラグインの登録](walkthrough-register-azure-aware-plug-in-using-plug-in-registration-tool.md)」を参照してください。  
  
 また、サービス バスにポストする必要なコード行を含むカスタム プラグインを作成できます。 このプラグインも同様の方法で登録しますが、サンドボックスに登録して、部分信頼で実行する必要があります。 Azure Service Bus にポストできるカスタム プラグインの作成方法の詳細については、[Azure 対応のカスタム プラグインの記述](write-custom-azure-aware-plugin.md) を参照してください。  
  
 また、実行コンテキストをサービス バスにポストするユーザー定義のワークフロー活動を作成し、この活動をワークフローに含めることもできます。 ユーザー定義の Azure 対応ワークフロー活動のサンプル コードは、トピック [サンプル: Azure 対応のユーザー定義ワークフロー活動](/dynamics365/customer-engagement/developer/sample-azure-aware-custom-workflow-activity) で提供されています。 
  
### <a name="see-also"></a>関連項目  
[プラグインの記述](write-plug-in.md)<br/>
[イベント実行パイプライン](event-framework.md#event-execution-pipeline)<br/> 
[ServiceEndpoint エンティティ](reference/entities/serviceendpoint.md)<br/>