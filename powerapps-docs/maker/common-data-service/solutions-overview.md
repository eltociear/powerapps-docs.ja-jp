---
title: Power Apps のソリューション | Microsoft Docs
description: Power Apps のソリューションの概要を提供します
ms.custom: ''
ms.date: 05/19/2020
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: Mattp123
ms.assetid: ece68f5f-ad40-4bfa-975a-3e5bafb854aa
caps.latest.revision: 55
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 1ca8525b6635695d5f4f7d437509222f75ab4111
ms.sourcegitcommit: 82fa1758e29fe302f9a252fd9943ace03b7aada0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/03/2020
ms.locfileid: "3427100"
---
# <a name="solutions-overview"></a>ソリューションの概要  

別の環境にアプリケーションおよびコンポーネントを移動したり、既存のアプリケーションに一連のカスタマイズを適用するために、ソリューションが使用されます。 ソリューションには、1 つ以上のアプリに加えて、サイト マップ、エンティティ、プロセス、Web リソース、オプション セット、フローなど、それ以外のコンポーネントを含めることができます。

ソリューションは、Power Apps やその他 Power Platform などの製品 (Power Automate など) のアプリケーション ライフサイクル管理 (ALM) を実装するためのメカニズムです。 ソリューションの概念、アプリケーションのライフサイクル管理にソリューションを使用する方法の詳細については、Power Platform ALM ガイド内の [Microsoft Power Platform を使った ALM の概要](/power-platform/alm/overview-alm) を参照してください。

このセクションでは、アプリ メーカーが Power Apps のソリューションを使って作業をしながら実行する必要がある **手動** タスクに注目します。

## <a name="get-started-solution-concepts"></a>開始する: ソリューションの概念

ソリューションで作業する前に、次のソリューションの概念を理解することが重要です。
- ソリューションの 2 つの種類 (管理型とアンマネージド型)
- ソリューション コンポーネント
- ソリューションのライフサイクル (ソリューションの作成、更新、アップグレード、パッチ)
- ソリューション発行者
- ソリューションとソリューション コンポーネントの依存関係

詳細については、Power Platform ALM ガイドの [ソリューションの概要](/power-platform/alm/solution-concepts-alm) を参照してください。

## <a name="default-solutions"></a>既定のソリューション

Power Apps は、次の規定の [アンマネージド](/power-platform/alm/solution-concepts-alm) ソリューションを提供します:

- **Common Data Service 規定のソリューション**。 このソリューションは、作成者が環境内でのカスタマイズのために既定で使用できます。 Common Data Service 規定のソリューションは、Power Apps を評価したい場合に役立ちます。 ただし、アプリ作成者は独自のアンマネージド ソリューションで作業することをお勧めします。 
- **規定のソリューション**。 これは、システムですべてのコンポーネントを含む特別なソリューションです。 既定のソリューションは、システム内のすべてのコンポーネントと構成を検出するのに役立ちます。

ただし、カスタマイズを使用またはエクスポートするには、アンマネージド ソリューションを作成することをお勧めします。 詳細: Power Platform ALM ガイドの [ソリューションを使ってカスタマイズする](/power-platform/alm/use-solutions-for-your-customizations)。

<!--  
<a name="BKMK_HowSolutionsAreApplied"></a>   

### How solutions are applied  
All solutions are evaluated as layers to determine what your app will actually do. The following diagram shows how managed and unmanaged solutions are evaluated and how changes in them will appear in your environment.  
  
![Solution layering](media/solution-layering.png "Solution layering")  
  
Starting from the bottom and working up to top:  
  
**System Solution**  
The system solution is like a managed solution that every environment has. The system solution is the definition of all the out-of-the box components in the system.  
  
**Managed Solutions**  
Managed solutions can modify the system solution components and add new components. If multiple managed solutions are installed, the first one installed is below the managed solution installed later. This means that the second solution installed can customize the one installed before it. When two managed solutions have conflicting definitions, the general rule is "Last one wins." If you uninstall a managed solution, the managed solution below it takes effect. If you uninstall all managed solution, the default behavior defined within the system solution is applied.  
  
**Unmanaged Customizations**  
Unmanaged customizations are any change you have made to your environment through an unmanaged solution. The system solution defines what you can or can't customize by using managed properties. Publishers of managed solutions have the same ability to limit your ability to customize solution components that they add in their solution. You can customize any of the solution components that do not have managed properties that prevent you from customizing them.  
  
**Application Behavior**  
The application or runtime behavior is what you actually see in your environment. The default system solution plus any managed solutions, plus any unmanaged customizations you have applied. --> 

## <a name="managed-properties"></a>マネージド プロパティ
マネージド プロパティを使用すると、どのマネージド ソリューション コンポーネントがカスタマイズ可能であるかを制御できます。 管理型コンポーネントを変更できないように、管理型プロパティを設定することをお勧めします。 これにより、テストや本番環境などの別の環境にインポートした後にソリューションが壊れる可能性のある変更からソリューションを保護できます。 

詳細: [Power Platform の管理プロパティ](/power-platform/alm/managed-properties-alm)

## <a name="work-with-solutions-in-power-apps"></a>Power Apps のソリューションで作業する

 Power Apps の左側のナビゲーションから **ソリューション** を選択するとソリューションの一覧を表示できます。 次のソリューション タスクを実行できます。 
- **新規ソリューション**: カスタマイズしたコンポーネントのみを見つけて操作するには、ソリューションを作成し、そこですべてのカスタマイズを行います。 その後、ソリューションを他の環境に簡単に配布できます。 詳細: [ソリューションの作成](create-solution.md) 
- **インポート**: ソリューション ファイルを環境にインポートする。 詳細: [ソリューションのインポート](import-update-export-solutions.md) 
- **AppSource を開く**: [Microsoft AppSource](https://appsource.microsoft.com/) は既に使用している製品と連携する、業種に適したソリューションを入手できる場所です。 
- **すべてのカスタマイズを公開する**: 環境内のすべてのアクティブなカスタマイズを公開します。 
- **クラシックに切り替える**: クラシック ソリューション エクスプローラーを開きます。 
- **履歴を見る**: インポート、エクスポート、アンインストールなど、時間の経過に伴うソリューション操作の詳細を表示します。 詳細: [ソリューションの履歴を表示する](solution-history.md)

    > [!div class="mx-imgBorder"]
    > ![ソリューション エリア](media/solutions-area-tasks.png)

**ソリューション** 領域から、ソリューションを選択して、そのすべてのコンポーネントを表示します。 
 
> [!div class="mx-imgBorder"]  
> ![すべてのコンポーネントのデモ ソリューション](media/solution-all-items-list.PNG "すべてのコンポーネントのデモ ソリューション")   
 
 ソリューションのすべてのコンポーネントはアイテムをスクロールすることで参照できます。 一覧に 100 項目以上ある場合は **次の 100 項目を読み込む** を選択して続きを参照します。 
 
> [!div class="mx-imgBorder"]  
> ![ンポーネントをさらに読み込む](media/load-more.PNG "コンポーネントをさらに読み込む")  

 ## <a name="search-and-filter-in-a-solution"></a>ソリューションの検索とフィルター
  名前で特定のコンポーネントを検索することもできます。 
 
> [!div class="mx-imgBorder"]  
> ![コンポーネント検索](media/solution-search-box.png "コンポーネント検索")  
 
 または一覧のすべてのアイテムをコンポーネントの種類でフィルター処理します。
  
> [!div class="mx-imgBorder"]  
> ![コンポーネントの種類別のフィルター処理](media/solution-filter.PNG "コンポーネントの種類別のフィルター処理")  
 

 ## <a name="contextual-commands"></a>コンテキスト コマンド
 ソリューションが既定もしくは管理されている場合、それぞれのコンポーネントを選択するとその種類によってコマンド バーで利用できる操作が変化します。 
 
> [!div class="mx-imgBorder"]  
> ![コンポーネントの特定のコマンド](media/component-commands.png "コンポーネントの特定のコマンド")  
 
 どのコンポーネントも選択しない場合は、コマンド バーはソリューション自体に適用される操作を表示します。 
 
> [!div class="mx-imgBorder"]  
> ![ソリューションの特定のコマンド](media/solution-commands.PNG "ソリューションの特定のコマンド")  
 
既定もしくはアンマネージドのソリューションでは、**新規** または **既存に追加** コマンドを使用して異なる種類のコンポーネントを作成または追加することができます。 詳細: [ソリューション コンポーネントの追加](create-solution.md#add-solution-components)
 
> [!NOTE]
> 管理ソリューションにコンポーネントを追加することはできません。 保存しようとすると、次のメッセージが表示されます。<br/>
`"You cannot directly edit the components within a managed solution. You’ll need to add it to another unmanaged solution that you’ve created to customize the component. The component might not be customizable."`


## <a name="known-limitations"></a>既知の制限

次の制限がソリューションのキャンバス アプリ、フロー、ユーザーのコネクタの使用に適用されされます。 

- 接続には認証と同意が必要です。これにはインタラクティブなユーザーセッションが必要であるため、ソリューションを介して転送することはできません。 ソリューションをインポートしたら、アプリを再生して接続を認証します。 ソリューションをインポートする前に、ターゲット環境で接続を作成することもできます。 
- キャンバス アプリ ボタンによってトリガーされるフローは、既にソリューションにあるアプリから作成する必要があります。 外部ソリューションからのこの種類のフロー追加はブロックされます。
  - アプリとフローは現在、展開後のターゲット環境で接続されません。 最初に有効な接続をフローに関連付け、フローを有効化します。 次にアプリを編集して、フローをボタンに再度関連付けます。
-   ソリューションに作成されたキャンバス アプリは共同所有者として Azure Active Directory AAD セキュリティ グループと共有できません。 ソリューションに追加する前にアプリの共有を解除します。
-   キャンバス アプリはクラシック ソリューション エクスプローラーに表示されません。 最近のエクスペリエンスをご使用いただけます。 それらをクラシック ソリューション エクスプローラーに追加する予定はありません。 
- バックアップ、復元、およびコピーなどのデータベース操作では、キャンバスのアプリケーション、およびワークフローがサポートされていません。 これらの操作を使用すると、キャンバスのアプリとワークフローが破損する可能性があります。
- マネージド ソリューションを削除しても別のキャンバス アプリのバージョンにロールバックしません。 代わりに、アプリのすべてのバージョンが削除されます。
- フローを含むソリューションをインポートしても、必要な接続が自動的に作成または関連付けされることはありません。 接続を修正するには、フローを編集する必要があります。
  - マネージド ソリューションを使用している場合は、アンマネージド層でアクティブなカスタマイズを作成します。 したがって、フローに対するそれ以降のソリューションの更新は反映されません。 
- ソリューションから作成されたフローは、[チーム フロー] 一覧に表示されません。 ソリューションを使用してアクセスする必要があります。 
- ボタンにトリガーされたフローはソリューションで利用できません。
- Excel など Microsoft 365 アプリケーションからトリガーされたフローは、ソリューションで使用できません。
- SharePoint に接続するフローはソリューションで利用できません。
- ソリューション フローが会社認証をサポートしません。 たとえば、フローへのアクセスは、ワークフローの作成元である SharePoint リストに対するアクセスを行うに基づいて自動的に付与されません。
- ソリューションの外部で作成されたカスタム コネクタは、この時点ではソリューションに追加することはできません。


 ソリューションの各コンポーネントのカスタマイズの詳細については、以下のトピックを参照してください:  
  
-   エンティティ、エンティティの関連付け、フィールドおよびメッセージのカスタマイズについては、[メタデータ](create-edit-metadata.md) を参照してください。  
  
-   エンティティ フォームについては、[フォーム](../model-driven-apps/create-design-forms.md) を参照してください。  
  
-   プロセスについては、[プロセス](../model-driven-apps/guide-staff-through-common-tasks-processes.md) を参照してください。  
  
-   業務ルールについては、[業務ルール](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md) を参照してください。
 
 
### <a name="next-steps"></a>次の手順  
[ソリューションの作成](create-solution.md) <br/>

 
