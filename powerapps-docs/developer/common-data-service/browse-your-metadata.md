---
title: 組織のメタデータの参照 (Common Data Service) | Microsoft Docs
description: エンティティ メタデータ ブラウザーを使用して、Common Data Service のエンティティとそのプロパティを表示できます。 エンティティ メタデータ ブラウザーは、ダウンロードして組織にインストール可能な管理ソリューションです。
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 50a7c59ac5655fdcf6928f626c5714a75fe3f57e
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "2753055"
---
# <a name="browse-the-metadata-for-your-environment"></a>環境のメタデータの参照

エンティティ メタデータ ブラウザーを使用して、Common Data Service のエンティティとそのプロパティを表示できます。 エンティティ メタデータ ブラウザーは、次のリンクを使用してダウンロードできる、マネージド ソリューションです。


|                                                                                               [バージョン]                                                                                                |                                                                                     Download                                                                                      |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Common Data Service | [Microsoft ダウンロード: MetadataBrowser_3_0_0_5_managed.zip](https://download.microsoft.com/download/8/E/3/8E3279FE-7915-48FE-A68B-ACAFB86DA69C/MetadataBrowser_3_0_0_5_managed.zip) |

ソリューションをダウンロードした後、インストールする必要があります。 管理ソリューションをインストールする方法の詳細については、「[ソリューションのインポート、更新およびエクスポート](/dynamics365/customer-engagement/developer/customize/import-update-export-solutions)」を参照してください。  

## <a name="open-as-an-app"></a>アプリとして開く
Common Data Service はアプリとして構成されています。 **エンティティ メタデータ ブラウザー**ソリューションをインストールした後、**メタデータ ツール**アプリケーションを見つけて開きます。 既定のビューは**エンティティ**です。 **ツール**のナビゲーション領域から**エンティティ メタデータ**を選択して個別のエンティティを検査します。

## <a name="open-from-the-solution-configuration-page"></a>ソリューション構成ページから開く
以前のバージョンでは次の手順を使用する必要がありますが、最新のバージョンにも対応しています。  

**エンティティ メタデータ ブラウザー**ソリューションをインストールした後、ソリューション リストの行をダブルクリックしてマネージド ソリューションを開いて**構成**ページを表示すると、エンティティ メタデータ ブラウザーに関する情報と、2 種類のビューを起動するためのボタンが表示されます。
- **メタデータ ブラウザ** はアプリの **エンティティ** ビューに相当します。
- **エンティティ メタデータ ブラウザ** はアプリの **エンティティ メタデータ** ビューに相当します。

## <a name="entities-view"></a>エンティティ ビュー
次のアクションを実行できます。

- **ビューの詳細の表示**: **エンティティ メタデータ**ビューを使用して表示するエンティティを選択します。
- **エンティティの編集**: サポートされている場合は、既定の組織で選択されたエンティティ フォームを開きます。
- **テキスト検索**: 次のエンティティのプロパティを使用して、表示したエンティティをフィルター処理します。<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.SchemaName>、<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.LogicalName>、<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.DisplayName>、<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.ObjectTypeCode>、または <xref:Microsoft.Xrm.Sdk.Metadata.MetadataBase.MetadataId>。
- **エンティティのフィルター処理**: エンティティのサブセットを表示するために簡単な条件を設定します。 すべての条件は AND ロジックによって評価されます。
- **フィルター プロパティ**: 選択されたエンティティのすべてのプロパティを表示します。 リストには 100 近くのプロパティがあります。 これを使用して該当するものだけを選択します。

## <a name="entity-metadata-view"></a>エンティティ メタデータ ビュー

単一のエンティティで次のアクションを実行できます。

- **エンティティ**: 表示するエンティティを変更します。
- **プロパティ**: そのエンティティのすべてのプロパティを表示し、表示されるプロパティをフィルター処理します。

    - **エンティティの編集**: サポートされている場合は、既定の組織で選択されたエンティティ編集フォームを開きます。
    - **フィルター プロパティ**: 選択されたエンティティのすべてのプロパティを表示します。 リストには 100 近くのプロパティがあります。 これを使用して該当するものだけを選択します。

- **属性**: マスター/詳細ビューのエンティティの属性を表示します。 このビューでは、次のことができます。

    - **属性の編集**: サポートされている場合は、既定の組織で選択された属性のフォームを開きます。
    - **テキスト検索**: 次の属性のプロパティを使用して、表示した属性をフィルター処理します。<xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.SchemaName>、<xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.LogicalName>、<xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.DisplayName>、または <xref:Microsoft.Xrm.Sdk.Metadata.MetadataBase.MetadataId>。
    - **フィルター属性**: 属性のプロパティ値によって属性をフィルターします。
    - **フィルター プロパティ**: 選択された属性のすべてのプロパティを表示します。

- **キー**: 代替キーがエンティティに対して有効な場合、どのように構成されているか確認できます。

- **関連付け**: 一対多、多対一、多対多の 3 つの種類のエンティティの関連づけを表示できます。 これらのビューでは、次のことができます。  
    - **関連づけの編集**: サポートされている場合は、既定の組織で選択された関連付けのフォームを開きます。  
    - **テキスト検索**: 関連付けの種類に適切な値を使用して、テキストの検索を実行し、表示される関連付けをフィルター処理します。  
    - **プロパティのフィルター**: 任意の関連付けプロパティ値によって接続をフィルターします。

- **特権**: ユーザー定義エンティティを表示します。 このビューでは、次のことができます。  
    - `PrivilegeId` を使用して表示した特権をフィルター処理します。

> [!NOTE]
> エンティティの詳細プロパティを表示すると、多数の複雑なプロパティが展開可能な状態になります。 最も頻繁に使用する値はリンク付きで表示され、リンクを使用して詳細な表示に切り替えることができます。 データをプログラムから取得した場合は、データの構造が詳細ビューに反映されます。 詳細ビューには、同じ領域で取得できるその他の関連データも表示されます (たとえば、**表示名**プロパティに対してローカライズされたラベルが存在する場合)。

> [!TIP]
> ページからテキストをコピーするには、テキストを選択し、Ctrl+C キーボード ショートカットまたはコンテキスト メニューの**コピー**のコマンドを使用します。

## <a name="community-tools"></a>コミュニティ ツール

**メタデータ ブラウザー** は Common Data Service に対して XrmToolbox コミュニティが開発したツールです。 コミュニティ開発ツールのトピック、[開発者ツール](developer-tools.md) を参照してください。

> [!NOTE]
> コミュニティ ツールは Common Data Service の製品ではなく、コミュニティ ツールに対するサポートは提供しません。 このツールに関するご質問は、その発行元にお問い合わせください。 詳細: [XrmToolBox](https://www.xrmtoolbox.com)。

### <a name="see-also"></a>関連項目

 [Common Data Service の開発者ツール](developer-tools.md)<br />
 [エンティティ メタデータのカスタマイズ](customize-entity-metadata.md)<br />
 