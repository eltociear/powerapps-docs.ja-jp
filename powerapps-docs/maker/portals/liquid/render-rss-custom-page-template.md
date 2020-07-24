---
title: ポータルのカスタム ページ テンプレートを使用する RSS フィードをレンダリングする | MicrosoftDocs
description: カスタム ページ テンプレートを作成して RSS フィードをレンダリングする手順。
author: gitanjalisingh33msft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: gisingh
ms.reviewer: tapanm
ms.openlocfilehash: dfa4ce196a080d800d81ad48975aea4ac5eef2c2
ms.sourcegitcommit: c12260f372ad2cc48d3146be570d2088c9ef1d86
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2020
ms.locfileid: "3491362"
---
# <a name="create-a-custom-page-template-to-render-an-rss-feed"></a>RSS フィードを表示するカスタム ページ テンプレートを作成する
この例では、ニュース記事の [RSS フィード](https://en.wikipedia.org/wiki/RSS) を表示するカスタム ページ テンプレートを Liquid および Web テンプレート ページ テンプレートを使用して作成します。 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Web テンプレートを使用したソース コンテンツの保存](store-content-web-templates.md)  

## <a name="step-1-create-a-new-power-apps-view"></a>ステップ 1: Power Apps ビューの新規作成

最初に、フィードのデータを読み込むのに使用する新しい Power Apps ビューを作成します。 この例では、Web ページのビューとし、このエンティティを使用して記事を保存します。 このビューを使用して、結果の並べ替えやフィルタリングの構成、Liquid テンプレートとして使用するエンティティ属性を列として含めることができます。

![ページ テンプレートの編集](../media/edit-page-template.png "ページ テンプレートの編集")  

## <a name="step-2-create-a-web-template-for-rss-feed"></a>ステップ 2: RSS フィードの Web テンプレートを作成する

このステップでは、RSS フィードに対して Web テンプレートを作成します。 このテンプレートは、Web サイトの特定の Web ページに適用されるため、そのページのタイトルおよび概要をフィードのタイトルおよび説明に使用します。 次に entityview タグを使用して、新しく作成されたニュース記事ビューを読み込みます。 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Power Apps Common Data Service エンティティ タグ](portals-entity-tags.md)。 Web テンプレートの **MIME の種類**フィールドも application/rss+xml に設定することに注意してください。 これは、テンプレートが描画された時の応答のコンテンツ タイプを示します。  

![RSS フィードの Web テンプレートの構成](../media/web-template-rss-feed.png "RSS フィードの Web テンプレートの構成")  

### <a name="rss-feed-web-template"></a>RSS フィード (Web テンプレート)

```xml
<?xml version=1.0 encoding=UTF-8 ?>
<rss version=2.0>
  <channel>
    <title>{{ page.title | xml_escape }}</title>
    <description>{{ page.description | strip_html | xml_escape }}</description>
    <link>{{ request.url | xml_escape }}</link>
    {% entityview logical_name:'adx_webpage', name:'News Articles', page_size:20 -%}
      {% for item in entityview.records %}
        <item>
          <title>{{ item.adx_name | xml_escape }}</title>
          <description>{{ item.adx_copy | escape }}</description>
          <link>{{ request.url | base | xml_escape }}{{ item.url | xml_escape }}</link>
          <guid>{{ item.id | xml_escape }}</guid>
          <pubDate>{{ item.createdon | date_to_rfc822 }}</pubDate>
        </item>
      {% endfor -%}
    {% endentityview %}
  </channel>
</rss>
```

## <a name="step-3-create-a-page-template-to-assign-rss-feed-template"></a>ステップ 3: RSS フィード テンプレートを割り当てるページ テンプレートを作成する

ここでは、RSS フィード テンプレートを Web サイトの任意の Web ページに割り当てることができる新しいページ テンプレートを作成します。 フィードのページ応答全体の描画を引き継ぐため、**Web サイト ヘッダーとフッターの使用**を選択解除することに注意してください。

![RSS フィードのページテンプレートの構成](../media/page-template-rss-feed.png "RSS フィードのページテンプレートの構成")  

## <a name="step-4-create-a-web-page-to-host-rss-feed"></a>ステップ 4: RSS フィードをホストする Web ページを作成

最後に、フィードをホストするため、RSS フィード テンプレートを使用して新しい Web ページを作成します。 この新しい Web ページを要求した場合、RSS フィード XML が表示されます。

![RSS フィードの例](../media/rss-feed-example.png "RSS フィードの例")  

この例では、カスタム RSS フィードを作成するために Lipuid、Web テンプレート、Power Apps ビュー、およびポータルのコンテンツ管理機能組み合わせる方法を紹介しました。 これらの機能の組み合わせは、任意のポータル アプリケーションに強力なカスタマイズ機能を追加します。

### <a name="see-also"></a>関連項目

[流動テンプレートと Web テンプレート ページ テンプレートの使用によるカスタム ページ テンプレートの作成](create-custom-template.md)  
[現在のページに関連付けられているエンティティの表示](render-entity-list-current-page.md)  
[Web サイト ヘッダーとプライマリ ナビゲーション バーの表示](render-site-header-primary-navigation.md)  
[ハイブリッド ナビゲーションの使用により、ページ階層のレベルを 3 つまで描画](hybrid-navigation-render-page-hierachy.md)  

