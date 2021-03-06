---
title: Power Apps で投稿に関する情報にアクセスするためにモデル駆動型アプリのメモ コントロールを設定する | MicrosoftDocs
ms.custom: ''
ms.date: 05/06/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: f10cdf1c-3540-439c-a171-27a10e72da45
caps.latest.revision: 63
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 52edc0881484d092332cc2ab5a3892d0f7983e30
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2019
ms.locfileid: "2862977"
---
# <a name="set-up-the-model-driven-app-notes-control-to-access-information-about-posts"></a>投稿に関する情報にアクセスするためにモデル駆動型アプリのメモ コントロールを設定する

 [更新されたフォーム](main-form-presentations.md#updated-forms) を使用する特定のシステム エンティティの Power Apps フォームでは、メモ コントロールによって、**投稿**、**アクティビティ**、および**メモ**に関する情報にアクセスする機能が提供されます。 メモと活動を有効にするユーザー定義エンティティでは、**メモ**と**活動**のみが表示されます。 **投稿**を含めるには、ユーザー定義エンティティに対して有効にする必要があります。  
  
## <a name="enable-posts-for-a-custom-entity"></a>ユーザー定義エンティティに対して投稿を有効にする  
  
1.  **[設定](advanced-navigation.md#settings)** > **アクティビティ フィード構成** に移動します。 
  
2.  ユーザー定義エンティティのレコードを開きます。  
  
3.  **この種類のレコードフォームでウォールを有効にする**が選択され、レコードを保存していることを確認します。  
  
4.  コマンド バーで、**アクティブ化**を選択します。  
  
5.  ウォールを有効にする必要がある場合は、エンティティを公開する必要があります。  
  
 既定では、システム エンティティの場合、メモ コントロールはフォーム上部の 3 列タブの真ん中にあるソーシャル ウィンドウ領域にあります。 フォームで 1 回のみ表示されます。 メモ コントロールを移動または削除できます。 追加し直すには、**挿入**タブの**コントロール**グループで**メモ**ボタンを使用します。  
  
 次の表に、メモ コントロールのプロパティを説明します。  
  
|タブ|プロパティ|説明|  
|---------|--------------|-----------------|  
|**表示**|**ラベル**|**必須**: ラベルが既定では表示されませんが、ラベルは必要です。|  
||**フォームでラベルを表示する**|ラベルを表示するようにすることもできます。|  
||**フォーム上でこのフィールドをロックする**|これにより、メモがフォームから誤って削除されることを防げます。|  
||**既定のタブ**|既定で表示するタブを選択します。 オプションは次のとおりです。<br /><br /> - **活動**<br />- **投稿**<br />- **注意**|  
|**形式**|**コントロールが使用する列数を指定してください**|メモ コントロールを含むセクションに複数の列があるとき、フィールドがセクションにある列の数まで占めるように設定できます。|  
||**行数**|コントロールが占める列数を選択することで、メモ コントロールの高さを制御できます。|  
||**自動拡張して、使用可能なスペースを広げます**|列数で高さを設定するのではなく、メモ コントロールの高さが使用可能なスペースに拡張されるようすることができます。|  
  
## <a name="next-steps"></a>次のステップ
[フォーム エディターを開く](open-form-editor.md)
