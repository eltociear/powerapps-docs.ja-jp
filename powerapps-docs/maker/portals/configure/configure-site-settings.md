---
title: ポータル用サイト設定の構成 | MicrosoftDocs
description: ポータルのサイト設定と組織内のすべてのポータルのグローバル設定を追加および構成する手順。
author: sandhangitmsft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: sandhan
ms.reviewer: tapanm
ms.openlocfilehash: f2bb801f2766c930fb48b2bb1df24a61a5862a39
ms.sourcegitcommit: c12260f372ad2cc48d3146be570d2088c9ef1d86
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2020
ms.locfileid: "3489817"
---
# <a name="configure-site-settings-for-portals"></a>ポータルのサイト設定の構成

サイト設定は、設定可能な名前付きの値で、ポータルの動作や外観を変更するためにウェブサイト コードで使用されます。 通常、開発者がウェブサイト コードを作成すると、さまざまなコンポーネントのサイト設定が参照され、コードを変更したり、サイト再コンパイルしたり、再配置したりすることなく、エンドユーザーが設定値を変更してウェブサイトを変更できるようになります。

Power Apps ポータルのインストールで提供されるサンプル ポータルには、背景スタイル、テキストの色、レイアウトの幅など、サイト内の多くのビジュアル要素を変更するために使用されるさまざまなスタイルの設定可能なサイト設定がいくつか含まれています。
次に示すサイトの設定の種類を管理することができます。

- **グローバル ポータルの設定**: これらの設定は、追加される Common Data Service 環境に関連付けられているすべてのポータルに適用されます。
- **ポータル サイトの設定**: これらの設定は、追加される Common Data Service 環境に関連付けられた特定のポータル (ウェブサイト レコード) に適用されます。


## <a name="manage-portal-site-settings"></a>ポータル サイト設定の管理

1. [ポータルの構成](../manage-existing-portals.md#settings) に移動し、 **サイトの設定** を選択します。

2. 新しい設定を作成する場合、**新規**を選択します。

3. 既存設定を編集する場合は、グリッドにリストされた**サイト設定**を選択します。

4. 用意されているフィールドの値を入力してください: 

    - **名前**: 適切な設定を取得するための Web サイト コードによって参照されるラベルです。 設定を取得するコードは、一致する名前で見つかった最初のレコードを取得するため、関連付けられたウェブサイトでは名前が固有である必要があります。
    
    - **Web サイト**: 関連する Web サイトです。 
    
    - **値**: 設定
    
    - **説明**: この設定の目的または特別な指示です。

5. **保存して閉じる**を選択します。

> [!NOTE] 
> Bing マップ 統合は、ドイツの主権クラウドではサポートされません。 この環境で Bingmaps/credentials の設定を作成しようとすると、エラー メッセージが表示されます。

## <a name="portal-site-settings"></a>ポータル サイトの設定

|Name|Value|説明|
|----|-----|-----------|
|Authentication/Registration/RequiresConfirmation|偽 |ブール値 true は E メールによる確認を有効にし、オープン登録を無効にします。 既定: False |
|Authentication/Registration/RequiresInvitation|偽 |ブール値 true は招待コード機能を有効にし、オープン登録を無効にします。 既定: False |
|conference-name|ポータル会議|特定のポータルの会議を表す adx_conference のレコード名。|
|HelpDesk/CaseEntitlementEnabled|真|ヘルプ デスクのサポート案件の権利が有効かを示すブール値。 既定: false|
|HelpDesk/Deflection/DefaultSelectedProductName| |producttypecode が 100000001 に等しい製品が複数ある場合は、ヘルプ デスクのサポート案件の転送に表示されるドロップダウンで、既定で選択された製品の製品レコード名。|
|Profile/ForceSignUp|偽|ブール値を "True" に設定すると、Web サイトのコンテンツにアクセス許可される前に、ユーザーはプロフィール情報を更新する必要があります。 既定: False|
|Profile/ShowMarketingOptionsPanel|真|プロフィールのマーケティング広告の設定を指定する、フィールド一覧を表示するパネルを表示するか示すブール値。 既定: False|
|検索/有効|真|検索が有効かを示すブール値。|
|検索/フィルター|コンテンツ: adx_webpage、Events: adx_event、adx_eventschedule;<br>ブログ: adx_blog、adx_blogpost、adx_blogpostcomment;<br>フォーラム: adx_communityforum、adx_communityforumthread、adx_communityforumpost;<br>アイデア: adx_ideaforum、adx_idea、adx_ideacomment;<br>問題: adx_issueforum、adx_issue、adx_issuecomment; ヘルプ デスク: サポート案件|検索論理名フィルター オプションのコレクション。 ここで値を定義すると、サイト全体検索にドロップダウン フィルター オプションを追加します。 この値は、コロンと区切られた名前と値を含む、名前/値のペア、およびセミコロンで区切られたペアの形式であるべきです。<br>例: 「Forums:adx_communityforum,adx_communityforumthread,adx_communityforumpost;Blogs:adx_blog,adx_blogpost,adx_blogpostcomment」。|
|Search/IndexQueryName|ポータル検索|ポータル検索クエリで使用されるシステム ビューの名前。 既定: ポータル検索|
|検索/クエリ|+(@Query) _title:(@Query) _logicalname:adx_webpage~0.9^0.2<br> -_logicalname:adx_webfile~0.9 adx_partialurl:(@Query)<br> _logicalname:adx_blogpost~0.9^0.1 -_logicalname:adx_communityforumthread~0.9|サイト検索のクエリを上書きして、追加の重みとフィルターを適用します。 @Query はユーザーが入力したクエリ テキストです。 Lucene クエリ構文の参照: [https://lucene.apache.org/core/old_versioned_docs/versions/2_9_1/queryparsersyntax.html](https://lucene.apache.org/core/old_versioned_docs/versions/2_9_1/queryparsersyntax.html)| 
|取得/ステミング機能|英語|ポータル検索のステミング アルゴリズムが使用する言語。 既定: 英語|
|CustomerSupport/DisplayAllUserActivitiesOnTimeline|偽| |
|Authentication/[Protocol]/[Provider]/AllowContactMappingWithEmail| |電子メールに基づいて取引先担当者レコードへの自動関連付けを許可します。 詳しくは、[ここ](azure-ad-b2c.md#allow-auto-association-to-a-contact-record-based-on-email)をクリックしてください。|
|||

さまざまなポータル機能に関連するサイト設定については、以下を参照してください:

- [認証 ID](set-authentication-identity.md)
- [Azure AD B2C プロバイダー](azure-ad-b2c.md)
- [OAuth 2.0](configure-oauth2-settings.md)
- [Open ID 接続](configure-openid-settings.md)
- [WS-Federation](configure-ws-federation-settings.md)
- [SAML 2.0](configure-saml2-settings.md)
- [アイデンティティ プロバイダを Azure AD B2Cへ移行する](migrate-identity-providers.md)
- [添付ファイルのコンテンツ内の検索](search-file-attachment.md)
- [日時フィールドの動作および形式](behavior-format-date-time-field.md)
- [位置情報の追加](add-geolocation.md)
- [一般データ保護規則の実装](https://docs.microsoft.com/dynamics365/customer-engagement/portals/implement-gdpr)
- [ヘッダーとフッターの出力キャッシュを有効にする](https://docs.microsoft.com/dynamics365/customer-engagement/portals/enable-header-footer-output-caching)

## <a name="manage-global-portal-settings"></a>グローバル ポータル設定の管理

1. [ポータルの構成](../manage-existing-portals.md#settings) に移動し、 **サイトの設定** を選択します。

2. **設定** &gt; **設定**の順に移動します。

3. 新しい設定を作成する場合、**新規**を選択します。

4. 既存設定を編集する場合は、グリッドにリストされた**サイト設定**を選択します。

5. 用意されているフィールドの値を入力してください: 

    - **名前**: 適切な設定を取得するためのコードによって参照される一意の名前です。

    - **値**: 設定

    - **説明**: この設定の目的または特別な指示です。

6. **保存して閉じる**を選択します。

> [!NOTE] 
> Bing マップ 統合は、ドイツの主権クラウドではサポートされません。 この環境で BinMap/Key または Adxstudio/ProductivityPack/BingMap/Key 設定を作成しようとすると、エラー メッセージが表示されます。


