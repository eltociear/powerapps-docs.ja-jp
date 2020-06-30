---
title: ポータルでのコンテンツ スニペットを使用したコンテンツのカスタマイズ | MicrosoftDocs
description: コンテンツ スニペットの使用によるコンテンツのカスタマイズの方法について学習します。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 05/21/2020
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 25e7b6c335e35ff97da8535cfdd9023feeaea9bc
ms.sourcegitcommit: 8b08fdc6a2934648ae926ea62ebee4cdb578b651
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/22/2020
ms.locfileid: "3394876"
---
# <a name="customize-content-by-using-content-snippets"></a>コンテンツ スニペットの使用によるコンテンツのカスタマイズ

コンテンツ スニペットは、開発者がページ テンプレートに配置できる編集可能なコンテンツの一部で、これによってページ レイアウトのどの部分にも簡単にカスタマイズ可能なコンテンツを挿入することができます。 スニペットのコンテンツを Web に対するインターフェースを持つポータルに表示する役割を担うスニペット コントロールは、開発者によってページ テンプレートに配置されます。

## <a name="edit-snippets"></a>スニペットの編集

スニペットはポータル管理アプリケーションから編集することもできます。 スニペットの主な能力は、(ページの主コピー以外の) コンテンツの一部を要約し個別に編集して、実質的にサイト上のすべての静的コンテンツを完全に管理し、編集可能にするという事実です。

1. [ポータル管理アプリ](configure-portal.md)を開きます。

1. **ポータル** > **コンテンツ スニペット**に移動します。

1. 新しいスニペットを作成するには、 **新規**を選択します。

1. 既存のスニペットを編集する: グリッド内の既存の **コンテンツ スニペット** を選択します。

以下のフィールドに値を入力:

| Name    | 内容                                                                                                   |
|---------|---------------------------------------------------------------------------------------------------------------|
| Name    | 開発者は名前を使用してポータルのコード内のページ テンプレートにスニペットの値を配置できます。 |
| Web サイト | スニペットに関連付けられている Web サイトです。                                                              |
| 表示名 | コンテンツのスニペットの表示名です。 |
| 種類​​ | コンテンツ スニペットの タイプです。テキスト、または HTML です。
| コンテンツ スニペット言語 | コンテンツ スニペットの言語を選択します。 さらに言語を追加するには、[多言語サポートを有効にする](enable-multiple-language-support.md)にアクセスしてください。
| 値   | ポータルに表示されるスニペットのコンテンツです。 プレーン テキストまたは HTML マークアップを入力することができます。 テキストまたはHTMLマークアップ値の両方を持つ、[リキッド オブジェクト](../liquid/liquid-objects.md)を使用することもできます。    |

## <a name="use-snippet"></a>スニペットの使用

スニペットを使用して、テキストまたはHTMLを表示できます。 コンテンツス ニペットは[リキッド オブジェクト](../liquid/liquid-objects.md)を使用することもでき、[エンティティ](../liquid/liquid-objects.md#entities)などその他のコンテンツを参照することができます。

たとえば、この記事の前半で説明した手順を使用して、コンテンツ スニペットを作成/編集することができます。 スニペットの編集中に、[エンティティ レコード](../liquid/liquid-objects.md#entities)を含むサンプル コードを含めることができます。 アカウント エンティティ レコードの ID をご利用の環境の正しい ID に置き換えてください。 アカウントの代わりに別のエンティティを使用することもできます。

上記例に示されているテキスト、HTML、またはリキッド オブジェクトを使用してスニペットを作成すると、ポータル ページで使用できます。

ポータル ページにスニペットを追加するには :

1. [Webテンプレート](../liquid/store-content-web-templates.md)を作成し、[スニペットのリキッド オブジェクト](../liquid/liquid-objects.md#snippets)を使用して作成したスニペットを呼び出します。

2. 作成済の Web テンプレートを使用して、[ページ テンプレート](page-templates.md)を作成します。

3. ポータル スタジオを使用して、作成したページテンプレートを使用して新たなページを作成します。

## <a name="example"></a>例

次の例では、[サンプルデータ](https://docs.microsoft.com/power-platform/admin/add-remove-sample-data)を使用した Common Data Service データベースの使用例を示しています。

1. [ポータル管理アプリ](configure-portal.md)を開きます。

1. **ポータル** > **コンテンツ スニペット**に移動します。

1. 新しいスニペットを作成するには、 **新規**を選択します。

1. 名前を入力します。 この例では、AccountData を入力します。

1. Web サイトを選択します。

1. 表示名を入力します。 この例では、AccountData を入力します。

1. この例では、タイプに HTML を選択します。 テキストを選択することもできます。

1. 言語を選択します。

1. サンプル値をコピーして貼り付けます :

    ```
    {% assign account = entities.account['f4f25307-d284-ea11-a816-000d3a36ff29'] %}
    {% if account %}
    <b> Account Name is: </b> {{ account.name }} <br>
    <i> Account State: </i> {{ account.statecode.label }})
    {% endif %}
    ```

    レコードの GUID を、ご利用の Common Data Serviceデータベースのアカウント エンティティ レコードに置き換えます。

    ![コンテンツ スニペットを作成する](./media/customize-content-snippets/new-content-snippet-html-liquid.png)

1. コンテンツ スニペットを保存します。

1. 左側パネルから **Web テンプレート** を選択します。

1. **新規**を選択します。

1. 名前を入力します。 この例では、account-web-template を入力します。

1. Web サイトを選択します。

1. ソースの値をコピーして貼り付けます :

    ```{% include 'snippet' snippet_name:'AccountData' %}```

    異なる場合は、 *snippet_name* をご利用のスニペットの名に更新します。

    ![Web テンプレート](./media/customize-content-snippets/web-template.png)

1. 保存を選択します。

1. 左側パネルから **ページ テンプレート** を選択します。

1. **新規**を選択します。

1. 名前を入力します。 この例では、アカウント データ スニペット を入力します。

1. Web サイトを選択します。

1. 種類に *Web テンプレート* を選択します。

1. 上記手順で作成した、Web テンプレートを選択します。 この例では、account-web-template を入力します。

1. 保存を選択します。

    ![ページ テンプレート](./media/customize-content-snippets/page-template.png)

1. ポータルを[編集](../manage-existing-portals.md#edit)します。

1. **新規** > **空白** ページを選択します。

    ![空白のページ](./media/customize-content-snippets/new-blank-page.png)

1. ページの名前を入力します。 この例では、Accounts Data を入力します。

1. 部分 URL を入力します。 この例では、accounts-data を入力します。

1. 上記手順で作成した、**ページ テンプレート**を選択します。 この例では、アカウント データ スニペット を入力します。

    ![Web ページのメタデータ](./media/customize-content-snippets/webpage-metadata.png)

1. 右上から **ウェブサイトの閲覧する**を選択し、ブラウザでページを表示します。

    ![ポータルの閲覧](./media/customize-content-snippets/browse-portal.png)

HTML 同様に、**テキスト** タイプのコンテンツ スニペットでも同じ手順を実行することができます :

```
{% assign account = entities.account['f4f25307-d284-ea11-a816-000d3a36ff29'] %}
{% if account %}
Account Name is: {{ account.name }} 
Account State: {{ account.statecode.label }}
{% endif %}
```
レコードの GUID を、ご利用の Common Data Serviceデータベースのアカウント エンティティ レコードに置き換えます。

このコンテンツ スニペットでページを閲覧すると、エンティティ情報は HTML ではなくテキストとともにリキッド オブジェクトで表示されます。 同様に、HTML のみを使用して、リキッド オブジェクトを使用せずにコンテンツを表示することもできます。

## <a name="see-also"></a>関連項目

[営キッド テンプレートを使用して作業する](../liquid/liquid-overview.md)
