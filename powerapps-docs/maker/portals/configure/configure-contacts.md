---
title: 取引先担当者をポータルで使用できるように設定する | MicrosoftDocs
description: ポータルで使用する連絡先を追加および設定する手順。
author: sandhangitmsft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: sandhan
ms.reviewer: tapanm
ms.openlocfilehash: 592e329645a8cafdd085c6a2c4674201a7a5e9af
ms.sourcegitcommit: c12260f372ad2cc48d3146be570d2088c9ef1d86
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2020
ms.locfileid: "3494652"
---
# <a name="configure-a-contact-for-use-on-a-portal"></a>取引先担当者をポータルで使用できるように設定

連絡先の基本情報を入力した後 (またはユーザーがポータルでサインアップ フォームに入力)、ポータルの連絡先フォームの Web 認証タブに移動して、ローカル認証を使用して連絡先を設定します。 フェデレーション認証オプションの詳細は、[ポータルの認証 ID を設定](set-authentication-identity.md) を参照してください。 ローカル認証を使用してポータルの取引先担当者を構成するには、次の手順に従います。  

1.  **ユーザー名**を入力してください。
2.  コマンド リボン上で、**コマンドの詳細** &gt; **パスワードの変更**へ進みます。

パスワードの変更ワークフローを完了すると、必要なフィールドが自動的に構成されます。 これを実行すると、ポータルに取引先担当者が構成されます。

## <a name="change-password-for-a-contact-from-portal-management-app"></a>ポータル管理アプリから取引先担当者のパスワードを変更する

1.  [ポータル管理アプリ](configure-portal.md)を開きます。

2.  **ポータル** > **取引先担当者**へと移動して、パスワードを変更する取引先担当者を開きます。
    あるいは、[共有](../manage-existing-portals.md#share) ウィンドウからも **取引先担当者** ページを開けます。 

3.  上のツール バーで **タスク フロー** を選択します。

    > [!div class="mx-imgBorder"]
    > ![タスク フロー アイコン](../media/task-flow.png "タスク フロー アイコン")

4.  **ポータル取引先担当者のパスワードを変更** タスク フローを選択します。

5.  **ポータル取引先担当者のパスワードを変更** ウィンドウで、パスワードを変更する取引先担当者を選択するか作成し、**次へ** を選択します。

    > [!div class="mx-imgBorder"]
    > ![取引先担当者を選択してパスワードを変更する](../media/change-password-select-contact.png "取引先担当者を選択してパスワードを変更する")

6.  **新しいパスワード** フィールドに、新しいパスワードを入力し、**次へ** を選択します。

    > [!div class="mx-imgBorder"]
    > ![取引先担当者の新しいパスワードを入力する](../media/change-password-new-password.png "取引先担当者の新しいパスワードを入力する")

    パスワードを入力しないで **次へ** を選択した場合、選択した取引先担当者のパスワードを削除するかどうかが尋ねられます。

    > [!div class="mx-imgBorder"]
    > ![取引先担当者の新しいパスワードを削除する](../media/change-password-remove-password.png "取引先担当者を選択してパスワードを削除する")

7.  変更を加えたら、**完了** を選択します。


### <a name="see-also"></a>関連項目
[ポータルに取引先担当者を招待](invite-contacts.md)  
[ポータル用の認証 ID の設定](set-authentication-identity.md)  