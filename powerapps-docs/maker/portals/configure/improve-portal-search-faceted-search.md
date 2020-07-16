---
title: ファセット検索を使用してポータル検索を向上させる | MicrosoftDocs
description: ファセット検索を有効または無効にする手順
author: sandhangitmsft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: sandhan
ms.reviewer: tapanm
ms.openlocfilehash: ae049999e35d1b387e81ad590735e8a634874e4f
ms.sourcegitcommit: c12260f372ad2cc48d3146be570d2088c9ef1d86
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2020
ms.locfileid: "3493302"
---
# <a name="use-faceted-search-to-improve-portal-search"></a>ファセット検索を使用してポータル検索を向上させる

ポータルのコンテンツは、そのコンテンツの特性に基づいたフィルターを用いて検索できます。 ファセット ポータル検索で実装されるフィルターにより、顧客は従来の検索よりも早く目的のコンテンツを見つけられます。

## <a name="enable-or-disable-faceted-search"></a>ファセット検索を有効または無効にする

標準のファセット検索はポータルで有効になっています。 それをコントロールしたり有効にするには、次の手順に従います。

1. [ポータル管理アプリ](configure-portal.md) を開いて、**ポータル** &gt; **Web サイト** &gt; **サイト設定**に移動します。
2. **Search/FacetedView** サイト設定を選択します。 
3. **値** を **True** に変更してファセット検索を有効にするか、**False** に変更にして無効にします。

ファセット ビューを 1 つ無効にするには:

1. [ポータル管理アプリ](configure-portal.md) を開いて、**ポータル** &gt; **Web テンプレート**に移動します。
2. 無効にするビューを選択 (ナレッジ マネージメント ー 評価の高い記事)
3. ページの上部にある**非アクティブ化**を選択します。

## <a name="group-entities-as-part-of-a-record-type-for-faceted-view"></a>ファセット ビューのレコードの種類の一部としてエンティティをグループ化する

**Search/RecordTypeFacetsEntities** サイト設定で類似したエンティティを一緒にグループ化して、ユーザーが検索結果を論理的にフィルタリングできるようになります。 たとえば、フォーラム、フォーラムの投稿、およびフォーラムのスレッド用のオプションを別々にせずに、これらのエンティティをフォーラムのレコードの種類の下にグループ化します。

**ポータル** &gt; **Web サイト** &gt; **サイト設定**の順に移動して、**Search/RecordTypeFacetsEntities** サイト設定を開きます。 

異なるエンティティが**フォーラム:** という語で始まることに注意してください。 これは属するグループの名前が最初の値となっているためです。 この語はポータルで使用されている言語に基づいて翻訳されることになります。

## <a name="use-faceted-search-to-improve-knowledge-search-results"></a>ファセット検索を使用してサポート情報の検索結果を向上させる

ファセット検索を使用するとポータルの左端に検索フィルターが表示され、フォーラム、ブログ、またサポート情報記事などの項目から選べるようになります。 特定の検索タイプにはより多くのフィルターが追加されます。 たとえば、サポート情報記事はレコードの種類、修正日、評価、また製品によってフィルタリングできるので、顧客が必要なコンテンツを見つけやすくなります。 また右端には、顧客が選択する関連性や (サポート情報記事に特有の) 表示回数に基づいて結果を並べ替えるドロップダウン ボックスもあります。 以下は、使用可能なフィルターの一部の例を示した画面キャプチャです。

![検索結果を改善するためにフィルタ―を使う](../media/faceted-search-filter.png "検索結果を改善するためにフィルタ―を使う")
