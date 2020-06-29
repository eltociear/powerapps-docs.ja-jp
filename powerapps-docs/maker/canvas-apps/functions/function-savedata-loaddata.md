---
title: SaveData および LoadData 関数 | Microsoft Docs
description: 構文を含む Power Apps の SaveData および LoadData 関数の参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/04/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: babd23bb7f3bb8fbf25e6422d4b53531cfe040e7
ms.sourcegitcommit: 0c92e85f95f3baa04cce140c96e53d5d86d685c0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "3333414"
---
# <a name="savedata-and-loaddata-functions-in-power-apps"></a>Power Apps の SaveData および LoadData 関数
ローカル デバイスに [コレクション](../working-with-data-sources.md#collections) を保存し、再読み込みします。

## <a name="description"></a>内容
**SaveData** 関数は、後で名前から使用できるようにコレクションを格納します。  

**LoadData** 関数は、既に **SaveData** で保存されている名前を使用してコレクションを再読み込みします。 別のソースからコレクションを読み込む場合、この関数は使用できません。  

> [!NOTE]
> **SaveData** および **LoadData** 間で共有される名前はキーで、ファイル名ではありません。 名前は各アプリに一意であり、名前が競合する危険がないため、複雑なものである必要はありません。 名前にこれらの文字のいずれかを含めることはできません: `*".?:\<>|/`。

これらの関数を使用して、アプリ起動時のパフォーマンスを向上させます。

- 最初の実行時の **[App.OnStart](../controls/control-screen.md#additional-properties)** 式のキャッシング データ。
- 次の実行時にローカル キャッシュを再読み込みします。

これらの関数を使用して、[簡単な Offline 機能](../offline-apps.md) をあなたのアプリに追加することもできます。

次の場合、ブラウザー内でこれらの関数を使用することはできません。

- Power Apps Studio でアプリを作成する。
- Web プレーヤーでアプリを実行します。 

アプリをテストするには、iPhone または Android デバイス上の Power Apps Mobile で実行します。

これらの関数は、メモリ内コレクションで動作するため、アプリの利用可能なメモリ容量によって制限されます。 利用可能なメモリは、次のような要因に基づいて異なります。 

- デバイスおよびオペレーティング システム。
- Power Apps プレーヤーが使用するメモリ。
- アプリの複雑性および画面とコントロール。 

アプリが大量のデータを格納するときに実行することが予想される種類のデバイスを使用し、予想されるシナリオでアプリをテストします。 一般的に、30 MB から 70 MB の利用可能なメモリが必要です。

これらの関数は、**[Collect](function-clear-collect-clearcollect.md)** または **[ClearCollect](function-clear-collect-clearcollect.md)** で暗黙的に定義されているコレクションに依存します。 データを定義のコレクションに読み込むのに、**Collect** または **ClearCollect** を呼び出す必要はありません。 前の **SaveData** の後に **LoadData** を使用する場合の、一般的なケースです。  数式内にこれらの関数が存在し、コレクションの構造が明示的に定義されていれば十分です。  詳細については、[変数の作成および削除](../working-with-variables.md#create-and-remove-variables) を参照してください。

読み込まれたデータはコレクションに追加されます。 空のコレクションから始めたい場合は、**LoadData** を呼び出す前に **[Clear](function-clear-collect-clearcollect.md)** 関数を使用します。

デバイス組み込みのアプリ サンドボックス機能を使用して、保存されたデータをその他のアプリから分離します。 

デバイスはデータを暗号化することもできます。また、[Microsoft Intune](https://www.microsoft.com/microsoft-365/enterprise-mobility-security/microsoft-intune) のようなモバイル デバイス管理ツールを使用することもできます。

## <a name="syntax"></a>構文
**SaveData**( *Collection*, *Name* )<br>**LoadData**( *Collection*, *Name* [, *IgnoreNonexistentFile* ])

* *Collection* - 必須。  格納または読み込みの対象となるコレクション。
* *Name* - 必須。  ストレージの名前。 同じデータ セットを保存し、読み込むには、名前が同じである必要があります。 名前空間は、その他のアプリまたはユーザーとは共有されません。  名前にこれらの文字のいずれかを含めることはできません: `*".?:\<>|/`。
* *IgnoreNonexistentFile* - オプション。 ファイルがまだ存在していない場合の処理を示すブール値。  *false* (既定) を使用するとエラーを返し、*true* の場合、エラーは非表示になります。   

## <a name="examples"></a>例

| 計算式 | 内容 | 結果 |
| --- | --- | --- |
| **SaveData( LocalCache, "MyCache" )** | 後で **LoadData** が取得できるように、「MyCache」の名前の下のユーザー デバイスに **LocalCache** コレクションを保存します。 | データはローカル デバイスに保存されます。 |
| **LoadData( LocalCache, "MyCache" )** | 「MyCache」という名前の下のユーザー デバイスから、以前に **SaveData** の呼び出しによって保存された **LocalCache** コレクションを読み込みます。  | データはローカル デバイスから保存されます。 |   

### <a name="simple-offline-example"></a>簡単なオフラインの例

次の簡単な例では、オフライン時の日常アイテムの名前と画像を取得し、格納します。  後で使用するために、デバイスのローカル ストレージに情報を格納します。 これにより、データを失うことなくアプリを閉じたり、デバイスを再起動したりできます。  

Web ブラウザーでは動作しない **LoadData** および **SaveData** 関数を使用しているので、デバイスを使用してこの例の手順に従う必要があります。

1. タブレットのレイアウトで空白のキャンバス アプリを作成します。  詳細については、[テンプレートからアプリを作成する](../get-started-test-drive.md) を読み、**空のアプリ**の下の**タブレット レイアウト**を選択してください。  

1. [**テキスト入力**](../controls/control-text-input.md) コントロールおよび [**カメラ**](../controls/control-camera.md) コントロールを追加し、表示されているように大まかに配置します。
    > [!div class="mx-imgBorder"]  
    > ![空白の画面に追加されたテキスト入力コントロールとカメラ コントロール](media/function-savedata-loaddata/simple-text-camera.png)

1. [**ボタン**](../controls/control-button.md) コントロールを追加します。

2. ボタン コントロールをダブル クリックして、ボタンのテキストを**アイテムの追加**に変更 (または **Text** プロパティを変更) します。

3. ボタン コントロールの **OnSelect** プロパティを次の式に設定し、コレクションにアイテムを追加します。
    ```powerapps-dot
    Collect( MyItems, { Item: TextInput1.Text, Picture: Camera1.Photo } )
    ```
    > [!div class="mx-imgBorder"] 
    > ![「アイテムの追加」というテキストと OnSelect プロパティ セットが追加されたボタン コントロール](media/function-savedata-loaddata/simple-additem.png)

1. 別の**ボタン** コントロールを追加します。

2. ボタン コントロールをダブル クリックして、ボタンのテキストを**データの保存**に変更 (または **Text** プロパティを変更) します。

3. ボタン コントロールの **OnSelect** プロパティを次の式に設定し、コレクションをローカル デバイスに保存します。
    ```powerapps-dot
    SaveData( MyItems, "LocalSavedItems" )
    ```
    > [!div class="mx-imgBorder"] 
    > ![「データの保存」というテキストと OnSelect プロパティ セットが追加されたボタン コントロール](media/function-savedata-loaddata/simple-savedata.png)

    影響がないため、ボタンをテストしたくなることがあります。 ただし、Web ブラウザーで作成しているときはエラーが表示されるだけです。 次の手順に従ってこの式をテストする前に、最初にアプリを保存し、デバイスで開きます。

1. 3 番目の**ボタン** コントロールを追加します。

2. ボタン コントロールをダブル クリックして、ボタンのテキストを**データの読み込み**に変更 (または **Text** プロパティを変更) します。

3. ボタン コントロールの **OnSelect** プロパティを次の式に設定し、コレクションをローカル デバイスから読み込みます。
    ```powerapps-dot
    LoadData( MyItems, "LocalSavedItems" )
    ``` 
    > [!div class="mx-imgBorder"] 
    > ![「データの読み込み」というテキストと OnSelect プロパティ セットが追加されたボタン コントロール](media/function-savedata-loaddata/simple-loaddata.png)

1. [**ギャラリー**](../controls/control-gallery.md) コントロールを画像とテキスト エリアを含む縦方向のレイアウトで追加します。 
    > [!div class="mx-imgBorder"] 
    > ![ギャラリーのさまざまな選択、画像とテキスト エリアが選択された「縦方向」](media/function-savedata-loaddata/simple-gallery-add.png)

1. 確認を要求されたら、このギャラリーのデータ ソースとして **MyItems** コレクションを選択します。  これにより、**ギャラリー** コントロールの **Items** プロパティを設定します。 
    > [!div class="mx-imgBorder"] 
    > ![ギャラリーのデータ ソースの選択](media/function-savedata-loaddata/simple-gallery-collection.png) ギャラリー テンプレートの画像コントロールについて、既定で**画像**プロパティは **ThisItem.Picture** に、ラベル コントロールについては両方とも既定で**テキスト**プロパティは **ThisItem.Item** になっている必要があります。  次の手順でアイテムを追加した後、ギャラリーに何も表示されない場合は、これらの式を確認してください。 

1. コントロールをその他のコントロールの右側に配置します。 
    > [!div class="mx-imgBorder"] 
    > ![画面の右側に再配置されたギャラリー](media/function-savedata-loaddata/simple-gallery-placed.png)

1. アプリを保存します。  保存するのが初めての場合、公開する必要はありません。 初めてでない場合は、保存した後にアプリを公開します。

1. スマートフォンやタブレットなどのデバイスでアプリを開きます。  **SaveData** および **LoadData** は、Studio または Web ブラウザーでは使用できません。  アプリがすぐに表示されない場合は、アプリ リストを更新してください。アプリがデバイスに表示されるまで数秒かかる場合があります。  サインアウトしてアカウントに再度サインインすることも役立ちます。
    > [!div class="mx-imgBorder"] 
    > ![アイテムを追加せずに実行しているアプリ](media/function-savedata-loaddata/simple-mobile.png) アプリがダウンロードされたら、ネットワークから接続を解除して、オフラインでアプリを実行できます。

1. 名前を入力して、アイテムの画像を撮影します。

2. **アイテムの追加**ボタンを選択します。  アイテムの追加を何回か繰り返し、コレクションを読み込みます。
    > [!div class="mx-imgBorder"] 
    > ![3 つのアイテムを追加して実行しているアプリ](media/function-savedata-loaddata/simple-mobile-with3.png) 

1. **データの保存**ボタンを選択します。  これにより、コレクション内のデータがローカル デバイスに保存されます。

1. アプリを閉じます。  すべてのアイテム名と画像を含め、メモリ内のコレクションは失われますが、デバイスのストレージからは削除されません。

1. アプリを再度起動します。  メモリ内のコレクションは、ギャラリーで再び空として表示されます。
    > [!div class="mx-imgBorder"] 
    > ![アイテムの追加なしで再び実行しているアプリ](media/function-savedata-loaddata/simple-mobile.png) 

1. **データの読み込み**ボタンを選択します。  コレクションは、デバイスに保存されているデータから再作成され、アイテムはギャラリーに戻ります。  このボタンが **LoadData** 関数を呼び出す前、コレクションは空でしたが、ストレージからデータを読み込む前に **Collect** または **ClearCollect** を呼び出す必要はありません。
    > [!div class="mx-imgBorder"] 
    > ![LoadData 関数を呼び出した後に復元された 3 つのアイテムで実行中のアプリ](media/function-savedata-loaddata/simple-mobile-load1.png) 

1. **データの読み込み**ボタンをもう一度選択します。  格納されたデータはコレクションの最後に追加され、ギャラリーにスクロール バーが表示されます。  追加ではなく置換したい場合、**LoadData** 関数を呼び出す前、最初に **Clear** 関数を呼び出してコレクションをクリアします。
    > [!div class="mx-imgBorder"] 
    > ![LoadData 関数を 2 回呼び出した後に復元された 6 つのアイテムで実行中のアプリ](media/function-savedata-loaddata/simple-mobile-load2.png) 
 
### <a name="more-advanced-offline-example"></a>より高度なオフラインの例

詳細な例については、[簡単なオフライン機能](../offline-apps.md) の記事を参照してください。







