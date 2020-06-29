---
title: マルチメディア ファイルをキャンバス アプリに埋め込んでアップロードする | Microsoft Docs
description: キャンバス アプリでマルチメディア ファイルを表示して、それらをデータ ソースにアップロードする
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 07/12/2017
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 58b96ab5758fd30a05d9f325cb623bbc338b0d00
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3306568"
---
# <a name="using-multimedia-files-in-power-apps"></a>Power Apps でマルチメディア ファイルを使用する

このトピックでは、キャンバス アプリにマルチメディア ファイルを埋め込み、データ ソースにペン画をアップロードして、キャンバス アプリでデータ ソースからの画像を表示する方法を説明します。 このトピックで使用しているデータ ソースは、OneDrive for Business の Excel ファイルです。

## <a name="prerequisites"></a>前提条件

Power Apps に[サインアップ](../signup-for-powerapps.md) し、サインアップに使用した同じ資格情報を使用して[サインイン](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) します。

## <a name="add-media-from-a-file-or-the-cloud"></a>ファイルまたはクラウドからメディアを追加する

追加するメディア ファイルの種類 (画像、ビデオ、オーディオなど) を選択できます。

1. **コンテンツ** タブで**メディア**を選択します。

2. **メディア**で、**画像**、**ビデオ**、または**オーディオ**を選択し、**参照**を選択します。

    ![メディアの参照][1]

3. 追加するファイルを選択して、**開く**を選択します。

    お使いのコンピューターの**ピクチャ** フォルダーが開き、そこから画像を選択するか、または別のフォルダーに移動できます。

4. ファイルの追加が終了したら、Esc キーを押して既定のワークスペースに戻ります。

5. **挿入**タブで**メディア**を選択し、**画像**、**ビデオ**、または**オーディオ**を選択します。

    ![メディアの種類の選択][8]

6. 画像コントロールを追加した場合は、その **[Image](controls/properties-visual.md)** プロパティを、追加したファイルに設定します。  

    ![Image プロパティの設定](./media/add-images-pictures-audio-video/imageproperty.png)

    > [!NOTE]
   > 拡張子を付けずに、単一引用符で囲んで、ファイル名のみを指定します。

7. ビデオまたはオーディオ コントロールを追加した場合は、その **Media** プロパティを、追加したファイルに設定します。  

    ![Media プロパティの設定](./media/add-images-pictures-audio-video/mediaproperty.png)

    > [!NOTE]
   > YouTube ビデオを再生するには、ビデオ コントロールの **Media** プロパティを、二重引用符で囲んだ該当する URL に設定します。

## <a name="add-media-from-azure-media-services"></a>Azure Media Services からメディアを追加する
1. Azure Media Services アカウントの **AMS > 設定 > 資産**から、ビデオ資産をアップロードして公開します。

2. 公開したら、ビデオの URL をコピーします。

3. Power Apps の**挿入 > メディア**から、**ビデオ** コントロールを追加します。

4. **Media** プロパティを、コピーした URL に設定します。

    次の図に示すように、Azure Media Services がサポートするすべてのストリーミング URL を選択できます。

    ![Media プロパティの設定](./media/add-images-pictures-audio-video/ams-with-powerapps.png)

## <a name="add-images-from-the-cloud-to-your-app"></a>クラウドからアプリに画像を追加する
このシナリオでは、クラウド ストレージ アカウントの OneDrive for Business に画像を保存します。 Excel テーブルを使用して画像へのパスを含め、アプリのギャラリー コントロールにその画像を表示します。

このシナリオでは、いくつかの .jpeg ファイルを含む [CreateFirstApp.zip](https://pwrappssamples.blob.core.windows.net/samples/CreateFirstApp.zip) を使用します。

> [!NOTE]
> Excel ファイル内のこれらの画像へのパスには、スラッシュを使用する必要があります。 Power Apps で Excel テーブルに画像のパスを保存すると、パスに円記号が使われます。 このようなテーブルからの画像のパスを使用する場合は、Excel テーブル内のパスを円記号ではなくスラッシュを使用するように変更します。 そうしないと、画像は表示されません。  

1. [CreateFirstApp.zip](https://pwrappssamples.blob.core.windows.net/samples/CreateFirstApp.zip) をダウンロードし、**Assets** フォルダーをクラウド ストレージ アカウントに抽出します。

2. **Assets** フォルダーの名前を **Assets_images** に変更します。

3. Excel スプレッドシートに 1 列のテーブルを作成し、次のデータを入力します。

    ![Jackets テーブル](./media/add-images-pictures-audio-video/jackets.png)

4. テーブルに **Jackets** と名前を付け、Excel ファイルに **Assets.xlsx** と名前を付けます。

5. アプリで、データ ソースとして **Jackets** テーブルを追加します。  

6. **画像のみ**コントロール (**挿入** タブ > **ギャラリー**) を追加し、その **Items** プロパティを `Jackets` に変更します。  

    ![Items プロパティ](./media/add-images-pictures-audio-video/items-jackets.png)

    ギャラリーがそれらの画像で自動的に更新されます。  

    ![ジャケット画像](./media/add-images-pictures-audio-video/images.png)

    **Items** プロパティを設定すると、**PowerAppsId** という名前の列が Excel テーブルに自動的に追加されます。

    Excel テーブル内の画像のパスは、画像への URL にすることもできます。 例として、[Flooring Estimates](https://pwrappssamples.blob.core.windows.net/samples/FlooringEstimates.xlsx) サンプル ファイルがあります。 クラウド ストレージ アカウントにそれをダウンロードして、`FlooringEstimates` テーブルをアプリにデータ ソースとして追加し、ギャラリー コントロールを `FlooringEstimates` に設定できます。 ギャラリーがそれらの画像で自動的に更新されます。

## <a name="upload-pen-drawings-to-the-cloud"></a>ペン画をクラウドにアップロードする
このシナリオでは、データ ソース OneDrive for Business にペン画をアップロードする方法を説明し、ペン画をそこに格納する方法を確認します。

1. Excel で、**Image [image]** をセル A1 に追加します。

2. 次の手順を使用してテーブルを作成します。    

   1. セル A1 を選択します。

   2. **挿入**リボンで**テーブル**を選択します。

   3. ダイアログ ボックスで、**先頭行をテーブルの見出しとして使用する**を選択し、**OK** を選択します。

       ![テーブルの作成](./media/add-images-pictures-audio-video/create-table.png)

       Excel ファイルがテーブル形式になりました。 Excel のテーブルの書式設定の詳細については、[データをテーブルとして書式設定する](https://support.office.com/article/Format-an-Excel-table-6789619F-C889-495C-99C2-2F971C0E2370) を参照してください。

   4. テーブルに、**Drawings** と名前を付けます。

       ![テーブルの名前を Drawings に変更する](./media/add-images-pictures-audio-video/name-media-table.png)

3. Excel ファイルを **SavePen.xlsx** という名前で、OneDrive for Business に保存します。

4. Power Apps で[空のアプリ](get-started-create-from-blank.md) を作成します。

5. アプリで、[データ ソース](add-data-connection.md) として、OneDrive for Business アカウントを追加します。

   1. **表示**タブをクリックまたはタップし、**データ ソース**をクリックまたはタップします。

       ![](./media/add-images-pictures-audio-video/choose-data-sources.png)

   2. **データ ソースの追加**をクリックまたはタップして、**OneDrive for Business** をクリックまたはタップします。

       ![](./media/add-images-pictures-audio-video/select-source.png)

   3. **SavePen.xlsx** をクリックまたはタップします。

   4. **Drawings** テーブルを選択して、**接続**をクリックまたはタップします。

       ![連結](./media/add-images-pictures-audio-video/savepen.png)  

       Drawings テーブルが、データ ソースとして一覧表示されます。

6. **挿入**タブで、**テキスト**を選択し、**ペン入力**を選択します。

7. 新しいコントロールの名前を **MyPen** に変更します。  

    ![名前の変更](./media/add-images-pictures-audio-video/rename-mypen.png)

8. **挿入**タブで、**ボタン**コントロールを追加し、その **OnSelect** プロパティを次の数式に設定します。

    **Patch(Drawings, Defaults(Drawings), {Image:MyPen.Image})**

9. **画像**コントロール (**挿入** タブ > **ギャラリー**) を追加し、その **Items** プロパティを `Drawings` に設定します。 ギャラリー コントロールの **Image** プロパティが自動的に `ThisItem.Image` に設定されます。

    画面が次のようになるように、コントロールを配置します。  

    ![サンプル画面](./media/add-images-pictures-audio-video/screen.png)

10. F5 キーを押すか、プレビューを選択します ( ![[プレビュー] ボタン](./media/add-images-pictures-audio-video/preview.png) )。

11. MyPen で何かを描画し、ボタンを選択します。

    ギャラリー コントロールの最初の画像に、描画したものが表示されます。

12. 他の何かを絵に追加して、ボタンを選択します。

    ギャラリー コントロールの 2 番目の画像に、描画したものが表示されます。

13. Esc キーを押して、プレビュー ウィンドウを閉じます。

    クラウド ストレージ アカウントに、**SavePen_images** フォルダーが自動的に作成されています。 このフォルダーには、それぞれのファイル名の ID が付いた保存済の画像が含められます。 フォルダーを表示するには、F5 キーを押すなどして、ブラウザー ウィンドウを更新する必要がある場合があります。

    **SavePen.xlsx** で、**Image** 列に、新しい画像へのパスが指定されます。

### <a name="known-limitations"></a>既知の制限
組織内の Excel データを共有する方法については、[これらの制限を確認する](connections/cloud-storage-blob-connections.md#known-limitations) をご覧ください。

## <a name="for-more-information"></a>詳細情報
アプリを、[ブラウザー ウィンドウ](https://home.dynamics.com/) や電話などのさまざまなプラットフォームでテストしてください。

別のデータ ソースへの直接のマルチメディアのアップロードを含む高度なシナリオについては、[画像のキャプチャの高度なヒント](https://powerapps.microsoft.com/blog/image-capture-pro-tips/) および[画像アップロード用のカスタム コネクタ](https://powerapps.microsoft.com/blog/custom-api-for-image-upload/) を参照してください。

データ ソースにファイルをアップロードする別の方法は、[Patch](functions/function-patch.md) 関数を使用することです。

[1]: ./media/add-images-pictures-audio-video/add-image-video-audio-file.png
[3]: ./media/add-images-pictures-audio-video/add-intro-sound.png
[4]: ./media/add-images-pictures-audio-video/add-picture.png
[5]: ./media/add-images-pictures-audio-video/camera-gallery.png
[6]: ./media/add-images-pictures-audio-video/audio-gallery.png
[7]: ./media/add-images-pictures-audio-video/pen-gallery.png
[8]: ./media/add-images-pictures-audio-video/mediaoptions.png
[9]: ./media/add-images-pictures-audio-video/imageproperty.png
[10]: ./media/add-images-pictures-audio-video/mediaproperty.png
[11]: ./media/add-images-pictures-audio-video/renamecamera.png
