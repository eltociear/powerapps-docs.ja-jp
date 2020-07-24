---
title: GUID 関数 | Microsoft Docs
description: Power Apps での GUID 関数の構文を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/14/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 88028d2dc4016d294e051ecff66b590996b57966
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3305142"
---
# <a name="guid-function-in-power-apps"></a>Power Apps での GUID 関数
GUID ([グローバル一意識別子](https://en.wikipedia.org/wiki/Universally_unique_identifier)) 文字列を GUID 値に変換する、または新しい GUID 値を作成します。

## <a name="description"></a>内容
**GUID** 関数を使用して、GUID の 16 進数表現を含む文字列をデータ ベースに渡せる GUID 値に変換します。 GUID 値は、Common Data Service および SQL Server などのデータ ベース システムによってキーとして使用されます。

渡される文字列は大文字または小文字を含めることができますが、次のいずれかの形式で 32 桁の 16 進数である必要があります。

- **"123e4567-e89b-12d3-a456-426655440000"** (標準の場所のハイフン)
- **"123e4567e89b12d3a456426655440000"** (ハイフンなし)

引数を指定しない場合、この関数は新しい GUID を作成します。

GUID 値を文字列に変換するには、ただ文字列コンテキストで使用するだけです。 GUID 値は、ハイフンおよび小文字をともなう 16 進数表現の文字列に変換されます。 

新しい GUID を生成するには、この関数は疑似乱数を使用して、バージョン 4 [IETF RFC 4122](https://www.ietf.org/rfc/rfc4122.txt) GUID を作成します。 文字列を GUID に変換する場合、この関数は 32 桁の 16 進数のすべての文字列を承認することにより、すべての GUID バージョンをサポートします。

## <a name="volatile-functions"></a>Volatile 関数
**GUID**は、引数なしで使用される場合、揮発性の関数です。 関数が評価されるたびに、別の値が返されます。  

データ フロー数式で使用すると、揮発性の関数は、それが表示される数式が再評価される場合にのみ、別の値を返します。 数式で何も変更がない場合、アプリの実行全体で同じ値を設定します。

たとえば、**Text** プロパティが **GUID()** に設定されているラベル コントロールは、アプリがアクティブになっている間は変更されません。 アプリを閉じて再び開いた場合にのみ、別の値という結果になります。

関数は、他の何かが変更された数式の一部である場合に再評価されます。 **Label** コントロールの **Text** プロパティをこの数式に設定する場合、たとえば、GUID はユーザーが**テキスト入力**コントロールの値を変更するたびに生成されます。

**TextInput1.Text & " " & GUID()**

[動作の数式](../working-with-formulas-in-depth.md) で使用すると、**GUID** は数式が評価されるたびに生成されます。 詳細については、このトピックの内容の後半の例を参照してください。

## <a name="syntax"></a>構文
**GUID**( [ *GUIDString* ] )

* *GUIDString* – オプション。.  GUID の 16 進数表現を含むテキスト文字列。 文字列が指定されていない場合、新しい GUID が作成されます。

## <a name="examples"></a>例

#### <a name="basic-usage"></a>基本的な使用

16 進数の文字列表現に基づいて GUID 値を返す場合。

* **GUID( "0f8fad5b-d9cb-469f-a165-70867728950e" )**

ハイフンなしの GUID 文字列を指定することもできます。 この数式では、同じ GUID 値を返します。

* **GUID( "0f8fad5bd9cb469fa16570867728950e" )**

コンテキストで使用し、新しいデータベース レコードの **Status** フィールドを十分確立された値に設定する場合。

* **Patch( Products, Default( Products ), { Status: GUID( "F9168C5E-CEB2-4faa-B6BF-329BF39FA1E4" ) } )**

GIUD をユーザーに表示したくない場合がありますが、GUID はアプリのデバッグに役立つます。 前の例で作成したレコードで **Status** フィールドの値を表示するには、**Label** コントロールの **Text** プロパティを次の数式に設定します。

* **First( Products ).Status**

**Label** コントロールは **f9168c5e-ceb2-4faa-b6bf-329bf39fa1e4** を表示します。

#### <a name="create-a-table-of-guids"></a>GUID のテーブルを作成する

1. **[Button](../controls/control-button.md)** コントロールの **[OnSelect](../controls/properties-core.md)** プロパティを次の数式に設定します。

    **ClearCollect( NewGUIDs, ForAll( [ 1, 2, 3, 4, 5 ], GUID() ) )**

    この数式は、5 回反復して、結果として 5 つの GUID が生成されるために使用される単一列のテーブルを作成します。

1. **[データ テーブル](../controls/control-data-table.md)** コントロールを追加し、その **Items** プロパティを **NewGUIDs** に設定し、**値**フィールドを表示します。

1. Alt キーを押しながら、クリックまたはタップしてボタンを選択します。

    データ テーブルには、GUID の一覧が表示されます。

    ![5 つの異なる GUID 値を持つデータ テーブルが表示するスクリーン](media/function-guid/guid-collection-1.png)

1. 再度ボタンを選択し、別の GUID 一覧を表示します。

    ![同じスクリーンが、5 つの異なる GUID 値の新しいセットを持つデータ テーブルを表示](media/function-guid/guid-collection-2.png)

テーブルの代わりに単一の GUID を生成するには、次の数式を使用します。

**Set( NewGUID, GUID() )**
