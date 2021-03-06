---
title: キャンバスアプリのコンポーネントを作成する |Microsoft Docs
description: キャンバスアプリの再利用可能なコンポーネントの概要
author: yifwang
ms.service: powerapps
ms.topic: article
ms.date: 02/20/2020
ms.author: yifwang
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b86f6c94a7a267fc28a70216c6b89d154cd7b865
ms.sourcegitcommit: efb05dbd29c4e4fb31ade1fae340260aeba2e02b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78293226"
---
# <a name="create-a-component-for-canvas-apps"></a>キャンバスアプリ用のコンポーネントを作成する

> [!IMPORTANT]
> この機能は依然としてパブリックプレビューの段階にあります。 詳細については、[試験的な機能とプレビュー機能](working-with-experimental.md)に関する記事を参照してください。

コンポーネントは、キャンバスアプリの再利用可能な構成要素です。これにより、アプリの開発者は、アプリ内または[コンポーネントライブラリ](component-library.md)を使用してアプリ内で使用するカスタムコントロールを作成できます。 コンポーネントでは、カスタムプロパティなどの高度な機能を使用して、複雑な機能を有効にすることができます。 この記事では、コンポーネントの概念といくつかの例について説明します。

コンポーネントは、類似したコントロールパターンを持つ大規模なアプリを構築する場合に役立ちます。 アプリ内のコンポーネント定義を更新すると、アプリ内のすべてのインスタンスに変更が反映されます。 また、コンポーネントを使って、コントロールをコピー/貼り付けしてパフォーマンスを向上させる必要がなくなるため、作業の重複が軽減されます。 コンポーネントは、[コンポーネントライブラリ](component-library.md)を使用するときに、コラボレーション開発を作成し、組織内でルックアンドフィールを標準化するのにも役立ちます。

## <a name="components-in-canvas-app"></a>キャンバスアプリ内のコンポーネント

この記事で説明されているように、または[コンポーネントライブラリ](component-library.md)内に新しいコンポーネントを作成することによって、アプリ内からコンポーネントを作成できます。 コンポーネントライブラリは、複数のアプリ画面でコンポーネントを使用するための要件に使用する必要があります。 既存のコンポーネントを既存のコンポーネントまたは新しいコンポーネントライブラリにコピーすることもできます。

アプリ内にコンポーネントを作成するには、 **[ツリービュー]** 、 **[コンポーネント]** タブの順に選択し、 **[新しいコンポーネント]** を選択します。

![ツリービューを使用した新しいカスタムコンポーネントの作成](./media/create-component/insert-new-component-treeview.png)

**[新しいコンポーネント]** を選択すると、空のキャンバスが開きます。 コントロールは、キャンバス上のコンポーネント定義の一部として追加できます。 キャンバスでコンポーネントを編集する場合は、他のアプリ画面で同じコンポーネントのインスタンスを更新します。 既に作成されたコンポーネントを再利用するアプリも、コンポーネントの変更を発行した後にコンポーネントの更新を受け取ることができます。

画面を選択した後、左側のナビゲーションで既存のコンポーネントの一覧からコンポーネントを選択できます。 コンポーネントを選択すると、そのコンポーネントのインスタンスが画面に挿入されます。コントロールを挿入するのと同じです。

アプリ内で使用できるコンポーネントは、ツリービュー内のコンポーネントの一覧の [**カスタム**カテゴリ] の下に一覧表示されます。 インポートされたコンポーネントライブラリは、[**ライブラリコンポーネント**カテゴリ] の下に一覧表示されます。

![アプリにコンポーネントを挿入する](./media/create-component/insert-components.png)

> [!NOTE]
> この記事で説明するコンポーネントは、開発者や開発者がモデル駆動型アプリとキャンバスアプリのコードコンポーネントを作成できるようにする、Power Apps コンポーネントフレームワークとは異なります。 詳細については、「 [Power Apps コンポーネントフレームワークの概要」](https://docs.microsoft.com/powerapps/developer/component-framework/overview)を参照してください。

## <a name="scope"></a>スコープ

コンポーネントは、インターフェイスとしてプロパティを持つカプセル化されたブラックボックスと考えることができます。 コンポーネントの外部からコンポーネント内のコントロールにアクセスすることはできません。 コンポーネント内からコンポーネントの外部にあるものを参照することはできません。 例外は、アプリとそのコンポーネント間で共有されるデータソースです。 スコープの制限により、コンポーネントのデータコントラクトがシンプルでまとまっていて、コンポーネント定義の更新を可能にします (特に、コンポーネントライブラリを使用したアプリ間で)。 コンポーネントのデータコントラクトを更新するには、1つまたは複数のカスタムプロパティを作成します。

> [!NOTE]
> コンポーネントライブラリ内の画面にコンポーネントのインスタンスを挿入し、テスト目的でその画面をプレビューすることができます。 また、 [Power Apps mobile](https://powerapps.microsoft.com/downloads/)を使用する場合は、コンポーネントライブラリが表示されないことに注意してください。

## <a name="custom-properties"></a>カスタムプロパティ

1つ以上のカスタムプロパティを作成すると、コンポーネントは入力値を受け取り、データを出力できます。 これらのシナリオは高度なものであり、[数式](formula-reference.md)やバインドコントラクトについて理解する必要があります。

**Input プロパティ**は、コンポーネントがコンポーネントで使用するデータを受け取る方法を示します。 コンポーネントのインスタンスが選択されている場合、右側のペインの **[プロパティ]** タブに入力プロパティが表示されます。 他のコントロールで標準プロパティを構成する場合と同様に、式または数式を使用して入力プロパティを構成できます。 その他のコントロールには、**テキスト入力**コントロールの**既定**のプロパティなどの入力プロパティがあります。

**出力プロパティ**は、データまたはコンポーネントの状態を出力するために使用されます。 たとえば、**ギャラリー**コントロールで**選択された**プロパティは、出力プロパティです。 出力プロパティを作成するときに、コンポーネントの状態を参照できる他のコントロールを指定できます。

次のチュートリアルでは、これらの概念について詳しく説明します。

## <a name="create-an-example-component"></a>サンプルコンポーネントの作成

この例では、次の図のようなメニューコンポーネントを作成します。 また、テキストを後で変更して、複数の画面、アプリ、またはその両方で使用することもできます。

![最終ギャラリー](./media/create-component/menu-instance-new.png)

> [!NOTE]
> 再利用するコンポーネントを作成する場合は、[コンポーネントライブラリ](component-library.md)を使用することをお勧めします。 アプリ内のコンポーネントを更新すると、アプリ内でコンポーネントの更新を使用できるようになります。 あるアプリから別のアプリにコンポーネントをインポートした場合、元のアプリのコンポーネントに対する新しい更新は、これらのコンポーネントをインポートしたアプリには反映されません。 コンポーネントライブラリを使用すると、ライブラリ内のコンポーネントが更新および発行されると、コンポーネントを更新するように求められます。

### <a name="create-a-new-component"></a>新しいコンポーネントの作成

1. [Make.powerapps.com](https://make.powerapps.com)にサインインします。

1. **[アプリ]** を選択し、[**キャンバスアプリ] を空白から**選択します。 

1. アプリ名を指定し、任意のレイアウトを選択して、 **[作成]** を選択します。

1. **ツリービュー**で、 **[コンポーネント]** を選択し、 **[新しいコンポーネント]** を選択して新しいコンポーネントを作成します。

    ![ツリービューを使用した新しいカスタムコンポーネントの作成](./media/create-component/insert-new-component-treeview.png)

1. 左側のナビゲーションで新しいコンポーネントを選択し、省略記号 (...) を選択して、 **[名前の変更]** を選択します。 名前を「 **Menucomponent**」と入力するか、貼り付けます。

1. 右側のウィンドウで、コンポーネントの 幅] を **[150]** 、[高さ を**250**に設定し、 **[新しいカスタムプロパティ]** を選択します。 また、必要に応じて高さ & 幅をその他の値に設定することもできます。

    ![新しいプロパティ](./media/create-component/new-property.png)

1. **[表示名]** 、 **[プロパティ名**]、 **[説明]** ボックスに、テキストを*項目*として入力するか貼り付けます。

    ![表示名、プロパティ名、説明ボックス](./media/create-component/property-names.png)

    式を記述するときに、この名前を使用してコンポーネントを参照するので、プロパティ名にスペースを含めないでください。 たとえば、 **ComponentName**のようになります。

    コンポーネントを選択すると、右側のウィンドウの **[プロパティ]** タブに表示名が表示されます。 わかりやすい表示名は、このプロパティの目的を理解するのに役立ちます。 **[プロパティ]** タブでこのプロパティの表示名をポイントすると、ツールヒントに**説明**が表示されます。

1. **[データ型]** ボックスの一覧で **[テーブル]** を選択し、 **[作成]** を選択します。

    ![プロパティのデータ型](./media/create-component/property-data-type.png)

    **Items**プロパティは、指定したデータ型に基づいて既定値に設定されます。 この値は、ニーズに合った値に設定できます。 **テーブル**または**レコード**のデータ型を指定した場合は、コンポーネントに入力するデータスキーマと一致するように**Items**プロパティの値を変更することができます。 この場合は、文字列のリストに変更します。

    右側のペインの **[プロパティ]** タブでプロパティの名前を選択した場合は、数式バーでプロパティの値を設定できます。

    ![[プロパティ] タブのカスタム入力プロパティ](./media/create-component/properties-tab.png)

    次の図に示すように、右側のウィンドウの **[詳細設定**] タブでプロパティの値を編集することもできます。

1. コンポーネントの**Items**プロパティを次の数式に設定します。

    ```powerapps-dot
    Table({Item:"SampleText"})
    ```

    ![[数式]](./media/create-component/set-component-items.png)

1. コンポーネントで、空の垂直**ギャラリー**コントロールを挿入し、プロパティ ウィンドウの **タイトル** で **レイアウト** を選択します。

1. プロパティリストに**Items**プロパティが表示されていることを確認します (既定では)。 次に、そのプロパティの値を次の式に設定します。

    ```powerapps-dot
    MenuComponent.Items
    ```

    このようにして、**ギャラリー**コントロールの**items**プロパティは、コンポーネントの**items** input プロパティを読み取って依存します。

1. 省略可能-**ギャラリー**コントロールの**borderthickness**プロパティを**1**に設定し、その**templatesize**プロパティを**50**に設定します。 また、必要に応じて、境界線の太さとテンプレートのサイズの値を他の値に更新することもできます。

### <a name="add-component-to-a-screen"></a>コンポーネントを画面に追加する

次に、コンポーネントを画面に追加し、表示するコンポーネントの文字列のテーブルを指定します。

1. 左側のナビゲーションバーで、画面の一覧を選択し、既定の画面を選択します。

    ![既定の画面](./media/create-component/default-screen.png)

1. **[挿入]** タブで、 **[コンポーネント]** メニューを開き、 **[menucomponent]** を選択します。

    ![［挿入］](./media/create-component/insert.png)

    新しいコンポーネントには、既定で**MenuComponent_1**という名前が付けられます。

1. **MenuComponent_1**の**Items**プロパティを次の数式に設定します。

    ```powerapps-dot
    Table({Item:"Home"}, {Item:"Admin"}, {Item:"About"}, {Item:"Help"})
    ```

    このインスタンスはこのグラフィックに似ていますが、各インスタンスのテキストおよびその他のプロパティをカスタマイズできます。

    ![最終ギャラリー](./media/create-component/menu-instance-new.png)

### <a name="create-and-use-output-property"></a>出力プロパティの作成と使用

ここまでで、コンポーネントを作成してアプリに追加しました。 次に、ユーザーがメニューで選択した項目を反映する出力プロパティを作成します。

1. コンポーネントの一覧を開き、 **[Menucomponent]** を選択します。

1. 右側のウィンドウで、 **[プロパティ]** タブを選択し、 **[新しいカスタムプロパティ]** を選択します。

1. **[表示名]** 、 **[プロパティ名**]、 **[説明]** の各ボックスに、「 **Selected**」と入力するか貼り付けます。

1. **[プロパティの種類]** で **[出力]** を選択し、 **[作成]** を選択します。

    ![出力としてのプロパティの型](./media/create-component/output-property-type.png)

1. [**詳細**設定] タブで、**選択した**プロパティの値を次の式に設定します。必要に応じて、ギャラリー名の数字を調整します。

    ```powerapps-dot
    Gallery1.Selected.Item
    ```

    ![[詳細設定] ウィンドウ](./media/create-component/advance.png)

1. アプリの既定の画面で、ラベルを追加し、 **Text**プロパティを次の式に設定します。必要に応じて、コンポーネント名の数字を調整します。

    ```powerapps-dot
    MenuComponent_1.Selected
    ```

    **MenuComponent_1**は、コンポーネント定義の名前ではなく、インスタンスの既定の名前です。 任意のインスタンスの名前を変更できます。

1. Alt キーを押しながら、メニューの各項目を選択します。

    **ラベル**コントロールには、最近選択したメニュー項目が反映されます。

## <a name="import-and-export-components"></a>コンポーネントのインポートとエクスポート

> [!NOTE]
> この機能は非推奨となります。 コンポーネント[ライブラリ](component-library.md)は、アプリ間でコンポーネントを再利用するために推奨される方法です。 コンポーネントライブラリを使用する場合、アプリは使用するコンポーネントへの依存関係を維持します。 依存コンポーネントに対する更新プログラムが利用可能になると、アプリの作成者に警告が表示されます。 そのため、再利用可能な新しいコンポーネントはすべて、代わりにコンポーネントライブラリ内に作成する必要があります。

### <a name="import-components-from-another-app"></a>別のアプリからコンポーネントをインポートする

1つ以上のコンポーネントを1つのアプリから別のアプリにインポートするには、 **[挿入]** メニューの **[コンポーネントのインポート]** をクリックし、 **[カスタム]** ドロップダウンを使用します。 または、左側のナビゲーションのツリービューの**コンポーネント**を使用します。

ダイアログボックスには、編集権限のあるコンポーネントが含まれているすべてのアプリが一覧表示されます。 アプリを選択し、 **[インポート]** を選択して、そのアプリ内のすべてのコンポーネントの最新の公開バージョンをインポートします。 少なくとも1つのコンポーネントをインポートしたら、必要のないコピーを編集して削除することができます。

![[コンポーネントのインポート] ダイアログボックス](./media/create-component/import-component-screen.png)

既存のコンポーネントを含むアプリをローカルにファイルに保存してから、ファイルをインポートして再利用することができます。 ファイルを使用して、コンポーネントを別のアプリにインポートできます。

同じコンポーネントの変更バージョンがアプリに含まれている場合は、変更されたバージョンを置き換えるか、インポートをキャンセルするかを決定するように求められます。 

アプリでコンポーネントを作成した後、他のアプリは、そのコンポーネントをインポートすることによって、このアプリのコンポーネントを使用できます。

### <a name="export-components-from-your-app"></a>アプリからコンポーネントをエクスポートする

コンポーネントをファイルにエクスポートして、別のアプリにインポートするためにダウンロードできます。

左側のナビゲーションツリービューの **[コンポーネント]** セクションから、 **[コンポーネントのエクスポート]** オプションを選択します。

![コンポーネントのエクスポート treeview](./media/create-component/export-components-treeview.png)

**[挿入]** メニューを使用して、代わりに **[カスタム]** ドロップダウンを選択することもできます。

![コンポーネントのエクスポート挿入メニュー](./media/create-component/export-components-insert-menu.png)

**[コンポーネントのエクスポート]** を選択すると、コンポーネントがファイルにダウンロードされます。

![コンポーネントのダウンロード](./media/create-component/download-component.png)

ダウンロードされたコンポーネントファイルは *、msapp*ファイル名拡張子を使用します。 

### <a name="import-components-from-exported-components-file"></a>エクスポートされたコンポーネントファイルからコンポーネントをインポートする

エクスポートされたコンポーネントファイルからコンポーネントをインポートするには、 **[挿入]** メニューの **[コンポーネントのインポート]** を選択します。 次に、 **[カスタム]** ドロップダウンを使用するか、左側のナビゲーションのツリービューの**コンポーネント**を使用します。 コンポーネント ダイアログボックスで、他のコンポーネントやアプリを選択するのではなく、**ファイルのインポート** を選択します。

![コンポーネントファイルのインポート](./media/create-component/import-component-file.png)

**[開く]** ダイアログボックスで、コンポーネントファイルの場所を参照し、 **[開く]** を選択して、アプリ内にコンポーネントをインポートします。

### <a name="import-components-from-exported-app"></a>エクスポートされたアプリからコンポーネントをインポートする

**ファイル** -> [名前を付け**て保存**] オプションを使用して、ローカルにアプリを保存できます。

![アプリの保存](./media/create-component/save-app-locally.png)

アプリを保存したら、ファイルからコンポーネントをインポートするのと同じ方法を使用して、このアプリのコンポーネントを再利用できます。 上記の「エクスポートされたコンポーネントファイルからコンポーネントをインポートする」セクションで説明されている手順に従います。

## <a name="known-limitations"></a>既知の制限事項

- データソース、フォーム、およびデータテーブルをコンポーネントと共に保存することはできません。
- コンポーネントのコレクションはサポートされていません。
- コンポーネントをギャラリーまたはフォームに挿入することはできません。
- コンポーネントのマスターインスタンスはローカルマスターで、アプリにスコープが設定されています。 マスターインスタンスを変更すると、アプリ内のコンポーネントのコピーだけが変更を反映します。 コンポーネントライブラリを再度インポートしない限り、他のアプリのコピーは同じままです。 これらのアプリのすべてのマスターインスタンスが自動的に検出され、更新されます。
- コンポーネントをインポートするときに、メディアファイルをパッケージ化することはできません。
- コンポーネントは[**Updatecontext**](./functions/function-updatecontext.md)関数をサポートしていませんが、 [**Set**](functions/function-set.md)関数を使用して、コンポーネントの変数を作成および更新できます。 これらの変数のスコープはコンポーネントに限定されますが、コンポーネントの外部からカスタム出力プロパティを使用してアクセスすることができます。

## <a name="next-steps"></a>次のステップ:

再利用可能なコンポーネントのリポジトリを作成するための[コンポーネントライブラリ](component-library.md)について説明します。