---
title: キャンバス アプリ フォームについて | Microsoft Docs
description: Power Apps で、キャンバス アプリにフォームを追加して、データ ソースから情報を収集して表示できるようにします。
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/27/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 6ab9a39a63e14cfd220edc79db37a78bc5bcd924
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3306867"
---
# <a name="understand-canvas-app-forms-in-microsoft-power-apps"></a>Microsoft Power Apps のキャンバス アプリ フォームについて理解する

ユーザーがレコードの参照、そのレコードの詳細の表示、およびレコードの編集または作成ができるように、3 種類のコントロールをキャンバス アプリに追加します。

| 活動​​ | コントロール​​ | 内容 |
| --- | --- | --- |
| **レコードを参照する** |**[Gallery](controls/control-gallery.md)** コントロール |データ ソースのレコードをフィルター処理、並べ替え、検索、スクロールして、特定のレコードを選択します。 小さな画面上でも、各レコードからいくつかのフィールドを表示して、一度に複数のレコードを表示します。 |
| **レコードの詳細を表示する** |**[Display form](controls/control-form-detail.md)** コントロール |単一レコードの場合、そのレコードで複数またはすべてのフィールドが表示されます。 |
| **レコードを編集または作成する** |**[Edit form](controls/control-form-detail.md)** コントロール |単一のレコードの 1 つ以上のフィールドを更新し (または既定値で始まるレコードを作成する)、これらの変更を基になるデータ ソースに保存します。 |

各コントロールを異なる画面に配置して、区別しやすくします:

![3 つの画面でのレコードの参照、表示、編集](./media/working-with-forms/three-screens.png)

このトピックで説明するように、これらのコントロールを数式と組み合わせて、ユーザー エクスペリエンス全体を作成します。

## <a name="prerequisites"></a>前提条件

* Power Apps に[サインアップ](../signup-for-powerapps.md) し、登録に使用した同じ資格情報を使用して[サインイン](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) します。
* Power Apps で[コントロールを構成する](add-configure-controls.md)方法を説明します。

## <a name="explore-a-generated-app"></a>生成されたアプリを使ってみる
Power Apps では、指定するデータ ソースに基づいて自動的にアプリを生成できます。 各アプリには、前述のコントロールおよびそれらを接続する数式を備えた 3 つの画面が含まれます。 これらのアプリを "そのまま" 実行したり、特定の目標に合わせてカスタマイズしたり、またはアプリの機能を調べて、独自のアプリに当てはまる有用な概念を学ぶこともできます。 次のセクションでは、生成されたアプリを起動させる画面、コントロール、数式について調べます。  

### <a name="browse-screen"></a>閲覧画面
![画面コントロールの参照](./media/working-with-forms/afd-browse-screen-basic.png)

この画面には、次の重要な数式が表示されます:

| コントロール​​ | サポートされる動作 | 計算式 |
| --- | --- | --- |
| **BrowseGallery1** |**資産**データ ソースからレコードを表示します。 |ギャラリーの **[Items](controls/properties-core.md)** プロパティは、**資産**データ ソースに基づく数式に設定されます。 |
| **ImageNewItem1** |各フィールドが既定値に設定されている**編集および作成**画面を表示します。それによりユーザーは簡単にレコードを作成できます。 |画像の **[OnSelect](controls/properties-core.md)** プロパティは、次の数式に設定されます:<br> **NewForm( EditForm1 );<br>Navigate( EditScreen1, None )** |
| **NextArrow1** (ギャラリー内) |現在選択されているレコードの多くまたはすべてのフィールドを表示するための**詳細**画面を表示します。 |矢印の **[OnSelect](controls/properties-core.md)** プロパティは、次の数式に設定されます:<br>**Navigate( DetailScreen1, None )** |

この画面の主要コントロールである **BrowseGallery1** は、画面の領域の大半を占めています。 ユーザーは、ギャラリーをスクロールして特定のレコードを見つけ、他のフィールドを表示したり更新したりできます。

データ ソースからのレコードを表示するように、ギャラリーの **[Items](controls/properties-core.md)** プロパティを設定します。 たとえば、このプロパティを**資産**に設定して、その名前のデータ ソースからのレコードを表示します。

> [!NOTE]
> 生成されたアプリでは、ユーザーがレコードの並べ替えや検索ができるように、**[Items](controls/properties-core.md)** が既定でかなり複雑な数式に設定されています。 この数式の構築方法についてはこのトピックの後半で説明しますが、一時的に簡易バージョンで十分です。

表示または編集するレコードを探す代わりに、ユーザーはギャラリーの上部にある "+" 記号を選択してレコードを作成できます。 この効果を作成するには、**[Image](controls/control-image.md)** コントロールを追加し、その中に "+" 記号を表示して、その **[OnSelect](controls/properties-core.md)** プロパティを次の数式に設定します:
<br>**NewForm( EditForm1 ); Navigate( EditScreen1, None )**

この数式により**編集および作成**画面が開き、この画面には **EditForm1** という名前の **[Edit form](controls/control-form-detail.md)** コントロールが表示されます。 また、そのフォームは**新規**モードに切り替わり、ユーザーが最初からレコードを容易に作成できるよう、フォームにはデータ ソースからの既定値が表示されます。

**BrowseGallery1** に表示される任意のコントロールを調べるには、そのギャラリーの最初のセクションでそのコントロールを選択します。これは、他すべてのセクションのテンプレートとして機能します。 たとえば、左端で中央にある **[Label](controls/control-text-box.md)** コントロールを選択します:

![画面コントロールの参照](./media/working-with-forms/afd-browse-gallery-controls.png)

この例では、コントロールの **[Text](controls/properties-core.md)** プロパティが **ThisItem.AssignedTo** に設定されています。これは**資産**データ ソースにあるフィールドです。 ギャラリー内の他の 3 つの **[Label](controls/control-text-box.md)** コントロールの **[Text](controls/properties-core.md)** プロパティは同様の数式に設定され、各コントロールにはデータ ソースの異なるフィールドが表示されます。  

**[Shape](controls/control-shapes-icons.md)** コントロール (矢印) を選択し、その **[OnSelect](controls/properties-core.md)** プロパティが次の数式に設定されていることを確認します:
<br>**Navigate( DetailScreen1, None )**

ユーザーは、**BrowseGallery1** でレコードを見つけると、そのレコードの矢印を選択して、その詳細情報を **DetailScreen1** に表示できます。 矢印を選択することで、ユーザーは **BrowseGallery1** の **Selected** プロパティの値を変更できます。 このアプリでは、そのプロパティによって **DetailScreen1** 内だけでなく、ユーザーがレコードを更新する場合に**編集および作成**画面にも表示されるレコードが決まります。

### <a name="detail-screen"></a>詳細画面
![詳細画面のコントロール](./media/working-with-forms/afd-detail-screen-basic.png)

この画面には、次の重要な数式が表示されます:

| コントロール​​ | サポートされる動作 | 計算式 |
| --- | --- | --- |
| **DetailForm1** |**Assets** データ ソースのレコードを表示します |**[DataSource](controls/control-form-detail.md)** プロパティを**資産**に設定します。 |
| **DetailForm1** |表示するレコードを決定します。 生成されたアプリでは、ユーザーがギャラリーで選択したレコードが表示されます。 |このコントロールの **[Item](controls/control-form-detail.md)** プロパティを次の値に設定します:<br>**BrowseGallery1.Selected** |
| **[Card](controls/control-card.md)** コントロール |**[Display form](controls/control-form-detail.md)** コントロールでは、レコードの単一のフィールドが表示されます。 |**[DataField](controls/control-card.md)** プロパティをフィールドの名前に設定し、二重引用符で囲みます (例: **"名前"**)。 |
| **ImageBackArrow1** |ユーザーがこのコントロールを選択するとき、**BrowseScreen1** が開きます。 |**[OnSelect](controls/properties-core.md)** プロパティを次の数式に設定します:<br>**Back()** |
| **ImageDelete1** |ユーザーがこのコントロールを選択するとき、レコードが削除されます。 |**[OnSelect](controls/properties-core.md)** プロパティを次の数式に設定します:<br>**Remove( Assets, BrowseGallery1.Selected )** |
| **ImageEdit1** |ユーザーがこのコントロールを選択するときに、**編集および作成**画面が開いて現在のレコードが表示されます。 |**[OnSelect](controls/properties-core.md)** プロパティを次の数式に設定します:<br>**Navigate( EditScreen1, None )** |

画面の上部には、3 つの画像が **DetailForm1** の外部に配置され、アプリの 3 つの画面間の調整を行うボタンとして機能します。

この画面の大部分を占める **DetailForm1** には、ユーザーがギャラリーで選択したレコードが表示されます (フォームの **[Item](controls/control-form-detail.md)** プロパティが **BrowseGallery1.Selected** に設定されているため)。 フォームの **[DataSource](controls/control-form-detail.md)** プロパティでは、各フィールドのわかりやすい表示名などのデータ ソースに関するメタデータも提供します。

**DetailForm1** には、複数の **[Card](controls/control-card.md)** コントロールが含まれます。 **[Card](controls/control-card.md)** コントロール自体、またはそれに含まれるコントロールを選択して、追加の情報を検出できます。

![オーサリング エクスペリエンスで選択された詳細カードとカード コントロール](./media/working-with-forms/afd-detail-card-controls.png)

**[Card](controls/control-card.md)** コントロールの **[DataField](controls/control-card.md)** プロパティにより、カードに表示されるフィールドが決まります。 この場合、そのプロパティは **AssetID** に設定されます。 カードには、**[Text](controls/properties-core.md)** プロパティが **Parent.Default** に設定されている **[Label](controls/control-text-box.md)** コントロールが含まれます。 このコントロールには、**[DataField](controls/control-card.md)** プロパティを介して設定される、カードの**既定**値が表示されます。

生成されたアプリでは、**[Card](controls/control-card.md)** コントロールが既定でロックされています。 カードがロックされていると、**[DataField](controls/control-card.md)** などの一部のプロパティを変更できず、これらのプロパティの数式バーを使用できません。 この制限は、生成されたアプリの基本機能がカスタマイズによって損なわれないようにするのに役立ちます。 ただし、カードとそのコントロールの一部のプロパティは、右側のウィンドウで変更できます:

![オプション ウィンドウが開いている詳細画面](./media/working-with-forms/detail-screen-new.png)

右側のウィンドウで、表示するフィールドおよび各フィールドに表示するコントロールの種類を選択できます。

### <a name="editcreate-screen"></a>編集/作成の画面
![コントロールの編集画面](./media/working-with-forms/afd-edit-screen-basic.png)

この画面には、次の重要な数式が表示されます:

| コントロール​​ | サポートされる動作 | 計算式 |
| --- | --- | --- |
| **EditForm1** |**資産**データ ソースでレコードを表示します。 |**[DataSource](controls/control-form-detail.md)** プロパティを**資産**に設定します。 |
| **EditForm1** |表示するレコードを決定します。 生成されたアプリでは、ユーザーが **BrowseScreen1** で選択したレコードが表示されます。 |**[Item](controls/control-form-detail.md)** プロパティを次の値に設定します:<br>**BrowseGallery1.Selected** |
| **[Card](controls/control-card.md)** コントロール |**[Edit form](controls/control-form-detail.md)** コントロールで、ユーザーがレコードの 1 つ以上のフィールドを編集できるようにコントロールを提供します。 |**[DataField](controls/control-card.md)** プロパティをフィールドの名前に設定し、二重引用符で囲みます (例: **"名前"**)。 |
| **ImageCancel1** |ユーザーがこのコントロールを選択するとき、進行中の任意の変更が破棄され、**詳細**画面が開きます。 |**[OnSelect](controls/properties-core.md)** プロパティを次の数式に設定します:<br>**ResetForm( EditForm1 ); Back()** |
| **ImageAccept1** |ユーザーがこのコントロールを選択すると、データ ソースへの変更が送信されます。 |**[OnSelect](controls/properties-core.md)** プロパティを次の数式に設定します:<br>**SubmitForm( EditForm1 )** |
| **EditForm1** |変更が承認されると、前の画面に戻ります。 |**[OnSuccess](controls/control-form-detail.md)** プロパティを次の数式に設定します:<br>**Back()** |
| **EditForm1** |変更が承認されない場合は、ユーザーが問題を修正して再送信を試みることができるように、現在の画面にとどまります。 |**[OnFailure](controls/control-form-detail.md)** プロパティを空のままにします。 |
| **LblFormError1** |変更が承認されない場合、エラー メッセージが表示されます。 |**[Text](controls/properties-core.md)** プロパティを次の値に設定します:<br>**EditForm1.Error** |

**詳細**画面と同様に、**編集および作成**画面の大部分は **EditForm1** という名前のフォーム コントロールで占められています。 さらに、**EditForm1** の **[Item](controls/control-form-detail.md)** プロパティが **BrowseGallery1.Selected** に設定されており、フォームにはユーザーが **BrowseScreen1** で選択したレコードが表示されます。 **詳細**画面では、各フィールドが読み取り専用として表示されますが、ユーザーは **EditForm1** のコントロールを使用して 1 つ以上のフィールドの値を更新できます。 また、**[DataSource](controls/control-form-detail.md)** プロパティを使用して、各フィールドのわかりやすい表示名や変更の保存場所など、このデータ ソースに関するメタデータにアクセスします。

ユーザーが "X" アイコンを選択して更新を取り消すと、**[ResetForm](functions/function-form.md)** 関数によって任意の未保存の変更が破棄され、**[Back](functions/function-navigate.md)** 関数によって**詳細**画面が開きます。 ユーザーが **BrowseScreen1** で別のレコードを選択するまで、**詳細**画面と**編集および作成**画面の両方に同じレコードが表示されます。 そのレコードのフィールドは、ユーザーが変更してから破棄した値ではなく、直前に保存された値に設定されたままになります。

ユーザーがフォームで 1 つ以上の値を変更してから "チェックマーク" アイコンを選択すると、**[SubmitForm](functions/function-form.md)** 関数によってユーザーの変更がデータ ソースに送信されます。

* 変更が正常に保存されると、フォームの **[OnSuccess](controls/control-form-detail.md)** 数式が実行され、**Back()** 関数によって詳細画面が開き、更新されたレコードが表示されます。
* 変更が正常に保存されなかった場合、フォームの **[OnFailure](controls/control-form-detail.md)** 数式が実行されますが、*空白*であるため、何も変更されません。 **編集および作成**画面は開いたままになるため、ユーザーは変更を取り消すまたはエラーを修正できます。 **LblFormError1** では、フォームの **Error** プロパティが設定されている、わかりやすいエラー メッセージが表示されます。

**[Display form](controls/control-form-detail.md)** コントロールと同様、**[Edit form](controls/control-form-detail.md)** コントロールには **[Card](controls/control-card.md)** コントロールが含まれており、これにはレコードの異なるフィールドを表示する他のコントロールが含まれます:

![オーサリング エクスペリエンスで選択された編集カードとカード コントロール](./media/working-with-forms/afd-edit-card-controls.png)

前の画像で、選択されるカードには **AssetID** フィールドが表示され、ユーザーがそのフィールドの値を編集できるよう **[Text input](controls/control-text-input.md)** コントロールが含まれます。 (対照的に、詳細画面には **[Label](controls/control-text-box.md)** コントロールの同じフィールドが表示され、これは読み取り専用です。) **[Text input](controls/control-text-input.md)** コントロールには **[Default](controls/properties-core.md)** プロパティがあり、**Parent.Default** に設定されています。 ユーザーがレコードを編集する代わりに作成していた場合、そのコントロールには、ユーザーが新しいレコードに対して変更できる初期値が表示されます。

右側のウィンドウでは、各カードを表示または非表示にしたり、カードを配置変更したり、さまざまな種類のコントロールにフィールドを表示するように構成することもできます。

![オプション ウィンドウが開いている編集画面](./media/working-with-forms/edit-screen.png)

## <a name="build-an-app-from-scratch"></a>アプリをゼロから作成
Power Apps がアプリを生成する方法を理解すると、このトピックの前半で説明したのと同じ構成要素と数式を使用するアプリを自分で作成できます。

## <a name="identify-test-data"></a>テスト データを識別する
このトピックを最大限に活用するために、実験できるデータ ソースから始めます。 このデータ ソースには、心配せず読み取りおよび更新できるテスト データが含まれる必要があります。

> [!NOTE]
> データソースとしてスペースを含む列名を含む SharePoint リストまたは Excel テーブルを使用する場合、Power Apps はスペースを **"\_x0020\_"** に置き換えます。 たとえば、SharePoint の **"列名"** または Excel は、データレイアウトまたは数式で表示すると、Power Apps では **"Column_x0020_Name"** として表示されます。

このトピックの残りの部分に正確に従うには、次のデータを含む "アイスクリーム" という名前の SharePoint リストを作成します。

![アイスクリーム SharePoint リスト](./media/working-with-forms/sharepointlist-icecream.png)

* 電話用に、アプリを最初から作成し、[それをデータ ソースに接続](add-data-connection.md)します。
  
    > [!NOTE]
  > タブレット アプリは非常に似ていますが、余分な画面スペースを最大限に活用するために、別の[画面レイアウト](#screen-design)が必要になる場合があります。
  
    トピックの残りの部分の例は、**アイスクリーム**という名前のデータ ソースに基づいています。

## <a name="browse-records"></a>レコードを参照する
ブラウザー画面のギャラリーで見つけることで、レコードから情報をすばやく取得します。

1. **縦**ギャラリーを追加して、レイアウトを**タイトル**のみに変更します。
   
    ![アイスクリーム データ ソースに接続されているギャラリー](./media/working-with-forms/new-gallery.png)
2. ギャラリーの **[Items](controls/properties-core.md)** プロパティを**アイスクリーム**に設定します。
3. ギャラリーの最初のラベルの **[Text](controls/properties-core.md)** プロパティを、他のものに設定されている場合は **ThisItem.Title** に設定します。
   
    これで、ラベルに各レコードの**タイトル** フィールドの値が表示されます。
   
    ![アイスクリーム データ ソースに接続されているギャラリー](./media/working-with-forms/new-gallery-2.png)
4. ギャラリーのサイズを画面いっぱいになるように変更し、**[TemplateSize](controls/control-gallery.md)** プロパティを **60** に設定します。
   
    画面は次の例のようになり、データ ソースのすべてのレコードが表示されます:
   
    ![アイスクリーム データ ソースに接続されているギャラリー](./media/working-with-forms/new-gallery-icecream.png)

## <a name="view-details"></a>詳細を表示します
ギャラリーに必要な情報が表示されない場合は、レコードの矢印を選択して詳細画面を開きます。 この画面の **[Display form](controls/control-form-detail.md)** コントロールには、選択したレコードのフィールドの多く(場合によってはすべて) が表示されます。

**[Display form](controls/control-form-detail.md)** コントロールでは、次の 2 つのプロパティを使用してレコードを表示します:

* **[DataSource](controls/control-form-detail.md)** プロパティ。  レコードを保持するデータ ソースの名前。 このプロパティにより右側のパネルにフィールドが入力され、各フィールドの表示名とデータ型 (文字列、数値、日付など) が決まります。  
* **[Item](controls/control-form-detail.md)** プロパティ。  表示するレコード。  このプロパティは多くの場合、**[Gallery](controls/control-gallery.md)** コントロールの **Selected** プロパティに関連付けられています。そのためユーザーは、**[Gallery](controls/control-gallery.md)** コントロールでレコードを選択した後、そのレコードの詳細を確認できます。

**[DataSource](controls/control-form-detail.md)** プロパティを設定すると、右側のウィンドウでフィールドを追加および削除したり、フィールドの表示方法を変更したりできます。

この画面では、ユーザーは意図的または誤ってレコードの値を変更することはできません。 **[Display form](controls/control-form-detail.md)** コントロールは読み取り専用であるため、レコードが変更されることはありません。

**[Display form](controls/control-form-detail.md)** コントロールを追加するには:

1. 画面を追加してから、**[Display form](controls/control-form-detail.md)** コントロールを追加します
2. フォーム コントロールの **[DataSource](controls/control-form-detail.md)** プロパティを **'アイスクリーム'** に設定します。

右側のウィンドウで、画面に表示するフィールドおよび各フィールドに表示するカードの種類を選択できます。 右側のウィンドウで変更を加えると、各 **[Card](controls/control-card.md)** コントロールの **[DataField](controls/control-card.md)** プロパティはユーザーが操作するフィールドに設定されます。 画面は次の例のようになります:

![アイスクリーム データ ソースの表示フォーム](./media/working-with-forms/ice-cream-new.png)

最後に、特定のレコードの詳細が表示されるように、**[Display form](controls/control-form-detail.md)** コントロールを **[Gallery](controls/control-gallery.md)** コントロールに接続する必要があります。  **[Item](controls/control-form-detail.md)** プロパティの設定が完了すると、すぐにギャラリーからの最初のレコードがフォームに表示されます。

* **[Display form](controls/control-form-detail.md)** コントロールの **[Item](controls/control-form-detail.md)** プロパティを **Gallery1.Selected** に設定します。
   
    選択した項目の詳細がフォームに表示されます。
   
    ![ギャラリー コントロールに接続された、アイスクリーム データ ソースの表示フォーム](./media/working-with-forms/view-form-select-coconut.png)

完成です !  次は、ナビゲーションに進みましょう: これは、ユーザーがギャラリー画面から詳細画面を開き、詳細画面からギャラリー画面を開く方法です。

* 画面に **[Button](controls/control-button.md)** コントロールを追加し、**[Back](functions/function-navigate.md)** と表示するよう **[Text](controls/properties-core.md)** プロパティを設定し、**[OnSelect](controls/properties-core.md)** プロパティを **Back()** に設定します。
   
    この数式により、ユーザーが詳細の表示を終了するとギャラリーに戻ります。

    ![戻るボタンで Ice Cream データ ソースのフォームを表示する](./media/working-with-forms/viewform-icecream-back.png)

ここで、**[Gallery](controls/control-gallery.md)** コントロールに戻り、詳細画面にいくつかのナビゲーションを追加します。

1. **[Gallery](controls/control-gallery.md)** コントロールをホストしている最初の画面に切り替え、ギャラリーの最初の項目の矢印を選択します。

2. 図形の **[OnSelect](controls/properties-core.md)** プロパティを次の数式に設定します:
   <br>**Navigate( Screen2, None )**
   
    ![戻るボタンで Ice Cream データ ソースのフォームを表示する](./media/working-with-forms/gallery-icecream-nav-new.png)

3. F5 キーを押してから、ギャラリーの矢印を選択して項目の詳細を表示します。

4. **[戻る](functions/function-navigate.md)** ボタンを選択して製品のギャラリーに戻ってから、Esc キーを押します。

## <a name="editing-details"></a>詳細を編集する
最後のコア アクティビティは、ユーザーが **[Edit form](controls/control-form-detail.md)** コントロールで完成する、レコードの内容を変更することです。

**[Edit form](controls/control-form-detail.md)** コントロールでは、次の 2 つのプロパティを使用してレコードを表示および編集します:

* **[DataSource](controls/control-form-detail.md)** プロパティ。  レコードを保持するデータ ソースの名前。  **[Display form](controls/control-form-detail.md)** コントロールと同様、このプロパティにより右側のパネルにフィールドが入力され、各フィールドの表示名とデータ型 (文字列、数値、日付など) が決まります。 またこのプロパティは、基になるデータ ソースに送信する前に各フィールドの値が有効かどうかも決定します。
* **[Item](controls/control-form-detail.md)** プロパティ。  編集するレコードで、これは多くの場合 **[Gallery](controls/control-gallery.md)** コントロールの **Selected** プロパティに関連付けられています。 それにより、**[Gallery](controls/control-gallery.md)** コントロールでレコードを選択して、詳細画面で表示し、**編集および作成**画面で編集することができます。

**[Edit form](controls/control-form-detail.md)** コントロールを追加するには:

1. 画面を追加し、**[Edit form](controls/control-form-detail.md)** コントロールを追加してから、フォームの **[DataSource](controls/control-form-detail.md)** プロパティを **'アイスクリーム'** に設定します。
2. **[Item](controls/control-form-detail.md)** プロパティを **Gallery1.Selected** に設定します。

これで、画面に表示するフィールドを選択できるようになりました。 各フィールドに表示するカードの種類を選択することもできます。 右側のウィンドウで変更を加えると、各 **[Card](controls/control-card.md)** コントロールの **[DataField](controls/control-card.md)** プロパティがユーザーの操作するフィールドに設定されます。  画面は次の例のようになります:

![アイスクリーム データ ソースの表示フォーム](./media/working-with-forms/icecream-edit.png)

これらの 2 つのプロパティは、**[Display form](controls/control-form-detail.md)** コントロールのプロパティと同じです。  これらだけで、レコードの詳細を表示できます。  

**[Edit form](controls/control-form-detail.md)** コントロールは、**[SubmitForm](functions/function-form.md)** 関数を提供することによりデータ ソースへの変更を記述できるようになります。 この機能をボタンまたは画像コントロールと共に使用して、ユーザーの変更を保存します。

* **[Button](controls/control-button.md)** コントロールを追加して、**保存**と表示されるようにその **[Text](controls/properties-core.md)** プロパティを設定し、**[OnSelect](controls/properties-core.md)** プロパティを次の数式に設定します:<br>
  **SubmitForm( Form1 )**

![Ice Cream データ ソースの編集フォーム](./media/working-with-forms/edit-icecream-save.png)

この画面との間でナビゲーションを追加するには:

1. 別の **[Button](controls/control-button.md)** コントロールを追加して、**キャンセル**と表示されるように **[Text](controls/properties-core.md)** プロパティを設定し、**[OnSelect](controls/properties-core.md)** プロパティを次の数式に設定します: <br>**ResetForm( Form1 ); Back()**
   
    この数式は未保存の編集をすべて破棄し、前の画面を開きます。
   
    ![アイスクリーム データ ソースの表示フォーム](./media/working-with-forms/edit-icecream-cancel.png)
2. フォームの **[OnSuccess](controls/control-form-detail.md)** プロパティを **Back()** に設定します。
   
    更新が正常に保存されると、前の画面 (この場合は、詳細画面) が自動的に開きます。
   
    !["OnSuccess" ルールが追加された編集フォーム](./media/working-with-forms/edit-icecream-onsuccess.png)
3. **表示**画面でボタンを追加し、**編集**と表示されるように **[Text](controls/properties-core.md)** プロパティを設定し、**[OnSelect](controls/properties-core.md)** プロパティを次の数式に設定します:<br> **Navigate( Screen3, None )**
   
    ![編集ボタンが追加された表示フォーム](./media/working-with-forms/viewform-icecream-edit.png)

これで、データを表示および入力するための 3 つの画面を備えた基本的なアプリを構築できました。  アプリを試してみるには、ギャラリー画面を表示してから、F5 キーを押します (または、画面の左上隅にある右向き矢印の "プレビュー" ボタンを選択します)。 ピンク色の円は、各ステップでユーザーがクリックまたはタップする画面上の場所を示します。

![Ice Cream アプリを試用する](./media/working-with-forms/try-icecream.png)

## <a name="create-a-record"></a>レコードを作成する
ユーザーは同じ**編集**フォームを操作して、レコードの更新と作成の両方を実行します。 ユーザーがレコードを作成すると、**[NewForm](functions/function-form.md)** 関数によりフォームが**新規**モードに切り替わります。

フォームが**新規**モードの場合、各フィールドの値はデータ ソースの既定値に設定されます。 フォームの **[Item](controls/control-form-detail.md)** プロパティに指定されたレコードは無視されます。  

ユーザーが新しいレコードを保存する準備ができたら、**[SubmitForm](functions/function-form.md)** が実行されます。 フォームが正常に送信された後、フォームは **EditMode** に戻ります。  

最初の画面で、**新規**ボタンを追加します:

1. ギャラリーを含む画面で、**[Button](controls/control-button.md)** コントロールを追加します。
2. ボタンの **[Text](controls/properties-core.md)** プロパティを**新規**に設定し、**[OnSelect](controls/properties-core.md)** プロパティを次の数式に設定します:<br>
   **NewForm( Form1 ); Navigate( Screen3, None )**
   
    この数式により **Screen3** の**[Edit form](controls/control-form-detail.md)** コントロールが**新規**モードに切り替わり、ユーザーが入力できる画面が開きます。

![編集ボタンが追加された表示フォーム](./media/working-with-forms/gallery-icecream-new.png)

編集および作成画面が開くと、フォームは空で、ユーザーが項目を追加できるようになります。 ユーザーが**保存**ボタンを選択すると、**[SubmitForm](functions/function-form.md)** 関数により、レコードが更新されるのではなく作成されるようになります。 ユーザーが**キャンセル** ボタンを選択する場合、**[ResetForm](functions/function-form.md)** 関数によりフォームが**編集**モードに切り替わり、**[Back](functions/function-navigate.md)** 関数によりギャラリーを参照するための画面が開きます。

## <a name="delete-a-record"></a>レコードを削除する
1. **表示**画面で、ボタンを追加して、**削除**と表示されるように **[Text](controls/properties-core.md)** プロパティを設定します。
2. ボタンの **[OnSelect](controls/properties-core.md)** プロパティを次の数式に設定します:
   <br>**Remove( 'Ice Cream', Gallery1.Selected ); Back()**
   
    ![編集ボタンが追加された表示フォーム](./media/working-with-forms/viewform-icecream-remove.png)

## <a name="handling-errors"></a>エラーを処理する
このアプリでは、フィールドの値が無効な場合、必須フィールドが空の場合、ネットワークから切断された場合など、その他任意の問題が発生した場合にエラーが発生します。  

何らかの理由で **[SubmitForm](functions/function-form.md)** が失敗すると、**[Edit form](controls/control-form-detail.md)** コントロールの **Error** プロパティにはユーザーに表示されるエラー メッセージが含まれます。 この情報により、ユーザーは問題を修正して変更を再送信したり、または更新を取り消すこともできるようになります。

1. 編集および作成画面で、**[Label](controls/control-text-box.md)** コントロールを追加し、それを**保存**ボタンのすぐ下に移動します。 ユーザーがこのコントロールを選択して変更を保存した後、エラーが確認しやすくなります。

2. **[Label](controls/control-text-box.md)** コントロールの **[Text](controls/properties-core.md)** プロパティを **Form1.Error** が表示されるように設定します。

    ![編集ボタンが追加された表示フォーム](./media/working-with-forms/edit-icecream-error.png)

Power Apps がデータから生成したアプリでは、このコントロールの **[AutoHeight](controls/control-text-box.md)** プロパティが *true* に設定されているため、エラーが発生しないと領域が使用されません。 **[Edit form](controls/control-form-detail.md)** コントロールの **[Height](controls/properties-size-location.md)** プロパティおよび **[Y](controls/properties-size-location.md)** プロパティも動的に調整され、エラーが発生するときに拡大するこのコントロールを構成します。 詳細については、既存のデータからアプリを生成し、これらのプロパティを調べてください。 エラーに対するテキスト ボックス コントロールは、エラーが発生していないときは非常に短くなっています。このコントロールを選択するには、(**表示**タブにある) **詳細**ビューを開く必要があります。

![エラー テキスト コントロールが選択されたデータ編集フォームからのアプリ](./media/working-with-forms/edit-assets-error1.png)

![フォーム コントロールが選択されたデータ編集フォームからのアプリ](./media/working-with-forms/edit-assets-error2.png)

## <a name="refresh-data"></a>データの更新
データ ソースはユーザーがアプリを開くたびに更新されますが、ユーザーはアプリを閉じなくてもギャラリーのレコードを更新したい場合があります。 **更新**ボタンを追加し、ユーザーがそのボタンを選択して手動でデータを更新できるようにします:

1. **[Gallery](controls/control-gallery.md)** コントロールを備えた画面で、**[Button](controls/control-button.md)** コントロールを追加し、**更新**と表示されるように **[Text](controls/properties-core.md)** プロパティを設定します。

2. このコントロールの **[OnSelect](controls/properties-core.md)** プロパティを次の数式に設定します:<br> **Refresh( 'Ice Cream' )**

    ![データ ソースの更新](./media/working-with-forms/browse-icecream-refresh.png)

## <a name="search-and-sort-the-gallery"></a>ギャラリーの検索と並べ替え
Power Apps がデータから生成したアプリでは、参照画面の上部にある 2 つのコントロールを無視してきました。 これらのコントロールを使用することにより、 ユーザーは 1 つ以上のレコードの検索、レコードの一覧を昇順または降順に、またはその両方の並べ替えを実行できます。

![参照画面でのコントロールの並べ替えと検索](./media/working-with-forms/afd-browse-search-sort.png)

ユーザーが並べ替えボタンを選択すると、ギャラリーの並べ替え順序が逆になります。 この動作を作成するには、*コンテキスト変数*を使用して、ギャラリーの並べ替え方向を追跡します。 ユーザーがボタンを選択すると、変数が更新され、方向が逆になります。 並べ替えボタンの **[OnSelect](controls/properties-core.md)** プロパティは次の数式に設定されます: **UpdateContext( {SortDescending1: !SortDescending1} )**

**[UpdateContext](functions/function-updatecontext.md)** 関数は、**SortDescending1** コンテキスト変数がまだ存在しない場合は、それを作成します。 この関数は、変数の値を読み取り、**!** 演算子を使用してその反対の論理値に設定します。 値が *true* の場合は *false* になります。 値が *false* の場合は *true* になります。

**[Gallery](controls/control-gallery.md)** コントロールの **[Items](controls/properties-core.md)** プロパティの数式では、このコンテキスト変数を **TextSearchBox1** コントロールのテキストと共に使用します:

```powerapps-dot
Sort( 
    If( IsBlank(TextSearchBox1.Text),
        Assets,
        Filter( Assets, TextSearchBox1.Text in Text(ApproverEmail) ) 
    ),
    ApproverEmail,
    If(SortDescending1, Descending, Ascending) 
)
```

これを詳しく見ていきましょう:

* 外側には **[Sort](functions/function-sort.md)** 関数があり、3 つの引数を取ります: テーブル、並べ替えの基準となるフィールド、並べ替える方向。  
  
  * 並べ替え方向は、ユーザーが **ImageSortUpDown1** コントロールを選択するときに切り替わるコンテキスト変数から取得されます。 *true*/*false* 値は、定数の**降順**および**昇順**に変換されます。
  * 並べ替えるフィールドは、**ApproverEmail** に固定されています。 ギャラリーに表示するフィールドを変更する場合は、この引数も変更する必要があります。
* 内側には **[Filter](functions/function-filter-lookup.md)** 関数があり、テーブルを引数として、レコードごとに評価する式を取ります。
  
  * テーブルは未加工の**資産**データ ソースで、これがフィルター処理または並べ替えの前の出発点となります。
  * この式では、**ApproverEmail** フィールド内の **TextSearchBox1** の文字列のインスタンスを検索します。  この場合も、ギャラリーに表示されるフィールドを変更する場合は、この引数も更新する必要があります。
  * **TextSearchBox1** が空で、ユーザーがすべてのレコードを表示する場合、**[Filter](functions/function-filter-lookup.md)** 関数がバイパスされます。

これは単なる一例ですが、**[Filter](functions/function-filter-lookup.md)**、**[Sort](functions/function-sort.md)** などの関数や演算子を組み合わせることで、アプリのニーズに応じて **[Items](controls/properties-core.md)** プロパティの独自の数式を作成できます。    

## <a name="screen-design"></a>画面のデザイン
ここまでで、画面全体にコントロールを分散する他の方法については説明してきませんでした。 それには多くの選択肢があり、最適な選択肢はアプリの特定のニーズによって決まるためです。

電話画面の領域が限られているため、参照、表示、編集/作成の各操作を別々の画面で行う必要があります。 このトピックでは、**[Navigate](functions/function-navigate.md)** 関数と **[Back](functions/function-navigate.md)** 関数を使用して各画面を開きます。  

タブレットでは、参照、表示、編集/作成の各操作を 2 つの画面、または場合によっては 1 つの画面で実行できます。 後者の場合、**[Navigate](functions/function-navigate.md)** 関数も **[Back](functions/function-navigate.md)** 関数も必要ありません。

ユーザーが同じ画面で操作している場合、ユーザーが**[Gallery](controls/control-gallery.md)** での選択肢を変更できず、**[Edit form](controls/control-form-detail.md)** コントロールでの編集内容を失う可能性があることに注意する必要があります。  別のレコードへの変更がまだ保存されていないときにユーザーが別のレコードを選択できないようにするには、ギャラリーの **[Disabled](controls/properties-core.md)** プロパティを次の数式に設定します:<br>
**EditForm.Unsaved**

