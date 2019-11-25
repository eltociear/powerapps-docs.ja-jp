---
title: PowerApps にてモデル駆動型アプリ メイン フォームを作成、編集する | MicrosoftDocs
description: メイン フォームの作成または編集の方法を学習する
ms.custom: ''
ms.date: 05/23/2018
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
ms.assetid: <needs new guid>
caps.latest.revision: 18
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 52b80ac0809bbcfe0b008e6fc31fd8b97b894959
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "2759209"
---
# <a name="create-or-edit-a-model-driven-app-main-form-for-an-entity"></a>エンティティのモデル駆動型アプリのメイン フォームの作成または編集 

このトピックでは、エンティティのメイン フォームを作成または編集する方法について説明します。

エンティティのフォームを新規作成する場合、そのフォームの種類は [メイン] です。 新しいフォームを開いたとき、そのフォームは [情報] という名前のフォームと同じです。 フォームに関連するフィールド、セクション、タブ、ナビゲーション、およびプロパティを追加または編集し、そのフォームを保存できます。

各メイン フォームは、1 つ以上のタブで構成されます。 各タブは、1 つ以上のセクションを持つことができます。 各セクションは、1 つ以上のフィールドまたは IFRAME を含みます。 既存のものに基づいて新しいフォームを作成する場合は、フォームを複製できます。 

このタスクを実行するために、システム管理者またはシステム カスタマイザーのセキュリティ ロール、または同等のアクセス許可があることを確認してください。

## <a name="how-to-create-or-edit-a-main-form"></a>メイン フォームの作成または編集の方法
  
1.   [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインします。


> [!IMPORTANT]
> **モデル駆動型** デザイン モードがない場合は、[環境の作成](https://docs.microsoft.com/powerapps/administrator/create-environment)が必要となることがあります。   
  
2.  **データ**を展開して**エンティティ**を選択し、目的のエンティティを選択して**フォーム** タブを選択します。 

3. 新しいメイン フォームを作成するには、ツール バーで **フォームの追加** > **メイン フォーム** を選択します。  
    \-または- 既存のメイン フォームを編集するには、**メイン**の**タイプ**のフォームを選択します。
  
3.  必要に応じて、以下の方法のいずれかで、フォームの設計を変更します:
    -   フォームへのタブの追加
    -   セクションをフォームに追加する
    -   フィールドをフォームに追加する
    -   フォームの IFRAME の追加または編集
    -   フォームでのサブグリッドの追加または編集
    -   フォームの Web リソースの追加または編集
    -   関連エンティティのフォーム ナビゲーションの追加または編集
    -   フォームのヘッダーおよびフッターの編集
    -   タブ セクション フィールド、または IFRAME の削除
    -   フォーム アシスタントの有効化または無効化
    
4.  必要に応じて、フォームのパーツのプロパティを編集します。
    -   フォーム プロパティの編集
    -   フォームのフィールドのプロパティを編集する
    -   タブのプロパティの編集
    -   セクション プロパティの編集

5.  必要に応じて、イベント スクリプトを追加します。 

6.  フォームを表示できるセキュリティ ロールを決定します。 詳細情報: [フォームへのセキュリティ ロールの割り当て](https://docs.microsoft.com/dynamics365/customer-engagement/admin/assign-security-roles-form)

7.  メイン フォームがどのように表示されるか、およびイベントがどのように機能するかをプレビューします。
    - **ホーム**タブで**プレビュー**を選択してから、**フォームの作成**、**フォームの更新**、または**読み取り専用**を選択します。
    - [プレビュー] フォームを閉じるには、**ファイル**メニューで、**閉じる**を選択します。

8.  フォームの編集が終了したら、**名前を付けて保存** を選択し、フォームの名前を入力し、次に **OK** を選択します。

9.  カスタマイズが完了したら、公開します。
    -   現在編集中のコンポーネントのみのカスタマイズを公開するには、**コンポーネント**の下で、取り組んでいるエンティティをクリックしてから、**公開**をクリックします。
    -   非公開のすべてのコンポーネントのカスタマイズを一度に公開するには、**コンポーネント**の下で、**エンティティ**をクリックしてから、コマンド バーで、**すべてのカスタマイズの公開**をクリックします。
    
 
### <a name="next-steps"></a>次のステップ  
[フォーム エディターのユーザー インターフェイスの概要](form-editor-user-interface-legacy.md)
 
