---
title: 'コンテナー コントロール: リファレンス | Microsoft Docs'
description: プロパティとサンプルを含む、コンテナー コントロールに関する情報
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.component: canvas
ms.date: 05/01/2020
ms.author: emcoope
ms.reviewer: tapanm-msft
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 472683bd7b8d78f655aae89d1fd618b54ae4b24e
ms.sourcegitcommit: b75b29d58adf1547c9fcd3ddd1f14f69fb7f572b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/02/2020
ms.locfileid: "3330518"
---
# <a name="container-control-in-power-apps-experimental"></a>Power Apps でのコンテナー コントロール (実験段階)
階層を作成する機能を提供します。

> [!IMPORTANT]
> これは実験段階の機能です。 試験的な機能は根本的に変更され、いつでも完全に表示されなくなります。
> 詳細については、[Power Apps での実験段階の機能とプレビュー機能について](https://docs.microsoft.com/powerapps/maker/canvas-apps/working-with-experimental-preview) をお読みください。

## <a name="description"></a>内容
 コンテナーは一連のコントロールを保持でき、独自のプロパティがあります。

空のコンテナーを挿入して開始できます。 次に、コントロールの追加、サイズ変更、移動、非表示化や他の変更を加えることによりカスタマイズできます。 いくつかのコントロールから始めて、それらを選択し、ツリー ビューの使用を追加することもできます。

## <a name="properties"></a>プロパティ​​
**[BorderColor](properties-color-border.md)** – コントロールの境界線の色。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線が**実線**、**破線**、**点線**、または**なし**かどうか。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さ。

**[塗りつぶし](properties-color-border.md)** – コントロールの背景色。

**[高さ](properties-size-location.md)** – コントロールの上端と下端間の距離。

**[幅](properties-size-location.md)** – コントロールの左端と右端間の距離。

**[表示](properties-core.md)** – コントロールが表示されるか非表示になるか。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離。 

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離。 


## <a name="known-limitations"></a>既知の制限

コンテナーはフォーム内では機能しません。

## <a name="frequently-asked-questions"></a>よく寄せられる質問

### <a name="what-is-the-difference-between-a-container-and-a-group"></a>コンテナーとグループ間の違いは何ですか。

作成グループは、コントロール内を移動し、グループ内のコントロールの同様のプロパティを一括編集するために使用される軽量概念です。 作成グループは、アプリのレイアウトに影響を与えません。

以前は実験段階で出荷されたコンテナー コントロールは、作成グループの代わりに拡張グループとして名前変更されました。 軽量の作成グループと追加のプロパティを持つ構造化されたコンテナー コントロールの両方に値があるため、コンテナー コントロールに名前変更されました。
