---
title: Power Apps ポータルのテーマ概要 | Microsoft Docs
description: Power Apps ポータルのテーマ概要。
author: neerajnandwana-msft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 04/28/2020
ms.author: nenandw
ms.reviewer: tapanm
ms.openlocfilehash: 3aba469224a5e980a8c402f632974a54a8b90141
ms.sourcegitcommit: 2fd873a1ea17f419f6194714efffa47a9bd00c2e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "3507678"
---
# <a name="overview-of-themes-in-power-apps-portals"></a>Power Apps ポータルのテーマ概要

Power Apps ポータルで、**基本テーマの有効化**機能は**オフ**に設定します。 この機能をオンにすると、**プリセット**と呼ばれる既定のテーマを使用できます。 カスタマイズ追加のために、プリセットテーマのコピーを作成することもできます。

この記事では、基本的なテーマ機能について説明します。 高度なテーマのカスタマイズについては、[編集CSS](edit-css.md) を参照してください。

> [!IMPORTANT]
> 基本的なテーマ機能はプレビュー段階です。 プレビュー機能の詳細については、[実験とプレビュー機能についてPower Apps](https://docs.microsoft.com/powerapps/maker/canvas-apps/working-with-experimental-preview) を参照してください。

## <a name="enable-basic-themes-for-existing-portals-preview"></a>既存ポータルの基本テーマを有効にする (プレビュー)

[このトピックはプレリリース ドキュメントであり、変更されることがあります。]

1. [Power Apps](https://make.powerapps.com) にサインインします。

1. 左側のナビゲーション ウィンドウで、**アプリ**を選択し、ポータルを選択します。

    ![アプリとポータルを選択](./media/theme-overview/select-app-portal.png "アプリとポータルを選択する")

1. **その他のコマンド** (**...**)を選択し、**編集**を選択します。

    ![ポータルの編集](./media/theme-overview/edit-portal.png "ポータルを編集する")

1. 左側のナビゲーション ウィンドウから、**テーマ**を選択し、**基本テーマの有効化**切り替えをオンにします。

    ![基本テーマの有効化](./media/theme-overview/enable-basic-theme.png "基本テーマを有効化する")

## <a name="change-theme-for-your-portal"></a>ポータル用テーマを変更する

ポータルの既存テーマをデフォルト テーマに設定できます。

1. [Power Apps](https://make.powerapps.com) にサインインします。

1. 左側のナビゲーション ウィンドウで、**アプリ**を選択し、ポータルを選択します。

1. **その他のコマンド** (**...**)を選択し、**編集**を選択します。

1. **テーマ**をコンポーネント ウィンドウから選択します。

    ![テーマ アイコンの選択](./media/theme-overview/select-theme.png "テーマ アイコンを選択する")

1. 利用可能なプリセットからデフォルトのテーマを選択します (この例では、**緑**を選択しました)。

    ![既定テーマの選択](./media/theme-overview/basic-theme.png "既定テーマを選択する")

選択されているテーマがポータルに適用されます。

![適用されたテーマ](./media/theme-overview/theme-applied.png "適用されたテーマ")

## <a name="create-a-new-theme"></a>新しいテーマを作成します

1. [Power Apps](https://make.powerapps.com) にサインインします。

1. 左側のナビゲーション ウィンドウで、**アプリ**を選択し、ポータルを選択します。

1. **その他のコマンド** (**...**)を選択し、**編集**を選択します。

1. **テーマ**をコンポーネント ウィンドウから選択します。

1. **新しいテーマ**を選択します。

    ![新しいテーマを作成します](./media/theme-overview/new-theme.png "新しいテーマを作成します")

## <a name="edit-theme-details"></a>テーマの詳細を編集する

テーマ名、説明、色、その他のタイポグラフィ設定を Power Apps Studio で更新できます。 

1. [Power Apps](https://make.powerapps.com) にサインインします。

1. 左側のナビゲーション ウィンドウで、**アプリ**を選択し、ポータルを選択します。

1. **その他のコマンド** (**...**)を選択し、**編集**を選択します。

1. **テーマ**をコンポーネント ウィンドウから選択します。

1. 現在適用されているテーマを選択するか、プリセットから新しいテーマを選択します。
   テーマを選択すると、ワークスペースの右側に詳細ウィンドウが開きます。

    ![テーマの詳細](./media/theme-overview/theme-details.png "テーマの詳細")

1. さまざまな領域の名前、説明、色などのテーマの詳細を編集します。

    |色のオプション | 影響を受ける領域 |
    | --- | ---  |
    | 基本 | ボタンとリンクの色。 |
    | ヘッダー​​ | ヘッダー背景色。 |
    | ヘッダー メニューのテキスト | ヘッダーメニューのテキストの色。 |
    | ヘッダー メニュー ホバー | カーソルを置いた時のメニュー項目の背景色。 |
    | 本文背景 |  本体セクションの背景色。 |
    | フッター背景 | フッターの背景色。 |
    | フッター テキスト | フッターのテキストの色。 |

1. 変更を保存して公開します。

## <a name="copy-a-preset-theme"></a>プリセット テーマをコピーする

1. [Power Apps](https://make.powerapps.com) にサインインします。

1. 左側のナビゲーション ウィンドウで、**アプリ**を選択し、ポータルを選択します。

1. **その他のコマンド** (**...**)を選択し、**編集**を選択します。

1. **テーマ**をコンポーネント ウィンドウから選択します。

1. コピーするプリセットからテーマを選択し、**...** を選択してから、次に**コピーとして保存**を選択します。

    ![ プリセット テーマをコピーする](./media/theme-overview/copy-preset-theme.png "プリセット テーマをコピーする")

1. 前のセクションで説明したようにテーマの詳細を更新してから、テーマを保存します。

## <a name="sass-variables"></a>サス変数

[サス](https://sass-lang.com/) は完全な CSS-互換構文を備えたスタイルシート言語です。 基本テーマ機能を有効にすると、値の代わりにテーマの色を構成して、[サス変数](https://sass-lang.com/documentation/variables) を使用できます。

たとえば、**ヘッダー**色を**プライマリー**色より 25％ 明るくする場合、特定の色の代わりに次の値を使用できます。

```
lighten($primaryColor, 25%);
```

![サス例](./media/theme-overview/sass-example.png "サス例")

基本テーマで次のサス変数を使用できます。

|色のオプション | サス変数名 |
| - | - |
| 基本 | ```$primaryColor``` |
| ヘッダー​​ | ```$headerColor``` |
| ヘッダー メニューのテキスト | ```$headerMenuTextColor``` |
| ヘッダー メニュー ホバー | ```$headerMenuHoverColor``` |
| 本文背景 |  ```$bodyBackground``` |
| フッター背景 | ```$footerColor``` |
| フッター テキスト | ```$footerTextColor``` |

### <a name="sass-variable-order"></a>サス変数順序

サス変数は上から下に機能します。 *ヘッダー*の色に ```lighten($primaryColor, 25%);``` を設定できます。 ただし、*ヘッダー*はカラー オプション リストで以下の*プライマリー*なので、*プライマリー*色を ```lighten($headerColor, 25%);``` に設定できません。

## <a name="basic-theme-considerations"></a>基本テーマに関する考慮事項

- 同じテーマ名または同じテーマ ファイル名を持つ 2 つのテーマを使用することはできません。 
- 手動で入力する色の値は、有効な色である必要があります。
- プリセット テーマの CSS 変更はサポートされていません。
- アクセスを可能にするために、推奨されるテーマの前景色と背景色のコントラスト比は 4.5:1 です。

### <a name="next-steps"></a>次のステップ

[テーマ CSS を編集する](edit-css.md)
