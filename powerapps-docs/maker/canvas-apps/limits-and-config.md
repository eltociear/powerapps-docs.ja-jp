---
title: キャンバス アプリのシステム要件、制限、および構成値 | Microsoft Docs
description: Power Apps で構築されたキャンバス アプリのシステム要件、制限、および構成値
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/19/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 7e434de24af417b5871c762d1aecd64cc41c5c72
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2020
ms.locfileid: "3308891"
---
# <a name="system-requirements-limits-and-configuration-values-for-canvas-apps"></a>キャンバス アプリのシステム要件、制限、構成の値
このトピックには、キャンバス アプリ用デバイス プラットフォーム、Web ブラウザーの要件、制限と構成値が含まれています。

## <a name="supported-platforms-for-running-canvas-apps-using-the-power-apps-mobile-app"></a>Power Apps モバイル アプリを使用して、キャンバス アプリを実行するためにサポートされているプラットフォーム

| **必要最小限** | **推奨** |
| --- | --- |
| iOS 12 以降 |iOS 12 以降|
| Android7 またはそれ以降 |Android7 またはそれ以降 |
| Windows 8.1 以降 (PC のみ) |Windows 10 Fall Creators Update、8 GB 以上のRAM)|

> [!NOTE]
> 現在、[Power Apps モバイル アプリ](/powerapps/user/run-app-client) 用 Windows プラットフォームの新機能はサポートされていません。 改良された Common Data Service オプションおよびゲスト アクセスなどの機能は、このプラットフォームでは使用できません。 Windows で Web プレーヤーを使い、すべての機能を活用することをお勧めします。 Windows プラットフォーム向け Power Apps モバイル アプリの更新プログラムは今後発表されます。

## <a name="supported-browsers-for-running-canvas-apps"></a>キャンバス アプリを実行するためにサポートされているブラウザー

| **ブラウザー** | **オペレーティング システム** |
| --- | --- |
| Google Chrome (最新バージョン)<br>(推奨) |Windows 7 SP1、8.1、10 <br>Android 5 またはそれ以降 <br>iOS 8 以降<br>macOS |
| Microsoft Edge (最新バージョン)<br>(推奨) |Windows 10 |
| Microsoft Internet Explorer 11 (互換表示オフで) |Windows 7 SP1、8.1、10 |
| Mozilla Firefox (最新バージョン) |Windows 7 SP1、8.1、10 <br> Android 5 またはそれ以降 <br>iOS 8 以降 <br>macOS |
| Apple Safari (最新バージョン) |iOS 8 以降 <br>macOS |

## <a name="supported-browsers-for-power-apps-studio"></a>Power Apps Studio 向けにサポートされているブラウザー

| **ブラウザー** | **オペレーティング システム** |
| --- | --- |
| Google Chrome (最新バージョン)<br>(推奨) |Windows 7 SP1、8.1、10 <br>macOS |
| Microsoft Edge (最新バージョン)<br>(推奨) |Windows 10 |
| Microsoft Internet Explorer 11 (互換表示オフで) |Windows 7 SP1、8.1、10 |

## <a name="request-limits"></a>要求の制限
これらの制限は、1 つの送信要求ごとに適用されます:

| 件名 | 制限 |
| --- | --- |
| タイムアウト |180 秒 |
| 再試行回数 |4 |

> [!NOTE]
> 再試行回数が異なる場合があります。 エラーの状況によっては、再試行は無意味です。

## <a name="ip-addresses"></a>IP アドレス
Power Apps からのリクエストは、IP アドレスが属する[環境](../../administrator/environments-overview.md) の領域に依存するアプリを使用します。 Power Apps シナリオで利用できる完全修飾ドメイン名は公開されていません。

アプリ経由で接続される API (たとえば、SQL API や SharePoint API) からの呼び出しでは、このトピックの後半で説明する IP アドレスを使用します。

たとえば、Azure SQL データベース用に IP アドレスをホワイトリスト登録する必要がある場合は、これらのアドレスを使用する必要があります。

> [!IMPORTANT]
>   既存の構成がある場合は、Power Apps アプリが存在する領域に関する一覧の IP アドレスが追加され、対応付けられるように、2018 年 9 月 30 日の前にできるだけ早く更新してください。

| 地域 | 送信 IP |
| --- | --- |
| アジア | 13.75.36.64 - 13.75.36.79、13.67.8.240 - 13.67.8.255、52.175.23.169、52.187.68.19、127.0.0.1 |
| オーストラリア  | 13.70.72.192 - 13.70.72.207、13.72.243.10、13.77.50.240 - 13.77.50.255、13.70.136.174、127.0.0.1 |
| ブラジル | 191.233.203.192 - 191.233.203.207、104.214.19.48 - 104.214.19.63、13.65.86.57、104.41.59.51、127.0.0.1 |
| カナダ | 13.71.170.208 - 13.71.170.223、13.71.170.224 - 13.71.170.239、52.237.24.126、40.69.106.240 - 40.69.106.255、52.242.35.152、127.0.0.1|
| ヨーロッパ | 13.69.227.208 - 13.69.227.223、52.178.150.68、13.69.64.208 - 13.69.64.223、52.174.88.118、137.117.161.181、127.0.0.1|
| インド  | 104.211.81.192 - 104.211.81.207、52.172.211.12、40.78.194.240 - 40.78.194.255、13.71.125.22、104.211.146.224 - 104.211.146.239、104.211.189.218、127.0.0.1 |
| 日本 | 13.78.108.0 - 13.78.108.15、13.71.153.19、40.74.100.224 - 40.74.100.239、104.215.61.248、127.0.0.1 |
| 南米 | 191.233.203.192 - 191.233.203.207、104.214.19.48 - 104.214.19.63、13.65.86.57、104.41.59.51、127.0.0.1 |
| 英国 | 51.140.148.0 - 51.140.148.15、51.140.80.51、51.140.211.0 - 51.140.211.15、51.141.47.105、127.0.0.1 |
| 米国 | 13.89.171.80 - 13.89.171.95、52.173.245.164、40.71.11.80 - 40.71.11.95、40.71.249.205、40.70.146.208 - 40.70.146.223、52.232.188.154、52.162.107.160 - 52.162.107.175、52.162.242.161、40.112.243.160 - 40.112.243.175、104.42.122.49、127.0.0.1 |
| 米国 (早期アクセス)  | 13.71.195.32 - 13.71.195.47、52.161.102.22、13.66.140.128 - 13.66.140.143、52.183.78.157、127.0.0.1 |

## <a name="required-services"></a>必要なサービス
このリストでは、Power Apps Studio の説明および使用法が適用されるすべてのサービスを識別します。 ネットワークはこれらのサービスをブロックしては **いけません**。

| ドメイン | プロトコル | 使用 |
| --- | --- | --- |
| api.bap.microsoft.com<br/>api.businessappdiscovery.microsoft.com | https | 環境アクセス許可の管理|
| management.azure.com |https |RP |
| msmanaged-na.azure-apim.net |https |コネクタ/API のランタイム |
| login.microsoft.com<br>login.windows.net<br>login.microsoftonline.com<br>secure.aadcdn.microsoftonline-p.com |https |ADAL |
| graph.microsoft.com<br>graph.windows.net |https |Azure Graph - ユーザー情報の取得用 (例: プロファイルの写真) |
| gallery.azure.com |https |サンプルおよびテンプレート アプリ |
| \*.azure-apim.net |https |Api Hubs - ロケールごとに異なるサブドメイン |
| \*.powerapps.com |https | create.powerapps.com、make.powerapps.com、content.powerapps.com、および make.powerapps.com |
| \*.azureedge.net |https | create.powerapps.com、make.powerapps.com、content.powerapps.com、および make.powerapps.com |
| \*.blob.core.windows.net |https | Blob Storage |
| \*.flow.microsoft.com | https | create.powerapps.com、make.powerapps.com、content.powerapps.com、および make.powerapps.com |
| \*.dynamics.com | https | Common Data Service |
| vortex.data.microsoft.com |https |テレメトリ |
| localhost | https | Power Apps モバイル|


> [!NOTE]
> VPN を使用している場合は、Power Apps Mobile のトンネリングから localhost を除外するように構成する必要があります。

## <a name="size-limits"></a>サイズの制限

テキスト、ハイパーリンク、画像、およびメディアのサイズ制限については、[データ型](functions/data-types.md#text-hyperlink-image-and-media) を参照してください。

## <a name="power-apps-per-app-plan"></a>アプリ プランごとの Power Apps

現在利用可能な情報については、Power Platform 管理ガイドの[アプリ プランごとの Power Apps](/power-platform/admin/signup-for-powerapps-admin#power-apps-per-app-plan) セクションを参照してください。
