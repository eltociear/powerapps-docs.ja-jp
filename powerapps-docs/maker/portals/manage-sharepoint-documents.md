---
title: ポータルの SharePoint ドキュメントの管理 | MicrosoftDocs
description: ポータルで SharePoint ドキュメントを管理するための手順。
author: gitanjalisingh33msft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: gisingh
ms.reviewer: tapanm
ms.openlocfilehash: 6efbca20258227365517fd4727ff28b0619411fd
ms.sourcegitcommit: c12260f372ad2cc48d3146be570d2088c9ef1d86
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2020
ms.locfileid: "3493887"
---
# <a name="manage-sharepoint-documents"></a>SharePoint ドキュメントの管理

Common Data Service は、[!INCLUDE[pn-microsoft-sharepoint-online](../../includes/pn-microsoft-sharepoint-online.md)] との統合をサポートしています。これによりユーザーは Common Data Service 内の [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] のドキュメント管理機能を使用できます。 Power Apps ポータルでは、ポータルのエンティティ フォームまたは Web フォームに [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] からのドキュメントを直接アップロードおよび表示することができるようになりました。 これにより、ポータル ユーザーは、ドキュメントをポータルで表示、ダウンロード、追加、削除できます。 ポータル ユーザーは各自のドキュメントの編成にサブフォルダーを作成することもできます。

> [!NOTE]
> - ドキュメント管理は、[!INCLUDE[pn-microsoft-sharepoint-online](../../includes/pn-microsoft-sharepoint-online.md)] に対してのみ動作します。
> - ドキュメント管理には、サーバーベースの統合がサポートされています。

[!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] のドキュメント管理機能を Common Data Service 内から使用するには、次を実行する必要があります。

1.  [Dynamics 365 でドキュメント管理機能を有効にする](#step-1-enable-document-management-functionality-in-model-driven-apps-in-dynamics-365)

2.  [SharePoint 統合を Power Apps ポータル管理センターから設定する](#step-2-set-up-sharepoint-integration-from-power-apps-portals-admin-center)

3.  [エンティティのドキュメント管理を有効にする](#step-3-enable-document-management-for-entities)

4.  [Power Apps ドキュメントから適切な形式を設定する](#step-4-configure-the-appropriate-form-to-display-documents)

5.  [適切なエンティティのアクセス許可を作成し、必要な Web ロールに割り当てる](#step-5-create-appropriate-entity-permission-and-assign-it-to-the-appropriate-web-role)

## <a name="step-1-enable-document-management-functionality-in-model-driven-apps-in-dynamics-365"></a>ステップ 1 : Dynamics 365 のモデル駆動型アプリでドキュメント管理機能を有効にします

サーバーベースの [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 統合を使用することで、Dynamics 365 のモデル駆動型アプリのドキュメント管理機能を有効にする必要があります。 サーバーベースの [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 統合により、Dynamics 365 のモデル駆動型アプリと [!INCLUDE[pn-microsoft-sharepoint-online](../../includes/pn-microsoft-sharepoint-online.md)] をサーバー間接続をおこなうようにすることができます。 既定の [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] サイト レコードは、ポータルによって使用されます。 Dynamics 365 のモデル駆動型アプリのドキュメント管理機能を有効にする方法については、[SharePoint オンラインを使用して Dynamics 365 のモデル駆動型アプリを設定する](https://docs.microsoft.com/power-platform/admin/set-up-dynamics-365-online-to-use-sharepoint-online) をご覧ください。

## <a name="step-2-set-up-sharepoint-integration-from-power-apps-portals-admin-center"></a>ステップ 2: Power Apps ポータル管理センターから SharePoint  統合を設定する

[!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] のドキュメント管理機能を使用するには、[!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 統合を Power Apps ポータル管理センターから有効にする必要があります。

> [!NOTE]
> このアクションを実行するには、グロバール管理者である必要があります。

1. [Power Apps ポータル管理センター](admin/admin-overview.md) を開きます。

2.  **[!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 統合の設定** > **[!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 統合を有効にする**の順に移動します。

    > [!div class=mx-imgBorder]
    > ![SharePoint 統合を有効にする](media/enable-sharepoint-integration.png "SharePoint 統合を有効にする")

3.  確認メッセージで**有効にする**を選択します。 これにより、ポータルは [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] と通信できるようになります。 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 統合が有効になりますが、ポータルが再起動されるため、数分間使用できなくなります。 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] の統合が有効になっている場合に、メッセージが表示されます。

[!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 統合が有効になっている場合、以下の操作が使用可能になります。

- **[!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 統合を無効にすることにより**、ポータルとの [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 統合を無効にすることができます。 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 統合が無効になりますが、ポータルが再起動されるため、数分間使用できなくなります。 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] の統合が無効になっている場合に、メッセージが表示されます。

    > [!div class=mx-imgBorder]
    > ![SharePoint 統合を無効にする](media/disable-sharepoint-integration.png "SharePoint 統合を無効にする")

[!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 統合を有効または無効にすることにより、それぞれ、ポータルの [!INCLUDE[pn-azure-active-directory](../../includes/pn-azure-active-directory.md)] ([!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] AD) アプリケーションが更新され、必要な [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] アクセス許可が追加または削除されます。 また、[!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] AD アプリケーションに行われる変更を承認するようにリダイレクトされます。 

> [!div class=mx-imgBorder]
> ![SharePoint 統合を無効にする](media/sharepoint-integration-consent.png "SharePoint 統合を無効にする")

承認しない場合は以下の通りになります。

- [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 統合の有効または無効が終了せず、エラー メッセージが表示されます。

- 標準 [!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] AD ログインはポータルで機能しません。 


## <a name="step-3-enable-document-management-for-entities"></a>ステップ 3: エンティティのドキュメント管理を有効にする
エンティティのドキュメント管理を有効にし、[!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] のエンティティ レコードに関連するドキュメントを  に保存する必要があります。 エンティティのドキュメント管理を有効にする方法については、[特定のエンティティの SharePoint ドキュメント管理を有効にする](https://docs.microsoft.com/dynamics365/customer-engagement/admin/enable-sharepoint-document-management-specific-entities)を参照してください。

## <a name="step-4-configure-the-appropriate-form-to-display-documents"></a>ステップ 4: 適切なフォームを設定し、ドキュメントを表示する

### <a name="power-apps-customization"></a>Power Apps カスタマイズ

ドキュメント管理機能を使用するフォームを特定します。  フォーム エディターからモデル駆動型アプリを使用してフォームを編集するか、サブグリッドを追加する必要があります。 サブグリッドは、ポータルのドキュメントをに使用するフォームにセクションを追加します。 この機能を起動するには、サブグリッドにある次のプロパティを設定する必要があります:

- **データ ソース**の**エンティティ**一覧から**ドキュメントの場所**を選択します。

- **データ ソース**の**エンティティ**一覧から**アクティブなドキュメントの場所**を選択します。

要件に応じて名前とラベルを指定できます。 サブグリッドが追加または構成されたら、フォームを保存して公開します。

> [!NOTE]
> フォームを編集するエンティティに対して、ドキュメント管理を有効にする必要があります。 詳細: [エンティティのドキュメント管理を有効にする](#step-3-enable-document-management-for-entities)

### <a name="power-apps-portals-configuration"></a>Power Apps ポータル構成

エンティティ フォームまたは Web フォームに必要な標準構成とは別に、ドキュメント管理を有効にするには、次のプロパティを設定する必要があります:

- **エンティティ名** および **フォーム名**: 前のステップでカスタマイズしたエンティティ名とフォーム名をそれぞれ入力します。

- **エンティティのアクセス許可**チェック ボックスを選択し、ユーザーがドキュメントを参照できるようにします。

- **モード**を**編集**に設定し、ドキュメントをアップロードできるようにします。

> [!NOTE]
> ドキュメントのアップロードには、親エンティティのレコードが存在する必要があります。 モードを挿入に設定した場合、フォームが送信されるまで親エンティティ レコードが作成されないため、ドキュメントのアップロードが機能しません。

## <a name="step-5-create-appropriate-entity-permission-and-assign-it-to-the-appropriate-web-role"></a>ステップ 5: 適切なエンティティのアクセス許可を作成し、必要な Web ロールに割り当てる

2 つのエンティティのアクセス許可レコードには、ドキュメントを表示またはアップロードするために必要なアクセスを確立する必要があります。

- エンティティまたは Web フォームのエンティティのアクセス許可: 
    - 以前に構成されたエンティティ フォームまたは Web フォームのエンティティのように、**エンティティ名**を指定し、**エンティティのアクセス許可**レコードを作成します。 
    - **スコープ**を選択し、フォームの希望する動作に適しているスコープ関連付けを選択します。 
    - **読み取り**および**追加**特権を有効にし、ドキュメントへの読み取りアクセス権を可能にし、必要に応じて、**書き込み**特権を有効にし、ドキュメントのアップロードを可能にします。 次の手順を入力するために、**子エンティティのアクセス許可**セクションを無視します。
- 以前のアクセス許可レコードを参照する**親スコープ**の**ドキュメントの場所**のアクセス許可 
    - **親**と設定された**スコープ**と**ドキュメントの場所**エンティティとして、**エンティティ名**を指定し、**エンティティのアクセス許可**レコードを作成します。 
    - 以前の手順で作成したエンティティのアクセス許可レコードに対して、親エンティティのアクセス許可を選択します。 
    - 特権 
        - ドキュメントへの読み取りアクセス権を許可する最低限の特権は、**読み取り**、**作成**および**追加**です。 
        - ドキュメントのアップロード アクセスにおける**書き込み**特権を含めます。 
        - **削除**を含め、ドキュメントを削除できるようにします。

> [!NOTE]
> **ドキュメントの場所**エンティティに対応する子エンティティのアクセス許可は、ドキュメントを表示する必要があるエンティティまたは Webフォームのエンティティに存在する親エンティティのアクセス許可レコードの各インスタンスごとに作成する必要があります。

## <a name="configure-file-upload-size"></a>ファイルのアップロード サイズを構成する

既定では、ファイル サイズは 10 MB にセットされています。 しかし、サイト設定 `SharePoint/MaxUploadSize` を使用して、ファイル サイズを最小 50 MB に構成できます。

## <a name="sample-configuration-to-enable-document-management-on-the-case-entity-form"></a>サポート案件エンティティ フォームのドキュメント管理を有効にするためのサンプル構成

以下の例は、前提条件として Dynamics 365 Customer Service アプリケーションが必要なサポート案件エンティティを使用した構成を示しています。 このサンプルではサポート案件エンティティを使用していますが、これは単に上記ステップの図で、他のユーザー定義エンティティまたは SharePoint で管理ドキュメントをサポートする Common Data Service エンティティともフォローできます。 

1.  [ステッププ 1](#step-1-enable-document-management-functionality-in-model-driven-apps-in-dynamics-365) の指示に従い、サーバーベースの構成が Dynamics 365 のモデル駆動型アプリと [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 統合に対して完了していることを確認します。

2.  [ステップ 2](#step-2-set-up-sharepoint-integration-from-power-apps-portals-admin-center) の指示書に従い、ポータルに [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] を統合するアクセス許可があるかを確認します。 

3.  [ステップ 3](#step-3-enable-document-management-for-entities) の指示に従い、サポート案件エンティティに対してドキュメント管理が有効になっていることを確認します。

4.  次の構成と[ステップ 4](#step-4-configure-the-appropriate-form-to-display-documents) の手順に従ってください:

    - Dynamics 365 のモデル駆動型アプリのカスタマイズ

        a. **設定** > **カスタマイズ** > **システムのカスタマイズ**の順に移動します。 

        b. **既定のソリューション**では、**サポート案件**エンティティ > **フォーム**の順に移動します。 
    
        c. フォーム エディターの **Web – サポート案件の編集**を開きます。

         > [!div class=mx-imgBorder]
         > ![Web - サポート案件の編集](media/web-edit-case-form.png "Web - サポート案件フォームの編集")
    
        d. フォーム上で**作成日時**フィールドを選択し、**挿入**タブで**サブグリッド**を選択します。

         > [!div class=mx-imgBorder]
         > ![Web にサブグリッドを追加する - サポート案件フォームの編集](media/add-sub-grid.png "Web にサブグリッドを追加する - サポート案件フォームの編集")
    
        e. **プロパティの設定**ダイアログ ボックスから次のプロパティを設定し、**OK** を選択します。

         - **名前** (どんな名前でも使用できます): CaseDocuments 
    
         - **ラベル** (どんなラベル名でも使用できます): サポート案件のドキュメント 
      
         - **エンティティ**: ドキュメントの場所 
    
         - **既定のビュー**: アクティブなドキュメントの場所

         > [!div class=mx-imgBorder]
         > ![[サブグリッドのプロパティ]](media/sub-grid-properties.png "サブグリッドのプロパティ")

        f. フォーム エディターで**保存**を選択し、**公開**を選択します。

    - Power Apps ポータル構成

        a. **ポータル** > **エンティティ フォーム**の順に移動します。
    
        b. **Customer Service - サポート案件の編集**エンティティ フォームを見つけて開きます。
    
        c. 次のプロパティが設定されていることを確認します:
    
         - **エンティティ名**: サポート案件 (インシデント)
    
         - **フォーム名**: Web – サポート案件の編集
    
         - **モード**: 編集
    
         - **エンティティのアクセス許可**: 有効化
    
         > [!div class=mx-imgBorder]
         > ![顧客サービス - サポート案件フォームの編集](media/customer-service-edit-case-form.png "顧客サービス - サポート案件フォームの編集")
    
        d. フォームに何かしらの変更を加えた場合は、**保存**を選択します。

5. [ステップ 5](#step-5-create-appropriate-entity-permission-and-assign-it-to-the-appropriate-web-role
) に従い、エンティティのアクセス許可がユーザーに付与されていることを確認します。

   1. ユーザーに関連付けられる **Web ロール**に移動します。 このサンプルでは、ユーザーが管理者の Web ロールを持っていることを前提としています。

   2. エンティティのアクセス許可は **取引先が顧客であるサポート案件の Customer Service** の名前別に存在することを確認します。 

      > [!NOTE]
      > Web ロールに追加されるこのエンティティのアクセス許可があることを確認します。 ユーザーが既に管理者である場合は、上記のエンティティのアクセス許可を明示的に割り当てられている必要はありません。

   3. 新しいエンティティのアクセス許可を作成し、次の情報を入力し、**保存**を選択します。

    - **名前** (どんな名前でも使用できます): Customer Service - 関連文書

    - **エンティティ名**: ドキュメントの場所
        
    - **スコープ**: 親
        
    - **親エンティティのアクセス許可**: Customer Service - 取引先担当者が顧客であるサポート案件
        
    - **親の関連付け**: incident_SharePointDocumentLocations
        
    - **特権**: 読み取り、作成、追加、書き込み、削除

      > [!div class=mx-imgBorder]
      > ![顧客サービス エンティティのアクセス許可](media/customer-service-entity-permission.png "顧客サービス エンティティのアクセス許可")
  
   4. ポータルにサインインし、ドキュメント管理がサポート案件エンティティに対して有効になっていることを確認します。

      a. **サポート** ページを移動します。

      > [!div class=mx-imgBorder]
      > ![ ポータルのサポートページ](media/portal-support-page.png " ポータルのサポートページ")

      b. リストから既存のサポート案件のレコードをクリックします。 ページの**サポート案件のドキュメント** セクションに移動し、ドキュメント リストが追加されていることを確認します。

      > [!div class=mx-imgBorder]
      > ![サポート案件ドキュメント](media/case-document.png "サポート案件ドキュメント")

