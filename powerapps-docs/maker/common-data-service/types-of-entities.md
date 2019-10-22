---
title: エンティティの種類 | MicrosoftDocs
ms.custom: ''
ms.date: 05/30/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: 2f3f6053-0b9e-41e7-bd94-2239351e9f4b
caps.latest.revision: 41
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="types-of-entities"></a>エンティティの種類

Common Data Service でエンティティを作成または編集するには、その前に、さまざまな種類のエンティティがあることを理解する必要があります。 ユーザー定義エンティティをいったん作成すると、これらの種類は変更できません。 2 つの重要な部分が、エンティティの所有権とエンティティが活動エンティティであるかどうかに基づいています。  
  
<a name="BKMK_EntityOwnership"></a>

## <a name="entity-ownership"></a>エンティティの所有権  

エンティティの所有権には 4 つの異なる種類があります。 ユーザー定義エンティティを作成するときのオプションは**ユーザーまたはチームが所有**または**組織所有**のみですが、他のエンティティは異なる所有権の種類を使用することに留意してください。  
  
|所有権|説明|  
|---------------|-----------------|  
|**部署が所有**|これらのエンティティのデータは、部署に帰属します。 データへのアクセスは、部署レベルで管理できます。|  
|**なし**|データは別のエンティティによって所有されません。|  
|**組織所有**|データは、組織に属します。 データへのアクセスは組織レベルで管理されます。|  
|**ユーザーまたはチームが所有**|データは、ユーザーまたはチームに属します。 これらのレコードで実行できる操作は、ユーザー レベルで管理できます。|  
  
  
> [!IMPORTANT]
>  エンティティ作成してから、企業形態を変更することはできません。 エンティティを作成する前に、適切な所有権の種類を選択してください。 ユーザー定義エンティティが別の種類であることが後で分かった場合は、それを削除し、新しいユーザー定義エンティティを作成する必要があります。
  
<a name="BKMK_ActivityEntities"></a>

## <a name="activity-entities"></a>活動エンティティ

活動は、カレンダーにエントリを作成できるアクションと考えることができます。 活動には、アクションがいつ実行されたか、またはいつ実行されるかの特定に役立つ時間ディメンション (開始時間、停止時間、期限、期間) が存在します。 また、活動には、活動が表しているアクションを判断するために役立つデータ (主題や説明) も含まれています。 活動は、開いたり、取り消したり、完了することができます。 活動の完了状態には、活動がどのように完了したかを明らかにする数種類のサブ状態値が関連付けられます。  
  
活動エンティティはユーザーまたはチームのみが所有することができ、組織が所有することはできません。  
  
The following table lists に、既定の Common Data Service 環境で使用可能な活動エンティティを示します。
  
|Name|説明|活動メニューでの表示|参照|
|----------|-----------------|----------------|---------------|  
|**予定**|開始時刻、終了時刻、および期間により時間間隔を定めた約束です。|あり|[予定](/powerapps/developer/common-data-service/reference/entities/appointment)|
|**電子メール**|電子メール プロトコルを使用して配信される活動です。|あり|[電子メール](/powerapps/developer/common-data-service/reference/entities/email)|
|**FAX**|FAX の通信結果やページ数を追跡する活動です。ドキュメントの電子コピーを保存することもできます。|あり|[FAX](/powerapps/developer/common-data-service/reference/entities/fax)|
|**レター**|レターの配送を追跡する活動です。 この活動にはレターの電子コピーを使用できます。|あり|[レター](/powerapps/developer/common-data-service/reference/entities/letter)|
|**電話**|通話を追跡する活動です。|あり|[PhoneCall](/powerapps/developer/common-data-service/reference/entities/phonecall)|
|**定期的な予定**|定期的な予定の系列のマスター予定です。|あり|[RecurringAppointmentMaster](/powerapps/developer/common-data-service/reference/entities/recurringappointmentmaster)|
|**タスク**|処理する必要がある作業を表す全般的な活動です。|あり|[タスク](/powerapps/developer/common-data-service/reference/entities/task)|
  
ユーザー定義の活動エンティティを新規に作成できます。 たとえば、インスタント メッセージング通信を記録するために、ユーザー定義の活動エンティティを作成する場合があります。 活動エンティティの作成は、プライマリ フィールドを指定しないので、非活動エンティティの作成とは異なります。 すべての活動エンティティには、**件名**に設定されている**プライマリ フィールド**と、活動エンティティによって定義されるその他の共通フィールドがあります。 これにより、すべての種類の活動を、共通フィールドだけが表示されるビューに表示することができます。  

> [!NOTE]
> PowerApps ポータルを使用してカスタム活動を作成することはできません。 **詳細設定** ボタンを使用してソリューション エクスプローラーを開く必要があります。
  
ユーザー定義の活動エンティティを作成するには、**活動エンティティとして定義**を選択します。 これを選択した後、**活動メニューに表示する**が選択されていることが分かります。 この設定によって、活動メニューでこの種類の活動を作成できます。 これは、特定のイベントに通常関連付けられていて、コードを使用するかまたはワークフローによって作成される活動については選択されません。 いったんエンティティを保存したら、これらの設定を変更できません。  

### <a name="see-also"></a>関連項目
[エンティティの作成または編集](create-edit-entities.md)
