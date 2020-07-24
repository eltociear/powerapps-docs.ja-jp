---
title: ポータル上でのヘッダーおよびフッター出力キャッシュの有効化 | MicrosoftDocs
description: 既存のユーザー用のポータルのヘッダーおよびフッターの出力キャッシュを有効にするための手順。
author: sandhangitmsft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/11/2019
ms.author: sandhan
ms.reviewer: tapanm
ms.openlocfilehash: 42223f9eb7bacd06c849988ca401b5a163699656
ms.sourcegitcommit: c12260f372ad2cc48d3146be570d2088c9ef1d86
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2020
ms.locfileid: "3494382"
---
# <a name="enable-header-and-footer-output-caching-on-a-portal"></a>ポータルでヘッダーおよびフッターの出力キャッシュを有効にします

ポータルのヘッダーおよびフッター Web テンプレートのプロセス パフォーマンスを向上させるため、ヘッダーとフッターの出力キャッシュを有効にします。 ヘッダーおよびフッター Web テンプレートは、ページの読み込まれるたびに解析および表示されます。 ヘッダーおよびフッターの出力キャッシュは、著しくページ処理時間を短縮します。

新しいユーザーの場合は、出力キャッシュが既定で有効になります。 次のサイト設定は利用可能であり、この機能をサポートするのに既定で true に設定されます。
- Header/OutputCache/Enabled: ヘッダーの出力キャッシュを有効にするため、値を true に設定します。
- Footer/OutputCache/Enabled: フッターの出力キャッシュを有効にするため、値を true に設定します。

新しいバージョンのポータルにアップグレードするユーザーに対して、既定で出力キャッシュが無効化されます&mdash;つまり、ヘッダーおよびフッター Web テンプレートが、各ページの読み込みで解析および表示されます。 キャッシュ出力を有効にするには、ヘッダー、フッター、言語ドロップダウン Web テンプレートを更新し、必要なサイト設定を作成する必要があります。

> [!Note]
> サイト設定の作成のみで出力キャッシュを有効にする場合、ヘッダーおよびフッターの一部が適切に表示せず、エラー メッセージが表示されます。

### <a name="enable-header-and-footer-output-caching-for-an-existing-user"></a>既存のユーザーに対するヘッダーおよびフッターの出力キャッシュを有効にします

**手順1: ヘッダー Web テンプレートの更新**

1. [ポータル管理アプリ](configure-portal.md)を開きます。
2. **ポータル** > **Web テンプレート**の順に移動します。
3. ヘッダー Web テンプレートを開きます。
4. **ソース**フィールドで、次の手順を実行します。
    - 次のコードを検索して更新します。
    
        **既存コード**

        ```
        <li>
            <a href={% if homeurl%}/{{ homeurl }}{% endif %}/Account/Login/LogOff?returnUrl={{ request.raw_url_encode | escape }} title={{ snippets[links/logout] | default:resx[Sign_Out] | escape }}>
            {{ snippets[links/logout] | default:resx[Sign_Out] | escape }}
            </a>
        </li>
        </ul>
        </li>
        {% else %}
        <li>
            <a href={% if homeurl%}/{{ homeurl }}{% endif %}/SignIn?returnUrl={{ request.raw_url_encode }}>
            {{ snippets[links/login] | default:resx[Sign_In] }}
            </a>
        </li>
        ```
        
        **更新済みコード**

         ```
        <li>
            <a href={% if homeurl%}/{{ homeurl }}{% endif %}{{ website.sign_out_url_substitution }} title={{ snippets[links/logout] | default:resx[Sign_Out] | escape }}>
            {{ snippets[links/logout] | default:resx[Sign_Out] | escape }}
            </a>
        </li>
        </ul>
        </li>
        {% else %}
        <li>
            <a href={% if homeurl%}/{{ homeurl }}{% endif %}{{ website.sign_in_url_substitution }}>
            {{ snippets[links/login] | default:resx[Sign_In] }}
            </a>
        </li>
        ```
    - 次のコードを検索して更新します。

        **既存コード**
        ```
        {% assign current_page = page.adx_partialurl %}
        {% assign sr_page = sitemarkers[Search].url | remove: '/' %}
        {% assign forum_page = sitemarkers[Forums].url | remove: '/' %}
        {% if current_page == sr_page or current_page == forum_page %}
          <section class=page_section section-landing-{{ current_page }} color-inverse>
            <div class=container>
              <div class=row >
                <div class=col-md-12 text-center>
                  {% if current_page == sr_page %}
                    <h1 class=section-landing-heading>{% editable snippets 'Search/Title' default: resx['Discover_Contoso'] %}</h1>
                    {% include 'Search' %}
                  {% endif %}
                </div>
              </div>
            </div>
          </section>
        {% endif %}
        ```

        **更新済みコード**

        ```
        {% substitution %}
          {% assign current_page = page.id %}
          {% assign sr_page = sitemarkers[Search].id %}
          {% assign forum_page = sitemarkers[Forums].id %}
          {% if current_page == sr_page or current_page == forum_page %}
            {% assign section_class = section-landing-search %}
            {% if current_page == forum_page %}
              {% assign section_class = section-landing-forums %}
            {% endif %}
           <section class=page_section section-landing-{{ current_page }} {{ section_class | h }} color-inverse>
              <div class=container>
                <div class=row >
                  <div class=col-md-12 text-center>
                    {% if current_page == sr_page %}
                      <h1 class=section-landing-heading>{% editable snippets 'Search/Title' default: resx['Discover_Contoso'] %}</h1>
                      {% include 'Search' %}
                    {% endif %}
                  </div>
                </div>
              </div>
            </section>
          {% endif %}
        {% endsubstitution %}
        ```

5. Web テンプレートを保存します。

**手順 2: フッター Web テンプレートの更新**

1. [ポータル管理アプリ](configure-portal.md)を開きます。
2. **ポータル** > **Web テンプレート**の順に移動します。
3. フッター Web テンプレートを開きます。
4. **ソース**フィールドで、次のコードを検索して更新します。
    
    **既存コード**
    
    ```
    <section id=gethelp class=page_section section-diagonal-right color-inverse {% if page %}{% unless page.parent %}home-section{% endunless %}{% endif %} hidden-print>
    ```

    **更新済みコード**

    ```
    <section id=gethelp class=page_section section-diagonal-right color-inverse {% substitution %}{% if page %}{% unless page.parent %}home-section{% endunless %}{% endif %}{% endsubstitution %} hidden-print>
    ```

5. Web テンプレートを保存します。

**手順 3: 言語ドロップダウン Web テンプレートの更新**

1. [ポータル管理アプリ](configure-portal.md)を開きます。
2. **ポータル** > **Web テンプレート**の順に移動します。
3. 言語ドロップダウン Web テンプレートを開きます。
4. **ソース**フィールドで、次のコードを検索して更新します。
    
    **既存コード**

    ```
    <a href=/{{ language.url }} title={{ language.name }} data-code={{ language.code }}>{{ language.name }}</a>
    ```

    **更新済みコード**

    ```
    <a href=/{{ language.url_substitution }} title={{ language.name }} data-code={{ language.code }}>{{ language.name }}</a>
    ```

5. Web テンプレートを保存します。

**手順 4: サイト設定の作成**

次のサイト設定を作成します。

|件名|値|
|----|-----|
|Header/OutputCache/Enabled|正|
|Footer/OutputCache/Enabled|正|
|||
