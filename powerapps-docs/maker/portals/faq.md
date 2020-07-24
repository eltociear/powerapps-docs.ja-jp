---
title: よくあるご質問 | Microsoft Docs
description: Power Apps ポータルに関してよくあるご質問。
author: sandhangitmsft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 05/21/2020
ms.author: sandhan
ms.reviewer: tapanm
ms.openlocfilehash: b36d49d4fbf0c1fe16cfdfe64349782e3cf80040
ms.sourcegitcommit: c12260f372ad2cc48d3146be570d2088c9ef1d86
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2020
ms.locfileid: "3494337"
---
# <a name="power-apps-portals-faq"></a>Power Apps ポータルに関する FAQ

必要な情報がすぐに手に入るように、よく寄せられる質問とその簡潔な回答を一覧にまとめました。

## <a name="general"></a>全般

### <a name="rendering-power-bi-report-on-my-portal-page-fails-with-the-following-error"></a>ポータル ページ で Power BI レポートのレンダリングが次のエラーで失敗します:

*レポートの表示中に構成エラーが発生しました。*

これは、次のような複数の理由により発生する可能性があります:

- [Power BI Embedded 構成](admin/set-up-power-bi-integration.md) が正しくありません。
- Power BI の [行レベルのセキュリティ](https://docs.microsoft.com/power-bi/admin/service-admin-rls) は有効になっていますが、[Power BI コンポーネント構成](compose-page.md#add-power-bi) (詳細設定) のロール、または [Power BI の Liquid タグ](liquid/portals-entity-tags.md#powerbi) の *ロール* パラメータを渡していません。
- Power BI [開発者設定](https://docs.microsoft.com/power-bi/admin/service-admin-portal#developer-settings) で **アプリにコンテンツを埋め込む** が有効になっていません。

### <a name="does-power-apps-portals-support-tls-12"></a>Power Apps ポータルは TLS 1.2 をサポートしていますか?

Power Apps ポータル バージョン 8.3 以降で [TLS 1.2](https://support.microsoft.com/help/4041984/portal-capabilities-for-microsoft-dynamics-365-version-8-3-2-85-releas) をサポートしています。

### <a name="what-is-the-difference-between-power-apps-portals-dynamics-365-portals-and-add-on-portals"></a>Power Apps ポータル、Dynamics 365 ポータル、アドオン ポータルとの違いは?

2019 年 10 月 1 日の Power Apps ポータル発売に伴い、Dynamics 365 ポータルは Power Apps ポータルと呼ばれます。 つまり、すべてのポータルは **Power Apps ポータル** と呼ばれます。

2019 年 10 月 1 日以降にポータルに導入された主要な変更の1つは、ライセンス モデルです。 以前は、ポータルは Dynamics 365 アプリのアドオンとしてライセンスされていましたが、特定の Dynamics 365 ライセンスには既定のポータルアド オンが含まれていました。 2019 年 10 月 1 日以降、ポータルは [使用方法に基づいてライセンス](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#can-you-share-more-details-regarding-the-new-power-apps-portals-licensing) されます。 既存のすべてのポータルは、現在の顧客契約に基づく移行期間の一部となり、その後、新しいライセンス モデルに変換する必要があります。

[Power Apps ポータル管理センター](./admin/admin-overview.md) からポータルの種類を確認できます:

![Power Apps ポータルの種類](./media/power-apps-portals-type.png)

容量ベースのライセンスとアドオン ベースのライセンスを持つ Power Apps ポータル間のその他の相違点:

- アドオン ポータルの場合、ポータルの種類に 'アドオン' という接尾辞が追加されます。 たとえば、運用アドオン ポータルの種類は '運用 (アドオン)' としてリストされます。
- Power Apps ポータルには、アドオン ベースのライセンス ポータルと比較して [異なるキャッシング メカニズム](admin/clear-server-side-cache.md) があります。
- プロビジョニング方法は、容量ベースのライセンスを持つポータルとアドオン ベースのライセンスでは異なります。

次の記事で説明されている手順を使用して、容量ベースのライセンスで Power Apps ポータル作成できます:

- [Common Data Service スターター ポータルの作成](create-portal.md)
- [Dynamics 365 環境でポータルを作成](create-dynamics-portal.md)

アドオン ベースのライセンスで Power Apps ポータルを作成するには、[ポータル アドオンを使用してポータルをプロビジョニング](provision-portal-add-on.md) を参照してください。

アドオン ベースのライセンスと容量ベースのライセンスのライセンスの違いについては、[Power Apps ポータル ライセンスに関する FAQ](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#what-is-the-difference-between-power-apps-portals-and-dynamics-365-portals-in-terms-of-licensing) を参照してください。

### <a name="when-is-an-add-on-portal-in-suspended-state"></a>アドオン ポータルが停止状態になるのはどのような場合ですか？

ポータル [ポータル アドオン プランを 使用した プロビジョニング](provision-portal-add-on.md) 以前に購入したものは、有効期限が切れると停止します。 この有効期限は、試用版 ポータル の場合は 30日間ですが、この期限は購入した ライセンス が 運用環境の アドオンポータル のによって異なる場合があります。 停止中の試用版ポータルは7日後に削除されますが、この停止期間は運用ポータルによって異なります。 詳細については、アドオン ポータルの [ポータル の ライフサイクル](./admin/portal-lifecycle.md#considerations-for-add-on-portals) をご確認ください。

### <a name="how-do-i-redirect-a-user-to-a-default-page-after-signing-in"></a>サインイン後にユーザーを既定のページにリダイレクトする方法を教えてください。

サインインすると、ユーザーを既定のページにリダイレクトするポータルを構成できます。 この機能を実現するには、ホーム Web テンプレートに JavaScript コードを含めることができます。

たとえば、サインインした後にすべてのユーザーをフォーラム ページにリダイレクトする場合は、次のようにホーム Web テンプレートに JavaScript コードを含めることができます。

```xml
{% if user %}
//if any user logs in
<script>
  window.location.href='./forums/'
</script>
{% else %}
//Home web page code, if you don't want to display the page when the user is being redirected
{% endif %}
//Home web page code, if you want to display the page when the user is being redirected
```

流動テンプレートの使用に関する詳細については、[流動テンプレートの使用](liquid/liquid-overview.md) を参照してください。

### <a name="im-getting-an-error-that-only-one-portal-can-be-created"></a>作成できるポータルは一つのみです、というエラーが表示されます。

現在、一言語あたり、一環境につき各種類で一つのポータルのみ作成できます。 1 つ以上のポータルを作成した場合は、次のエラー メッセージが表示されます:

> [!div class=mx-imgBorder]
> ![ポータル作成の上限に達したエラー](media/portal-max-error.png "ポータル作成の上限に達したエラー")

より多くのポータルを作成するには、エラー メッセージ内の**新しい環境の作成** リンクを使用して新しい環境を作成する必要があります。 ポータルの作成に関する詳細情報は、[ポータルの作成](create-portal.md)を参照してください。

### <a name="im-getting-an-error-that-i-cant-delete-my-portal"></a>ポータルを削除できないというエラーメッセージが表示されます。

ポータルを削除するために十分な特権がない場合、次のエラーが表示されます:

> [!div class=mx-imgBorder]
> ![ポータルの削除エラー](media/portal-delete-error.png "ポータルの削除エラー")

ポータルの削除と必要な特権の詳細については、[ポータルの削除](manage-existing-portals.md#delete)を参照してください。

### <a name="im-getting-an-error-that-i-cant-create-a-portal"></a>ポータルを作成できないというエラーメッセージが表示されます。

その環境でポータルを作成するための適切な特権を持っていない場合は、次のエラーが表示されます:

> [!div class=mx-imgBorder]
> ![ポータルの作成エラー](media/portal-create-error.png "ポータルの作成エラー")

ポータルの削除と必要な特権の詳細については、[ポータルの削除](create-portal.md)を参照してください。

### <a name="im-getting-the-message-your-data-isnt-quite-ready"></a>「あなたのデーターの準備ができていません」というメッセージが表示されます。

時々、データベース作成に時間がかかることがあり、適切な状態がホーム ページに反映されていない場合もあります。 この場合、次のメッセージが表示されます:

> [!div class=mx-imgBorder]
> ![データが準備できていません](media/data-not-ready.png "データが準備できていません")

"データベースの作成" プロンプトや "データの準備ができていません" プロンプトが何度も表示される場合は、**空のポータル** タイルを選択する前に、Power Apps ホーム ページを更新してみてください。

### <a name="im-getting-an-error-that-i-dont-have-required-permissions-to-create-azure-active-directory-applications"></a>Azure Active Directory アプリケーションの作成に必要なアクセス許可がありません、というメッセージが表示されます。

ポータルを作成する際、新しいアプリケーションとしてのポータルは、そのテナントに関連付けられた Azure Active Directory に登録されています。 自分の Azure Active Directory テナントでアプリケーションに登録するために適切なアクセス許可を持っていない場合は、次のエラーメッセージが表示されます。

> [!div class=mx-imgBorder]
> ![Azure Active Directory エラー](media/azure-ad-error.png "Azure Active Directory エラー")

Azure Active Directory でアプリケーションの作成および登録するには、**アプリ登録**設定をあなたのテナント用に有効化してもらうように自分のテナント管理者に問い合わせてください。 詳細については、[必要なアクセス許可](https://docs.microsoft.com/azure/active-directory/develop/howto-create-service-principal-portal#required-permissions)をご覧ください。

### <a name="im-getting-an-error-that-portal-creation-is-blocked-in-this-tenant-by-global-administrator"></a>グローバル管理者によって、このテナントでのポータル作成がブロックされている、というエラーが表示されています。

グローバル管理者によってテナントでポータル作成がブロックされている場合は、次のエラーが表示されます。

> [!div class=mx-imgBorder]
> ![ポータル作成ブロックエラー](media/portal-create-blocked-error.png "ポータル作成ブロックエラー")

グローバル管理者に連絡をして、非管理者によるポータルの作成も有効にしてください。

あなた自身がグローバル管理者の場合は、PowerShell を通じて `disablePortalsCreationByNonAdminUsers` テナント レベルの設定を無効にする必要があります。 PowerShell ウィンドウで次のコマンドを実行します (PowerShellを管理者として実行)。

```
Set-TenantSettings -RequestBody @{ "disablePortalsCreationByNonAdminUsers" = $false }
```

詳細: [テナントでポータル作成を無効化する](create-portal.md#disable-portal-creation-in-a-tenant)

### <a name="im-getting-an-error-that-i-dont-have-appropriate-license-to-access-this-website"></a>この Web サイトにアクセスするための適切なライセンスがありませんというエラーが表示されます。

ポータルを使用して認証済みページにアクセスする組織内ユーザーは、ポータルが接続されている環境にライセンスを割り当てる必要があります。 内部ユーザーのポータルのユーザー権限について詳しくは、 [こちら](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#can-you-clarify-the-use-rights-to-portals-for-internal-users) をご覧ください。 環境にライセンスが割り当てられていない場合、内部ユーザーは次のようなエラーを受け取ります:

> [!div class=mx-imgBorder]
> ![ポータル ログイン エラー](media/portal-login-error.png "ポータル ログイン エラー")

## <a name="licensing-and-provisioning"></a>ライセンスとプロビジョニング

### <a name="how-do-i-get-a-portal-subscription"></a>どのようにポータル サブスクリプションを取得しますか。

[Power Apps ポータル](overview.md) は、Power Apps でスタンドアロンとして利用できるようになりました。 ポータル の プロビジョニング にあたって ライセンス を取得する必要はなくなりました。 ポータル に ユーザーが アクセス するには、ペルソナ の タイプ に応じたライセンスが必要です。 詳細は、 [Power Appsポータル ライセンスに関するよくある質問](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#can-you-share-more-details-regarding-the-new-power-apps-portals-licensing)を参照してください。

### <a name="how-do-i-change-the-audience-and-type-of-a-portal-after-its-provisioned"></a>プロビジョニング後、どのようにポータルの対象者と種類を変更しますか?

ポータルをプロビジョニングすると、ポータル対象者を変更するオプションが無効になります。

ただし、[Dynamics 365 インスタンス、対象者、またはポータルの種類の変更](admin/change-dynamics-instance.md) の手順に従うことによって、プロビジョニング後に、ポータルの対象者と種類を変更できます。

> [!NOTE]
> - 対象者、ポータルの種類、組織などを変更するには、ポータルを再度リセットしてプロビジョニングすることをお勧めします。 詳細: [ポータルのリセット](admin/reset-portal.md)
> - Dynamics 365 インスタンスの変更は、古いポータルアドオンを使用してプロビジョニングされたポータルにのみ適用されます。

### <a name="how-do-i-change-the-base-url-of-a-portal-after-its-provisioned"></a>プロビジョニングの後、どのようにポータルの基本 URL を変更しますか?

[ポータルの基本 URL の変更](admin/change-base-url.md) のステップに従うことによって、プロビジョニング後にポータルの基本 URL を変更できます。

### <a name="how-do-i-delete-a-portal-completely-after-its-provisioned"></a>プロビジョニング後、ポータルを完全に削除するにはどうすればよいですか?

ポータルは、次のコンポーネントで構成されています。

- **ポータル Web サイトのホスト**: ポータル Web サイトのホストは実際の Web サイトを形成するポータル コードです。

- **ポータル ソリューション**:  Common Data Service 環境にインストールされ、任意のポータルのメタデータ エンティティを含むソリューションです。

ポータルを完全に削除するには、ポータル Web サイト ホストを削除し、ポータル ソリューションを Common Data Service 環境からアンインストールする必要があります。

ポータル ホストをリセットするには、「[ポータルのリセット](admin/reset-portal.md)」の手順に従います。 ポータル ホストをリセットしても Common Data Service 環境で行われた構成には影響しないことに注意してください。

ポータル ソリューションを削除するには、Dynamics 365 のソリューション エクスプローラー UI からソリューションを削除する必要があります。 アンインストールするポータル ソリューションの順序は「[ポータル ソリューションのアンインストール](https://community.dynamics.com/365/b/dynamics365portalssupport/archive/2017/02/27/portal-troubleshooting-part-three-uninstalling-portal-solutions)」に記載されています。

## <a name="common-data-service-environment-lifecycle"></a>Common Data Service 環境のライフサイクル

### <a name="we-recently-moved-our-common-data-service-environment-from-one-geolocation-or-tenant-to-another-how-do-we-handle-portals-connected-to-our-organization"></a>最近、ある物理的場所またはテナントから別の物理的場所またはテナントに Common Data Service 環境を移動しました。 どのように組織に接続されたポータルを扱いますか。

ある位置情報またはテナントから別の位置情報またはテナントに Common Data Service 環境を移動しても、その組織に関連付けられたポータルは、自動的に移動しません。 また、組織を移動したため、その組織に関連付けられたポータルは動作しなくなり、起動時にエラーがスローされます。

関連した組織にポータルを再度関連付けるには:

1. 「[ポータルのリセット](admin/reset-portal.md)」の手順に従って、既存の物理的場所またはテナントから既存のポータル ホストをリセットします。 これにより、関連付けられたポータルのリソースは削除され、操作が完了した後はポータル URL にアクセスできなくなります。

2. 既存のポータルがリセットされた後、新しいテナント (または既存のテナントの新しい物理的場所) に移動し、そこで使用可能なポータルをプロビジョニングします。

### <a name="after-restoring-a-common-data-service-environment-from-an-old-backup-the-portal-connected-to-the-organization-isnt-working-how-do-we-fix-it"></a>古いバックアップから Common Data Service 環境を復元した後は、組織に接続されたポータルは機能しません。 どのように修正しますか。

Common Data Service 環境がバックアップから復元されるとき、ポータルの組織とのつながりを壊す可能性のあるさまざまな変更が組織に加えられます。 この問題を解決するには、以下を行います。

- 組織 ID が復元操作後と同じで、ポータル ソリューションも使用できる場合:

    1. [Power Apps ポータル管理センター](admin/admin-overview.md) を開きます。
    2. **ポータルの詳細** タブに移動します。
    3. **ポータルの状態**ドロップダウン リストで、**オフ**を選択します。
    4. **更新**を選択します。 
    5. 更新操作が完了したら、**ポータルの状態**ドロップダウン リストを**オン**に設定し、**更新**を選択します。

  ポータルは再起動し、つながりが組織に再度作成されます。

- 組織 ID が復元操作後と異なる、または組織からポータル ソリューションが削除された場合:

  - この場合は [ポータルのリセット](admin/reset-portal.md) の手順に従ってポータルをリセットし、その後で再プロビジョニングすることをお勧めします。

### <a name="we-recently-changed-the-url-of-our-common-data-service-environment-and-our-portal-stopped-working-how-do-we-fix-it"></a>最近、Common Data Service 環境の URL を変更したところ、ポータルは機能しなくなりました。 どのように修正しますか。

Common Data Service 環境の URL を変更すると、ポータルは Common Data Service 環境 の URL を特定できなくなるため、機能を停止します。 この問題を解決するには、以下を行います。

1. [Power Apps ポータル管理センター](admin/admin-overview.md) を開きます。
2. **ポータル アクション** > **Dynamics 365 の URL を更新**に移動します。
3. ウィザードの指示に従います。

ポータルは再起動され、再び稼働を開始します。

## <a name="debugging-and-fixing-problems"></a>デバッグおよび問題の修正

### <a name="performance-of-entity-forms-actions-such-as-createupdatedelete-on-entity-forms-take-a-lot-of-time-to-complete-or-timeout"></a>エンティティ フォームのパフォーマンス: エンティティ フォームの作成/更新/削除などのアクションは、完了またはタイムアウトするまでに多くの時間がかかります。

これは、データや Common Data Service のエンティティで行われたカスタマイズに依存するなど、複数の理由で発生する可能性があります。 ポータルからのレコード アクションに関するこのようなパフォーマンス関連の問題をトラブルシューティングするときは、これらの遅延を引き起こす可能性のあるイベントに同期プラグインが登録されていないことを確認してください。 可能な限り、それらを非同期に実装して、トランザクションを保持または遅延させないようにしてください。

### <a name="when-accessing-my-portal-i-see-a-generic-error-page-how-can-i-see-the-actual-error"></a>ポータルにアクセスすると、汎用エラー ページが表示されます。 どのように実際のエラーを表示しますか。

ポータルを表示しようとするとサーバー エラーが発生し、そのたびにエンド ユーザーにはエラーのタイムスタンプと活動 ID とともに汎用エラー ページが表示されます。 ポータル管理者はポータルを構成して、デバッグおよび問題の修正に役に立つ実際エラーの詳細を取得できます。 実際のエラーを表示するには:

- **ポータルのユーザー定義のエラー ページの無効化**: これにより、ユーザー定義のエラー ページが無効になり、そのページを参照する時にエラーの完全なスタック トレースを確認できます。 「[ユーザー定義のエラーを無効にする](admin/view-portal-error-log.md#disable-custom-error)」の手順に従って、ユーザー定義のエラーを無効にできます。

ポータルを開発しているときにのみ、これを使用することをお勧めします。 ポータルがユーザーに対して使用可能になった後、ユーザー定義のエラーを再び有効にする必要があります。 詳細: [ポータル エラー ログの表示](admin/view-portal-error-log.md)

- **診断ログを有効にする**: これにより、Azure Blob Storageの取引先企業のすべてポータル エラーを取得できます。 「[ポータル エラー ログへのアクセス](admin/view-portal-error-log.md#access-portal-error-logs)」の手順に従って、診断ログを有効にできます。

診断ログを有効にすると、汎用エラー ページに表示されている活動 ID を使用して、ユーザーが報告する特定のエラーを検索できます。 活動 ID はエラーの詳細とともにログに記録され、実際の問題の発見に役立ちます。

## <a name="portal-administration-and-management"></a>ポータル管理および操作

### <a name="do-portals-use-any-static-content-from-cdns-content-delivery-network-that-i-need-to-whitelist"></a>ポータルは、ホワイトリストに登録する必要がある CDN (コンテンツ配信ネットワーク) の静的コンテンツを使用しますか?

はい。 Power Apps ポータルは、既定の JavaScript と以前ポータルアプリの一部として表示されたプレゼンテーション用の CSS ファイルを含む Azure CDN からの、すぐに使えるポータルの静的資産を使用します。 ポータルを正常に表示するには、次の CDN URLをホワイトリストに登録する必要があります。

    https://content.powerapps.com/resource/powerappsportal

> [!NOTE]
> Microsoft Government Cloudでホストされている Power Apps ポータルは CDN を使用しません。

### <a name="how-do-i-use-a-custom-login-provider-on-my-portal"></a>ポータルでどのようにカスタム ログイン プロバイダーを使用しますか。

ポータルは標準認証プロトコルのサポートを提供する任意のカスタム ログイン プロバイダーをサポートします。 任意のカスタム IDP では OpenIdConnect、SAML2、および WS-Federation プロトコルがサポートされます。 Oauth 2 は一定の既知の IDP でのみサポートされます。 IDP 構成のセットアップ方法の詳細については、[ポータル認証の構成](configure/configure-portal-authentication.md) を参照してください。

### <a name="how-do-i-get-new-portal-releases-in-my-sandbox-portal-first-before-it-gets-applied-to-production"></a>運用環境に適用する前に、まず自分のサンドボックス ポータルで新しいポータル リリースを取得する方法を教えてください。

すべてのポータル リリースは、初期アップグレードおよび一般提供 (GA) の2 つの段階で実行されます。 初期アップグレード段階では、初期アップグレードにマークされたポータルのみをアップグレードします。 自分のサンドボックス (開発環境またはテスト) 環境で新しいポータル リリースを取得するため、自分のポータルを初期アップグレードに対して有効化することができます。 初期アップグレードに対してポータルを有効化する方法については、「[ポータルのアップグレード](https://docs.microsoft.com/dynamics365/customer-engagement/portals/upgrade-portal)」を参照してください。

### <a name="how-do-i-use-a-custom-domain-name-for-my-portal"></a>自分のポータルでカスタム ドメイン名を使用する方法を教えてください。

標準の `microsoftcrmportals.com` ドメイン名の代わりにカスタム ドメイン名を使用するようにポータルを有効化することができます。 詳細: [ポータルをカスタム ドメインにリンクする](admin/add-custom-domain.md)

## <a name="portal-checker"></a>ポータル チェッカー

### <a name="portal-doesnt-load-and-displays-a-generic-error-page-server-error-in--application"></a>ポータルは読み込まれず、一般的なエラー ページ ("/" アプリケーションでのサーバー エラー) を表示します 

この問題は、ポータルが基礎となる Common Data Service 環境に接続できない場合、Common Data Service 環境が存在しないか URL が変更された場合、Common Data Service 環境への要求がタイムアウトした場合など、さまざまな理由で発生する可能性があります。 ポータル チェッカー ツールを実行すると、厳密の原因を判断しようとし、正しいを軽減策を提示します。 

最も一般的な原因と対応する軽減策手順の一覧を以下に示します:

#### <a name="url-of-the-connected-common-data-service-environment-has-changed"></a>接続された Common Data Service 環境の URL が変更されました。 

これは、ポータルから組織に対してプロビジョニングされた後、Common Data Service 環境の URL がユーザーによって変更されたときに発生します。 この問題を修正するには、Dynamics 365 の URL を更新します。

1. [Power Apps ポータル管理センター](admin/admin-overview.md) を開きます。
2. **ポータル アクション** > **Dynamics 365 の URL を更新**に移動します。 

この操作が正常に実行されると、Common Data Service 環境 URL が更新され、ポータルが動作を開始します。

#### <a name="common-data-service-environment-connected-to-your-portal-is-in-administration-mode"></a>ポータルに接続された Common Data Service 環境が管理者モードになっている

この問題は、組織を運用モードからサンドボックス モードに変更したり、組織管理者により手動で変更した場合に、Common Data Service 環境が管理モードになると発生します。

これが原因である場合は、[ここ](https://docs.microsoft.com/dynamics365/admin/manage-sandbox-instances#administration-mode) にリストされたアクションを実行して管理モードを無効にできます。 管理モードを無効にすると、ポータルは問題なく機能します。

#### <a name="authentication-connection-between-common-data-service-environment-and-portal-is-broken"></a>Common Data Service 環境とポータルとの間の、認証のための接続が切断されています

これは、Common Data Service 環境がバックアップから復元されたか、バックアップから削除または再作成されたため、Dynamics 365 組織とポータル間の認証接続が切断されると発生する問題です。 この問題を解決するには、以下を行います。

1. [Power Apps ポータル管理センター](admin/admin-overview.md) を開きます。
2. **ポータルの詳細** タブで、**ポータルの状態** リストから **オフ** を選択します。
3. **更新**を選択します。
4. **ポータルの状態** の一覧から **オン** を選択します。
5. **更新** を選択します。 ポータルが再起動し、認証接続できるようになります。

特定の状況では、特に組織 ID が復元操作後に変更された場合 (または組織を再プロビジョニングした場合)、これらの軽減策は機能しません。 このような状況では、同じにインスタンスに対してポータルをリセットおよび再プロビジョニングできます。 ポータルをリセットする方法については、[ポータルのリセット](admin/reset-portal.md)を参照してください。

#### <a name="request-to-common-data-service-environment-has-timed-out"></a>Common Data Service 環境に対する要求がタイムアウトしました

この問題は通常、Common Data Service 環境に対する API 要求がタイムアウトした場合に発生する一時的な問題です。API 要求が機能し始めると、自動的に軽減されます。 この問題を軽減するには、ポータルの再起動を再度試行することができます。

1. [Power Apps ポータル管理センター](admin/admin-overview.md) を開きます。
2. **ポータル アクション** > **再起動** の順に移動します。

ポータルの再起動が機能せず、この問題が長時間発生している場合は、Microsoft サポートにお問い合わせください。

#### <a name="website-binding-not-found"></a>Web サイトのバインドが見つからない

この問題は、ポータルの Web サイト バインド レコードが基盤となる Common Data Service 環境から削除され、ポータルがバインドを自動的に作成できない場合に発生します。 この問題を解決するには、以下を行います。

1. [ポータル管理アプリ](configure/configure-portal.md)を開きます。
2. **ポータル** > **Web サイト バインド**の順に移動します。
3. ポータルを指しているすべての Web サイト バインド レコードを削除します。 **サイト名** フィールドでは、ポータルの Web サイト バインド レコードを特定できます。
4. すべての Web サイト バインド レコードを削除すると、ポータルを再開します。

上記の手順を完了すると、ポータルが再開され、Web ポータル バインド レコードが自動的に再作成されます。

インスタンスで使用する Web サイト レコードの GUID がポータルの既定のインストール時に作成されたものと異なるときに、Web サイト バインド レコードを自動的に作り直せない場合があります。 この状況では、次の手順を実行します:

1. ポータルに関連するすべての Web サイト バインド レコードを削除します。

2. 次の値で Web サイト バインド レコードを手動で作成します。

      - **名前**: 任意の文字列にできます
      - **Web サイト**: ポータルでレンダリングする Web サイト レコードを選択します
      - **サイト名**: ポータルのホスト名を入力します。たとえば、 先頭に ```https://``` がないポータル URL。 ポータルがカスタム ドメイン名を使用している場合、ここでドメイン名を使用します。
      - 他のフィールドすべては空白のままにします。

3. Web サイト バインド レコードが作り直されたら、Power Apps ポータル管理センターからポータルを再起動します。

#### <a name="an-unexpected-error-has-occurred-while-trying-to-connect-to-your-common-data-service-environment"></a>Common Data Service 環境に接続しようとしているときに、予期しないエラーが発生しました

この状況は、予期しない問題のために起こる場合があります。 この状況を緩和するには、ポータルをリセットするか、または再プロビジョニングできます。 ポータルをリセットする方法については、[ポータルのリセット](admin/reset-portal.md)を参照してください。

ポータルのリセットと再プロビジョニングでこの問題が解決しない場合、Microsoft サポートにお問い合わせください。

### <a name="portal-isnt-displaying-updated-data-from-common-data-service-environment"></a>ポータルに Common Data Service 環境から更新されたデータが表示されません

ポータルに表示されるデータはすべて、ポータル キャッシュからレンダリングされます。 このキャッシュは、Common Data Service 環境のデータが更新されると必ず更新されます。 ただし、このプロセスは非同期であるため、最大 15 分かかる場合があります。 ポータルのメタデータ エンティティで変更が加えられた場合、たとえば、Web ページ、Web ファイル、コンテンツ スニペット、サイトの設定など、キャッシュを手動でクリアするか、Power Apps ポータル管理センターからポータルを再起動することをお勧めします。 キャッシュのクリア方法の説明については、[ポータルのサーバー側キャッシュのクリア](admin/clear-server-side-cache.md)を参照してください。 

ただし、非ポータル メタデータ エンティティに古いデータが長い間表示されている場合、次に示すさまざまな問題が原因の可能性があります:

#### <a name="entities-not-enabled-for-cache-invalidation"></a>エンティティでキャッシュの無効化が有効になっていません

すべてのデータではなく、特定のエンティティの古いデータのみが表示されている場合、その特定のエンティティで Change Tracking メタデータが有効化されていないことが原因の可能性があります。

ポータル チェッカー (セルフサービス診断) ツールを実行した場合、エンティティ リストまたはエンティティ フォームおよび Web フォームのポータルで参照されているすべてのエンティティのオブジェクトの種類コードが一覧表示され、Change Tracking が有効なっていません。 [組織のメタデータの参照](https://docs.microsoft.com/dynamics365/customerengagement/on-premises/developer/browse-your-metadata)で説明している手順を使用してメタデータを参照してください

これらのエンティティのいずれかで古いデータの問題が発生している場合、Power Apps ポータル管理センターを使用して Change Tracking を有効にできます。 UI または Dynamics 365 API。 詳細: [エンティティの変更追跡の有効化](https://docs.microsoft.com/dynamics365/customerengagement/on-premises/developer/use-change-tracking-synchronize-data-external-systems#enable-change-tracking-for-an-entity)

#### <a name="organization-not-enabled-for-change-tracking"></a>組織で変更追跡が有効になっていない

Change Tracking が有効になっている各エンティティとは別に、組織全体でも Change Tracking が有効になっている必要があります。 ポータル プロビジョニング要求が送信されると、組織で変更追跡が有効になります。 ただし、これは、組織が古いデータベースから復元されるかリセットされると無効になることがあります。 この問題を解決するには、以下を行います。

1. [Power Apps ポータル管理センター](admin/admin-overview.md) を開きます。
2. **ポータルの詳細** タブで、**ポータルの状態** リストから **オフ** を選択します。
3. **更新**を選択します。
4. **ポータルの状態** の一覧から **オン** を選択します。
5. **更新** を選択します。 ポータルが再起動し、認証接続できるようになります。

### <a name="performance-best-practices"></a>パフォーマンスのベスト プラクティス

ポータルのパフォーマンスの問題は、さまざまな構成の問題が原因で発生する可能性があります。 すぐに使えるすべてのポータル テンプレートは、ポータル パフォーマンスに影響を与える可能性があるさまざまな読み込み条件や構成でテストされており、以下に、ポータルのパフォーマンス上の問題につながる場合がある一般的なポータル構成のリストを示します。

ポータル チェッカー (セルフサービス診断) ツールでも、ポータル構成を見るとこれらの問題がわかります。

#### <a name="web-page-tracking-enabled"></a>Web ページの追跡が有効

ページ追跡用ポータル Web ページを有効にすると、ポータルでパフォーマンスの問題が生じる場合があります。 この機能は、Dynamics 365 ポータルの 2018 年 1 月リリース以降非推奨です。 詳細: [Dynamics 365 ポータル: 非推奨機能](https://blogs.msdn.microsoft.com/crm/2018/03/20/portal-capabilities-for-dynamics-365-deprecated-features/)

ポータル チェッカー ツールには、ページ追跡が有効になっているすべての Web ページが示されます (ルートとコンテンツ ページの両方)。 これらのページは、次の手順に従って、無効にする必要があります。

1. [ポータル管理アプリ](configure/configure-portal.md)を開きます。
2. 高度な検索に移動します。
3. **追跡の有効化 (非推奨)** フィールドが有効になっているすべての Web ページを検索します (値を [はい] に設定)。
4. すべてのページを一括編集し、このフィールドを **いいえ** に設定します。

ポータル チェッカーの結果に表示される各ページに移動し、代わりに **追跡の有効化 (非推奨)** フィールドの値を **いいえ** に設定することもできます。

Dynamics 365 ポータル ソリューション バージョン 9.x を使用している場合、このフィールドはフォームに表示されず、まずフォームに追加する必要があるかもしれないことを理解することは重要です。 

#### <a name="web-file-tracking-enabled"></a>Web ファイルの追跡が有効

ページ追跡用ポータル Web ファイルを有効にすると、ポータルでパフォーマンスの問題が生じる場合があります。 この機能は、Dynamics 365 ポータルの 2018 年 1 月リリース以降非推奨です。 詳細: [Dynamics 365 ポータル: 非推奨機能](https://blogs.msdn.microsoft.com/crm/2018/03/20/portal-capabilities-for-dynamics-365-deprecated-features/)

ポータル チェッカー ツールには、ページ追跡が有効になっているすべての Web ファイルが示されます。 これらのファイルは、次の手順に従って、無効にする必要があります。

1. [ポータル管理アプリ](configure/configure-portal.md)を開きます。
2. 高度な検索に移動します。
3. **追跡の有効化 (非推奨)** フィールドが有効になっているすべての Web ファイルを検索します (値を [はい] に設定)。
4. すべてのレコードを一括編集し、このフィールドを **いいえ** に設定します。

ポータル チェッカーの結果に表示される各ファイルに移動し、代わりに **追跡の有効化 (非推奨)** フィールドの値を **いいえ** に設定することもできます。 ポータル ソリューション バージョン 9.x を使用している場合、このフィールドはフォームに表示されず、まずフォームに追加する必要があるかもしれないことを理解することは重要です。 

#### <a name="login-tracking-enabled"></a>ログインの追跡が有効

ポータル ログイン追跡を有効にすると、ポータルでパフォーマンスの問題が生じる場合があります。 この機能は、Dynamics 365 ポータルの 2018 年 1 月リリース以降非推奨です。 詳細: [Dynamics 365 ポータル: 非推奨機能](https://blogs.msdn.microsoft.com/crm/2018/03/20/portal-capabilities-for-dynamics-365-deprecated-features/)

ポータル チェッカー ツールは、ログイン追跡がポータルで有効になっているかどうかをチェックし、有効な場合は失敗したチェックが表示されます。 ログイン追跡は、次の手順に従って、無効にする必要があります。

1.  [ポータル管理アプリ](configure/configure-portal.md)を開きます。
2.  **ポータル** > **サイトの設定** の順に移動します。
3.  `Authentication/LoginTrackingEnabled` という名前のサイト設定を検索します。
4.  このサイト設定の値を **False** に変更するか、またはサイトの設定を削除します。
5.  ポータルを再起動します。 

#### <a name="header-output-cache-is-disabled"></a>ヘッダー出力キャッシュが無効

ポータルでヘッダー出力キャッシュを無効にすると、高負荷時にポータルでパフォーマンスの問題が発生する場合があります。 この機能の詳細は、[ポータルでのヘッダーおよびフッター出力キャッシュの有効化](configure/enable-header-footer-output-caching.md)を参照してください

ポータル チェッカー ツールは、ヘッダー出力キャッシュがポータルで無効になっているかどうかをチェックし、無効な場合は失敗したチェックが表示されます。 これを有効にするには、次の手順を行います。

1.  [ポータル管理アプリ](configure/configure-portal.md)を開きます。
2.  **ポータル** > **サイトの設定** の順に移動します。
3.  `Header/OutputCache/Enabled` という名前のサイト設定を検索します。
4.  このサイト設定が使用可能な場合、サイト設定の値を **True** に変更します。 サイト設定を使用できない場合、新しいサイト設定をこの名前で作成し、値を **True** に設定します。
5.  ポータルを再起動します。 

#### <a name="footer-output-cache-is-disabled"></a>フッター出力キャッシュが無効

ポータルでフッター出力キャッシュを無効にすると、高負荷時にポータルでパフォーマンスの問題が発生する場合があります。 この機能の詳細は、[ポータルでのヘッダーおよびフッター出力キャッシュの有効化](configure/enable-header-footer-output-caching.md)を参照してください

ポータル チェッカー ツールは、フッター出力キャッシュがポータルで無効になっているかどうかをチェックし、無効な場合は失敗したチェックが表示されます。 これを有効にするには、次の手順を行います。

1.  [ポータル管理アプリ](configure/configure-portal.md)を開きます。
2.  **ポータル** > **サイトの設定** の順に移動します。
3.  `Footer/OutputCache/Enabled` という名前のサイト設定を検索します。
4.  このサイト設定が使用可能な場合、サイト設定の値を **True** に変更します。 サイト設定を使用できない場合、新しいサイト設定をこの名前で作成し、値を **True** に設定します。
5.  ポータルを再起動します。 

#### <a name="large-number-of-web-file-records"></a>多数の Web ファイル レコード

Web ファイル エンティティは、ポータルで使用する静的ファイルを保存するためにポータルによって使用されます。 このエンティティの主な用途は、CSS、JavaScript、イメージ ファイルなどの Web サイトの静的コンテンツを保存することです。 ただし、このような多くのファイルがあると、ポータルの起動が遅くなる可能性があります。

ポータル チェッカー ツールはこのシナリオをチェックし、ポータルに 500 件以上のアクティブ Web ファイルがあるかどうかを示します。 これらのファイルすべてが、CSS、JavaScript、イメージ ファイルなどの静的コンテンツなどを表している場合は、この問題を軽減するための次のアクションを実行できます。

- これらのファイルを保存するために Azure Blob Storage や CDN などの外部ファイル サーバーを使用し、ページ内または基になるテンプレートの適切なページでこれらのファイルを参照します。

- ファイルを外に移動できない場合、すべてのファイルがホーム ページとともにロードされていないことを確認してください。 そのファイルの親ページがホームに設定されている場合、Web ファイルはホーム ページとともに読み込まれます。 このシナリオを回避するには、次の手順を実行します:

  1. コンテンツと空のテンプレートなしでダミー Web ページを作成します。 このページは、Web ページへの直接パスを作成するために使用できます。 
  2. ホーム ページで必要ではないすべての Web ファイルで、このダミー Web ページに親ページを変更します。 完了すると、Web ファイルへの完全パスは `Portal URL/{dummy_webpage}/{web file}` になります
  3. これを使用するページ テンプレートまたは Web テンプレートの HTML で直接 Web ファイルを参照してください。 これにより、そのページでファイルがオンデマンドで読み込まれます。 

#### <a name="loading-static-resources-cssjs-asynchronously"></a>静的リソース (css/js) の非同期読み込み

ポータルの実装に取り組むときは、ページの HTML を完全に管理することを理解することが重要です。 つまり、Web ページのクライアント側のパフォーマンスが影響を受けないようにするために、標準の Web 開発プラクティスに従う必要があります。

Web ページのパフォーマンス上の問題の最も一般的な原因の 1 つは、ページの読み込み時に多くの静的リソース (css/js) が同期的に読み込まれることです。 大量の css/js ファイルが同期的に読み込まれると、Web ページのクライアント側の処理時間が長くなる場合があります。

ポータルでは、Web ファイルを直接ホーム ページに関連付けると、生成された HTML に依存関係が作成されます。 これは、Web ファイルが常にホーム ページとともにロードされることを意味します。 この Web ファイルがファイル css/js の場合、同期的にロードされ、クライアント側の処理時間が長くなる可能性があります。

これを回避するには、次の手順を実行します:

1. Web ファイルがホーム ページで必要ない場合、その親ページがホーム ページとして設定されていないことを確認し、上で説明したメカニズムを再利用してオンデマンドで読み込みます。
2. JavaScript ファイルを任意のページでオンデマンドで読み込んでいる間、`<async>` または `<defer>` HTML 属性を使用し、ファイルを非同期に読み込みます。
3. CSS ファイルをオンデマンドで読み込んでいる間、まだすべてのブラウザーでプリロードがサポートされているわけではないため、`<preload>` HTML 属性 (https://www.w3.org/TR/preload/) または JavaScript ベースのアプローチを使用できます。

#### <a name="entity-form-lookup-configuration"></a>エンティティ フォームの検索構成 

エンティティ フォームまたは Web フォームでドロップダウン モードとしてレンダリングする検索を有効にすると、ドロップダウンに表示されるレコードの数が 200 を超え、頻繁に変更される場合、パフォーマンスが集中する可能性があります。 このオプションは、国リストや州リストなど、限られた数のレコードを持つ静的検索にのみ使用します。

多数のレコードを含む可能性のある検索でこのオプションを有効にすると、エンティティ フォームが利用可能な Web ページの読み込み時間が遅くなります。 このページが多くのユーザーによって使用され、何度もロードされると、Web サイト全体が遅くなり、Web ページのリソースがこのページのレンダリングに使用されます。 これらの状況では、完全な検索エクスペリエンスを使用するか、AJAX エンドポイント (Web テンプレートを使用して作成) を呼び出すカスタム HTML コントロールを目的のルック アンド フィールに構築する必要があります。

#### <a name="number-of-web-roles"></a>Web ロールの数

Web ロールはポータルで使用され、ロールベースのアクセス制御を可能にします。 通常、許可のさまざまな組み合わせの数も制限されるため、ポータル内の Web ロールの数は制限されます。 ポータルで Web ロールの数が 100 を超えると、パフォーマンスの問題が発生し、ポータルのすべてのページに影響を与える可能性があります。

### <a name="an-active-home-site-marker-isnt-available-for-this-portal"></a>アクティブな [ホーム] サイト マーカーは、このポータルで使用できません

この問題は、ポータル構成で **ホーム** サイト マーカーが使用できない場合に発生します。 この問題を解決するには、以下を行います。

1.  [ポータル管理アプリ](configure/configure-portal.md)を開きます。
2.  左側のウィンドウで、**サイト マーカー** を選択します。
3.  次の値で新しいサイトマーカーを作成します:
    - **名**: ホーム
    - **ウェブサイト** : ポータル ホストの Web サイトを選択します。
    - **ページ** : ポータルのホームページとして設定されている Web ページ レコードを選択します。

### <a name="the-home-site-marker-isnt-pointing-to-any-webpage"></a>[ホーム] サイト マーカーが、どの Web ページもポイントしていません

この問題は、**ホーム** サイト マーカーは利用可能であるが、どの Web ページも参照していない場合に発生します。 この問題を解決するには、以下を行います。

1.  [ポータル管理アプリ](configure/configure-portal.md)を開きます。
2.  左側のウィンドウで、**サイト マーカー** を選択します。
3.  **ホーム**サイト マーカー レコードを検索します。
4.  **ページ** フィールドを更新して、ポータルのアクティブなホームページをポイントします。

### <a name="the-home-site-marker-is-pointing-to-a-deactivated-web-page"></a>ホーム サイト マーカーが非アクティブ化された Web ページをポイントしています。

この問題は、**ホーム** サイト マーカーは使用可能ですが、非アクティブ化された Web ページをポイントしています。 この問題を解決するには、以下を行います。

1.  [ポータル管理アプリ](configure/configure-portal.md)を開きます。
2.  左側のウィンドウで、**サイト マーカー** を選択します。
3.  **ホーム**サイト マーカー レコードを検索します。
4.  **ページ** フィールドを更新して、ポータルのアクティブなホームページをポイントします。

### <a name="the-home-site-marker-isnt-pointing-to-home-page-of-the-portal"></a>[ホーム] サイト マーカーがポータルのホーム ページをポイントしていません

この問題は、**ホーム** サイト マーカーは利用可能であるが、ポータルのホーム ページではない Web ページを参照している場合に発生します。 この問題を解決するには、以下を行います。

1.  [ポータル管理アプリ](configure/configure-portal.md)を開きます。
2.  左側のウィンドウで、**サイト マーカー** を選択します。
3.  **ホーム**サイト マーカー レコードを検索します。
4.  **ページ** フィールドを更新して、ポータルのアクティブなホームページをポイントします。

### <a name="an-active-profile-site-marker-isnt-available-for-this-portal"></a>アクティブな [プロファイル] サイト マーカーは、このポータルで使用できません

この問題は、ポータル構成で **プロファイル** サイト マーカーが使用できない場合に発生します。 この問題を解決するには、以下を行います。

1.  [ポータル管理アプリ](configure/configure-portal.md)を開きます。
2.  左側のウィンドウで、**サイト マーカー** を選択します。
3.  次の値で新しいサイトマーカーを作成します: 
    - **名**: プロファイル
    - **ウェブサイト** : ポータル ホストの Web サイトを選択します。
    - **ページ** : ポータルのプロファイル ページとして設定されている Web ページ レコードを選択します。

### <a name="the-profile-site-marker-isnt-pointing-to-any-webpage"></a>[プロファイル] サイト マーカーが、どの Web ページもポイントしていません

この問題は、**プロファイル** サイト マーカーは利用可能であるが、どの Web ページも参照していない場合に発生します。 この問題を解決するには、以下を行います。

1.  [ポータル管理アプリ](configure/configure-portal.md)を開きます。
2.  左側のウィンドウで、**サイト マーカー** を選択します。
3.  **プロファイル**サイト マーカー レコードを検索します。
4.  **ページ** フィールドを更新して、ポータルのアクティブなプロファイルをポイントします。

### <a name="the-profile-site-marker-is-pointing-to-a-deactivated-web-page"></a>プロファイル サイト マーカーが非アクティブな Web ページをポイントしています。

この問題は、**プロファイル** サイト マーカーが使用可能ですが、非アクティブ化された Web ページをポイントしている場合に発生します。 この問題を解決するには、以下を行います。

1.  [ポータル管理アプリ](configure/configure-portal.md)を開きます。
2.  左側のウィンドウで、**サイト マーカー** を選択します。
3.  **プロファイル**サイト マーカー レコードを検索します。
4.  **ページ** フィールドを更新して、ポータルのアクティブなプロファイルをポイントします。

### <a name="an-active-page-not-found-site-marker-isnt-available-for-this-portal"></a>アクティブな [ページが見つかりません] サイト マーカーは、このポータルで使用できません

この問題は、ポータル構成で **ページが見つかりません** サイト マーカーが使用できない場合に発生します。 この問題を解決するには、以下を行います。

1.  [ポータル管理アプリ](configure/configure-portal.md)を開きます。
2.  左側のウィンドウで、**サイト マーカー** を選択します。
3.  次の値で新しいサイトマーカーを作成します: 
    - **名前**: ページが見つかりません
    - **ウェブサイト** : ポータル ホストの Web サイトを選択します。
    - **ページ** : ポータルの [ページが見つかりません] として設定されている Web ページ レコードを選択します。

### <a name="the-page-not-found-site-marker-isnt-pointing-to-any-webpage"></a>[ページが見つかりません] サイト マーカーが、どの Web ページもポイントしていません

この問題は、**ページが見つかりません** サイト マーカーは利用可能であるが、どの Web ページも参照していない場合に発生します。 この問題を解決するには、以下を行います。

1.  [ポータル管理アプリ](configure/configure-portal.md)を開きます。
2.  左側のウィンドウで、**サイト マーカー** を選択します。
3.  **ページが見つかりません**サイトマーカーレコードを検索します。
4.  **ページ** フィールドを更新して、ポータルの [ページが見つかりません] をポイントします。

### <a name="the-page-not-found-site-marker-is-pointing-to-a-deactivated-web-page"></a>[ページが見つかりません] サイト マーカーが非アクティブかされた Web ページをポイントしています。

この問題は、**ページが見つかりません** サイト マーカーは使用可能ですが、どの非アクティブ化された Web ページもポイントしていない場合に発生します。 この問題を解決するには、以下を行います。

1.  [ポータル管理アプリ](configure/configure-portal.md)を開きます。
2.  左側のウィンドウで、**サイト マーカー** を選択します。
3.  **ページが見つかりません**サイトマーカーレコードを検索します。
4.  **ページ** フィールドを更新して、ポータルの [ページが見つかりません] をポイントします。

### <a name="an-active-access-denied-site-marker-isnt-available-for-this-portal"></a>アクティブな [アクセスが拒否されました] サイト マーカーは、このポータルで使用できません

この問題は、ポータル構成で **アクセスが拒否されました** サイト マーカーが使用できない場合に発生します。 この問題を解決するには、以下を行います。

1.  [ポータル管理アプリ](configure/configure-portal.md)を開きます。
2.  左側のウィンドウで、**サイト マーカー** を選択します。
3.  次の値で新しいサイトマーカーを作成します: 
    - **名前**: アクセスが拒否されました
    - **ウェブサイト** : ポータル ホストの Web サイトを選択します。
    - **ページ** : ポータルの [アクセスが拒否されました] ページとして設定されている Web ページ レコードを選択します。

### <a name="the-access-denied-site-marker-isnt-pointing-to-any-webpage"></a>[アクセスが拒否されました] サイト マーカーが、どの Web ページもポイントしていません

この問題は、**アクセスが拒否されました** サイト マーカーは利用可能であるが、どの Web ページも参照していない場合に発生します。 この問題を解決するには、以下を行います。

1.  [ポータル管理アプリ](configure/configure-portal.md)を開きます。
2.  左側のウィンドウで、**サイト マーカー** を選択します。
3.  **アクセスが拒否されました**サイト マーカー レコードを検索します。
4.  **ページ** フィールドを更新して、ポータルのアクティブなアクセスが拒否されたページをポイントします。

### <a name="the-access-denied-site-marker-is-pointing-to-a-deactivated-web-page"></a>アクセスが拒否されたサイト マーカーが非アクティブ化された Web ページをポイントしています。

この問題は、**アクセスが拒否された**サイトマーカーは使用できますが、非アクティブ化された Web ページをポイントします (ルートまたはコンテンツページは非アクティブ化できます)。 この問題を解決するには、以下を行います。

1.  [ポータル管理アプリ](configure/configure-portal.md)を開きます。
2.  左側のウィンドウで、**サイト マーカー** を選択します。
3.  **アクセスが拒否されました**サイト マーカー レコードを検索します。
4.  **ページ** フィールドを更新して、ポータルのアクティブなアクセスが拒否されたページをポイントします。

### <a name="profile-web-form-isnt-available-for-contact-entity"></a>取引先担当者エンティティに対してプロファイルの Web フォームを使用できません

プロファイル ページは、すべてのプロファイル関連の問題に対してポータルで使用される一般的なページの 1 つです。 このページには、ユーザーがプロファイルを更新するために使用できるフォームが表示されます。 このページで使用されるフォームは、取引先担当者エンティティで使用可能な**プロフィール Web ページ** メインフォームから来ています。 ポータルがプロビジョニングされると、このフォームは Common Data Service 環境で作成されます。 このエラーは、**プロフィール** Webフォームが削除されるか、ポータルで無効になった場合に表示されます。 このフォームは必須で、このフォームの削除または無効にすると、ポータルでランタイムエラーが表示される Web サイト全体が破損する可能性があります。 これは取り返しのつかない状態であり、環境にポータルを再インストールする必要があります。

### <a name="published-state-isnt-available-for-this-website"></a>公開済み状態は、この Web サイトでは使用できません

この問題を修正するには、公開状況エンティティの  **公開済み** が使用可能で、アクティブであることを確認します。

### <a name="published-state-isnt-visible"></a>公開済み状態は表示されていません

この問題を修正するには、公開状況エンティティ **公開済み** の **isVisible** チェックボックスがオンに設定されていることを確認してください

### <a name="list-of-entities-with-search-result-having-invalid-url"></a>検索結果に無効な URL  があるエンティティの一覧

この問題を修正するには、エンティティに適切なセキュリティ アクセス許可が付与されていることを確認してください。

### <a name="list-of-entities-with-cms-security-check-failed"></a>CMS セキュリティ チェックで  が失敗したエンティティの一覧

この問題を修正するには、エンティティに適切な検索ページが設定されていることを確認してください。

### <a name="web-file-isnt-active"></a>Web ファイル がアクティブではありません

この問題を修正するには、Web ファイルがアクティブ状態にあることを確認してください。

### <a name="the-partial-url-of-web-file-is-misconfigured"></a>Web ファイルの一部の URL が正しく構成されていません

この問題を修正するには、部分 URL が、ホームをルート ページとして使用したファイル名になっていることを確認してください。

### <a name="web-file-doesnt-have-a-file-attachment"></a>Web ファイルに添付ファイルがありません

この問題を修正するには、対応する CSS ファイルを Web ファイルのメモ セクションに追加します。

### <a name="file-attachment-doesnt-have-content"></a>添付ファイルが空です

この問題を修正するには、内容の全体を含む CSS ファイルを Web ファイルのメモ セクションに追加します。

### <a name="mime-type-of-file-isnt-textcss"></a>ファイルの MIME の種類が text/css ではありません

この問題を修正するには、CSS ファイルの MIME の種類を上書きするプラグインまたはフローがないことを確認してください。
