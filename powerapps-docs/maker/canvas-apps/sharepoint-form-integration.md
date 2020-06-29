---
title: SharePoint フォームの統合を理解する | Microsoft Docs
description: カスタム フォームがどのように SharePoint と連携するのか理解する
author: NickWaggoner
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/11/2017
ms.author: niwaggon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9befcf4cb0e7267820c62ab78a14ee28ba985490
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3307097"
---
# <a name="understand-sharepoint-forms-integration"></a>SharePoint フォームの統合について
Power Apps にて、簡単に[あらゆる SharePoint リスト フォームをカスタマイズ](customize-list-form.md) 可能です。 この記事では、これらのフォームの動作と、フォームをさらにカスタマイズする方法を詳しく見てみましょう。

SharePoint リスト フォームをカスタマイズしたことがある場合、既定の生成されたフォームが、項目の作成、表示、編集などのすべての操作に対応していることをご存知でしょう。 これは、生成された数式と **SharePointIntegration** コントロールによって実現されています。

## <a name="understand-the-default-generated-form"></a>既定の生成されたフォームを理解する

既定の生成されたフォームは、次のコントロールと対応する既定値で構成されています:

* **FormScreen1** - これは、フォームを含む[スクリーン](controls/control-screen.md) です。

* **SharePointForm1** - これは、リスト アイテムの作成、表示、または編集に使用される[フォーム](working-with-forms.md) です。

    * **データ ソース** - フォームがカスタマイズされているリストです。

    * **項目** - リストから選択された項目です。 これは、Power Apps Studio で操作するとき便利なように、リストの First() 項目に設定されています。

        **If(IsBlank(SharePointIntegration.Selected) || IsEmpty(SharePointIntegration.Selected),First('*YourListName*'),SharePointIntegration.Selected)**

    * **OnSuccess** - 項目が正常に作成または保存されると、フォームがリセットされ、SharePoint でこのフォームが非表示になります。

        **ResetForm(SharePointForm1); RequestHide()**

* **SharePointIntegration** - このコントロールは、SharePoint と Power Apps の間でユーザー アクションを伝達します。

    * **データ ソース** - フォームがカスタマイズされているリストです。

        **'*YourListName*'**

    * **OnNew** - **SharePointForm1** を新しいモードに設定します。

        **NewForm(SharePointForm1)**

    * **OnView** - **SharePointForm1** を表示モードに設定します。

        **ViewForm(SharePointForm1)**

    * **OnEdit** - **SharePointForm1** を編集モードに設定します。

        **EditForm(SharePointForm1)**

    * **OnSave** - **SharePointForm1** の変更を送信します。 フォームの送信が成功すると、**SharePointForm1.OnSuccess** 式が実行されます。

        **SubmitForm(SharePointForm1)**

    * **OnCancel** - **SharePointForm1** の変更をリセットします。 ユーザーが SharePoint で**キャンセル**をクリックまたはタップすると、SharePoint では常にフォームが非表示になります。

        **ResetForm(SharePointForm1)**

これらの既定値によって、SharePoint 内で実行したときにフォームが機能し、ユーザーが SharePoint でフォームと対話したときに Power Apps フォーム モードが変更され、変更内容が SharePoint に確実に送信されます。

## <a name="understand-the-sharepointintegration-control"></a>SharePointIntegration コントロールを理解する
**SharePointIntegration** コントロールは、SharePoint と Power Apps の間でユーザー アクションを伝達します。

![](./media/sharepoint-form-integration/sharepointintegration-object.png)

>[!NOTE]
>**SharePointIntegration** コントロールのプロパティには、フォームが SharePoint で実行されているときにのみアクセスでき、Power Apps Studio でフォームをカスタマイズしているときにはアクセスできません。 これらのプロパティは、**OnStart** または **OnVisible** では使用できないことがあります。 

**SharePointIntegration** コントロールには、次のプロパティがあります:

**選択済み** - SharePoint リストから選択された項目です。

**OnNew** - ユーザーが**新規**ボタンをクリックかタップ、または SharePoint の**項目作成**フォームを開いたときのアプリの応答です。

**OnView** - ユーザーが、**項目**をクリックかタップ、または SharePoint の**項目詳細**フォームを開いたときのアプリの応答です。

**OnEdit** - ユーザーが**すべてを編集**ボタンをクリックかタップ、または SharePoint の**項目の編集**フォームを開いたときのアプリの応答です。

**OnSave** - ユーザーが SharePoint の**保存**ボタンをクリックまたはタップしたときのアプリの応答です。

**OnCancel** - ユーザーが SharePoint の**キャンセル**ボタンをクリックまたはタップしたときのアプリの応答です。

**SelectedListItemID** - SharePoint リストで選択された項目 ID です。

**データ ソース** – フォームが表示、編集、または作成するレコードが含まれるリストです。 このプロパティを変更すると、**Selected** プロパティと **SelectedItemID** プロパティが無効になる可能性があることに注意してください。

## <a name="customize-the-default-form"></a>既定のフォームをカスタマイズする
既定の生成されたフォームと **SharePointIntegration** コントロールを理解したら、数式を変更して、フォームをさらにカスタマイズすることができます。 フォームをカスタマイズするときの注意事項をいくつか次に示します:

* 項目を作成、表示、または編集するための個別のカスタム エクスペリエンスを作成するには、**SharePointIntegration** コントロールの **OnNew**、**OnView**、または **OnEdit** 式を、変数を設定するか別の画面に移動するように設定します。

* ユーザーが SharePoint で **保存** をクリックまたはタップしたときの動作をカスタマイズするには、**SharePointIntegration** コントロールの **OnSave** 式を使用します。 複数のフォームがある場合は、現在使用しているフォームに対する変更だけを送信してください。

  > [!TIP]
  >    **OnNew**、**OnView**、および **OnEdit** 式の変数には異なる値を設定します。 **OnSave** 式でこの変数を使用すると、使用されているフォームを指定できます。

* すべてのフォームの **OnSuccess** 式に必ず **RequestHide()** を含めてください。 これを忘れると、SharePoint はフォームを非表示にするタイミングを認識できません。

* ユーザーが SharePoint で **キャンセル**をクリックまたはタップしたさいのフォームの非表示は制御できないので、**SharePointIntegration** コントロールの **OnCancel** 式でかならずフォームをリセットしてください。

* **SharePointIntegration** コントロールのプロパティは **OnStart** または **OnVisible** では使用できないことがあり、それらのイベントはリストの読み込み中に 1 回だけ実行します。 **OnNew**、**OnView**、または **OnEdit** 式を使って、フォームが毎回ユーザーに表示される前にロジックを実行できます。 
