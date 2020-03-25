---
title: " イベント フレームワーク (Common Data Service) | Microsoft Docs"
description: イベント フレームワークと、開発者がそれを扱う際に知っておくべき情報について説明します。
ms.custom: ''
ms.date: 06/18/2019
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
ms.openlocfilehash: 4c055dbac811186dde54cc4a002ee721e3ca25cf
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2020
ms.locfileid: "3109037"
---
# <a name="event-framework"></a>イベント フレームワーク

Common Data Service の既定の動作を拡張する機能は、サーバーでのイベント発生時の検出内容によって異なります。 *イベント フレームワーク*は、特定のイベントに応答して実行されるカスタム コードを登録する機能を提供します。 

プラットフォームの既定の動作を拡張するすべての機能は、イベント フレームワークによって異なります。 コードを記述することなくワークフロー デザイナを使用してイベントに応答するワークフローを構成する場合、そのイベントはイベント フレームワークによって提供されます。 

開発者は、プラグイン、Azure 統合、仮想エンティティ データ プロバイダー、および Webhook を構成して、イベント フレームワークによって提供されるイベントに応答する*プラグイン登録ツール*を使用します。 イベントが発生し、それらに応答するために拡張機能が登録されると、その操作に関連するデータに関するコンテキスト情報が拡張機能に渡されます。 イベントへの登録がどのように構成されているかに応じて、拡張機能は渡されたデータを修正したり、すぐに適用される自動プロセスを導入したり、後で実行されるキューにアクションを追加することを定義できます。

カスタム拡張機能のイベント フレームワークを活用するには、以下を理解する必要があります。

 - 指定できるイベント
 - イベントの処理方法
 - イベントが発生したときに拡張機能が利用できるデータの種類
 - 時間とリソースの制約が適用される場合
 - パフォーマンスを監視する方法

## <a name="available-events"></a>使用可能なイベント

[メッセージを組織サービスと共に使用する](org-service/use-messages.md) で説明したように、 Common Data Service プラットフォームのデータ操作はメッセージに基づいており、すべてのメッセージに名前が付けられています。 エンティティで発生する基本的なデータ操作をカバーする `Create`、`Retrieve`、`RetrieveMultiple`、`Update`、`Delete`、`Associate`、`Disassociate` メッセージがあります。 さらに複雑な操作に特化したメッセージもあります。 ユーザー定義アクションは新しいメッセージを追加します。

プラグイン登録ツールを使用して拡張機能を特定のメッセージに関連付けると、*ステップ*として登録されます。 以下のスクリーンショットは、プラグインの登録時に使用される**新しいステップの登録**ダイアログです。

![ステップを登録するためのダイアログ](media/register-new-step-plug-in.png)

ステップは、拡張機能がどのメッセージに応答すべきか、および他の構成の選択に関する情報を提供します。 拡張機能が応答するメッセージを選択するには、**メッセージ** フィールドを使用します。

一般に、<xref:Microsoft.Crm.Sdk.Messages> または <xref:Microsoft.Xrm.Sdk.Messages> の名前空間にあるほとんどの **Request* クラスのメッセージを見つけることができますが、組織内で作成されたユーザー定義アクションのメッセージも表示されます。 エンティティ メタデータを含む操作は使用できません。

メッセージに関するデータは、[SDK メッセージ](reference/entities/sdkmessage.md) エンティティと [SDK メッセージ](reference/entities/sdkmessagefilter.md) エンティティに格納されます。 Plugin Registration Tool はこの情報をフィルタリングして有効なメッセージのみを表示します。

データベース クエリを使用してプラグインの実行をサポートしているかどうかを確認するには、次のWeb API クエリを使用できます:

```
{{webapiurl}}sdkmessages?$select=name
&$filter=isprivate eq false 
and (name ne 'SetStateDynamicEntity' 
and name ne 'RemoveRelated' 
and name ne 'SetRelated' and 
name ne 'Execute') 
and sdkmessageid_sdkmessagefilter/any(s:s/iscustomprocessingstepallowed eq true 
and s/isvisible eq true)
&$expand=sdkmessageid_sdkmessagefilter($select=primaryobjecttypecode;
$filter=iscustomprocessingstepallowed eq true and isvisible eq true)
&$orderby=name
```

> [!TIP]
> クエリとブログ投稿で提供されている手順を使用して、Excelワークシートにデータをエクスポートできます: [Common Data Service を使用してプラグインに適したメッセージとエンティティを検索します。](https://powerapps.microsoft.com/blog/find-messages-and-entities-eligible-for-plug-ins-using-the-common-data-service/)


この情報を以下のFetchXMLを使って取得することもできます。 [FetchXML Builder](https://fxb.xrmtoolbox.com) は、この種類のクエリを実行するのに役立つツールです。

```xml
<fetch>
  <entity name='sdkmessage' >
    <attribute name='name' />
    <link-entity name='sdkmessagefilter' alias='filter' to='sdkmessageid' from='sdkmessageid' link-type='inner' >
      <filter type='and' >
        <condition attribute='iscustomprocessingstepallowed' operator='eq' value='1' />
        <condition attribute='isvisible' operator='eq' value='1' />
      </filter>
      <attribute name='primaryobjecttypecode' />
    </link-entity>
    <filter>
      <condition attribute='isprivate' operator='eq' value='0' />
      <condition attribute='name' operator='not-in' >
        <value>SetStateDynamicEntity</value>
        <value>RemoveRelated</value>
        <value>SetRelated</value>
          <value>Execute</value>
      </condition>
    </filter>
    <order attribute='name' />
  </entity>
</fetch>
```

> [!CAUTION]
> `Execute` メッセージは利用可能ですが、すべての操作で呼び出されるため、拡張子を登録しないでください。

> [!NOTE]
> 更新イベント用に登録されたプラグインとワーク フローを 2 回呼び出すことができるケースがあります。 詳細: [特化された更新操作の動作](special-update-operation-behavior.md)

## <a name="event-execution-pipeline"></a>イベント実行パイプライン

Plugin Registration Tool を使用してステップを登録するときは、**実行のイベント パイプライン ステージ**も選択する必要があります。  各メッセージは、次の表に示すように一連の 4 つのステージで処理されます。

|Name|説明|
|--|--|
|**事前検証**|[!INCLUDE [cc-prevalidation-description](../../includes/cc-prevalidation-description.md)]|
|**事前操作**|[!INCLUDE [cc-preoperation-description](../../includes/cc-preoperation-description.md)]|
|**MainOperation**|内部のみで使用|
|**PostOperation**|[!INCLUDE [cc-postoperation-description](../../includes/cc-postoperation-description.md)]|

選択する必要があるステージは、拡張機能の目的によって異なります。 すべてのビジネス ロジックを単一の手順に適用する必要はありません。 複数のステップを適用することで、**事前検証**ステージで操作を進めるかどうかのロジックを確認でき、**PostOperation** ステージでロジックをメッセージ プロパティに変更できるようにすることができます。

> [!IMPORTANT]
> 任意のステージでコードによってスローされた例外により、トランザクション全体がロールバックされます。 考えられる例外がコードによって処理されるように注意する必要があります。 操作を取り消したい場合は、**事前検証**ステージでこれを検出し、操作がキャンセルされた理由を説明する適切なメッセージを含む <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> をスローしてください。

同じメッセージとステージに対して複数の拡張機能を登録することができます。 ステップ登録の中で、**実行順序**値は、複数の拡張機能が所定のステージに対して処理されるべき順序を決定します。

登録されたステップに関する情報は、[SdkMessageProcessingStep エンティティ](reference/entities/sdkmessageprocessingstep.md) に格納されます。

## <a name="event-context"></a>イベント コンテキスト

拡張機能がプラグインである場合、<xref:Microsoft.Xrm.Sdk.IPluginExecutionContext> インターフェイスを実装するパラメーターを受け取ります。 このクラスは、プラグインが登録されている <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext.Stage> に関する情報と、現在の操作をトリガーさせた別のプラグイン内の操作に関する情報を提供する <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext.ParentContext> に関する情報を提供します。

拡張機能が Webhook または Azure Service Bus エンドポイントの場合、登録されたエンドポイントに投稿されるデータは、<xref:Microsoft.Xrm.Sdk.IPluginExecutionContext> と <xref:Microsoft.Xrm.Sdk.IExecutionContext> の両方を実装する <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext> の形式になります

実行コンテキストに関する詳細については、[実行コンテキストを理解する](understand-the-data-context.md) を参照してください。