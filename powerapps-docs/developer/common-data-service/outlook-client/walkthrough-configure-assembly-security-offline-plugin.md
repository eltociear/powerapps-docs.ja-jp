---
title: 'チュートリアル: オフライン プラグインのアセンブリ セキュリティの構成(Common Data Service) | Microsoft Docs'
description: オフライン プラグインのアセンブリ セキュリティの構成についてチュートリアルが提供されます。
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: sriharibs
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: d2e7f675e9781e9792f9e9447103541a2d189816
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749244"
---
# <a name="walkthrough-configure-assembly-security-for-an-offline-plug-in"></a>チュートリアル: オフライン プラグインのアセンブリ セキュリティの構成

Common Data Service プラットフォームでは、登録済みオフライン プラグインのアセンブリに追加のセキュリティ制限が適用されます。 オフライン アクセス対応 Dynamics 365 for Microsoft Office Outlook のインストール時に、AllowList キーがクライアント コンピューターのシステム レジストリに追加されます。 オフライン プラグインを含むアセンブリを登録する場合は、アセンブリごとに AllowList キーの下にレジストリ サブキーを追加する必要があります。このキーには、アセンブリの公開キー トークンから派生した名前を付けます。 このキーを追加しないと、オフライン プラグインが登録されても、そのプラグインはプラットフォームで実行されません。 このチュートリアルでは、プラグインのアセンブリのサブキーを追加する方法について説明します。  
  
### <a name="get-the-public-key-token"></a>公開キー トークンの取得  
  
1.  オフライン プラグインを含むアセンブリをプラグイン登録ツールに読み込みます。 ツールの使用方法の詳細については [プラグインの登録](../register-plug-in.md) を参照してください。  
  
2.  ツールのツリー ビューでプラグインのアセンブリを選択します。  
  
3.  **公開キー トークン**フィールドの値を貼り付け用のバッファーにコピー (Ctrl+C) します。  
  
### <a name="add-an-allowlist-key"></a>AllowList キーの追加  
  
1.  **スタート**ボタンをクリックし、**ファイル名を指定して実行**を選択し、「`regedit.exe`」と入力して、レジストリ エディターを実行します。  
  
2.  ツリー ビュー ウィンドウで、**AllowList** キーに移動します。 キーの完全なパスは `HKEY_CURRENT_USER\Software\Microsoft\MSCRMClient\AllowList` です。  
  
3.  **AllowList** キーを選択して右クリックし、コンテキスト メニューを表示します。  
  
4.  **新規**を選択し、**キー**をクリックして新しいサブキーを作成します。  
  
5.  公開キー トークンの値を新しいサブキーの名前に貼り付けます。  
  
6.  レジストリ エディターを閉じます。  
  
### <a name="see-also"></a>関連項目  
 [プラグインの開発](/dynamics365/customer-engagement/developer/plugin-development)   
 [サンプル: 基本プラグインの作成](../org-service/samples/basic-followup-plugin.md)   
 [プラグインの登録および展開](/dynamics365/customer-engagement/developer/register-deploy-plugins)