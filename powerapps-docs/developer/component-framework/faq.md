---
title: FAQ | MicrosoftDocs
description: コンポーネント フレームワークに関してよく寄せられる質問
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: index-page
ms.assetid: 9f940264-d7d5-4930-8052-1bd582445d37
ms.author: grhurl
author: ghurlman
ms.reviewer: nkrb
ms.openlocfilehash: 1c1c7f6ef32be9771b989d9ea3b6c7825afa307c
ms.sourcegitcommit: 51d899f17feebd9da8e165dce3e2e2c017ac76ca
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2020
ms.locfileid: "3378345"
---
# <a name="faqs"></a>よく寄せられる質問

[!INCLUDE[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

### <a name="component-changes-are-not-reflected-after-the-updated-solution-import"></a>更新されたソリューションのインポート後にコンポーネントの変更は反映されませんか？

コンポーネント マニフェスト ファイルのコンポーネント バージョン (マイナーまたはパッチ) を更新します (たとえば、1.0.0 から 1.0.1)。 コンポーネントの更新ごとに、Common Data Service サーバに反映されるコンポーネントのバージョンを上げる必要があります。

> [!NOTE]
> - メジャー バージョンを上げたい場合は、毎回新しいソリューションを作成する必要があります。 メジャー バージョン番号 (1.0 から 2.0 など) の増分は、アップグレードとしてサポートされていません。
> - 3 つのバージョン セクションのみがサポートされています (つまり、MAJOR.MINOR.PATCH)。 これらのバージョン番号セクションは、0 ～ 65536 の範囲内である必要があります。

### <a name="what-are-the-things-to-be-considered-from-a-performance-perspective"></a>パフォーマンスの観点から考慮すべきことは何ですか?

1. 大量のデータ項目にアクセスする場合は、[フィルター処理](reference/filtering.md) と [ページング](reference/paging.md) を実装して、ロードするデータ量を制限します。
2. ネットワーク呼び出しをバッチ処理し、ネットワーク呼び出しを非同期にします。 すべての必要な情報が 1 回の呼び出しで提供されるように、コンポーネントを設計します。 
3. ユーザーが各データ項目を呼び出すのではなく、特定の項目のデータのロードを開始するアクション (ボタンをクリックするなど) を実行する必要があるようにコンポーネントを設計します。
4. 必ず [破棄](reference/control/destroy.md) 機能を使用してリソースをクリーンアップしてください。 オープン ネットワークの呼び出し、接続、およびイベント ハンドラーをクリーンアップして、パフォーマンスを向上させる必要があります。

### <a name="where-can-i-find-some-good-examples-of-code-components"></a>コード コンポーネントの良い例はどこにありますか?

[Power Apps コミュニティ フォーラム](https://powerusers.microsoft.com/t5/Power-Apps-Component-Framework/Community-content-sample-components-blogs-etc-Link-to-this-page/td-p/280710) には、コミュニティからの素晴らしい例がたくさんあります。

### <a name="how-to-use-rich-data-types-in-code-components-such-as-collections"></a>コレクションなどのコード コンポーネントでリッチ データ型を使用する方法は?

この機能は現在、サポートされていません。 ただし、キャンバス アプリには [JSON 関数](https://docs.microsoft.com/powerapps/maker/canvas-apps/functions/function-json) があり、アプリ メーカーはデータを文字列化することができます。

1. コレクションを JSON 関数に渡します。
2. JSON 関数から返されるコレクション データの文字列表現を、コンポーネントの文字列プロパティの 1 つに渡します。
3. コンポーネント コードの [JSON.parse](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse) を使用して、JavaScript オブジェクト に変換します。

### <a name="how-can-i-define-multiple-components-in-a-single-manifest-file"></a>単一のマニフェスト ファイルで複数のコンポーネントを定義するにはどうすればよいですか?

単一のマニフェスト ファイルで複数のコンポーネントを定義することはサポートされていません。 

### <a name="how-can-i-define-behavior-properties"></a>動作プロパティを定義するにはどうすればよいですか?

これは現時点ではサポートされていません。 現在、モデル駆動型アプリでは、[ナビゲーション](reference/navigation.md) メソッドを使用してダイアログ ボックスを呼び出すことができます。

### <a name="how-can-i-call-other-components-from-within-another-component"></a>別のコンポーネント内から他のコンポーネントを呼び出すにはどうすればよいですか?

これは、フレームワークによって単純にサポートされていません。 多くのサード パーティ ライブラリの 1 つを使用して、コンポーネントでこの機能を有効にできます。

### <a name="can-i-bundle-font-resources"></a>フォント リソースをバンドルできますか?

現在、フォント リソース (.ttf ファイル拡張子を持つファイル) は、フレームワークでサポートされていません。

### <a name="can-i-use-img-resource-property-in-canvas-apps"></a>キャンバス アプリで img リソース プロパティを使用できますか。

現在、[img](manifest-schema-reference/img.md) リソースはキャンバス アプリでサポートされていません。

### <a name="tabindex-support-for-components-in-canvas-apps"></a>キャンバス アプリでのコンポーネントの TabIndex サポート

現在、コード コンポーネントはキャンバス アプリの `tabindex` プロパティをサポートしていません。 モデル駆動型アプリの場合、タブ割り当ては `tabIndex = 0` を使用して自動的に割り当てられるため、要素は出現順にナビゲートされます。 


## <a name="related-topics"></a>関連トピック

[Power Apps Component Framework API の参照](reference/index.md)<br/>
[Power Apps Component Framework の概要](overview.md)
