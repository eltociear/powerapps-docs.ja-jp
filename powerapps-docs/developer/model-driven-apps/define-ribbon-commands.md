---
title: リボン コマンドを定義する (モデル駆動型アプリ) | MicrosoftDocs
description: リボン コマンドは、リボン コントロール要素から参照できる再使用可能な定義を作成します。
keywords: ''
ms.date: 03/27/2020
ms.service: powerapps
ms.topic: article
ms.assetid: 60933770-8c7c-499c-12b4-8b64f6eedb35
author: Nkrb
ms.author: nabuthuk
manager: shilpas
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0578be828ec9d061df54df173320e8719137bf9c
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/21/2020
ms.locfileid: "3275975"
---
# <a name="define-ribbon-commands"></a>リボン コマンドを定義する

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/define-ribbon-commands -->

*リボン* コマンドは、リボン コントロール要素から参照できる再使用可能な定義を作成します。  
  
## <a name="ribbon-command-elements"></a>リボン コマンド要素  
 `<CommandDefinition>` 要素は、リボンのコマンドを定義します。 `Id` 属性は、`Command` パラメーターを使用してリボン コントロール要素から参照可能なコマンドの一意の ID を指定します。  
  
 リボン コマンドは次の 3 つを定義します。  
  
- **有効化ルール**: 特定のリボン コントロールを有効にするタイミングを指定します。  
  
- **表示ルール**: 特定のリボン要素を表示するタイミングを指定します。  
  
- **操作**: リボン コントロールの使用中に実行するコードを指定します。  
  
> [!IMPORTANT]
>  コマンドの定義はすべて、ユーザーのコンピューターにダウンロードされるので、コマンドの定義を実行時に評価できます。 つまり、リボンの特定のコントロールを表示する特権を持っていなくても、ユーザーは、ブラウザーの**ソースの表示**コマンドを使用して、コードを確認し、表示されないコントロールが存在しないかどうかを調べることができます。  
  
### <a name="see-also"></a>関連項目  
 [コマンドとリボンのカスタマイズ](customize-commands-ribbon.md)   
 [リボンでのローカライズされたラベルの使用](use-localized-labels-ribbons.md)   
 [リボン有効化ルールを定義する](define-ribbon-enable-rules.md) [リボンの問題のトラブルシューティング](https://support.microsoft.com/help/4552163)
