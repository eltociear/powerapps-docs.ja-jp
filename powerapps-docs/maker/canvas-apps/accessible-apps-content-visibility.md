---
title: キャンバス アプリで支援技術のコンテンツを表示または非表示にする | Microsoft Docs
description: キャンバス アプリのコンテンツを視力のあるユーザーだけ、またはスクリーン リーダーのユーザーだけに表示する手法
author: tahoon-ms
ms.service: powerapps
ms.topic: article
ms.custom: canvas
ms.date: 10/22/2018
ms.author: tahoon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c680767bc6a56f0596eba03dd555c1c9a0205346
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "3303877"
---
# <a name="show-or-hide-content-from-assistive-technologies-for-canvas-apps"></a>キャンバス アプリの支援技術のコンテンツを表示または非表示にする

ほとんどの場合、すべてのユーザーがすべてのコンテンツにアクセスできるようにする必要がありますが、場合によっては、視力のあるユーザーまたはスクリーン リーダーのユーザーのみにコンテンツを表示することもできます。 たとえば、スクリーン リーダーのユーザーだけが、視力のあるユーザーには明らかなグラフの傾向の説明にアクセスできるようにすることができます。 隣接するラベルがアイコンを説明している場合は、スクリーン リーダーのユーザーに対してアイコンを非表示にすることもできます。 アイコンに別の説明があると、冗長になってしまいます。

## <a name="hide-content-from-all-users"></a>すべてのユーザーにコンテンツを非表示にする

* **[Visible](controls/properties-core.md)** を false に設定します。

## <a name="hide-content-from-sighted-users-and-show-it-to-screen-reader-users"></a>視力のあるユーザーにコンテンツを非表示にし、スクリーン リーダーのユーザーに表示する

次のいずれかの手法を使用します。

* **[Size](controls/properties-text.md)** を 0 に設定します。
* **[Width](controls/properties-size-location.md)** および **[Height](controls/properties-size-location.md)** を 1 に設定します。
* コントロールが画面の外になるように、**[X](controls/properties-size-location.md)**、**[Y](controls/properties-size-location.md)**、または両方のプロパティを設定します。
* **[Color](controls/properties-color-border.md)** および関連するプロパティを透明に設定します。
* 長方形の**[図形](controls/control-shapes-icons.md)** をコンテンツの上に配置して、**[Fill](controls/properties-color-border.md)** を画面の背景色と同じ色に設定します。

> [!NOTE]
> 前の一覧のいずれかの方法で非表示にした場合でも、ユーザーはキーボードを使用して**[ボタン](controls/control-button.md)** などの対話型コントロールにアクセスできます。 ユーザーが Tab キーを押してコントロールにアクセスできないようにする場合は、**[TabIndex](controls/properties-accessibility.md)** を -1 に設定します。

## <a name="hide-content-from-screen-reader-users-and-show-it-to-sighted-users"></a>スクリーン リーダーのユーザーにコンテンツを非表示にし、視力のあるのユーザーに表示する

* **[イメージ](controls/control-image.md)**、**[アイコン](controls/control-shapes-icons.md)**、および**[図形](controls/control-shapes-icons.md)** コントロールでは、**[AccessibleLabel](controls/properties-accessibility.md)** をからの文字列 "" に設定します。

## <a name="next-steps"></a>次の手順

キャンバス アプリのコントロールの[アクセシビリティ プロパティ](controls/properties-accessibility.md) について説明します。
