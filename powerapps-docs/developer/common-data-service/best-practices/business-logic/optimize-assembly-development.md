---
title: ユーザー定義のアセンブリ開発を最適化する | MicrosoftDocs
description: 個々のプラグイン/ユーザー定義ワークフロー活動を単一のカスタム アセンブリに統合してパフォーマンスおよび保守性を改善し、アセンブリ サイズがサンドボックス アセンブリ サイズの上限に近い場合は、プラグイン / ユーザー定義ワークフロー活動をユーザー定義アセンブリに移動することを検討してください。
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: sunilg
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 1/15/2019
ms.author: phecke
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 44671a13acf299663544527ed3dc124737f3b7b4
ms.sourcegitcommit: 2fd873a1ea17f419f6194714efffa47a9bd00c2e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "3506524"
---
# <a name="optimize-assembly-development"></a>アセンブリ開発を最適化する

**カテゴリ**: パフォーマンス、保守性、設計

**影響の可能性**: 低い

<a name='symptoms'></a>

## <a name="symptoms"></a>現象

カスタム アセンブリの開発時には、考慮すべき事項がいくつかあります:

1. 多数のユーザー定義ワークフロー活動を持つアセンブリは、登録時にアップロードに時間がかかることがあります。
1. 異なる複数のカスタム アセンブリ
    - 保守性の複雑さの増大
    - プラグイン実行期間の増大の可能性
1. Common Data Service でのサンドボックス アセンブリ サイズの制約は16 MBです。


<a name='guidance'></a>

## <a name="guidance"></a>ガイダンス

### <a name="limit-the-number-of-custom-workflow-activities-in-a-single-assembly"></a>1 つのアセンブリのユーザー定義ワークフロー活動の数を制限する

プラグインの登録中にユーザー定義ワークフロー活動を持つアセンブリをアップロードすると、ユーザー定義ワークフロー活動に追加のチェックが必要になります。

何百もの通常のプラグイン タイプを持つアセンブリは、非常に迅速にアップロードできますが、100 を超えるユーザー定義ワークフロー活動があるアセンブリは、登録または更新時に数分またはタイムアウトする場合があります。 1 つのアセンブリに含めるユーザー定義ワークフロー活動は 50 以下にすることをお勧めします。

### <a name="consolidate-plug-ins-or-custom-workflow-activities-into-a-single-assembly"></a>プラグインまたはユーザー定義ワークフロー活動を単一のアセンブリに統合します。

Common Data Service ソリューション用に開発されたプラグインおよびユーザー定義ワークフロー活動は、単一の Visual Studio プロジェクト内に存在させる必要があります。 プラグインが次の例外に当てはまらない限り、個別のプラグインまたはユーザー定義ワークフロー活動を単一の Visual Studio プロジェクトまたはアセンブリに統合することを考量してください。

1. プラグイン / ユーザー定義のワークフロー活動は、選択的に 1 つの環境に展開する必要があります。
1. Common Data Service インスタンスの場合、物理アセンブリ サイズは 16 MB に近いサイズまたはそれ以上です。
1. [1 つのアセンブリのユーザー定義ワークフロー活動の数を制限する](#limit-the-number-of-custom-workflow-activities-in-a-single-assembly) で説明したように、アセンブリには 50 を超えるユーザー定義ワークフロー活動があります


### <a name="move-plug-inscustom-workflow-activities-into-multiple-assemblies"></a>プラグイン / ユーザー定義ワークフロー活動を複数のアセンブリに移動する

Power Apps および Dynamics 365 (online) には 16 MB のアセンブリ サイズ制限があり、これは変更できません。 アセンブリ サイズが 16 MB に近づいたら、プラグイン/ユーザー定義ワークフロー活動を複数のアセンブリに移動することを検討します。

<a name='problem'></a>

## <a name="problematic-patterns"></a>問題となるパターン

### <a name="assemblies-take-a-long-time-to-upload-when-being-registered"></a>アセンブリは、登録時にアップロードに時間がかかります

ユーザー定義ワークフロー活動タイプのプラグインが登録中にアップロードされると、タイプごとに追加の検証チェックが必要になります。 アセンブリに 100 を超えるユーザー定義ワークフロー活動タイプのプラグインが含まれている場合、チェックを完了するのに数分かかる可能性があり、タイムアウトするリスクがあります。

### <a name="multiple-assemblies"></a>複数のアセンブリ

複数の領域に影響を与える可能性のあるアセンブリが複数ある:

1. パフォーマンス - 各アセンブリには、Common Data Service によって管理されるライフサイクルがあります。  これにはアセンブリの読み込み、キャッシュ、アンロードが含まれます。  複数のアセンブリが原因でサーバー上で多くの作業 (アセンブリの読み込みやキャッシュ) が実行されており、プラグイン/ユーザー定義ワークフロー活動の全体の実行時間に影響を与える可能性がある。

2. 保守性 - 複数のプラグイン/ユーザー定義ワークフロー活動があると、Visual Studio プロジェクトのアプリケーション ライフサイクル管理 (ALM) が複雑化する原因となります。 これにより、特定のプラグイン/ユーザー定義ワークフロー活動のプロジェクトを更新またはパッチする場合、プラグイン/ユーザー定義ワークフロー活動をソリューション内にパッケージする場合、プラグイン/ユーザー定義ワークフロー活動を展開内で管理する場合のリスクと作業時間が増大します。

### <a name="assembly-larger-than-16-mb"></a>16 MB より大きいアセンブリ
16 MB より大きい ユーザー定義アセンブリは、Common Data Service 内に登録できません。

<a name='additional'></a>

## <a name="additional-information"></a>追加情報

多くの場合、開発者はプラグイン/ユーザー定義ワークフロー活動ごとに新しい Visual Studio プロジェクトを作成します。  つまり、プラグイン/ユーザー定義ワークフロー活動ごとに個別のアセンブリが生成されることになります。

<a name='seealso'></a>

### <a name="see-also"></a>関連項目

[イベント フレームワーク](../../event-framework.md)<br />
[ビジネス プロセスを拡張するためのプラグインの使用](../../plug-ins.md)<br />
