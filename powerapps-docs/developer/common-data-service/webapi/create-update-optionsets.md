---
title: Web API を使用してオプションセットを作成、更新する (Common Data Service) | Microsoft Docs
description: メタデータ駆動のアーキテクチャを使用してユーザー定義エンティティや追加のシステム エンティティ属性の柔軟な作成を実現する Common Data Service エンティティの作成と更新について説明します。
ms.custom: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
caps.latest.revision: 15
author: JimDaly
ms.author: jdaly
ms.reviewer: pehecke
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3d6d211de33cb342a915bd11f390d96aa39f637e
ms.sourcegitcommit: c6906775005aec98973b1f5c3dbe5924aff6d26e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2020
ms.locfileid: "3341308"
---
# <a name="create-and-update-option-sets-using-the-web-api"></a>Web API を使用してオプション セットを作成および更新

通常、*グローバル* オプション セットでフィールドを設定するのは、さまざまなフィールドを同じオプション セットで共有して、それらを 1 つの場所でメンテナンスできるようにするためです。 特定の属性に対してのみ定義される*ローカル* オプション セットとは異なり、グローバル オプション セットは再利用できます。 要求パラメーターの中で列挙体のときと同じように使われる例もあります。  
  
*自社組織のURI*`/api/data/v9.0/GlobalOptionSetDefinitions` への POST 要求を使用してグローバル オプション セットを設定するときは、値の設定をシステムに委任することを推奨します。 具体的には新規の `OptionMetadata` インスタンスを作成するとき、引数として **null** 値を渡します。 オプションを変更すると、そのオプション セットが作成されたソリューションに設定されている発行者のコンテキストに固有の接頭辞がオプション値に含められます。 この接頭辞は、マネージド ソリューションや、マネージド ソリューションのインストール先の組織で定義されている任意のオプション セットの中で、オプション セットの重複が生じる可能性を減らす効果があります。 詳細については、[オプション セット オプションのマージ](/power-platform/alm/how-managed-solutions-merged#merge-option-set-options) を参照してください。

 ## <a name="messages"></a>メッセージ  
 次の表に、グローバル オプション セットで使用できるメッセージを示します。  
  
|メッセージ|Web API 操作|  
|--|--|
|CreateOptionSet|*自社組織のURI*`/api/data/v9.0/GlobalOptionSetDefinitions` への `POST` リクエストを使用します。|
|DeleteOptionSet|*自社組織のURI*`/api/data/v9.0/GlobalOptionSetDefinitions(`*metadataid*`)` への `DELETE` リクエストを使用します。|
|RetrieveAllOptionSets|*自社組織のURI*`/api/data/v9.0/GlobalOptionSetDefinitions` への `GET` リクエストを使用します。| 
|RetrieveOptionSet|*自社組織のURI*`/api/data/v9.0/GlobalOptionSetDefinitions(`*metadataid*`)` への `GET` リクエストを使用します。|   


次の表に、ローカルおよびグローバル オプション セットで使用できるメッセージを示します。

|メッセージ|Web API 操作|  
|--|--|
|DeleteOptionValue</br>グローバル オプション セットから値の 1 つを削除します。|<xref href="Microsoft.Dynamics.CRM.DeleteOptionValue?text=DeleteOptionValue Action" />  
|InsertOptionValue</br>新しいオプションをグローバル オプション セットに挿入します。|<xref href="Microsoft.Dynamics.CRM.InsertOptionValue?text=InsertOptionValue Action" />| 
|InsertStatusValue</br>`Status` 属性に使用する新しいオプションをグローバル オプション セットに挿入します。|<xref href="Microsoft.Dynamics.CRM.InsertStatusValue?text=InsertStatusValue Action" />|
|OrderOption</br>オプション セット内のオプションの相対順序を変更します。|<xref href="Microsoft.Dynamics.CRM.OrderOption?text=OrderOption Action" />|
|UpdateOptionSet|*自社組織の URI*`/api/data/v9.0/GlobalOptionSetDefinitions(`*metadataid*`)/Microsoft.Dynamics.CRM.OptionSetMetadata` への `PUT` リクエストを <xref href="Microsoft.Dynamics.CRM.OptionSetMetadata?text=OptionSetMetadata EntityType" /> とともに使用します。<br />ローカル オプション セットについては、 *自社組織のURI*`/api/data/v9.0/EntityDefinitions(`*metadataid*`)/Attributes(`*metadataid*`)/Microsoft.Dynamics.CRM.PicklistAttributeMetadata/OptionSet` を使用します。|
|UpdateOptionValue</br>グローバル オプション セットのオプションを更新します。|<xref href="Microsoft.Dynamics.CRM.UpdateOptionValue?text=UpdateOptionValue Action" />|
|UpdateStateValue</br>`Status` 属性に使用される新しいオプションをオプション セットに挿入します。|<xref href="Microsoft.Dynamics.CRM.UpdateStateValue?text=UpdateStateValue Action" />|

### <a name="see-also"></a>関連項目

[オプション セットのカスタマイズ](../org-service/metadata-option-sets.md)