---
title: Char 関数 | Microsoft Docs
description: Power Apps での Char 関数の構文と例を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/01/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 578e196bfa55f33416de1ee551d1e63e106a612a
ms.sourcegitcommit: ed583eb94720a9645bfd79776311792a958077b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/01/2020
ms.locfileid: "3307994"
---
# <a name="char-function-in-power-apps"></a>Power Apps の Char 関数

文字コードを文字列に変換します。

## <a name="description"></a>内容

**Char**関数は、数値を対応する ASCII 文字を含む文字列に変換します。

## <a name="syntax"></a>構文

**Char**( *CharacterCode* )

- *CharacterCode* - 必須。 変換する ASCII 文字コード。

## <a name="examples"></a>例

| 計算式 | 内容 | 結果 |
| --- | --- | --- |
| **Char( 65 )** |ASCII コード 65 に対応する文字を返します。 |"A" |
| **Char( 105 )** |ASCII コード 105 に対応する文字を返します。 |"i" |
| **Char( 35 )** |ASCII コード 35 に対応する文字を返します。 |"#" |

### <a name="display-a-character-map"></a>文字マップを表示する

1. タブレット アプリの空の画面で、**横方向 (空)** レイアウトの [**Gallery**](../controls/control-gallery.md) コントロールを追加し、次のプロパティを設定します。

    - **Items**: `[0,1,2,3,4,5,6,7]`
    - **Width**: 800
    - **Height**: 500
    - **TemplateSize**: 100
    - **TemplatePadding**: 0

1. そのギャラリー内で、**横方向 (空)** レイアウトの **Gallery** コントロールを追加し、次のプロパティを設定します。

    - **Items**: `ForAll( [0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15], Value + ThisItem.Value * 16 )`
    - **Width**: 100
    - **Height**: 500
    - **TemplateSize**: 30
    - **TemplatePadding**: 0

    **Items** プロパティの値は、最初のギャラリー (`ThisItem.Value` 内の 0-7) の **Items** プロパティの 値列によって提供される列番号で 16 を乗算します。 次に、式は 2 番目のギャラリーの行番号の 1 つに結果を追加します ([**ForAll**](function-forall.md) 関数が提供するレコード スコープの 0-15)。

1. 2番目 (垂直方向) のギャラリー内に、**Label** コントロールを追加し、次のプロパティを設定します。

    - **Text**: `ThisItem.Value`
    - **Width**: 50

1. 2番目 (垂直方向) のギャラリー内に、別の **Label** コントロールを追加し、次のプロパティを設定します。

    - **Text**: `Char( ThisItem.Value )`
    - **Width**: 50
    - **X**: 50

最初の 128 ASCII 文字のチャートを作成しました。 小さな四角で表示される文字は印刷できません。

![最初の 128 ASCII 文字](media/function-char/chart-lower.png)

ASCII 拡張文字を表示するには、この式の 2 番目のギャラリーの **Items** プロパティを設定します。これにより、各文字値に 128 が追加されます。

`ForAll( [0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15], Value + ThisItem.Value * 16 + 128)`

![ASCII 拡張文字](media/function-char/chart-higher.png)

別のフォントで文字を表示するには、2 つ目のラベル **Font** プロパティを、**'Dancing Script'** などの値に設定します。

![Dancing Script](media/function-char/chart-higher-dancing-script.png)
