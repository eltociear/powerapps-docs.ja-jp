---
title: Download 関数 | Microsoft Docs
description: キャンバス アプリでの Download 関数の構文と例を含む参照情報
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
ms.openlocfilehash: 80d106667e0c13ab558123aded3788fc8004b22e
ms.sourcegitcommit: 0c92e85f95f3baa04cce140c96e53d5d86d685c0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "3333557"
---
# <a name="download-function-in-power-apps"></a>Power Apps での Download 関数

ローカル デバイスに Web からファイルをダウンロードします。

## <a name="description"></a>内容

**Download** 関数は、Web からローカル デバイスにファイルをダウンロードします。

ネイティブ プレイヤー (Windows、Android、および iOS) で、ユーザーはファイルを保存する場所を求められます。  

Web で使用する場合、**ダウンロード**はファイルで何が起こるか確認するためにブラウザーの設定に依存しています。 ブラウザーがネイティブでサポートする画像、ビデオ、およびその他のファイル タイプの場合、新しいブラウザー タブはファイルを表示するため開かれます。多くのブラウザーは、内容をローカルのファイル システムに保存することをサポートしています。

Windows でのみ、**ダウンロード**はファイルがテキスト文字列としてローカルに保存された場所を返します。

**ダウンロード**は[動作の数式](../working-with-formulas-in-depth.md) 内でのみ使用できます。

## <a name="syntax"></a>構文

**Download**( *Address* )

* *Address* – 必須。  ダウンロードする Web リソースの URL アドレス。

## <a name="examples"></a>例

### <a name="simple-download"></a>簡易なダウンロード

次の数式は、PDF ファイルの、Surface Book のユーザー ガイドをダウンロードします。

```powerapps-dot
Download( "https://go.microsoft.com/fwlink/?linkid=827480" )
```

モバイル デバイスで実行すると、ユーザーはファイルを保存する場所を求められます。  

ほとんどのブラウザーがこのファイルの種類をネイティブにサポートしているため、ほとんどの Web ブラウザーで実行する場合、新しいタブが開かれ、PDF ファイルが表示されます。 

### <a name="step-by-step"></a>手順

**製品ショーケース**タブレット レイアウト テンプレートは、次の例で使用されました。 このテンプレートを使用してアプリを作成するには、[アプリの作成](../get-started-test-drive.md) の記事の手順に従い、**製品ショーケース** テンプレートを選択します。 自分のアプリを使用することもできます。

1. [Power Apps](https://make.powerapps.com) に移動します。
1. 左側のナビゲーション ウィンドウから、**アプリ**を選択します。
1. アプリを選択し、**編集**を選択します。
1. メニューから**挿入**を選択し、**ラベル**を選択します。
1. ラベルを画面右下に移動します。
1. 右側のプロパティ ウィンドウから、**色**を*白*に選択し、**境界線の太さ**を *1* に設定します。
1. 右側から**Text** プロパティを選択し、テキストを*ダウンロード ユーザー ガイド*として入力します。
1. 左上のプロパティ リストから、**OnSelect** を選択します。
1. 数式を `Download("https://go.microsoft.com/fwlink/?linkid=827480")` と入力します。 他の使用したい URL を使用することもできます。

    ![ダウンロードの例](media/function-download/download-example-onselect.png "ダウンロードの例")

1. アプリを保存し、公開します。
1. アプリを再生します。
1. **ダウンロード ユーザー ガイド** ボタンを選択し、ガイドをダウンロードします。

> [!NOTE]
> ブラウザー設定により、ファイルをダウンロードするか、または新しいタブでファイルを直接開くか決定します。詳細については、[Download 関数の内容](#description) を参照してください。

### <a name="see-also"></a>関連項目

[キャンバス アプリの数式のリファレンス](../formula-reference.md)
