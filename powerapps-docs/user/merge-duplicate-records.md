---
title: 重複するレコードをマージする |MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 10/25/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5a14662d25a7c2dda79f2399b863b959f9f70cc5
ms.sourcegitcommit: 79ac9decef3d5aab40fbf3bc95f8f4ba03f9b3df
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/26/2019
ms.locfileid: "72959326"
---
# <a name="merge-duplicate-records"></a>重複レコードをマージする 

重複するレコードは、データを手動で入力したり、データを一括してインポートしたりするときに、データにクリープできます。 Common Data Service を使用すると、アカウントと連絡先の重複を検出することで、潜在的な重複を解決できます。 また、管理者は、他の状況に対して重複検出ルールを設定することもできます。  
  
たとえば、連絡先レコード、Jim Glynn、および携帯電話番号を入力するとします。  重複検出ルールは、既に類似したレコードがあることを検出し、このダイアログボックスを表示します。  
  
 > [!div class="mx-imgBorder"] 
 > ![重複する連絡先レコードの関連付けが関連付けられています](media/duplicates-detected.png "重複する連絡先レコードの関連付けが関連付けられています")  
  
 これが新しいレコード (既存の連絡先と同じ名前であるかどうか) または重複しているかどうかは不明なので、 **[無視して保存]** を選択します。  
  
 次に、[すべての**連絡先**] 一覧にアクセスし、同じ名前の2つのレコードがあることを確認します。 レコードを確認した後は、マージする必要がある重複であると判断します。  
 
 > [!div class="mx-imgBorder"] 
 > ![重複する連絡先レコードの関連付けが関連付けられています](media/duplicates-detected_1.png "重複する連絡先レコードの関連付けが関連付けられています")  
 
Common Data Service には、アカウントと連絡先の重複検出規則が含まれています。 これらのルールは自動的に有効になるため、これらのレコードの種類に対して重複する検出を設定するために何もする必要はありません。  
  
> [!NOTE]
>  システムで使用できる場合は、連絡先とアカウントに加えて、他のレコードの種類の重複を確認することもできます。 システム管理者に確認してください。 [管理者またはサポート担当者を見つける](find-admin.md)  
  
## <a name="merge-duplicate-records"></a>重複レコードをマージする  
  
1. 重複するレコードを選択し、 **[マージ]** を選択します。  
  
   > [!div class="mx-imgBorder"] 
   > ![重複する連絡先レコードの関連付けが関連付けられています](media/duplicates-detected_2.png "重複する連絡先レコードの関連付けが関連付けられています")  
  
2. **[レコードのマージ]** ダイアログボックスで、(保持する) マスターレコードを選択し、マスターレコードにマージする新しいレコードの任意のフィールドを選択します。 これらのフィールドのデータは、マスターレコードの既存のデータを上書きする可能性があります。 **[OK]** を選択します。  
  
     
   > [!div class="mx-imgBorder"] 
   > ![レコードをマージするためのダイアログボックス](media/merge-records-dialog.png "レコードをマージするためのダイアログボックス")  
  
> [!NOTE]
>  重複が見つかった場合は、次のような状況が考えられます。  
> 
> - レコードが作成または更新されたとき。  
>   - Outlook 用の Dynamics 365 を使用していて、オフラインからオンラインに移行している場合。  
>   - データのインポートウィザードを使用してデータをインポートする場合。  
> 
>   レコードをマージするとき、活動を完了済みとして保存するとき、またはレコードのアクティブ化や再アクティブ化などのレコードの状態を変更するときに、重複は検出されません。  