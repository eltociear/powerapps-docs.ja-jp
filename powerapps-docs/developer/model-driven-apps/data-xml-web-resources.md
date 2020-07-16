---
title: データ (XML) Web リソース (モデル駆動型アプリ) | Microsoft Docs
description: データを保存してアクセスするための、データ (XML) Web リソースの使用について学習します。
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: article
ms.assetid: 2bf0d49f-8b6d-6d5b-0af5-edf6dd485fed
author: Nkrb
ms.author: nabuthuk
manager: shilpas
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 78375106556e8b901562d8cfe0d259986faab13c
ms.sourcegitcommit: b5ab419dad4e9d64a5e6610641363b0d7487930a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2020
ms.locfileid: "3465501"
---
# <a name="data-xml-web-resources"></a>データ (XML) Web リソース

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/data-xml-web-resources -->

データを保存したり、データにアクセスしたりするには、データ (XML) Web リソースを使用します。  
  
## <a name="capabilities-of-xml-web-resources"></a>XML Web リソースの機能  
 ソリューションで使用するデータをキャッシュするには、XML Web リソースを使用します。  
  
### <a name="limitations-of-xml-web-resources"></a>XML Web リソースの制限  
 ソリューションの構成設定またはメタデータをキャッシュするには、XML Web リソースを使用します。  
  
 XML Web リソースは、複数のユーザーによって頻繁に更新されるデータのための堅牢なソリューションを表すものではありません。 あるユーザーが XML Web リソースを更新している間に、別のユーザー (または自動化されたプロセス) はその Web リソースを更新できますが、最初のユーザーが変更を保存するとデータは失われます。  
  
 すべての XML ファイルでは、ファイル名の拡張子として .xml を使用する必要があります。 XML データを使用し、ファイル名の拡張子 .xml を使用しないファイルは、拡張子が変更されるまで Web リソースとしてアップロードできません。  
  
### <a name="see-also"></a>関連項目  
 [Web リソース](web-resources.md)   
 [Web ページ (HTML) の Web リソースの使用](webpage-html-web-resources.md)   
 [スタイル シート (CSS) Web リソースの使用](css-web-resources.md)   
 [スクリプト (JScript) Web リソースの使用](script-jscript-web-resources.md)   
 [画像 (JPG、PNG、GIF) Web リソースの使用](image-web-resources.md)   
 [スタイル シート (XSL) Web リソースの使用](stylesheet-xsl-web-resources.md) 