---
title: モデル駆動型アプリ フォームを作成および設計する | MicrosoftDocs
ms.custom: ''
ms.date: 01/30/2020
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
ms.assetid: 99c795e0-9165-4112-85b1-6b5e1a4aa5ec
caps.latest.revision: 33
ms.author: matp
manager: kvivek
author: Mattp123
tags:
- Links to topic not migrated
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 2e64771257519bded104aa49bde84ac993e1b361
ms.sourcegitcommit: 60a721432b3fa2abd14ccb3bd16a6b34e13ada85
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2020
ms.locfileid: "3026430"
---
# <a name="create-and-design-model-driven-app-forms"></a>モデル駆動型アプリ フォームを作成および設計する 

Power Apps では、フォームは、ユーザーが各自の作業を遂行するために必要なデータとのやり取りに使用するユーザー インターフェイスを提供します。 ユーザーが使用するフォームは、必要とする情報を効率よく検索または入力できるように設計されていることが重要です。 

既定のソリューションまたはアンマネージド ソリューションでは、新しいフォームを作成したり、フォームのカスタマイズが許可されているすべてのエンティティの既存のフォームを編集したりすることができます。 アンマネージド ソリューションでは、ソリューション用に作成されたアンマネージドなユーザー定義エンティティの管理プロパティを編集できます。
マネージド ソリューションの表示中に、新しいフォームを作成したり、ここのエンティティの既存のフォームを編集したりすることはできません。 ただし、管理ソリューションのエンティティの管理プロパティでカスタマイズが許可されている場合は、そのエンティティにフォームを追加したり、そのエンティティのフォームを編集することができます。 
  

<a name="BKMK_TypesOfForms"></a> 
## <a name="type-of-forms"></a>フォームの種類
様々なフォームの種類があり、種類ごとに固有の機能または使用法があります。 詳細情報: [Power Appsにおけるフォームの種類](types-forms.md)  

## <a name="main-form-dialogs-preview"></a>メイン フォーム ダイアログ (プレビュー)
クライアントAPIを使用すると、メイン フォーム ダイアログを使用して、フォームから移動せずに親フォームまたはベース フォーム上の関連レコード エンティティを開くことができます。 詳しくは：[ダイアログでクライアント API を使用してメイン フォームを開く](../../developer/model-driven-apps/customize-entity-forms.md#open-main-form-in-a-dialog-using-client-api) を参照してください 
  
<a name="BKMK_FormDifferencesByEntity"></a>   
## <a name="updated-versus-classic-entities"></a>標準エンティティに対して更新済み  
Power Apps には、フォームを設計するためのオプションが数多く用意されています。 統一インターフェイスにより、応答の早いインターフェイスに合わせて大半のエンティティが更新されました。 更新されたエンティティおよびユーザー定義のエンティティには、Dynamics 365 for tablets クライアント、業務プロセス フロー、および業務ルールのサポートが含まれます。 これらのエンティティを使用すると、一度設計すればすべてのクライアントに展開できます。  
  
現在も、以前のバージョンから引き継がれた外観と機能を保持している、ここで従来のエンティティと呼ばれる多数のエンティティが存在しています。 これらのエンティティはあまり使用されません。 それらをここに一覧表示します。  
  
||||||  
|-|-|-|-|-|  
|アドレス|記事 |記事のコメント |一括削除操作 |つながり |  
|値引き |値引き表 |ドキュメントの場所 |電子メールの添付ファイル|フォロー|  
|目標 |目標の指標|インポート ソース ファイル |請求書の製品|受注製品 |  
|価格表 |キュー アイテム |見積もり製品|ロールアップ フィールド|ロールアップ クエリ|  
|保存されているビュー|サービス|サービス活動|SharePoint サイト|サービス拠点|  
|担当地域|出荷単位|出荷単位一覧|||  

  
## <a name="form-display-faq"></a>フォーム表示のFAQ

### <a name="why-is-my-form-not-visible-in-the-form-selector-drop-down-in-my-app"></a>自分のアプリ内のフォーム選択ドロップダウンに自分のフォームが表示されないのはなぜですか。
フォームがアプリに未追加であるために使用可能でない可能性があります。
1. アプリ デザイナーでアプリを開きます。
2. **エンティティ ビュー**領域で、エンティティの隣の**フォーム**を選択します。
3. **コンポーネント** タブで、アプリに含まれるメイン フォームを検証します。 表示するフォームがチェック済みであることを確認します。 チェックされていない場合、それを選択してから、アプリを公開します。

   > [!div class="mx-imgBorder"] 
   > ![](media/forms-included-in-app.png "Forms included with app")
   
### <a name="why-isnt-my-form-displayed-as-the-default-form-in-the-app"></a>自分のフォームがアプリ内で既定のフォームとして表示されないのはなぜですか。
フォームは、フォームの順序構成を使用して、またはユーザーが既定のフォームを個人か設定としてセットするときに、既定のフォームとしてセットすることができます。
1. ソリューション エクスプローラーを開きます。 順序を変更するフォームを含むエンティティを展開してから、**フォーム**を選択します。
2. ツールバーで**フォームの順序** > **メイン フォーム セット**を選択します。 

   > [!div class="mx-imgBorder"] 
   > ![](media/form-order-toolbar.png "Form Order toolbar command")
   
3. フォームの順序が表示されます。 フォームを選択して上下矢印を使用し、フォームの順序内のフォームを移動します。 リストの最上部のフォームが既定のフォームです。 

   > [!div class="mx-imgBorder"] 
   > ![](media/form-order-dialog.png "Form order dialog")
   
4. **OK**を選択してフォームの順序の変更内容を保存します。
5. フォーム デザイナー ツール バーで**公開**を選択して、フォームの順序をアプリ内で使用可能にします。
 
#### <a name="form-order-user-personalization-setting"></a>フォームの順序のユーザー個人用設定
アプリのユーザーがアプリのフォーム選択ドロップダウンでフォーム選択を変更すると、そのフォームがそのユーザーの既定のフォームになることに注意してください。 この個人用設定により、アプリ内のエンティティに対して指定された既定のフォームがオーバライドされます。

   > [!div class="mx-imgBorder"] 
   > ![](media/change-form-user-setting.png "User setting to change default form")
   
### <a name="related-topics"></a>関連トピック  
    
[フォームの順序の割り当て](assign-form-order.md) <br />
[フォームへのアクセスの制御](control-access-forms.md) <br />
[メイン フォームを他のクライアントに表示する方法](main-form-presentations.md) <br />
