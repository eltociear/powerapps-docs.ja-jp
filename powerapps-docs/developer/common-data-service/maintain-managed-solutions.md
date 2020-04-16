---
title: 管理ソリューションの維持 (Common Data Service) | Microsoft Docs
description: ''
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
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
ms.openlocfilehash: 48f614c7e938dc243ac0780c7387ea91a1926795
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156147"
---
# <a name="maintain-managed-solutions"></a>管理ソリューションの保守

マネージド ソリューションをリリースする前に、その運用と保守の方法を検討する必要があります。 エンティティや属性が含まれる場合、マネージド ソリューションのアンインストールおよび再インストールを選択することは、事実上できません。 これは、エンティティが削除されるとデータが失われてしまうためです。 しかし、ソリューションには、データを保持しながらマネージド ソリューションを更新する方法があります。 ソリューションの更新方法は、ソリューションの特性と変更の要件にまさに依存します。  

<a name="BKMK_VersionCompatibilty"></a>   

## <a name="version-compatibility"></a>バージョン互換性  
 Common Data Service の新バージョンからエクスポートしたソリューションは、Dynamics 365 の旧バージョンにインポートできません。 これにはメジャー バージョンとマイナー バージョンが含まれます。 次の表に示すように、旧バージョンの Dynamics 365 からエクスポートされたソリューションは、それ以降のバージョンにインポートできます。  
  
![ソリューション バージョンの互換性](media/crm_v9.0_solution_compatibility_chart.png)
  
 追加の更新プログラムのロールアップまたはサービス更新が Common Data Service に適用されると、これらの更新を使用した組織からエクスポートされたソリューションは、これらの更新をしていない組織にインポートできません。 詳細: [ソリューションの概要](introduction-solutions.md)。  
  
 `<ImportExportXml>` ルート要素は、`SolutionPackageVersion` 属性を使用して、このソリューションと互換性のあるバージョンの値を設定します。 この値は、手動で編集することはできません。  
  
<a name="BKMK_CreateManagedSolutionUpdates"></a>   
## <a name="create-managed-solution-updates"></a>マネージド ソリューション更新の作成  
 ソリューションを更新するには 2 つの基本的な方法があります。  
  
-   マネージド ソリューションの新バージョンのリリース  
  
-   マネージド ソリューションの更新プログラムのリリース  
  
<a name="BKMK_ReleaseANewVersion"></a>   
### <a name="release-a-new-version-of-your-managed-solution"></a>マネージド ソリューションの新バージョンのリリース  
 適しているのは、マネージド ソリューションの新バージョンをリリースする方法です。 元のアンマネージド ソース ソリューションを使用して、必要な変更を行い、ソリューションのバージョン番号を大きくして、マネージド ソリューションとしてパッケージ化します。 ソリューションを使用している組織が新バージョンをインストールすると、機能がアップグレードされて、変更が反映されます。 以前のバージョンの動作に戻す必要がある場合は、以前のバージョンを再インストールします。 以前のバージョンの定義でソリューション コンポーネントが上書きされますが、新バージョンで追加されたソリューション コンポーネントが削除されることはありません。 その新しいソリューション コンポーネントはシステムにそのまま残りますが、以前のソリューション コンポーネント定義によって使用されることはないため、影響を及ぼすことはありません。  
  
 以前のバージョンのソリューションのインストールの際には、Common Data Service によって、以前のバージョンをインストールしているユーザーに対して操作の続行が確認されます。  
<a name="BKMK_ReleaseAnUpdate"></a>   
### <a name="release-an-update-for-your-managed-solution"></a>マネージド ソリューションの更新プログラムのリリース  
 ソリューション コンポーネントの小さなサブセットのみを緊急に変更する必要がある場合は、更新プログラムをリリースして問題を解決できます。 更新プログラムをリリースするには、新しいアンマネージド ソリューションを作成し、更新する元のアンマネージド ソース ソリューションからコンポーネントを追加します。 新しいアンマネージド ソリューションを、元のソリューションで使用した発行元と同じ発行元に関連付ける必要があります。 変更が終了したら、新しいソリューションをマネージド ソリューションとしてパッケージ化します。  
  
 元のソリューションがインストールされている組織に更新ソリューションをインストールすると、更新に含まれる変更が組織に適用されます。 組織が元のバージョンに "ロールバック" する必要がある場合は、更新をアンインストールします。  
  
 更新プログラム内のソリューション コンポーネントに適用されたカスタマイズは上書きされます。 更新プログラムをアンインストールすると、それらは元に戻ります。  
  
### <a name="see-also"></a>関連項目  
 [ソリューション開発の計画](/dynamics365/customer-engagement/developer/plan-solution-development)   
 [AppSourceでアプリを公開する](publish-app-appsource.md)
