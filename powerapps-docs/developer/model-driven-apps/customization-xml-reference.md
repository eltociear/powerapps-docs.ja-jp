---
title: カスタマイズ XML リファレンス (モデル駆動型アプリ) | MicrosoftDocs
description: customizations.xml ファイルは、エクスポートされるアンマネージド ソリューションに含まれるファイルの 1 つです。 ファイルにはシステムのカスタマイズおよび構成の全てまたは選択部分が含まれます
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: article
ms.assetid: 864699de-c22f-3504-f120-84ca5a4aeca6
author: Nkrb
ms.author: nabuthuk
manager: shilpas
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: aa507c08df5fd93a8a9ffb7c852fc787d0efb63b
ms.sourcegitcommit: b5ab419dad4e9d64a5e6610641363b0d7487930a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2020
ms.locfileid: "3465525"
---
# <a name="customization-xml-reference"></a>カスタマイズ XML リファレンス

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customization-xml-reference -->

customizations.xml ファイルは、エクスポートされるアンマネージド ソリューションに含まれるファイルの 1 つです。 ファイルにはシステムのカスタマイズおよび構成の全てまたは選択部分が含まれます。 
  
 ソリューション ファイルは圧縮された .zip ファイルとしてエクスポートされます。 アンマネージド ソリューション ファイルのコンテンツは、カスタマイズ ファイルを編集する前に展開する必要があります。 アンマネージド ソリューションのすべてのファイルは、インポートする前に圧縮された .zip ファイルに追加する必要があります。  

> [!NOTE]
> - マネージド ソリューション ファイルの編集はサポートされていません。  
> - customizations.xml ファイルのすべての要素を編集できるわけではありません。 詳細: [カスタマイズ ファイルの編集のサポート](../common-data-service/when-edit-customization-file.md)

## <a name="in-this-section"></a>このセクションの内容

 [リボン コアのスキーマ](ribbon-core-schema.md)[リボン タイプのスキーマ](ribbon-types-schema.md)  
 [リボン WSS のスキーマ](ribbon-wss-schema.md)  
 [フォーム XML スキーマ](form-xml-schema.md)  
 [FetchXML スキーマ](../common-data-service/fetchxml-schema.md) 

## <a name="related-sections"></a>関連セクション

[カスタマイズ ファイルを編集するとき](../common-data-service/when-edit-customization-file.md)  
[スキーマ検証を使用したカスタマイズ ファイルの編集](edit-customizations-xml-file-schema-validation.md)  
[Dynamics 365 のリボンのカスタマイズ](customize-commands-ribbon.md)  
[SiteMap を使用したアプリケーション ナビゲーションの変更](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-site-map-app) 
