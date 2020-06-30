---
title: リボン アクションを定義する (モデル駆動型アプリ) | MicrosoftDocs
description: <CommandDefinition> 要素のコマンド バーまたはリボン コントロールによって実行されるアクションを、リボンでそのコントロールを有効化するか、表示するかを制御するルールと一緒に定義する方法について説明します。
keywords: ''
ms.date: 05/07/2020
ms.service:
- PowerApps
ms.topic: article
ms.assetid: fbb7ff68-e4be-d8c2-069f-6a4a69665b56
author: Nkrb
ms.author: nabuthuk
manager: shilpas
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: d3fa1bdb13054ba3e59d60b795868e13c02ce28a
ms.sourcegitcommit: ed423b9382bf183d0b28907039d3432b99d4e7f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2020
ms.locfileid: "3353488"
---
# <a name="define-ribbon-actions"></a>リボン アクションの定義

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/define-ribbon-actions -->

`<CommandDefinition>` 要素でコマンド バーまたはリボン コントロールによって実行するアクションを、リボンでそのコントロールを有効化するか、表示するかを制御するルールと一緒に定義します。  
  
 リボン コントロールは、次の 2 種類のアクションを実行できます。複数のアクションが含まれることもあります。  
  
- **JavaScript 関数** :  `<JavaScriptFunction>` 要素は、[スクリプト (JScript) Web リソース](/powerapps/developer/model-driven-apps/script-jscript-web-resources)に定義された関数を参照します。  
  
- **URL を開く**: リボンは、`<Url>` 要素の Address 属性の値を使用して URL を開きます。 追加パラメーターによって、どの QueryString パラメーターをどのように渡すかと、ウィンドウが開くときのモードに関する情報を渡すことができます。  
  
     リボンを使用してパラメーターを URL に渡すための選択肢はいくつかあります。 詳細: [リボンを使用して URL にパラメーターを渡す](pass-parameters-url-by-using-ribbon.md)  
  
## <a name="passing-parameters-to-ribbon-actions"></a>パラメーターをリボン アクションに渡す  

 ユーザー定義のアクションに渡すデータを定義するには、以下の要素を使用します。  
  
 `<BoolParameter>`  
[!INCLUDE[ribbon_element_BoolParameter](../../includes/ribbon-element-boolparameter.md)]
  
 `<CrmParameter>`  
 [!INCLUDE[ribbon_element_CrmParameter](../../includes/ribbon-element-crmparameter.md)] 詳細: [データをページからパラメーターとしてリボン操作に渡す](pass-data-page-parameter-ribbon-actions.md) 
  
 `<DecimalParameter>`  
 [!INCLUDE[ribbon_element_DecimalParameter](../../includes/ribbon-element-decimalparameter.md)]
  
 `<IntParameter>`  
 [!INCLUDE[ribbon_element_IntParameter](../../includes/ribbon-element-intparameter.md)]
  
 `<StringParameter>`  
 [!INCLUDE[ribbon_element_StringParameter](../../includes/ribbon-element-stringparameter.md)]
  
 パラメーターは、`<Url>` 要素に渡される場合、クエリ文字列として渡されます。 そのため、クエリ文字列のキー/値のペアの「キー」を表す名前値を含める必要があります。  
  
 `<JavaScriptFunction>` に渡すパラメーターに名前は必要ありませんが、これらのパラメーターは、関数が必要とする順序で指定し、正しいデータ型を使用する必要があります。  
  
## <a name="see-also"></a>関連項目  

 [コマンドとリボンのカスタマイズ](customize-commands-ribbon.md)   
 [リボンの表示ルールの定義](define-ribbon-display-rules.md)   
 [データをページからパラメーターとしてリボン操作に渡す](pass-data-page-parameter-ribbon-actions.md)  


