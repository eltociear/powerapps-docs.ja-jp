---
title: Power BI 用の Power Apps ビジュアル | Microsoft Docs
description: 同じデータ ソースを使用して、Power BI の他のレポート項目と同様にフィルター処理することができるキャンバス アプリの埋め込みに関する手順と制限
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/29/2020
ms.author: ropur
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 14eaa34323208066f305016bcc7754c259f2f089
ms.sourcegitcommit: e2c92335fe6162c4576f0b86238ccbe4a7f74732
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2020
ms.locfileid: "3418193"
---
# <a name="power-apps-visual-for-power-bi"></a>Power BI 用の Power Apps ビジュアル

Power BI では、データ インサイトおよび適切な意思決定をすることができ、Power Apps は、すべてのユーザーがビジネス データに接続するアプリを作成して使用することができます。 Power Apps ビジュアルを使用して、コンテキスト認識データをキャンバス アプリに渡すことができます。キャンバス アプリは、レポートを変更するとリアルタイムで更新されます。 これで、アプリ ユーザーは、ビジネス インサイトを把握し、Power BI レポートとダッシュ ボード内で操作を実行できます。

## <a name="using-the-power-apps-visual"></a>Power Apps ビジュアルの使用

Power BI レポートで Power Apps ビジュアルを使用するために必要な手順を見ていきましょう。

1. Power Apps ビジュアルは、Power BI サービスを既定で使用できます。 Power BI Desktop を使用しているのに表示されない場合は、Power BI Desktop の最新バージョンにアップグレードする必要があります。

2. Power Apps ビジュアルをレポートに追加してから、それに関連付けられているデータ フィールドを設定します。

    ![レポート データの選択](./media/powerapps-custom-visual/add-visual-set-data.png)

    既存のアプリを選択したり、作成したりすることができますが、レポートを Power BI サービスに公開して、Microsoft Edge または Google Chrome で開く必要があります。

3.  アプリを作成する場合は、それを作成する環境を選択できます。

    ![新規または既存のアプリ](./media/powerapps-custom-visual/create-new-or-choose-app.png)

    既存のアプリを使用する場合は、ビジュアルは Power Apps アプリを開くように求めます。 次にビジュアルは、Power BI が Power Apps にデータを送信できるように、アプリで必要なコンポーネントを設定します。

    新しいアプリを作成する場合、Power Apps は現在設定されている必須コンポーネントで簡単なアプリを作成します。

    > [!NOTE]
    > アプリで `PowerBIIntegration.Refresh()` 関数を使用できるようにするには、Power BI レポートの Power Apps ビジュアルから新しいアプリを作成する必要があります。

    ![新規アプリ](./media/powerapps-custom-visual/new-app.png)

4. 現在、Power Apps Studio では、手順 2 で設定したデータ フィールドを使用できます。 `PowerBIIntegration` オブジェクトは他の Power Apps 読み取り専用データ ソースまたはコレクションと同様に機能します。 オブジェクトを使用して、すべてのコントロールを設定したり、他のデータ ソースを結合してフィルター処理したりすることができます。

    ![カスタム数式](./media/powerapps-custom-visual/custom-formula.png)

    この数式は、顧客のデータ ソースと Power BI のデータを結合します: `LookUp(Customer,Customer_x0020_Name=First(PowerBIIntegration.Data).Customer_Name)`

   Power BI レポートと起動された Power Apps Studio のインスタンスは、ライブ データの接続を共有します。 それらがどちらも開いている時は、レポート データをフィルター処理または変更して、更新されたデータが Power Apps Studio アプリですぐに反映されるようにすることができます。

5. アプリの構築または変更の完了後、Power Apps でアプリを保存および公開し、Power BI レポートにアプリを表示します。

6. 変更が完了したら、Power Apps アプリをレポート ユーザーと共有していることを確認してから、レポートを保存します。

7. ユーザーがアクションを実行してデータからインサイトを得ることができるレポートを作成できました。

    ![レポート操作](./media/powerapps-custom-visual/working-report.gif)

    アプリを変更する必要がある場合は、編集モードでレポートを開き、Power Apps ビジュアルで**その他のオプション** (**. . .**) を選択して、**編集**を選択します。

    ![アプリの編集](./media/powerapps-custom-visual/edit-app.png)

## <a name="limitations-of-the-power-apps-visual"></a>Power Apps ビジュアルの制限

Power Apps ビジュアルには次の制限が適用されます。

- Power Apps ビジュアルは、[ゲスト ユーザー](share-app.md#share-with-guests) ではサポートされません。
- Power Apps ビジュアルは、主権あるクラウドではサポートされていません。
- ビジュアルに関連付けられているデータ フィールドを変更する場合、省略記号 (...) を選択してから、**編集**を選択することによって、Power BI サービス内からアプリを編集する必要があります。 それ以外の場合は、Power Apps に変更が反映されず、アプリは予期しない方法で動作します。
- Power Apps ビジュアルは、Power BI Desktop 内から Power BI レポートと Power BI データ ソースの更新をトリガーできません。 アプリからレポートと同じデータ ソースにデータを書き戻す場合、変更内容は Power BI Desktop にすぐには反映されません。 変更内容は、次回のスケジュールされた更新で反映されます。
- Power Apps ビジュアルでは、データをフィルター処理したり、データをレポートに送信したりできません。
- レポートとは別に Power Apps アプリを共有する必要があります。 詳細: [Power Appsでのアプリの共有](share-app.md)。
- Power BI レポート サーバーは、Power Apps ビジュアルをサポートしていません。
- `PowerBIIntegration.Refresh()` 関数使用時に次の制限が適用されます。
    - アプリでこの関数を使用できるようにするには、Power BI レポートのPower Apps ビジュアルから新しいアプリを作成する必要があります。
    - [DirectQuery](https://docs.microsoft.com/power-bi/desktop-directquery-data-sources) をサポートするソースを使用し、DirectQuery メソッドを使用してデータ接続を作成する必要があります。
- Power BI Desktop の Power Apps は、アプリの作成時に Power Apps Studio にデータを提供しますが、編集中には提供しません。 アプリの編集中に Power BI Web を使用してデータをプレビューします。
- Power BI モバイル アプリは、Power Apps ビジュアルでのマイク コントロールをサポートしていません。

> [!NOTE]
> 最初にレポートを Power BI サービスに公開し、アプリを作成または変更することをお勧めします。

## <a name="browser-support"></a>ブラウザーのサポート

次の表は、Power Apps ビジュアルのアクションの表示、作成、および変更に対するブラウザー サポートの一覧を示します。 サポートされているブラウザとアクションは、チェックマーク (&check;) で識別されます。

|ブラウザー|ビュー​​|作成​​|修正
|-|-|-|-
|Microsoft Edge|&check;|&check;|&check;
|Internet Explorer 11|&check;
|Google Chrome|&check;|&check;|&check;
|Safari \*|&check;
|Mozilla Firefox
|他のすべてのブラウザー

\*Safari で、Power Apps ビジュアルを表示するには、サイト間の追跡を有効にします (**基本設定** > **プライバシー**、そして**サイト間の追跡を防止する**をオフにします)。

## <a name="accessibility-support"></a>ユーザー補助サポート

キーボードを使用して Power Apps ビジュアルを移動するには、次の手順を実行します。

1. 必要な Power Apps ビジュアルの Power BI レポートに選択をフォーカスします。
2. ビジュアルがハイライトされるまで、キーボードの**タブ** キーを使用します。
3. ビジュアルを入力するには、キーボードの **Ctrl + 右**キーを使用します。
3. 必要なビジュアル コンポーネントが選択されるまで、キーボードの**タブ** キーを使用します。

詳細については、[Power BI ユーザー補助に関するドキュメント]( https://docs.microsoft.com/power-bi/desktop-accessibility) を参照してください


## <a name="next-steps"></a>次の手順

* 簡単な[手順ごとのチュートリアル](https://docs.microsoft.com/power-bi/visuals/power-bi-visualization-powerapp) を実行します。
* [ビデオ](https://aka.ms/powerappscustomvisualvideo) をご覧ください。
