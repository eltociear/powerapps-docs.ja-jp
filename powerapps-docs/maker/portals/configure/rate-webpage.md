---
title: ポータルの Web ページの評価または投票 | MicrosoftDocs
description: ポータルで Web ページの評価を有効にし、管理するための手順。
author: sandhangitmsft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/11/2019
ms.author: sandhan
ms.reviewer: tapanm
ms.openlocfilehash: bdb68d547799ef947d8043f56181739577277fd4
ms.sourcegitcommit: c12260f372ad2cc48d3146be570d2088c9ef1d86
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2020
ms.locfileid: "3491587"
---
# <a name="rate-or-vote-on-a-webpage-on-a-portal"></a>ポータルの Web ページの評価または投票

評価はユーザーにWeb ページの評価または投票を提供します。 評価はページのコメントに対して有効にすることもできます。 既定ではこの機能は無効ですが、ページ単位で有効にすることができます。

評価はカスタム活動なので、電子メールや電話などのその他の活動と同じように使用できます。 評価は活動なので、カスタマイズすることで、カスタム エンティティを含む選択したあらゆるエンティティに対する評価を表示したり、ポータル上に表示できます。

## <a name="enable-ratings-for-pages"></a>ページの評価を有効にする

1. [ポータル管理アプリ](configure-portal.md)を開きます。

2. **ポータル** > **Web ページ**の順に移動します。

3. 評価を可能にしたい **Web ページ** を選択します。

4. **全般** タブの **ページ オプション** で、**評価を有効にする** を **はい** に設定します。

5. **保存して閉じる**を選択します。

## <a name="use-ratings"></a>評価の使用

ページ評価が有効化されていて開発者がコントロールをテンプレートに適用している Web ページの場合、ユーザーはページ テンプレートにコントロールが追加された際に選択された種類に応じて、評価尺度または投票によって評価できます。

### <a name="rating-type"></a>評価の種類

![評価の種類](../media/rating-type.png "評価の種類")  

### <a name="vote-type"></a>投票の種類

![投票の種類](../media/vote-type.png "投票の種類")  

## <a name="manage-ratings"></a>評価の管理

Web ページに対する評価は Power Apps ポータルで表示、変更、または削除できます。

1. [ポータル管理アプリ](configure-portal.md)を開きます。

2. 評価を見ることに興味がある **Web ページ** に移動します。

3. **関連** タブで **活動** を選択します。 関連ビューは、選択した Web ページに対するログを評価します。 このビューで、既存の価格を変更または削除できます。
