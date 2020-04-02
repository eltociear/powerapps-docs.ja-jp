---
title: 管理ソリューションのマージ方法 (Common Data Service) | Microsoft Docs
description: 複数のインストールされたソリューションが互いに干渉しないようにするには、ソリューションの構築中にベストプラクティスに従います。
ms.custom: ''
ms.date: 02/27/2020
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: shmcarth
ms.author: jdaly
manager: ryjones
search.audienceType:
- maker
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 7b6a5d741179c26799badfd6c7427e06941f5851
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2020
ms.locfileid: "3108457"
---
# <a name="understand-how-managed-solutions-are-merged"></a>管理ソリューションのマージ方法について

管理ソリューションをインストールする準備をするときは、環境に複数のソリューションがインストールされているか、将来的に他のソリューションがインストールされる可能性があることに注意してください。 ソリューションをベスト プラクティスに従って構築して、他のソリューションと競合しないようにします。  
  
Common Data Service のカスタマイズをマージするプロセスは、ソリューションの機能を保持することに重点が置かれています。 プレゼンテーションを保持するためにあらゆる処理が行われても、カスタマイズ間に非互換性があると、カスタマイズの機能を保持することが優先されて、プレゼンテーションの細部が変更されることがあります。  
  
<a name="BKMK_MergingFormCustomizations"></a>   

## <a name="merge-form-customizations"></a>フォームのカスタマイズのマージ  
 マージが必要なフォームのカスタマイズは、すでに環境内にあるエンティティ フォームに対して実行されるカスタマイズのみです。 つまり、通常は、Common Data Service のインストール時に作成されたエンティティ用に含まれているフォームをソリューションでカスタマイズする場合にのみ、フォームのカスタマイズをマージする必要があります。 フォームのマージを回避する方法の 1 つとして、どの Common Data Service エンティティにも新しいフォームを提供します。 カスタム エンティティ用のフォームをマージする必要があるのは、カスタム エンティティとそのフォームを作成した既存のマネージド ソリューションを更新または変更するソリューションを作成する場合に限られます。  
  
 ソリューションをマネージド ソリューションとしてパッケージすると、FormXML に格納されているフォーム定義と元の FormXML とが比較され、相違点のみがそのマネージド ソリューションに取り込まれます。 その管理ソリューションを新しい環境にインストールすると、フォーム カスタマイズの相違点が既存のフォームの FormXML とマージされて、新しいフォーム定義が作成されます。 ユーザーに表示されるフォーム定義は、この新しい方のフォーム定義で、システム カスタマイザーが変更できるのも、この新しいフォーム定義です。 このマネージド ソリューションをアンインストールすると、その中に取り込まれていた相違するフォーム要素のみが削除されます。  
  
 マージするフォームに新しい要素を追加するときは、新しい要素を新しいコンテナー要素 (タブまたはセクション) に含めることをお勧めします。 要素はコンテナーの最下部に追加されます。 たとえば、フィールドをセクションに追加すると、そのフィールドはセクションの最下部に配置されます。 ソリューションをインストールするカスタマイザーは、インストール後にフォームを変更して、要素を再配置することが予想されます。  
  
 マネージド ソリューションに含まれるフォームで新しいセキュリティ ロールを使用していると、そのマネージド ソリューションは、それらのセキュリティ ロールに依存します。 そのようなセキュリティ ロールがある場合は、マネージド ソリューションと共に含める必要があります。 管理ソリューションがインストールされている環境にないフォームに関連付けられたセキュリティ ロールがある場合、インストールは失敗しませんが、フォームはどのセキュリティ ロールにも関連付けられません。 マネージド ソリューションをアンインストールすると、そのマネージド ソリューションに付属するセキュリティ ロールもすべて削除されます。 その後、それらのセキュリティ ロールにマネージド ソリューション外のフォームを関連付けることはできません。  
  
> [!NOTE]
>  管理ソリューション エンティティに複数のフォームがあり、環境エンティティ フォームにも複数のフォームがある場合、新しいフォームは、使用可能なフォーム一覧の最後に追加されるのではなく、元のエンティティ フォームに挿入されます。  
  
<a name="BKMK_MergingNavigationCustomizations"></a>   
## <a name="merge-navigation-sitemap-customizations"></a>ナビゲーション (サイト マップ) のカスタマイズのマージ  
 ソリューションをマネージド ソリューションとしてパッケージすると、そのサイトマップ XML は、元のサイトマップ XML とそのサイトマップに加えられた他のカスタマイズと比較されます。 マネージド ソリューションには相違点のみ取り込まれます。 これらの違いには、変更、移動、追加、または削除されたアイテムなどが含まれます。 管理ソリューションを新しい環境にインストールすると、SiteMap の変更は、管理ソリューションがインストールされている環境で見つかった SiteMap XML とマージされます。 ユーザーに表示されるのは、新しいサイトマップ定義です。  
  
 この時点で、カスタマイザーは、サイトマップをアンマネージド ソリューションにエクスポートでき、そのサイトマップの定義には、アクティブなサイトマップのすべての要素が取り込まれます。 カスタマイザーは、SiteMap を変更し、アンマネージド カスタマイズとして再インポートできます。  後で、このマネージド ソリューションをアンインストールすると、このマネージド ソリューションと共にインポートされたサイトマップ XML は、このマネージド ソリューションと共に追加された変更を削除するために参照されます。 新しいアクティブなサイトマップが計算されるのはその後です。  
  
 サイトマップに追加される新しい可視要素は、常に、その要素が属するコンテナーの最下部に表示されます。 たとえば、新しい領域を追加すると、ナビゲーション領域の最下部に表示されます。 追加された要素を適切な場所に配置するには、まず、サイトマップをエクスポートして、正確な位置を設定するように編集する必要があります。その後、さらに、そのサイトマップをアンマネージド ソリューションとして再度インポートする必要があります。  
  
> [!NOTE]
>  公開間に適用できるサイトマップのカスタマイズは 1 つのみです。 未公開のサイトマップのカスタマイズは、新しいサイトマップの定義がインポートされると失われます。  
  
<a name="BKMK_MergingOptionSetOptions"></a>   
## <a name="merge-option-set-options"></a>オプション セット オプションのマージ  
 新しい各オプション セット オプションは、接頭辞付きのオプション値を含む、割り当て済み整数値によって初期化されます。 オプション値の接頭辞は、オプション値の前に追加される 5 桁の数字です。 オプション値の接頭辞は、ソリューション発行者のカスタマイズによる接頭辞に基づいて生成されますが、任意の値に設定することもできます。 オプション値の接頭辞があることで、特定のソリューション発行者のコンテキストで作成された新しいオプション セット オプションを区別しやすく、オプション値が競合する可能性を容易に低減できます。 オプション値の接頭辞の使用は必須ではありませんが、使用することをお勧めします。  
  
 管理ソリューションは、通常、取引先企業のカテゴリや業種オプション セットなど、環境内の既存のオプション セットのオプションを更新または追加します。 管理ソリューションでオプション セット内の使用可能なオプションを変更すると、その管理ソリューションに定義されているすべてのオプションが環境内で使用できるようになります。 そのマネージド ソリューションをアンインストールすると、オプション セットは元の状態に戻ります。  
  
### <a name="see-also"></a>関連項目  

[ソリューションの概要](solutions-overview.md)  <br />
[エクスポート ソリューション](export-solutions.md) <br />
[サイト マップ デザイナーを使用してモデル駆動型アプリのサイト マップを作成する](../model-driven-apps/create-site-map-app.md)