---
title: 作成フェーズ - Power Apps プロジェクトの計画 | Microsoft Docs
description: これで、アプリの計画と設計が完了しました。 次のステップは、実際にそれを作成することです。 この記事では、キャンバス アプリとモデル駆動型アプリを作成する手順の概要を説明します。
author: taiki-yoshida
ms.service: powerapps
ms.topic: conceptual
ms.custom: guidance
ms.date: 06/16/2020
ms.author: tayoshi
ms.reviewer: kathyos
ms.openlocfilehash: 40e7dacf26977c459e90f2e1d6ed7559c3586ba7
ms.sourcegitcommit: 213c46f7055eb71b9064b0645d8d17cf8eaad179
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/16/2020
ms.locfileid: "3461602"
---
# <a name="making-phase"></a>作成フェーズ

これで、アプリの計画と設計が完了しました。 次のステップは、実際にそれを作成することです。

> [!TIP]
> 以下のリンクに加えて、[Microsoft Power Platform: 学習リソース](https://aka.ms/PowerPlatformResources) には、厳選されたリンクのコレクションがあります。

## <a name="basic-steps-for-making-canvas-apps"></a>キャンバス アプリを作成するための基本的な手順

以下は、キャンバス アプリを作成するための基本的な手順です。

1. データ ソースを設定する。

   - [エンティティの設定](../../maker/common-data-service/create-edit-entities.md) (Common Data Service 使用時)。

   - テーブルの設定 (データベース使用時)。

   - [リストの設定](https://support.office.com/article/create-a-list-in-sharepoint-0d397414-d95f-41eb-addd-5e6eff41b083) (SharePoint 使用時)。

2. [新しいアプリを作成する](../../maker/canvas-apps/getting-started.md#build-an-app)。

3. [コネクタを追加する](../../maker/canvas-apps/add-manage-connections.md)。

4. [次の画面を作成する](../../maker/canvas-apps/add-screen-context-variables.md):

   - ホーム画面

   - リスト ビュー

   - ビューのフォーム

   - 編集フォーム

5. [Power Automate フローを作成する](https://docs.microsoft.com/power-automate/get-started-logic-flow)。

## <a name="basic-steps-for-making-model-driven-apps"></a>モデル駆動型アプリを作成するための基本的な手順

以下は、モデル駆動型アプリを作成するための基本的な手順です。

1. [ソリューション](../../maker/model-driven-apps/distribute-model-driven-app.md) を作成する。

2. [エンティティ](../../maker/common-data-service/entity-overview.md) と [フィールド](../../maker/common-data-service/fields-overview.md) を定義してデータ モデルを設定する。

3. [セキュリティ ロール](https://docs.microsoft.com/power-platform/admin/security-roles-privileges) を設定する。

4. 新しいを [モデル駆動型アプリ](../../maker/model-driven-apps/build-first-model-driven-app.md) を設定して、サイト マップを作成する。

5. [フォーム](../../maker/model-driven-apps/create-design-forms.md) と [ビュー](../../maker/model-driven-apps/create-edit-views.md) をカスタマイズする。

6. [ビジネス プロセス フロー](https://docs.microsoft.com/power-automate/business-process-flows-overview) を設定する。

7. [ビジネス ルール](../../maker/model-driven-apps/create-business-rules-recommendations-apply-logic-form.md) を設定する。

8. [Power Automate フロー](https://docs.microsoft.com/power-automate/connection-cds) を設定する。

詳細: [モデル駆動型アプリのコンポーネントについて](../../maker/model-driven-apps/model-driven-app-components.md)

## <a name="developing-solutions-collaboratively"></a>共同でソリューションを開発する

複数のアプリ作成者でソリューションを開発する場合、コラボレーション手法は、作成するアプリケーションの種類によって異なります。

### <a name="canvas-apps"></a>キャンバス アプリ

[Power Apps コンポーネント](../../maker/canvas-apps/create-component.md)&mdash;再利用可能な構成要素のセット&mdash;を使用したり、作成した Power Apps コンポーネント上で他のユーザーと共有や共同作業に使用できるリポジトリである、コンポーネント ライブラリを使用することで、共同でキャンバス アプリを開発できます。 詳細: [PowerApps キャンバス アプリの共同開発](https://powerapps.microsoft.com/blog/collaborative-development-for-powerapps-canvas-apps/)

### <a name="model-driven-apps"></a>モデル駆動型アプリ

モデル駆動型アプリを開発する場合は、複数のアプリ作成者向けに指定されたソリューションと環境の使用を検討してください。 詳細: [ソリューションの概要](/powerapps/maker/common-data-service/solutions-overview)

> [!div class="nextstepaction"]
> [次のステップ: アプリをテストする](testing-phase.md)
