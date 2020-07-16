---
title: マルチメディア ファイルをキャンバス アプリに埋め込んでアップロードする | Microsoft Docs
description: キャンバス アプリでマルチメディア ファイルを表示して、それらをデータ ソースにアップロードする
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/21/2020
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9537d37fb4c4c8364df7110c19d7f02d194aac65
ms.sourcegitcommit: 8b08fdc6a2934648ae926ea62ebee4cdb578b651
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/22/2020
ms.locfileid: "3394920"
---
# <a name="using-multimedia-files-in-power-apps"></a>Power Apps でマルチメディア ファイルを使用する

画像、オーディオ、ビデオ ファイルをキャンバス アプリに追加できます。 [Microsoft Stream](https://docs.microsoft.com/stream/)、[Azure Media Services](https://docs.microsoft.com/azure/media-services/) などのストリーミングサービスや、YouTube などのサードパーティのストリーミング サービスからビデオを追加する。 または、**ペン入力** のような入力コントロールを使用して署名を収集します。

この記事では、マルチメディア、ストリーミング、入力制御のシナリオにおける作業について説明します。 この記事で使用しているデータ ソースは、OneDrive for Business の Excel ファイルです。

## <a name="prerequisites"></a>前提条件

Power Apps に[サインアップ](../signup-for-powerapps.md) し、サインアップに使用した同じ資格情報を使用して[サインイン](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) します。

## <a name="add-media-from-a-file-or-the-cloud"></a>ファイルまたはクラウドからメディアを追加する

追加するメディア ファイルの種類 (画像、ビデオ、オーディオなど) を選択できます。 メディア ペインまたは画像コントロールを使用して画像を追加できます。

![メディア ペイン](./media/add-images-pictures-audio-video/media-pane.gif "メディア ペイン")

### <a name="add-images-audio-or-video-using-the-media-pane"></a>メディア ペインを使用して画像、オーディオ、ビデオを追加する

ご利用のアプリで、**メディア** ペインを使用してメディアファイルを追加、削除するには :

1. 左側のパペインで **メディア** を選択します。

    ![メディア](./media/add-images-pictures-audio-video/media-panel.png "メディア")

1. メディア パネルから **アップロード**を選択します。

    ![メディアのアップロード](./media/add-images-pictures-audio-video/upload-media.png "メディアのアップロード")

1. 追加するファイルを選択して、**開く** を選択します。

1. メディア ペインからファイルを選択して、画面に挿入します。

    ![メディアを追加する](./media/add-images-pictures-audio-video/add-media.png "メディアを追加する")

1. アプリを[保存](save-publish-app.md#save-changes-to-an-app)して[公開](save-publish-app.md#publish-an-app)します。

1. 他のユーザーと[アプリを共有する](share-app.md)。

### <a name="add-images-audio-or-video-using-the-controls"></a>コントロールを使用して画像、オーディオ、ビデオを追加する

[画像](./controls/control-image.md)、[オーディオまたはビデオ](./controls/control-audio-video.md)コントロールを使用して画像、オーディオ、ビデオを追加するには :

1. 上部のメニューで **挿入** を選択します。

1. **メディア** ドロップダウンを選択します。

1. **画像**、**オーディオ**、**ビデオ**コントロールから選択します。

**画像**コントロールで、*画像*プロパティを、拡張子なしの画像ファイル名で更新します。 **オーディオ**または**ビデオ**コントロールで、*メディア* プロパティをファイル名、または YouTube の動画 URL などの URL をダブル クォーテーションを付加して更新します。

## <a name="add-media-from-azure-media-services"></a>Azure Media Services からメディアを追加する

1. Azure Media Services アカウントの **AMS > 設定 > 資産**から、ビデオ資産をアップロードして公開します。

1. 公開したら、ビデオの URL をコピーします。

1. Power Apps の**挿入 > メディア**から、**ビデオ** コントロールを追加します。

1. **Media** プロパティを、コピーした URL に設定します。

    次の図に示すように、Azure Media Services がサポートするすべてのストリーミング URL を選択できます。

    ![Media プロパティの設定](./media/add-images-pictures-audio-video/ams-with-powerapps.png)

1. アプリを[保存](save-publish-app.md#save-changes-to-an-app)して[公開](save-publish-app.md#publish-an-app)します。

1. 他のユーザーと[アプリを共有する](share-app.md)。

## <a name="add-microsoft-stream-media"></a>Microsoft Stream メディアを追加する

Microsoft Streamビデオコントロールの追加方法の詳細については、[Microsoft Stream ビデオ コントロールの例](controls/control-stream-video.md#example)に移動します。

## <a name="add-images-from-the-cloud-to-your-app"></a>クラウドからアプリに画像を追加する

このシナリオでは、クラウド ストレージ アカウントの OneDrive for Business に画像を保存します。 Excel テーブルを使用して画像へのパスを含め、アプリのギャラリー コントロールにその画像を表示します。

このシナリオでは、いくつかの .jpeg ファイルを含む [CreateFirstApp.zip](https://pwrappssamples.blob.core.windows.net/samples/CreateFirstApp.zip) を使用します。

> [!NOTE]
> Excel ファイル内のこれらの画像へのパスには、スラッシュを使用する必要があります。 Power Apps で Excel テーブルに画像のパスを保存すると、パスに円記号が使われます。 このようなテーブルからの画像のパスを使用する場合は、Excel テーブル内のパスを円記号ではなくスラッシュを使用するように変更します。 そうしないと、画像は表示されません。  

1. [CreateFirstApp.zip](https://pwrappssamples.blob.core.windows.net/samples/CreateFirstApp.zip) をダウンロードし、**Assets** フォルダーをクラウド ストレージ アカウントに抽出します。

1. **Assets** フォルダーの名前を **Assets_images** に変更します。

1. Excel スプレッドシートに 1 列のテーブルを作成し、次のデータを入力します。

    ![Jackets テーブル](./media/add-images-pictures-audio-video/jackets.png)

    **ビジネス向け OneDrive** からファイル パスをコピーするには、ファイルを選択してから、続いて画面右側の詳細ペインから **パス** (*直接リンクをコピー*) を選択します。

1. テーブルに **Jackets** と名前を付け、Excel ファイルに **Assets.xlsx** と名前を付けます。

1. ご利用のアプリで、[データ ソース](add-data-connection.md)として**Jackets** テーブルを追加します。  

1. 必要に応じて、アプリの[オリエンテーション](set-aspect-ratio-portrait-landscape.md)を横方向に更新します。

1. **挿入** > **ギャラリー** を選択し、続いて **水平方向** を選択します。

1. 必要に応じて、テキスト フィールドを選択してから最初の画像の下部の見出しフィールドを選択し、それらを削除して画像のみを画面に表示します。

    ![フィールドの削除](./media/add-images-pictures-audio-video/delete-fields.png)

    数式エラーが表示された場合は、**Ctrl + Z**を押下して削除を元に戻します。最初に*サブタイトル* フィールドを削除し、続いて *タイトル* フィールドを削除するようにしてください。

1. ギャラリーの **アイテム** プロパティを `Jackets` に設定します。

    ![Items プロパティ](./media/add-images-pictures-audio-video/items-jackets.png)

1. ギャラリーの最初の画像を選択し、**画像**プロパティを `ThisItem.Images` に設定します :

    ![アイテム画像](./media/add-images-pictures-audio-video/image-this-item.png)

    ギャラリーがそれらの画像で自動的に更新されます。  

    ![ジャケット画像](./media/add-images-pictures-audio-video/images.png)

    **Items** プロパティを設定すると、**PowerAppsId** という名前の列が Excel テーブルに自動的に追加されます。

1. アプリを[保存](save-publish-app.md#save-changes-to-an-app)して[公開](save-publish-app.md#publish-an-app)します。

1. 他のユーザーと[アプリを共有する](share-app.md)。

## <a name="upload-pen-drawings-to-the-cloud"></a>ペン画をクラウドにアップロードする

このシナリオでは、データ ソース OneDrive for Business にペン画をアップロードする方法を説明し、ペン画をそこに格納する方法を確認します。

1. Excel で、**Image [image]** をセル A1 に追加します。

1. 次の手順を使用してテーブルを作成します。

   1. セル A1 を選択します。

   1. **挿入**リボンで**テーブル**を選択します。

   1. ダイアログ ボックスで、**先頭行をテーブルの見出しとして使用する**を選択し、**OK** を選択します。

       ![テーブルの作成](./media/add-images-pictures-audio-video/create-table.png)

       Excel ファイルがテーブル形式になりました。 Excel の表の書式設定の詳細については、[テーブルの書式を設定する](https://support.office.com/article/Format-an-Excel-table-6789619F-C889-495C-99C2-2F971C0E2370) を参照してください。

   1. テーブルに、**Drawings** と名前を付けます。

       ![テーブルの名前を Drawings に変更する](./media/add-images-pictures-audio-video/name-media-table.png)

1. Excel ファイルを **SavePen.xlsx** という名前で、OneDrive for Business に保存します。

1. Power Apps で、タブレット レイアウトで[空白のアプリ](get-started-create-from-blank.md)を作成します。

1. アプリで、[データ ソース](add-data-connection.md) として、OneDrive for Business アカウントを追加します。

   1. **ビュー** メニューを選択し、 **データ ソース**を選択します。

       ![データ ソースの選択](./media/add-images-pictures-audio-video/choose-data-sources.png)

   1. **データ ソースの追加**を選択し、**ビジネス向け OneDrive** を選択します。

   1. **SavePen.xlsx** を選択します。

   1. **図面** テーブルを選択して、**接続** を選択します。

       ![連結](./media/add-images-pictures-audio-video/savepen.png)  

       Drawings テーブルが、データ ソースとして一覧表示されます。

1. **挿入** > **入力**を選択し、続いて**ペン入力**を選択します。

1. 新しいコントロールの名前を **MyPen** に変更します。  

    ![名前の変更](./media/add-images-pictures-audio-video/rename-mypen.png)

1. **挿入**タブで、**ボタン**コントロールを追加し、その **OnSelect** プロパティを次の数式に設定します。

    **Patch(Drawings, Defaults(Drawings), {Image:MyPen.Image})**

    ![OnSelect ボタン](./media/add-images-pictures-audio-video/button-on-select.png)

1. **横型**ギャラリー コントロールを追加します (**インサート**タブ > **ギャラリー**)。

1. 必要に応じて、テキスト フィールドを選択してから最初の画像の下部の見出しフィールドを選択し、それらを削除して画像のみを画面に表示します。

    ![フィールドの削除](./media/add-images-pictures-audio-video/delete-fields.png)

    数式エラーが表示された場合は、**Ctrl + Z**を押下して削除を元に戻します。最初に*サブタイトル* フィールドを削除し、続いて *タイトル* フィールドを削除するようにしてください。

1. ギャラリーの **アイテム** プロパティを `Drawings` に設定します。 ギャラリー コントロールの **Image** プロパティが自動的に `ThisItem.Image` に設定されます。

    画面が以下のようになるように、コントロールを配置します :  

    ![サンプル画面](./media/add-images-pictures-audio-video/screen.png)

1. F5 キーを押すか、プレビューを選択します ( ![[プレビュー] ボタン](./media/add-images-pictures-audio-video/preview.png) )。

1. MyPen で何かを描画し、ボタンを選択します。

    ギャラリー コントロールの最初の画像に、描画したものが表示されます。

1. 他の何かを絵に追加して、ボタンを選択します。

    ギャラリー コントロールの 2 番目の画像に、描画したものが表示されます。

1. Esc キーを押して、プレビュー ウィンドウを閉じます。

    クラウド ストレージ アカウントに、**SavePen_images** フォルダーが自動的に作成されています。 このフォルダーには、それぞれのファイル名の ID が付いた保存済の画像が含められます。 フォルダーを表示するには、F5 キーを押すなどして、ブラウザー ウィンドウを更新する必要がある場合があります。

    > [!NOTE]
    > Excel のファイル名が異なる場合は、フォルダー名が異なる場合があります。 たとえば、ファイル名が Pen.xlsx の場合、フォルダ名は Pen_images になります。

    **SavePen.xlsx** で、**Image** 列に、新しい画像へのパスが指定されます。

1. アプリを[保存](save-publish-app.md#save-changes-to-an-app)して[公開](save-publish-app.md#publish-an-app)します。

1. 他のユーザーと[アプリを共有する](share-app.md)。

## <a name="known-limitations"></a>既知の制限

- アプリの読み込み中のパフォーマンスを向上させる目的で、次のサイズ制限が適用されます :
    - アプリにアップロードされるすべてのメディア ファイルの合計サイズは 200 MB を超えることはできません。
    - アプリ内の個々のメディア ファイルの最大サイズは 64 MB を超えることはできません。
- 対応しているメディアの種類は次のとおりです : `.jpg, .jpeg, .gif, .png, .bmp, .tif, .tiff, .svg, .wav, .mp3, .mp4, .wma, .wmv`
- [クラウドストレージの既知の制限](connections/cloud-storage-blob-connections.md#known-limitations)は、アプリをクラウドベースのストレージに接続する際に適用されます。

## <a name="see-also"></a>関連項目

- [コントロールのリファレンス](reference-properties.md)
- [計算式を使用する](working-with-formulas.md)