---
title: あらゆる種類のアプリで作業する| MicrosoftDocs
ms.custom: ''
ms.date: 06/16/2020
ms.reviewer: Mattp123
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- powerapps
author: mmercuri
ms.author: mmercuri
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: f0b9f6cf8ef24736b68c6ccae44f470c20c50d19
ms.sourcegitcommit: 75efc726828507593b1ae38a456d28e00d27b777
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "3517178"
---
# <a name="work-with-any-type-of-app"></a>あらゆる種類のアプリで作業する 

Common Data Service は、あらゆる種類のアプリ＆ &mdash;モバイル、ウェブ、デスクトップ、デバイス、システム、またはサービスに統合するための複数の方法を提供します。 クラウド ソリューションの場合、ソリューションが展開されているモデルに関係なく、サービスとしての &mdash; インフラストラクチャ (IaaS)、サービスとしてのプラットフォーム (PaaS)、またはサービスとしてのソフトウェア (SaaS) を統合するための方法がいくつかあります。 IaaS ベースのソリューションの場合、ソリューションがコンテナー内で実行されている場合、統合アプローチもうまく機能します。

場合によっては、アプリは、Common Data Service に含まれるビジネス ロジックを使用して達成できます。 他の場合では、イベントや Common Data Service OData API を介して、またはプラグインを使用しての統合が含まれます。

## <a name="defining-business-logic"></a>ビジネス ロジックを定義する

Common Data Service 内のエンティティは、豊富なサーバー サイドのロジックと検証を使用してデータ品質を保証し、エンティティ内でデータを作成し、使用する各アプリケーションにて繰り返し使用されるコードを削減できます。

- **ビジネス ルール** は、複数のフィールドとエンティティ間でデータを検証し、データの作成に使用されたアプリケーションに関係なく、警告メッセージとエラー メッセージを表示します。 詳細: [エンティティに対する業務ルールの作成](/powerapps/maker/common-data-service/data-platform-create-business-rule)

- **業務プロセス フロー**は、ユーザーがデータを統一して入力し、毎回同じ手順に従うようにします。 ビジネス プロセス フローでは、現在モデル駆動型アプリでのみサポートされています。 詳細: [ビジネス プロセス フローの概要](/power-automate/business-process-flows-overview)

- **ワークフロー**: ユーザーとの対話なしでビジネス プロセスを自動化します。 詳細: [クラシックCommon Data Serviceワークフロー](/power-automate/workflow-processes)

- **コードによるビジネス ロジック**: 高度な開発者シナリオをサポートし、アプリをコードを通じて直接拡張します。 詳細: [コードによりビジネス ロジックを適用する](/powerapps/developer/common-data-service/apply-business-logic-with-code)

## <a name="integrating-with-apps-by-using-events"></a>イベントを使用したアプリとの統合

アプリ統合の一般的なアプローチは、イベントを使用することです。 たとえば、Common Data Service で新しいレコードを追加するなどのイベント、そしてこれは、アクションを実行できるように関連システムに通信する必要があります。 たとえば、新しいサポート リクエストが発生した場合、割り当てられたサポート スタッフに SMS メッセージが送信される可能性があります。

この双方向性は反対方向にも発生する可能性があります&mdash;外部システムでの更新により、データが追加、更新、または Common Data Service 環境から削除される可能性があります。

Common Data Service で最も人気のあるアプローチには、webhook、Azure メッセージング (Service Bus、Event Hubs)、Azure Logic Apps、または Power Automate が含まれます。

![Common Data Service でのイベント](media/cds-events.png "Common Data Service でのイベント")

### <a name="webhooks"></a>Webhook

Common Data Service により、webhooks を使用してサーバーで発生するイベントに関するデータを Web アプリケーションに送信できます。 WebHooks は、Web API およびサービスを公開/登録モデルと接続するための軽量の HTTP パターンです。 ｗebhook の送信側は、イベントに関する情報を使用して受信側のエンドポイントに要求を行うことで、受信側にイベントについて通知します。

Webhook を使用すると、開発者と ISV は Common Data Service のデータを、外部サービスでホストされている自らのカスタム コードに統合できます。 ｗebhook モデルを使用することにより、認証ヘッダーまたはクエリ文字列パラメーター キーを使用してエンドポイントを保護できます。 これは Shared Access Signature よりも簡単です<!--Was SAS. Should be no caps, no abbreviation via Cloud Style Guide.--> Azure Service Bus の統合で使用される認証モデル。

- webhook は、ご使用のホステッド Web サービスがメッセージを処理できるポイントまでのみスケールできます。

- Webhook では同期ステップと非同期のステップが可能です。

- Webhook は JSON ペイロードを使った POST 要求のみを送信し、任意のプログラミング言語または任意の場所でホストされる Webアプリケーションで使用できます。

- Webhook は、プラグインまたはユーザー定義のワークフロー活動から呼び出すことができます。

### <a name="azure-service-bus"></a>Azure Service Bus

Service Bus は Common Data Service ランタイムデータと外部のクラウド ベースの基幹業務アプリケーションの間で、安全かつ信頼性の高い通信チャネルを提供します。 この機能は異なる Common Data Service システムやその他の Common Data Service サーバーを変更されたビジネス データと同期させる場合に特に役立ちます。

イベントの順序は次のとおりです。

- リスナー アプリが Service Bus ソリューション エンドポイントに登録され、Common Data Service リモート実行コンテキストをサービス バスでアクティブにリスニングし始めます。

- ユーザーは、登録されている標準のプラグインかユーザー定義の Azure 認識プラグインの実行をトリガーする、Common Data Service での一部の操作を実行します。 このプラグインが、非同期サービス システム ジョブを介して、現在の要求データ コンテキストのサービス バスへのポストを開始します。

- Common Data Service によってポストされたクレームが認証されます。 次に、サービス バスが、リモート実行コンテキストをリスナーに渡します。 リスナーはコンテキスト情報を処理し、その情報に対してビジネス関連タスクを実行します。 サービス バスから非同期サービスにポストの成功が通知され、関連するシステム ジョブが完了ステータスに設定されます。

サービスバスは Common Data Service アプリケーションとサービス バス ソリューション リスナー アプリケーションの間で要求されたメッセージのデータ コンテキストを中継します。 またサービス バスはデータ セキュリティも提供し、これにより投稿した Dynamics 365 データには承認済みのアプリケーションのみがアクセスできます。 データ コンテキストをサービス バスに投稿し、リスナー アプリケーションがそれを読み込むために Common Data Service が行う認証は、Azure Shared Access Signatures によって管理されています。

詳細: [サービス バス](https://azure.microsoft.com/services/service-bus/) および [サービス バス承認と承認](https://azure.microsoft.com/documentation/articles/service-bus-authentication-and-authorization/)

## <a name="logic-apps-and-power-automate"></a>ロジック アプリと Power Automate

Azure を介して提供されるロジック アプリ、Microsoft Power Platform を介して提供される Power Automate は、アプリケーションのイベントやスケジュール上のデータと統合する、またはデータベース、システム、サービス、SaaS で活動別に統合するために使用できるワークフローをトリガーできます。

![ロジック アプリと Common Data Service 付き Power Automate](media/logic-apps-and-power-automate.png "ロジック アプリと Common Data Service を使った Power Automate")

これらのワークフローは、ロジックを実行し、データベース、PaaS、SaaS への何百ものコネクタを使用してこれらのシステムと対話できます。

たとえば、SQL などのリレーショナル データベースにレコードが追加されると、Common Data Service でこのデータを挿入できるワークフローをトリガーする時があります。

サービスの Open API (旧称 Swagger) 定義を使用してカスタム コネクタを作成する機能により、IaaS および Azure Kubernetes Service (AKS) で実行されているサービス、関数、コードを含めることも簡単にできます。

## <a name="integrating-common-data-service-into-apps-with-the-odata-api"></a>OData APIを使用して Common Data Service をアプリに統合する

すべての一般的なプログラミング言語は、REST ベースの API との統合の形式をサポートしています。

![OData API を使った Common Data Service](media/cds-with-odata.png "OData API を使った Common Data Service")

Common Data Service は、各種のプログラミング言語、プラットフォーム、およびデバイスで使用できる開発作業を提供します。 Web API は、多様なデータ ソースに対して RESTful API を構築して使用するための OASIS 標準規格 OData (オープン データ プロトコル)、バージョン 4.0 を実装します。 このプロトコルの詳細については、 [www.odata.org](https://www.odata.org/) で説明されています。この規格についての詳細は、 [www.oasis-open.org](https://www.oasis-open.org/standards#odatav4.0) をご覧ください。

Common Data Service が "API ファースト" のアプローチをとります。 つまり、このサービスはデータをクエリするメカニズムを提供するだけでなく、ビジネス ルールや制約などに関するサービスからのメタデータも提供し、インテリジェントで応答性の高いアプリやサービスの構築に使用できます。

API は OAuth を使用して保護されています。 OAuth では、認証に ID プロバイダーが必要です。 Common Data Service については、Azure Active Directory (Azure AD) が ID プロバーダーとなります。 Microsoft の職場または学校のアカウントを使用して Azure AD で認証するには、Azure AD 認証ライブラリ (ADAL)を使用します。

Common Data Service Web API を始めることに関する詳細については、[Common Data Service Web API を使用する](/powerapps/developer/common-data-service/webapi/overview).を参照してください。

OAuthを使用した Common Data Service Web API を使用することに関する細については、、[Common Data Service を使って OAuth を使用する](/powerapps/developer/common-data-service/authenticate-oauth) をご覧ください。

## <a name="plug-ins"></a>プラグイン

Common Data Service は、API とデータの間に位置するコードを作成する機能を提供します。  .NET で記述されたこのコードは、*プラグイン* として参照されます。 プラグインは API とデータの間にあるため、すべてのアプリに同じロジックを適用します。

プラグインは同期または非同期であり、次のタスクを実行します。 

- エラーをユーザーに返します。

- Common Data Service データをクエリして、実行するロジックを評価します。

- データ操作を実行します。

- アウトバウンド HTTP リクエストを実行します。

プラグインは、ここに示されているイベント パイプラインのポイントに登録されます。

![イベント パイプラインにプラグイン](media/plug-in-event-pipeline.png "イベント パイプラインにプラグイン")

イベント パイプライン内では、次のイベントが発生する可能性があります。 

- **リクエスト** と **応答** は、**確認** や **拒否** されたり、あるいはイベント パイプラインのいくつかのステップで **操作される** ことができます。

- **検証ハンドラー** は、カスタム例外をスローして、ロジックが無効と見なす操作を拒否できます。

- **操作前ハンドラー** は、データベース操作の前にリクエストを変更できます。

- **操作後ハンドラー** は応答を変更できます。

- **非同期ハンドラー** は、応答が返された後に自動化を実行します。

プラグインでの 1 つの制約は、プラグインが自己完結型でなければならないことです。 統合コードが他のライブラリへの参照を必要とする場合、Azure Functions を使用して統合を行うことができます。

### <a name="azure-functions"></a>Azure Functions

Azure Functions は、ビジネスおよび統合ロジック用のサーバーレス コード実行オプションを提供します。

![Azure Functions を使った Common Data Service](media/azure-functions.png "Azure Functions を使った Common Data Service")

関数は、外部システム、サービス、またはコードからの呼び出しによってトリガーされます。 Common Data Service については、そのトリガーは、Service Bus、Webhook、またはプラグインからの呼び出しを使用して、Common Data Service から直接来ることができます。 さらに、Azure Functions の呼び出しは、Logic Apps または Common Data Service コネクタを含む Power Automate のいずれかでフローを介して開始されることができます。

詳細: [ビジネス プロセスを拡張するためのプラグインの使用](/powerapps/developer/common-data-service/plug-ins)
