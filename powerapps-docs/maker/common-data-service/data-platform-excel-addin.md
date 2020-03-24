---
title: エンティティ データを Excel で開く | Microsoft Docs
description: 対話型の表示および編集用に Excel でエンティティ データを開きます。
author: lancedMicrosoft
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 05/21/2018
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 7cf24511fd8f314fde5f653608c1a4fa43ebc4e4
ms.sourcegitcommit: 2b34de88c977c149e4c632b23d8e816901c15949
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2020
ms.locfileid: "3040660"
---
# <a name="open-entity-data-in-excel"></a>エンティティ データを Excel で開く
Microsoft Excel でエンティティ データを開くことで、 Microsoft Power Apps Excel アドインを使用してすばやく簡単にデータを表示、編集することができます。 Power Apps Excel アドインには Microsoft Excel 2016 が必要になります。

![Excel アドイン](./media/data-platform-cds-excel-addin/ExcelAddin.png "Power Apps Excel アドイン")

Power Apps Excel のアドインをインストールするには、[Microsoft PowerApps Office のアドイン](https://appsource.microsoft.com/en-us/product/office/WA104380330?tab=Overview)を参照してください。 Office Excel アドインを追加、削除する方法の詳細については、[Excel でアドインを追加、削除する](https://support.office.com/en-us/article/add-or-remove-add-ins-in-excel-0af570c4-5cf3-4fa9-9b88-403625a0b460)を参照してください。

## <a name="open-entity-data-in-excel"></a>エンティティ データを Excel で開く
1. [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) で**データ**セクションを展開し、左側のナビゲーション ウィンドウで**エンティティ**をクリックまたはタップします。 すべてのエンティティが表示されます。
2. 関心のあるエンティティの右側にある省略記号 (...) をクリックします。
3. **Excel で開く**をクリックし、生成されるワークブックを開きます。 このワークブックには、エンティティのバインド情報、環境へのポインタおよび Power Apps Excel アドイン へのポインタが含まれています。  
4. Excel で、 **編集を有効にする** をクリックして Power Apps Excel アドインの実行を有効にします。 Excel ウィンドウの右側にあるウィンドウで Excel アドインを実行します。
5. Power Apps Excel アドインを初めて実行する場合は、 **このアドインを信頼する** をクリックしてExcelアドインを実行できるようにします。
6. サインインするように要求された場合、**サインイン**をクリックし、[powerapps.com](https:///?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) で使用した同じ資格情報を使用してサインインします。 Excel アドインでは、前のサインインのコンテキストを使用し、できる場合は自動的にサインインします。 したがって、Excel アドインの右上部にあるユーザー名を検証します。

Excel アドインは選択したエンティティのデータを自動的に読み取ります。 Excel アドインが読み取るまで、ワークブックにはデータがないことに注意してください。

## <a name="view-and-refresh-data-in-excel"></a>Excel でデータを表示または更新する
Excel アドインがエンティティ データをワークブックに読み込んだ後、 Excel アドインで**更新**をクリックしてデータをいつでも更新できます。

## <a name="edit-data-in-excel"></a>Excel でデータを編集
必要に応じてエンティティ データを変更でき、Excel アドインで**公開**をクリックして公開することもできます。

レコードを編集するには、ワークシートでセルを選択し、セル値を変更します。

新しいレコードを追加するには、以下の手順の 1 つに従います。

* ワークシートのどこかをクリックし、Excel アドインで**新規**をクリックします。
* ワークシートの最後の行をクリックし、カーソルがその行の最後の列から移動して新しい行が作成されるまで、Tab キーを押します。
* ワークシートのすぐ下の行でクリックして、セルへのデータの入力を開始します。 そのセルからフォーカスを移動する場合、新しい行を含めるためワークシートを拡張します。

レコードを削除するには、以下の手順の 1 つに従います。

* 削除するワークシート行の横にある行番号を右クリックし、**削除**をクリックします。
* 削除するワークシート行で右クリックし、**削除** > **テーブル行**をクリックします。

## <a name="add-or-remove-columns"></a>列の追加または削除
ワークシートに自動的に追加された列およびエンティティを調整するデザイナーを使用できます。

1. **オプション**ボタン (歯車のアイコン) をクリックして Excel アドインのでデータ ソース デザイナーを有効にし、**設計を有効にする**チェック ボックスを選択します。
2. Excel アドインで**設計**をクリックします。 すべてのソース データが表示されます。
3. データ ソースの隣にある**編集**ボタン (鉛筆アイコン) をクリックします。
4. 必要に応じて**選択されフィールド**フィールドで一覧を調整します。
   * **使用可能なフィールド**フィールドから**選択されたフィールド**フィールドにフィールドを追加するには、フィールドをクリックし、**追加**をクリックします。 または、フィールドをダブルクリックします。
   * **選択されたフィールド**フィールドからフィールドを削除するには、フィールドをクリックし、**削除**をクリックします。 または、フィールドをダブルクリックします。
   * フィールドの順序を変更するには、**選択されたフィールド**フィールドでフィールドをクリックし、**上**または**下**矢印をクリックします。
5. **更新**をクリックしてデータ ソースへの変更を適用し、**完了**をクリックしてデザイナーを終了します。 フィールド (列) を追加する場合、**更新**をクリックして更新された一連のデータを取り入れます。

> [!NOTE]
> 公開時にエラーが表示されることがあるため、ワークブックに ID および必須フィールドを常に含んでいることを確認します。

> [!NOTE]
> 検索フィールドを追加する場合、ID フィールドおよび表示フィールドの両方を追加するようにしてください。

## <a name="troubleshooting"></a>トラブルシューティング
簡単な手順により解決できるいくつかの問題は以下の通りです。

* すべてのエンティティで新しいレコードの作成と編集がサポートされているわけではありません。これらのエンティティは Excel で開いてデータを表示できますが、公開は無効です。
* 検索フィールドは、適切なレコードが参照されるようにアドインを使用して編集される必要があります。これらのフィールドをコピーや貼り付けして更新したり、またはフィールドに直接入力することはサポートされていません。


ここに記述されていない問題が発生した場合は、[サポート ページ](https://powerapps.microsoft.com/support/) を通してご連絡ください。

## <a name="next-steps"></a>次のステップ
* [エンティティでのフィールドの管理](data-platform-manage-fields.md)
* [エンティティ間での関連付けの定義](data-platform-entity-lookup.md)
* [Common Data Service を使用してアプリケーションを生成する](../canvas-apps/data-platform-create-app.md)
* [Common Data Serviceを使用してアプリをはじめから作成する](../canvas-apps/data-platform-create-app-scratch.md)

