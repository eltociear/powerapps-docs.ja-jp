---
title: ポータルの添付ファイルのコンテンツ内の検索 | MicrosoftDocs
description: ポータル内の添付ファイルのコンテンツ内を検索するよう、ポータルを構成する方法を説明します。
author: sandhangitmsft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: sandhan
ms.reviewer: tapanm
ms.openlocfilehash: 9c1c6bfd14736efac3b8c4fcc03cf455b51225dc
ms.sourcegitcommit: c12260f372ad2cc48d3146be570d2088c9ef1d86
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2020
ms.locfileid: "3494022"
---
# <a name="search-within-file-attachment-content"></a>添付ファイルのコンテンツ内の検索

サポート情報記事にダウンロード可能なファイルを含めるために、メモ添付ファイルを使用することができます。 また、Web ファイルを使用してダウンロード可能なコンテンツを持つ FAQ ページを作成することができます。

ポータル ユーザーが添付ファイルのサポート情報記事のコンテンツ内で検索できるようにポータルを構成できます。 これはユーザーが探している情報を検索するために役立ちます。

サポート情報記事では、定義された接頭語があるすべてのメモ添付ファイルはインデックス付きです。 Web ファイルでは、最新のメモ添付ファイルはインデックス付きです。

添付ファイルにインデックスを作成するには、次のサイト設定を作成して、その値を **true** にセットする必要があります。

|サイト設定|説明|
|------------|-----------|
|Search/IndexNotesAttachments|サポート情報記事および Web ファイルのメモ添付ファイルの内容をインデックス付きにする必要があるかどうかを示します。 既定では、**False** に設定されています。|
|KnowledgeManagement/DisplayNotes|サポート情報記事の添付ファイルにインデックスを作成するかどうかを示します。 既定では、**False** に設定されています。|
|||

> [!NOTE]
> サポート情報記事に添付されているファイルのみ検索できます。 Web ファイルに添付されているファイルは検索できません。

用語を検索するとき、検索結果には添付ファイルも含まれます。 検索語がメモ添付ファイルと一致する場合、対応するサポート情報記事へのリンクも表示されます。 ダウンロード可能な添付ファイルを表示するには、左ウィンドウの**レコードの種類**で**ダウンロード**を選択します。 **ダウンロード** ラベルを変更するには、検索/ファセット/ダウンロードのコンテンツ スニペットを編集します。 既定では、値は**ダウンロード**にセットされています。

![添付ファイルのダウンロード](../media/search-attachment-content.png "添付ファイルのダウンロード") 

> [!NOTE]
> - この機能を使用するには、[関連性検索を有効にする](https://docs.microsoft.com/dynamics365/customer-engagement/admin/configure-relevance-search-organization) 必要があります。 詳細: [関連性検索](https://docs.microsoft.com/dynamics365/customer-engagement/basics/relevance-search-results)
 
## <a name="update-portal-configurations"></a>ポータル構成の更新

2018 年4 月以前のポータルを持ち、ポータルを最新バージョンにアップグレード済みの場合、新しいポータル インストールと同じユーザー エクスペリエンスを持つには以下の構成を使用する必要があります。

**コンテンツ スニペット**

注釈および Web ファイル ダウンロードの検索結果に表示されるラベルを修正するには、コンテンツ スニペット Search/Facet/Downloads を作成してから、必要に応じてその値を設定します。 既定値は**Downloads**です。

**Web ファイル**

Web ファイルに関連付けられる添付ファイルの内容にインデックスを作成できるようになりました。 CSS ファイルおよび画像ファイル (たとえば、bootstrap.min.css、theme.css、および homehero.jpg) の既存の Web ファイルを、検索から除外されるように更新することができます。 

1. [ポータル管理アプリ](configure-portal.md)を開き **ポータル** > **Web ファイル**に移動します。
2. 検索から除外するファイルを開きます。
3. **その他**の、**検索から除外**フィールドで**はい**を選択します。

**Web テンプレート**

ファセット検索 - 結果テンプレートの Web テンプレートは、サポート情報記事に関連付けられたファイルを、関連記事リンクを持つ主要な検索結果項目として表示するように変更されます。 ファセット検索 - 結果テンプレートの Web テンプレートを以下のソースに対して更新する必要があります。

```
{% assign openTag = '{{' %}
{% assign closingTag = '}}' %}
{%raw%}
  <script id=search-view-results type=text/x-handlebars-template>
   {{#if items}}
    <div class=page-header>
     <h3>{%endraw%}{{openTag}} stringFormat {{ resx.Search_Results_Format_String }} firstResultNumber lastResultNumber itemCount {{closingTag}}{%raw%}
      <em class=querytext>{{{query}}}</em>
      {{#if isResetVisible}}
       <a class="btn btn-default btn-sm facet-clear-all" role="button" title="{%endraw%}{{ snippets['Search/Facet/ClearConstraints'] | default: res['Search_Filter_Clear_All'] }}{%raw%}" tabIndex="0">{%endraw%}{{ snippets['Search/Facet/ClearConstraints'] | default: res['Search_Filter_Clear_All'] }}{%raw%}</a>
      {{/if}}
     </h3>
    </div>
   <ul>
    {{#each items}}
     <li>
      <h3><a title={{title}} href={{url}}>{{#if parent}}<span class=glyphicon glyphicon-file pull-left text-muted aria-hidden=true></span>{{/if}}{{title}}</a></h3>
      <p class=fragment>{{{fragment}}}</p>
      {{#if parent}}
       <p class=small related-article>{%endraw%}{{ resx.Related_Article }}{%raw%}: <a title={{parent.title}} href={{parent.absoluteUrl}}>{{parent.title}}</a></p>
      {{/if}}
      <ul class=note-group small list-unstyled>
       {{#if relatedNotes}}
        {{#each relatedNotes}}
         <li class=note-item>
         {{#if isImage}}
          <a target=_blank title={{title}} href={{absoluteUrl}}><span class=glyphicon glyphicon-file aria-hidden=true></span>&nbsp;{{title}}</a>
         {{else}}
          <a title={{title}} href={{absoluteUrl}}><span class=glyphicon glyphicon-file aria-hidden=true></span>&nbsp;{{title}}</a>
         {{/if}}
         <p class=fragment text-muted>{{{fragment}}}</p>
         </li>
        {{/each}}
        {{/if}}
      </ul>
     </li>
    {{/each}}
   </ul>
   {{else}}
    <h2>{%endraw%}{{ resx.Search_No_Results_Found }}{%raw%}<em class=querytext>{{{query}}}</em>
     {{#if isResetVisible}}
      <a class="btn btn-default btn-sm facet-clear-all" role="button" title="{%endraw%}{{ snippets['Search/Facet/ClearConstraints'] | default: res['Search_Filter_Clear_All'] }}{%raw%}" tabIndex="0">{%endraw%}{{ snippets['Search/Facet/ClearConstraints'] | default: res['Search_Filter_Clear_All'] }}{%raw%}</a>
     {{/if}}
    </h2>
   {{/if}}
  </script>
{%endraw%}
```

**サイト設定**

`\_logicalname:annotation~0.9^0.25` 値を Search/Query サイト設定に追加する必要があります。 追加後、その値は次のようになります。
```
+(@Query) \_title:(@Query) \_logicalname:knowledgearticle~0.9^0.3 \_logicalname:annotation~0.9^0.25 \_logicalname:adx_webpage~0.9^0.2 -\_logicalname:adx_webfile~0.9 adx_partialurl:(@Query) \_logicalname:adx_blogpost~0.9^0.1 -\_logicalname:adx_communityforumthread~0.9
```

ファセットを構成して、サポート情報記事に関連付けられた注釈と単一ファセット内の Web ファイルをグループ化するには、Search/RecordTypeFacetsEntities サイト設定名を編集してその値に `;Downloads:annotation,adx_webfile` を追加します。

サポート情報記事に関連付けられた添付ファイルがポータルおよび検索結果に表示されるようにするには、**KnowledgeManagement/DisplayNotes** サイト設定を編集してその値を**True**にセットします。 サイト設定**KnowledgeManagement/NotesFilter**には、メモ上のメモ テキスト フィールドの前に付ける必要がある接頭語値が含まれます。指定して接頭語値を持つメモのみがポータルに表示されます。 既定では、その値は \*WEB\* ですが、サイト設定を介して変更することができます。

メモに関連付けられた添付ファイルのインデックス作成を有効にするには、 **Search/IndexNotesAttachments** サイト設定を作成してその値を **True** にセットします。
