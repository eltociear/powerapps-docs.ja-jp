---
title: 埋め込みキャンバス アプリの作業のガイドライン | MicrosoftDocs
ms.custom: ''
ms.date: 08/19/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
author: RichdiMSFT
ms.author: matp
manager: kvivek
tags:
- Power Apps maker portal impact
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 1b74b1a9e7cd86240d361fadd2590a704f707176
ms.sourcegitcommit: 564b939577aae9fbedb2186bea3d4740d32e7473
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/13/2020
ms.locfileid: "3043589"
---
# <a name="guidelines-on-working-with-embedded-canvas-apps"></a>埋め込みキャンバス アプリの作業のガイドライン
このトピックでは、埋め込みキャンバス アプリの作業のガイドライン、および発生する可能性がある問題のトラブルシューティングを実行するために役立つヒントを提供します。

-   埋め込みキャンバス アプリは統一インターフェイスのモデル駆動型アプリでのみサポートされます。
-   埋め込みキャンバス アプリはフォームごとに 1 つのみ有効にすることができます。 
     - 複数の埋め込みキャンバス アプリをフォームに追加することができますが、一度に 1 つのみ有効にすることができます。
     - 複数の埋め込みキャンバス アプリを 1 つのモデル駆動型フォーム上で有効にしようとすると、「1 つのフォームで 1 つのキャンバス アプリのみを有効にすることができます。」というメッセージが表示されます。
     - 埋め込みキャンバス アプリを有効化または無効化するには、[埋め込みキャンバス アプリの有効化](#enable-an-embedded-canvas-app)および[埋め込みキャンバス アプリの無効化](#disable-an-embedded-canvas-app)を参照してください。
-   埋め込みキャンバス アプリをモデル駆動型フォームに追加する時は、常に値があることを保証されている必須フィールドを使用します。 フィールドに値がない場合、埋め込みキャンバス アプリはホストのモデル駆動型フォーム上のデータが変更されるときにリフレッシュされません。
-   モデル駆動型フォームを公開しても、埋め込みキャンバス アプリは公開されません。
     - 埋め込みキャンバス アプリはホストのモデル駆動型フォームと独立して公開する必要があります。 詳細: [アプリの公開](../canvas-apps/save-publish-app.md#publish-an-app)。
-   キャンバス アプリ コントロール プロパティ内の **カスタマイズ** ボタンを介して埋め込みキャンバス アプリを作成または編集するために Power Apps Studio を開くことが Web ブラウザーのポップアップ ブロッカーによりブロックされる場合、make.powerapps.com サイトを有効化、または一時的にポップアップ ブロッカーを無効化してから、再度 **カスタマイズ** を選択する必要があります。
-   新しいレコードを作成するときは、それに渡すためにレコード コンテキストが必要なため、埋め込みキャンバス アプリは表示されません。
-   ModelDrivenFormIntegration.Item オブジェクトは読み取り専用です。 
     - データを記述するには、 Common Data Service コネクタを使用する必要があります。 詳細: [Common Data Service](/connectors/commondataservice/)
-   埋め込みキャンバス アプリは、ホストのモデル駆動型フォームを介してのみ作成することができます。 
    - 既存のキャンバス アプリケーションをモデル駆動型フォームに埋め込んで追加することは現在サポートされていません。
    - アプリ IDを使用して既存のキャンバス アプリをモデル駆動型フォームに埋め込むためのサポートは、今後のアップデートで提供されます。
- 埋め込みキャンバス アプリでモデル駆動型フォームを表示するとき、「そのアプリを見つけることができませんでした」というエラー メッセージが表示される場合、その埋め込みキャンバス アプリがモデル駆動型フォームと同じソリューション内にあることを確認します。
- 埋め込みキャンバス アプリを使用してモデル駆動型フォームを表示するときに、「このアプリに対するアクセス権がないようです。 アクセス権を共有するように所有者にお尋ねください」というエラー メッセージが表示される場合、作成者が埋め込みキャンバス アプリをユーザーと共有済みであるか確認します。 詳細: [埋め込みキャンバス アプリの共有](share-embedded-canvas-app.md)。
- サブグリッド コントロールにキャンバス アプリを追加することはできなくなりました。
    - プレビュー リリースでは、メーカーはサブグリッド コントロールにキャンバス アプリを追加できました。 キャンバス アプリがモデル駆動型フォームに埋め込まれ、一般提供されたため、モデル駆動型フォームに埋め込まれたキャンバス アプリを追加することは、フィールドに対して簡素化されます。 
    - これにより、メーカーは、現在の (メイン フォーム) レコードをデータ コンテキストあるいは、現在の (メイン フォーム) レコードに関連するレコードの一覧として渡すかを事前に決める必要がなくなるため、容易になりました。 
    - メーカーは、フィールドから常に開始し、現在の (メイン フォーム) レコード、または現在の (メイン フォーム) レコードに関連するレコードの一覧の両方にアクセスできます。
    - キャンバス アプリの関連レコードの一覧にアクセスするには、メーカーは、 Common Data Service コネクタとキャンバス アプリで [データ ソースの操作性と Common Data Service 表示機能を改善](https://powerapps.microsoft.com/blog/improved-data-source-selection-and-common-data-service-views/) した [フィルター](../canvas-apps/functions/function-filter-lookup.md) 関数が使用できます。  
    たとえば、 *取引先担当者* エンティティの *アクティブな取引先担当者* ビューにアクセスするには、メーカーは以下を使用できます: *フィルター (取引先担当者、'取引先担当者 (ビュー)'.'アクティブな取引先担当者')*。
    - サブグリッド コントロールを使用する既存のキャンバス アプリは、引き続き機能します。 ただし、代わりにフィールドを使用するために、次のアプリケーションに移行することをお勧めします。 詳細: 詳しくは、 [現在の (メイン フォーム) レコードに関連するレコードの一覧を使用するモデル駆動型フォーム上の埋め込みキャンバス アプリへの移行](embedded-canvas-app-migrate-from-preview.md#migrating-embedded-canvas-apps-on-model-driven-forms-that-use-a-list-of-records-related-to-the-current-main-form-record) をご覧ください。

## <a name="enable-an-embedded-canvas-app"></a>埋め込みキャンバス アプリの有効化
1. 埋め込みキャンバス アプリとして表示するようにカスタマイズされたフィールドを選択します。
2. **フィールド プロパティ** ダイアログで、 **コントロール** タブを選択します。
3. コントロールのリストで、**キャンバス アプリ**を選択してから**Web** オプションを選択します。
4. **OK** を選びます。

## <a name="disable-an-embedded-canvas-app"></a>埋め込みキャンバス アプリの無効化
1. 埋め込みキャンバス アプリとして表示するようにカスタマイズされたフィールドを選択します。
2. **フィールド プロパティ** ダイアログで、 **コントロール** タブを選択します。
3. コントロールのリストで、既定のコントロールを選択してから**Web** オプションを選択します。
4. **OK** を選びます。

## <a name="known-issues-and-limitations-with-embedded-canvas-apps"></a>埋め込みキャンバス アプリに関する既知の問題および制限
- キャンバス アプリ コントロールは **Web** クライアントの種類と共に使用する場合にのみサポートされます。 現在、**電話**および**タブレット PC** クライアントの種類はサポートされていません。
- ModelDrivenFormIntegration コントロールは、関連エンティティのフィールドに値を指定しません。 
  - たとえば、ModelDrivenFormIntegration コントロールが取引先企業エンティティに接続されている場合、 *ModelDrivenFormIntegration.Item.'取引先責任者'.'氏名'* を使用しても値は返されません。 
  - 関連エンティティ メーカーのフィールドにアクセスするにはここに示した式のいずれかを使用できます:
    - *LookUp(取引先企業, 取引先企業 = GUID(First(ModelDrivenFormIntegration.Data).ItemId)).'取引先責任者'.'氏名'*  
      - *ItemId* は作成時には空ですが、実行時には値を持ちます。
    - *LookUp(取引先企業, 取引先企業 = ModelDrivenFormIntegration.Item.Account).'取引先責任者'.'氏名'* (この式は読みやすくなっていますが、前式の方が速度が若干よいです。)
- セキュリティ ロール内の**キャンバス アプリ**特権を使用して、埋め込みキャンバス アプリまたはスタンドアロン キャンバス アプリのいずれかに対するアクセス権をアプリ ユーザーに付与することはできません。 埋め込みキャンバス アプリの共有の詳細については、[埋め込みキャンバス アプリの共有](share-embedded-canvas-app.md)を参照してください。
- ホストのモデル駆動型フォームに表示されているものと同じデータを記述する場合、フォームがリフレッシュされるまで引き続き古いデータが表示されます。 そのための簡単な方法は [RefreshForm](embedded-canvas-app-actions.md#refreshformshowprompt) メソッドを使うことです。

## <a name="see-also"></a>関連項目
[モデル駆動型フォーム上にキャンバス アプリを埋め込む](embed-canvas-app-in-form.md) <br />
[埋め込み型キャンバス アプリケーションをモデル駆動フォームに追加する](embedded-canvas-app-add-classic-designer.md) <br />
[モデル駆動型フォームの埋め込み型キャンバス アプリケーションを編集する](embedded-canvas-app-edit-classic-designer.md) <br />
[モデル駆動フォームに埋め込まれたキャンバス アプリケーションの画面サイズと表示方向をカスタマイズする](embedded-canvas-app-customize-screen.md) <br />
[組み込みキャンバス アプリ内からホスト フォームで事前定義済みの操作を実行する](embedded-canvas-app-actions.md) <br />
[ModelDrivenFormIntegrationコントロールのプロパティとアクション](embedded-canvas-app-properties-actions.md) <br />
[埋め込みキャンバス アプリの共有](share-embedded-canvas-app.md) <br />
[パブリック プレビュー リリースを使用して作成された、モデル駆動型フォームの埋込み型キャンバスアプリケーションを最新版へと移行する](embedded-canvas-app-migrate-from-preview.md) <br />
