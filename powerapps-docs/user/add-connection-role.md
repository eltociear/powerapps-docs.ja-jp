---
title: 相互にレコードをリンクするためのつながりロールを追加する | MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 8/01/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4552c874ca6be72d37465abd2492a64979aba865
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "3302520"
---
# <a name="add-a-connection-role-to-link-records-to-each-other"></a>相互にレコードをリンクするためのつながりロールを追加する

接続を使用すると、ユーザー、連絡先、見積もり、受注、およびその他多くのエンティティ レコード同士を簡単に関連付けることができます。 関連付け内のレコードを特定のロールに割り当てると、関係の目的の定義に役立ちます。

これにより、特定のレコードに対して複数のつながりとロールを簡単に作成できます。 たとえば、1 つの連絡先が他の連絡先、取引先企業、または契約と多くの関係を持っている場合があります。 それぞれの関係について、その連絡先に異なるロールを割り当てることができます。

つながりロールはつながりに直接関連付けられます。 つながりロールを使用するには、まず、つながりをレコードに追加する必要があります。

接続ロールを追加するには、管理者が追加の権限を有効化している必要があります。詳細については、[接続の役割を構成する](https://docs.microsoft.com/powerapps/maker/common-data-service/configure-connection-roles) を参照してください。

1. つながりを追加または管理するには、営業案件など、管理するレコードを選択します。  
2. **[関連]** タブを選択し、**[つながり]** を選択します。 これにより、つながりグリッドが開いて、レコードのつながりの一覧が表示されます。

    > [!div class="mx-imgBorder"]
    > ![新規接続ロールを追加する](media/connection1.png "新規接続ロールを追加する") 

3. **[つながり]** を選択し、**[他へ]** または **[自分に関連付け]** を選択します。

    > [!div class="mx-imgBorder"]
    > ![接続の種類を選択する](media/connection2.png "接続の種類を選択する") 
  
4. **[名前]** フィールドで、つながりのレコードの名前を入力するか、検索します。

5. **[このロールとして]** フィールドでルックアップ アイコンを選択し、**[新しいつながりロール]** を選択します。 または、検索を使用して、つながりに関連付ける既存のロールを検索し、**[保存]** を選択します。

    > [!div class="mx-imgBorder"]
    > ![新規接続のロールを選択する](media/connection3.png "新規接続のロールを選択する")  

    > [!NOTE]
    > 新しいつながりロールを作成する前に情報を入力すると、警告ダイアログが表示され、キャンセルしてつながりを続行するか、入力している現在のレコードをそのままにして先に進むかを質問されます。

6. 新しいつながりロールを作成するには、**[新しいつながりロール]** 画面で、名前を入力して、**[つながりロール カテゴリ]** を選択します。

    > [!div class="mx-imgBorder"]
    >  ![接続ロールのカテゴリを追加する](media/connection4.png "接続ロールのカテゴリを追加する") 

7. 完了したら、**[保存して閉じる]** を選択します。

  
## <a name="manage-connection-roles"></a>つながりロールの管理

つながりロールを管理するには、つながりエンティティからつながりロールを選択します。 これにより、つながりロール エンティティ レコードが開きます。  名前を編集して、つながりロール カテゴリを選択し、説明を追加することができます。


   > [!div class="mx-imgBorder"]
   > ![接続ロールを編集する](media/connection7.png "接続ロールを編集する") 
  
また、つながりロールに関連付けるつながりロールの種類を管理することもできます。

1. つながりロールを開いて、コマンドの **[レコードの種類の管理]** を選択します。 

    > [!div class="mx-imgBorder"]
    > ![接続ロールを編集する](media/connection5.png "接続ロールを編集する") 
  

2. これにより、このつながりロールに対して追加または削除できるつながりロールの種類の一覧が開きます。

    > [!div class="mx-imgBorder"]
    > ![レコードの種類を管理する](media/connection6.png "レコードの種類を管理する") 


