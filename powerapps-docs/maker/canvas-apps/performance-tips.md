---
title: キャンバス アプリのパフォーマンスを最適化 | Microsoft Docs
description: このトピックのベスト プラクティスに従い、Power Apps で作成するキャンバス アプリのパフォーマンスを向上させます。
author: yingchin
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/17/2019
ms.author: yingchin
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9b2e3298f09857e26df4c3707d8ae36737557b08
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3307212"
---
# <a name="optimize-canvas-app-performance-in-power-apps"></a>Power Apps でキャンバス アプリのパフォーマンスを最適化
Microsoft は Power Apps プラットフォームで実行されるすべてのアプリのパフォーマンスを改善するために懸命に取り組んでいます。 このトピックのベスト プラクティスに従って、作成するアプリのパフォーマンスを改善できます。

ユーザーがアプリを開くと、これらのフェーズを実行してからユーザー インターフェイスが表示されます。 
1. **ユーザーの認証** - ユーザーが以前にアプリを開いたことがない場合、アプリに必要な接続の資格情報でサインインするようにユーザーに求めます。 同じユーザーが再びアプリを開く場合、組織のセキュリティ ポリシーによっては、資格情報の入力が再度求められることがあります。 
2. **メタデータの取得** - アプリが実行される Power Apps プラットフォームのバージョンやデータを取得する必要があるソースなどのメタデータを取得します。 
3. **アプリの初期化** - **OnStart** プロパティに指定されたタスクを実行します。 
4. **画面の表示** - アプリによってデータが入力されたコントロールで最初の画面を表示します。 ユーザーが他の画面を開くと、アプリは同じプロセスを使用してその画面を表示します。  

## <a name="limit-data-connections"></a>データ接続の制限 
**同じアプリから 30 を超えるデータ ソースに接続しないでください**。 アプリは新しいユーザーに各コネクタへのサインインを促すため、コネクタを追加するたびに、アプリの起動に必要な時間が増えます。 アプリの実行中、アプリがソースからのデータを要求する場合、各コネクタで CPU リソース、メモリ、ネットワーク帯域幅が必要になります。 

アプリの実行中、[Microsoft Edge](https://docs.microsoft.com/microsoft-edge/devtools-guide/network) または [Google Chrome](https://developers.google.com/web/tools/chrome-devtools/network-performance/) で開発者ツールをオンにすることで、アプリのパフォーマンスを簡単に測定できます。 Common Data Service、Azure SQL、SharePoint、Excel on OneDrive など、30 を超えるデータ ソースから頻繁にデータを要求する場合、アプリがデータを返すために 15 秒以上かかることがあります。  

## <a name="limit-the-number-of-controls"></a>コントロール数の制限 
**同じアプリに 500 を超えるコントロールを追加しないでください**。 Power Apps は、各コントロールを表示するための HTML DOM を生成します。 コントロールを追加すると、Power Apps に必要な生成時間が増えます。 

個別コントロールではなく、ギャラリーを使用することで、場合によっては同じ結果を得たり、アプリを速く起動したりできることもあります。 また、同じ画面でコントロールの種類の数を減らすことができます。 一部のコントロール (PDF ビューアー、データ テーブル、コンボ ボックスなど) は大きな実行スクリプトを取り込み、表示に時間がかかります。 

## <a name="optimize-the-onstart-function"></a>OnStart 関数の最適化
ユーザー セッション中に変わらない場合、[**ClearCollect**](functions/function-clear-collect-clearcollect.md) 関数を使用し、データをローカルでキャッシュします。 また、データ ソースを同時に読み込むには、[**Concurrent**](functions/function-concurrent.md) 関数を使用します。

[この参照トピック](functions/function-concurrent.md) で示しているように、**Concurrent** を利用して、データを読み込むためにアプリが必要な時間を半分に減らすことができます。

**Concurrent** 関数がない場合、この数式は 4 つのテーブルを一度に 1 つずつ読み込みます。

```
ClearCollect( Product, '[SalesLT].[Product]' );
ClearCollect( Customer, '[SalesLT].[Customer]' );
ClearCollect( SalesOrderDetail, '[SalesLT].[SalesOrderDetail]' );
ClearCollect( SalesOrderHeader, '[SalesLT].[SalesOrderHeader]' )
```

ブラウザーの開発者ツールでこの動作を確認できます。

![シリアル ClearCollect](./media/performance-tips/perfconcurrent1.png)
    
**Concurrent** 関数で同じ数式を囲むと、操作に必要な全体の時間を減らすことができます。

```
Concurrent( 
    ClearCollect( Product, '[SalesLT].[Product]' ),
    ClearCollect( Customer, '[SalesLT].[Customer]' ),
    ClearCollect( SalesOrderDetail, '[SalesLT].[SalesOrderDetail]' ),
    ClearCollect( SalesOrderHeader, '[SalesLT].[SalesOrderHeader]' ))
```

この変更により、アプリはテーブルを並行して取得します。 

![パラレル ClearCollect](./media/performance-tips/perfconcurrent2.png)  

## <a name="cache-lookup-data"></a>検索データのキャッシュ
**Set** 関数を使用して検索テーブルからのデータをローカルでキャッシュし、ソースからデータを繰り返し取得するのを回避します。 この方法により、セッション中にデータが変更されなければ、パフォーマンスが最適化されます。 この例では、データはソースから 1 回のみ取得され、ユーザーがアプリを閉じるまで、ローカルで参照されます。 

```
Set(CustomerOrder, Lookup(Order, id = “123-45-6789”));
Set(CustomerName, CustomerOrder.Name);
Set(CustomerAddress, CustomerOrder.Address);
Set(CustomerEmail, CustomerOrder.Email);
Set(CustomerPhone, CustomerOrder.Phone);
```

連絡先情報は頻繁に変更されません。既定値やユーザー情報も同じです。 そのため、この方法は一般的に **Defaults** 関数や **User** 関数でも使用できます。 

## <a name="avoid-controls-dependency-between-screens"></a>画面間のコントロール依存回避
パフォーマンスを向上させるため、アプリ画面は必要なときにのみメモリに読み込まれます。 この最適化は、たとえば画面 1 が読み込まれ、その数式の 1 つが画面 2 のコントロールのプロパティを使用している場合に妨げられる可能性があります。 次に、画面 1 を表示する前に、画面 2 を読み込んで依存関係を満たす必要があります。 画面 2 が画面 4 など別の依存関係がある画面 3 に依存しているとします。 この依存関係チェーンにより、多くの画面が読み込まれる可能性があります。

このため、画面間の数式の依存関係は避けてください。 場合によっては、グローバル変数またはコレクションを使用して、画面間で情報を共有できます。

例外があります。 前述の例で、画面 1 を表示する唯一の方法は画面 2 から移動させることでした。 その後、画面 1 が読み込まれるときに、画面 2 はすでにメモリに読み込まれています。 画面 2 の依存関係を満たすために追加の作業は必要ないため、パフォーマンスへの影響はありません。

## <a name="use-delegation"></a>委任の使用
ローカル デバイスの処理のためにデータを取得する代わりに、可能な場合、データ処理をデータ ソースに委任する関数を使用します。 アプリでデータをローカル処理する必要がある場合、特にデータ セットが大きい場合にはその操作にはたくさんの処理能力、メモリ、ネットワーク帯域幅が必要になります。

[この一覧](delegation-list.md) でご覧いただけるように、さまざまなデータ ソースはさまざまな関数からの委任に対応しています。

![委任の使用](./media/performance-tips/perfdelegation1.png)

たとえば、SharePoint リストの場合、[**Filter**](functions/function-filter-lookup.md) 関数からの委任には対応していますが、[**Search**](functions/function-filter-lookup.md) 関数からの委任は対応していません。 そのため、SharePoint リストに含まれる項目が 500 を超える場合、ギャラリーの項目を検索するには、**Search** の代わりに **Filter** を使用する必要があります。 詳細については、[Power Apps で大規模な SharePoint リストを扱う](https://powerapps.microsoft.com/blog/powerapps-now-supports-working-with-more-than-256-items-in-sharepoint-lists/) (ブログの投稿) を参照してください。 

## <a name="use-delayed-load"></a>遅延読み込みの使用
アプリに 10 個以上の画面があり、ルールがなく、多くのコントロールが複数の画面上にあってデータ ソースに直接バインドされている場合、遅延読み込みの[テスト機能](working-with-experimental.md) を有効にしてください。 この種類のアプリを作成して、この機能を有効にしない場合、開いていない画面も含め、すべての画面のコントロールを事前設定する必要があるため、アプリのパフォーマンスが低下することがあります。 また、ユーザーがレコードを追加するときなどデータ ソースが変わる場合は、必ずアプリのすべての画面を更新する必要があります。

## <a name="working-with-large-data-sets"></a>大規模なデータ セットの操作
委任できるデータ ソースと数式を使用してアプリのパフォーマンスを維持することによって、ユーザーが必要とするあらゆる情報にアクセスできるようにして、委任できないクエリのために、データ行の制限である 2000 に到達しないようにします。 ユーザーがデータを検索、フィルター処理、並べ替えできるデータレコード列については、[SQL Server](https://docs.microsoft.com/sql/relational-databases/sql-server-index-design-guide?view=sql-server-2017) と [SharePoint](https://support.office.com/article/Add-an-index-to-a-SharePoint-column-f3f00554-b7dc-44d1-a2ed-d477eac463b0) に関するドキュメントで説明されているように、列のインデックスが適切に設計されています。  

## <a name="republish-apps-regularly"></a>アプリの定期再発行
[アプリを再発行](https://powerapps.microsoft.com/blog/republish-your-apps-to-get-performance-improvements-and-additional-features/) (ブログ記事) して、Power Apps プラットフォームからパフォーマンス改善と追加機能を取得します。

## <a name="avoid-repeating-the-same-formula-in-multiple-places"></a>同じ数式を複数の場所で繰り返さないでください
複数のプロパティが同じ数式を実行する場合 (特に複雑な場合)、一度設定してから、後続のプロパティで最初のプロパティの出力を参照することを検討してください。 たとえば、コントロール A、B、C、D、E の **DisplayMode** プロパティを同じ複雑な数式に設定しないでください。 代わりに、A の **DisplayMode** プロパティを複雑な式に設定し、B の **DisplayMode** プロパティを A の **DisplayMode** プロパティの結果に設定します。C、D、E についても同様に設定します。

## <a name="enable-delayoutput-on-all-text-input-controls"></a>すべてのテキスト入力コントロールで DelayOutput の有効化
**Text input** コントロールの値を参照する複数の数式またはルールがある場合、そのコントロールの **DelayedOutput** プロパティを true に設定します。 そのコントロールの **Text** プロパティは、短い時間に連続して入力したキーボード操作が停止した後にのみ更新されます。 数式またはルールは何度も実行されず、アプリのパフォーマンスが改善します。

## <a name="avoid-using-formupdates-in-rules-and-formulas"></a>ルールと数式で Form.Updates を使用しないでください
**Form.Updates** 変数を使用してルールまたは数式でユーザー入力値を参照する場合、レコードを作成するたびに、すべてのフォームのデータ カードを繰り返します。 アプリをより効率的にするには、データ カードまたはコントロール値から直接値を参照します。

## <a name="next-steps"></a>次の手順
アプリのパフォーマンスを最大化し、アプリ管理を維持しやすくするために、[コーディング標準](https://aka.ms/powerappscanvasguidelines) を確認します。
