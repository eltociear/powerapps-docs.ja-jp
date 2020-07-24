---
title: EditForm、NewForm、SubmitForm、ResetForm、および ViewForm 関数 | Microsoft Docs
description: Power Apps での EditForm、NewForm、SubmitForm、ResetForm、および ViewForm 関数の構文と例を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 07/06/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8cb2acc15d7d82e2c0935133ffdaf5e4f5284f0c
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3305165"
---
# <a name="editform-newform-submitform-resetform-and-viewform-functions-in-power-apps"></a>Power Apps での EditForm、NewForm、SubmitForm、ResetForm、および ViewForm 関数
**[編集フォーム](../controls/control-form-detail.md)** コントロールで、項目の表示、編集、または作成、内容の保存、およびコントロールのリセットを行います。

## <a name="overview"></a>概要
これらの関数は、**編集フォーム**コントロールの状態を変更します。  フォーム コントロールは、次のモードのいずれかになります。

| MODE | 内容 |
| --- | --- |
| **FormMode.Edit** |フォームには、既存のレコードが設定され、ユーザーはフィールドの値を変更できます。  完了すると、ユーザーはレコードに変更を保存できます。 |
| **FormMode.New** |フォームは既定値が設定され、ユーザーはフィールドの値を変更できます。  完了すると、ユーザーはレコードをデータ ソースに追加できます。 |
| **FormMode.View** |フォームには既存のレコードが設定されますが、ユーザーはフィールドの値を変更できません。 |

## <a name="description"></a>内容
これらの関数は多くの場合、**[Button](../controls/control-button.md)** または **[Image](../controls/control-image.md)** コントロールの **[OnSelect](../controls/properties-core.md)** 数式から呼び出され、ユーザーが編集を保存、編集を破棄、またはレコードを作成したりできるようにします。 [コントロールおよびこれらの関数を併用して](../working-with-forms.md) 完全なソリューションを作成できます。

これらの関数は値を返しません。

### <a name="submitform"></a>SubmitForm
Button コントロールの **[OnSelect](../controls/properties-core.md)** プロパティで **SubmitForm** 関数を使用して、フォーム コントロールの変更をデータ ソースに保存します。

変更が送信される前に、この関数では必須としてマークされている、またはその値に 1 つ以上の制約があるフィールドの検証の問題をチェックします。 この動作は、**[Validate](function-validate.md)** 関数の動作と同じです。

**SubmitForm** では、フォーム コントロールに含まれる **[Card](../controls/control-card.md)** コントロールのすべての **[Valid](../controls/control-card.md)** プロパティの集計である、フォームの **[Valid](../controls/control-form-detail.md)** プロパティもチェックされます。 問題が発生した場合、データは送信されず、フォーム コントロールの **[Error](../controls/control-form-detail.md)** および **[ErrorKind](../controls/control-form-detail.md)** プロパティがそれに応じて設定されます。

検証に合格した場合、**SubmitForm** は変更をデータ ソースに送信します。

* 成功した場合は、フォームの **[OnSuccess](../controls/control-form-detail.md)** 動作が実行され、**[Error](../controls/control-form-detail.md)** および **[ErrorKind](../controls/control-form-detail.md)** プロパティがクリアされます。  フォームが **FormMode.New** モードの場合は、**FormMode.Edit** モードに返されます。
* 成功しなかった場合は、フォームの **[OnFailure](../controls/control-form-detail.md)** 動作が実行され、**[Error](../controls/control-form-detail.md)** および **[ErrorKind](../controls/control-form-detail.md)** プロパティがそれに応じて設定されます。  フォームのモードは変更されません。  

### <a name="editform"></a>EditForm
**EditForm** 関数は、フォーム コントロールのモードを **FormMode.Edit** に変更します。 このモードで、フォーム コントロールの **[Item](../controls/control-form-detail.md)** プロパティの内容はフォームの設定に使用されます。  フォームがこのモードの場合に **SubmitForm** 関数が実行されると、レコードの作成ではなく変更が行われます。  **FormMode.Edit** は、フォーム コントロールの既定です。

### <a name="newform"></a>NewForm
**NewForm** 関数では、フォーム コントロールのモードが **FormMode.New** に変更されます。 このモードでは、フォーム コントロールの **[Item](../controls/control-form-detail.md)** プロパティの内容が無視され、フォームの **[DataSource](../controls/control-form-detail.md)** プロパティの既定値がフォームに設定されます。 フォームがこのモードの場合に **SubmitForm** 関数が実行されると、レコードの変更ではなく作成が行なわれます。

### <a name="resetform"></a>ResetForm
**ResetForm** 関数は、ユーザーが変更を行う前に、フォームの内容を初期値にリセットします。 フォームが **FormMode.New** モードである場合、フォームは **FormMode.Edit** モードにリセットされます。 フォーム コントロールの **[OnReset](../controls/control-form-detail.md)** 動作も実行されます。  **[Reset](function-reset.md)** 関数を使用して個々のコントロールをリセットすることもできますが、フォーム内からのみです。

### <a name="viewform"></a>ViewForm
**ViewForm** 関数は、フォーム コントロールのモードを **FormMode.View** に変更します。 このモードで、フォーム コントロールの **[Item](../controls/control-form-detail.md)** プロパティの内容はフォームの設定に使用されます。  このモードの場合、**SubmitForm** および **ResetForm** 関数は無効になります。

### <a name="displaymode-property"></a>DisplayMode プロパティ
現在のモードは **Mode** プロパティによって読み取ることができます。  モードは、フォーム コントロール内のデータ カードおよびコントロールで使用できる **DisplayMode** プロパティの値も決定します。  多くの場合、データ カードの **DisplayMode** プロパティは **Parent.DisplayMode** (フォームを参照) に設定され、コントロールの **DisplayMode** プロパティ (データ カードを参照) と同様です。 

| MODE | DisplayMode | 内容 |
| --- | --- | --- |
| **FormMode.Edit** |**DisplayMode.Edit** |データ カードとコントロールは編集可能で、レコードへの変更を受け入れる準備ができています。 |
| **FormMode.New** |**DisplayMode.Edit** |データ カードとコントロールは編集可能で、新しいレコードを受け入れる準備ができています。 |
| **FormMode.View** |**DisplayMode.View** |データ カードとコントロールは編集できず、表示に最適化されています。 |

## <a name="syntax"></a>構文
**SubmitForm**( *FormName* )

* *FormName* - 必須。 データ ソースに送信するフォーム コントロール。

**EditForm**( *FormName* )

* *FormName* - 必須。  **FormMode.Edit** モードに切り替えるフォーム コントロール。

**NewForm**( *FormName* )

* *FormName* - 必須。 **FormMode.New** モードに切り替えるフォーム コントロール。

**ResetForm**( *FormName* )

* *FormName* - 必須。 初期値にリセットするフォーム コントロール。 フォームを **FormMode.New** モードから **FormMode.Edit** モードに切り替えます。

**ViewForm**( *FormName* )

* *FormName* - 必須。  **FormMode.View** モードに切り替えるフォーム コントロール。

## <a name="examples"></a>例
完全な例については、[データ フォームについて](../working-with-forms.md) を参照してください。

1. Button コントロールを追加して、**保存**と表示されるようにその **[Text](../controls/properties-core.md)** プロパティを設定し、その **[OnSelect](../controls/properties-core.md)** プロパティを次の数式に設定します。
   
    **SubmitForm( EditForm )**
2. フォーム コントロールの **[OnFailure](../controls/control-form-detail.md)** プロパティを空白に設定し、その **[OnSuccess](../controls/control-form-detail.md)** プロパティを次の数式に設定します。
   
    **Back()**
3. **[Label](../controls/control-text-box.md)** コントロールに **ErrorText** という名前を付けて、その **[Text](../controls/properties-core.md)** プロパティを次の数式に設定します。
   
    **EditForm.Error**
   
    ユーザーが**保存**ボタンを選択すると、フォーム コントロールのすべての変更が、基になるデータ ソースに送信されます。
   
   * 送信が成功すると、変更が保存、または、フォーム コントロールが**新規**モードの場合、レコードが作成されます。 **ErrorText** は*空白*で、前のスクリーンが再び表示されます。
   * 送信が失敗すると、**ErrorText** ではユーザー フレンドリなエラー メッセージを表示し、ユーザーが問題を修正してやり直せるように現在のスクリーンは表示されたままになります。
4. Button コントロールを追加して、**キャンセル**と表示されるようにその **[Text](../controls/properties-core.md)** プロパティを設定し、その **[OnSelect](../controls/properties-core.md)** プロパティを次の数式に設定します。
   
    **ResetForm( EditForm ); Back()**
   
    ユーザーが**キャンセル**ボタンを選択すると、フォーム コントロールの値はユーザーが編集を開始する前の値にリセットされ、前のスクリーンが再び表示され、および、フォーム コントロールが**新規**モードだった場合は**編集**モードに戻ります。
5. Button コントロールを追加して、**新規**と表示されるようにその **[Text](../controls/properties-core.md)** プロパティを設定し、その **[OnSelect](../controls/properties-core.md)** プロパティを次の数式に設定します。
   
    **NewForm( EditForm ); Navigate( EditScreen, None )**
   
    ユーザーが**新規**ボタンを選択すると、フォーム コントロールは**新規**モードに切り替わり、フォーム コントロールのデータ ソースの既定値がそのコントロールに設定され、フォーム コントロールを含むスクリーンが表示されます。 **SubmitForm** 関数が実行されると、レコードは更新ではなく作成されます。

