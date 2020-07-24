---
title: Power Apps アーキテクチャ デザイン - ロジックを配置する場所| Microsoft Docs
description: 'システムのどこにロジックを配置するかを決定する際の考慮事項: キャンバス アプリ、モデル駆動型アプリ、Common Data Service、または Power Automate フロー?'
author: taiki-yoshida
ms.service: powerapps
ms.topic: conceptual
ms.custom: guidance
ms.date: 06/16/2020
ms.author: tayoshi
ms.reviewer: kathyos
ms.openlocfilehash: 4ac21a3f7176ff5a6d68543bc867b3db62dd2eb3
ms.sourcegitcommit: 213c46f7055eb71b9064b0645d8d17cf8eaad179
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/16/2020
ms.locfileid: "3461574"
---
# <a name="where-to-place-logic-canvas-apps-model-driven-apps-common-data-service-or-power-automate-flows"></a>ロジックを配置する場所: キャンバス アプリ、モデル駆動型アプリ、Common Data Service、または Power Automate フロー?

アプリには、データ検証 (メールアドレスの正しい形式を使用するなど)、計算、データに基づく次のプロセス ステップの選択、すべての必須フィールドにデータがある場合のボタンの有効化などのビジネス ロジックが含まれます。 この記事では、システムのどこにロジックを配置するかを決定する際の考慮事項について説明します。

## <a name="power-apps-canvas-apps"></a>Power Apps キャンバス アプリ

数式を使用して、キャンバス アプリにロジックを設定します。 すべての数式ロジックは、アプリが実行されているデバイスで処理されます。 ロジックが複雑になるほど、デバイスがすべてのロジックを処理するために必要な処理能力が高くなります。

アプリのパフォーマンスを維持するには、キャンバス アプリにロジックを配置するときに次のことを考慮する必要があります:

- 変更を画面上にすぐに表示する必要がある状況に使用する

- 単純なロジックのみを使用し、数十行もの複雑な数式を避ける

- 数式内のいくつかのデータ コネクタに限定する

- ロジックを使用してデータを操作または変換しない

- 一度に複数のレコードを処理しない (たとえば、ForAl l関数の使用は避ける)

詳細: [Power Apps でキャンバス アプリの数式を使用する](../../maker/canvas-apps/working-with-formulas.md)

## <a name="power-apps-model-driven-apps"></a>Power Apps モデル駆動型アプリ

モデル駆動型アプリは、ロジックを実行するいくつかの方法を提供します。 すべての開発者に適したロー コード メソッドを使用するロジックには、4 つのタイプがあります:

- ビジネス プロセス フロー

- ワークフロー

- 操作​​

- ビジネス ルール

さらに、プロの開発者は次のタイプのロジックを使用できます:

- クライアント側スクリプト

- API 開発

- Web リソースでのコードの使用

これらのオプションはすべて、アプリを実行するデバイス上で実行されます。 次の場合は、モデル駆動型アプリにロジックを配置することを検討してください:

- ロジックをデバイス上で実行する必要があります。

- ロジックには複数のエンティティ (テーブル) が必要です。

- すぐに使える機能では利用できない高度なロジックが必要です。

一般に、複雑なロジックでアプリを作成する場合は、キャンバス アプリを使用してすべてをしようとするのではなく、モデル駆動型アプリの使用を検討してください。

詳細: [モデル駆動型アプリの業務ルールおよびフローによるカスタム ビジネス ロジックの適用](../../maker/model-driven-apps/guide-staff-through-common-tasks-processes.md)

## <a name="power-automate-flows"></a>Power Automate フロー

複雑なロジックを実行する必要がある、複数のコネクタが必要である、またはアクションが完了するまでユーザーを待たせたくないなどのユース ケースでは、Power Automate フローは、ロジックを実行するための優れたオプションを提供します。 次の場合は、Power Automate フローを検討してください:

- ロジックは複数のコネクターにわたって実行する必要があります。

- 承認プロセスを作成しています。

- 出力は別の形式で作成されています。

- デバイス側の処理能力への依存を減らしたい。

詳細: [Power Automate に関するドキュメント](https://docs.microsoft.com/power-automate/)

## <a name="common-data-service"></a>Common Data Service

Common Data Service にロジックを設定することで、デバイスではなくサービスですべてのロジックが実行されるようにすることができます。 これにより、アプリのパフォーマンスが向上し、ロジックがアプリやフローから独立し、データが特定の方法で使用されるようになります。

たとえば、取引先企業エンティティを使用するすべてのアプリとフローにアドレスを入力する必要がある場合は、各アプリとフローではなく Common Data Service にこのロジックを設定する必要があります。

Common Data Service にロジックを適用する方法はいくつかあります。 ロー コードを使用して、自動番号付けフィールド、計算フィールド、ロールアップ フィールドなどを設定できます。 プロの開発者は、プラグインを作成するか、ワークフローの拡張機能を開発することにより、コードを使用するビジネス ロジックを適用できます。

詳細: [Common Data Service でビジネスロジックを適用](../../maker/common-data-service/cds-processes.md)

> [!div class="nextstepaction"]
> [次のステップ: アプリとデータを保護する](security.md)
