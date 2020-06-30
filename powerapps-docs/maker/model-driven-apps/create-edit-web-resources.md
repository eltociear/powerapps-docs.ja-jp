---
title: Power Apps でモデル駆動型アプリ Web リソースを作成、編集する | MicrosoftDocs
description: Web リソースの作成または編集の方法を学習する
ms.custom: ''
ms.date: 06/02/2018
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
ms.assetid: ef4ba8df-9ba9-4066-b40d-def9761c7de2
caps.latest.revision: 21
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 449eaf5f299c3b6272bc3cdf7ff2ff09d4b728cc
ms.sourcegitcommit: 909948d219c3c61d617f13aceb355e1d5bcb0b55
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2020
ms.locfileid: "3432709"
---
# <a name="create-or-edit-model-driven-app-web-resources-to-extend-an-app"></a>モデル駆動型アプリ Web リソースを作成または編集してアプリを拡張

Web リソースは、通常、Web 開発で使用されるファイルを使用してアプリを拡張するために、開発者によって使用されます。 アプリ ユーザーとして、開発者またはデザイナーによって提供される Web リソースを管理する必要がある場合があります。  

> [!TIP]
> Web リソースの包括的な説明については、 [開発者ドキュメント: モデル駆動型アプリ の Web リソース](/powerapps/developer/model-driven-apps/web-resources) を参照してください。
   
<a name="BKMK_WhatAreWebResources"></a>

## <a name="what-are-web-resources"></a>Web リソースとは。  

Web リソースは、システムに格納される仮想ファイルです。 各 Web リソースは、ファイルを取得するために URL で使用できる一意の名前を持ちます。 このように考えてください。Web アプリを実行する実際の Web サーバーにアクセスした場合、その Web サイトにファイルをコピーできます。 しかし、ほとんどのオンライン サービスでは、そうすることはできません。  代わりに、Web リソースを使用してシステムにファイルをアップロードし、ファイルとして Web サーバーにコピーしたかのように、名前によって参照することができます。  
  
たとえば、"new_myWebResource.htm" という名前の Web リソースとして HTML ページを作成する場合は、次のような URL を使用して、ブラウザーでそのページを開くことができます。  
 
`<base URL>/WebResources/new_myWebResource.htm`
  
*\<base URL>* は、アプリを閲覧する際に使用する URL のうち、`dynamics.com` で終わる部分です。 Web リソースはシステムにあるデータなので、組織でのライセンスを受けたユーザーのみが、この方法でアクセスできます。 通常、Web リソースは、直接参照されるのではなく、フォームに含まれています。 最も一般的な使用方法は、フォーム スクリプトの JavaScript ライブラリを提供することです。  
    
Web リソースはシステム内のデータであり、ソリューションに対応しているため、ソリューションの一部としてエクスポートして、別の組織にソリューションをインポートすることによって、別の組織に移動させることができます。 Web リソースを使用するには、ソリューション エクスプローラーを使用する必要があります。
  
## <a name="solution-publisher-prefix"></a>ソリューション発行者の接頭辞

作成する Web リソースの名前の一部はソリューション発行者の接頭辞です。 これは、作業中のソリューションの発行者に基づいて設定されます。 発行者の接頭辞がこの Web リソースに必要なアンマネージド ソリューションで作業していることを確認してください。 詳細 : [ソリューション発行者](../common-data-service/create-solution.md#solution-publisher)  

## <a name="view-and-add-web-resources"></a>Web リソースの表示と追加
1. [Power Apps](https:///?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインし、左側のナビゲーション ウィンドウから**ソリューション**を選択します。 
2. アンマネージド ソリューションを開き、コマンドバーで**既存を追加する**を選択します。**その他**を選択し、続いて**Web リソース**を選択します。 
   使用可能な Web リソースの一覧が表示されます。 
3. アンマネージド ソリューションに Web リソースを追加するには、Web リソースを選択してから、**追加**を選択します。 Web リソースを追加せずにリストを閉じるには、**キャンセル**を選択します。 

## <a name="create-a-web-resource"></a>Web リソースを作成する

1. [Power Apps](https:///?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインし、左側のナビゲーション ウィンドウから**ソリューション**を選択します。 
2. アンマネージド ソリューションを開き、コマンドバーで**新規**を選択します。**その他**を選択し、続いて**Web リソース**を選択します。 
3. フォームを完了して Web リソースを作成します :

    ![Web リソースを作成する](media/new-web-resource-form.png)
  
|フィールド|内容|  
|-----------|-----------------|  
|**名前**|*必須*。 これは、Web リソースの一意の名前です。 いったん Web リソースを保存したら、これを変更することはできません。<br />&bull; この名前には、文字、数字、ピリオド、および連続していないスラッシュ (“/”) のみを含めることができます。<br /> &bull; Web リソース名の先頭に、ソリューション発行者のカスタマイズ接頭辞が追加されます。|  
|**表示名**|Web リソースの一覧を表示すると、この名前が表示されます。|  
|**説明**|Web リソースの説明です。|  
|**種類**|*必須*。 これは、Web リソースの種類です。 いったん Web リソースを保存したら、これを変更することはできません。|  
|**テキスト エディター**|Web リソースの種類が一種のテキスト ファイルを表す場合は、このボタンを選択してページを開き、テキスト エディターを使用してコンテンツを編集します。<br />詳細: [テキスト エディターの適切な使用](#use-the-text-editor-appropriately)| 
|**言語**|言語を選択できます。 このオプションは、Web リソースのデータが格納されているレコードをタグ付けするだけです。 Web リソースの動作は変更されません。|  
|**ファイルのアップロード**|**参照...** を選択します。 を押して、Web リソースとしてアップロードするファイルを選択します。<br />&bull; 新しい Web リソースを作成する場合、または、既存の Web リソースを上書きする場合に、ファイルをアップロードすることができます。<br />&bull; ファイル名の拡張子は、許可されている拡張子と一致していなければなりません。<br />&bull;デフォルトでは、Web リソースとしてアップロードできるファイルの最大サイズは 5 MB です。 この値は、 **システム設定** > **電子メール** タブ > **添付ファイルのサイズ制限の設定** の設定を使用して変更できます。 詳細: [[システムの設定] ダイアログ ボックス - [電子メール] タブ](https://docs.microsoft.com/dynamics365/customer-engagement/admin/system-settings-dialog-box-email-tab) |  
|**URL**|Web リソースを保存した後、Web リソースへの URL がここに表示されます。 ブラウザーで Web リソースを表示するには、このリンクを選択します。|  
  
4. 変更を追加した後、**保存**を選択し、続いて**公開**を選択します。  

## <a name="edit-a-web-resource"></a>Web リソースを編集する
アンマネージド ソリューションを開き、編集する Web リソースを選択します。 


> [!NOTE]
> Web リソースへの変更は、公開するアプリケーションに表示されません。
  
### <a name="use-the-text-editor-appropriately"></a>テキスト エディターの適切な使用

Web リソース用のアプリケーションで提供されているテキスト エディターは、テキスト ファイルの簡単な編集のみに使用する必要があります。 HTML Web リソースの作成と編集に使用することができますが、テキスト エディターを使って作成された HTML Web リソース以外は編集しないでください。 テキスト エディターは、非常に単純な HTML コンテンツ用に設計されています。 

> [!IMPORTANT]
> テキスト エディターを使用して作成された HTML Web リソース コンテンツでない場合は、編集にテキスト エディターを使用しないでください。  
> テキスト エディターでは、編集することができるように HTML のソースを変更するコントロールが使用されます。 これらの変更は、ブラウザーでのページの動作を変え、より高度なコードの動作を停止させる場合があります。 テキスト エディターで HTML Web リソースを開き、変更を加えずに保存すると、いくつかの HTML Web リソースが壊れる可能性があります。  <!--More information: [Developer Documentation: Use the text editor for HTML web resources](/dynamics365/customer-engagement/developer/webpage-html-web-resources#use-the-text-editor-for-html-web-resources)  -->
  
外部エディターを使用してテキスト ファイルを編集し、それらをアップロードする前に、**ファイルのアップロード**ボタンを使ってローカルで保存することをお勧めします。 このようにすると、以前のバージョンに戻す必要がある場合に、Web リソースのコピーを保持することができます。 メモ帳のような単純なエディターを使用することもできますが、より高度な機能を備えたテキスト エディターを使用することを強くお勧めします。 [Visual Studio コミュニティ ](https://www.visualstudio.com/vs/community/) および [Visual Studio コード](https://code.visualstudio.com/)   

## <a name="create-and-edit-a-web-resource-on-a-form-using-solution-explorer"></a>ソリューション エクスプローラーを使用して、フォーム上の Web リソースを作成して編集する

ユーザーにとってさらに魅力的で便利になるように、フォーム上の Web リソースを追加または編集できます。 

> [!NOTE]
> web リソースはフォーム ヘッダーまたはフッターに含めることができません。  

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

### <a name="navigate-to-a-form"></a>フォームに移動する
ソリューション エクスプローラーを開いた状態で、**コンポーネント**の下の**エンティティ**を展開し、作業するエンティティを展開します。

**フォーム**を選択し、一覧内で種類がメインのフォームを探し、オープンするエントリをダブルクリックまたはタップし、フォームを編集します。

### <a name="add-or-edit-web-resource-in-a-form"></a>フォームの Web リソースの追加または編集

フォームでの Web リソースに設定するプロパティに関する情報については、「[Web リソースのプロパティ](web-resource-properties-legacy.md)」を参照してください。

### <a name="preview"></a>プレビュー​​

メイン フォームの表示とイベントの動作をプレビューするには以下を実行します。
- **ホーム**タブで**プレビュー**を選択してから、**フォームの作成**、**フォームの更新**、または**読み取り専用**を選択します。
- [プレビュー] フォームを閉じるには、**ファイル**メニューで、**閉じる**を選択します。

### <a name="save"></a>保存

フォームの編集が終了したら、**ホーム**タブで、**保存して閉じる**を選択して、フォームを閉じます。 

### <a name="publish"></a>Publish

カスタマイズが完了したら、公開します。
- 現在編集中のコンポーネントのみのカスタマイズを公開するには、ナビゲーション ウィンドウで、取り組んでいるエンティティを選択してから、**公開**を選択します。
- 非公開のすべてのコンポーネントのカスタマイズを一度に公開するには、ナビゲーション ウインドウで、**エンティティ**を選択し、**操作**ツールバーで、**全てのカスタマイズの公開**を選択します。
   
  
### <a name="see-also"></a>関連項目  

[Web リソースのプロパティ](web-resource-properties-legacy.md) <br /> 
[フォームの作成および設計](create-design-forms.md) <br />
[モデル駆動型アプリのコンポーネントについて](model-driven-app-components.md) <br /> 
[開発者ドキュメント: モデル駆動型のアプリケーションでWebリソース](/powerapps/developer/model-driven-apps/web-resources)
