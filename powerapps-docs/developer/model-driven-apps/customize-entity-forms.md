---
title: エンティティ フォームのカスタマイズ (モデル駆動型アプリ) | MicrosoftDocs
description: フォームには、エンティティ レコードを作成、表示、編集するために使用するユーザー インターフェイス (UI) が用意されています。 エンティティ フォームを作成または編集するには、カスタマイズ ツールのフォーム デザイナーを使用します。 このトピックでは、フォームをプログラムで作成または編集するために必要な情報を提供します。
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: article
ms.assetid: e6a25bbe-e484-cfe9-9ad9-20ac6f19336a
author: JimDaly
ms.author: jdaly
manager: shilpas
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5bec04a5f2104eb2dda3cc7515390c7d52573a7f
ms.sourcegitcommit: 4349eefb1fd788f5e27d91319bc878ee9aba7a75
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2020
ms.locfileid: "3012606"
---
# <a name="customize-entity-forms"></a>エンティティ フォームのカスタマイズ

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/customize-entity-forms -->

フォームには、エンティティ レコードを作成、表示、編集するために使用するユーザー インターフェイス (UI) が用意されています。 エンティティ フォームを作成または編集するには、カスタマイズ ツールのフォーム デザイナーを使用します。 詳細: アプリケーション内のフォームの作業に関連するタスクの詳細は、[フォームの作成および設計](../../maker/model-driven-apps/create-design-forms.md)を参照してください。  

 このトピックでは、フォームをプログラムで作成または編集するために必要な情報を提供します。  

<a name="BKMK_AccessingFormDefinitions"></a>   

## <a name="access-form-definitions"></a>フォーム定義へのアクセス  
 エンティティ フォームは、ダッシュボードおよびビジュアル化とともに `SystemForm` のエンティティに格納されます。 エンティティのフォーム定義を確認する以下の 2 つの方法があります。  

-   エンティティをアンマネージド ソリューションに含め、ソリューションをエクスポートします。  

-   `SystemForm` のエンティティをクエリ  

<a name="BKMK_ViewingFormXml"></a>   

### <a name="view-formxml-from-an-exported-entity"></a>エクスポートしたエンティティから FormXML を表示  
 カスタマイズ済みのシステム エンティティ フォームの定義のみが、エクスポートされた管理ソリューションに含まれます。 システム エンティティ フォームの定義を表示するには、何らかの方法でそれを変更するか、または既存のフォームを新しい名前で保存して新しいフォームを作成するかのどちらかが必要です。  

 ソリューションのエクスポート後、コンテンツを抽出して customizations.xml ファイルを表示します。 フォームの定義は `ImportExportXml` > `Entities` > `Entity` > `FormXml` にあります。 `<FormXml>` ノード内では、各種類のフォームが `<forms>` 要素内に、フォームの種類を示す `type` 属性と共にグループ化されています。  

<a name="BKMK_FormProperties"></a>   
## <a name="form-properties"></a>フォームのプロパティ  
 次の表は、主な `SystemForm` エンティティ属性および対応するデータについて説明しています。このデータには、ソリューションとともにエクスポートされた XML 要素が含まれています。  


|  SystemForm プロパティ  |                 FormXML 要素                 |                                                                                                              内容                                                                                                              |
|-----------------------|-------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   `AncestorFormId`    |                  `<ancestor>`                   |                      親フォームを表す一意識別子です。 これは既存のフォームで**名前を付けて保存**を使用して、または <xref:Microsoft.Crm.Sdk.Messages.CopySystemFormRequest> を使用して新しいフォームを作成したときに設定されます。                      |
|    `CanBeDeleted`     |                `<CanBeDeleted>`                 |                                    このコンポーネントを削除できるかどうか指定する情報です。この管理プロパティは、管理ソリューションのインポートによりフォームが作成される場合にのみ適用されます。                                    |
|     `Description`     |                `<Descriptions>`                 | `Description` は文字列で、`<Descriptions>` にはフォームの説明のためのローカライズされたラベルが含まれています。<br /><br /> ローカライズされたラベルは <xref:Microsoft.Crm.Sdk.Messages.RetrieveLocLabelsRequest> を使用して取得できます。 |
| `FormActivationState` |             `<FormActivationState>`             |                                  フォームの状態を指定します。<br /><br /> 「メイン」の種類のフォームのみを非アクティブ化できます。<br /><br /> 有効な値:<br /><br /> -   0 : 非アクティブ<br />-   1 : アクティブ                                  |
|       `FormId`        |                   `<formid>`                    |                                                                                                     フォームを表す一意識別子                                                                                                     |
|  `FormPresentation`   |              `<FormPresentation>`               |                                     このフォームが Common Data Service の更新済み UI のレイアウトであるかを指定します。                                      |
|       `FormXml`       |                    `<form>`                     |                                                                                                フォーム レイアウトの XML 表現です。                                                                                                 |
|  `IntroducedVersion`  |              `<IntroducedVersion>`              |                                                                                          フォームが追加されたソリューションのバージョンです。                                                                                          |
|     `IsAIRMerged`     |                       なし                       |                                           このフォームが Common Data Service の更新済み UI のレイアウトでマージ済みであるかを指定します。                                           |
|   `IsCustomizable`    |               `<IsCustomizable>`                |                            このコンポーネントがカスタマイズ可能かどうかを指定する情報です。<br /><br /> この管理プロパティは、フォームが管理ソリューションをインポートして作成された場合にのみ適用されます。                            |
|      `IsDefault`      |                       なし                       |                                                                          フォームまたはダッシュボードがシステムの既定であるかどうかを指定する情報です。                                                                          |
|        `Name`         |               `<LocalizedNames>`                |       `Name` は文字列で、`<LocalizedNames>` にはフォーム名のためのローカライズされたラベルが含まれています。<br /><br /> ローカライズされたラベルは <xref:Microsoft.Crm.Sdk.Messages.RetrieveLocLabelsRequest> を使用して取得できます。       |
|   `ObjectTypeCode`    | フォームは `Entity` 要素の子孫です。 |                                                                                        `ObjectTypeCode` 値はエンティティの論理名です。                                                                                         |
|        `Type`         |       `<forms>` 要素 `type` 属性        |                                                       フォームで有効な値は以下の通りです。<br /><br /> -   2: `main`<br />-   5: `mobile`<br />-   6: `quick`<br />-   7: `quickCreate`                                                        |

<a name="BKMK_CreateAndEditForms"></a>   

## <a name="create-and-edit-forms"></a>フォームを作成して編集する  

 エンティティの新しいフォームは、<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>. <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.CanCreateForms> が許可する場所にのみ作成することができます。  

 新しいフォームは、<xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> または <xref:Microsoft.Crm.Sdk.Messages.CopySystemFormRequest> のいずれかを使用して作成できます。 <xref:Microsoft.Crm.Sdk.Messages.CopySystemFormRequest> を使用するか、フォーム エディターの**名前を付けて保存**使用するとき、フォーム間に継承がないことに注意してください。 したがって、基本フォームを変更しても、そこから作成されたフォームにはその変更は自動的に適用されません。  

 エンティティ フォームを編集するサポートされる方法は、エクスポートされた管理ソリューションからフォーム定義を編集し、ソリューションを再度インポートすることです。 手動でフォームを編集するとき、スキーマ検証を使用できる XML エディターの使用を強くお勧めします。 詳細: [スキーマ検証を使用した XML カスタマイズ ファイルの編集](edit-customizations-xml-file-schema-validation.md)  

## <a name="open-main-form-in-a-dialog-using-client-api"></a>ダイアログでクライアント API を使用してメイン フォームを開く

クライアント API を使用してダイアログでメイン フォームを開くには、 [Xrm.Navigation.navigateTo](https://docs.microsoft.com/powerapps/developer/model-driven-apps/clientapi/reference/xrm-navigation/navigateto) メソッドを使用して呼び出す必要があります。 [Xrm.Navigation.navigateTo](https://docs.microsoft.com/powerapps/developer/model-driven-apps/clientapi/reference/xrm-navigation/navigateto)API メソッドを使用すると、サイズや位置などのオプションが表示されたダイアログを開くことができます。

> [!IMPORTANT]
> - クライアント API を使用したダイアログでメインフォームを開く機能は現在プレビューの状態です。
> - プレビュー機能は運用環境での使用を想定しておらず、機能が制限されている可能性があります。 これらの機能を公式リリースの前に使用できるようにすることで、顧客が一足先にアクセスし、そこからフィードバックを得ることができます。


> [!NOTE]
> [Xrm.Navigation.openForm](https://docs.microsoft.com/powerapps/developer/model-driven-apps/clientapi/reference/xrm-navigation/openform)メソッドでは、メインフォームをダイアログで開くことには対応していません。

## <a name="examples"></a>例

### <a name="open-a-new-record"></a>新しいレコードを開く

この例では、ダイアログが新規レコードを作成する新たな取引先企業のフォームを開きます。 ダイアログは、呼び出し元のフォームの最上部にモード形式の使用可能なウィンドウの最大50%を使用して中央にポップアップされます。

```JavaScript
Xrm.Navigation.navigateTo({pageType:"entityrecord", entityName:"account", formType:2}, {target: 2, position: 1, width: {value: 50, unit:"%"}});
```
> [!div class="mx-imgBorder"]
> ![新しいレコードを開く](media/open-new-record-mfd.png "新しいレコードを開く")

### <a name="open-an-existing-record"></a>既存のレコードを開く

この例では、ダイアログが連絡先フォームの取引先企業のエンティティID値を使用して既存の取引先企業レコードを開きます。 このエンティティの ID を、ダイアログにて開くレコードの ID に置き換えます。

```JavaScript
Xrm.Navigation.navigateTo({pageType:"entityrecord", entityName:"account", formType:2, entityId:"xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"}, {target: 2, position: 1, width: {value: 80, unit:"%"}});
```
> [!div class="mx-imgBorder"]
> ![既存のレコードを開く](media/open-existing-record-mfd.png "既存のレコードを開く")

### <a name="open-a-new-record-on-the-side-pane"></a>サイド ウィンドウで新しいレコードを開きます

この例では、ダイアログ ウィンドウの右隅で新しいレコードを開きます。 これは、ピクセル オプションを使用して実現できます。

```JavaScript
Xrm.Navigation.navigateTo({pageType:"entityrecord", entityName:"account", formType:2}, {target: 2, position: 2, width: {value: 500, unit:"px"}});
```
> [!div class="mx-imgBorder"]
> ![サイド ウィンドウで既存のレコードを開きます](media/open-record-side-pane-mfd.png "サイド ウィンドウで既存のレコードを開きます")

### <a name="open-main-form-in-a-dialog-with-callback-method"></a>コールバック メソッドを使用してダイアログでメインフォームを開く

この例では、レコードを保存してダイアログを閉じた後に、メインフォームのダイアログがコールバック メソッドでどのように呼び出されるかを示しています。

```Javascript
Xrm.Navigation.navigateTo({pageType:"entityrecord", entityName:"account", formType:2},{target: 2, position: 2, width: {value: 80, unit:"%"}}).then(
    function (retVal) {
        console.log(retVal.savedEntityReference[0].id + ", " + retVal.savedEntityReference[0].name)
    },
    function (error) {
        console.log(error);
    });
```

### <a name="see-also"></a>関連項目  

 [フォームの作成および設計](../../maker/model-driven-apps/create-design-forms.md)   
 [SystemForm エンティティ](../common-data-service/reference/entities/systemform.md)  
 [フォーム XML スキーマ](form-xml-schema.md)<br/>
 [Xrm.Navigation.navigateTo](https://docs.microsoft.com/powerapps/developer/model-driven-apps/clientapi/reference/xrm-navigation/navigateto)
