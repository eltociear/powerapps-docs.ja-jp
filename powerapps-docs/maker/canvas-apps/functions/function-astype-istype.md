---
title: キャンバス アプリの AsType 関数と IsType 関数 | Microsoft Docs
description: キャンバス アプリの AsType および IsType 関数の構文と例を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/17/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0ecb30a5a452a6ee092ccf9bc9d47f6182ef60ab
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "3303762"
---
# <a name="astype-and-istype-functions-in-canvas-apps"></a>キャンバス アプリの AsType 関数と IsType 関数

特定のエンティティの種類 (**IsType**) のレコード参照を確認し、参照を特定の種類 (**AsType**) として扱います。

## <a name="description"></a>内容

概要と詳細については、[レコード参照とポリモーフィック ルックアップについて](../working-with-references.md)を参照してください。

検索フィールドは通常、特定のエンティティのレコードを参照します。 エンティティの種類は十分に確立されているため、単純なドット表記を使用して検索フィールドにアクセスできます。 たとえば、**First( Accounts ).'Primary Contact'.'Full Name'** は**取引先企業**エンティティから**取引先担当者**エンティティの**取引先責任者**レコードに移動し、**氏名**フィールドを抽出します。

Common Data Service は、これらの例のように、エンティティのセットからのレコードを参照できポリモーフィック ルックアップ フィールドもサポートしています。

| 検索フィールド | 以下を参照 |
|--------------|--------------|
| **所有者** | **ユーザー**または**チーム** |
| **顧客** | **取引先企業**または**取引先担当者** |
| **関連** | **取引先企業**、**取引先担当者**、**サポート情報記事**、など。 |

<!--note from editor: Change "Knowledge Articles" to "Knowledge Base articles" if that is what is being referenced.   -->

キャンバス アプリの式では、レコード参照を使用して、ポリモーフィック ルックアップを操作できます。 レコード参照はさまざまなエンティティを参照できるため、数式を作成する際にどのフィールドを使用できるかはわかりません。 *.Field* 表記は使用できません。 これらの数式は、アプリの実行時にアプリが検出するレコードに合わせて適応させる必要があります。

**IsType** 関数は、レコード参照が特定のエンティティの種類を参照しているかどうかをテストします。 関数はブール値の TRUE または FALSE を返します。

**AsType** 関数は、レコード参照を特定のエンティティの種類として扱い、*キャスト*と呼ばれることもあります。 結果をエンティティのレコードであるかのように使用し、*.Field* 表記を使用して、そのレコードのすべてのフィールドにアクセスすることができます。 参照が特定の種類ではない場合、エラーが発生します。

これらの関数を一緒に使用して、最初にレコードのエンティティの種類をテストし、次にそれをその種類のレコードとして扱い、フィールドが使用できるようにします。

```powerapps-dot
If( IsType( First( Accounts ).Owner, Users ),
    AsType( First( Accounts ).Owner, Users ).'Full Name',
    AsType( First( Accounts ).Owner, Teams ).'Team Name'
)
```

これらの関数は、レコード参照のフィールドにアクセスする場合にのみ必要です。 たとえば、レコード参照を [**Filter**](function-filter-lookup.md) 関数で **IsType** または **AsType** なしで使用できます。

```powerapps-dot
Filter( Accounts, Owner = First( Users ) )
```

同様に、レコード参照を [**Patch**](function-patch.md) 関数と共に使用することもできます。

```powerapps-dot
Patch( Accounts, First( Accounts ), { Owner: First( Teams ) } )
```  

[**Gallery**](../controls/control-gallery.md) または [**Edit form**](../controls/control-form-detail.md) コントロール内などのレコード コンテキストで使用する場合、エンティティの種類を参照するのに[グローバル曖昧性除去演算子](operators.md#disambiguation-operator)を使用する必要がある場合があります。 たとえば次の式は、**会社名**が**顧客**ルックアップである取引先担当者のリストを表示するギャラリーに有効です。

```powerapps-dot
If( IsType( ThisItem.'Company Name', [@Accounts] ),
    AsType( ThisItem.'Company Name', [@Accounts] ).'Account Name',
    AsType( ThisItem.'Company Name', [@Contacts] ).'Full Name'
)
```

どちらの関数でも、エンティティに接続されているデータ ソースの名前を使用して種類を指定します。 数式を機能させるには、テストまたはキャストする種類のアプリにデータ ソースも追加する必要があります。 たとえば、**IsType** および **AsType** を **Owner** ルックアップと共に使用する場合は、**ユーザー** エンティティをデータ ソースとして追加する必要があります。 アプリで実際に使用するデータ ソースのみを追加できます。ルックアップが参照できるすべてのエンティティを追加する必要はありません。

レコード参照が*空白*の場合、**IsType** は FALSE を返し、**AsType** は*空白*を返します。 *空白*レコードのすべてのフィールドは、*空白*になります。

## <a name="syntax"></a>構文

**AsType** (*RecordReference*、*EntityType*)

- *RecordReference* - 必須。 多くの場合、レコード参照は、複数のエンティティのいずれかのレコードを参照できる検索フィールドです。
- *EntityType* - 必須. テストする特定のエンティティです。

**IsType** (*RecordReference*、*EntityType*)

- *RecordReference* - 必須。 多くの場合、レコード参照は、複数のエンティティのいずれかのレコードを参照できる検索フィールドです。
- *EntityType* - 必須. レコードをキャストする特定のエンティティです。

## <a name="example"></a>例

[レコード参照とポリモーフィック ルックアップについて](../working-with-references.md)には、豊富な例が含まれています。

1. タブレット用の空白のキャンバス アプリを作成します。

1. **表示**タブで、**データ ソース**を選択し、**取引先担当者**および**取引先企業**エンティティを、データ ソースとして追加します。
    > [!div class="mx-imgBorder"]
    > ![2 つのデータソースを持つ空白のアプリ: 取引先企業と取引先担当者](media/function-astype-istype/contacts-add-datasources.png)

1. **ギャラリー** コントロールを**縦方向 (空)** に挿入します。

    > [!div class="mx-imgBorder"]
    > ![ギャラリー コントロールを空の縦方向レイアウトに挿入する](media/function-astype-istype/contacts-customer-gallery.png)

1. 画面の右側にある**プロパティ** タブで、ギャラリーの **Items** プロパティを **Contacts** に設定します。

    > [!div class="mx-imgBorder"]
    > ![プロパティ ウィンドウでアイテムを取引先担当者に設定する](media/function-astype-istype/contacts-customer-datasource.png)

1. ギャラリーのレイアウトを、**タイトルとサブタイトル**に設定します。

    > [!div class="mx-imgBorder"]
    > ![プロパティ ウィンドウからレイアウト ピッカーを開く](media/function-astype-istype/contacts-customer-layout.png)

    > [!div class="mx-imgBorder"]
    > ![レイアウトをタイトルとサブタイトルに設定する](media/function-astype-istype/contacts-customer-flyout.png)

1. **データ** ウィンドウで、**Title1** リストを開き、**氏名**を選択します。

    > [!div class="mx-imgBorder"]
    > ![タイトルの値を設定する](media/function-astype-istype/contacts-customer-title.png)

1. **Subtitle1** のラベル コントロールを選択します。

    > [!div class="mx-imgBorder"]
    > ![サブタイトルの値を設定する](media/function-astype-istype/contacts-customer-subtitle.png)

1. **Subtitle1** の **Text** プロパティを次の数式に設定します。

    ```powerapps-dot
    If( IsBlank( ThisItem.'Company Name' ), "--",
        IsType( ThisItem.'Company Name', [@Accounts] ),
            "Account: " & AsType( ThisItem.'Company Name', [@Accounts] ).'Account Name',
        "Contact: " & AsType( ThisItem.'Company Name', [@Contacts] ).'Full Name'
    )
    ```

    > [!div class="mx-imgBorder"]
    > ![画面が完成し、ギャラリーに取引先企業と取引先担当者が混在して表示される](media/function-astype-istype/contacts-customer-complete.png)

    ギャラリーのサブタイトルはこれらの値を示しています。
    - もし**会社名**が*空白*の場合は、"--" となります。
    - **会社名**フィールドがアカウントを参照している場合、「取引先企業: 」および**取引先企業**エンティティの**取引先企業名**フィールド。
    - **会社名**フィールドが取引先担当者を参照している場合、「取引先担当者: 」および**取引先担当者**エンティティの**氏名**フィールド。

    追加の結果の種類を表示するように変更されたサンプル データを使用するため、結果はこのトピックの結果と異なる場合があります。
