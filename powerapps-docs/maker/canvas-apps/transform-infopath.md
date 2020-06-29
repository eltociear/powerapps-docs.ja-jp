---
title: InfoPath フォームをキャンバス アプリに変換する | Microsoft Docs
description: 一般的なシナリオに関する情報、およびキャンバス アプリでのこれらの項目の作成方法を使用して、InfoPath フォームの Power Apps への変換を開始します。
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: article
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/05/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9c4796a652c6e42609010162794dcc60a6466864
ms.sourcegitcommit: d194d2fa009ca7bfcbe95e5f31473832a130e0a6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "3307465"
---
# <a name="transform-your-infopath-form-to-power-apps"></a>InfoPath のフォームを Power Apps に変換する

自分はInfoPath で作成した優れたものをさらに堅牢なプラットフォームで提供する方法について習得したいビルダーですか?

## <a name="key-advantages-of-power-apps-over-infopath"></a>InfoPath を超える Power Apps の主な利点

InfoPath のほとんどのパワー ユーザーと同様に、これまで特有のスキル セットを使用して優れたフォームを作成してきました。 ユーザーは自分で作成したフォームに非常に満足していますが、その制限も理解しています、&quot;古くさい&quot; 感じ、モバイル デバイスの理想的ではないエクスペリエンス、将来の可能性の不確実さ、およびコードを記述しないで他のサービスに接続しようとするといつでも制限があること、などです。

Power Apps チームには、こうした意見および他の多くの課題が伝えられています。 チームは、より良いエクスペリエンスに組み込み、ユーザーが既存のビジネスおよび技術的スキルを活用してキャンバス アプリを作成できるように努力してきました。 By using Power Apps を使用することで、コードを記述することなく、適切なビジネス ソリューションをすばやくビルドおよびデプロイすることができます。

**Power Apps が可能にする強力な将来**  
Power Apps はサービスとしてのソフトウェア (SaaS) プラットフォームであり、Web、SharePoint、Dynamics 365、Teams、Power BI、またはモバイル デバイスに余計な手間なしでデプロイすることができる高機能のアプリを短時間で構築できるように設計されています。 公開済みのアプリへの URL を伝えるだけでデプロイできるので、更新も簡単に行うことができます。

**アプリの共有**  
アプリを構築して、それを iOS または Android デバイス公開しようとしたことがありますか？ 複雑な作業です。 2 つ目のアプリをデプロイしたり、または既存のものを更新したりする場合、ユーザーは、はるかに多くの手順を実行する必要があります。 Power Apps とは違います。 ユーザーは自分のデバイスに Power Apps Mobile をインストールし、サインインします。 これで、ユーザーは共有されているすべての高機能アプリを利用できるようになります。 将来的には、これらのアプリを更新したり、または新しいアプリをユーザーにプッシュしたりすると、ユーザーのデバイスにこれらのアプリが表示されるようになります。 デバイス管理の問題がないモバイル アプリは、ユーザーおよびビジネスにとって大きな成功です。

**モバイルについて**  
Power Apps では、ユーザーのモバイル デバイスの機能を活用することができます。 アクセラレーション、カメラ、コンパス、接続情報、および場所信号などのすべてにアプリ内からアクセスできます。 これにより、作業を完了するためのアプリ構築の可能性がさらに広がります。 もちろん、Power Apps ではタッチ機能が自動的に行われ、アプリを構築するときに余分なコーディングは必要ありません。

**既成の枠を破る**  
InfoPath では、通常、1 つのソースからのデータを使用して作業します。 ただし、別のソース (別のサイト コレクションの SharePoint リストなど) を更新したり、または外部サービスに接続したりする場合、複雑になります。 分離コードなどの概念に悩まされることになります。 Power Apps は、複数のデータ ソースおよびサービス接続を 1 つのアプリで作業できるように設計されています。 現時点では、[200 を超えるコネクタ](connections-list.md#all-standard-connectors) で、Microsoft Office 365 および Power Automate と Dynamics 365 などの Azure サービスを含む、オンプレミスとクラウド データの組み合わせをサポートしています。 Dropbox、Google、Salesforce、Slack、および他の人気のある対象などの多数のサード パーティ サービスに接続することもできます。

元のデータがあった場所だけでなく、ユーザーが必要とする場所を拡張するソリューションを構築できます。

## <a name="power-apps-and-sharepoint-even-better-together"></a>Power Apps および SharePoint: 併用するとなお良い

Power Apps は、SharePoint エクスペリエンスを 2 つの方法で改善するための優れたツールです。 SharePoint リスト用のフォームをカスタマイズしたり、または SharePoint データを操作するためのスタンドアロン アプリを作成したりすることができます。

**SharePoint フォームのカスタマイズ**は、ユーザーが日常の作業に使用しているリストの項目を追加、表示、または編集する方法をカスタマイズする場合に適切です。 **フォームのカスタマイズ**をクリックすると、コンテキストに基づいてモード (新規/編集/表示) を変更する単一スクリーンの &quot;フォーム アプリ&quot; が作成されます。 SharePoint はこれらのアプリを管理され、そのアクセス許可は、編集/表示のためのリストのアクセス許可と同じです。

**SharePointから Power Apps キャンバス アプリを作成する** とモバイル デバイスでアプリを単独で実行することができます。 SharePoint ページにアプリを埋め込むこともできます。 これをクリックすると、3 スクリーンのアプリ (参照リスト、詳細の表示、および項目の作成/更新) が作成されます。 これらのアプリのアクセス許可/共有モデルは、SharePoint には関連付けられていませんが、代わりに Power Apps から管理されます。

2 つのオプションの違いを理解したので、次のセクションではそれぞれの使い方の概要を説明します。

## <a name="sharepoint-forms"></a>SharePoint のフォーム

Power Apps および SharePoint チームは一致協力して、SharePoint で使用するためのカスタマイズ ストーリーを作成してきました。 ほとんどの InfoPath 開発者であれば、SharePoint と対話するために InfoPath を学習しました。 SharePoint は優れていますが、既定のフォームは少し平凡であり、InfoPath なしではカスタマイズまたはビジネス ロジックに対応していません。 まあ、それももう昔の方法です。

Power Apps を使用して、ネイティブ機能としてリスト フォームをカスタマイズできます。 その場合、Power Apps のすべての機能を利用できます。 次のスクリーンショットでは、Power BI レポートが埋め込まれた Power Apps フォームの例を確認できます。 ソリューション全体は、15 分未満で完了しました。

![SharePoint 統合](./media/transform-infopath/sharepoint-integration.png)

Power Apps の別の重要な機能は、同じフォームから別の SharePoint サイト コレクションまたは異なる環境に簡単に接続できることです。 たとえば、SharePoint Online および SharePoint オンプレミス環境からのデータを同時に表示したり更新したりする 1 つのフォームを作成したいことはありませんか? 心配する必要はありません。 [オンプレミス データ ゲートウェイ](gateway-management.md) をインストールすると、数分で作業を開始し、Power Apps、Power BI、Power Automate、および Azure Logic Apps をオンプレミスのデータに接続できます。 ファイアウォール規則を変更する必要はありません。 このアプリを Power Automate に接続すると、さらに一歩進むことができます。

## <a name="a-standalone-sharepoint-app"></a>スタンドアロン SharePoint アプリ

リスト フォームのエクスペリエンスを更新するだけではなく、完全に構築する場合は、SharePoint データに基づくスタンドアロン アプリでこの手法を使います。 これは開始するのに最も良い方法でもあるので、Power Apps キャンバスがどのように機能するかを学習して、さまざまなデータ ソースから将来のアプリの構築を始めることができます。

開始するには、次の手順を実行します。

1. アプリの構築元となる SharePoint リストを開きます。
1. メニュー バーで **PowerApps** を選択し、次に**アプリの作成**を選択します。
1. 名前を指定し、次に**作成**を選択します。

Power Apps は、カスタマイズができるアプリを構築します。

最初のアプリ用に、異なる種類の 2 つだけのフィールドを含む簡単なカスタム リストを使用して開始します。 これにより、圧倒されることなく強固な基盤を構築することができます。 心配する必要はありません、すぐにプロになり複雑なアプリに取り組むことができます。 この最初のアプリを作成する手順については、こちらの [ドキュメント](app-from-sharepoint.md#create-an-app-from-within-sharepoint-online) またはこちらのコミュニティ [ビデオ](https://youtu.be/BnYe_7fpZRM) を参照してください。 次の例では、InfoPath の一般的なタスクおよび Power Apps でのその方法を表示します。 これらはそれぞれ、簡単な SharePoint リスト アプリを基に構築されています。

## <a name="how-do-you-do-that-with-power-apps"></a>Power Apps でどのように行いますか?

基本的な概念を理解したので、次に進みます。 最初のアプリが身についたので、このセクションは Power Apps で InfoPath の一般的な概念のいくつかを適用するのに役立ちます。

**値に基づいてフィールドを非表示/表示/ロックする**  
成功したフォームの多くは、たとえば値またはアクションに基づいてフィールドの状態を変更することにより、強力なビジネス ロジックを実施することがあります。 Power Apps では、コントロールの **DisplayMode** プロパティを**編集**または**表示**に設定して、ユーザーがフィールドを変更できるかどうかを指定できます。 簡単な **If** 数式を使用して、条件付きで行うこともできます。 最初に、編集するカードを選び、次にロック アイコンを選択します。 この手順によりカードをロック解除して、値が変更できるようにします。

![データ カードの非表示、表示、ロック](./media/transform-infopath/hide-show-lock.png)

右側のウィンドウで、**DisplayMode** プロパティまでスクロールして編集できるようにします。

![If-Else ステートメント式](./media/transform-infopath/if-else-statement.png)

この例では **If** 数式を使用します。

```If(ThisItem.Color = "Blue", DisplayMode.View, DisplayMode.Edit)```

この数式は、現在の項目の**色**フィールドが**青**の場合は**動物**フィールドが読み取り専用であることを示しています。 それ以外の場合は、フィールドは編集可能です。

カードを読み取り専用にするのではなく、非表示にするには、同様の関数を **DisplayMode** の真上の **Visible** プロパティに挿入します。

たとえば、ユーザーのメール アドレスが承認者のメール アドレスと一致する場合にのみ、承認ボタンが表示されるように試してみたりすることもできます。 (ヒント: **User().Email** を使用して現在のユーザーのメール アドレスにアクセスします。) したがって、承認者のメール アドレスを **YourDataCard** に格納し、次にボタンの **Visible** プロパティを次の数式に設定できます:

```If( YourDataCard.Text = User().Email, true, false )```

**条件付き書式**  
上でフィールドを非表示にしたのと同様の方法で、ユーザーにビジュアル フィードバックを提供することもできます。 入力された値が許容範囲外の場合はテキストを赤で強調表示したり、またはユーザーがファイルをアップロードした後にアップロード ボタンのテキストの色を変更したりする場合があります。 どちらも **Color** や **Visible** などのプロパティで **If** などの関数を使うことにより行うことができます。

たとえば、[IsMatch](functions/function-ismatch.md) 関数と組み合わせて **If** 関数を使用し、ユーザーが入力ボックスに適切に書式設定されたメールを入力しない場合に、メール フィールドのテキストの色を赤に変更できます。 これを行うには、**TextInput1** (ユーザーがメール アドレスを入力する場所) の**色**の値を次の数式に設定します。

```If( IsMatch(TextInput1.Text, Email), Black, Red )```

**IsMatch** では、メールなどの非常に多くの事前定義済みのパターンをサポートしたり、または独自に作成することもできます。 条件付き書式については、こちらの[コミュニティ ビデオ](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/PowerApps-Conditional-Formatting-and-Popups/m-p/84962) を参照してください。

**ロールベース セキュリティの実装**  
最初に検討する関数は [DataSourceInfo](functions/function-datasourceinfo.md) です。 データ ソースから戻る情報は異なりますが、多くの場合、この数式を使用して、ユーザーにデータを編集するアクセス権があるかどうかを確認できます (*YourDataSource* をデータ ソースの名前に置き換えます)。

```DataSourceInfo( YourDataSource, DataSourceInfo.EditPermission )```

これにより、ユーザーが編集するアクセス権を持っている場合にのみ、フォームまたはボタンを表示できます。 関数でクエリできる情報の完全な一覧に関しては、[DataSourceInfo](functions/function-datasourceinfo.md) ドキュメントを確認してください。

Active Directory グループを使用してアプリ内のボタンまたはフォームへのアクセスを管理する場合は、さらに深く掘り下げる必要があります。 これを行うには、Power Apps の柔軟性を利用し、Microsoft Graph API を使用して独自のコネクタを作成します。 困難に思える場合は、この[ブログ投稿](https://powerapps.microsoft.com/blog/implementing-role-based-permission/) の手順ごとのガイダンスに従うことができます。

**アプリからメールを送信**  
Power Apps からメール メッセージを送信するにはさまざまな方法がありますが、最も簡単なのは、Office 365 Outlook コネクタを使用することです。 このコネクタを使用すると、アプリからユーザーとしてメッセージを送信できます。 メール、およびメールボックスとやり取りするその他のタスクを取得できます。 メールの送信については、[ドキュメント](connections/connection-office365-outlook.md) またはこちらのコミュニティ [ビデオ](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/Send-an-email-from-PowerApps/m-p/74349) を参照してください。

Power Automate を使用したり、および作成したフローにアプリを接続することにより、さらに複雑なメッセージを (たとえば、一部の SharePoint 承認ワークフローとして) 送信できます。 アプリを Power Automate に接続すると、Power Apps のような外部データおよびサービスにとてもうまく接続するワークフロー エンジンの機能を最大限活用することが可能になります。 Power Apps および Power Automate に接続する方法の詳細については、こちらの[ドキュメント](using-logic-flows.md) を参照してください。

探しているメール オプションが見つからない場合は、ベンチマーク メール、Gmail、MailChimp、Outlook.com、SendGrid、または SMTP の Power Apps コネクタも利用できます。 接続性は、Power Apps の優れた点です。

**ワークフロー**  
ワークフロー エンジンなしにビジネス アプリおよびビジネス ロジックについて説明するのは容易ではありません。 良いニュースは、Power Apps チームがわざわざ一からやり直して別のワークフロー エンジンを提供するということをしなかったことです。 代わりに、Power Automate サービスへの堅牢なコネクタを提供します。 使いやすいワークフロー エンジンを通じて [200 以上のさまざまな サービス](https://flow.microsoft.com/connectors/) にわたりプロセスおよびタスクを自動化することができます。 Power Apps および Power Automate に接続する方法の詳細については、こちらの[ドキュメント](using-logic-flows.md) を参照してください。

**Power Apps の変数**  
ソリューションを構築するとき、変数を含める必要があると考えるのは自然です。 Power Apps には、複数の種類の変数が提供されていますが、必要なときにのみ使用します。 データを取得し、変数に格納して、次にその変数を参照することを考える代わりに、そのデータを直接参照することを考えてください。 Excel と比較すると、このモデルをより深く理解することができます。 Excel では、合計は変数ではなく他のフィールドの合計です。 したがって、シートの他の場所でそれを使う場合は、合計を計算したセルを指定します。 [ドキュメント](working-with-variables.md) には、これらのすべてが詳しく説明されています。 別の思考プロセスを受け入れてください。

それでも変数が必要な場合 (さまざまケースがあります)、これは異なるオプションを理解するのに役立ちます。 Power Apps では、変数を定義する必要がないことに留意してください。 関数を使用して格納する名前および値を指定するだけで、変数が作成されます。 **表示**タブの**変数**を選択すると、作成した変数を表示できます。変数はメモリ内に保持され、アプリを閉じるとその値は失われます。 次の種類の変数を作成できます。

- グローバル変数は、まず考えられる最も一般的なものです。 [Set](functions/function-set.md) 関数を使用して、グローバル変数の値を指定し、アプリ全体で使用できるにします。

    ```Set( YourVariable, YourValue )```

    次に、アプリ全体で、*YourVariable* を名前で参照できます。

- コンテキスト変数は、それらが定義されているスクリーンでのみ使用できます。 スクリーンから離れると、それらはリセットされます。 それらは、たとえば、前スクリーンから渡された情報を格納したり、またはフォームが送信されたかどうかを追跡したりするためによく使用されます。 コンテキスト変数を設定するには、この例のように、[UpdateContext](functions/function-updatecontext.md) 関数を使用します。

    ```UpdateContext( { Submitted: "true" } )```

    この例では、**Submitted** という名前の変数の値を **true** に設定します。 送信ボタンの **OnSelect** プロパティにこの数式を追加して、情報が送信されたことを追跡し、すべてのフィールドを読み取り専用に変更することができます。

- コレクションには、個別に更新可能な情報のテーブルが格納されます。 たとえば、ユーザーが送信するさまざまな SharePoint 項目にタグを付けるショッピング カートを作成するには、[Collect](functions/function-clear-collect-clearcollect.md) を使用します。 その概念の操作方法ついては、コミュニティ[ビデオ](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/Learn-about-PowerApps-Collections/m-p/89180) を参照してください。

**カスケード ドロップダウン**  
カスケード ドロップダウンは、たとえば、前のドロップダウンで選択した値に基づいて、1 つのドロップダウンの選択をフィルター処理できるため、非常に便利です。 Power Apps では、多くの場合、アプリに 2 つのデータ ソースを使用して作成されることがあります。 最初のデータ ソースは表示または更新しているデータで、2 つ目のデータ ソースはカスケード効果を構築するための値を格納します。 次の図は、2 つ目のデータ ソースと選択オプションの例を示します。

![カスケード ドロップダウン](./media/transform-infopath/cascading-dropdowns.png)

この例では、**ddSelectType** という名前のドロップダウンを追加し、その **Items** プロパティを次の数式に設定できます。

```Distinct( Impacts, Title )```

ドロップダウンには、コスト、プログラムの影響、およびスケジュールのみが表示されます。 次に、2 つ目のドロップダウンを追加して、その **Items** プロパティを次の数式に設定できます。

```Filter( Impacts, ddSelectType.Selected.Value in SCategory )```

このようにしてカスケード ドロップダウンを作成します。 詳細については、Power Apps チームからのこの投稿 [SharePoint: カスケード ドロップダウンを簡単な 4 つのステップで!](https://powerusers.microsoft.com/t5/PowerApps-Community-Blog/SharePoint-Cascading-Dropdowns-in-4-Easy-Steps/ba-p/16248) を参照してください またはこちらの[コミュニティ ビデオ](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/PowerApps-Cascading-Dropdown/m-p/92813)。 心配する必要はありません: SharePoint なしで簡単に行うことができます。

**1 つの スーパー アプリを構築しない**  
Power Apps では、アプリから別のアプリを呼び出すことができます。 したがって、間に合わせでまとめて構築した大量の InfoPath フォームの代わりに、相互に呼び出したり、データを渡したりすることさえもするアプリのグループを構築して、開発をより簡単にすることができます。

## <a name="next-steps"></a>次の手順

Power Apps とトピックの内容を使用して、どの状況にも対応して一度に 1 つのアプリを構築する準備ができました。 体験を続けながら、以下の Power Apps コミュニティ サイトへのリンクなどの、役立つ便利なリンクを参照してください。 コミュニティに参加して、自分独自よりもはるかに速くスキルを増してください。

[**数式のリファレンス**](formula-reference.md) - 一部の既定の数式を参照するたけでも、刺激を受けるのに優れた方法です。

[**Power Apps コミュニティ**](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1) - 例を参照し、他のユーザーと交流し、質問して回答し、Power Apps コミュニティの拡大にご協力ください。
