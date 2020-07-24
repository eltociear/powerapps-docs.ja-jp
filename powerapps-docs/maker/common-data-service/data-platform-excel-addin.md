---
title: エンティティ データを Excel で開く | Microsoft Docs
description: 対話型の表示および編集用に Excel でエンティティ データを開きます。
author: lancedMicrosoft
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 06/03/2020
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: b5621e8ccade35ec59ca0eab4d2578ddfc517648
ms.sourcegitcommit: 909948d219c3c61d617f13aceb355e1d5bcb0b55
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2020
ms.locfileid: "3432797"
---
# <a name="open-entity-data-in-excel"></a>エンティティ データを Excel で開く
Microsoft Excel でエンティティ データを開くことで、 Microsoft Power Apps Excel アドインを使用してすばやく簡単にデータを表示、編集することができます。 <!-- The Power Apps Excel Add-in requires Microsoft Excel 2016. -->

> [!div class="mx-imgBorder"] 
> ![Excel アドイン](./media/data-platform-cds-excel-addin/ExcelAddin.png "Power Apps Excel アドイン")

Power Apps Excel のアドインをインストールするには、[Microsoft PowerApps Office のアドイン](https://appsource.microsoft.com/en-us/product/office/WA104380330?tab=Overview)を参照してください。 Office Excel アドインを追加、削除する方法の詳細については、[Excel でアドインを追加、削除する](https://support.office.com/en-us/article/add-or-remove-add-ins-in-excel-0af570c4-5cf3-4fa9-9b88-403625a0b460)を参照してください。

## <a name="open-entity-data-in-excel"></a>エンティティ データを Excel で開く
1. [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインします。

1. 左ウィンドウで、**データ**セクションを展開し、**エンティティ**を選択します。 すべてのエンティティが表示されます。

2. 関心のあるエンティティの右側にある省略記号 (...) を選択し、続いて**Excel でデータを編集する**を選択します。 

3. ブラウザの既定のダウンロード フォルダにダウンロードされている Excel ワークシートを開きます (*エンティティ名 (1591125669213).xlsx*)。 このワークブックには、エンティティのバインド情報、環境へのポインタおよび Power Apps Excel アドイン へのポインタが含まれています。

4. Excel で、**編集を有効にする** を選択して Power Apps Excel アドインの実行を有効化します。 Excel ウィンドウの右側にあるウィンドウで Excel アドインを実行します。

    > [!IMPORTANT]
    > ウィンドウにエラーメッセージが表示される場合は、[Office ストア アドインのダウンロードを無効化する](#office-store-add-in-download-disabling)を参照してください。 

5. 初めて Power Apps アドインを実行した場合、**このアドインを信頼する** を選択して Excel アドインの実行を許可します。

6. サインインを要求された場合は、**サインイン**を選択し、[Power Apps](https:///?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) で使用したものと同じ資格情報を使用してサイン インします。 Excel アドインでは、前のサインインのコンテキストを使用し、できる場合は自動的にサインインします。 したがって、Excel アドインの右上部にあるユーザー名を検証します。

Excel アドインは選択したエンティティのデータを自動的に読み取ります。 Excel アドインが読み取るまで、ワークブックにはデータがないことに注意してください。

## <a name="view-and-refresh-data-in-excel"></a>Excel でデータを表示または更新する
Excel アドインがエンティティ データをワークブックに読み込んだ後は、 Excel アドインで**更新**を選択していつでもデータを更新できます。

## <a name="edit-data-in-excel"></a>Excel でデータを編集
エンティティ データは、必要に応じて変更でき、Excel アドインで**公開**を選択して公開することもできます。

レコードを編集するには、ワークシートでセルを選択し、セル値を変更します。

新しいレコードを追加するには、以下の手順の 1 つに従います。

* ワークシートのどこかを選択して、Excel アドインで**新規**を選択します。
* ワークシートの最後の行を選択し、カーソルがその行の最後の列から外れるまで Tab キーを押すと、新たな行が作成されます。
* ワークシートのすぐ下の行で選択して、セルにデータの入力を開始します。 そのセルからフォーカスを移動する場合、新しい行を含めるためワークシートを拡張します。

レコードを削除するには、以下の手順の 1 つに従います。

* 削除するワークシート行の横にある行番号を右クリックし、**削除**を選択します。
* 削除するワークシート行で右クリックし、**削除** > **テーブル行**選択します。

## <a name="add-or-remove-columns"></a>列の追加または削除
ワークシートに自動的に追加された列およびエンティティを調整するデザイナーを使用できます。

1. **オプション** ボタン (歯車のアイコン) をクリックして Excel アドインのデータ ソース デザイナーを有効化し、**データ コネクター**セクションを展開し、続いて**設計を有効化する**チェック ボックスを選択します。

2. Excel アドインで**設計**を選択します。 すべてのソース データが表示されます。

3. データ ソースの隣にある**編集**ボタン (鉛筆アイコン) を選択します。

4. 必要に応じて**選択されフィールド**フィールドで一覧を調整します。
   * **使用可能なフィールド**フィールドから**選択されたフィールド**フィールドにフィールドを追加するには、フィールドを選択し、**追加**を選択します。 または、フィールドをダブルクリックします。
   * **選択されたフィールド**フィールドからフィールドを削除するには、フィールドを選択し、**削除**を選択します。 または、フィールドをダブルクリックします。
   * フィールドの順序を変更するには、**選択されたフィールド**フィールドでフィールドを選択し、**上**または**下**矢印を選択します。

5. **更新**を選択してデータ ソースへの変更を適用し、**完了**を選択してデザイナーを終了します。 フィールド (列) を追加する場合、**更新**を選択して更新された一連のデータを取り込みます。

> [!NOTE]
> - 公開時にエラーが表示されることがあるため、ワークブックに ID および必須フィールドを常に含んでいることを確認します。
> - 検索フィールドを追加する場合、ID フィールドおよび表示フィールドの両方を追加するようにしてください。

## <a name="troubleshooting"></a>トラブルシューティング
簡単な手順により解決できるいくつかの問題は以下の通りです。

* すべてのエンティティで新しいレコードの作成と編集がサポートされているわけではありません。これらのエンティティは Excel で開いてデータを表示できますが、公開は無効です。
* 検索フィールドは、適切なレコードが参照されるようにアドインを使用して編集される必要があります。これらのフィールドをコピーや貼り付けして更新したり、またはフィールドに直接入力することはサポートされていません。

ここに記述されていない問題が発生した場合は、[サポート ページ](https://powerapps.microsoft.com/support/) を通してご連絡ください。

### <a name="office-store-add-in-download-disabling"></a>Office Storeアドインのダウンロードを無効化する
組織で Office Store アドインのダウンロードが無効化されている場合、[Excelでデータを編集] コマンドを選択した後に Excel ワークシートを開くと、次のようなエラーメッセージが表示される場合があります。 

*Office 365 は、Office Store アドインの個別の取得と実行ができないように構成されています。*

この設定により、Power Apps Excelアドインでダウンロードができなくなります。 この場合、エンティティ レコード データはExcelに表示されません。 

Office Store アドインのダウンロードを有効にする方法の詳細については、Office アプリの管理者にお問い合わせください。 

Office Store から Office Store アドインをダウンロードできないようにする方法の詳細については、[すすべてのクライアントで Office Store をオフにしてアドインのダウンロードを防止する](/microsoft-365/admin/manage/manage-deployment-of-add-ins?view=o365-worldwide#prevent-add-in-downloads-by-turning-off-the-office-store-across-all-clients-except-outlook) を参照してください。

## <a name="other-ways-to-export-and-view-entity-record-data"></a>エンティティ レコード データをエクスポートして表示するその他の方法
エンティティ レコード データをエクスポートして表示する方法の詳細については、以下の記事を参照してください。
- [CSV 形式でデータをエクスポートする](/powerapps/maker/common-data-service/data-platform-import-export#export-data-to-csv) 
- [Excel Online にデータをエクスポートする](/powerapps/user/export-to-excel-online)
- [エンティティデータを Azure Data Lake Storage Gen2 にエクスポートする](/powerapps/maker/common-data-service/export-to-data-lake)
- [データフローでセルフサービス データを準備する](/powerapps/maker/common-data-service/self-service-data-prep-with-dataflows)


### <a name="see-also"></a>関連項目
* [エンティティでのフィールドの管理](data-platform-manage-fields.md)
* [エンティティ間での関連付けの定義](data-platform-entity-lookup.md)
* [Common Data Service を使用してアプリケーションを生成する](../canvas-apps/data-platform-create-app.md)
* [Common Data Serviceを使用してアプリをはじめから作成する](../canvas-apps/data-platform-create-app-scratch.md)

