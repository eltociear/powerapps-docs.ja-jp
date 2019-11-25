---
title: 重複データ検出メッセージ (Common Data Service) | Microsoft Docs
description: BulkDetectDuplicatesRequest または RetrieveDuplicatesRequest メッセージを使用して重複を検知します。
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: ed2d9180bfb148c59efb679f6a44d8d184a9c2d7
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748798"
---
# <a name="duplicate-detection-messages"></a>重複データ検出のメッセージ

次の表に示すメッセージを使用して、Common Data Service 内の重複データを検出します。  


|                                                                                                                                                                                                                   メッセージ                                                                                                                                                                                                                   |                                      Web API 操作                                       |                         SDK アセンブリ                          |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------|---------------------------------------------------------------|
| クエリ基準に基づいて、指定されたエンティティの種類に対する重複データを検出し、Common Data Service データベースに重複レコード エンティティの種類のインスタンスとして格納します。<br /><br /> 重複データ検出ジョブを実行するレコードを記述するクエリ式は、この要求の <xref:Microsoft.Crm.Sdk.Messages.BulkDetectDuplicatesRequest.Query> プロパティで指定されます。 | <xref href="Microsoft.Dynamics.CRM.BulkDetectDuplicates?text=BulkDetectDuplicates Action" /> | <xref:Microsoft.Crm.Sdk.Messages.BulkDetectDuplicatesRequest> |
|                                                                                                         指定されたレコードの重複を検出し、取得します。<br /><br /> 一致するエンティティの種類は、この要求の <xref:Microsoft.Crm.Sdk.Messages.RetrieveDuplicatesRequest.MatchingEntityName> プロパティで指定されます。                                                                                                          |  <xref href="Microsoft.Dynamics.CRM.RetrieveDuplicates?text=RetrieveDuplicates Function" />  |  <xref:Microsoft.Crm.Sdk.Messages.RetrieveDuplicatesRequest>  |

### <a name="see-also"></a>関連項目  
 [重複データ検出の有効化と無効化](enable-disable-duplicate-detection.md)  
 [重複データ検出の実行](run-duplicate-detection.md)   
 [重複ルール エンティティ](duplicaterule-entities.md)<br />
