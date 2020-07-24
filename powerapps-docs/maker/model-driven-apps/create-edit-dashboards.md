---
title: モデル駆動型アプリ ダッシュボードを作成または編集する | MicrosoftDocs
ms.custom: ''
ms.date: 04/08/2020
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
ms.assetid: 641885d2-4a08-41b8-b914-d9a244e4d5b1
caps.latest.revision: 10
ms.author: matp
manager: kvivek
author: Mattp123
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 9a9e49a14268c3ee82a8c5fb541473903bbf5f11
ms.sourcegitcommit: 3c6c5594b73abd5ff438d50f3b579d56cef7241c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2020
ms.locfileid: "3285808"
---
# <a name="create-or-edit-model-driven-app-dashboards"></a>モデル駆動型アプリ ダッシュボードを作成または編集する

ユーザー ダッシュボードとシステム ダッシュボードの 2 種類のダッシュボードがあります。 アプリ ユーザーは、特権を持つユーザーがアプリ領域にいるときのみ見られるダッシュボードを作成できます。 管理者またはカスタマイザーは、公開されるとすべてのアプリ ユーザーに対して表示されるシステム ダッシュボードを作成またはカスタマイズします。 ユーザーは自分のユーザー ダッシュボードを既定のダッシュボードとして設定し、システム ダッシュボードに上書きするよう選択できます。   

ダッシュボードは、標準型または対話型に設定することができます。 標準ダッシュボードは、グラフやリストなどの 1 つ以上の関連付けがされていないコンポーネントの追加に対応しています。 対話型ダッシュボードは、ユーザーがダッシュボードから直接特定のレコードを操作する機能を提供します。 このトピックは標準型のダッシュボードに特化しています。 対話型ダッシュボードの構成方法の詳細については、 [モデル駆動型アプリの対話型エクスペリエンス ダッシュボードの構成](configure-interactive-experience-dashboards.md) を参照してください。
  
<a name="BKMK_createdashboard"></a>   
## <a name="create-a-new-standard-dashboard"></a>新しい標準型ダッシュボードを作成する  
  
1.  [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインします。
  
2. **ソリューション** を選択し、続いて対象とするソリューションを開きます。

3. ツール バーで **新規** を選択し、**ダッシュボード** を選択します。続いて 2、3、4、などの列のレイアウトを選択します。  
  
4.  **ダッシュボード: 新規**ページにて、ダッシュボードの名前を入力します。  
  
5.  いずれかのコンポーネント領域を選択し、グラフまたはリストのアイコンを選択します。  
  
     ダッシュボードには最大 6 つのコンポーネントを含めることができます。  
  
6.  たとえば、グラフを追加するには、ダッシュボード キャンバスのタイルで、グラフを表示したい場所にあるグラフのアイコンを選択します。 続いて、**コンポーネントの追加** ダイアログ ボックスで、**レコードの種類** の値を選択します。続いて **ビュー**、**グラフ**の値を選択し、**追加** を選択するとダッシュボードにグラフが追加されます。 グラフの作成方法に関する詳細は、[モデル駆動型アプリのシステム グラフを作成する](create-edit-system-chart.md) を参照してください。
  
7.  ダッシュボードへのコンポーネントの追加完了後は、**保存** を選択し、続いて **閉じる** を選択します。  

8. ソリューションのツール バーで、**公開** を選択します。 
  
<a name="BKMK_editdashboard"></a>   
## <a name="edit-an-existing-dashboard"></a>既存のダッシュボードの編集  
  
1. [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインします。

2. **ソリューション** を選択し、続いて対象とするソリューションを開きます。  

3. ソリューション コンポーネントのリストで、ダッシュボードを開きます。コンポーネント領域のいずれかを選択し、続いてツールバーの **コーポーネントの編集** を選択します。  
  
4.  **プロパティの設定** ダイアログ ボックスで、エンティティの変更、既定のビュー、グラフ セレクターの追加、モバイル アプリでダッシュボードを使用できるようにするなど、グラフまたはリストに変更を加えることができます。 終了したら、**OK** を選択します。  
  
     設定ダッシュボードのコンポーネント プロパティの詳細については、「[ダッシュボードに組み込むグラフまたはリストのプロパティ設定](set-properties-chart-list-included-dashboard.md)」を参照してください。  
  
5.  ツールバーの変更の完了後は、**保存** を選択し、**閉じる**を選択します。 

6. ソリューションのツール バーで、**公開** を選択します。  
  
追加のシステム ダッシュボードで実行できるタスクには、以下のものが含まれます。  
  
-   ダッシュボードからリストまたはグラフを削除する  

-   ダッシュボードに対してリストまたはグラフを追加する  

-   既定のダッシュボードを設定する  

-   セキュリティ ロールを使用して、特定のロールのみに対してダッシュボードが表示されるようにする    

## <a name="next-steps"></a>次のステップ  
[ダッシュボードに組み込むグラフまたはリストのプロパティ設定](set-properties-chart-list-included-dashboard.md)
