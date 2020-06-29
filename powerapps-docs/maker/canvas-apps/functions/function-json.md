---
title: JSON 関数 | Microsoft Docs
description: Power Apps での JSON 関数の構文を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/02/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0780280298041aede5b24a9a819aa2743584f8c8
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3304981"
---
# <a name="json-function-in-power-apps"></a>Power Apps の JSON 関数

テーブル、レコード、または値の JSON テキスト文字列を生成します。

## <a name="description"></a>内容

**JSON** 関数は、テキストとしてデータ構造の JavaScript Object Notation (JSON) 表現を返すため、ネットワーク間での保存や送信に適しています。 [ECMA-404](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-404.pdf) および[IETF RFC 8259](https://tools.ietf.org/html/rfc8259) は JavaScript や他のプログラミング言語で広く使用されている形式について説明します。

キャンバス アプリは、このテーブルがテキスト表現についての詳細とともにリストする[データ型](data-types.md) をサポートします:

| データの種類 | 内容 | 結果の例 |
|-----------|-------------|---------|
| **Boolean** | *true* または *false*. | `true` |
| **色** | 色の 8 桁の16 進数表現を含む文字列。 この表現は、#*rrggbbaa* 形式をとります。*rr* が赤のコンポーネント、*gg* が緑、*bb* が青、*aa* がアルファ チャネルです。 アルファ チャネルの場合、**00** は完全に透明であり、**ff** は完全に不透明です。 文字列を[**ColorValue**](function-colors.md) 関数に渡すことができます。  | `"#102030ff"` |
| **通貨** | ユーザーの言語に適切な小数点を使用する数値。 必要に応じて指数表記が使用されます。 | `1.345` |
| **日付** | ISO 8601**yyyy-mm-dd** 形式の日付を含む文字列。 | `"2019-03-31"` |
| **DateTime** | ISO 8601 の日付/時刻を含む文字列。 末尾の「Z」が示すように、日付/時刻の値は UTC です。  | `"2019-03-31T22:32:06.822Z"`  |
| **GUID** | GUID 値を含む文字列。 文字は小文字です。 | `"751b58ac-380e-4a04-a925-9f375995cc40"`
| **イメージ、メディア** | **IncludeBinaryData** が指定されている場合、メディア ファイルは文字列にエンコードされます。 http: または https: URL スキームを使用する Web 参照は変更されません。 メモリ内データの参照は、[「data:*mimetype*; base64,...」](https://en.wikipedia.org/wiki/Data_URI_scheme) 形式とともにエンコードされます。 メモリ内データには、ユーザーが[**Camera**](../controls/control-camera.md) コントロールと appres: および BLOB: URL スキームでのその他の参照を使用してキャプチャする画像を含みます。| `"data:image/jpeg;base64,/9j/4AA..."` |
| **番号** | ユーザーの言語に適切な小数点を使用する数値。 必要に応じて指数表記が使用されます。 | `1.345` |
| **オプション &nbsp; 設定** | 表示に使用されるラベルではなく、オプション セットの数値。 この数値は、言語に依存しないため使用されます。  | `1001` |
| **時刻** | ISO 8601 *hh:mm:ss.fff* 形式を含む文字列。  | `"23:12:49.000"` |
| **Record** | フィールドとその値の **{** および **}** 間のコンマ区切りのリスト。 この表記はキャンバス アプリのレコードの表記に似ていますが、名前は常に二重引用符間にあります。 この形式は、多対一関係に基づくレコードをサポートしていません。  | `{ "First Name": "Fred", "Age": 21 }` |
| **Table** | レコードの **[** および **]** 間のコンマ区切りのリスト。 この形式は、多対一関係に基づくテーブルをサポートしていません。  | `[ { "First Name": "Fred", "Age": 21 }, { "First Name": "Jean", "Age": 20 } ]` |
| **2&nbsp; オプション** | 表示に使用されるラベルではなく、*true* または *false* の 2 つのオプションのブール値。 言語に依存しないため、ブール値が使用されます。 | `false` |
| **ハイパーリンク、テキスト** | 二重引用符の間の文字列。 この関数は、埋め込まれた二重引用符をバックスラッシュでエスケープし、改行を「\n」に置き換え、他の標準 JavaScript の置き換えを行います。 | `"This is a string."` |

結果の読み取り方法と、サポートされていないおよびバイナリ データの種類の処理方法を制御するために、任意の*形式*引数を指定します。 既定では、出力は不要なスペースや改行なしで可能な限りコンパクトであり、サポートされていないデータの種類とバイナリ データは許可されません。 **&** 演算子を指定する場合、複数の形式を組み合わせることができます。

| JSON 形式列挙型 | 内容 |
|-----------------|-------------|
| **コンパクト** | 既定。  出力は、スペースや改行を追加せず、可能な限りコンパクトです。 |
| **IndentFour** | 読みやすくするために、出力には各列と入れ子レベルの改行が含まれ、インデント レベルごとに 4 つのスペースが使用されます。 |
| **IncludeBinaryData** | 結果には、イメージ、ビデオ、およびオーディオ クリップ列が含まれます。 この形式は、結果のサイズが大幅に増加し、アプリのパフォーマンスが低下する可能性があります。 |
| **IgnoreBinaryData** | 結果には、イメージ、ビデオ、またはオーディオ クリップ列が含まれません。 **IncludeBinaryData** も **IgnoreBinaryData** も指定しない場合、この関数はバイナリ データを検出するとエラーを生成します。 |
| **IgnoreUnsupportedTypes** | サポートされていないデータの種類は許可されますが、結果はそれらを含みません。 既定では、サポートされていないデータの種類はエラーを生成します。 |

結果を含むデータを制御し、サポートされていないデータの種類を削除するために、[**ShowColumns** および **DropColumns**](function-table-shaping.md) 関数を使用します。

**JSON** はメモリおよびコンピューティング処理となる可能性があるため、この関数は、[動作関数](../working-with-formulas-in-depth.md) でのみ使用します。 **JSON** からの結果を[変数](../working-with-variables.md) にキャプチャして、データ フローで使用できます。

列に表示名と論理名の両方がある場合、結果には論理名が含まれます。 表示名はアプリ ユーザーの言語を反映するため、一般的なサービスへのデータ転送には不適切です。

## <a name="syntax"></a>構文

**JSON**( *DataStructure* [, *Format* ] )

* *DataStructure* – 必須。 JSON に変換するデータ構造。  テーブル、レコード、およびプリミティブ値がサポートされ、任意に入り子にされます。
* *形式* - 任意。  **JSONFormat** 列挙値。 既定値は**コンパクト**で、改行またはスペースを追加せず、バイナリ データとサポートされていない列をブロックします。

## <a name="examples"></a>例

### <a name="hierarchical-data"></a>階層データ

1. [**Button**](../controls/control-button.md) コントロールを挿入し、**OnSelect** プロパティに次の数式を設定します。

    ```powerapps-dot
    ClearCollect( CityPopulations,
        { City: "London",    Country: "United Kingdom", Population: 8615000 },
        { City: "Berlin",    Country: "Germany",        Population: 3562000 },
        { City: "Madrid",    Country: "Spain",          Population: 3165000 },
        { City: "Hamburg",   Country: "Germany",        Population: 1760000 },
        { City: "Barcelona", Country: "Spain",          Population: 1602000 },
        { City: "Munich",    Country: "Germany",        Population: 1494000 }
    );
    ClearCollect( CitiesByCountry, GroupBy( CityPopulations, "Country", "Cities" ) )
    ```

1. Alt キーを押しながら、ボタンを選択します。

    **CitiesByCountry** コレクションは、このデータ構造で作成されます。**ファイル** メニューの**コレクション**を選択した後、コレクションの名前を選択すると表示できます。

    > [!div class="mx-imgBorder"]
    > ![CitiesByCountry コレクション](media/function-json/cities-grouped.png)

    **ファイル** > **アプリの設定** > **詳細設定** > **数式バーの結果ビューを有効にする**を選択し、数式バーでコレクションの名前を選択し、数式バーの下でコレクションの名前の横にある下矢印を選択して、このコレクションを表示することもできます。

    > [!div class="mx-imgBorder"]
    > ![数式バーの結果ビューのコレクション](media/function-json/cities-grouped-resultview.png)

1. 別のボタンを挿入し、**OnSelect** プロパティに次の数式を設定します:

    ```powerapps-dot
    Set( CitiesByCountryJSON, JSON( CitiesByCountry ) )
    ```

    この数式はグローバル変数 **CitiesByCountryJSON** を **CitiesByCountry** の JSON 表現に設定します。

1. Alt キーを押しながら、ボタンを選択します。

1. [**Label**](../controls/control-text-box.md) コントロールを挿入し、その **Text** プロパティを次の変数に設定します。

    ```powerapps-dot
    CitiesByCountryJSON
    ```

    ラベルはこの結果を、すべてスペースなしの 1 行で示し、ネットワークを介した送信に適しています。

    ```json
    [{"Cities":[{"City":"London","Population":8615000}],"Country":"United Kingdom"},{"Cities":[{"City":"Berlin","Population":3562000},{"City":"Hamburg","Population":1760000},{"City":"Munich","Population":1494000}],"Country":"Germany"},{"Cities":[{"City":"Madrid","Population":3165000},{"City":"Barcelona","Population":1602000}],"Country":"Spain"}]
    ```

1. 出力をより読みやすくするため、2 番目のボタンの数式を変更します。

    ```powerapps-dot
    Set( CitiesByCountryJSON, JSON(CitiesByCountry, JSONFormat.IndentFour ))
    ```

1. Alt キーを押しながら 2 つ目のボタンを選択します。

    ラベルは、より読みやすい結果を示します。

    ```json
    [
        {
            "Cities": [
                {
                    "City": "London",
                    "Population": 8615000
                }
            ],
            "Country": "United Kingdom"
        },
        {
            "Cities": [
                {
                    "City": "Berlin",
                    "Population": 3562000
                },
                {
                    "City": "Hamburg",
                    "Population": 1760000
                },
                {
                    "City": "Munich",
                    "Population": 1494000
                }
            ],
            "Country": "Germany"
        },
        {
            "Cities": [
                {
                    "City": "Madrid",
                    "Population": 3165000
                },
                {
                    "City": "Barcelona",
                    "Population": 1602000
                }
            ],
            "Country": "Spain"
        }
    ]
    ```

### <a name="images-and-media-in-base64"></a>Base64 のイメージおよびメディア

1. [**画像**](../controls/control-image.md) コントロールを追加します。

    このコントロールは **SampleImage** を提供します。

1. [**Button**](../controls/control-button.md) コントロールを追加し、その **OnSelect** プロパティを次の数式に設定します。

    ```powerapps-dot
    Set( ImageJSON, JSON( SampleImage, JSONFormat.IncludeBinaryData ) )
    ```

1. Alt キーを押しながら、ボタンを選択します。

1. ラベルを追加し、その **Text** プロパティを次の変数に設定します。

    ```powerapps-dot
    ImageJSON
    ```

1. コントロールのサイズを変更し、ほとんどの結果を表示するために、必要に応じてフォント サイズを小さくします。

    ラベルは、**JSON** 関数がキャプチャしたテキスト文字列を示します。

    ```json
    "data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0idXRmLTgiPz4NCjxzdmcgdmVyc2lvbj0iMS4xIg0KCSB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHhtbG5zOnhsaW5rPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5L3hsaW5rIiB4bWxuczphPSJodHRwOi8vbnMuYWRvYmUuY29tL0Fkb2JlU1ZHVmlld2VyRXh0ZW5zaW9ucy8zLjAvIg0KCSB4PSIwcHgiIHk9IjBweCIgd2lkdGg9IjI3MHB4IiBoZWlnaHQ9IjI3MHB4IiBlbmFibGUtYmFja2dyb3VuZD0ibmV3IDAgMCAyNzAgMjcwIiB4bWw6c3BhY2U9InByZXNlcnZlIj4NCgk8ZyBjbGFzcz0ic3QwIj4NCgkJPHJlY3QgeT0iMC43IiBmaWxsPSIjRTlFOUU5IiB3aWR0aD0iMjY5IiBoZWlnaHQ9IjI2OS4zIi8+DQoJCTxwb2x5Z29uIGZpbGw9IiNDQkNCQ0EiIHBvaW50cz0iMjc3LjksMTg3LjEgMjQ1LDE0My40IDE4OC42LDIwMi44IDc1LDgwLjUgLTQuMSwxNjUuMyAtNC4xLDI3MiAyNzcuOSwyNzIiLz4NCgkJPGVsbGlwc2UgZmlsbD0iI0NCQ0JDQSIgY3g9IjIwMi40IiBjeT0iODQuMSIgcng9IjI0LjQiIHJ5PSIyNC4zIi8+DQoJPC9nPg0KPC9zdmc+"
    ```
