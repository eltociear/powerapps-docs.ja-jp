---
title: Power Apps のモデル駆動型アプリのメイン フォーム用 iFrame プロパティ | MicrosoftDocs
description: メイン フォームのiFrameプロパティについて
Keywords: メイン フォーム; iFrame のプロパティ; Dynamics 365
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 06/18/2018
ms.service: powerapps
ms.topic: article
ms.assetid: 1b7e6a0c-18a9-47e2-aa7d-0cffb8c93b19
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 7c4d4348726dfb53b0b54e3a8d86a1809a568b7b
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "2875007"
---
# <a name="iframe-properties-for-model-driven-app-main-forms"></a>モデル駆動型アプリのメイン フォーム用 iFrame プロパティ

iFrameをフォームに追加して、フォーム内の別のWebサイトからコンテンツを統合できます。 

iFrame プロパティを表示するには、以下の手順で作業します。

1.  [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインします。

2.  **データ**を展開して**エンティティ**を選択し、目的のエンティティを選択して**フォーム** タブを選択します。 

3. フォームの一覧で、種類が**メイン**のフォームを開きます。 次に、**挿入**タブで IFRAME を選択して IFRAME のプロパティを表示します。

![iframe-properties](media/iframe-properties.png)


> [!NOTE]
> フォームは、iFrame内に表示されるように設計されていません。  
  
|タブ​​|プロパティ|説明|  
|---------|--------------|-----------------|  
|**一般**|**名前**|**必須**: iFrames を表す一意の名前。 名前には、英数字とアンダースコアのみを使用できます。|  
||**URL**|**必須**: iFrame に表示されるページの URL。|  
||**パラメーターとして、レコードのオブジェクトの種類コードおよび一意の識別子を渡します**|組織、ユーザー、およびレコードに関するデータは iFrame に渡すことができます。 詳細情報: [iFrame へのパラメーターの引き渡し](#pass-parameters-to-iframes) |  
||**ラベル**|**必須**: iFrame に表示されるラベル。|  
||**フォームでラベルを表示する**|ラベルを表示するかどうか。|  
||**サポートされている場合はクロスフレーム スクリプトを制限します**|スクリプトを使用して、Dynamics 365 アプリケーションと対話するために別のサイトからのページを使用することを許可するのは、セキュリティ上のリスクと見なされます。 このオプションを使用して、管理していないページに対して、クロスフレーム スクリプトを制限します。<br /><br />|  
||**既定で表示する**|iFrame の表示は任意で、スクリプトを使用して管理します。 詳細情報: [表示オプション](visibility-options-legacy.md)|
||**モバイルの有効化**|モバイル用 iFrame を有効にするには、チェックボックスを選択します。|  
|**形式**|**コントロールが使用する列数を指定してください**|iFrame を含むセクションに複数の列があるとき、フィールドがセクションにある列の数まで占めるように設定できます。|  
||**コントロールが使用する行数を指定してください**|コントロールが占める列数を指定することで、iFrame の高さを制御できます。|  
||**自動拡張して、使用可能なスペースを広げます**|最高値を設定するのではなく、iFrame の高さが使用可能なスペースに拡張されるようすることができます。|  
||**iFrame のスクロールの種類を選択してください**|次の 3 つのオプションがあります。<br /><br /> - **必要に応じて**: iFrame のサイズが使用できるサイズより大きい場合、スクロールバーが表示されます。<br />- **常に**: スクロールバーを常に表示します。<br />- **しない**: スクロールバーは表示されません。|  
||**境界の表示**|iFrame の周りに境界を表示します。|  
|**依存関係**|**依存フィールド**|iFrame がスクリプトを使用してフォームのフィールドと対話することがあります。 フィールドがフォームから削除されると、iFrame のスクリプトが破損することがあります。 iFrame のスクリプトで参照されるフィールドはすべて**依存フィールド**にフィールドに追加して、誤って削除されないようにします。|  
  
## <a name="pass-parameters-to-iframes"></a>iFrame へのパラメーターの引き渡し  
 レコードについての情報は、**パラメーターとして、レコードのオブジェクトの種類コードおよび一意の識別子を渡します**オプションを有効にすることで、渡すことができます。 渡される値は次のとおりです。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`orglcid`|組織の既定の言語の LCID。|  
|`orgname`|組織の名前。|  
|`userlcid`|ユーザーが指定した言語の LCID|  
|`type`|エンティティの種類コード。 この値は、異なる組織のユーザー定義エンティティでは異なります。 `typename` を代わりに使用します。|  
|`typename`|エンティティの種類名。|  
|`id`|レコードの ID 値。 エンティティ レコードを保存するまで、このパラメーターには値がありません。|  

## <a name="next-steps"></a>次のステップ

[メイン フォームとそのコンポーネントの使用](use-main-form-and-components.md)
