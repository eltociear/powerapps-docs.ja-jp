---
title: ソリューションを作成する | MicrosoftDocs
description: ソリューションの作成方法を学習する
ms.custom: ''
ms.date: 03/20/2020
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
author: Mattp123
ms.assetid: e21a4876-08b4-417a-a644-c577a27c5cf1
caps.latest.revision: 12
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 59c041d7fe74e1a1dbbce9f1516057d324447478
ms.sourcegitcommit: 310dd3dc68ffebe6a416450836ac0ba988b84fb4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2020
ms.locfileid: "3162200"
---
# <a name="create-a-solution"></a>ソリューションの作成

カスタマイズしたコンポーネントだけを検索して操作するには、ソリューションを作成し、ソリューションですべてのカスタマイズを行います。 コンポーネントを追加、編集、作成する際には、常にカスタムソリューションのコンテキストで作業をしてください。 これにより、ソリューションを別の環境にインポートしたり、バックアップ目的で簡単にエクスポートできます。   
  
ソリューションの概念の詳細については、「[ソリューションの使用](solutions-overview.md)」を参照してください。  
  
1.  [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインし、左側のナビゲーションから **ソリューション** を選択します。 
  
2.  **新しいソリューション**を選択し、ソリューションの必須フィールドを完了します。
  
    |フィールド|説明|  
    |-----------|-----------------|  
    |**表示名**|ソリューションの一覧に表示される名前。 これは後で変更できます。|  
    |**名前**|ソリューションの一意の名前。 これは、表示名フィールドに入力した値を使用して作成されます。 ソリューションを保存する前に編集できますが、保存後は変更できません。|  
    |**発行元**|既定の発行者を選択するか、または新しい発行元を作成できます。 ソリューションをご利用の環境全体で安定して使用をするあたって、組織のパブリッシャーを作成することを推奨します。 詳細: [ソリューション発行者の概要](change-solution-publisher-prefix.md) |  
    |**バージョン**|ソリューションのバージョン番号を入力します。 これは、ソリューションをエクスポートする場合にのみ重要です。 バージョン番号は、ソリューションをエクスポートしたときにファイル名に含まれます。|  
  
3.  **保存**を選びます。  
  
 ソリューションの保存後、必須でないフィールドに情報を追加することができます。 これらの手順は任意です。 **説明**フィールドを使用してソリューションを説明し、ソリューションの**構成ページ**として HTML Web リソースを選択します。 構成ページは通常、ソリューションを配布する ISV が使用します。 これを設定すると、**情報**ノードの下に新しい**構成**ノードが表示され、この Web リソースが表示されます。 開発者はこのページを使用して、指示やコントロールを含めるので、構成データを設定したり、これらのソリューションを立ち上げたりすることができます。  
  
<a name="BKMK_AddSolutionComponents"></a>   

## <a name="add-solution-components"></a>ソリューション コンポーネントの追加  
 ソリューションを作成した後は、ソリューション コンポーネントはまったく含まれていません。 新しいソリューション コンポーネントを作成したり、既定のソリューションからソリューション コンポーネントを追加するために一覧メニューの**既存を追加**ボタンを使用したりできます。  
  
 これを行うと**不足している必須コンポーネント**ダイアログが表示される場合があります。  
   
 ![必須コンポーネント ダイアログの追加](media/crm-itpro-cust-addrequiredcomponents.PNG "必須コンポーネント ダイアログの追加")  
  
 このダイアログでは、ソリューション コンポーネントが別のソリューション コンポーネントと依存関係があることが警告されます。 **いいえ、必須コンポーネントを含めません**を選択すると、これらの必須コンポーネントのすべてが揃っていない別の組織にインポートする場合、ソリューションは失敗することがあります。 ソリューションのインポートが成功した場合でも、他のソリューションの動作が元の組織と同じでない場合があります。これはコンポーネントがソース ソリューションのコンポーネントとは異なる方法で構成されるためです。  
  
エンティティ コンポーネントを選択するときは、ソリューションのセグメンテーションを使用して、ソリューションの更新を配布するときに新規または更新されたエンティティコンポーネントのみを含めることをお勧めします。 ソリューションのセグメント化により、すべての資産を含むエンティティ全体ではなく、選択したエンティティ資産 (エンティティ フィールド、フォーム、ビューなど) とともにソリューションで作業できます。 詳細: [セグメント化されたソリューションを使用する](use-segmented-solutions-patches-simplify-updates.md)
  
 ソリューションをエクスポートしない場合、またはアンマネージド ソリューションとしてエクスポートし同じ組織にインポートし直す場合、必須コンポーネントが含まれている必要はありません。 そのようなソリューションをエクスポートすると、必須コンポーネントの一部が存在しないことを示す別の警告が表示されます。 同じ組織にソリューションをインポートし直す場合にのみ、この警告を無視してもかまいません。 サード パーティの編集ツールを使用せずにアプリケーション ナビゲーションやリボンを編集する手順では、同じ組織にソリューションをエクスポートし直すことを仮定しています。  

<!-- >
> [!IMPORTANT]
>  If you plan to include appointments in solutions, we strongly recommend that you don’t include only appointments and only recurring appointments in separate solutions. If you install and uninstall separate solutions with different appointment types, you’ll encounter a SQL Server error and you’ll have to re-create the appointments.  -->

## <a name="publish-changes"></a>変更の公開 

 ユーザー インターフェイスを変更する特定のカスタマイズは、アプリケーションで使用する前に公開する必要があります。 
 
### <a name="publish-your-customizations"></a>カスタマイズの公開

1.  左のナビゲーション ウィンドウから、**ソリューション**を選択します。

2.  公開するソリューションを選択して開きます。

3.  コマンドの一覧から、**すべてのカスタマイズの公開**を選びます。  

![すべてのカスタマイズの公開](media/publish-all-customizations.PNG "すべてのカスタマイズの公開")  
  
> [!IMPORTANT]
>  カスタマイズの準備には時間がかかることがあります。 ブラウザーのページが反応しなくなっているというメッセージが表示された場合は、閉じないで、ページが反応する状態になるまで待機します。  

### <a name="see-also"></a>関連項目
 [ソリューションの使用](use-solution-explorer.md)
