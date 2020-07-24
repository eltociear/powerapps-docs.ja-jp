---
title: 'タイマー コントロール: リファレンス | Microsoft Docs'
description: 各種プロパティとサンプルを含むタイマー コントロールに関する情報
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/25/2016
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 88c96535de5fc4f77da06ca11ba3f6c49b37bcdd
ms.sourcegitcommit: c0508e233a03ac4846c04d5caae79eccca3e2843
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/15/2020
ms.locfileid: "3309305"
---
# <a name="timer-control-in-power-apps"></a>Power Apps のタイマー コントロール
一定の時間が経過した後のアプリの反応を決定できるコントロールです。

## <a name="description"></a>内容
たとえば、タイマーはコントロールが表示される時間の長さを決定したり、一定の時間が経過した後にコントロールの他のプロパティを変更したりすることができます。

> [!NOTE]
> Power Apps Studio では、タイマーはプレビュー モードでのみ実行されます。


## <a name="key-properties"></a>主要なプロパティ
**Duration** – タイマーを実行する時間の長さを、ミリ秒単位で指定します。 最大値は、ミリ秒で表される 24 時間です。 既定値は 60 秒です。

**OnTimerEnd** – タイマーが実行を完了した場合のアプリの反応を指定します。

**Repeat** – タイマーが実行を完了したときに自動的に再開するかどうかを指定します。

## <a name="additional-properties"></a>追加のプロパティ
**[配置](properties-text.md)** – コントロールの水平方向の中心に対するテキストの位置。

**AutoPause** – ユーザーが別の画面に移動した場合、タイマー コントロールを自動的に一時停止するかどうかを指定します。

**AutoStart** – ユーザーがタイマー コントロールを含む画面に移動したときに、自動的に再生を開始するかどうかを指定します。

**[BorderColor](properties-color-border.md)** – コントロールの境界線の色。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線が**実線**、**破線**、**点線**、または**なし**かどうか。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さ。

**[色](properties-color-border.md)** – コントロールのテキストの色。

**[DisplayMode](properties-core.md)** – コントロールがユーザー入力を許可するか (**編集**)、データのみを表示するか (**表示**)、または無効にするか (**無効**) どうか。

**[DisabledBorderColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロールの境界線の色。

**[DisabledColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロール内のテキストの色。

**[DisabledFill](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが**無効**に設定されている場合のコントロールの背景色。

**[塗りつぶし](properties-color-border.md)** – コントロールの背景色。

**[FocusedBorderColor](properties-color-border.md)** – コントロールがフォーカスされているときのコントロールの境界線の色。

**[FocusedBorderThickness](properties-color-border.md)** – コントロールがフォーカスされているときのコントロールの境界線の太さ。

**[フォント](properties-text.md)** – テキストを表示するフォントのファミリーの名前。

**[FontWeight](properties-text.md)** – コントロール内のテキストの太さ: **太字**、**中太**、**標準**、または**細字**。

**[高さ](properties-size-location.md)** – コントロールの上端と下端間の距離。

**[HoverBorderColor](properties-color-border.md)** – ユーザーがコントロール上にマウス ポインターを重ねているときのコントロールの境界線の色。

**[HoverColor](properties-color-border.md)** – ユーザーがコントロールにマウス ポインターを重ねているときのコントロール内のテキストの色。

**[HoverFill](properties-color-border.md)** – ユーザーがコントロールにマウス ポインターを重ねているときのコントロールの背景色。

**[斜体](properties-text.md)** – コントロール内のテキストを斜体にするかどうか。

**[OnSelect](properties-core.md)** – ユーザーがコントロールをタップまたはクリックする場合のアプリの反応方法。

**OnTimerStart** – タイマーが実行を開始したときのアプリの反応を指定します。

**[PressedBorderColor](properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロールの境界線の色。

**[PressedColor](properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロール内のテキストの色。

**[PressedFill](properties-color-border.md)** – ユーザーがコントロールをタップまたはクリックしたときのコントロールの背景色。

**[Reset](properties-core.md)** – コントロールを既定値に戻すかどうかを指定します。

**[サイズ](properties-text.md)** – コントロールに表示されるテキストのフォント サイズ。

**Start** – タイマーを開始するかどうかを指定します。

**[Strikethrough](properties-text.md)** – コントロールに表示されるテキストに取り消し線を付けるかどうか。

**[TabIndex](properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序。

**[テキスト](properties-core.md)** – コントロールに表示されるテキスト、またはユーザーがコントロールに入力するテキスト。

**[ツールヒント](properties-core.md)** – ユーザーがコントロールにカーソルを置くときに表示される説明テキスト。

**[下線](properties-text.md)** – コントロールに表示されるテキストの下に線を引くかどうか。

**[表示](properties-core.md)** – コントロールが表示されるか非表示になるか。

**[幅](properties-size-location.md)** – コントロールの左端と右端間の距離。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離。

## <a name="related-functions"></a>関連する関数
[**Refresh**( *DataSource* )](../functions/function-refresh.md)

## <a name="examples"></a>例
### <a name="show-a-countdown"></a>カウントダウンの表示
1. タイマーを追加して **Countdown** という名前を付けます。

    [コントロールの追加、名前付け、構成](../add-configure-controls.md) についてはこちらをご覧ください。
2. タイマーの **Duration** プロパティを **10000** に、その **Repeat** および **Autostart** プロパティを **true** に設定します。
3. (任意) **[Height](properties-size-location.md)** プロパティを **160** に、**[Width](properties-size-location.md)** プロパティを **600** に、**[Size](properties-text.md)** プロパティを **60** に設定して、タイマーを読み取りやすくします。
4. ラベルを追加し、その **[Text](properties-core.md)** プロパティを次の数式に設定します。
   <br>**「残りの秒数: 」 & RoundUp(10-Countdown.Value/1000, 0)**

    **[RoundUp](../functions/function-round.md)** 関数または [その他の関数](../formula-reference.md) については、各関連記事を参照してください。

    ラベルには、タイマーが再開されるまでの秒数が表示されます。

### <a name="animate-a-control"></a>コントロールのアニメーション
1. タイマーを追加して **FadeIn** という名前を付けます。

    [コントロールの追加、名前付け、構成](../add-configure-controls.md) についてはこちらをご覧ください。
2. タイマーの **Duration** プロパティを **5000** に、**Repeat** プロパティを **true** に、そして **[Text](properties-core.md)** プロパティを**アニメーションの切り替え**に設定します。
3. (任意) **[Height](properties-size-location.md)** プロパティを **160** に、**[Width](properties-size-location.md)** プロパティを **600** に、**[Size](properties-text.md)** プロパティを **60** に設定して、タイマーを読み取りやすくします。
4. ラベルを追加し、その **[Text](properties-core.md)** プロパティを設定して**ようこそ!** を表示し、 その **[Color](properties-color-border.md)** プロパティを次の数式に設定します。
   <br>**ColorFade(Color.BlueViolet, FadeIn.Value/5000)**

    **[ColorFade](../functions/function-colors.md)** 関数または [その他の関数](../formula-reference.md) については、各関連記事を参照してください。

5. アニメーションを開始または停止するには、タイマー ボタンを選択します。 ラベル内のテキストが白色にフェードした後、最大輝度に戻り、このプロセスが繰り返されます。

## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
ユーザーが操作を実行できる場合、**[ボタン](control-button.md)** コントロールと同じガイドラインが**タイマー** コントロールに適用されます。

### <a name="background-timers"></a>バックグラウンド タイマー
バックグラウンド タイマーは自動的に実行され、非表示になります。 経過時間がユーザーにほとんど関心のないサポート ロールで使用します。 たとえば、1 分ごとにデータを更新したり、また一定の時間だけ通知メッセージを表示したりできます。

バックグラウンド タイマーは **[Visible](properties-core.md)** プロパティを false に設定する必要があり、これによりすべてのユーザーに非表示になります。

### <a name="timing-considerations"></a>タイミングに関する考慮事項
**タイマー**が自動的に実行される場合、ユーザーがコンテンツを読み、使用するのに十分な時間があるかどうかを検討してください。 キーボード ユーザーおよびスクリーン リーダー ユーザーは、時間制限のあるイベントに反応するまでにより多くの時間がかかることがあります。

以下のいずれかの戦略で十分です。
* ユーザーが時間制限のあるイベントをキャンセルできるようにする。
* ユーザーが開始前に時間制限を調整できるようにする。
* 時間制限が切れる前に 20 秒間警告し、制限を簡単に延長する方法を提供する。

一部のシナリオでは、これらの要件は除外されます。 詳細については、[時間制限に関する WCAG 2.0 ガイドライン](https://www.w3.org/TR/WCAG20/#time-limits) を参照してください。

### <a name="screen-reader-support"></a>スクリーン リーダー サポート
* タイマーが現在の画面上での変更をトリガーする場合、[ライブ リージョン](../accessible-apps-live-regions.md) を使用してスクリーン リーダーのユーザーに変更内容を通知します。

    > [!NOTE]
    > タイマーが表示されていて実行中の場合、スクリーン リーダーは経過時間を 5 秒ごとに通知します。

* 時間的制約がある重要な情報のために、コントロールの **[Text](properties-core.md)** プロパティを使用しないでください。 スクリーン リーダーは **[テキスト](properties-core.md)** に変更を通知しません。
* 対話型タイマーの場合
    * **[Text](properties-core.md)** を指定する必要があります。
    * 経過時間を示すために、**[ラベル](control-text-box.md)** コントロールを追加することを検討してください。 タイマーの開始または停止をユーザーに指示するには、タイマーの **[Text](properties-core.md)** プロパティを使用します。
