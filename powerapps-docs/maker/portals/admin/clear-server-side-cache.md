---
title: ポータルのサーバー側キャッシュをクリアする | MicrosoftDocs
description: ポータルで強制的にキャッシュを更新させる指示。
author: neerajnandwana-msft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 04/23/2020
ms.author: nenandw
ms.reviewer: tapanm
ms.openlocfilehash: 88a58a329be67bdc223e9087033744088cce8025
ms.sourcegitcommit: 2fd873a1ea17f419f6194714efffa47a9bd00c2e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "3506777"
---
# <a name="clear-the-server-side-cache-for-a-portal"></a>ポータルのサーバー側キャッシュをクリアにします

ポータル管理者として、Common Data Service からの更新されたデータがポータルにすぐに反映されるよう、ポータル全体のサーバー側キャッシュをクリアできます。 Common Data Service からの更新は非同期モードでポータルに伝えられるので、Common Data Service で更新された時刻のデータおよびポータルで表示される更新されたデータの時刻との間に遅れがあるかもしれません。 この遅延&mdash;を排除するには、例えば、ポータルの構成&mdash;に影響を与える場合、ポータルがキャッシュを迅速に更新するよう強制することができます。

> [!NOTE]
> キャッシュ リフレッシュの SLA (Common Data Service とポータル間のデータ転送) は 15 分です。

## <a name="steps-to-clear-portal-server-side-cache"></a>サーバー側のキャッシュをクリアにする手順

> [!IMPORTANT]
> ポータルのサーバー側キャッシュをクリアすることにより、Common Data Service から再度読み込みをしている間、一時的にポータルのパフォーマンスが低下します。

サーバー側のキャッシュをクリアする:

1. ポータルに管理者としてログインします。

1. 次のような URL に移動ます: `<portal_path>/_services/about`。

1. **キャッシュのクリア** を選択します。

サーバー側のキャッシュが削除され、データが Common Data Serviceから再度読み込まれます。 

![ポータルのキャッシュをクリアする](media/clear-server-side-cache/clear-portal-cache.png)

## <a name="configuration-entity-caching-portals-with-capacity-based-licenses"></a>キャパシティ ベースのライセンスを備えた構成エンティティ キャッシュ ポータル

[キャパシティ ベース](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#portals) ポータルには、より多くのオプションがあります `<portal_path>/_services/about`:

![キャパシティ ベースのライセンスでポータル キャッシュをクリアにする](media/clear-server-side-cache/clear-config-capacity-license.png)

Power Apps ポータルとポータル アドオンの違いについては、[Power Apps ポータル FAQ](../faq.md#what-is-the-difference-between-power-apps-portals-dynamics-365-portals-and-add-on-portals) を参照してください。

ポータル メタデータは、*構成エンティティ*呼ばれるエンティティに保管されています。 *統一インターフェイス アプリケーション*を使用して構成エンティティを変更する場合、使用しているポータルに変更を反映させるため、**構成をクリア**を**必ず**選択し、構成キャッシュをクリアします。  

### <a name="list-of-configuration-entities-refreshed-when-you-clear-config"></a>構成をクリアすると更新される構成エンティティの一覧

以下の*構成エンティティ*からのデータ更新が含まれるポタータルのサーバー側構成キャッシュをクリア:

| 構成エンティティ:| | |
|-------------------------------------------|---------------------------|--------------------------------------|
| adx_contentaccesslevel                    | adx_redirect              | adx_webpage_tag                      |
| adx_contentsnippet                        | adx_setting               | adx_webpageaccesscontrolrule         |
| adx_entityform                            | adx_shortcut              | adx_webpageaccesscontrolrule_webrole |
| adx_entityformmetadata                    | adx_sitemarker            | adx_webpagehistory                   |
| adx_entitylist                            | adx_sitesetting           | adx_webpagelog                       |
| adx_entitypermission_webrole              | adx_webfile               | adx_webrole_systemuser               |
| adx_externalidentity                      | adx_webfilelog            | adx_website                          |
| adx_pagealert                             | adx_webform               | adx_website_list                     |
| adx_pagenotification                      | adx_webformmetadata       | adx_website_sponsor                  |
| adx_pagetag                               | adx_webformsession        | adx_websiteaccess                    |
| adx_pagetag_webpage                       | adx_webformstep           | adx_websiteaccess_webrole            |
| adx_pagetemplate                          | adx_weblink               | adx_websitebinding                   |
| adx_portallanguage                        | adx_weblinkset            | adx_websitelanguage                  |
| adx_publishingstate                       | adx_webnotificationentity | adx_webtemplate                      |
| adx_publishingstatetransitionrule         | adx_webnotificationurl    | adx_urlhistory                       |
| adx_publishingstatetransitionrule_webrole | adx_webpage               | adx_entitypermission                 |
