---
title: Power Apps でソリューションを作成する | MicrosoftDocs
description: Power Apps におけるソリューションの作成方法を説明します
ms.custom: ''
ms.date: 05/19/2020
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
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
ms.openlocfilehash: 51f24972c664770bbcd2b21ed7880ef629aad31e
ms.sourcegitcommit: 909948d219c3c61d617f13aceb355e1d5bcb0b55
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2020
ms.locfileid: "3432753"
---
# <a name="create-a-solution"></a>ソリューションの作成

カスタマイズしたコンポーネントだけを検索して操作するには、ソリューションを作成し、ソリューションですべてのカスタマイズを行います。 コンポーネントを追加、編集、作成する際には、常にカスタムソリューションのコンテキストで作業をしてください。 これにより、ソリューションを簡単にエクスポートし、別の環境にバックアップまたはインポートできます。 

> [!NOTE]
> ソリューションを使用した健全なアプリケーション ライフサイクル管理 (ALM) の導入については、[Power Platform ALM ガイド](/power-platform/alm)を参照してください。
  
ソリューションの作成方法 :   
1.  [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインし、左側のナビゲーションから **ソリューション** を選択します。 
  
2.  **新しいソリューション**を選択し、ソリューションの必須フィールドを完了します。
  
    |フィールド|説明|  
    |-----------|-----------------|  
    |**表示名**|ソリューションの一覧に表示される名前。 これは後で変更できます。|  
    |**名前**|ソリューションの一意の名前。 これは、表示名フィールドに入力した値を使用して作成されます。 ソリューションを保存する前に編集できますが、保存後は変更できません。|  
    |**発行元**|既定の発行者を選択するか、または新しい発行元を作成できます。 ソリューションを使用する環境全体で一貫して使用できるように、組織で使用する発行元を作成することをお勧めします。 この記事の後半に記載している、[ソリューション発行者](#solution-publisher) を参照してください。 |  
    |**バージョン**|ソリューションのバージョン番号を入力します。 これは、ソリューションをエクスポートする場合にのみ重要です。 バージョン番号は、ソリューションをエクスポートしたときにファイル名に含まれます。|  
  
3.  **保存**を選びます。  
  
 ソリューションの保存後、必須でないフィールドに情報を追加することができます。 これらの手順は任意です。 **説明**フィールドを使用してソリューションを説明し、ソリューションの**構成ページ**として HTML Web リソースを選択します。 構成ページは通常、ソリューションを配布する ISV が使用します。 これを設定すると、**情報**ノードの下に新しい**構成**ノードが表示され、この Web リソースが表示されます。 開発者はこのページを使用して、指示やコントロールを含めるので、構成データを設定したり、これらのソリューションを立ち上げたりすることができます。  
  
<a name="BKMK_AddSolutionComponents"></a>

## <a name="add-solution-components"></a>ソリューション コンポーネントの追加

 ソリューションを作成した後は、ソリューション コンポーネントはまったく含まれていません。 ソリューションに追加する新たなコンポーネントの作成や、既存のコンポーネントを新たなソリューションに追加することができます。
 
 ### <a name="create-components-in-a-solution"></a>ソリューションに新しいコンポーネントを作成する

 **新規** コマンドを使用して、さまざまなタイプのコンポーネントを作成することができます。 選択したコンポーネントの種類によって、この先の作成エクスペリエンスは異なります。 作成が完了したコンポーネントはそのソリューションに追加されます。 
 
> [!div class="mx-imgBorder"]  
> ![ソリューションに新しいコンポーネントを作成する](media/solution-new-component.PNG "ソリューションに新しいコンポーネントを作成する")  
 
 ### <a name="add-an-existing-component-to-a-solution"></a>既存のコンポーネントをソリューションに追加する
 
 ソリューションが既定ではなくアンマネージドの場合、 **既存を追加** コマンドを使用してソリューション内にすでに存在するコンポーネントを取り込みます。  
 
> [!div class="mx-imgBorder"]  
> ![既存のコンポーネントをソリューションに追加する](media/solution-add-existing-component.PNG "既存のコンポーネントをソリューションに追加する")  

> [!NOTE]
> 既存のコンポーネントのリストは、環境にインポートされたバージョンとソリューションによって異なります。 
  
**すべてのコンポーネントを含める**や**エンティティメタデータを含める**を選択せずに、既存のエンティティを追加するには、**コンポーネントの選択**オプションを使用して、更新されたエンティティ コンポーネントのみを追加します。 ソリューションのセグメント化では、すべての資産を含むエンティティ全体ではなく、選択したエンティティ資産 (エンティティ フィールド、フォーム、ビューなど) をソリューション アップデートと共にエクスポートできます。 [エンティティ資産を使用してセグメント化したソリューションを作成](#create-a-segmented-solution-with-entity-assets)

 カスタマイズの多くには、エンティティが関係します。 現在のソリューション内で全てのエンティティの一覧を表示するには **エンティティ** フィルターを使用します。それは何らかの方法でカスタマイズすることもできます。 下記に示す取引先企業エンティティのスクリーンショットのように、エンティティを開くとその一部であるコンポーネントが表示されます。 
   
> [!div class="mx-imgBorder"]  
> ![展開済みの取引先企業エンティティを表示したデモ ソリューション](media/solution-entity-account.png "展開済みの取引先企業エンティティを表示したデモ ソリューション")  
  
<!--
When you do this you may see a **Missing Required Components** dialog.  
   
 ![Add Required Components Dialog](media/crm-itpro-cust-addrequiredcomponents.PNG "Add Required Components Dialog")  
  
 This dialog alerts you that the solution component has dependencies on other solution components. If you select **No, do not include required components**, the solution may fail if you import it into another organization where all those required components do not exist. If the solution import succeeds, the behavior in the other solution may not be identical as the original organization because the components are configured differently than those in the source solution.  
  
When you select entity components, we recommend that you use solution segmentation so that you only include entity components that are new or updated when you distribute solution updates. With solution segmentation, you work in a solution with selected entity assets, such as entity fields, forms, and views, rather than entire entities with all the assets. More information: [Use segmented solutions](use-segmented-solutions-patches-simplify-updates.md)
  
 If you don’t intend to export the solution, or if you only intend to export it as an unmanaged solution and import it back into the same organization, it isn’t necessary to include required components. If you ever export the solution you’ll see another warning indicating that some required components are missing. If you are only going to import this solution back into the same organization, it is OK to disregard this warning. The steps to edit application navigation or the ribbon without using a third-party editing tool expect that you’ll export the solution back into the same organization.-->  

## <a name="publish-changes"></a>変更の公開 

環境で管理されていない変更を行うと、フォーム、エンティティ、モデル駆動型アプリ、サイトマップ、ビューなどの一部のコンポーネントが非公開の状態で保存されます。 公開アクションを使用すると、これらの変更をアクティブ状態に昇格し、エンド ユーザーの利用と、エクスポートが可能となります。 
 
### <a name="publish-your-customizations"></a>カスタマイズの公開

1.  左のナビゲーション ウィンドウから、**ソリューション**を選択します。

2.  公開するソリューションを選択して開きます。

3.  コマンドの一覧から、**すべてのカスタマイズの公開**を選びます。  

![すべてのカスタマイズの公開](media/publish-all-customizations.PNG "すべてのカスタマイズの公開")  
  
> [!IMPORTANT]
>  カスタマイズの準備には時間がかかることがあります。 ブラウザーのページが反応しなくなっているというメッセージが表示された場合は、閉じないで、ページが反応する状態になるまで待機します。  

## <a name="solution-publisher"></a>ソリューション発行者
作成したアプリや加えたカスタマイズもソリューションの一部です。 すべてのソリューションには発行者がいます。 ソリューションを作成する際に発行元を指定します。 

ソリューション発行者とは、アプリの開発者を意味します。 このため、分かりやすいソリューション発行者を作成する必要があります。 ソリューションの発行者は、Power Apps の **ソリューション** エリアで **設定** を選択すると確認できます。 ソリューション発行者の詳細については、Power Platform ALM ガイドに記載の[ソリューション発行者](/power-platform/alm/solution-concepts-alm#solution-publisher)を参照してください。

> [!NOTE]
> **Common Data Services 既定のソリューション**が**Common Data Service の既定のパブリッシャー**に関連付けられています。 既定のカスタマイズ接頭辞はこの発行者に対してランダムに割り当てられます。例えば `cr8a3` などです。 つまり、組織のために作成された新しいメタデータの項目名は、項目を一意に識別するために使用される名前の前にこれを追加します。

### <a name="create-a-solution-publisher"></a>ソリューション発行者の作成
1.  Power Apps ポータルで、 **ソリューション**を選択します。 
2.  コマンドバーで、**新しいソリューション** を選択し、右側のウインドウの **発行元** ドロップ ダウン リストから **+発行元** を選択します。 
    > [!div class="mx-imgBorder"] 
    > <img src="media/create-new-pubisher.png" alt="Create a new publisher" height="738" width="400">
3.  **新しい発行元** のフォームで、必要な情報とオプション情報を入力します。 
   - **表示名**: 発行元の表示名称を入力します。 
   - **名前**. 発行元の一意の名称を入力します。 
   - **接頭辞**:  お好みの発行元の接頭辞を入力します。 
   -    **オプション値の接頭辞**。 このフィールドは、発行元の接頭辞に基づいた番号を生成します。 この番号は、オプション セットにオプションを追加する際に使用し、オプションを追加するのに使用したソリューションを識別する助けとなります。 
   - **取引先担当者の詳細**。 オプションで、連絡先と住所の情報を追加できます。
4. **保存して閉じる**を選択します。

### <a name="change-a-solution-publisher"></a>ソリューションの発行元を変更する
管理されていないソリューションの発行者を変更するには、次の手順に従ってください:
1.  Power Appsポータルで、 **ソリューション** を選択し、 **…** を選択します 変更するソリューションの **設定** を選択します。 
2.  **ソリューション設定** ウィンドウで、 **発行元の編集** を選択します。 
3.  **表示名称** と **接頭辞** フィールドの値を変更します。 **オプション値の接頭辞** フィールドは、発行元の接頭辞に基づいた番号を生成します。 この番号は、オプション セットにオプションを追加する際に使用し、オプションを追加するのに使用したソリューションを識別する助けとなります。 
4.  接頭辞に加えて、 **連絡先** セクションのソリューション発行者の表示名称、連絡先情報、アドレスを変更することもできます。 
5.  **保存して閉じる**を選択します。

## <a name="create-a-segmented-solution"></a>セグメント化されたソリューションを作成する

ソリューションのアップデートを配布するときに更新されるエンティティ コンポーネントのみを含めるように、ソリューションのセグメンテーションを使用します。 詳細については、Power Platform ALM ガイドに記載の[セグメント化されたソリューションを使用する](/power-platform/alm/segmented-solutions-alm)を参照してください

### <a name="create-a-segmented-solution-with-entity-assets"></a>エンティティ資産を使用してセグメント化したソリューションを作成 
 セグメント化したソリューションを作成するには、アンマネージド ソリューションの作成と既に更新したコンポーネントのみの追加から開始します。 ウィザード風のセットアップにより、エンティティ資産の追加のプロセスを段階的に進みます。 

たとえば、他のどの環境にも存在しない *カスタムエンティティ* とう名前の新しいカスタムエンティティを作成し、アカウント エンティティに *トップテン* という名前の新しいフィールドを追加したとします。 セグメント化されたソリューションを作成するには、次の手順に従います。 
  
1. Power Apps ポータルに移動し、**ソリューション** を選択します。  
  
2.  **新規ソリューション** を選択してソリューションを作成します。 必須フィールドに情報を入力します。 **作成**を選びます。  
  
3.  作成したソリューションを開きます。 コマンド バーで、**既存を追加** を選択し、次に **エンティティ** を選択します。  
  
4.  **既存のエンティティの追加** ウィンドウで、ソリューションに追加する 1 つ以上のエンティティを選択します。 たとえば、**アカウント** そして **カスタム エンティティ** を選択します。 **次へ**を選択します。  

5.  **エンティティを選択** ウィンドウでは、次を含めるアセットから選択できます。 
    - **すべてのコンポーネントを含める**。 このオプションにはすべてのコンポーネント*かつ*エンティティに関連付けられたメタデータが含まれます。 ビジネス プロセス フロー、レポート、接続、キューなどの他のエンティティまたはエンティティ コンポーネントを含めることができます。 
    - **エンティティ メタデータを含める**。 このオプションにはエンティティに関連付けられたメタデータ*のみ*含まれます。 メタデータには、監査、重複データ検出、変更追跡などのエンティティ属性が含まれます。 
    - **コンポーネントを選択する**。 このオプションを使用すると、フィールド、リレーションシップ、ビジネス ルール、ビュー、フォーム、グラフなど、エンティティに関連付けられている各コンポーネントを個別に選択できます。 
    - コンポーネントは含めないでください。 

      この例では、*カスタム エンティティ* はターゲット環境にインポートされたことはないことから、**カスタム エンティティ** の横で、**すべてのコンポーネントを含める** を選択します。 **アカウント** の下で、**コンポーネントを選択** を選択します。  
      > [!div class="mx-imgBorder"] 
      > ![既存のエンティティの追加](media/add-existing-entities1.png)
  
6.  *トップテン* カスタムフィールドのみがこのアカウント エンティティにとって新しいので、**トップ テン** を選択して、**追加** を選択します。  
     > [!div class="mx-imgBorder"] 
     > ![エンティティ コンポーネントの選択](media/add-existing-entities2.png)

7. **追加** を選択して、コンポーネントをソリューションに追加します。 

### <a name="create-a-segmented-solution-using-solution-explorer"></a>ソリューション エクスプローラーを使用してセグメント化されたソリューションを作成する  
次の図に、エンティティ資産を`Account`エンティティ、`Case`エンティティ、および`Contact`エンティティから選択してセグメント化したソリューションを作成した例を示します。  

> [!NOTE]
> ケース エンティティは、Dynamics 365 Customer Service などの一部の Dynamics 365 アプリケーションに含まれています。 
  
作成したアンマネージド ソリューションを開くことから始めます。 **エンティティ** コンポーネントを選択します。  

 > [!div class="mx-imgBorder"] 
 > ![既存のリソースを追加。](media/solution-segmentation-add-existing-resources-admin.png "既存のリソースを追加。")  
  
 次に、ソリューション コンポーネントを選択します。  
  
 ![ソリューションのコンポーネントを選択。](media/solution-segmentation-select-components-admin.png "ソリューションのコンポーネントを選択。")  
  
 ウィザードに従います。 手順 1 で、アルファベット順に開始して、次のように、最初のエンティティである`Account`エンティティの資産を選択します。  
  
 ![ウィザードを開始します。](media/solution-segmentation-wizard-starts-admin.png "ウィザードを開始します。")  
  
 **フィールド**タブを開き、**取引先企業番号**フィールドを選択します。  
  
 ![取引先企業のエンティティ資産を選択します。](media/solution-segmentation-select-account-assets-admin.png "取引先企業のエンティティ資産を選択します。")  
  
 手順 2 で、**サポート案件**エンティティについて、すべての資産を追加します。  
  
 ![サポート案件のエンティティ資産を選択します。](media/solution-segmentation-select-case-assets-admin.png "サポート案件のエンティティ資産を選択します。")  
  
 手順 3 で、**取引先担当者**エンティティの**記念日**フィールドを追加します。  
  
 ![取引先担当者のエンティティ資産を選択します。](media/solution-segmentation-select-contact-assets-admin.png "取引先担当者のエンティティ資産を選択します。")  
  
 その結果、作成したセグメント化されたソリューションには、`Account`、`Case`、および`Contact`の 3 つのエンティティが含まれます。 各エンティティには選択した資産のみが含まれます。  
  
 > [!div class="mx-imgBorder"] 
 > ![エンティティを含むソリューション。](media/solution-segmentation-solution-entities-admin.png "エンティティを含むソリューション。")

### <a name="see-also"></a>関連項目
 [ソリューションの使用](use-solution-explorer.md)
