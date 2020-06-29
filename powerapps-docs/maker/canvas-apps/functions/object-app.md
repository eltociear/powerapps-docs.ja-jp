---
title: アプリ オブジェクト | Microsoft Docs
description: Power Apps でのアプリ オブジェクトの構文と例を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/29/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f5f09bab44f3f229b47d9a801703b3aa10cba06d
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/13/2020
ms.locfileid: "3308638"
---
# <a name="app-object-in-power-apps"></a>Power Apps のアプリ オブジェクト

現在実行中のアプリとアプリの動作に対する制御に関する情報を提供します。

## <a name="description"></a>内容

コントロールのように、**アプリ** オブジェクトは、表示されている画面を識別し、変更が失われないように保存するようユーザーに促すプロパティを提供します。 すべてのアプリには**アプリ** オブジェクトがあります。

**アプリ** オブジェクトの一部のプロパティには、式を記述することができます。 **ツリー ビュー** ウィンドウの一番上で、その他のコントロールまたは画面と同じように**アプリ** オブジェクトを選択します。 数式バーの左側にあるドロップダウン リストでオブジェクトのプロパティの 1 つを選択して、表示および編集を行います。

> [!div class="mx-imgBorder"]
> ![ツリー ビュー ウィンドウのアプリ オブジェクト](media/object-app/appobject.png)

## <a name="activescreen-property"></a>ActiveScreen プロパティ

**ActiveScreen** プロパティは、表示されている画面を識別します。

このプロパティは、スクリーン オブジェクトを返します。このオブジェクトを使って画面のプロパティを参照したり、別の画面と比較してどちらの画面が表示されているかを調べたりすることができます。 **App.ActiveScreen.Name** 式を使用して、表示されている画面の名前を取得することもできます。

**[Back](function-navigate.md)** または **[Navigate](function-navigate.md)** 関数を使用して、表示されている画面を変更します。

## <a name="onstart-property"></a>OnStart プロパティ

**OnStart** プロパティは、ユーザーがアプリを開始するときに実行されます。 多くの場合、アプリ メーカーは、このプロパティを使用して次のタスクを実行します。

- **[Collect](function-clear-collect-clearcollect.md)** 関数を使用して、データをコレクションに取得し、キャッシュします。
- **[Set](function-set.md)** 関数を使用して、グローバル変数を設定します。
- **[ナビゲート](function-navigate.md)** 関数を使用して、初期画面に移動します。

この数式は最初の画面が表示される前に評価されます。 画面が読み込まれないため、**[UpdateContext](function-updatecontext.md)** 関数を使用してコンテキスト変数を設定することはできません。 ただし、**Navigate** 関数を使用してコンテキスト変数を渡すことはできます。

**OnStart** プロパティを変更した後、**ツリー ビュー** ウィンドウの**アプリ** オブジェクトにカーソルを合わせることによりテストすることができ、表示される省略記号 (...) を選択してから、**Run OnStart** を選択します。 アプリが初めて読み込まれるときとは異なり、既存のコレクションおよび変数はすでに設定されています。 空のコレクションから始めるには、**Collect** 関数の代わりに、**[ClearCollect](function-clear-collect-clearcollect.md)** 関数を使用します。

> [!div class="mx-imgBorder"]
> ![OnStart で実行用のアプリ アイテム ショートカット メニュー](media/object-app/appobject-runonstart.png)

## <a name="confirmexit-properties"></a>ConfirmExit プロパティ

保存されていない変更を失いたい人はいません。 **ConfirmExit** および **ConfirmExitMessage** プロパティを使用し、アプリを閉じる前にユーザーに警告します。

> [!NOTE]
> たとえば、Power BI および SharePoint など、埋め込まれたアプリで **ConfirmExit** は動作しません。

> [!NOTE]
> 現在、**遅延読み込み**プレビュー機能が有効になっている場合 (新しいアプリでは既定)、これらのプロパティは、最初の画面のコントロールだけを参照することができます。 参照が作成される場合、Power Apps Studio はエラーを表示しませんが、結果として公開されるアプリは Power Apps モバイルまたはブラウザーでは開きません。 この制限の解消に積極的に取り組んでいます。 それまでの間、**ファイル** > **アプリ設定** > **詳細設定** (**プレビュー機能**の下) で、**遅延読み込み**をオフにすることができます。

### <a name="confirmexit"></a>ConfirmExit

**ConfirmExit** は、*true* の場合、アプリを閉じる前に確認ダイアログ ボックスを開く、ブール値のプロパティです。 既定では、このプロパティは *false* で、ダイアログ ボックスは表示されません。

このプロパティを使用して、ユーザーが変更を加えた後、保存していない場合に確認ダイアログ ボックスを表示します。 変数およびコントロールのプロパティを確認する式を使用します ([**編集フォーム**](../controls/control-form-detail.md) コントロールの **Unsaved** プロパティなど)。

次の例のように、データが失われる可能性がある状況では、確認ダイアログ ボックスが表示されます。

- [**Exit**](function-exit.md) 関数を実行しています。
- アプリがブラウザーで実行されている場合。
  - アプリが実行されているブラウザーまたはブラウザー タブを閉じます。
  - ブラウザーの戻るボタンを選択します。
- アプリが Power Apps モバイル (iOS または Android) で実行されている場合。
  - [**Launch**](function-param.md) 関数を実行しています。<br>**Launch** 関数は、その他のタブを開いてデータが失われないようにするため、ブラウザーのダイアログ ボックスをトリガーしません。
  - スワイプすることで、Power Apps モバイルの異なるアプリに切り替えます。
  - Android デバイス上の戻るボタンを選択します。

確認ダイアログ ボックスの正確な外観は、Power Apps のデバイスおよびバージョン間でさまざまです。

確認ダイアログ ボックスは、Power Apps Studio では表示されません。

### <a name="confirmexitmessage"></a>ConfirmExitMessage

既定では、確認ダイアログ ボックスに**変更が保存されていない可能性があります。** などの、汎用メッセージが表示されます ユーザーの言語。

**ConfirmExitMessage** を使用し、確認ダイアログ ボックスのカスタム メッセージを指定します。 このプロパティが*空白*の場合、既定値が使用されます。 カスタム メッセージは確認ダイアログ ボックスに合わせて必要に応じて切り詰められるため、メッセージは最大で数行にします。

ブラウザー内で、確認ダイアログ ボックスにブラウザーからの汎用メッセージが表示されることがあります。

### <a name="example"></a>例

1. **AccountForm** および **ContactForm** の、2 つのフォーム コントロールを含むアプリを作成します。

1. **アプリ** オブジェクトの **ConfirmExit** プロパティをこの式に設定します。

    ```powerapps-dot
    AccountForm.Unsaved Or ContactForm.Unsaved
    ```

    このダイアログボックスは、ユーザーがいずれかのフォームでデータを変更し、変更を保存せずにアプリを閉じようとした場合に表示されます。

    > [!div class="mx-imgBorder"]
    > ![汎用の確認ダイアログ ボックス](media/object-app/confirm-native.png)

1. **アプリ** オブジェクトの **ConfirmExitMessage** プロパティをこの数式に設定します。

    ```powerapps-dot
    If( AccountsForm.Unsaved,
        "Accounts form has unsaved changes.",
        "Contacts form has unsaved changes."
    )
    ```

    このダイアログボックスは、ユーザーが取引先企業フォームでデータを変更し、変更を保存せずにアプリを閉じようとした場合に表示されます。

    > [!div class="mx-imgBorder"]
    > ![フォーム固有の確認ダイアログ ボックス](media/object-app/confirm-native-custom.png)
