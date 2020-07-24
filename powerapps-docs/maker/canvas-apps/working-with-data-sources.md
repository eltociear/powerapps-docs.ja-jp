---
title: キャンバス アプリのデータ ソースについて | Microsoft Docs
description: キャンバス アプリの接続とデータ ソースの操作に関する参照情報。
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/08/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 351e6cd6c680d4d5dc89f4e77c98bdd520f4c2ee
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/13/2020
ms.locfileid: "3308730"
---
# <a name="understand-data-sources-for-canvas-apps-in-power-apps"></a>Power Apps のキャンバス アプリに対するデータ ソースについて理解する

Power Apps では、ほとんどのキャンバス アプリで、**データ ソース**と呼ばれるクラウド サービスに格納されている外部情報を使用します。 一般的な例は、OneDrive for Business に格納されている Excel ファイル内のテーブルです。 アプリは**接続**を使用して、これらのデータ ソースにアクセスします。

この記事では、さまざまな種類のデータ ソースと、テーブル データ ソースの操作方法について説明します。

データ ソースに対する基本的な読み取りと書き込みを実行するアプリを作成するのは簡単です。 しかし、アプリのデータ フローの入出力をより細かく制御することが必要になる場合があります。  この記事では、**[Patch](functions/function-patch.md)**、**[DataSourceInfo](functions/function-datasourceinfo.md)**、**[Validate](functions/function-validate.md)**、および**[Errors](functions/function-errors.md)** 関数を使用してより細かな制御を提供する方法について説明します。

## <a name="kinds-of-data-sources"></a>データ ソースの種類

データ ソースは、クラウド サービスに接続すること、またはアプリに対してローカルに配置することもできます。

### <a name="connected-data-sources"></a>接続されたデータ ソース

最も一般的なデータ ソースは、情報の取得と保存に使用できる**テーブル**です。 データ ソースへの**接続**を使用して、Microsoft Excel ブック、SharePoint リスト、SQL テーブル、その他多くの形式でデータの読み書きを行うことができます。それらのデータは、OneDrive for Business、DropBox、SQL Server などのクラウド サービスに格納できます。

テーブル以外のデータ ソースには、電子メール、予定表、Twitter、通知が含まれますが、この記事ではこのような他の種類のデータ ソースについては説明しません。

### <a name="local-data-sources"></a>ローカル データ ソース

**[Gallery](controls/control-gallery.md)**、**[Display form](controls/control-form-detail.md)**、**[Edit form](controls/control-form-detail.md)** コントロールを使用すると、データ ソースからデータを読み取りおよび書き込むアプリを簡単に作成できます。  始めに、[データ フォームについて](working-with-forms.md) の記事をお読みください。  

データからアプリを作成するよう Power Apps に要求すると、これらのコントロールが使用されます。 バックグラウンドで、アプリは、データ ソースから取得したデータを格納して操作するために内部テーブルを使用します。

特別な種類のデータ ソースは[コレクション](working-with-data-sources.md#collections)です。それは、アプリに対してローカルであり、クラウドのサービスへの接続に基づきません。したがって、同じユーザーのデバイス間または複数のユーザー間で情報を共有することはできません。 コレクションはローカルで読み込まれ、保存されます。

### <a name="kinds-of-tables"></a>テーブルの種類

Power Apps アプリの内部テーブルは、数値または文字列が値であると同様に固定値です。 内部テーブルはどこにも格納されず、アプリのメモリにのみ存在します。 テーブルの構造とデータを直接変更することはできません。 代わりに、数式を使用して新しいテーブルを作成することができます: その数式を使用して、元のテーブルの変更されたコピーを作成します。

外部テーブルはデータ ソースに格納され、後で取得して共有することができます。  Power Apps は、格納されたデータを読み取りと書き込みのための「接続」を提供します。  接続内では、複数の情報テーブルにアクセスできます。  アプリで使用するテーブルを選択すると、それぞれのテーブルが別個の*データ ソース*になります。  

[テーブルの操作](working-with-tables.md) に関するページで内部テーブルについて詳しく説明されていますが、それはクラウド サービスに存在する外部テーブルにも当てはまります。

## <a name="working-with-tables"></a>テーブルの操作
テーブルのデータ ソースは、内部の Power Apps テーブルと同じ方法で使用できます。  内部テーブルと同じように、各データ ソースには、[レコード](working-with-tables.md#records)、[列](working-with-tables.md#columns)、および数式で使用できるプロパティがあります。 さらに:

* データ ソースは、接続の基になるテーブルと同じ列名とデータ型があります。
  
    > [!NOTE]
  > SharePoint および名前にスペースが使われている列を含む Excel のデータ ソースの場合、Power Apps はスペースを **"\_x0020\_"** に置き換えます。 たとえば、SharePoint の **"列名"** または Excel は、データレイアウトまたは数式で表示すると、Power Apps では **"Column_x0020_Name"** として表示されます。
* データ ソースは、アプリが読み込まれると、自動的にサービスから読み込まれます。  **[Refresh](functions/function-refresh.md)** 関数を使用して、強制的にデータを最新の情報に更新できます。
* ユーザーはアプリを実行するとき、レコードを作成、変更、削除して、その変更をサービスの基になるテーブルにプッシュ転送できます。
  * レコードは、**[Patch](functions/function-patch.md)** および**[Collect](functions/function-clear-collect-clearcollect.md)** 関数を使用して作成されます。  
  * レコードは、**[Patch](functions/function-patch.md)**、**[Update](functions/function-update-updateif.md)**、および**[UpdateIf](functions/function-update-updateif.md)** 関数を使用して変更されます。
  * レコードは、**[Remove](functions/function-remove-removeif.md)** および**[RemoveIf](functions/function-remove-removeif.md)** 関数を使用して削除されます。
  * データ ソースの操作に関するエラーは、**[Errors](functions/function-errors.md)** 関数を介して使用できます。
* **[DataSourceInfo](functions/function-datasourceinfo.md)**、**[Defaults](functions/function-defaults.md)**、および**[Validate](functions/function-validate.md)** 関数は、ユーザー エクスペリエンスを最適化するために使用できる、データ ソースに関する情報を提供します。

### <a name="creating-data-sources"></a>データ ソースの作成
Power Apps は、接続されたデータ ソースを作成したり、データ ソースの構造を変更したりするために使用することはできません; データ ソースは、既にいずれかのサービスに存在している必要があります。 たとえば、OneDrive に保存された Excel ブックにテーブルを作成するには、最初に OneDrive で Excel Online を使用してブックを作成します。 次に、アプリからそのブックへの接続を作成します。  

ただし、コレクションのデータ ソースは、アプリ内で作成と変更を*行えます*が、これは一時的なものです。

### <a name="display-one-or-more-records"></a>1 つまたは複数のレコードの表示
![](media/working-with-data-sources/reading-from-a-datasource.png) 上の図は、アプリがデータ ソース内の情報を読み取る場合の情報の流れを示しています:

* 情報は、ストレージ サービス (この場合は、Office 365 サイトの SharePoint リスト) を介して保存され、共有されます。
* 接続は、この情報をアプリで使用できるようになります。  接続は、情報にアクセスするためのユーザーの認証を処理します。
* アプリが起動されるか、**[Refresh](functions/function-refresh.md)** 関数が押されると、情報は接続からアプリのデータ ソースに取得され、ローカルで使用できるようになります。
* 数式は、情報を読み取り、その情報をユーザーが参照するコントロールに公開するために使用されます。 データ ソースのレコードを表示するには、画面のギャラリーを使用し、**[Items](controls/properties-core.md)** プロパティをデータ ソースに関連付けます: **Gallery.Items = DataSource**。  コントロールの**[Default](controls/properties-core.md)** プロパティを使用して、ギャラリー内のコントロールをギャラリーに関連付けます。  
* データ ソースは、テーブルでもあります。  したがって、データ ソースを全体として使用する前に、**[Filter](functions/function-filter-lookup.md)**、**[Sort](functions/function-sort.md)**、**[AddColumns](functions/function-table-shaping.md)**、およびその他の関数を使用して、改良と拡張を行えます。  また、**[Lookup](functions/function-filter-lookup.md)**、**[First](functions/function-first-last.md)**、**[Last](functions/function-first-last.md)**、およびその他の関数を使用して、個々のレコードを操作することもできます。

### <a name="modify-a-record"></a>レコードの変更
前のセクションでは、データ ソースを読み取る方法について説明しました。  ここで、上の図に示されている矢印が一方向であることに注意してください。  データ ソースへの変更は、データを取得したのと同じ数式を介してプッシュ転送されません。  代わりに、新しい数式が使用されます。  多くの場合、特にモバイル デバイス上で、レコードの編集用には、レコードを閲覧用とは異なる画面が使用されます。

データ ソースの既存のレコードを変更するには、そのレコードがデータ ソースから取得されている必要があることに注意してください。  レコードは、ギャラリー、[コンテキスト変数](working-with-variables.md#use-a-context-variable)、任意の数式の数値を介している可能性がありますが、その取得元はデータ ソースまでさかのぼることができる必要があります。  レコードを一意に識別する追加情報がレコードに付属することで正しいレコードを変更することが保証されるため、これは重要なことです。    

![](media/working-with-data-sources/writing-to-a-datasource.png) 上の図は、データ ソースを更新するための情報の流れを示しています:

* **[Edit form](controls/control-form-detail.md)** コントロールは、入力カードのコンテナーを提供します。入力カードは、テキスト入力コントロールまたはスライダーなどのユーザー入力コントロールで構成されます。  **[DataSource](controls/control-form-detail.md)** および**[Item](controls/control-form-detail.md)** プロパティは、編集するレコードを識別するために使用されます。
* 各入力カードには**[Default](controls/properties-core.md)** プロパティがあります。このプロパティは、通常はフォームの **ThisItem** レコードのフィールドに設定されます。  入力カード内のコントロールは、**[Default](controls/properties-core.md)** から入力値を受け取ります。  通常はこれを変更する必要はありません。
* 各入力カードは、**[Update](controls/control-card.md)** プロパティを公開します。  このプロパティは、ユーザーの入力を、データ ソースに書き戻すために、レコードの特定のフィールドにマップします。  通常はこれを変更する必要はありません。
* 画面上のボタンまたはイメージ コントロールをは、ユーザーがレコードへの変更を保存できます。  そのためには、コントロールの**[OnSelect](controls/properties-core.md)** 数式で**[SubmitForm](functions/function-form.md)** 関数を呼び出します。  **[SubmitForm](functions/function-form.md)** は、カードのすべての **[Update](controls/control-card.md)** プロパティを読み取り、これを使用してデータ ソースに書き戻します。
* 場合によっては問題が発生することがあります。  ネットワーク接続が切断されている場合や、アプリが認識できないサービスによって検証チェックが行われている場合があります。  フォーム コントロールの **Error** および**[ErrorKind](controls/control-form-detail.md)** プロパティは、この情報を使用可能するので、ユーザーに表示できるます。  

プロセスをより細かく制御するために、**[Patch](functions/function-patch.md)** および**[Errors](functions/function-errors.md)** 関数を使用することもできます。  **[Edit form](controls/control-form-detail.md)** コントロールでは**[Update](controls/control-form-detail.md)** プロパティが公開されるため、フォーム内のフィールドの値を読み取ることができます。  このプロパティを使用して、**Patch** および **SubmitForm** 関数を完全にバイパスし、接続上でカスタム コネクタを呼び出すこともできます。

### <a name="validation"></a>検証
レコードに変更を加える前に、アプリはできる限りのことを行い、変更が受け入れられることを確認する必要があります。  これには 2 つの理由があります:

* *ユーザーへの即時のフィードバック*。  問題を修正するのに最適な時は、その問題が発生し、ユーザーの記憶に新鮮なときです。  実際、タッチ操作またはキー入力ごとに、入力の問題を示す赤いテキストを表示できます。
* *ネットワーク トラフィックの削減とユーザーの待ち時間の短縮*。  アプリで問題を多く検出することは、問題を検出して解決するためのネットワーク経由の会話を減らすという意味です。  各会話は、ユーザーが進む前に待つ必要のある間、時間がかかります。

Power Apps は、検証用に 2 つのツールが用意されます:

* データ ソースは、有効なものとそうではないものに関する情報を提供できます。  たとえば、数値に最小値と最大値があり、1 つ以上のエントリを必須にできます。  この情報には、**[DataSourceInfo](functions/function-datasourceinfo.md)** 関数を使用してアクセスできます。  
* **[Validate](functions/function-validate.md)** 関数は、単一の列またはレコード全体の値を確認するため、この同じ情報を使用します。

### <a name="error-handling"></a>エラー処理
これで、レコードを検証することができました。  次に、**[Patch](functions/function-patch.md)** を使用してそのレコードを更新します!

しかし、残念ながら、まだ問題があります。  アプリは、ネットワークがダウンしている、サービスでの検証に失敗した、ユーザーが適切なアクセス許可を持っていない、などのエラーが発生する可能性があります。  エラー状況に適切に対応して、ユーザーにフィードバックおよびエラーを修正する手段を提供する必要があります。  

データ ソースでエラーが発生すると、アプリは自動的にエラー情報を記録し、それを**[Errors](functions/function-errors.md)** 関数を介して使用できるようにします。  エラーは、問題が発生したレコードに関連付けられます。  検証の問題など、ユーザーによって修正可能な問題の場合、レコードを再送信して、エラーが解決されます。

**[Patch](functions/function-patch.md)** または**[Collect](functions/function-clear-collect-clearcollect.md)** を使用してレコードが作成されたときにエラーが発生した場合、エラーが関連付けられるレコードはありません。  その場合、**[Patch](functions/function-patch.md)** によって*空白*が返され、これを**[Errors](functions/function-errors.md)** へのレコード引数として使用できます。  作成エラーは次の操作で解決されます。

**[Errors](functions/function-errors.md)** 関数は、エラー情報のテーブルを返します。  エラーが特定の列に原因があると考えられる場合は、この情報は列情報を含めることができます。  編集画面上の列の近くにあるラベル コントロールで、列レベルのエラー メッセージを使用します。  エラー テーブルの**列**が*空白*であるレコード レベルのエラー メッセージは、レコード全体の**保存**ボタンの近くの場所で使用します。  

### <a name="working-with-large-data-sources"></a>大規模なデータ ソースの操作
(数百万件のレコードが含まれる) 大規模なデータ ソースからレポートを作成する場合は、ネットワーク トラフィックを最小限にします。 ニューヨーク市の、StatusCode が「Platinum」であるすべての顧客を報告するとします。 この顧客テーブルには、数百万件のレコードが含まれています。

数百万人の顧客レコードをアプリに取り込んだ後で目的のレコードを選択することは**しません**。 テーブルが格納されているクラウド サービス内でその選択が行われるようにし、選択されたレコードのみをネットワーク経由で送信します。

すべてではありませんが、レコードを選択するために使用できる関数の多くは*委任*することができます。つまり、それらはクラウド サービス内で実行されます。 その方法については、[委任](delegation-overview.md)に関するページを参照してください。

## <a name="collections"></a>コレクション
コレクションは、特別な種類のデータ ソースです。  コレクションは、アプリに対してローカルであり、クラウドのサービスへの接続に基づきません。したがって、同じユーザーのデバイス間または複数のユーザー間で情報を共有することはできません。  コレクションは他のデータ ソースと同様に機能しますが、いくつかの例外を除きます:

* コレクションは、**[Collect](functions/function-clear-collect-clearcollect.md)** 関数を使用して動的に作成できます。  コレクションは、接続ベースのデータ ソースのように、事前に確立する必要はありません。
* コレクションの列は、**[Collect](functions/function-clear-collect-clearcollect.md)** 関数を使用していつでも変更できます。
* コレクションは、重複するレコードを許可します。  コレクションでは、同じレコードのコピーが複数存在できます。  **All** 引数が指定されていない限り、**[Remove](functions/function-remove-removeif.md)** などの関数は見つけた最初の一致で動作します。
* **[SaveData](functions/function-savedata-loaddata.md)** および**[LoadData](functions/function-savedata-loaddata.md)** 関数を使用して、コレクションのコピーの保存と再読み込みを行うことができます。  情報は、他のユーザー、アプリ、またはデバイスがアクセスできないプライベートな場所に保存されます。
* **[Export](controls/control-export-import.md)** および**[Import](controls/control-export-import.md)** コントロールを使用して、ユーザーが操作できるファイルとの間でコレクションのコピーの保存と再読み込みを行うことができます。  

データ ソースとしてのコレクションの操作方法の詳細については、[コレクションの作成と更新](create-update-collection.md) を参照してください。

コレクションは通常、アプリのグローバルな状態を保持するために使用しされます。  状態を管理するために使用できるオプションについては、[変数の操作](working-with-variables.md) を参照してください。

