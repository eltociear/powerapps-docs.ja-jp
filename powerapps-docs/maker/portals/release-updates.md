---
title: Power Apps ポータルのリリースの更新 | MicrosoftDocs
description: Power Apps ポータルののリリース更新について説明します。
author: dileepsinghmicrosoft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/22/2019
ms.author: dileeps
ms.reviewer: tapanm
ms.openlocfilehash: 5009d47f0d1f0402ae47df410e31c79efa67ef32
ms.sourcegitcommit: c12260f372ad2cc48d3146be570d2088c9ef1d86
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2020
ms.locfileid: "3490912"
---
# <a name="release-updates"></a>リリースの更新

このトピックは、最近リリースされた新機能と今後数か月でリリースされる新機能について学ぶことができるリソースを提供します。

## <a name="power-apps-portals-updates"></a>Power Apps ポータルの更新

計画に使用できる今後数か月間にリリースされる新機能については、以下を参照してください。

- [2019 年リリース ウェーブ 2 プラン](https://docs.microsoft.com/power-platform-release-plan/2019wave2/microsoft-powerapps/planned-features#portal-capabilities-for-power-apps)

## <a name="previous-portal-updates"></a>以前のポータルの更新

これが Dynamics 365 ポータルに追加された機能のリストです。 現在までの Dynamics 365 ポータルの更新の詳細については、[Microsoft Dynamics 365 のポータル機能のリリース](https://support.microsoft.com/help/3181191) を参照してください。

> [!NOTE]
> Power Apps ポータルは、以前は Dynamics 365 ポータルとして知られていました。

### <a name="dynamics-365-portals-version-914-for-the-model-driven-apps-in-dynamics-365"></a>Dynamics 365 のモデル駆動型アプリ用 Dynamics 365 ポータル バージョン 9.1.4

Dynamics 365 モデル駆動型アプリ用 Dynamics 365 ポータル バージョン 9.1.4 には、これらの更新プログラムと機能があります。

- **ポータルのメンテナンス モード**: ポータル管理者として、メンテナンス活動中にいつでも顧客へ適切なメッセージを表示するようにポータルを設定できます — たとえば、ソリューション パッケージのアップグレード中に。 詳細: [ポータルのメンテナンス モード](admin/enable-maintenance-mode.md)

- **Power BI Embedded サービスの有効化**: ポータルのカスタマイザーとして、 Power BI Embedded サービスを有効にすることで Power BI の新しいワークスペースに作成されたダッシュボードとレポートを埋め込むことができます。 ダッシュボードとレポートは powerbi Liquid タグを使用してポータルの Web ページに埋め込まれます。 詳細については、 [Power BI 統合の設定](admin/set-up-power-bi-integration.md#enable-power-bi-embedded-service) を参照してください。

- **アイデアのコンテンツ管理の有効化**: ポータル管理者として、ポータルに送信されたアイデアを管理するコンテンツ モデレーション ポリシーを作成できます。

- **OAuth 2.0 暗黙的な許可フロー**: ポータル開発者として OAuth 2.0の暗黙的な許可フローを使用して、クライアント側の API 呼び出しを外部 API にして安全にできます。 詳細: [OAuth 2.0 の暗黙的な許可フロー](oauth-implicit-grant-flow.md)

- **Common Data Service スターター ポータル (プレビュー)**: ポータル管理者として、 Common Data Service 環境に接続してユーザーが対話できるようにポータルを構成可能になりました。 この機能を使用すると、Dynamics 365 (Dynamics 365 Sales、Dynamics 365 サービス、または Dynamics 365 Marketing) のモデル駆動型アプリがあらかじめインストールされていない Common Data Service 環境に、ポータルを接続することができます。

### <a name="dynamics-365-portals-version-911-for-the-model-driven-apps-in-dynamics-365"></a>Dynamics 365 のモデル駆動型アプリ用 Dynamics 365 ポータル バージョン 9.1.1

Dynamics 365 モデル駆動型アプリ用 Dynamics 365 ポータル バージョン 9.1.1 には、これらの更新プログラムと機能があります。

- **ポータル チェッカー**: ポータル チェッカーを使用し、さまざまな構成パラメーターを調べることでポータルで問題を特定し、修正方法に関する提案を示すことができるようになりました。 詳細: [ポータル チェッカー](admin/portal-checker.md)

### <a name="dynamics-365-portals-version-9010-for-the-model-driven-apps-in-dynamics-365"></a>Dynamics 365 のモデル駆動型アプリ用 Dynamics 365 ポータル バージョン 9.0.10

Dynamics 365 モデル駆動型アプリ用 Dynamics 365 ポータル バージョン 9.0.10 には、これらの更新プログラムと機能があります。

- **Dynamics 365 ポータル構成を移行**: 開発からテスト、または運用環境に Dynamics 365 ポータル構成を移行できるようになりました。 移行には、ソースの Dynamics 365 インスタンスからの既存の構成のエクスポートと、ターゲットの Dynamics 365 インスタンスへのインポートが含まれています。 構成データを移行するには、構成移行ツールおよびポータル固有の構成スキーマ ファイルを使用する必要があります。 詳細: [Dynamics 365 ポータル構成の移行](admin/migrate-portal-configuration.md)

- **Power BI のビジュアル化を追加**: ポータル カスタマイザーとして、powerbi Liquid タグを使用して、Web ページの Power BI ビジュアル化 (ダッシュボード、レポート、タイル) を埋め込むことができるようになりました。 詳細については、 [Power BI 統合の設定](admin/set-up-power-bi-integration.md) を参照してください。

- **IP アドレスからポータル アクセスを制限**: ポータル管理者として、ポータルへのアクセスを可能にする IP アドレスの一覧を定義できるようになりました。 ポータルへの要求がユーザーから発生した場合、IP アドレスは許可リストに対して評価されます。 IP アドレスが一覧にない場合、ポータルには HTTP 403 状態コードの Web ページが表示されます。 詳細: [IP アドレスによるポータル アクセスを制限する](admin/ip-address-restrict.md)

- **SharePoint ドキュメントの管理**: Dynamics 365 ポータルでは、ポータルのエンティティ フォームまたは Web フォームに SharePoint からのドキュメントを直接アップロードおよび表示することができるようになりました。 これにより、ユーザーは、ポータルからのドキュメントを表示、ダウンロード、追加、削除することができます。 ポータル ユーザーは各自のドキュメントの編成にフォルダーを作成することもできます。 詳細: [SharePoint ドキュメントの管理](manage-sharepoint-documents.md)

- **新しいポータル コンテンツ エディター (プレビュー)**: このプレビューでは、新しい簡素化されたポータル エディターが Dynamics 365 ポータルのカスタマイズに利用できるようになり、このことは Dynamics 365 ポータルのカスタマイズの学習曲線を減らし、カスタマイズの生産性を向上させるのに役立ちます。

- **ステータスに対する投票を有効にする**: 既定では、ステータスが新規にセットされるときにのみ、アイデアが投票に対して有効にされます。 さまざまなステータスの理由により、アイデアの投票を有効にできるようになりました。 異なるステータスの理由により投票を有効にするには、Ideas/EnableVotingForStatusReasons サイト設定を作成して、その値を必要なステータス値にセットする必要があります。 

### <a name="dynamics-365-portals-version-906-for-the-model-driven-apps-in-dynamics-365"></a>Dynamics 365 のモデル駆動型アプリ用 Dynamics 365 ポータル バージョン 9.0.6

Dynamics 365 モデル駆動型アプリ用 Dynamics 365 ポータル バージョン 9.0.6 により、以下の最新の更新プログラムと機能がもたらされました。

- **Dynamics 365 ポータル アプリ**: Dynamics 365 ポータル アプリには、顧客とのコミュニケーションや共同作業のためのオンライン プラットフォームを構成し管理するための新しいエクスペリエンスが用意されています。 Dynamics 365 ポータルのバージョン 9.0 およびそれ以降をインストールすると、統一インターフェイス フレームワーク上に、Dynamics 365 ポータル アプリがすぐに使える状態で作成されます。

- **ポータルのリセット**: 他の地理的場所または他のテナントに移動し、これ以上ポータルを使用しない場合は、ポータルをリセットすることができるようになりました。 ポータルをリセットすると、ポータルのホストされたリソースは削除され、ポータルの URL にアクセスできなくなります。 詳細: [ポータルのリセット](admin/reset-portal.md)

- **ポータルの基本 URL を変更する**: プロビジョニング後にポータルの基本 URL を変更することができるようになりました。 たとえば、ポータルのプロビジョニング中に contosocommunity.microsoftcrmportals.com を基本 URL として選択する場合、必要に応じて後から contosocommunityportal.microsoftcrmportals.com に変更することができます。 詳細: [基本 URL の変更](admin/change-base-url.md)


### <a name="dynamics-365-portals-version-841-for-the-model-driven-apps-in-dynamics-365"></a>Dynamics 365 のモデル駆動型アプリ用 Dynamics 365 ポータル バージョン 8.4.1

Dynamics 365 のモデル駆動型アプリの Dynamics 365 ポータル バージョン 8.4.1 は、パフォーマンス向上だけでなく、次の機能と共に一連のバグ修正を取り入れます。

- **サポート情報記事および Web ファイルの添付ファイル コンテンツ内を検索**: 関連する検索結果の可能性を高めるため、サポート情報記事および Web ファイルの添付ファイル コンテンツが検索可能になりました。 詳細: [添付ファイルのコンテンツ内の検索](configure/search-file-attachment.md)
- **ユーザー補助**: 簡単に使えるポータル (コミュニティ ポータル、パートナー ポータル、顧客ポータル、従業員セルフサービス ポータル) にアクセスできるようになりました。 ただし、カスタマイザーはカスタマイズまたは変更後もポータルがアクセス可能であることを確認する必要があります。


### <a name="dynamics-365-portals-version-84-for-the-model-driven-apps-in-dynamics-365"></a>Dynamics 365 のモデル駆動型アプリ用 Dynamics 365 ポータル バージョン 8.4

Dynamics 365 のモデル駆動型アプリの Dynamics 365 ポータル バージョン 8.4 は、パフォーマンス向上だけでなく、次の機能と共に一連のバグ修正を取り入れます。

- **ポータル エラー ログへのアクセス**: ポータル開発者として、ポータルのすべての問題に関する詳細なエラー ログにアクセスできるようになりました。 これにより、ポータルを開発中に問題をデバッグすることができます。 ポータルがライブになると、所有する Azure Blob Storage アカウントにすべてのアプリケーション エラーを送信するように、ポータルを構成することができます。 これにより、顧客によって報告された問題をデバッグできます。 詳細: [ポータル エラー ログへのアクセス](admin/view-portal-error-log.md)
- **ポータル認証キーの更新**: ポータルは Azure Active Directory アプリケーションを使用して Common Data Service 環境と接続します。 これを行うには、 Azure Active Directory アプリケーションに接続される認証キーが必要です。 このキーは、ポータルをプロビジョニングするときに追加され、2 年ごとに更新する必要があります。 このバージョンのポータルでは、管理者がキーの有効期限を通知され、 Power Apps ポータル管理センターからこのキーを更新できるようになりました。 詳細: [ポータル認証キーの更新](admin/manage-auth-key.md)
- **ポータルに一般的なデータ保護規則を実装**: ポータル管理者として、GDPR 基準を満たすようにポータルを設定することができるようになりました。 また、ポータルを使用するポータル ユーザーが同意する必要がある、特定の利用条件も規定できます。 また、ポータルが未成年者ユーザーによってアクセスされる場合はユーザーがポータルにアクセスするには保護者の承諾が必要である、などのチェックもセットアップできます。 GDPR を実装すると、個人データの使用に関するポータル ユーザーからの同意を取得し、未成年ユーザーを識別し、未成年者の親の同意を取得することができます。 詳細: [ポータルでの GDPR の実装](configure/implement-gdpr.md)

### <a name="dynamics-365-portals-version-83-for-the-model-driven-apps-in-dynamics-365"></a>Dynamics 365 のモデル駆動型アプリ用 Dynamics 365 ポータル バージョン 8.3

Dynamics 365 モデル駆動型アプリ用 Dynamics 365 ポータル バージョン 8.3 には、新しい更新プログラムと機能があります。

- **サポート情報記事の添付ファイルを含める機能**: サポート情報記事とともに添付メモを表示することができます。 この機能を有効にするには、サイト設定 KnowledgeManagement/DisplayNotes を作成し、値を **true** に設定します。 ポータル ユーザーは、これらの添付ファイルを検索することもできます。 詳細: ナレッジ記事の添付ファイルの表示

  > [!Note]
  > 添付ファイルの検索は、メモの説明および添付ファイル名にのみ実行可能です。 添付されたファイルの内容は検索不可能です。
  
- **ポータルにエンティティを追加するための管理ウィザード**: この機能により、ポータルに簡単にデータを公開するための新しい管理ウィザードが導入されます。 ウィザードを使用して作成されたエンティティは組織からデータを取得し、選択されたセキュリティおよびアクセス許可モデルに基づいて、ポータルの顧客がそのサブセットを使用できるようにします。

- **メタデータ翻訳のインポート**: この機能を活用し、ポータルのインストール後に新にアクティブ化された言語のメタデータ翻訳をインポートします。 詳細: [メタデータ翻訳のインポート](admin/import-metadata-translation.md)

- **ポータルのソース コードの可用性**: 開発者向け MIT ライセンス下でダウンロードできるよう、Dynamics 365 ポータル コードの 1 回限りのリリースが Microsoft ダウンロード センターにリリースされています。 この機能により、ポータルを Dynamics 365 On-premises または Online 環境に展開することができ、開発者は固有のビジネス ニーズに合わせてコードをカスタマイズすることができます。

  > [!NOTE]
  > ソース コードは、作業サンプルとして必要に応じて提供されます。 直接サポートはどのコード変更にも提供されません。

- **シングル サインオン (SSO) 構成の向上および Azure Active Directory B2C (Azure AD B2C) のサポート**: 顧客ベースのログインが必要な顧客ポータル向けに、この機能は以下の機能をサポートするようになりました。
  - SSO を使用するようにポータル認証を設定します。 
  - 顧客認証のための Azure AD B2C のサポート
  - Azure のポータル セキュリティの管理

  詳細: [ポータルの Azure AD B2C プロバイダー設定](configure/azure-ad-b2c.md)

- **ポータル フォームのタイムゾーン &ndash; 非依存の日付の形式をサポート**: この機能により、ポータルの日付と時刻フィールドの**日付のみ**および**タイム ゾーン非依存**動作へのサポートが追加されます。 詳細: [日時フィールドの動作と形式](configure/behavior-format-date-time-field.md)

- **非グローバル管理者のポータル プロビジョニングを許可**: ポータル用に選択された CRM 組織のシステム管理者ロールに割り当てられているユーザーは、ポータルをプロビジョニングすることができるようになりました。 以下のロールのいずれかを持っている場合、既存ポータルを管理できるようにもなりました。
  - Dynamics 365 サービス管理者
  - ポータル用に選択された CRM 組織のシステム管理者

- **ポータル用カスタム ドメイン名を保存**: この機能は Web サイト レコードにポータルのプライマリ ドメイン名を保存します。 以降ドメイン名が変更された場合は、最新のプライマリ ドメイン名が保存されます。

- **ポータルの Cookie の追跡**: ユーザーがポータルに移動するたびに、永続的 Cookie Dynamics365PortalAnalytics が設定されます。 この Cookie には、90 日の有効期限があります。 この Cookie は、ユーザーの個人データを保存せず、Microsoft がポータル サービスに関する分析収集を行うために使用されます。 Microsoft オンライン サービスのプライバシーに関する声明については、[こちら](https://go.microsoft.com/fwlink/p/?linkid=856855) をお読みください。

- **ポータルのヘッダーおよびフッターのパフォーマンスの向上**: 2 つの新しいサイト設定 : Header/OutputCache/Enabled および Footer/OutputCache/Enabled が追加され、これらの設定が true に設定されると、ヘッダーとフッターの出力キャッシュが有効化されます。 新しいユーザーの場合、これらのサイト設定は既定で true に設定され、これによりヘッダーとフッターの出力キャッシュが有効化されます。 Dynamics 365 ポータルの新しいバージョンにアップグレードする既存のユーザーの場合、出力キャッシュは既定で無効になっています。 ヘッダーおよびフッター Web テンプレートは、ページの読み込みごとに解析および表示されることを意味します。 キャッシュ出力を有効にするには、適切な Web テンプレートを更新し、必要なサイト設定を作成する必要があります。 詳細: [ヘッダーおよびフッター出力キャッシュの有効化](configure/enable-header-footer-output-caching.md)

### <a name="december-2016-updates"></a>2016 年 12 月の更新

2016 年 12 月の更新により、多くの新機能が Dynamics 365 のポータル機能にもたらされました。 これらの更新により、企業、パートナー、および顧客間でのより良い対話が可能になり、ポータルをより迅速かつ簡単にナビゲートできるようになりました。 主な更新の一部は次のとおりです:

- **複数言語のサポート:** 1 つのポータルを使用して複数の地域の顧客をサポートします。 詳細: [複数言語のサポートの有効化](configure/enable-multiple-language-support.md)
- **東アジア言語のサポート:** 日本語、中国語、韓国語などのマルチバイト文字がサポートされるようになりました。
- **ファセット検索:** 新しいフィルターは、コンテンツの可視性をより詳細に制御しながら、顧客が探しているコンテンツをどれぐらい迅速に見つけ出すかを向上させます。 詳細: [ファセット検索](configure/improve-portal-search-faceted-search.md)
- **製品のフィルタリング:** ポータル ユーザーは、情報の過負荷を避けるために、製品所有権に関連するアクセス サポート情報記事を調整することができます。
- **コンテンツ アクセス レベル:** 適切な記事を適切な顧客に提供し、および無関係な記事が浮上することを禁止できるよう、サポート情報記事へのアクセスを制御するために使用されるポータル取引先担当者、取引先企業、または Web ロールに関連付けられた新しいレベルの所有権。 詳細: [コンテンツ アクセス レベル](https://docs.microsoft.com/dynamics365/portals/manage-knowledge-articles-content-levels)
- **サポート情報記事レポートの強化:** ポータルは、ポータルでサポート情報記事が使用された場所を追跡します。
- **Project Service Automation 統合:** パートナーと顧客に対するプロジェクト ライフサイクルの全ステージにわたってアクティブなプロジェクトおよび終了したプロジェクトに対するアクセスと可視性を提供します。 チーム メンバー、レビュー担当者、および顧客は、このソリューションを使用して、ポータル上でプロジェクトの状態、見積もり、受注のフォーラム、および予約可能なリソースを表示できます。 詳細: [Project Service Automation を統合する](https://docs.microsoft.com/dynamics365/portals/integrate-project-service-automation)
- **Field Service 統合:** このソリューションを使用して、アクティブな契約、資産、作業指示書、請求書、およびサポート案件に関する情報をポータル上のパートナーおよび顧客に公開します。 詳細: [Field Service を統合する](https://docs.microsoft.com/dynamics365/portals/integrate-field-service)
- **パートナーのオンボーディング:** より良い顧客の販売とサービス エクスペリエンスのために新しいパートナーを募集します。 潜在的なパートナーは、ポータルを通じてパートナーの状態を申請することができます。

### <a name="privacy-notice"></a>プライバシーに関する声明

[!INCLUDE[cc-privacy-crm-portals-data-exposed](../../includes/cc-privacy-crm-portals-data-exposed.md)]

追加の [!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] サービス提供の詳細については、「[[!INCLUDE[cc_privacy_note_azure_trust_center](../../includes/cc_privacy_note_azure_trust_center.md)]](https://azure.microsoft.com/support/trust-center/)」を参照してください。  
