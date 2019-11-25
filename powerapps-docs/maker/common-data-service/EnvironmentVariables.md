---
title: 'プレビュー: ソリューションで環境変数を使用する | MicrosoftDocs'
description: 環境変数を使用して、ソリューション内のアプリケーション構成データを移行します。
Keywords: 環境変数、変数、モデル駆動型アプリ、構成データ
author: caburk
ms.author: caburk
manager: kvivek
ms.date: 10/22/2019
ms.service: powerapps
ms.topic: article
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: f0c3189fceebb785a022d04c58ff6cf71fd388bc
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "2758285"
---
# <a name="preview-environment-variables-overview"></a>プレビュー: 環境変数の概要 

[!INCLUDE[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

アプリおよびワークフローは多くの場合、環境間で異なる構成設定が必要です。 構成可能な入力パラメーターとして環境変数を使用すると、カスタマイズ内または追加ツールを使用して、ハードコーディング値と比較するデータを個別に管理できます。 ソリューション コンポーネントなので、パフォーマンスは、構成データをレコード データとしてインポートするよりもはるかに優れています。

環境変数を使用するメリット:
- 運用環境で構成可能な値を手動で編集する必要はありません。
- 1 か所で 1 つ以上の変数を構成し、複数のソリューション コンポーネント間のパラメーターのように参照します。
- コード変更をせずに値を更新します。
- [Common Data Service](https://docs.microsoft.com/powerapps/maker/common-data-service/data-platform-intro) が管理する詳細なレベルのセキュリティ。
- 変数の数に制限はありません (ソリューションの最大サイズは 29 MB)。
- 定義と値を個別または一緒にサービスします。
- [SolutionPackager](/powerapps/developer/common-data-service/compress-extract-solution-file-solutionpackager) と [DevOps](/powerapps/developer/common-data-service/build-tools-overview) ツールでサポートされているため、継続的インテグレーションと継続的デリバリー (CI/CD) が可能です。
- ローカライズのサポート
- 機能フラグと他のアプリケーション設定を管理するために使用できます。

> [!IMPORTANT]
> - これはプレビュー機能です。
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)] 

## <a name="how-they-work"></a>どのように機能しますか?
環境変数は最新のインターフェイスを介して、または [コードを使用する](https://docs.microsoft.com/powerapps/developer/common-data-service/work-with-data-cds) ことで作成および管理できます。 個別のJSONファイルは、ソリューション パッケージ内で値に対して作成されます。ソース コントロールで管理し、ビルド パイプラインで変更することもできます。 ExcelへのエクスポートおよびExcelからのインポートはサポートされています。 環境変数を作成した後、プラグイン、ワークフロー、そのほかのコンポーネント内の入力として使用できます。

## <a name="default-value"></a>既定値
このフィールドは、環境変数定義エンティティの一部であり、必須ではありません。 運用環境の既定値の設定または、異なる環境で値を変更する必要がない場合に設定します。

## <a name="value"></a>値
現在の値または上書き値とも呼ばれるこのフィールドは任意であり、環境変数値エンティティの一部です。 現在の環境の既定値を上書きする時に値を設定します。 次の環境で使用したくない場合はソリューションから値を削除します。 値は、エクスポートされた solution.zip ファイル内の個別の JSON ファイルに分割されます。 

>[!NOTE]
> 値は定義なしに存在することはできません。 インターフェイスは定義ごとに一つの値のみを作成できます。 

既定値と現在値の分離により、現在値とは別に定義と既定値を提供できます。 また、将来的に機能を拡張して、特定の実行時のコンテキストにスコープされた複数の値をサポートすることもできます。

## <a name="notifications"></a>通知
通知は、環境変数に値がないときに表示されます。 これは、変数に依存するコンポーネントが失敗しないように値を設定するための機能です。 また、パートナーは値なしで変数を送ることができ、顧客は値の入力を求められます。

>[!NOTE]
> パートナーが顧客に値を提供するよう求める独自のインターフェイスを構築することをお勧めします。 このステップがスキップされた場合、通知は失敗を防ぐのに役立ちます。 

## <a name="security"></a>セキュリティ
environmentvariabledefinition と environmentvariablevalue エンティティは両方とも、 [ユーザーまたはチームが所有](https://docs.microsoft.com/powerapps/maker/common-data-service/types-of-entities) しています。 環境変数を使用するアプリケーションを作成する場合は、ユーザーに適切なレベルのアクセス許可を割り当ててください。 詳細: [Common Data Service のセキュリティ](https://docs.microsoft.com/power-platform/admin/wp-security)。 

## <a name="current-limitations"></a>現在の制限
- キャッシング。 プラグインは、値をフェッチするためのクエリを実行する必要があります。 
- キャンバス アプリとフローは、エンティティ レコード データと同じように環境変数を使用できます。 将来的に、キャンバス アプリおよびフロー デザイナーに追加操作を組み込む予定です。 これにより、作成を簡素化したり、特定のアプリやフローによって使用されている環境変数の可視性を高めます。
- シークレット管理のための Azure Key Vault 統合。 現在の環境変数は、パスワードやキーのような安全なデータの保存には使用しないでください。
- データの種類は、最新のソリューション インターフェイスでのみ検証されますが、現在はプレビュー時にサーバーで検証されません。 
- 依存関係は、特定のコンポーネントの種類では適用されません。
- 環境変数をインポートするために Excel を使用する場合、必ず SchemaName に発行者の接頭辞を先頭に付加してください。

### <a name="see-also"></a>関連項目
[ビジネス プロセスを拡張するためのプラグインの使用](https://docs.microsoft.com/powerapps/developer/common-data-service/plug-ins) </BR>
[Web API サンプル](https://docs.microsoft.com/powerapps/developer/common-data-service/webapi/web-api-samples) </BR>
[Common Data Service を使用してゼロからキャンバス アプリを作成します。](https://docs.microsoft.com/powerapps/maker/canvas-apps/data-platform-create-app-scratch) </BR>
[Common Data Service を使用してフローの作成](https://docs.microsoft.com/flow/connection-cds)
