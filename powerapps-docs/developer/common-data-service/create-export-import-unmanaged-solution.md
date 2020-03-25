---
title: アンマネージド ソリューションの作成、エクスポート、インポート (Common Data Service) | Microsoft Docs
description: アンマネージド ソリューションは、アンマネージド カスタマイズのセットを組織間で転送可能なセットにグループ化する方法として役立ちます。
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: shmcarth
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8a525320894a280bb8a092892180879f3bf626ea
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2020
ms.locfileid: "3109050"
---
# <a name="create-export-or-import-an-unmanaged-solution"></a>アンマネージド ソリューションの作成、エクスポート、またはインポート

アンマネージド ソリューションは、マネージド ソリューションの作成に必須であるだけでなく、一連のアンマネージド カスタマイズを組織間でやり取りする 1 つのセットにグループ化する手段としても有効です。  

 詳細: [カスタマイズでのソリューションの使用](/dynamics365/customer-engagement/developer/customize/use-solutions-for-your-customizations)。  

<a name="BKMK_CreateUnmanagedSolution"></a> 

## <a name="create-an-unmanaged-solution"></a>アンマネージド ソリューションの作成  
 すべてのソリューションには発行元が必要です。 ソリューションを配布しない場合、組織用に既に作成されている既定の発行元を使用できます。 ソリューションの発行元の作成方法については、[ソリューションの発行元の作成](create-export-import-unmanaged-solution.md#BKMK_CreateSolutionPublisher) を参照してください。  

 ソリューションに含まれるフィールドと説明を次の表に示します。  


|      フィールド ラベル       |                                                                                                                                                              説明                                                                                                                                                               |
|------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    **表示名**    |                                                                                                                                                       ソリューションの名前です。                                                                                                                                                       |
|        **名前**        |                                     Common Data Service は、**表示名** に基づいて一意の名前を生成します。 一意な名前は編集できます。 一意な名前には、英数字とアンダースコアのみを使用できます。                                     |
|     **発行元**      |                                                                                                                                ソリューションを発行元に関連付けるには、**発行元**検索を使用します。                                                                                                                                |
|      **バージョン**       |                                                                                                                     次の形式でバージョンを指定します: major.minor.build.revision (例: 1.0.0.0)。                                                                                                                     |
| **構成ページ** | ソリューションに HTML Web リソースを含める場合、この検索を使用して HTML Web リソースを指定の構成ページとして追加できます。<br /><br /> 詳細: [ソリューション構成ページの使用](create-export-import-unmanaged-solution.md#BKMK_UseSolutionConfigurationPage) |
|    **説明**     |                                                                                                                                  このフィールドを使用して、ソリューションに関する詳細を記入できます。                                                                                                                                   |

 アンマネージド ソリューションを作成した後、ソリューション コンポーネントを追加するには、このソリューションのコンテキスト内でソリューション コンポーネントを作成するか、他のソリューションから既存のコンポーネントを追加します。 ソリューションをプログラムで作成する方法の詳細については、[ソリューションの作成](work-solutions.md#BKMK_CreateASolution)を参照してください  

<a name="BKMK_CreateSolutionPublisher"></a>   

### <a name="create-a-solution-publisher"></a>ソリューション発行者の作成  
 マネージド ソリューションを配布する場合、`Publisher` を作成する必要があります。 `Publisher` に含まれるフィールドと説明を次の表に示します。  


|          ラベル          |                                                                                                                                                                                                       説明                                                                                                                                                                                                        |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    **表示名**     |                                                                                                                                                                       ソリューションの**発行元**検索フィールドに表示する名前です。                                                                                                                                                                        |
|        **名前**         |                               Common Data Service は、**表示名**に基づいて一意の名前を生成します。 一意な名前には、英数字とアンダースコアのみを使用できます。 **注:**  `Unique Name` を使用して `Publisher` を一意に識別することができます。 同じ発行元を共有するマネージド ソリューションは相互に更新できます。                               |
|     **説明**     |                                                                                                                                                                           このフィールドを使用して、ソリューションに関する詳細を記入できます。                                                                                                                                                                            |
|       **接頭辞**        |                   カスタマイズの接頭辞は、ソリューション コンポーネントを追加した発行元を識別するために役立ちます。 たとえば、この発行元に関連付けられたソリューションのコンテキストで作成したエンティティまたは属性の論理名に接頭辞が追加されます。 接頭辞は 2 ～ 8 文字で指定する必要があり、英数字のみを使用できます。 ‘mscrm’ で始めることはできません。                   |
| **オプション値の接頭辞** | この値は、統合オプションをサポートするためにオプション セットに追加するオプションを区別するのに役立ちます。 値は、一意性がより確実になるように、**接頭辞**テキストに基づいて自動生成されます。 この値は 10,000 ～ 99,999 にする必要があります。<br /><br /> 詳細: [オプション セット オプションのマージ](/dynamics365/customer-engagement/developer/understand-managed-solutions-merged#BKMK_MergingOptionSetOptions) |
|   **取引先担当者の詳細**   |                                                                                                                                                           これらのフィールドを使用して、ソリューションのインストール担当者が連絡をとるための情報を追加します。                                                                                                                                                           |

 発行元をプログラムで作成する方法については、[発行元の作成](work-solutions.md#BKMK_CreatePublisher) を参照してください。  

<a name="BKMK_UseSolutionConfigurationPage"></a>   
### <a name="use-the-solution-configuration-page"></a>ソリューション構成ページの使用  
 ソリューション構成ページは、情報を表示したり、ソリューションのコンテキストで顧客が操作できるようにするためのキャンバスです。 構成ページを設定するには、**構成ページ**検索フィールドを使用して、ソリューションに含まれている Web ページ (HTML) の Web リソースを選択します。 これにより、**構成**ノードが**情報**ノードの下の [ソリューション] ウィンドウと**コンポーネント**ノードに表示されます。 **構成**ノードに、設定した Web リソースが表示されます。
 
 > [!NOTE]
>  ソリューションの構成ページは、現在クラシック モードでのみアクセスすることができます。

 ソリューション構成ページで、ソリューションを構成するコントロールを表示できます。 たとえば、ソリューションに、ソリューションの動作を制御するエンティティを設定できます。 データ アクセスの Web API を使用して Web リソース ページにカスタム コントロールを設定することで、これらのエンティティのデータを更新することができます。  

<a name="BKMK_UnmanagedSolution"></a>   
## <a name="export-an-unmanaged-solution"></a>アンマネージド ソリューションのエクスポート  
 次のような場合には、アンマネージド ソリューションをエクスポートできると便利です。  

- たとえば、サイトマップの編集やカスタマイズされたリボンの作成を行う場合。この場合には customizations.xml ファイル内の XML コンテンツを編集する必要があります。  

- アンマネージド ソリューションを組織間で転送する場合。  

- 現在のカスタマイズ セットのバックアップを作成する場合。  

  アンマネージド ソリューションをエクスポートすると、圧縮 (zip) ファイルが作成されます。この圧縮ファイルを他の組織または同じ組織にインポートできます。  

  ソリューションをエクスポートするとき、公開済みのカスタマイズのみが含まれるので、ソリューションをエクスポートする前にかならず変更を公開してください。  

  Web アプリケーションを使用してソリューションをエクスポートするとき、ソリューションに不足している必須コンポーネントが含まれている場合は、**不足している必須コンポーネント**の手順を参照してください。 アンマネージド ソリューションとしてこれを元の組織にインポートする場合は、この警告を無視できます。 それ以外は、ダイアログ ボックスの指示に従って、エクスポートをキャンセルし、必須コンポーネントを追加します。  

  ソリューションをプログラムでエクスポートするには、<xref:Microsoft.Crm.Sdk.Messages.ExportSolutionRequest> メッセージを使用します。 詳細: [ソリューションのエクスポートまたはパッケージ化](work-solutions.md#BKMK_ExportPackageSolution)  

  **システム設定のエクスポート (詳細)** ステップで Web アプリケーションを使用してソリューションをエクスポートするとき、ソリューションに含めるシステム設定を選択できます。 これらのオプションは、要求で使用できるメンバーを介して、 <xref:Microsoft.Crm.Sdk.Messages.ExportSolutionRequest> を使用して開発者が使用できます。 どちらの設定を含めるかの詳細に対する要求についての注釈を参照してください。  

  <!--You can pick a target version when you export a solution. You can export a solution that is compliant with earlier versions. More information: [Export a solution for a specific Dynamics 365 version](export-solution-specific-version.md).-->  

<a name="BKMK_ImportUnmanagedSolution"></a>   
## <a name="import-an-unmanaged-solution"></a>アンマネージド ソリューションのインポート  
 次のような場合には、アンマネージド ソリューションをインポートする必要があります。  

- 一連のカスタマイズを組織間で転送し、ソリューション コンポーネントを変更できるようにする場合。  

- 以前のソリューション コンポーネント定義セットに戻す場合。  

  アンマネージド ソリューションのインポートは追加プロセスです。 古いバージョンのマネージド ソリューションをインポートしても、新しいバージョンに含まれるソリューション コンポーネントは削除されません。 ただし、ソリューション コンポーネント プロパティの定義は、最後にインポートしたアンマネージド ソリューションに含まれる定義で上書きされます。  

> [!IMPORTANT]
>  アンマネージド ソリューションのインポートによって適用された変更はアンインストールできません。 変更をロールバックできるようにする場合は、アンマネージド ソリューションをインストールしないでください。  

 この操作をプログラムで実行するには、<xref:Microsoft.Crm.Sdk.Messages.ImportSolutionRequest> メッセージを使用します。 このメッセージを非同期に実行するコードを作成できます。 詳細: [バックグラウンドのメッセージを実行する (非同期)](/dynamics365/customer-engagement/developer/org-service/use-messages-request-response-classes-execute-method#bkmk_executeasync)。 インポートの進行状況を追跡する場合、またはインポートの成功に関するレポートを生成する場合は、`ImportJob` エンティティを使用します。 詳細: [ソリューションのインストールまたはアップグレード](work-solutions.md#BKMK_InstallUpgradeSolution)  

> [!IMPORTANT]
>  ソリューションのインストールやカスタマイズの発行は、通常のシステム操作に影響を与える可能性があります。 ユーザーに対する影響が最小であるうちに、ソリューションのインポートを予定することを推奨します。  

<a name="BKMK_MaxSizeOfSolution"></a>   
### <a name="maximum-size-of-solution-to-import"></a>インポートするソリューションの最大サイズ  
 Common Data Service の場合、ソリューションの最大サイズは 29.296 MB です。  

 設置型の組織の場合、ソリューションの既定の最大サイズは 6 MB ですが、この値は必要に応じて増やすことができます。  

 最大許容サイズを変更するには、アプリケーションの web.config ファイル内の [\<httpRuntime>](https://msdn.microsoft.com/library/e1f13641\(v=vs.100\).aspx) 要素を編集します。 必要なサイズを許容するには、`executionTimeout` 属性と `maxRequestLength` 属性を編集します。 ソリューションのインストールが完了した後、必要なサイズに設定できます。  

### <a name="see-also"></a>関連項目  
 [ソリューション開発の計画](/dynamics365/customer-engagement/developer/plan-solution-development)   
 [Dynamics 365 ソリューションを使用した拡張機能のパッケージ化および配布](/dynamics365/customer-engagement/developer/package-distribute-extensions-use-solutions)   
 [カスタマイズ ソリューション ファイルのスキーマ](/dynamics365/customer-engagement/developer/customize-dev/customization-solutions-file-schema)   
 [マネージド ソリューションの作成、インストール、および更新](create-install-update-managed-solution.md)   
 [ソリューションのアンインストールまたは削除](uninstall-delete-solution.md)
