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
ms.openlocfilehash: 8d6669c644b3ecc9419f7900030eb663cf25ebe1
ms.sourcegitcommit: 5701e7a755fade6c3bac5c4a5774fcc74627e168
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2020
ms.locfileid: "3115651"
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
 [スタイルシート (CSS) ウェブ リソースを使用する](css-web-resources.md)   
 [スクリプト (JScript) Web リソースの使用](script-jscript-web-resources.md)   
 [画像 (JPG、PNG、GIF、ICO) Web リソースの使用](image-web-resources.md)   
 [Silverlight (XAP) Web リソースの使用](/dynamics365/customer-engagement/developer/silverlight-xap-web-resources)<br/>   <!-- TODO need to update the relevant link from the powerapps repo-->
 [スタイル シート (XSL) Web リソースの使用](/dynamics365/customer-engagement/developer/stylesheet-xsl-web-resources) <!-- TODO need to update the relevant link from the powerapps repo-->
