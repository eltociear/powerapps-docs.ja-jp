---
title: モデル駆動型アプリ フォームを作成および設計する | MicrosoftDocs
ms.custom: ''
ms.date: 06/26/2018
ms.reviewer: ''
ms.service: crm-online
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
tags:
  - Links to topic not migrated
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-and-design-model-driven-app-forms"></a>モデル駆動型アプリ フォームを作成および設計する 

PowerApps では、フォームは、ユーザーが各自の作業を遂行するために必要なデータとのやり取りに使用するユーザー インターフェイスを提供します。 ユーザーが使用するフォームは、必要とする情報を効率よく検索または入力できるように設計されていることが重要です。 

既定のソリューションまたはアンマネージド ソリューションでは、新しいフォームを作成したり、フォームのカスタマイズが許可されているすべてのエンティティの既存のフォームを編集したりすることができます。 アンマネージド ソリューションでは、ソリューション用に作成されたアンマネージドなユーザー定義エンティティの管理プロパティを編集できます。
マネージド ソリューションの表示中に、新しいフォームを作成したり、ここのエンティティの既存のフォームを編集したりすることはできません。 ただし、管理ソリューションのエンティティの管理プロパティでカスタマイズが許可されている場合は、そのエンティティにフォームを追加したり、そのエンティティのフォームを編集することができます。 
  

<a name="BKMK_TypesOfForms"></a> 
## <a name="type-of-forms"></a>フォームの種類
様々なフォームの種類があり、種類ごとに固有の機能または使用法があります。 詳細情報: [PowerApps でのフォームの種類](types-forms.md)。  

  
<a name="BKMK_FormDifferencesByEntity"></a>   
## <a name="updated-versus-classic-entities"></a>標準エンティティに対して更新済み  
PowerApps には、フォームを設計するためのオプションが数多く用意されています。 統一インターフェイスにより、応答の早いインターフェイスに合わせて大半のエンティティが更新されました。 更新されたエンティティおよびユーザー定義のエンティティには、Dynamics 365 for tablets クライアント、業務プロセス フロー、および業務ルールのサポートが含まれます。 これらのエンティティを使用すると、一度設計すればすべてのクライアントに展開できます。  
  
現在も、以前のバージョンから引き継がれた外観と機能を保持している、ここで従来のエンティティと呼ばれる多数のエンティティが存在しています。 これらのエンティティはあまり使用されません。 それらをここに一覧表示します。  
  
||||||  
|-|-|-|-|-|  
|アドレス|記事 |記事のコメント |一括削除操作 |つながり |  
|値引き |値引き表 |ドキュメントの場所 |電子メールの添付ファイル|フォロー|  
|目標 |目標の指標|インポート ソース ファイル |請求書の製品|受注製品 |  
|価格表 |キュー アイテム |見積もり製品|ロールアップ フィールド |ロールアップ クエリ |  
|保存されているビュー |サービス|サービス活動|SharePoint サイト|サービス拠点|  
|担当地域|出荷単位|出荷単位一覧|||  
  
### <a name="related-topics"></a>関連トピック  
    
[フォームの順序の割り当て](assign-form-order.md) <br />
[フォームへのアクセスの制御](control-access-forms.md) <br />
[メイン フォームを他のクライアントに表示する方法](main-form-presentations.md) <br />