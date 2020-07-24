---
title: Power Apps を使用してモデル駆動型アプリを共有する | Microsoft Docs
description: モデル駆動型アプリを共有する方法を説明します
documentationcenter: ''
author: Mattp123
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 03/04/2020
ms.author: matp
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8b2f0b850b74d3af590e1eb9efb3f07bbf5893eb
ms.sourcegitcommit: 09861c876b5d8fa2ec0bd422124aa44c077c540d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/30/2020
ms.locfileid: "3412548"
---
# <a name="share-a-model-driven-app-using-power-apps"></a>Power Apps を使用してモデル駆動アプリと共有する

[!INCLUDE [powerapps](../../includes/powerapps.md)] アプリは、共有にロールベースのセキュリティを使用します。 ロールベースのセキュリティの基本概念は、セキュリティ ロールにはアプリ内で実行できる一連の操作を定義する特権が含まれるということです。 すべてのアプリ ユーザーは、これらの中で 1 つ以上の定義済みロールまたはユーザー定義ロールに割り当てられる必要があります。 または、チームにもロールを割り当てることができます。 これらのロールのいずれかにユーザーまたはチームを割り当てると、そのロールに関連付けられた一連の特権がユーザーまたはチーム メンバーに付与されます。 

## <a name="prerequisites"></a>前提条件
[セキュリティ ロール](https://docs.microsoft.com/power-platform/admin/security-roles-privileges) とアプリや他のユーザーに割り当てているロールと同等以上の権限を持っていることを確認してください。 

## <a name="create-a-security-role-for-your-app"></a>アプリ用にセキュリティ ロールを作成する
通常、モデル駆動型アプリには、カスタム エンティティおよびその他のカスタム構成が含まれます。 最初に、アプリで使用されるすべてのコンポーネントに対する許可と共に [セキュリティ ロールを作成する](#create-a-security-role-for-your-app) ことが重要です。  
> [!NOTE]
> 既存のロールがアプリのデータへのアクセスを許可している場合、このステップはスキップできます。 

## <a name="preview-share-a-model-driven-app"></a>プレビュー : モデル駆動型アプリの共有 
モデル駆動型アプリの共有には、2 つの主要なステップが含まれます。 まず、1 つ以上のセキュリティ ロールをそのアプリに関連付けてから、セキュリティ ロールをユーザーに割り当てます。 
1. https://make.powerapps.com へ移動します
2. モデル駆動型アプリを選択して、**共有** をクリックします。
3. アプリを選択し、リストからセキュリティ ロールを選択します。
    > [!div class="mx-imgBorder"] 
    > ![](media/share-model-driven-app/share-app.png "Assign a role to the app")
4. ユーザーの検索
5. ユーザーを選択し、リストからロールを選択します。
    > [!div class="mx-imgBorder"] 
    > ![](media/share-model-driven-app/share-user.png "Assign a role to the user")
6. **共有** をクリックします。

### <a name="share-the-link-to-your-app"></a>アプリへのリンクの共有
キャンバス アプリの共有とは異なり、モデル駆動型アプリの共有では現在、アプリへのリンクを含むメールは送信されません。

アプリへの直接リンクを取得するには :
1. アプリを編集して、**プロパティ** タブをクリックします。
2. **統一インターフェイス URL** をコピーします。
3. SharePoint サイトに投稿したり、メールで送信するなど、ユーザーがアクセスできる位置にアプリ URL を貼り付けます。


## <a name="create-or-configure-a-security-role"></a>セキュリティ ロールの作成または構成
[!INCLUDE [powerapps](../../includes/powerapps.md)] 環境には、[定義済みのセキュリティ ロール](#about-predefined-security-roles)が用意されています。これらのセキュリティ ロールは、一般的なユーザー タスクを反映し、アプリの使用に必要な最小限の業務データへのアクセスを許可する、というセキュリティのベスト プラクティスの目的に沿うようにアクセス レベルが定義されています。 たとえば、アプリがカスタム エンティティに基づいている場合、ユーザーが作業する前にエンティティ権限を明示的に指定する必要があります。 これを行うには、次のいずれかの操作を行うように選択します。
- ユーザー定義エンティティに基づいてレコードに特権が含まれるようにするには、あらかじめ定義されたセキュリティ ロールを展開します。 
- アプリのユーザーに対して特権を作成する目的でユーザー定義のセキュリティ ロールを作成します。 

アクセス権とスコープ特権の詳細については、「[セキュリティ ロール](https://docs.microsoft.com/dynamics365/customer-engagement/admin/security-roles-privileges#security-roles)」を参照してください。

### <a name="create-a-custom-security-role"></a>カスタム セキュリティ ロールの作成
1.  [!INCLUDE [powerapps](../../includes/powerapps.md)] サイトで **アプリ**を選択し、共有したいモデル駆動型アプリの横の **…** を選択し、その後 **共有** を選択します。

2. アプリを選択し、セキュリティ ロールのリストを展開します。

3. **すべてのロール** ページで、**新規** を選択します。  

4. セキュリティ ロール デザイナーでは、アクション (読み取り、書き込み、削除など) と、そのアクションを実行するためのスコープを選択します。 スコープにより、ユーザーが特定の処理を実行できる環境階層の高さが決まります。 **ロール名** ボックスで*ペット グルーミング技術者*と入力します。

5. **ユーザー定義エンティティ** タブを選択し、目的のユーザー定義エンティティを探します。 この例では、**ペット**という名前のユーザー定義エンティティが使用されます。 

6. **ペット** 行で、組織スコープ グローバルの![組織グローバル スコープ](media/share-model-driven-app/organizational-scope-privilege.png)が選択されるまで、以下の各特権を 4 回選択します: **読み取り、書き込み、追加**

   > [!div class="mx-imgBorder"] 
   > ![新しいセキュリティ ロール](media/share-model-driven-app/custom-security-role.png)

7. ペット グルーミング アプリには、取引先企業エンティティとの関連付けがあるため、**コア レコード** タブを選択し、**取引先企業** 行で、組織スコープ グローバル![組織グローバル スコープ](media/share-model-driven-app/organizational-scope-privilege.png)が選択されるまで、**読み取り** を 4 回選択します。 

8. **カスタマイズ** タブを選択し、組織のスコープの ![組織グローバル スコープ](media/share-model-driven-app/organizational-scope-privilege.png) が選択されるように、特権の一覧で **モデル駆動アプリ** の横の **読み取り** 特権を選択します。

    > [!div class="mx-imgBorder"] 
    > ![アプリのセキュリティ ロールの選択](media/app-access-specific-use.png)

9. **保存して閉じる**を選択します。 

10. セキュリティ ロール デザイナーで、**ロール名** ボックスに*ペット グルーミング スケジューラ*を入力します。 

11. **ユーザー定義エンティティ** タブを選択し、**ペット** エンティティを探します。 

12. **ペット** 行で、組織スコープ グローバルの![組織グローバル スコープ](media/share-model-driven-app/organizational-scope-privilege.png)が選択されるまで、以下の各特権を 4 回選択します: **作成、読み取り、書き込み、削除、追加、追加先指定、割り当て、共有**

13. ペット グルーミング アプリには、取引先企業エンティティとの関連付けがあり、スケジューラは取引先企業レコードを作成および変更できる必要があるため、**コア レコード** タブを選択し、**取引先企業** 行で、組織スコープ グローバル![組織グローバル スコープ](media/share-model-driven-app/organizational-scope-privilege.png)が選択されるまで、以下の各特権を 4 回選択します。 
    **作成、読み取り、書き込み、削除、追加、追加先、割り当て、共有**

14. **保存して閉じる**を選択します。

### <a name="assign-security-roles-to-users"></a>ユーザーへのセキュリティ ロールの割り当て
セキュリティ ロールは、一連のアクセス レベルとアクセス許可により、ユーザーのアクセスをコントロールします。 特定のセキュリティ ロールに含まれるアクセス許可とアクセス レベルの組み合わせにより、ユーザーが表示できるデータおよびユーザーのデータ使用方法を制限します。

#### <a name="assign-a-security-role-to-pet-grooming-technicians"></a>ペット グルーミング技術者へのセキュリティ ロールの割り当て
1. **このアプリの共有** ダイアログの **セキュリティ ロールへのユーザーの割り当て** で、**セキュリティ ユーザー** を選択します。
2. 表示されたリストで、ペットグルーマーであるユーザーを選択し、コマンドバーで **役割の管理** を選択します。

3. **セキュリティ ロールの管理** をクリックします。
    > [!div class="mx-imgBorder"] 
    > ![](media/share-model-driven-app/manage-roles.png "Manage roles")

4. **すべてのロール** ページで、**Common Data Service ユーザー** を選択して、次に **行動**、**ロールをコピー** をクリックします。 

> [!TIP]
> 既存のロールをコピーする代わりに、新しい空のロールを作成することもできます。 

6. **ロール名** ボックスで、*マイ カスタム アプリへのアクセス* などわかりやすいロールを入力します。  **OK** をクリックします。

7. セキュリティ ロール デザイナーから、読み取り、書き込み、または削除などのアクションと、[アクセス レベル](https://docs.microsoft.com/power-platform/admin/security-roles-privileges#security-roles) を選択します。 アクセス レベルは、ユーザーが特定の処理を実行できる環境階層の高さが決まります。 

8. **ユーザー定義エンティティ** タブを選択し、アプリで使用されるユーザー定義エンティティを見つけます。 

9.  ユーザー定義エンティティの行で、各権限のアクセスレベルを設定します。  

10. アプリで使用される他のエンティティに対して繰り返します。 

11. **カスタマイズ** タブを選択し、組織アクセスレベルの ![組織グローバル スコープ](media/share-model-driven-app/organizational-scope-privilege.png) が選択されるように、**モデル型駆動アプリ** に **読み取り** 特権が設定されていることを確認します。

    > [!IMPORTANT]
    > **読み取り**、**作成**、そして **書き込み** を **モデル駆動型アプリ** 特権に対して付与されたユーザーは、環境内のすべてのアプリにアクセスできます (アプリにアクセスできるロールの一部ではない場合でも)。
    > ![モデル駆動型アプリの特権での作成および書き込み](media/app-access-cds.png)

12. **保存して閉じる**を選択します。 


## <a name="about-predefined-security-roles"></a>定義済みのセキュリティ ロールについて
これらの定義済みロールは、[!INCLUDE [powerapps](../../includes/powerapps.md)] 環境で使用できます。


|セキュリティ ロール  |*特権  |説明 |
|---------|---------|---------|
|環境作成者     |  なし       | Power Automate を使用して、アプリ、つながり、カスタム API、ゲートウェイ、フローなど、環境に関連付けられた新しいリソースを作成できます。 ただし、環境内のデータにアクセスする特権はありません。 詳細: [環境の概要](https://powerapps.microsoft.com/blog/powerapps-environments/)        |
|システム管理者     |  作成、読み取り、書き込み、削除、カスタマイズ、セキュリティ ロール       | セキュリティ ロールの作成、変更、割り当てなど、環境をカスタマイズまたは管理する完全なアクセス許可があります。 環境のすべてのデータを表示できます。 詳細情報: [カスタマイズに必要な特権](https://docs.microsoft.com/dynamics365/customer-engagement/customize/privileges-required-customization)        |
|システム カスタマイザ     | 作成 (自己)、読み取り (自己)、書き込み (自己)、削除 (自己)、カスタマイズ         | 環境をカスタマイズするための完全なアクセス許可が付与されます。 ただし、作成した環境エンティティのレコードの表示のみ行うことができます。 詳細情報: [カスタマイズに必要な特権](https://docs.microsoft.com/dynamics365/customer-engagement/customize/privileges-required-customization)        |
|Common Data Service ユーザー     |  読み取り、作成 (自己)、書き込み (自己)、削除 (自己)       | 環境内のアプリを実行し、自分が所有しているレコードの一般的なタスクを実行できます。        |
|代理人     | 別のユーザーの代わりに操作        | コードを別のユーザーとして実行するか、偽装するコードを実行できます。  通常、レコードへのアクセスを許可するためのセキュリティ ロールで使用されます。 詳細情報: [もう一方のユーザーの偽装](https://docs.microsoft.com/dynamics365/customer-engagement/developer/org-service/impersonate-another-user)        |

*特権は、特に指定されていない限り、グローバル スコープです。

## <a name="use-azure-active-directory-groups-to-manage-access"></a>Azure Active Directory グループを使用してアクセスを管理する
管理者は、組織の Azure Active Directory (Azure AD) グループを使って、ライセンスを持った Common Data Service ユーザーのアクセス権を管理できます。 Officeとセキュリティ、両方の Azure AD グループを使用して、ユーザーのアプリへのアクセス権を保護することができます。 詳細 : [グループ チームについて](/power-platform/admin/manage-teams#about-group-teams) 


### <a name="see-also"></a>関連項目
[モバイル デバイス上でモデル駆動型アプリを実行](../../user/run-app-client-model-driven.md)

[ユーザーを作成し、セキュリティ ロールを割り当てる](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles)


