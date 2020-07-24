---
title: モバイル アプリの使用 | Microsoft Docs
description: モバイルアプリの使用方法の概要を示します。
author: ramanasridhar
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 06/22/2020
ms.author: ramanasr
ms.reviewer: nkrb
ms.openlocfilehash: 6a60f851e32a063b135123e06f19a2c382021fba
ms.sourcegitcommit: bd543dccaa38bd63ad576f408c8b669c7e653ca3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/24/2020
ms.locfileid: "3500966"
---
# <a name="use-the-higher-education-crisis-financial-impact-tracker-mobile-app"></a>Higher Education Crisis Financial Impact Tracker モバイル アプリの使用

Higher Education Crisis Financial Impact Tracker アプリを使用すると、ユーザーは、取り組んでいるスポンサー プログラムを確認し、パンデミックやその他の危機によって引き起こされた努力損失を報告できます。

## <a name="prerequisites"></a>前提条件

モバイル アプリを開始するには、デバイスのアプリ ストアを使用して、Power Apps Mobile をデバイスにダウンロードする必要があります。

-  [Power Apps Mobile](https://powerapps.microsoft.com/downloads) のダウンロード。

    - iPhone や iPad などの Apple デバイスの場合は、[App ストア](https://aka.ms/powerappsios) を使用します。

    - Android デバイスの場合は、[Google Play](https://aka.ms/powerappsandroid) を使用します。

-   組織が [展開済み](deploy-solution.md) と [構成済み](configure-data.md) の Higher Education Crisis Financial Impact Tracker アプリを持っていることを確認します。

Power Apps Mobile をインストールした後、デバイスからアプリを開き、会社の Azure Active Directory アカウントでログインします。 サインインした後、組織が自分と共有しているすべてのアプリを表示できます。 詳細: [Power Apps モバイル デバイスのサインイン](https://docs.microsoft.com/powerapps/user/run-app-client#open-power-apps-and-sign-in)

## <a name="using-the-mobile-app"></a>モバイル アプリの使用

Power Apps Mobile から Higher Education Crisis Financial Impact Tracker アプリを開き、ウェルカム メッセージを確認してから **始めましょう** を選択します。

> [!div class="mx-imgBorder"]
> ![ようこそメッセージ](./media/welcome-cfit-app-message.png "ようこそメッセージ")

> [!NOTE]
> アプリを初めて開くと、ソリューションの管理アプリで構成されたウェルカム メッセージが表示されます。 今後表示しない場合は、**今後このメッセージを表示しない** を選択します。

## <a name="app-components"></a>アプリのコンポーネント 

Higher Education Crisis Financial Impact Tracker アプリは、次の主要コンポーネントで構成されています。

- [助成金](#grants): 共同主任研究者としてのあなたに関連付けられている助成金のリスト。 助成金やスポンサーのプログラムの概要を確認できます。

- [スポンサー プログラム](#sponsored-programs): 共同主任調査員として関連付けられているスポンサープログラムのリスト。 スポンサー プログラムの概要を確認し、各従業員の努力損失を報告できます。

- [従業員](#employees): **スポンサープログラム** タブ上のスポンサー プログラムに関連付けられている従業員のリスト。給与期間ごとの従業員の努力損失の概要を確認できます。

### <a name="sponsored-programs"></a>スポンサー プログラム

**スポンサー プログラム** タブで、共同主任調査員としてのあなたに関連付けられているスポンサープログラムのリストを確認できます。 検索ボックスにテキストを入力して、特定のプログラムを検索できます。

> [!div class="mx-imgBorder"]
> ![スポンサー プログラム](./media/list-of-sponsored-programs-records.png "スポンサー プログラム")

**>** を選択してスポンサープログラムに関する詳細を表示します。

**助成金** を選択して、[助成金の詳細](#grant-details) そして、同様に、**従業員** を表示して [従業員の詳細](#employee-details) を見ることができます。 また、右上隅に表示される情報記号 ![情報](./media/information-icon.png) を選択して、[よくある質問](#frequently-asked-questions) を表示します。

### <a name="sponsored-program-details"></a>スポンサー プログラムの詳細

**スポンサー プログラム** の詳細フォームを使用して、スポンサー付きプログラムの概要を確認し、各従業員の努力損失を報告できます。

> [!div class="mx-imgBorder"]
> ![スポンサー プログラムの詳細](./media/sponsored-programs-record-with-details.png "スポンサー プログラムの詳細")

**支払い期間**、**損失率**、**損失の理由** を入力します。 努力損失を報告する従業員を選択し、**送信する** を選択して努力損失を報告します。

左上隅で **<** を選択して、変更を送信せずにスポンサー プログラム リストに戻ります。 **送信する** を選択して、入力した値を送信します。

**スポンサー プログラムのフィールドと説明**

| フィールド   | 内容   |
|---------|---------------|
| 共同主任研究者  | 共同主任研究者の名前。  |
| 助成金   | このスポンサー プログラムが関連付けられている助成金の名前。 名前を選択して助成金の詳細を表示します。|
| スポンサー プログラムの説明 | スポンサー プログラムの説明。|
| スポンサー名 | スポンサー プログラムを後援している組織の名前。|
| 労力損失の影響額  | この時点で報告されている給与期間全体の努力損失の合計。|
| 労力損失の影響率 | これは、授与された合計額と比較したパーセンテージでの努力損失の合計です。 (努力損失影響度の額) / (アワード額)&times;100。|
| 支払い期間 | Higher Education Crisis Financial Impact Tracker 管理アプリで構成されている支払い期間を選択します。|
| 損失の割合 | 選択した給与期間の従業員の損失率を入力します。|
| 損失の理由 | 報告された損失の理由を選択します。|
| 従業員リスト | 選択したスポンサー プログラムで働いている従業員のリスト。|
|||

### <a name="grants"></a>補助金

**助成金** タブで、共同主任調査員としてのあなたに関連付けられている助成金のリストを確認できます。

> [!div class="mx-imgBorder"]
> ![助成金の一覧](./media/list-of-grants-records.png "助成金の一覧")

助成金の横にある **>** を選択して、助成金の詳細を表示します。

**スポンサー プログラム** を選択して、[スポンサー プログラムの詳細](#sponsored-program-details) そして、同様に、**従業員** を表示して [従業員の詳細](#employee-details) を見ることができます。 また、右上隅に表示される情報記号 ![情報](./media/information-icon.png) を選択して、[よくある質問](#frequently-asked-questions) を表示します。

### <a name="grant-details"></a>助成金の詳細

**助成金** 詳細フォームを使用して、選択した助成金に関連する助成金やスポンサー プログラムの概要を確認します。

> [!div class="mx-imgBorder"]
> ![助成金の詳細](./media/grant-records-with-details.png "助成金の詳細")

左上隅の **<** を選択して、**助成金** リストページに戻ります。

**助成金のフィールドと説明**

| フィールド  | 内容  |
|------------|----------------------|
| 助成金のタイトル  | 助成金のタイトルです。|
| 助成金番号 | 助成金の一意の番号です |
| 主任研究者 | 助成金の主任研究者の名前。  |
| 助成金の説明  | 助成金の説明です。  |
| 助成金の状態  | 助成金の状態。 |
| 開始日 | 助成が開始された日付。  |
| 終了日  | 助成金が終了する日付。 |
| スポンサー プログラムのリスト  | 助成金に関連付けられ、共同主任研究者としてあなたに関連付けられているすべてのスポンサー プログラムのリスト。|
| スポンサー名 | プログラムを後援している組織の名前。|
| 共同主任研究者 | 共同主任研究者の名前。|
| 努力の影響度％ | これは、授与された合計額と比較したパーセンテージでの努力損失の合計です。 (努力損失の影響額) / (アワード額)&times;100。 |
| 努力の影響度 (\$)  | この時点で報告されている複数の給与期間全体の努力損失の合計。|
| アワード金額 | スポンサー プログラムのアワード金額を入力します。|
| 利用可能残高 | スポンサー プログラムの利用可能残高。 |
|||

### <a name="employees"></a>社員

**従業員** タブで、スポンサー プログラム リストに関連付けられている従業員のリストを確認できます。

> [!div class="mx-imgBorder"]
> ![従業員のリスト](./media/list-of-employee-records.png "従業員のリスト")

従業員の横にある **>** を選択して、従業員の詳細を表示します。

**スポンサー プログラム** を選択して、[スポンサー プログラムの詳細](#sponsored-program-details) そして、同様に、**助成金** を表示して [助成金の詳細](#grant-details) を表示します。 また、右上隅に表示される情報記号 ![情報](./media/information-icon.png) を選択して、[よくある質問](#frequently-asked-questions) を表示します。

### <a name="employee-details"></a>従業員の詳細

**従業員** 詳細フォームを使用して、選択した従業員に関連する従業員や努力の影響度の概要を確認します。

> [!div class="mx-imgBorder"]
> ![従業員の詳細](./media/employee-record-with-details.png "従業員の詳細")

左上隅の **<** を選択して、従業員リストページに戻ります。

**従業員のフィールドと説明**

| フィールド   | 内容  |
|---------|--------------|
| 雇用形態 | 従業員の分類。 |
| 課 | 従業員の部署。|
| 氏名 | 従業員の氏名。|
| 大学 | 従業員の大学。|
| 年間基本給 | 従業員の年間基本給。 |
| 努力影響度のリスト  | 従業員が作業しているすべてのスポンサー プログラムのリスト、および各給与期間について報告された努力影響度。 |
| 報告期間 | 損失の影響が報告された支払い期間。|
| スポンサー プログラム | スポンサー プログラムの名前。|
| 平均努力 % | スポンサー プログラムに関連する従業員の平均努力。|
| 金額 (\$) | 給与の平均努力に基づく努力。|
| 努力影響度 % .| 給与期間について報告された努力影響度。|
| 努力の影響度 (\$) | 給与期間に対して報告された努力の影響度の値。|
| 努力損失の理由 | 給与期間に対する努力損失の理由。|
|||

### <a name="frequently-asked-questions"></a>よく寄せられる質問

任意の画面で情報記号 ![情報](./media/information-icon.png) を選択すると、よくある質問を確認できます。 これらのよくある質問は、組織のルールとガイドラインに基づいて、Higher Education Crisis Financial Impact Tracker 管理アプリで構成されます。 詳細情報が必要な場合は、システム管理者にお問い合わせください。 左上隅の **<** を選択して、前のページに戻ります。

> [!div class="mx-imgBorder"]
> ![よくあるご質問の詳細](./media/frequently-asked-questions-record-with-details.png "よく寄せられる質問の詳細")

## <a name="issues-and-feedback"></a>問題とフィードバック 

- Higher Education Crisis Financial Impact Tracker アプリの問題を報告するには、<https://aka.ms/crisis-financial-impact-tracker-issues> にアクセスしてください。
- Higher Education Crisis Financial Impact Tracker アプリに関するフィードバックについては、<https://aka.ms/crisis-financial-impact-tracker-feedback> にアクセスしてください。

