---
title: コマンドとリボンのカスタマイズ (モデル駆動型アプリ) | MicrosoftDocs
description: Common Data Service は、エンティティおよびクライアントに応じてさまざまな方法でコマンドを表示します。 Web アプリケーションの大抵の場所で、リボンの代わりにコマンド バーが表示されます。 また、タブレット PC 用 Dynamics 365 はリボンとして定義されたデータを使用して、タッチ操作のために最適化されたコマンド バーを使用してどのコマンドを使用できるかコントロールします。
keywords: ''
ms.date: 03/27/2020
ms.service: powerapps
ms.topic: article
ms.assetid: 926364b0-ede6-00e9-39d4-5aae5e00be0b
author: Nkrb
ms.author: nabuthuk
manager: shilpas
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 27b041e7a62b76bab7e920deac9a8933accf4fca
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/21/2020
ms.locfileid: "3275947"
---
# <a name="customize-commands-and-the-ribbon"></a>コマンド、およびリボンをカスタマイズする

Common Data Service は、エンティティおよびクライアントに応じてさまざまな方法でコマンドを表示します。 Web アプリケーションの大抵の場所で、リボンの代わりに*コマンド バー*が表示されます。 

また、Dynamics 365 for Tablets はリボンとして定義されたデータを使用して、タッチ操作のために最適化されたコマンド バーを使用してどのコマンドを使用できるかコントロールします。  
  
コマンド バーは、より良いパフォーマンスを提供します。 リボンは、特定のエンティティ フォームでは Web アプリケーションでまだ表示され、 Dynamics 365 for Outlook のリスト ビューにも使用されます。  
  
コマンド バーとリボンの両方が同じ基礎となる XML データを使用して、表示するコマンド、コマンドを有効にする時期、およびコマンドの実行内容を定義します。  
  
このセクションの記事では、理解しておく必要のある重要な概念と、コマンド バーまたはリボンをカスタマイズするときに実行する一般的なタスクについて説明します。  
  
> [!NOTE]
>  基礎となる XML スキーマはリボンとしてコマンドを表示するように設計されているため、*リボン* という用語はドキュメントで引き続き使用されます。  
  
## <a name="troubleshoot-ribbon-issues"></a>リボンの問題のトラブルシューティング

リボン コマンド バー ボタンで問題が発生している場合は、次の[トラブルシューティング ガイド](https://support.microsoft.com/help/4552163)を使用して問題を見つけ解決してください。


## <a name="community-tool"></a>コミュニティツール
SDK では、customization.xml ファイルを直接編集することでリボンを編集するプロセスについて説明します。 コミュニティ ツール [リボン ワークベンチ](https://www.develop1.net/public/rwb/ribbonworkbench.aspx) を使って、UI を使用してリボンを視覚的に編集します。 

> [!NOTE]
> Microsoft は、コミュニティ ツールのヘルプやサポートは提供していません。 これらのプログラムを使用するためのサポートまたヘルプを得るには、プログラムの発行元にお問い合わせください。  
  
  
## <a name="see-also"></a>関連項目  

 [リボン コアのスキーマ](ribbon-core-schema.md)  
 [リボン タイプのスキーマ](ribbon-types-schema.md)  
 [リボン WSS のスキーマ](ribbon-wss-schema.md)<br/> 
 [サンプル: リボン定義をエクスポートする](sample-export-ribbon-definitions.md)<br/> 
 [モデル駆動型アプリでクライアント スクリプトを使用してビジネス ロジックを適用](client-scripting.md)
