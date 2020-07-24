---
title: Power Apps Component Framework を使用して最初のコンポーネントを作成する | MicrosoftDocs
description: TypeScript を使用してコード コンポーネントを実装する方法
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: index-page
ms.assetid: 18e88d702-3349-4022-a7d8-a9adf52cd34f
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: ebcf23a4986129aacab5ea11dbffe2be7e7a0518
ms.sourcegitcommit: ee4796919a3ef520e95210468ec57f8d4baa39db
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2020
ms.locfileid: "3442218"
---
# <a name="create-your-first-component"></a>最初のコンポーネントを作成する 

 このチュートリアルでは、ユーザーがフィールドに値を入力する代わりに、視覚的なスライダーを使用して数値を変更できる線形スライダー コード コンポーネントを構築する方法を説明をします。 

線形スライダー コード コンポーネントを構築するには、次の手順が必要です。

- [新しいコンポーネント プロジェクトを作成する](#creating-a-new-component-project)
- [マニフェストの実装](#implementing-manifest)
- [TypeScript を使ってコンポーネント ロジックを実装する](#implementing-component-logic)
- [コード コンポーネントにスタイルを追加する](#adding-style-to-the-code-component)
- [コード コンポーネントを構築する](#build-your-code-components)
- [コード コンポーネントのパッケージ化](#packaging-your-code-components)
- [コンポーネントをモデル駆動型アプリに追加する](#adding-code-components-in-model-driven-apps)
- [コンポーネントをキャンバス アプリに追加する](#adding-code-components-to-a-canvas-app)

## <a name="creating-a-new-component-project"></a>新しいコンポーネント プロジェクトを作成する

新しいプロジェクトを作成するには:

1. **VS 2017 以降の開発者コマンド プロンプト** ウィンドウを開きます。 次のコマンドを使用してプロジェクトの新しいフォルダを作成します: 
    ```CLI
     mkdir LinearComponent
    ```
                     
1. コマンド `cd LinearComponent` を使用してコンポーネントへ移動します。 
         
1. このコマンドを実行して、基本パラメータを渡して新しいコンポーネントプロジェクトを作成します。

   ```CLI
    pac pcf init --namespace SampleNamespace --name TSLinearInputComponent --template field
    ``` 

1. `npm install` コマンドを使用して、プロジェクトのビルド ツールをインストールします。 
1. 任意の開発者環境でプロジェクト フォルダ を開き、コード コンポーネントの開発を開始します。 最も簡単な方法は、プロジェクト ディレクトリに移動して、コマンド プロンプトから `code .` を実行することです。 このコマンドは、 Visual Studio コードにあるコンポーネントプロジェクトを開きます。

## <a name="implementing-manifest"></a>マニフェストの実装

マニフェストは、コード コンポーネントのメタデータを含む XML ファイルです。 また、コード コンポーネントの動作も定義します。 このチュートリアルでは、`<Your component Name>` サブフォルダーでマニフェスト ファイルが作成されます。 Visual Studio コードで `ControlManifest.Input.xml` ファイルを開く場合、マニフェストが一部のプロパティに定義済であることがわかります。 詳細: [マニフェスト](manifest-schema-reference/manifest.md)。

次のように定義済みマニフェスト ファイルへの変更を実施します:

1. [コントロール](manifest-schema-reference/control.md) ノードは、コード コンポーネントの名前空間、バージョン、および表示名を定義します。 ここでは、ここで示すように、[制御](manifest-schema-reference/control.md) ノードの各プロパティを定義します:

   - **名前空間**: コード コンポーネントの名前空間。 
   - **コンストラクター**: コード コンポーネントのコンストラクター。
   - **バージョン**: コンポーネントのバージョン。 コンポーネントを更新すると、実行時に変更を表示するの最新バージョンに更新する必要があります。
   - **表示名前キー**: UIに表示するコード コンポーネントの名前。
   - **表示名キー**: UIに表示するコード コンポーネントの説明。
   - **control-type**: コード コンポーネントの種類。 コード コンポーネントの *標準* タイプのみがサポートされています。

     ```XML
      <?xml version="1.0" encoding="utf-8" ?>
      <manifest>
      <control namespace="SampleNameSpace" constructor="TSLinearInputComponent" version="1.0.0" display-name-key="TSLinearInputComponent_Display_Key" description-key="TSLinearInputComponent_Desc_Key" control-type="standard">
     ```

2. [プロパティ](manifest-schema-reference/property.md) ノードは、フィールドのデータ型の定義など、コード コンポーネントのプロパティを定義します。 プロパティ ノードに、`control` 要素下で子要素として指定されます。 ここに示されている通り、[プロパティ](manifest-schema-reference/property.md) ノードを定義します:

   - **名前**: プロパティの名前。
   - **表示名前キー**: UIで表示するプロパティの表示名。
   - **表示名キー**: UIに表示するプロパティの説明。 
   - **of-type-group**: [of-type-group](manifest-schema-reference/type-group.md) は、2 つ以上のデータ フィールドが必要な場合に使用されます。 [of-type-group](manifest-schema-reference/type-group.md) 要素をマニフェストの `property` 要素の兄弟として追加します。 `of-type-group` はコンポーネント値を指定し、整数、通貨、浮動小数点、または 10 進数値を含めることができます。
   - **使用**: 2 つのプロパティ、*バインド*と*入力*を持っています。 プロパティ バインドは、フィールドの値のみ使用されます。 入力プロパティは、フィールドへのバインド、または静的な値の許可のいずれかです。
   - **必須**: プロパティが必須かどうかを定義します。

     ```XML
      <property name="sliderValue" display-name-key="sliderValue_Display_Key" description-key="sliderValue_Desc_Key" of-type-group="numbers" usage="bound" required="true" />
      ```

3. [リソース](manifest-schema-reference/resources.md)ノードは、コード コンポーネントのビジュアル化を定義します。 これはコード コンポーネントのビジュアル化とスタイル化を構築するすべてのリソースが含まれています。 [コード](manifest-schema-reference/code.md) は、リソース要素下で子要素として指定されます。 以下に示されるように、[リソース](manifest-schema-reference/resources.md) を定義します:

   - **コード**: すべてのリソース ファイルが設置されるファイル パスを参照します。
 
      ```XML
      <resources>
        <code path="index.ts" order="1" />
        <css path="css/TS_LinearInputComponent.css" order="1" />
      </resources>
        ```
      マニフェスト ファイル全体は、次のように表示されます。 

     ```XML
      <?xml version="1.0" encoding="utf-8" ?>
      <manifest>
      <control namespace="SampleNamespace" constructor="TSLinearInputComponent" version="1.0.0" display-name-key="TSLinearInputComponent_Display_Key" description-key="TSLinearInputComponent_Desc_Key" control-type="standard">
        <type-group name="numbers">
          <type>Whole.None</type>
          <type>Currency</type>
          <type>FP</type>
          <type>Decimal</type>
         </type-group>
        <property name="sliderValue" display-name-key="sliderValue_Display_Key" description-key="sliderValue_Desc_Key" of-type-group="numbers" usage="bound" required="true" />
       <resources>
         <code path="index.ts" order="1" />
         <css path="css/TS_LinearInputComponent.css" order="1" />
       </resources>
      </control>
     </manifest>
     ```

4. `ControlManifest.Input.xml` ファイルに加えた変更を保存します。

## <a name="implementing-component-logic"></a>コンポーネント ロジックの実装

マニフェスト ファイルを実行した後の次の手順は、TypeScript を使用してマニフェスト ファイルをコンポーネントのロジックに実装することです。 コンポーネントのロジックは、`index.ts` ファイル内で実装する必要があります。 Visual Studio コードで `index.ts` ファイルを開くと、4 つの重要な関数が事前定義されていることがわかります。 次に、コード コンポーネントのロジックを実装します。 

1. 任意のコードエディタで `index.ts` ファイルを開きます。
2. 次のコードで `TSLinearInputComponent` クラスを更新します。

```TypeScript
import { IInputs, IOutputs } from "./generated/ManifestTypes";
export class TSLinearInputComponent
  implements ComponentFramework.StandardControl<IInputs, IOutputs> {
  // Value of the field is stored and used inside the component
  private _value: number;
  // Power Apps component framework delegate which will be assigned to this object which would be called whenever any update happens.
  private _notifyOutputChanged: () => void;
  // label element created as part of this component
  private labelElement: HTMLLabelElement;
  // input element that is used to create the range slider
  private inputElement: HTMLInputElement;
  // reference to the component container HTMLDivElement
  // This element contains all elements of our code component example
  private _container: HTMLDivElement;
  // reference to Power Apps component framework Context object
  private _context: ComponentFramework.Context<IInputs>;
  // Event Handler 'refreshData' reference
  private _refreshData: EventListenerOrEventListenerObject;

  constructor() {}

  public init(
    context: ComponentFramework.Context<IInputs>,
    notifyOutputChanged: () => void,
    state: ComponentFramework.Dictionary,
    container: HTMLDivElement
  ) {
    this._context = context;
    this._container = document.createElement("div");
    this._notifyOutputChanged = notifyOutputChanged;
    this._refreshData = this.refreshData.bind(this);
    // creating HTML elements for the input type range and binding it to the function which refreshes the component data
    this.inputElement = document.createElement("input");
    this.inputElement.setAttribute("type", "range");
    this.inputElement.addEventListener("input", this._refreshData);
    //setting the max and min values for the component.
    this.inputElement.setAttribute("min", "1");
    this.inputElement.setAttribute("max", "1000");
    this.inputElement.setAttribute("class", "linearslider");
    this.inputElement.setAttribute("id", "linearrangeinput");
    // creating a HTML label element that shows the value that is set on the linear range component
    this.labelElement = document.createElement("label");
    this.labelElement.setAttribute("class", "TS_LinearRangeLabel");
    this.labelElement.setAttribute("id", "lrclabel");
    // retrieving the latest value from the component and setting it to the HTML elements.
    this._value = context.parameters.sliderValue.raw
      ? context.parameters.sliderValue.raw
      : 0;
    this.inputElement.value =
      context.parameters.sliderValue.formatted
        ? context.parameters.sliderValue.formatted
        : "0";
    
    this.labelElement.innerHTML = context.parameters.sliderValue.formatted
      ? context.parameters.sliderValue.formatted
      : "0";
    // appending the HTML elements to the component's HTML container element.
    this._container.appendChild(this.inputElement);
    this._container.appendChild(this.labelElement);
    container.appendChild(this._container);
  }

  /**
   * Updates the values to the internal value variable we are storing and also updates the html label that displays the value
   * @param context : The "Input Properties" containing the parameters, component metadata and interface functions
   */

  public refreshData(evt: Event): void {
    this._value = (this.inputElement.value as any) as number;
    this.labelElement.innerHTML = this.inputElement.value;
    this._notifyOutputChanged();
  }

  public updateView(context: ComponentFramework.Context<IInputs>): void {
    // storing the latest context from the control.
    this._value = context.parameters.sliderValue.raw
      ? context.parameters.sliderValue.raw
      : 0;
    this._context = context;
    this.inputElement.value =
     
      context.parameters.sliderValue.formatted
        ? context.parameters.sliderValue.formatted
        : "";
    
    this.labelElement.innerHTML = context.parameters.sliderValue.formatted
      ? context.parameters.sliderValue.formatted
      : "";
  }

  public getOutputs(): IOutputs {
    return {
      sliderValue: this._value
    };
  }

  public destroy() {
    this.inputElement.removeEventListener("input", this._refreshData);
  }
}

```

3. `index.ts` ファイルへの変更を保存します。

## <a name="adding-style-to-the-code-component"></a>コード コンポーネントにスタイルを追加する

開発者およびアプリ作成者は、CSS を使用してコード コンポーネントを表するためのスタイルを定義できます。 CSS は、スタイル、、色、レイアウトやフォントを含む、コード コンポーネントのプレゼンテーションを開発者が説明できるようにします。 線形入力コンポーネントの [init](reference/control/init.md) メソッドは、入力の要素を作成し、クラス属性を `linearslider` に設定します。 `linearslider` クラスのスタイルは別に `CSS` ファイルで定義されます。 `CSS` ファイルのような追加のコンポーネント リソースをコード コンポーネントに含め、さらにカスタマイズをサポートすることができます。

> [!IMPORTANT]
> CSS を使用してコード コンポーネントにスタイルを実装する場合は、コンポーネントのコンテナー `DIV` 要素に適用される自動生成された CSS クラスを使用して、CSS がコントロールにスコープ設定されていることを確認してください。 CSS がグローバルにスコープ設定されている場合、コード コンポーネントが表示されるフォームまたは画面の既存のスタイルが損なわれる可能性があります。 サード パーティの CSS フレームワークを使用している場合は、すでに名前空間が設定されているフレームワークのバージョンを使用するか、手動で、または CSS プリプロセッサを使用して、そのフレームワークを名前空間にラップします。

1. `TSLinearInputComponent` フォルダの下に新しい `css` サブフォルダを作成します。 
2. `css` サブ フォルダの中に新しい `TS_LinearInputComponent.css` ファイルを作成します。 
3. 以下のスタイル コンテンツを `TS_LinearInputComponent.css` ファイルに追加します:

    ```CSS
    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider {
      margin: 1px 0;
      background: transparent;
      -webkit-appearance: none;
      width: 100%;
      padding: 0;
      height: 24px;
      -webkit-tap-highlight-color: transparent
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider:focus {
      outline: none;
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider::-webkit-slider-runnable-track {
      background: #666;
      height: 2px;
      cursor: pointer
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider::-webkit-slider-thumb {
      background: #666;
      border: 0 solid #f00;
      height: 24px;
      width: 10px;
      border-radius: 48px;
      cursor: pointer;
      opacity: 1;
      -webkit-appearance: none;
      margin-top: -12px
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider::-moz-range-track {
      background: #666;
      height: 2px;
      cursor: pointer
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider::-moz-range-thumb {
      background: #666;
      border: 0 solid #f00;
      height: 24px;
      width: 10px;
      border-radius: 48px;
      cursor: pointer;
      opacity: 1;
      -webkit-appearance: none;
      margin-top: -12px
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider::-ms-track {
      background: #666;
      height: 2px;
      cursor: pointer
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider::-ms-thumb {
      background: #666;
      border: 0 solid #f00;
      height: 24px;
      width: 10px;
      border-radius: 48px;
      cursor: pointer;
      opacity: 1;
      -webkit-appearance: none;
    }
    ```

5. `TS_LinearInputComponent.css` ファイルを保存します。
6. `ControlManifest.Input.xml` ファイルを編集して、リソース要素内の `CSS` リソース ファイルを含めます。
 
    ```XML
    <resources> 
      <code path="index.ts" order="1"/> 
      <css path="css/TS_LinearInputComponent.css" order="1"/> 
    </resources> 
     ```

> [!NOTE]
> Power Apps component framework は、ローカライズされた文字列の管理に使用される文字列 (resx) Web リソースを実装する概念を使用し、任意のユーザー インターフェイスに表示されます。 詳細: [文字列 (Resx) Web リソース](https://docs.microsoft.com/dynamics365/customerengagement/on-premises/developer/resx-web-resources)。
> `resx` Web リソースを使用してコード コンポーネントをローカライズする方法については、[ローカライズ API](sample-controls/localization-api-control.md) サンプル を参照してください。 


## <a name="build-your-code-components"></a>コード コンポーネントを構築する

マニフェスト、コンポーネント ロジック、スタイルの追加が完了したら、次のコマンドを使用してコード コンポーネントをビルドします:
```
npm run build
```

または、コンポーネント プロジェクトをビルドするには、Visual Studio Code の `package.json` を含むプロジェクト フォルダを開き、(Ctrl-Shift-B) コマンドを使用して、ビルド オプションを選択します。 ビルドは、`TSLinearInputComponent/generated` フォルダーの TypeScript 型の宣言ファイルを作成および更新します。
コンポーネントは `out/controls/TSLinearInputComponent` フォルダにコンパイルされます。 構築アーティファクトには以下が含まれます:

   - bundle.js – バンドルされたコンポーネントのソースコード。 
   - ControlManifest.xml – Common Data Service にアップロードされるコンポーネント マニフェスト ファイル。

## <a name="debugging-your-code-component"></a>コード コンポーネントのデバッグ

コード コンポーネント ロジックの実装が完了したら、以下のコマンドを実行してデバッグ処理を開始します。 詳細: [コード コンポーネントのデバッグ](debugging-custom-controls.md)

```CLI
npm start
```

## <a name="packaging-your-code-components"></a>コード コンポーネントのパッケージ化

[ソリューション](https://docs.microsoft.com/powerapps/maker/common-data-service/solutions-overview) ファイルを作成してインポートするには、次の手順に従います:

1. **LinearComponent** フォルダー内の新しい フォルダー **ソリューション** 作成し、フォルダーに移動します。 
2. 以下のコマンドを使用して **LinearComponent** フォルダに新しいソリューション プロジェクトを作成します:
 
    ```CLI
     pac solution init --publisher-name developer --publisher-prefix dev 
    ```

   > [!NOTE]
   > [publisher-name](https://docs.microsoft.com/powerapps/developer/common-data-service/reference/entities/publisher) と [publisher-prefix](https://docs.microsoft.com/powerapps/maker/common-data-service/change-solution-publisher-prefix) の値は環境に特化したものである必要があります。
 
3. 新しいソリューション プロジェクトを作成したら、その作成したコンポーネントが配置される場所を参照する必要があります。 以下のコマンドを使用して参照を追加できます:

    ```CLI
     pac solution add-reference --path c:\users\LinearComponent
    ```

4. ソリューション プロジェクトから zip ファイルを生成するには、ソリューション プロジェクト ディレクトリに `cd` して、以下のコマンドを使ってプロジェクトをビルドする必要があります: 

    ```CLI
     msbuild /t:restore
    ```

5. 再度、次のコマンドを実行します:
    ```CLI
     msbuild
    ```
    > [!TIP]
    > 次のエラーが発生します: `msbuild` コマンドを使用してソリューションファイルをビルドし、Common Data Service にインポートして、ソリューション チェッカーを実行する場合は、*`eval` 関数または同等の機能を使用しないでください*。
    > コマンド `msbuild/property:configuration=Release` を使用してソリューション ファイルを再構築し、ソリューションを Common Data Service に再インポートして、ソリューション チェッカーを実行します。
      
    > [!NOTE]
    > **NuGet ターゲットおよび構成タスク** のチェックボックスをオンにしてください。 これを有効にするには、次の手順を行います。
    > - **Visual Studio インストーラー** を開きます。
    > - Visual Studio 2017 以降の場合は、**修正** を選択します。
    > - **個別のコンポーネント** を選択します。
    > - **コード ツール** の **NuGetターゲットとビルド タスク** にチェックマークを付けます。

6. 生成されたソリューションの zip ファイルは、`Solution\bin\debug` フォルダーにあります。
7. zipファイルが準備ができたらWeb ポータルを使用して、手動で [ソリューションを Common Data Service にインポートする](https://docs.microsoft.com/powerapps/maker/common-data-service/import-update-export-solutions) か、 [Microsoft Power Platform Build Tools](https://marketplace.visualstudio.com/items?itemName=microsoft-IsvExpTools.PowerApps-BuildTools) を使用して自動的にインポートします。

## <a name="adding-code-components-in-model-driven-apps"></a>モデル駆動型のアプリのコード コンポーネントの追加

線形入力コンポーネントのようなコード コンポーネントを追加するには、記事 [コンポーネントをフィールドとエンティティに追加する](add-custom-controls-to-a-field-or-entity.md) に記載されている手順に従ってください。

## <a name="adding-code-components-to-a-canvas-app"></a>キャンバス アプリにコード コンポーネントを追加する

コード コンポーネントをキャンバス アプリに追加するには、記事 [キャンバス アプリにコード コンポーネントを追加する](component-framework-for-canvas-apps.md#add-components-to-a-canvas-app) の手順に従ってください。

### <a name="see-also"></a>関連項目

[サンプル コンポーネントをダウンロード](https://github.com/microsoft/PowerApps-Samples/tree/master/component-framework)<br/>
[Power Apps component framework の学習](https://docs.microsoft.com/learn/paths/use-power-apps-component-framework)<br/>
[既存の Power Apps component framework のコンポーネントを更新する](updating-existing-controls.md)<br/>
[Microsoft Power Platform Build Tools](https://docs.microsoft.com/powerapps/developer/common-data-service/build-tools-overview)<br/>
[Power Apps Component Framework API の参照](reference/index.md)<br/>
[Power Apps Component Framework の概要](overview.md)
