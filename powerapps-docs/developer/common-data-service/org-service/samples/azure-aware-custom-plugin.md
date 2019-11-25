---
title: Azure 対応の カスタム プラグイン (Common Data Service) | Microsoft Docs
description: これはパイプライン実行コンテキストを Azure Service Bus にポストできるプラグインのサンプルです。
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 1148a8e6194a5aa78cda9f01c458c8c817dd261c
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749103"
---
# <a name="sample-azure-aware-custom-plug-in"></a>サンプル: Azure 対応のカスタム プラグイン

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-azure-aware-custom-plugin -->

このプラグインは、`Execute` メソッドのサービス プロバイダー パラメーターから実行コンテキストとトレース サービスを取得する方法を示しています。 プラグインは、次にコンテキストを Azure サービス バス エンドポイントにポストし、トレース ログに情報を書き込んでプラグインを容易にデバッグできるようにします。 サンプルは [ここ](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/Azureplugin) からダウンロードできます。

## <a name="how-to-run-this-sample"></a>このサンプルを実行する方法

1. [サンプル](https://github.com/Microsoft/PowerApps-Samples) リポジトリをダウンロードまたは複製して、ローカル コピーを用意します。
2. サンプル ソリューションを Visual Studio で開き、キーでアセンブリに署名します。
3. **プラグイン登録ツール**を使用したプラグインの登録

>[!NOTE]
> このサンプルでは、サービス エンドポイントが最初に作成される必要があり、プラグイン ステップが登録されたときに、その ID がセキュリティ保護されていない構成パラメーターを介してプラグイン コンストラクターに渡されます。


