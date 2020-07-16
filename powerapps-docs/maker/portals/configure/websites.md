---
title: ポータルで Web サイトを管理する | MicrosoftDocs
description: ポータルで Web サイトを管理する方法について説明します。
author: sandhangitmsft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 04/30/2020
ms.author: sandhan
ms.reviewer: tapanm
ms.openlocfilehash: 452b649103e01a6149c15f49d935b3ae76877304
ms.sourcegitcommit: c12260f372ad2cc48d3146be570d2088c9ef1d86
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2020
ms.locfileid: "3493032"
---
# <a name="manage-websites"></a>Web サイトの管理

Web サイトはポータル アプリケーションのコア エンティティです。 ポータル アプリは単一の Web サイト レコードを選択して、このアプリ ケーションに対して[Web ページ](web-page.md)、[Web ファイル](web-files.md)、[Web ロール](create-web-roles.md)、および [コンテント スニペット](customize-content-snippets.md) などでどのポータル エンティティが適用対象であるかを決定します。

アプリケーション スコープを提供する Web サイトにより、複数の異なるポータル アプリケーションを単一の組織に接続することができます。

> [!NOTE]
> 指定したポータル アプリケーションのバインド対象となる Web サイト レコードを決定するのは、通常ポータル展開の構成で指定した Web サイト名です。
ただし、ドメイン名または Web サイト バインドによってこれをコントロールすることも可能です。

## <a name="manage-websites"></a>Web サイトの管理

新しいポータルを作成すると、Web サイトが作成されます。 ただし、高度な Web サイト管理は、ポータル管理アプリから実行できます。 

> [!WARNING]
> Web サイト レコードを削除すると、Web ページや Web リンクなどのポータル メタデータ エンティティの Web サイト レコードに関連するデータも削除されます。 Web サイト全体およびその関連データを単一の操作で組織から削除することができることを意味するため、通常これは望ましい動作です。

1. [ポータル管理アプリ](configure-portal.md)を開きます。

2. **ポータル** > **Web サイト**に移動します。

3. 既存の Web サイトを編集するには、Web サイト名を選択します。

4. フィールドに適切な値を入力または編集します。

5. **保存して閉じる**を選択します。

### <a name="website-attributes"></a>Web サイト属性

|名前|説明|
|-|-|
|名前|Web サイトの内容を示す名前。 これは必須フィールドです。|
| 既定の言語 | 選択したポータル用の既定の言語。 既定の言語を変更する前に、次のことを行う必要があります。 <br> - [Common Data Service 環境に言語を追加](https://docs.microsoft.com/power-platform/admin/enable-languages)。 <br> - Web サイト レコード用セクションの[サポートされている言語に言語を追加](enable-multiple-language-support.md)。
| 所有者  | 選択された Web サイト レコード用の所有取引先担当者レコード。
|プライマリ ドメイン名|この Web サイト レコードが追加されるポータルのプライマリ ドメイン名です。|
|親 Web サイト\*|Web サイトの親 Web サイトです。 このフィールドは、単一のポータル アプリケーションが、アプリケーションのルート パスにあり特定のサブパスで利用可能な 1 つまたは複数の子 Web サイトを持つ 1 つのマスター Web サイトにバインドされる、特定の詳細ポータル構成を除き、通常は無視することができます。 <br>\* 下位互換性の場合のみ、新規または既存ポータルには使用できません。 |
| ヘッダーおよびフッター テンプレート | グローバル ヘッダーおよびフッターを上書きする[ヘッダーおよびフッターの Web テンプレート](../liquid/store-content-web-templates.md#web-templates-as-page-templates)。
| サポートされている言語 | 選択された Web サイト レコードの [サポートされた言語](enable-multiple-language-support.md)。

### <a name="see-also"></a>関連項目

[Web サイト バインド](website-bindings.md)
