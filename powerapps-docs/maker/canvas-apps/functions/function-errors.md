---
title: Errors 関数 | Microsoft Docs
description: Power Apps での Errors 関数の構文と例を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/11/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 245bdbfbcf8e95b5bca6ca736ff67d5623f772f5
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3305280"
---
# <a name="errors-function-in-power-apps"></a>Power Apps での Errors 関数
[データ ソース](../working-with-data-sources.md) への前の変更のエラー情報を提供します。

## <a name="overview"></a>概要
エラーは、データ ソースの[レコード](../working-with-tables.md#records) が変更された場合に発生することがあります。  ネットワークの停止、不適切なアクセス許可、および編集の競合を含む、多くの原因が考えられます。  

**[Patch](function-patch.md)** 関数および他のデータ関数は、直接エラーを返しません。 代わりに、操作の結果が返されます。 データ関数の実行後、**Errors** 関数を使用して、エラーの詳細を取得することができます。  **IsEmpty( Errors ( ... ) )** の数式で **[IsEmpty]** 関数を使用して、エラーの存在を確認することができます。

**[Validate](function-validate.md)** および **[DataSourceInfo](function-datasourceinfo.md)** 関数を使用して、いくつかのエラーを発生前に回避することができます。  エラーの処理および回避方法についての推奨事項については、[データ ソースの操作](../working-with-data-sources.md) を参照してください。

## <a name="description"></a>内容
**Errors** 関数は、次の[列](../working-with-tables.md#columns) を含むエラーの[テーブル](../working-with-tables.md) を返します。

* **レコード**。  エラーが発生したデータ ソース内のレコード。  レコードの作成中にエラーが発生した場合、この列は*空白*になります。
* **列**。  エラーが 1 つの列に原因があると考えられる場合に、エラーの原因となった列。 そうでない場合は、*空白*になります。
* **メッセージ**。  エラーの説明。  このエラー文字列は、エンド ユーザーに対して表示できます。  このメッセージはデータ ソースによって生成される場合があり、長くなったり、ユーザーには意味を持たない生の列名を含んでいる可能性があることに注意してください。
* **エラー** :   エラーを解決するために数式で使用できるエラー コード。

| ErrorKind | 内容 |
| --- | --- |
| ErrorKind.Conflict |同じレコードに対して別の変更が行われ、変更の競合という結果になりました。  **[Refresh](function-refresh.md)** 関数を使用して、レコードを再読み込みし、変更を再度試します。 |
| ErrorKind.ConstraintViolation |1 つ以上の制約に違反しています。 |
| ErrorKind.CreatePermission |レコードを作成しようとしましたが、現在のユーザーにはレコードを作成するためのアクセス許可がありません。 |
| ErrorKind.DeletePermission |レコードを削除しようとしましたが、現在のユーザーにはレコードを削除するためのアクセス許可がありません。 |
| ErrorKind.EditPermission |レコードを編集しようとしましたが、現在のユーザーにはレコードを編集するためのアクセス許可がありません。 |
| ErrorKind.GeneratedValue |データ ソースが自動的に生成する列を変更しようとしました。 |
| ErrorKind.MissingRequired |必要な列の値がレコードにありません。 |
| ErrorKind.None |エラーはありません。 |
| ErrorKind.NotFound |レコードを編集または削除しようとしましたが、レコードが見つかりませんでした。  別のユーザーがレコードを変更した可能性があります。 |
| ErrorKind.ReadOnlyValue |読み取り専用の列を変更しようとしました。 |
| ErrorKind.Sync |データ ソースによってエラーが報告されました。  詳細については、メッセージの列を確認してください。 |
| ErrorKind.Unknown |エラーが発生しましたが、種類が不明です。 |
| ErrorKind.Validation |他の種類の 1 つに適合しない、一般的な検証のイシューが検知されました。 |

関数に*レコード*引数を提供すると、データ ソース全体または選択された行のみにエラーが返されます。  

**[Patch](function-patch.md)** または他のデータ関数は、たとえば、レコードを作成できなかった場合は、*空白*値を返すことがあります。 **Errors** に*空白*を渡すと、そのような場合は適切なエラー情報が返されます。  同じデータ ソースのそれ以降のデータ関数の使用は、このエラー情報を消去します。

エラーがない場合、**Errors** が返すテーブルは[空](function-isblank-isempty.md) になり、**[IsEmpty](function-isblank-isempty.md)** 関数でテストすることができます。

## <a name="syntax"></a>構文
**Errors**( *DataSource* [, *Record* ] )

* *DataSource* – 必須。 エラーを返すデータ ソース。
* *Record* – オプション。  エラーを返す特定のレコード。 この引数を指定しない場合、関数はデータ ソース全体のエラーを返します。

## <a name="examples"></a>例
### <a name="step-by-step"></a>手順
この例では、**IceCream** データ ソースを使用して操作します。

![](media/function-errors/icecream.png)

アプリを使用して、ユーザーはチョコレートのレコードをデータ入力フォームに読み込み、次に**数量**の値を 90 に変更します。  操作するレコードは、[コンテキスト変数](../working-with-variables.md#use-a-context-variable) **EditRecord** に配置されています。

* **UpdateContext( { EditRecord: First( Filter( IceCream, Flavor = "Chocolate" ) ) } )**

データ ソースでこの変更を行うには、**[Patch](function-patch.md)** 関数を使用します。

* **Patch( IceCream, EditRecord, Gallery.Updates )**

ここで、**Quantity** 関数のみが変更されたため、**Gallery.Updates** は **{ Quantity: 90 }** と評価されます。

残念ながら、**[Patch](function-patch.md)** 関数が呼び出された直前に、他のユーザーがチョコレートの**数量**を 80 に変更しました。  Power Apps はこれを検出し、競合する変更の発生を許可しません。  次の数式でこの状況を確認できます。

* **IsEmpty( Errors( IceCream, EditRecord ) )**

**Errors** 関数が次のテーブルを返したため、**false** が返されます。

| レコード | 列 | メッセージ | エラー |
| --- | --- | --- | --- |
| { Flavor: "Chocolate", Quantity: 100 } |*空白* |"別のユーザーが、変更しようとしているレコードを変更しました。 レコードを再読み込みしてから再度やり直してください。" |ErrorKind.Conflict |

このエラーをユーザーに表示するため、フォームにラベルを置くことができます。

* エラーを表示するには、ラベルの **[Text](../controls/properties-core.md)** プロパティを次の数式に設定します。<br>
  **Label.Text = First(Errors( IceCream, EditRecord )).Message**

フォームに**リロード** ボタンを追加すると、ユーザーが効率的に競合を解決できるようにすることもできます。

* 競合が発生した場合にのみボタンを表示するには、ボタンの **[Visible](../controls/properties-core.md)** プロパティを次の数式に設定します。<br>
    **!IsEmpty( Lookup( Errors( IceCream, EditRecord ), Error = ErrorKind.Conflict ) )**
* ユーザーがボタンを選択して変更を元に戻すには、その **[OnSelect](../controls/properties-core.md)** プロパティを次の数式に設定します。<br>
    **ReloadButton.OnSelect = Revert( IceCream, EditRecord )**

