---
title: キャンバス アプリを共有する | Microsoft Docs
description: アクセス許可を他のユーザーに付与することでキャンバス アプリを共有し、実行または修正します
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 06/01/2020
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c8e5ca63c3eb09909097001846deb334957e040f
ms.sourcegitcommit: 4311eef027ee7580a655fa8fb1566e944d6e8212
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "3421978"
---
# <a name="share-a-canvas-app-in-power-apps"></a>キャンバス アプリを Power Apps と共有する

ビジネス ニーズに対応するキャンバス アプリをビルドした後、アプリを実行できる組織内のユーザー、およびアプリを変更したり、再度共有したりすることもできるユーザーを指定します。 各ユーザーを名前で指定するか、Azure Active Directory のセキュリティ グループを指定します。 すべてのユーザーがアプリから恩恵を受ける場合、組織全体がアプリを実行できるように指定します。

> [!IMPORTANT]
> 期待どおり機能する共有アプリの場合、[Common Data Service](#common-data-service) または [Excel](share-app-data.md) などのアプリの基になるデータ ソースまたはソースのアクセス許可を管理する必要もあります。 アプリが依存する、フロー、ゲートウェイまたは接続などの[その他のリソース](share-app-resources.md) を共有する必要がある場合もあります。

## <a name="prerequisites"></a>前提条件

アプリを共有するには、そのアプリを[クラウドに保存](save-publish-app.md#save-changes-to-an-app) (ローカルではなく) および[発行](save-publish-app.md#publish-an-app) する必要があります。

- ユーザーがアプリで行う内容を理解し、リストで簡単に見つけられるように、アプリにわかりやすい名前と明確な説明を追加します。 Power Apps Studio の**ファイル**メニューで、**アプリの設定**を選び、説明を入力するか貼り付けます。

- 変更を加えるたびに、他のユーザーがそれらの変更を表示する必要がある場合は、再度アプリを保存および発行する必要があります。

## <a name="share-an-app"></a>アプリの共有

1. [Power Apps](https://make.powerapps.com) にサインインします。

1. 左側のウィンドウから、**アプリ**を選択します。

    ![アプリ リストの表示](./media/share-app/file-apps.png)

1. アイコンを選択して、共有するアプリを選択します。

    ![アプリの選択](./media/share-app/select-app.png)

1. トップ メニューから、**共有**を選択します。 また**その他のコマンド** (**...**) を選び、ドロップダウン メニューから**共有**を選択します:

    ![アプリの共有](./media/share-app/share-app.png)

1. アプリを共有する Azure Active Directory のユーザーまたはセキュリティ グループを、名前またはエイリアスで指定します。

    - 組織全体がアプリを実行できるようにするには (ただし、変更や共有はできません)、共有パネルに**すべてのユーザー**と入力します。

        ![すべてのユーザー](./media/share-app/everyone.png)

    - 項目ががセミコロンで区切られている場合、アプリをエイリアス、フレンドリ名、またはそれらの組み合わせのリスト (たとえば、**Meghan Holmes&lt;meghan.holmes@contoso.com>**) と共有できます。 複数のユーザーが同じ名前でエイリアスが異なる場合、最初に見つかったユーザーがリストに追加されます。 名前またはエイリアスにすでに権限がある、または解決できない場合は、ヒントが表示されます。

        ![個々のユーザー](./media/share-app/individual-user.png)

    > [!NOTE]
    > 組織内の配布グループ、または組織外のグループとアプリを共有することはできません。

1. ユーザーにアプリの編集および共有を許可する場合は、**共同所有者**チェック ボックスを選択します。

    ![共同所有者](./media/share-app/co-owner.png)

    [ソリューション内からアプリを作成した](add-app-solution.md) 場合、セキュリティ グループに**共同所有者**アクセス許可を付与できません。

    > [!NOTE]
    > 権限に関係なく、2 人が同時にアプリを編集することはできません。 1 人が編集のためにアプリを開いた場合、他の人はそれを実行できますが編集はできません。

1. 使用ているアプリが、ユーザーがアクセス権限を必要とするデータに接続する場合は、それらを指定します。

    たとえば、使用しているアプリが Common Data Service データベースのエンティティに接続する可能性があります。 そのようなアプリを共有すると、共有パネルはそのエンティティのセキュリティを管理するように求めます。

    ![セキュリティ ロールの割り当て](media/share-app/data-permissions-common-data-servicel.png)

    エンティティのセキュリティ管理の詳細については、[エンティティの権限を管理する](share-app.md#manage-entity-permissions) を参照してください。

    使用しているアプリが、ビジネス用 OneDrive でホストされている Excel ファイルなど他のデータ ソースへの接続を使用する場合、そのようなデータ ソースはアプリを共有するユーザーと共有するようにしてください。

    ![ビジネス用 OneDrive で Excel を共有](media/share-app/data-permissions-odb-excel.png)

    キャンバス アプリのリソースと接続の共有の詳細については、[キャンバス アプリのリソースを共有する](share-app-resources.md) を参照してください。

1. アプリを見つけてもらいやすくするには、**新規ユーザーに招待メールを送信する**チェック ボックスを選択してください。

    ![招待メールの送信](media/share-app/send-email-invitation.png)

1. 共有パネルの下部にある**共有**ボタンを選択します。

    モバイル デバイスの Power Apps モバイルを使用して、すぐにアプリを実行できます。 または、ブラウザーの [Dynamics 365](https://home.dynamics.com) にて、AppSource から実行可能です。 共同主催者は、[Power Apps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) のアプリを編集および共有できます。

    招待メールを送信した場合、ユーザーは招待メールのリンクを選択してアプリを実行することもできます。

    - ユーザーがモバイル デバイス上のリンクを選択すると、アプリは Power Apps モバイルで表示されます。
    - ユーザーがデスクトップ コンピューター上のリンクを選択すると、アプリがブラウザーで表示されます。

    招待状を受け取った共有者には、Power Apps Studio に編集用のアプリを開く別のリンクが表示されます。

ユーザーまたはセキュリティ グループのアクセス許可を変更するには:

- 共同主催者にアプリの実行を許可し、編集や共有は許可しないようにするには、**共同所有者**チェック ボックスをクリアにします。
- そのユーザーまたはグループとのアプリの共有を停止するには、削除 (x) アイコンを選択します。

## <a name="security-group-considerations"></a>セキュリティ グループの考慮事項

- セキュリティ グループの既存のすべてのメンバーは、アプリの権限を継承します。 セキュリティ グループに参加する新しいユーザーは、アプリのセキュリティ グループ権限を継承します。 グループを離れるユーザーは、そのグループを介してアクセスできなくなります。 ユーザーは、直接または別のセキュリティ グループのメンバーシップを通じて、引き続きアクセス許可を持つことができます。

- セキュリティ グループのすべてのメンバーは、アプリに対してグループ全体が持つのと同じアクセス許可を持っています。 ただし、グループの 1 人または複数のメンバーに、より高いアクセス許可を指定することで、アクセス レベルを高めることができます。 たとえば、アプリを実行するため、セキュリティ グループ A にアクセス許可を付与できます。 そして、そのグループに属しているユーザー B に**共同所有者**許可を与えることが可能です。 セキュリティ グループのすべてのメンバーがアプリを実行できますが、編集を行うことができるのはユーザー B だけです。 セキュリティ グループ A に対して**共同所有者**アクセス許可を付与し、ユーザー B に対してアプリを実行するアクセス許可を付与した場合でも、そのユーザーはアプリを編集できます。

### <a name="share-an-app-with-office-365-groups"></a>アプリを Office 365 グループと共有

アプリを [Office 365 グループ](https://docs.microsoft.com/office365/admin/create-groups/compare-groups#office-365-groups) と共有できます。 ただし、グループではセキュリティを有効にする必要があります。 セキュリティを有効にすると、Office 365 グループは、アプリまたはリソースにアクセスするための認証用セキュリティ トークンを受け取ることができます。

Office 365 グループでセキュリティが有効になっている場合、次の手順に従ってください:

1. [Azure AD cmdlets](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-v2-cmdlets) にアクセスできることを確認してください。

1. [Azure portal](https://portal.azure.com/) \> Azure Active Directory \> Groups \> 適切なグループの選択 \> オブジェクト ID をコピー、の順に移動します。

1. PowerShell を使用して、[Azure AD に接続](https://docs.microsoft.com/powershell/module/azuread/connect-azuread) します:

    ![AzureAD に接続](media/share-app/azure_cmdlet_connect.png)

1. [グループの詳細](https://docs.microsoft.com/powershell/module/AzureAD/Get-AzureADGroup) を、```Get-AzureADGroup -ObjectId <ObjectID\> |
    select *``` で取得します。 <br> 出力で、プロパティ **SecurityEnabled** が **True** に設定されていることを確認します:

    ![SecurityEnabled プロパティを確認](media/share-app/azure_cmdlet_get_azuread_group_details.png)

グループでセキュリティが有効になっていない場合は、**SecurityEnabled** プロパティを **True** に設定することで、PowerShell コマンドレット [AzureADGroup の設定](https://docs.microsoft.com/powershell/module/AzureAD/Set-AzureADGroup) を使い有効にできます: 

```Set-AzureADGroup -ObjectId <ObjectID> -SecurityEnabled $True```

![SecurityEnabled を True に設定](media/share-app/azure_cmdlet_set_security_enabled.png)

> [!NOTE]
> Office 365 グループの所有者となり、セキュリティを有効にする必要があります。
> SecurityEnabled プロパティを *true* に設定しても、Power Apps および Office 365 機能の動作に影響はありません。 既定で Azure AD 外の Office 365 グループを作成するとき、SecurityEnabled プロパティが *false* に設定されいるため、このコマンドは必要です。

しばらくすると、パネルを共有している Power Apps でグループを検出し、グループとアプリを共有できます。

## <a name="manage-entity-permissions"></a>エンティティのアクセス許可を管理する

### <a name="common-data-service"></a>Common Data Service

Common Data Service に基づいてアプリを作成する場合、アプリで使用される 1 つまたは複数のエンティティに対して適切なアクセス許可を持っているかを確認する必要があります。 特に、ユーザーは、関連するレコードの作成、読み取り、書き込み、削除などのタスクを実行できるセキュリティ ロールに属していなければなりません。 多くの場合、アクセス許可を持つ 1 つまたは複数のカスタム セキュリティ ロールを作成します。それは、アプリを実行するためにユーザーが必要とするものです。 そして、必要に応じて各ユーザーにロールを割り当てることができます。

> [!NOTE]
> 現時点において、Office グループ ではない Azure AD の個々のユーザーとセキュリティ グループにセキュリティ ロールを割り当てることができます。

#### <a name="prerequisite"></a>前提条件

ロールを割り当てるには、Common Data Service データベース用の**システム管理者**のアクセス許可を所有する必要があります。

#### <a name="assign-a-security-group-in-azure-ad-to-a-role"></a>Azure AD のセキュリティ グループをロールに割り当てる

1. 共有パネルで、**データのアクセス許可**の下の**セキュリティ ロールを割り当てる**を選択します。

1. 選択した Azure AD ユーザー (複数) または グループ (複数) に適用する Common Data Service ロール (複数) を選びます:

     ![セキュリティ ロールのリスト](media/share-app/cds-assign-security-role-list.png "セキュリティ ロールのリスト")

### <a name="common-data-service-previous-version"></a>Common Data Service (以前のバージョン)

古いバージョンの Common Data Service に基づくアプリを共有するときは、サービスに対する実行時のアクセス許可を別途共有する必要があります。 そのためのアクセス許可がない場合は、ご利用の環境の管理者に問い合わせてください。

## <a name="share-with-guests"></a>ゲストと共有する
 
Power Apps キャンバス アプリは、Azure Active Directory テナントのゲスト ユーザーと共有することができます。 これにより、外部のビジネス パートナー、請負業者、および第三者を招待して、会社のキャンバスアプリを実行できます。 

> [!NOTE]
> - ゲストに割り当てられるのは、**共同所有者**ロールではなく、共有してるアプリ用の**ユーザー**ロールです。
> - Power Apps キャンバス アプリのゲスト アクセスは、Azure B2B を利用します。 Power Apps は、[Azure B2B ドキュメント](https://docs.microsoft.com/azure/active-directory/b2b/user-properties) の状態 1 – 4 で、概説されているゲストを認識します。 Power Apps では、[Azure AD 直接連合](https://docs.microsoft.com/azure/active-directory/b2b/direct-federation) を使用して認証するゲストを認識できません。

### <a name="prerequisites"></a>前提条件

- Azure Active Directory (Azure AD) では、テナント用に B2B 外部コラボレーションを有効にします。 詳細: [B2B 外部コラボレーションを有効にし、ゲストを招待できるユーザーを管理する](/azure/active-directory/b2b/delegate-invitations)

    - B2B 外部コラボレーションの有効化は既定でオンになっています。 ただし、テナント管理者は設定を変更できます。Azure AD B2B 詳細については、[Azure AD B2B のゲスト ユーザー アクセスとは ?](/azure/active-directory/b2b/what-is-b2b) を参照してください  

- Azure AD テナントにゲスト ユーザーを追加できるアカウントへアクセスします。 ゲスト招待元ロールを持つ管理者およびユーザーは、ゲストをテナントに追加できます。

- ゲスト ユーザーは、次のいずれかのテナントを通じて割り当てられたアプリの機能と一致する Power Apps 使用権のライセンスを所持する必要があります。

    - 共有されているアプリをホストしているテナント。
    - ゲスト ユーザーのホーム テナント。

> [!NOTE]
> アプリ プランごとの Power Apps は、特定の環境のアプリに限定されているため、テナント間で認識できません。 Office およびユーザー プランごとの Power Apps に含まれる Power Apps は、特定の環境にバインドされないため、ゲスト シナリオのテナント全体で認識されます。 

### <a name="steps-to-grant-guest-access"></a>ゲスト アクセスを許可する手順

1. **新しいゲスト ユーザー**を選択して、Azure AD にゲスト ユーザーを追加します。 詳細: [クイック スタート: Azure AD に新しいゲスト ユーザーを追加する](/azure/active-directory/b2b/b2b-quickstart-add-guest-users-portal)。

    ![Azure AD にゲストを追加する](media/share-app/guest_access_doc_1.png "Azure AD にゲストを追加します")

2. ゲスト ユーザーがホーム テナントにライセンスを所持していない場合、ゲスト ユーザーにライセンスを割り当てます。

   - admin.microsoft.com からゲスト ユーザーを割り当てるには、[1 人のユーザーにライセンスを割り当てる](/office365/admin/subscriptions-and-billing/assign-licenses-to-users) を参照してください。

   - portal.azure.com からゲスト ユーザーを割り当てるには、[ライセンスの割り当てまたは削除](/azure/active-directory/fundamentals/license-users-groups) を参照してください。
 
   > [!IMPORTANT]
   > ゲストにライセンスを割り当てるには、Microsoft 365 管理センターのプレビューを無効にする必要がある場合があります。 

3. キャンバス アプリを共有します。 

    1. [Power Apps](https://make.powerapps.com) にサインインします。

    1. 左側のウィンドウから、**アプリ**を選択します。

    1. キャンバス アプリを選択します。

    1. コマンド バーから**共有**を選択します。

    1. ゲスト ユーザーのメールアドレスを Azure AD テナントから入力します。 詳細: [Azure AD B2B のゲスト ユーザー アクセスとは ?](/azure/active-directory/b2b/what-is-b2b)

        ![ゲストと共有する](media/share-app/guest_access_doc_2.png "ゲストと共有します")

ゲスト アクセス用のアプリを共有した後、ゲストは共有の一部として送信されたメールから、共有されているアプリを検出およびアクセスできます。 代わりに、アプリの URL をゲストと直接共有することもできます。 URL を見つけるには、[Power Apps](https://make.powerapps.com) へ移動し、左ペインから**アプリ**を選び、アプリを選択してから、**細部**タブを選びます。アプリの URL は **Web リンク**の下に表示されます。

![ゲストはアプリ共有メールを受け取ります](media/share-app/guest_access_doc_4.png "ゲストはアプリ共有メールを受け取ります")

### <a name="frequently-asked-questions"></a>よく寄せられる質問

#### <a name="whats-the-difference-between-canvas-app-guest-access-and-power-apps-portals"></a>キャンバス アプリのゲスト アクセスと Power Apps ポータルの違いは何ですか ?

キャンバス アプリを使用すると、C# などの従来のプログラミング言語でコードを記述することなく、ビジネス プロセスのデジタル化に合わせたアプリを構築できます。 キャンバス アプリのゲスト アクセスにより、共通のビジネスプ ロセスに参加しているさまざまな組織で構成される個人のチームが、 さまざまな Microsoft および第三者のソースと統合できる同じアプリリソースにアクセスできます。 詳細: [Power Apps のキャンバス アプリ コネクタの概要](/powerapps/maker/canvas-apps/connections-list)。

[Power Apps ポータル](/powerapps/maker/portals/overview) では、外部ユーザーが Common Data Service に格納されているデータを操作できるようにする、低コードで応答性の高い Web サイトを構築する機能 を提供します。 組織は、匿名または LinkedIn、Microsoft アカウントや他の商用ログイン プロバイダーなどの選択したログイン プロバイダーによる組織の外部ユーザーと共有できる Web サイトを作成することを可能にします。 

次の表は、Power Apps ポータルとキャンバス アプリの間のいくつかのコア機能の違いをまとめたものです。  

| | インターフェイス | 認証 | 可能なデータ ソース |
|------|--------|----------|-------------------|
| Power Apps ポータル | ブラウザーのみのエクスペリエンス | 匿名と認証済みアクセスを許可 | Common Data Service |
| キャンバス アプリ | ブラウザーとモバイル アプリ | Azure AD で認証を要求 | 指定なし ~150 の既定のコネクタとカスタム コネクタ  |
||

#### <a name="can-guests-access-customized-forms-in-sharepoint"></a>ゲストが SharePoint のカスタマイズ フォームにアクセスできますか?

はい。 SharePoint リストがカスタマイズ フォームにアクセスできるユーザーは、フォームを使用してリストの項目を作成および編集できます。 カスタム フォームが標準コネクタのみを使用している限り、ゲストは Power Apps ライセンスを持つ必要はありません。

#### <a name="why-is-a-guest-accessing-a-customized-form-in-sharepoint-prompted-for-a-trial"></a>ゲストが、トライアル用に促された SharePoint のカスタマイズ フォームにアクセスするのはなぜですか?

カスタム フォームがプレミアム コネクタを使用する場合、ゲストは Power Apps ライセンスを所有してカスタム フォームにアクセスする必要があります。 カスタム フォームが標準コネクタのみを使用する場合、テナントは Power Platform インターナル同意プランを許可し、ユーザーに割り当てられる必要があります。 Power Platform インターナル同意プランについては、[トライアル ライセンス コマンドのブロック](https://docs.microsoft.com/power-platform/admin/powerapps-powershell#block-trial-licenses-commands) を参照してください。  

#### <a name="can-guests-access-apps-embedded-in-sharepoint"></a>ゲストは SharePoint に埋め込まれたアプリにアクセスできますか?

はい。 ただし、キャンバスのスタンドアロン アプリにアクセスするには、アプリの機能と一致する Power Apps ユーザー権限のライセンスが必要です; 埋め込まれたアプリを含みます。 Microsoft Power Apps 埋め込みコントロールを使用して SharePoint のキャンバス アプリを埋め込む場合、アプリ ID を入力します。これを行うには、**アプリの Web リンクまたは ID** ボックスにアプリ ID を入力します。

![ゲスト用 SharePoint にキャンバス アプリを埋め込む](media/share-app/guest_access_doc_5.PNG "ゲスト用 SharePoint にキャンバス アプリを埋め込みます")

iFrame HTML タグを介して、SharePoint にキャンバス アプリを埋め込む場合、完全な Web URL を使用してアプリを参照します。 URL を見つけるには、[Power Apps](https://make.powerapps.com) にサイン インして、アプリを選び、**細部**タブを選択すると URL が**Web リンク**の下に表示されます。

![キャンバス アプリの詳細](media/share-app/guest_access_doc_6.PNG "キャンバス アプリの詳細")

#### <a name="how-come-guests-can-launch-the-app-shared-with-them-but-connections-fail-to-be-created"></a>ゲストが共有されているアプリを起動できるのに、接続を作成できないのはなぜですか?

ゲスト以外の場合と同様に、アプリがアクセスする基になるデータ ソース (複数) もゲストがアクセスできるようにする必要があります。

#### <a name="what-license-must-be-assigned-to-my-guest-so-they-can-run-an-app-shared-with-them"></a>ゲストが共有するアプリを実行できるようにするには、ゲストにどのライセンスを割り当てる必要がありますか。

非ゲストがアプリを実行するために必要な同じライセンス。 たとえば、アプリがプレミアム コネクタを使用している場合、アプリ プランごとの Power Apps またはユーザー プランごとの Power Apps をゲストに割り当てる必要があります。  

|                                 | SharePoint カスタマイズ フォーム | 非プレミアム コネクタを使用するスタンドアロン キャンバス アプリ | プレミアム コネクタを使用するスタンドアロン キャンバス アプリ | モデル駆動型アプリ |
|---------------------------------|----------------------------|----------------------------------------------------|------------------------------------------------|------------------|
| SharePoint ユーザー (PA ライセンスなし) | x                          |                                                    |                                                |                  |
| Power Apps オフィス付き    | x                          | x                                                  |                                                |                  |
| アプリ プランごとの Power Apps          | x                          | x                                                  | x                                              | x                |
| ユーザー プランごとの Power Apps         | x                          | x                                                  | x                                              | x                |

価格とさまざまなプランの機能に関する詳細は、[Microsoft Power Apps および Power Automate ライセンス ガイド](https://go.microsoft.com/fwlink/?linkid=2085130) を参照してください。

#### <a name="in-power-apps-mobile-how-does-a-guest-see-apps-for-their-home-tenant"></a>Power Apps モバイルに、ゲストはホーム テナント用のアプリをどのように表示しますか?

モバイル デバイスでキャンバス アプリにアクセスしたユーザー、ホーム テナントではない Azure AD テナントで公開されたユーザーは、Power Apps からサイン アウトして Power Apps モバイルに再びサイン インする必要があります。  

#### <a name="in-power-apps-mobile-how-does-a-guest-see-apps-in-the-guest-tenant"></a>Power Apps モバイルに、ゲストはゲスト テナントのアプリをどのように表示しますか?

ゲスト ユーザーとして、ゲスト テナントのアプリが共有されたときに受信したメールを開き、**アプリを開く**ボタンを選択します。 これは Azure Active Directory と Microsoft アカウント ユーザーの両方に適用されます。   

#### <a name="must-a-guest-accept-the-azure-ad-guest-invitation-before-sharing-an-app-with-the-guest"></a>アプリをゲストと共有する前に、Azure AD ゲスト招待ゲストを受け入れる必要がありますか?

番号 ゲストが、ゲスト招待を受け入れる前に共有されているアプリを起動した場合、アプリの起動中にサイン インのエクスペリエンスの一部として招待を受け入れるように求められます。  

#### <a name="what-azure-ad-tenant-are-connections-for-a-guest-user-created-in"></a>作成されたゲスト ユーザーの接続は、どの Azure AD テナントですか?

アプリの接続は、常にアプリが関連付けられている Azure AD テナントのコンテキストで行われます。 たとえば、アプリが Contoso テナントで作成された場合、Contoso 内部とゲスト ユーザーに対して行われた接続は、Contoso テナントのコンテキスト内にあります。

#### <a name="can-guests-use-microsoft-graph-via-microsoft-security-graph-connector-or-a-custom-connector-using-microsoft-graph-apis"></a>ゲストは、Microsoft Security Graph コネクタまたは Microsoft Graph API を使用するカスタム コネクタを介して、Microsoft Graph を使用できますか?

いいえ、Azure AD ゲストは、ゲストであるテナントの情報を取得するために Microsoft Graph をクエリできません。

#### <a name="what-intune-policies-apply-to-guests-using-my-power-apps"></a>自身の Power Apps を使用してゲストに適用するのは、どの Intune ポリシーですか?

Intune は、ユーザーのホーム テナントのポリシーのみを適用します。 たとえば、Lesa@Contoso.com が Wanda@Fabrikam.com とアプリを共有している場合、Intune は、Wanda が実行するアプリに関係なく、Wanda のデバイスに Fabrikam.com ポリシーを適用し続けます。

#### <a name="what-connectors-support-guest-access"></a>ゲスト アクセスをサポートするのは、どのコネクタですか?

あらゆるタイプの Azure AD 認証のを使用しないすべてのコネクタは、ゲスト アクセスをサポートします。 次の表は、Azure AD 認証を使用するすべてのコネクタと、現在どのコネクタがゲスト アクセスをサポートしているかを列挙しています。

| **コネクタ**                                     | **ゲスト アクセスをサポート**                                              |
|---------------------------------------------------|------------------------------------------------------------------------|
| 10to8 Appointment Scheduling                      | No                                                                     |
| Adobe Creative Cloud                              | No                                                                     |
| Adobe Sign                                        | No                                                                     |
| Asana                                             | No                                                                     |
| AtBot Admin                                       | No                                                                     |
| AtBot Logic                                       | No                                                                     |
| Azure AD                                          | 有効                                                                    |
| Azure の自動化                                  | 有効                                                                    |
| Azure Container Instance                          | 有効                                                                    |
| Azure Data Factory                                | 有効                                                                    |
| Azure Data Lake                                   | 有効                                                                    |
| Azure DevOps                                      | No                                                                     |
| Azure Event Grid                                  | No                                                                     |
| Azure IoT Central                                 | 有効                                                                    |
| Azure Key Vault                                   | No                                                                     |
| Azure Kusto                                       | 有効                                                                    |
| Azure ログ分析                               | 有効                                                                    |
| Azure Resource Manager                            | 有効                                                                    |
| Basecamp 2                                        | No                                                                     |
| Bitbucket                                         | No                                                                     |
| Bitly                                             | No                                                                     |
| bttn                                              | No                                                                     |
| Buffer                                            | No                                                                     |
| Business Central                                  | No                                                                     |
| CandidateZip                                      | No                                                                     |
| Capsule CRM                                       | No                                                                     |
| Cloud PKI Management                              | No                                                                     |
| Cognito Forms                                     | No                                                                     |
| Common Data Service                               | はい*                                                                     |
| Common Data Service (レガシ)                      | No                                                                     |
| D&B Optimizer                                     | No                                                                     |
| Derdack SIGNL4                                    | No                                                                     |
| Disqus                                            | No                                                                     |
| Document Merge                                    | No                                                                     |
| Dynamics 365                                      | No                                                                     |
| Dynamics 365 AI for Sales                         | 有効                                                                    |
| Dynamics 365 for Fin & Ops                        | No                                                                     |
| Enadoc                                            | No                                                                     |
| Eventbrite                                        | No                                                                     |
| Excel Online (Business)                           | No                                                                     |
| Excel Online (OneDrive)                           | No                                                                     |
| Expiration Reminder                               | No                                                                     |
| FreshBooks                                        | No                                                                     |
| GoToMeeting                                       | No                                                                     |
| GoToTraining                                      | No                                                                     |
| GoToWebinar                                       | No                                                                     |
| Harvest                                           | No                                                                     |
| HTTP with Azure AD                                | No                                                                     |
| Infusionsoft                                      | No                                                                     |
| Inoreader                                         | No                                                                     |
| Intercom                                          | No                                                                     |
| JotForm                                           | No                                                                     |
| kintone                                           | No                                                                     |
| LinkedIn                                          | No                                                                     |
| Marketing Content Hub                             | No                                                                     |
| 中                                            | No                                                                     |
| Metatask                                          | No                                                                     |
| Microsoft Forms                                   | No                                                                     |
| Microsoft Forms Pro                               | No                                                                     |
| Microsoft Graph Security                          | No                                                                     |
| Microsoft Kaizala                                 | No                                                                     |
| Microsoft School Data Sync                        | No                                                                     |
| Microsoft StaffHub                                | No                                                                     |
| Microsoft Teams                                   | 有効                                                                    |
| Microsoft To-Do (ビジネス)                        | No                                                                     |
| Muhimbi PDF                                       | No                                                                     |
| NetDocuments                                      | No                                                                     |
| Office 365 Groups                                 | 有効                                                                    |
| Office 365 Outlook                                | No                                                                     |
| Office 365 Users                                  | 有効                                                                    |
| Office 365 Video                                  | No                                                                     |
| OneDrive                                          | No                                                                     |
| OneDrive for Business                             | No                                                                     |
| OneNote (Business)                                | No                                                                     |
| Outlook Customer Manager                          | No                                                                     |
| Outlook Tasks                                     | 有効                                                                    |
| Outlook.com                                       | No                                                                     |
| Paylocity                                         | No                                                                     |
| Planner                                           | No                                                                     |
| Plumsail Forms                                    | No                                                                     |
| Power BI                                          | 有効                                                                    |
| Project Online                                    | No                                                                     |
| ProjectWise Design Integration                    | No                                                                     |
| Projectwise Share                                 | No                                                                     |
| SharePoint                                        | 有効                                                                    |
| SignNow                                           | No                                                                     |
| Skype for Business Online                         | No                                                                     |
| Soft1                                             | No                                                                     |
| Stormboard                                        | No                                                                     |
| Survey123                                         | No                                                                     |
| SurveyMonkey                                      | No                                                                     |
| Toodledo                                          | No                                                                     |
| Typeform                                          | No                                                                     |
| Vimeo                                             | No                                                                     |
| Webex Teams                                       | No                                                                     |
| Windows Defender Advanced Threat Protection (ATP) | No                                                                     |
| Word Online (Business)                            | No                                                                     |

\*Common Data Service コネクタを使用する場合、自分が Common Data Service を配置しているのと同じテナントからゲスト ユーザーがライセンス付与されていることを確認してください。
