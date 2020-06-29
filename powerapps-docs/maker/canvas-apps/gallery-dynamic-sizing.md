---
title: ギャラリーで異なる高さのアイテムを表示する | Microsoft Docs
description: 高さ調整可能なギャラリーを追加し、自動でギャラリーの各アイテムのコンテンツの分量に合わせるように構成する
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/01/2017
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 712d7ed6166b2ea655a086b1f9a4416af1e8065f
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2019
ms.locfileid: "3304291"
---
# <a name="show-items-of-different-heights-in-a-power-apps-gallery"></a>Power Apps ギャラリーで異なる高さのアイテムを表示する
データ セットの各アイテムの同一フィールドに含まれるデータ量が異なる場合、含まれるデータを量が少ないアイテムの後にスペースを挿入しなくても、データ量が多いアイテムの全体を表示することができます。 **伸縮可能な高さ**ギャラリー コントロールを追加し、次の操作を行えるように構成します。

* コンテンツに合わせて伸縮するように **Label** コントロールを構成する。
* 各コントロールを、上にあるコントロールのすぐ下に自動で表示されるように配置します。

このチュートリアルでは、**伸縮可能な高さ**ギャラリー コントロールにフローリング製品に関するデータを表示します。 各製品画像は、概要の行数が 5 行と 2 行のどちらの場合でも概要の 5 ピクセル下に表示します。

![完成版のアプリ](./media/gallery-dynamic-sizing/dynamic-app.png)

**推奨記事**

ギャラリーにコントロールを追加したことがない場合は、このトピックの先へ進む前に「[アイテムのリストの表示](add-gallery.md)」の手順を参照してください。

## <a name="add-data-to-a-blank-app"></a>空のアプリにデータを追加する
1. [この Excel ファイル](https://az787822.vo.msecnd.net/documentation/get-started-from-data/FlooringEstimates.xlsx) をダウンロードします。このファイルには、フローリング製品の名前、概要、画像へのリンクが含まれています。

    ![フローリング製品](./media/gallery-dynamic-sizing/flooring-products.png)

2. Excel ファイルを、OneDrive、Dropbox、Google Drive などのクラウド ストレージ アカウントにアップロードします。

3. Power Apps Studio で、**ファイル** メニューの**新規**をクリックまたはタップします。

4. **空のアプリ** タイルで、**携帯電話レイアウト** をクリックまたはタップします。

    ![ファイル メニューの新しいオプション](./media/gallery-dynamic-sizing/blank-app.png)

5. Excel ファイル内の **FlooringEstimates** テーブルへの接続を追加します。

    詳細については、「[接続の追加](add-data-connection.md)」を参照してください。

## <a name="add-data-to-a-gallery"></a>ギャラリーにデータを追加する
1. **挿入**タブの**ギャラリー**をクリックまたはタップし、**伸縮可能な高さ**をクリックまたはタップします。

    ![ギャラリーを追加する](./media/gallery-dynamic-sizing/add-flexible.png)
2. スクリーン全体を占めるようにギャラリーのサイズを変更します。

3. ギャラリーの **[Items](controls/properties-core.md)** プロパティを **FlooringEstimates** に設定します。

## <a name="show-the-product-names"></a>製品名を表示する
1. ギャラリーの左上隅にある鉛筆アイコンをクリックまたはタップして、ギャラリー テンプレートを選択します。

    ![鉛筆のアイコン](./media/gallery-dynamic-sizing/edit-template.png)

2. ギャラリー テンプレートを選択した状態で、**[Label](controls/control-text-box.md)** コントロールを追加します。

3. **Label** コントロールの **Text** プロパティに次の式を設定します。<br>
   **ThisItem.Name**

    ![ラベルの追加](./media/gallery-dynamic-sizing/add-text-box.png)

## <a name="show-the-product-overviews"></a>製品の概要を表示する
1. ギャラリー テンプレートを選択した状態で、別の **Label** コントロールを追加し、1 番目の **Label** コントロールの下に移動させます。  

2. 2 番目の **Label** コントロールの **Text** プロパティに、次の式を設定します。<br> **ThisItem.Overview**

3. 2 番目の **Label** コントロールを選択した状態で、**コンテンツ** タブの名前タグ アイコンをクリックまたはタップし、コントロールの名前を **OverviewText** に変更します。

    ![ラベルの名前を変更する](./media/gallery-dynamic-sizing/rename-text-box.png)

4. **OverviewText** ボックスの **AutoHeight** プロパティを **true** に設定します。

    この手順により、ボックスがそのコンテンツに合わせて伸縮するようになります。

      ![テキストの高さの自動設定](./media/gallery-dynamic-sizing/autoheight-text.png)

## <a name="show-the-product-images"></a>製品画像を表示する
1. テンプレートのサイズを、高さが 2 倍になるように変更します。

    アプリの作成時にテンプレートへコントロールを追加しやすくなりました。この変更はアプリの実行時の見た目に影響しません。

2. ギャラリー テンプレートを選択した状態で、**[Image](controls/control-image.md)** コントロールを追加し、**OverviewText** ボックスの下に移動させます。

3. **Image** コントロールの **Image** プロパティに次の式を設定します。<br>
    **ThisItem.Image**

4. 次の式のように、**OverviewText** ボックスの位置とサイズを基に **Image** コントロールの **[Y](controls/properties-core.md)** プロパティを設定します。
   <br>**OverviewText.Y + OverviewText.Height + 5**

    ![完成版のアプリ](./media/gallery-dynamic-sizing/final-app.png)

他のコントロールを追加する場合も考え方は同じです。各コントロールの **Y** プロパティを、その上にあるコントロールの **Y** プロパティと **Height** プロパティに基づいて設定します。

## <a name="next-steps"></a>次の手順
[ギャラリー](working-with-forms.md) コントロールと[数式](working-with-formulas.md) の使用方法について説明します。
