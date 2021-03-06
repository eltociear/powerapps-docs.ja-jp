---
title: Power BI の Power Apps ビジュアルMicrosoft Docs
description: 同じデータ ソースを使用し、Power BI の他のレポート項目と同様にフィルタリングできるキャンバス アプリの埋め込みに関する手順と制限
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/11/2020
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b3678c01210d5cb0398ce12e2111dba516404cfe
ms.sourcegitcommit: d500f44e77747a3244b6691ad9b3528e131dbfa5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79133587"
---
# <a name="power-apps-visual-for-power-bi"></a>Power BI 用の Power Apps ビジュアル

Power BI を使用すると、データの洞察が向上し、より的確な意思決定が可能になります。一方、Power Apps では、すべてのユーザーがビジネスデータに接続するアプリをビルドして使用できます。 Power Apps ビジュアルを使用すると、コンテキストに対応したデータを canvas アプリに渡すことができます。これは、レポートに変更を加えたときにリアルタイムで更新されます。 これで、アプリ ユーザーは、ビジネスの動向を把握し、Power BI レポートとダッシュ ボードから直接アクションを実行できます。

## <a name="using-the-power-apps-visual"></a>Power Apps ビジュアルの使用

Power BI レポートで Power Apps ビジュアルを使用するために必要な手順を見てみましょう。

1. Power Apps のビジュアルは、Power BI サービスでは既定で利用できます。 Power BI Desktop を使用していても表示されない場合は、最新バージョンの Power BI Desktop にアップグレードする必要があります。

2. Power Apps ビジュアルをレポートに追加し、関連付けられているデータフィールドを設定します。

    ![レポート データの選択](./media/powerapps-custom-visual/add-visual-set-data.png)

    既存のアプリを選択するか、またはアプリを作成できますが、レポートは Power BI サービスに発行し、Microsoft Edge または Google Chrome で開く必要があります。

3.  アプリを作成する場合は、それを作成する環境を選択できます。

    ![新規または既存のアプリ](./media/powerapps-custom-visual/create-new-or-choose-app.png)

    既存のアプリを使用することを選択した場合は、アプリを Power Apps で開くようにというメッセージが表示されます。 その後、ビジュアルはアプリに必要なコンポーネントを設定し、Power BI が Power Apps にデータを送信できるようにします。

    新しいアプリを作成する場合、Power Apps では、必要なコンポーネントが既に設定されている単純なアプリを作成します。

    > [!NOTE]
    > アプリで `PowerBIIntegration.Refresh()` 機能を使用できるようにするには Power BI レポートで、Power Apps ビジュアルから新しいアプリを作成する必要があります。

    ![新しいアプリ](./media/powerapps-custom-visual/new-app.png)

4. 現在、Power Apps Studio では、手順 2. で設定したデータフィールドを使用できます。 `PowerBIIntegration` オブジェクトは、他のすべての Power Apps 読み取り専用データソースまたはコレクションと同様に機能します。 オブジェクトを使用して、すべてのコントロールに入力できるほか、他のデータ ソースを結合したりフィルタリングしたりすることができます。

    ![ユーザー定義式](./media/powerapps-custom-visual/custom-formula.png)

    この数式は、顧客のデータ ソースと Power BI のデータを結合します。`LookUp(Customer,Customer_x0020_Name=First(PowerBIIntegration.Data).Customer_Name)`

   Power BI レポートと、起動された Power Apps Studio のインスタンスは、ライブデータ接続を共有します。 どちらも開いている間は、レポート内のデータをフィルター処理または変更して、更新されたデータが Power Apps Studio でアプリにすぐに反映されるようにすることができます。

5. アプリのビルドまたは変更が完了したら、アプリを Power Apps に保存して発行し、Power BI レポートにアプリを表示します。

6. 変更が完了したら、Power Apps アプリをレポートのユーザーと共有し、レポートを保存してください。

7. これで、ユーザー アクションを実行してデータから洞察を得ることができるレポートが作成されました。

    ![レポートの操作](./media/powerapps-custom-visual/working-report.gif)

    アプリに変更を加える必要がある場合は、レポートを編集モードで開き、[Power Apps] ビジュアルの [**その他のオプション**( **...** )] をクリックまたはタップして、 **[編集]** を選択します。

    ![アプリの編集](./media/powerapps-custom-visual/edit-app.png)

## <a name="limitations-of-the-power-apps-visual"></a>Power Apps ビジュアルの制限事項

Power Apps のビジュアルには、次の制限事項が適用されます。

- ビジュアルに関連付けられているデータ フィールドを変更する場合、省略記号 (...) を選択し、 **[編集]** を選択して Power BI サービス内でアプリを編集する必要があります。 そうしないと、変更は Power Apps に反映されず、アプリは予期しない方法で動作します。
- Power Apps ビジュアルでは、Power BI Desktop 内から Power BI レポートと Power BI データソースの更新をトリガーすることはできません。 アプリケーションからレポートと同じデータソースにデータを書き戻す場合、変更内容はすぐに Power BI Desktop に反映されません。 変更は、次回のスケジュールされた更新で反映されます。
- Power Apps のビジュアルでは、データをフィルター処理したり、レポートにデータを送信したりすることはできません。
- Power Apps アプリは、レポートとは別に共有する必要があります。 [Power apps でのアプリの共有](share-app.md)について説明します。
- Power BI Report Server は、Power Apps ビジュアルをサポートしていません。
- `PowerBIIntegration.Refresh()` 関数を使用する場合は、次の制限事項が適用されます。
    - この機能をアプリで使用できるようにするには Power BI レポートで、Power Apps ビジュアルから新しいアプリを作成する必要があります。
    - [Directquery](https://docs.microsoft.com/power-bi/desktop-directquery-data-sources)をサポートするソースを使用する必要があり、データ接続は directquery メソッドを使用して作成する必要があります。
- Power BI Desktop の power Apps は、アプリを作成するときに Power Apps Studio にデータを提供しますが、編集中は提供しません。 Power BI Web を使用して、アプリの編集中にデータをプレビューします。
- Power BI モバイルアプリは、Power Apps ビジュアルのマイクコントロールをサポートしていません。

> [!NOTE]
> 最初にレポートを Power BI サービスに発行してから、アプリを作成または変更することをお勧めします。

## <a name="browser-support"></a>ブラウザー サポート

次の表に、Power Apps ビジュアルの表示、作成、および変更アクションのブラウザーのサポートを示します。 サポートされているブラウザーとアクションは、チェックマーク (&check;) によって識別されます。

|ブラウザー|表示|作成|変更
|-|-|-|-
|Microsoft Edge|&check;|&check;|&check;
|Internet Explorer 11|&check;
|Google Chrome|&check;|&check;|&check;
|Safari \*|&check;
|Mozilla Firefox
|その他すべてのブラウザー

Safari で \*、サイト間の追跡を有効にする必要があります ( **[ユーザー設定]**  >  **[プライバシー]** をオンにして、 **[クロスサイトトラッキングを防止]** する をオフにする)。

## <a name="accessibility-support"></a>ユーザー補助機能のサポート

キーボードを使用して Power Apps ビジュアル内を移動するには、次の手順を実行します。

1. 目的の Power Apps ビジュアルの Power BI レポートでフォーカスを選択します。
2. ビジュアルが強調表示されるまで、キーボードの**Tab**キーを使用します。
3. キーボードの**Ctrl + Right**キーを使用してビジュアルを入力します。
3. ビジュアルの必要なコンポーネントが選択されるまで、キーボードの**Tab**キーを使用します。

詳細については、 [Power BI アクセシビリティのドキュメント]( https://docs.microsoft.com/power-bi/desktop-accessibility)を参照してください。


## <a name="next-steps"></a>次のステップ:

* 単純な[ステップ バイ ステップ チュートリアル](https://docs.microsoft.com/power-bi/visuals/power-bi-visualization-powerapp)を実行する。
* [ビデオ](https://aka.ms/powerappscustomvisualvideo)をご覧ください。
