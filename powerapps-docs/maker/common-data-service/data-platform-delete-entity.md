---
title: エンティティを削除する | Microsoft Docs
description: ユーザー定義エンティティを削除し Power Apps のすべてのデータを消去する方法に関する詳細な手順
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 06/29/2020
ms.author: lanced
ms.reviewer: matp
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 9b0658c24fac54ac8adac55dd7c356aff4b32432
ms.sourcegitcommit: 3f8213fc8eec12df2b563824e347d4f647adaf96
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "3527707"
---
# <a name="delete-an-entity"></a>エンティティの削除
ユーザー定義エンティティを削除できますが、標準のエンティティは削除できません。 カスタム エンティティに 1 つ以上の依存関係を持つコンポーネントが存在している場合は、削除できないことに注意してください。 詳細情報 : [依存関係のあるエンティティを削除する](#delete-an-entity-that-has-dependencies)

> [!WARNING]
> エンティティを削除すると、エンティティ定義およびエンティティに含まれるすべてのデータの両方とも削除されます。 エンティティとエンティティ内のデータを削除すると復旧できません。

## <a name="delete-a-custom-entity"></a>ユーザー定義エンティティの削除
1. [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)にログインし、左側のナビゲーション ペインで、**ソリューション**を選択します。削除するカスタム エンティティを含むソリューションを開き、選択します。

    ![エンティティの詳細](./media/data-platform-cds-create-entity/entitylist.png "エンティティ リスト")

2. コマンドバーで選択**削除**を選択し、以下のの選択肢から選択します :  
   - **このソリューションから削除する**。 ソリューションからコンポーネントを削除します。 既定のソリューションからは、引き続きエンティティにアクセスできます。 
   - **この環境から削除します**。 エンティティと関連データを削除します。 

3. 表示されたダイアログ ボックスで、**削除**を選択してエンティティを削除します。 *このコンポーネントを他のコンポーネントが参照しいるため、削除できません*というメッセージが表示された場合、この記事の次のセクションを参照してください。 

## <a name="delete-an-entity-that-has-dependencies"></a>依存関係のあるエンティティを削除する
ビジネス プロセス フローやモデル駆動型アプリなど、他のコンポーネントに依存しているエンティティは削除できません。 

依存関係を削除するには、次の2つの方法があります : 
- コンポーネントを再構成して、依存関係を削除します。 
- コンポーネントを削除します。 

### <a name="remove-a-dependency"></a>依存関係の削除
コンポーネントの依存関係を確認するには、[コンポーネントの依存関係を表示する](view-component-dependencies.md)を参照してください。 

続いて、コンポーネントを削除します。 たとえば、削除するエンティティを参照するビジネス プロセス フローがある場合は、ビジネス プロセス フローを編集してそのエンティティを削除してください。 ビジネス プロセス フローがこのエンティティを参照しなくなると、エンティティは依存関係の表示リストに表示されなくなり、削除することができます。 詳細 : [カスタム エンティティを削除する](#delete-a-custom-entity)   

> [!IMPORTANT]
> 依存関係を削除すると、コンポーネントが機能しなくなる可能性があります。 たとえば、モデル駆動型アプリからエンティティを削除すると、モデル駆動型アプリが機能しなくなる可能性があります。 

詳細については、これらの記事を参照してください。 
- [アーティファクトを編集、または削除する](../model-driven-apps/add-edit-app-components.md#edit-or-remove-artifacts)
- [業務プロセス フローを編集する](/power-automate/create-business-process-flow#edit-a-business-process-flow)
- [関連付けの削除](create-edit-1n-relationships-portal.md#delete-relationships)
