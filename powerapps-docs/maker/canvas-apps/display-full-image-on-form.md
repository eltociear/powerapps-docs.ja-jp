---
title: キャンバス アプリ フォームにフルサイズの画像を表示する | MicrosoftDocs
description: キャンバス アプリ フォームにフルサイズの画像を表示する方法を説明します
keywords: ''
ms.date: 10/14/2019
ms.service: powerapps
ms.custom: ''
ms.topic: article
applies_to:
- powerapps
author: Mattp123
ms.assetid: ''
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4327b2c84a4150760b4115b3caa8b38ea1f50334
ms.sourcegitcommit: 82fa1758e29fe302f9a252fd9943ace03b7aada0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/03/2020
ms.locfileid: "3427828"
---
# <a name="display-a-full-sized-image-on-a-canvas-app-form"></a>キャンバス アプリ フォームにフルサイズの画像を表示する
既定では、アプリ ユーザーが表示する画像をキャンバス アプリのフォームに追加すると、表示される画像はサムネイル画像になります。 キャンバス アプリの完全な画像を表示するには、次の手順に従います。 
1. PowerApps Studio で、キャンバス アプリを開きます。 
2. **挿入** を選択し、**画像** を選択します。
3. 画像のデータ カードを選択します。 

    > [!div class="mx-imgBorder"] 
    > ![画像データ カード](../canvas-apps/media/display-full-sized-image/image-data-card.png)

4. **詳細**タブ配下で、**データ**フィールドに表示する画像を含むエンティティを設定します。
5.  画像の**既定**設定の値の後に **.Full**  を追加します。 

    > [!div class="mx-imgBorder"] 
    > ![画像のフル サイズ設定](../canvas-apps/media/display-full-sized-image/image-full-setting.png)

6.  **保存**を選択します。 

### <a name="see-also"></a>関連項目
[キャンバス アプリにレコードを表示、編集、または追加する](add-form.md) <br />
[イメージ フィールド](../common-data-service/types-of-fields.md#image-fields)