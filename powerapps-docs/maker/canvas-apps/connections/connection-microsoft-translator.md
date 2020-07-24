---
title: Microsoft Translator 接続の概要 | Microsoft Docs
description: いくつかの例を通して Microsoft Translator への接続方法の段階的説明とすべての機能について参照する
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 07/12/2017
ms.author: lanced
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 772f74b13d254746b75253012940efd8bda6e9d3
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3306361"
---
# <a name="connect-to-microsoft-translator-from-power-apps"></a>Power Apps から Microsoft Translator に接続する
![Microsoft Translator](./media/connection-microsoft-translator/translatoricon.png)

Microsoft Translator コネクタを追加すると、アプリの**ラベル** コントロールに翻訳されたテキストを表示できます。 たとえば、ユーザーに翻訳するテキストの入力を求める入力用のテキスト ボックスを作成できます。 また、別のラベルには翻訳されたテキストを表示できます。

このトピックでは、Microsoft Translator 接続の作成方法とアプリでの Microsoft Translator 接続の使用方法を説明し、使用可能な機能の一覧を示します。

> [!NOTE]
> このコネクタの呼び出し数は、ユーザーあたり 1 日 150 件に制限されています。

[!INCLUDE [connection-requirements](../../../includes/connection-requirements.md)]

## <a name="connect-to-microsoft-translator"></a>Microsoft Translator に接続する
1. Power Apps を開き、**新規**を選択してから、**空白のアプリ**を作成します。 携帯電話またはタブレットのレイアウトを選択します。 タブレットのレイアウトは、より多くのワークスペースを提供します:  

   ![空のアプリを開く](./media/connection-microsoft-translator/blank-app.png)
2. 右側のウィンドウで、**データ** タブをクリックまたはタップしてから、**データソースの追加**をクリックまたはタップします。
3. **新規接続**を選択してから、**Microsoft Translator** を選択します:  

    ![Microsoft Translator に接続する](./media/connection-microsoft-translator/addconnection.png)

    ![Microsoft Translator に接続する](./media/connection-microsoft-translator/add-translator.png)
4. **接続** を選択します。 **データ ソース**で接続が表示されます:  

    ![Microsoft Translator に接続する](./media/connection-microsoft-translator/translatordatasource.png)

## <a name="use-the-microsoft-translator-connection-in-your-app"></a>アプリで Microsoft Translator 接続を使用する
### <a name="translate-text"></a>テキストの翻訳
1. **挿入**メニューで、**テキスト**を選択してから、**テキスト入力**を選択します。 テキスト入力コントロールの名前を**ソース**に変更します:  

    ![名前の変更](./media/connection-microsoft-translator/renametosource.png)
2. **ドロップ ダウン** リスト (**挿入**メニュー > **コントロール**) を追加し、名前を **TargetLang** に変更して**ソース**の下に移動します。
3. **TargetLang** の **[項目](../controls/properties-core.md)** プロパティに次の式を設定します:  

    `MicrosoftTranslator.Languages()`
4. ラベルを追加して **TargetLang** の下に移動させ、**[テキスト](../controls/properties-core.md)** プロパティに次の式を設定します:  

    `MicrosoftTranslator.Translate(Source.Text, TargetLang.Selected.Value)`
5. **ソース**にテキストを入力し、**TargetLang** で言語を選択します。 ラベルに、入力したテキストが選択した言語で表示されます:  

    ![英語からスペイン語へのテキスト翻訳](./media/connection-microsoft-translator/translate-text.png)

### <a name="speak-translated-text"></a>翻訳されたテキストの読み上げ
まだ翻訳していない場合は、前のセクションの手順に従ってテキストを翻訳します。 以下の手順では、前のセクションと同じコントロールを使用します。

1. **TargetLang** のドロップダウン リストの **[項目](../controls/properties-core.md)** プロパティに次の式を設定します:  

    `MicrosoftTranslator.SpeechLanguages()`
2. 2 つ目のラベル (**ソース** ボックスではない方) の名前を**対象**に変更します。
3. **オーディオ** コントロール (**挿入**メニュー > **メディア**) を追加し、**メディア** プロパティに次の式を設定します:  

    `MicrosoftTranslator.TextToSpeech(Target.Text, TargetLang.Selected.Value)`
4. F5 キーを押すか、プレビュー ボタン (![](./media/connection-microsoft-translator/preview.png)) を選択します。 **ソース**にテキストを入力して **TargetLang** で言語を選択してから、オーディオ コントロールの再生ボタンを選択します。

    入力した言語が選択した言語の音声で読み上げられます。
5. 既定のワークスペースに戻るには、Esc キーを押します。

### <a name="detect-the-source-language"></a>ソース言語の検出
次の手順では、前のセクションと同じ**ソース**のテキスト入力コントロールと**対象**のテキスト コントロールを使用します。 必要であれば新しいコントロールを作成し、式の名前をその名前に更新してください。

1. **対象**のテキスト コントロールを選択し、**[テキスト](../controls/properties-core.md)** プロパティに次の式を設定します:  

    `MicrosoftTranslator.Detect(Source.Text).Name`
2. **ソース**にテキストを入力します。

    ラベルに、入力したテキストの言語が表示されます。 たとえば、ラベルには、**bonjour** と入力すると**フランス語**と表示され、**ciao** と入力すると**イタリア語**と表示されます。

## <a name="view-the-available-functions"></a>使用可能な関数を表示する
この接続には、次の関数が含まれています:

| 関数名 | 内容 |
| --- | --- |
| [言語](connection-microsoft-translator.md#languages) |Microsoft Translator でサポートされるすべての言語を取得します |
| [翻訳](connection-microsoft-translator.md#translate) |Microsoft Translator を使用してテキストを指定された言語に翻訳します |
| [検出](connection-microsoft-translator.md#detect) |入力したテキストのソース言語を検出します |
| [SpeechLanguages](connection-microsoft-translator.md#speechlanguages) |音声合成に使用できる言語を取得します |
| [TextToSpeech](connection-microsoft-translator.md#texttospeech) |入力したテキストを、WAVE 形式の音声ストリームの音声に変換する |

### <a name="languages"></a>言語
言語の取得: Microsoft Translator でサポートされるすべての言語を取得する

#### <a name="input-properties"></a>入力プロパティ
ありません。

#### <a name="output-properties"></a>出力プロパティ

| プロパティ名 | データの種類 | 必要な領域 | 内容 |
| --- | --- | --- | --- |
| コード |string |No | |
| 件名 |string |No | |

### <a name="translate"></a>翻訳
テキストの翻訳: Microsoft Translator を使用してテキストを指定された言語に翻訳する

#### <a name="input-properties"></a>入力プロパティ

| 件名 | データの種類 | 必要な領域 | 内容 |
| --- | --- | --- | --- |
| クエリ |string |はい |翻訳するテキスト |
| languageTo |string |はい |翻訳先言語のコード (例: 'fr'(フランス語)) |
| languageFrom |string |いいえ |ソース言語 (指定しない場合、自動検出が行われます) (例: en(英語)) |
| カテゴリ |string |いいえ |翻訳のカテゴリ (既定値: '一般') |

#### <a name="output-properties"></a>出力プロパティ
ありません。

### <a name="detect"></a>検出
言語の検出: 入力したテキストのソース言語を検出する

#### <a name="input-properties"></a>入力プロパティ

| 件名 | データの種類 | 必要な領域 | 内容 |
| --- | --- | --- | --- |
| クエリ |string |はい |言語を特定するテキスト |

#### <a name="output-properties"></a>出力プロパティ

| プロパティ名 | データの種類 | 必要な領域 | 内容 |
| --- | --- | --- | --- |
| コード |string |No | |
| 件名 |string |No | |

### <a name="speechlanguages"></a>SpeechLanguages
音声言語の取得: 音声合成に使用できる言語を取得する

#### <a name="input-properties"></a>入力プロパティ
ありません。

#### <a name="output-properties"></a>出力プロパティ

| プロパティ名 | データの種類 | 必要な領域 | 内容 |
| --- | --- | --- | --- |
| コード |string |No | |
| 件名 |string |No | |

### <a name="texttospeech"></a>TextToSpeech
テキストの音声変換: 入力したテキストを、WAVE 形式の音声ストリームの音声に変換する

#### <a name="input-properties"></a>入力プロパティ

| 件名 | データの種類 | 必要な領域 | 内容 |
| --- | --- | --- | --- |
| クエリ |string |はい |変換するテキスト |
| 言語 |string |はい |音声を生成する言語コード (例: 'en-us'(米国英語)) |

#### <a name="output-properties"></a>出力プロパティ
ありません。

## <a name="helpful-links"></a>便利なリンク
[使用可能な接続](../connections-list.md) をすべて参照してください。  
アプリに [接続を追加する](../add-manage-connections.md) 方法についてご確認ください。

