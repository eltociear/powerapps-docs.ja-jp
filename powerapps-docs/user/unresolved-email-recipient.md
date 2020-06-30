---
title: 未解決のメール受信者を解決する | MicrosoftDocs
description: 未解決のメール受信者を解決する方法について説明します。
ms.date: 05/11/2020
ms.service:
- dynamics-365-sales
ms.topic: article
author: sbmjais
ms.author: shjais
manager: shujoshi
ms.openlocfilehash: 0f4ea88a34c7d7c5618732aff021dac1c9d716c1
ms.sourcegitcommit: ef921bbf0908283a3621c2ca1069e6b58a2b14e7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2020
ms.locfileid: "3373900"
---
# <a name="resolve-an-unresolved-email-recipient"></a>未解決の電子メール受信者を解決する

*未解決のメール受信者* は、Common Data Service でメールアドレスがエンティティ レコードに関連付けられていない人です。 規定では、未解決のメール受信者にメールを送信することはできません。 未解決のメール受信者アドレスを入力した場合、**宛先**、**Cc**、または **Bcc** フィールドからフォーカスを移動するとすぐに削除されます。 管理者は、**システム設定** の **メール** タブにある、**未解決のメール受信者を含むメッセージの送信を許可する** で **はい** を選択することで、未解決メールの受信者機能を有効にします。 詳細: [システムの設定のメールタブ](https://docs.microsoft.com/power-platform/admin/system-settings-dialog-box-email-tab)

この機能を有効にした後、**宛先**、**Cc**、または **Bcc** フィールドの未解決メールの受信者を追加できます。 入力したメールアドレスは赤字で表示されます。 次に、メールアドレスを選択し、それをメール フォームから移動せずに Common Data Service でエンティティレコードに関連付けることができます。

エンティティ レコードに関連付けられていないメール アドレスを含むメールを受信した場合、そのメール アドレスは赤で表示されます。 次に、メール アドレスを個別に選択して、エンティティ レコードに関連付けることができます。 その後、新しく追加されたメール アドレスにメールを送信できます。

**未解決のメール受信者を解決するには**

1. メール エディターを開き、未解決のメール受信者を選択します。

    ![未解決のメール受信者](media/unresolved-email.png "未解決のメール受信者")

2. **レコードの検索** ペインで、**新規レコード** を選択します。

    ![未解決のメール受信者のレコード ペインの検索](media/unresolved-email-lookup.png "未解決のメール受信者のレコード ペインの検索")

    > [!NOTE]
    > レコードが検索結果に表示されている場合は、メールを既存のレコードのいずれかに解決できます。

3. 作成するレコードの種類を選択します。 たとえば、**連絡先** です。

    ![レコードの種類の選択](media/unresolved-email-select-record-type.png "レコードの種類の選択")

4. **クイック作成: 連絡先** ペインで、必要な詳細を入力し、**保存して閉じる** を選択します。

    ![取引先担当者の詳細の入力](media/unresolved-email-create-record.png "取引先担当者の詳細の入力")

5. 取引先担当者が作成され、**ルックアップ レコード** ペインで選択されます。 **追加** を選択します。

    ![取引先担当者の追加](media/unresolved-email-add-record.png "取引先担当者の追加")

6. 未解決のメール受信者が解決され、メールエディタの **宛先** フィールドに表示されます。

    ![解決されたメール受信者](media/resolved-email-recipient.png "解決されたメール受信者")


### <a name="see-also"></a>関連項目

[未解決のメール受信者を許可する](https://docs.microsoft.com/power-platform/admin/system-settings-dialog-box-email-tab)
