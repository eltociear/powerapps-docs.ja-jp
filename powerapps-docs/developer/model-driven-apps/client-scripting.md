---
title: JavaScript を使用するモデル駆動型アプリでクライアント スクリプトを使用してビジネス ロジックを適用 | Microsoft Docs
description: 開発者がクライアント側スクリプトで JavaScript を使用して、モデル駆動型アプリでカスタム ビジネス ロジックを適用する方法を説明します
services: ''
suite: powerapps
author: KumarVivek
ms.service: powerapps
ms.topic: article
ms.date: 03/18/2020
ms.author: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 27ca63ba1db97d7c5c63e72230852ab4e64617e7
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/21/2020
ms.locfileid: "3276203"
---
# <a name="apply-business-logic-using-client-scripting-in-model-driven-apps-using-javascript"></a>JavaScript を使用するモデル駆動型アプリでクライアント スクリプトを使用してビジネス ロジックを適用

JavaScript を使用したクライアント サイド スクリプトは、モデル駆動型アプリケーションのフォームにデータを表示するにあたってのカスタム ビジネス プロセス ロジックを適用する方法の1つです。

> [!IMPORTANT]
> このドキュメントで説明するすべてのクライアント スクリプトの概念と API は、[Dynamics 365 Customer Engagement (on-premises)](https://docs.microsoft.com/dynamics365/customerengagement/on-premises/overview) ユーザーにも適用されます。

しかし、モデル駆動型のアプリケーション フォームにカスタマイズしたビジネス プロセス ロジックを適用する場合には、クライアント スクリプトを最初に選択することは推奨しません。 *ビジネスルール* では、JavaScriptの知識がない、開発者ではないユーザーがフォームにてビジネス プロセス ロジックを適用する方法を提供します。 詳細については次を参照してください: [ロジックを適用するビジネスルールを作成する](/powerapps/maker/model-driven-apps/create-business-rules-recommendations-apply-logic-form) **データ** > **エンティティ** > [make.powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) の [entity_name] 領域内に、ビジネス ルール デザイナーがあります。 エンティティを表示するとき、**業務ルール**タブを検索します。

ビジネス ルールを使用しても業務上の要件を達成できない場合は、アプリケーションの動作を拡張し、クライアントでの自動化を実現する強力な方法として、クライアントAPIオブジェクト モデルを使用したクライアント スクリプト作成する方法があります。

## <a name="use-client-scripting-in-model-driven-apps"></a>モデル駆動型アプリでクライアント スクリプトを使用する

モデル駆動型アプリのフォームのヘルプにより、データをユーザーに表示します。 モデル駆動型アプリのフォームは、フィールド、簡易入力フォームまたはグリッドなどのアイテムを含むことができます。 [イベント](clientapi/events-forms-grids.md) は、常にモデル駆動型アプリ フォームで発生します:

- フォームロード
- データはフォーム内のフィールドまたはアイテムにおいて変更されます
- データはフォームに保存されます。

フォームにイベントが発生した場合にコードが実行されるように、これらのイベントに「応答」するためのJavaScriptコードを添付できます。 モデル駆動型アプリの[スクリプト Web リソース](script-jscript-web-resources.md) を使用して、これらのイベントに JavaScript コード (スクリプト) を添付します。 

モデル駆動型アプリは、何時および何をフォームに表示するかをコントロールするフォームオブジェクトおよびイベントと対話するための**クライアント API** の豊富なセットを提供します。

> [!NOTE]
> 一部のクライアントAPIは、現在のリリースのモデル駆動型アプリケーションでは推奨していません。 モデル駆動型アプリのクライアント側のコードを記述する際に、これらの API に注意しているか確認してください。 詳細: [使用が中止されたクライアントAPI](/dynamics365/get-started/whats-new/customer-engagement/important-changes-coming#some-client-apis-are-deprecated)

## <a name="get-started-here"></a>ここから始めましょう

[フォームおよびグリッドのイベント](clientapi/events-forms-grids.md)<br/>
[クライアント API オブジェクト モデルについて](clientapi/understand-clientapi-object-model.md)<br/>
[チュートリアル: 最初のクライアント スクリプトを記述する](clientapi/walkthrough-write-your-first-client-script.md)

## <a name="reference"></a>参照

[クライアント API リファレンス](clientapi/reference.md)


### <a name="related-topics"></a>関連トピック

[モデル駆動型アプリのための Web リソース](web-resources.md)<br/>
[コマンドとリボンのカスタマイズ](customize-commands-ribbon.md)<br/>


