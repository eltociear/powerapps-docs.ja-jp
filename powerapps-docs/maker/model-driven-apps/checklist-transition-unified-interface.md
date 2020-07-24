---
title: 'チェックリスト: 統一インターフェイスへの移行 | MicrosoftDocs'
description: 統一インターフェイスに移行する準備が整っていることを確認するチェックリスト。
ms.custom: ''
ms.date: 05/21/2020
ms.reviewer: kvivek
ms.service: powerapps
ms.topic: article
author: Mattp123
ms.author: haybass
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 882d07a284dae31c4fe2ee5478d9b494df667f03
ms.sourcegitcommit: 4b6f187c9501332f9acca5978fa326621f2980e5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/22/2020
ms.locfileid: "3394728"
---
# <a name="checklist-unified-interface-transition"></a>チェックリスト: 統一インターフェイスへの移行

統一インターフェイスに移行する準備が整っていることを確認するには、この記事の手順に従います。 統一インターフェイスへの移行の準備状況は、基本的な互換性が目的なのか、新機能を最大限に活用するために再設計するのかにより異なります。 詳細については [統合インターフェイスの活用プレイブック](https://docs.microsoft.com/powerapps/maker/model-driven-apps/unified-interface-playbook) と [ユーザー エクスペリエンス ホワイト ペーパー](https://docs.microsoft.com/powerapps/maker/model-driven-apps/approaching-unified-interface) を参照してください。

この手順は Dynamics 365 の次のモデル駆動型アプリに適用されます。

- Dynamics 365 Sales

- Dynamics 365 Customer Service

- Dynamics 365 Field Service

- Dynamics 365 Project Service Automation

## <a name="run-the-power-apps-solution-checker-on-your-solutions"></a>ソリューションで Power Apps ソリューション チェッカーを実行する

[Power Apps ソリューション チェッカー](https://docs.microsoft.com/powerapps/maker/common-data-service/use-powerapps-checker) は、一連のベスト プラクティス ルールに対してソリューションの豊富な静的分析チェックを実行し、問題のあるパターンを迅速に特定します。 チェックが完了すると、特定された問題、影響を受けるコンポーネントとコード、各問題を解決する方法が説明されたするドキュメントへのリンクが一覧になった詳細なレポートを受け取ります。

ソリューション チェッカーは、これらのソリューション コンポーネントを分析します:

-   Common Data Serviceプラグイン

-   Common Data Serviceユーザー定義のワークフロー活動

-   Common Data Service Web リソース (HTML および JavaScript)

-   SDK メッセージ手順などの Common Data Service 構成

**考慮事項** 

-   ソリューション チェッカーが検出した潜在的な問題が影響するのは、統一インターフェイスだけではありません。結果を確認する際は、移行に影響を与える要因に注意が必要です。

-   自動コード レビューの場合と同様に、一部の問題は誤報であり、そのアプリケーションを統一インターフェイスで実行できないわけではありません。

-   プラグイン、カスタム ワークフロー活動、SDK メッセージ手順の構成など、サーバー側で実行されるロジックはユーザー インターフェースに影響を与えません。したがって統一インターフェースへの移行に影響しないはずです。

-   すべての問題が統一インターフェースに直接関係しない場合も、アプリケーション全体の正常性を向上するためによく確認することを推奨します。

## <a name="check-third-party-solutions-compatibility-with-unified-interface"></a>サードパーティ ソリューションと統一インターフェイスの互換性を確認する


統一インターフェイスに移行する前に、アプリケーションで使用するサードパーティのソリューションが統一インターフェイスで機能することを確認することが重要です。

-   [AppSource](https://appsource.microsoft.com) で ISV (独立ソフトウェア ベンダー) アドインをインストールした場合は、**環境** > [環境名] > **ソリューション管理** を選択し、 [Power Platform 管理センター](https://admin.powerplatform.microsoft.com) でアップグレードが利用可能かどうか確認します。

-   AppSource の外部で提供されたサードパーティ ソリューションを使用している場合は、プロバイダー (パートナーや ISV) に連絡して、アプリを統一インターフェイスに更新する新しいバージョンを入手してください。

> [!NOTE]
> サードパーティ ソリューションが統一インターフェイスと互換性のあるバージョンに更新する予定がない場合は、これらの機能をネイティブ プラットフォームの機能または互換性のある代替ソリューションに置き換えるパスを特定することが重要です。

## <a name="identify-replacements-for-deprecated-features"></a>廃止された機能の代替機能を見つける

非推奨のクライアント API と機能に関する **Power Apps ソリューション チェッカー** の出力と [で予定されている重要な変更 (廃止)](https://docs.microsoft.com/power-platform/important-changes-coming) に含まれる情報に基づいて、統一インターフェイス プロジェクトで修正や置換が必要なカスタマイズと機能について十分な理解が必要です。

注意が必要な最も一般的な領域の一部を次に示します。

-   **クライアント API**: 推奨する交換方法は [こちら](https://docs.microsoft.com/power-platform/important-changes-coming#some-client-apis-are-deprecated) に記載されています。

-   **プロセス ダイアログ**: 推奨するダイアログの代替は [こちら](https://docs.microsoft.com/flow/replace-dialogs) に記載されています。

-   **タスク フロー**: タスク フローの置き換えには [業務プロセス フロー](https://docs.microsoft.com/power-platform-release-plan/2019wave2/microsoft-flow/business-process-immersive-experiences) の使用を検討します。

-   **Dynamics 365 for Outlook (COMアドイン)** : [非推奨な](/power-platform/important-changes-coming#dynamic-365-for-outlook-is-deprecated)Dynamics 365 for Outlook (COMアドイン) を最新で軽量な[Dynamics 365 App for Outlook](https://docs.microsoft.com/dynamics365/outlook-app/overview) と交換することを検討してください。 スムーズな移行を行うための詳細情報と手順については、[Dynamics 365 for Outlook（COMアドイン）ハンドブック](https://aka.ms/OutlookCOMPlaybook) をダウンロードしてください

- **Dynamics 365 Customer Service**:
    -   サービスのスケジューリング : 従来のサービス スケジューリングの代わりに、[Universal Resource Scheduling](https://docs.microsoft.com/dynamics365/common-scheduler/schedule-anything-with-universal-resource-scheduling) の使用を検討してください。
    - [非推奨のナレッジ マネジメント エンティティ](https://docs.microsoft.com/previous-versions/dynamicscrm-2016/administering-dynamics-365/dn265924(v=crm.8)#some-knowledge-management-entities-are-deprecated) : 最新のナレッジ マネジメント エンティティを操作するには、[ナレッジ記事の作業をする](https://docs.microsoft.com/dynamics365/customer-service/work-knowledge-articles)を参照してください。
    - [非推奨の契約エンティティ](https://docs.microsoft.com/power-platform/important-changes-coming#contracts-contract-line-items-and-contract-templates-entities-are-deprecated) : 資格に移行するには、[資格移行戦略の契約](https://docs.microsoft.com/dynamics365/customer-service/contract-to-entitlement-migration) を参照してください。 

## <a name="test-your-application-in-unified-interface"></a>統一インターフェイスでアプリケーションをテストする

統一インターフェイスでアプリケーションをテストする簡単な方法の 1 つは、運用環境のコピーで [**統一インターフェイスのみを有効化**](https://docs.microsoft.com/power-platform/admin/enable-unified-interface-only) オプションをオンにすることです。 統一インターフェイスを有効化すると、**Dynamics 365 – カスタム** アプリを使用してアプリケーションにアクセスし、コンテキストに関連する使用事例をテスト可能になります。

### <a name="test-your-business-and-technical-scenarios"></a>ビジネスと技術のシナリオをテストする

潜在的に影響を受ける可能性のある対象に重点を置きます。

-   **業務プロセス** 業務プロセス フロー、ビジネス ルールなど

-   **カスタマイズ** フォーム、ビュー、コマンド バー ボタン、Web リソース、グラフなど

> [!TIP]
> この初期テストの実行と同時に、ユーザー エクスペリエンスも試す: これは完全に意味と価値がありますか。 削除/改善/追加が必要なのは何ですか。 たとえば、現在のビューのリストは関連しますか。 または、ユーザーは自分のビューの作成を強制されますか。

### <a name="identify-gaps"></a>ギャップの識別

-   ソリューション チェッカーとサードパーティ ソリューション更新で、まだ発見されていない潜在的なリグレッション。

-   最適化 (セクションやタブの再編成による新しいフォームのレンダリングなど) または特定のトレーニングにつながる可能性があるユーザーの問題点。

-   軽量 Dynamics 365 App for Outlook の代わりに従来の Outlook COM アドインを使用するなど、従来の Web クライアントに対するその他の依存関係。

## <a name="define-your-app-strategy-and-settings"></a>アプリの戦略と設定を定義する

統一インターフェイス向けに最適化されておらず互換モードで実行する **Dynamics 365 – カスタム** アプリを使用する代わりに、Microsoft のファーストパーティ アプリを活用するか、独自のアプリを作成することを推奨します。

統一インター フェイスに向けて、最適化がされている Dynamics 365 アプリは以下のとおりです :

-   Dynamics 365 Sales ハブ

-   Dynamics 365 Customer Service ハブ

-   Dynamics 365 Marketing

-   Dynamics 365 Field Service (バージョン 8.x 以降)

-   Dynamics 365 Project Service Automation (バージョン 3.x 以降)

### <a name="what-are-model-driven-apps"></a>モデル駆動型アプリとは。

**モデル駆動型アプリ** は、Power Apps を使用して作成できるアプリの種類で、組織内の役割に応じてユーザーに合わせたエクスペリエンスを提供するのに役立ちます。 たとえば営業担当者が同じ環境のデータを使用している場合でも、顧客サービス担当者と異なるモデル駆動型アプリにとってまったく異なるエクスペリエンスを使用できます。 Common Data Service 環境で複数のモデル駆動型アプリを作成できます。 詳細: [モデル駆動型アプリとは](https://docs.microsoft.com/powerapps/maker/model-driven-apps/model-driven-app-overview)

上記の Dynamics 365 アプリは、モデル駆動型アプリの例です。

### <a name="how-to-define-your-app-strategy"></a>アプリ戦略を定義する方法を教えてください。

次の質問について検討してください。

1.  特定の業務プロセスでユーザーを複数のグループに分割できますか。

2.  このグループに関して、表示や実行する内容に異なる要件がありますか。

3.  アプリを使用せずに異なるユーザー エクスペリエンスを実現するのは難しそうですか。

これらの質問に「はい」と答えた場合は、複数のアプリを使用することを検討してください。

これは、各グループや役割について業務プロセスのコンテキストでエクスペリエンスを再考する機会です。

### <a name="out-of-the-box-apps-for-example-sales-hub-or-customized-apps"></a>(営業ハブのような) 標準のアプリか、それともカスタマイズしたアプリか。

-   これはエクスペリエンスを調整する方法によります。

-   カスタマイズがほとんど不要な場合、またはファーストパーティ アプリの更新を利用する場合は、ネイティブ アプリの使用を検討してください。

-   標準アプリとカスタマイズのエクスペリエンスと更新をさらに制御する場合は、独自のアプリを作成します。

### <a name="once-you-have-defined-your-app-strategy-what-should-be-the-next-steps"></a>アプリ戦略を定義したら、次のステップは何ですか。

1.  対象のアプリをカスタマイズし、ユーザーに必要な機能のみを含めます。 シンプルが一番です。 散乱を防ぎ、ユーザーの作業効率を高めます。

2.  未使用のアプリからセキュリティ ロールを分離します。

## <a name="review-your-apps-settings-and-user-experience-fundamentals"></a>アプリ設定とユーザー エクスペリエンスの基本をレビューする

### <a name="app-settings"></a>アプリの設定

-   サイトマップに含まれていない場合も、必要なエンティティをすべてアプリに含めます。  
    
-   **セキュリティ ロール** ダイアログ ボックスの **カスタマイズ** タブで、**モデル駆動型アプリ** に **読み取り** 特権を提供します。

-   ユーザーが従来の Web クライアントを使用しない場合は **統一インターフェイスのみ** モードを有効化します。 **設定** > **詳細設定** を選択して引き続き管理機能にアクセスできます。

-   よりシンプルなアプリ URL を作成します。 例: https://\*.crm.dynamics.com/apps/MyApp*

-   ユーザーがアクセスできるアプリの数をできるだけ制限します。  
    
    > [!TIP]
    > **統一インターフェイスのみを使用** が **はい** に設定され、ユーザーが 1 つのアプリのみにアクセスできる場合、ルート URL (https://\*.crm.dynamics.com)* にアクセスすると自動的にアプリにリダイレクトされます。

### <a name="optimize-navigation-sitemap"></a>ナビゲーションの最適化 (サイトマップ)

-   **グループ** で調整した最も使用する **サブ領域** (ダッシュボードやエンティティなど) に 1 つのメイン **領域** を定義します。

-   使用頻度の低い機能 (構成や設定など) に 1 つ以上の追加領域を作成します。 このアイデアは、ユーザーが作業の重要なことだけに集中できるようにすることです。

### <a name="update-icons"></a>アイコンの更新

-   統一インターフェイスへの移行は、アイコンを刷新する良い機会です。

-   画面の解像度に関係なく適切に表示されるため **SVG** 形式を推奨します。

    > [!TIP]
    > SVG アイコン形式の例。  
    > 幅と高さ: 16px; パディング: 0px; 背景: 透明; アイコンの色: \#FF000000  
    表示の問題を回避するにはエディタ (メモ帳など) で SVG ファイルを開いて fill="\#000000" を削除します

## <a name="enrich-your-app-with-unified-interface-exclusive-features"></a>統一インターフェイスの独自機能でアプリを充実させる

-   ユーザーが各アプリにアクセスしたときに表示する **ようこそページ** を作成します。 これは最初の手順でユーザーをガイドする絶好の機会です。

-   既存の **カスタム コントロール** を使用して、特にモバイルでほとんどのフィールド タイプの使いやすさを改善します。 たとえば、0 〜 5 のフィールド評価を星に置き換え、予定のビューをカレンダー ビューで置き換え、サブグリッド ビューをカード フォームで置き換えます。

-   フォームの **参照パネル** を活用して、複数のビュー、簡易表示、サポート情報検索機能を 1 か所にまとめます。

-   [Power Apps Component Framework](https://docs.microsoft.com/powerapps/developer/component-framework/overview) を活用してカスタム コントロールをさらに追加します。 コミュニティ、パートナー、ISV から入手できます。

-   フォームに [キャンバス アプリ](https://docs.microsoft.com/powerapps/maker/canvas-apps/getting-started) を埋め込み、アプリケーションを簡単に拡張します。 コード不要または低コードでアプリを拡張します。カスタムの HTML/JS Web リソースを開発する必要はありません。

-   フォームに **Power BI** レポートとタイルを埋め込みます。1 つのビューに複数のシステムのデータを統合します。

-   **対話型ダッシュボード** を活用してダッシュボード コンポーネント全体のグローバル フィルターを許可するワンストップ ワークプレースの構成を検討してください。

-   ユーザーがヘルプとガイダンスをすばやく入手できるように **カスタム ヘルプ ウィンドウとガイド付きタスク** を構成します。

## <a name="conduct-user-acceptance-testing"></a>ユーザー受け入れテストを実施する

アプリケーション、ビジネス シナリオ、技術シナリオを、運用環境と同様の条件でビジネス ユーザーが統一インターフェイスでテストすることが非常に重要です。 このユーザーはビジネスの意思決定者として行動して、ビジネス全体で知識を拡大します。

テストは、ユーザーをすべて統一インターフェイスに移行する前に対処すべき残りの項目を特定するのに役立ちます。

## <a name="update-user-training-materials"></a>ユーザーのトレーニング教材を更新する

既存および計画中のトレーニング教材のレビューを実施し、最新のスクリーンショットがあることを確認し、ユーザー フローに加えた変更をすべて反映します。

## <a name="check-your-transition-date"></a>移行日を確認する

2020 年 12 月 1 日をもって、[従来の Web クライアントは利用できなくなります](https://docs.microsoft.com/power-platform/important-changes-coming#legacy-web-client-is-deprecated)。
問題に対処する時間があることを確認するために、事前に適切な移行を確認します。
