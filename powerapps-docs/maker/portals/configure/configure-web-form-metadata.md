---
title: ポータルの Web フォーム メタデータ | MicrosoftDocs
description: ポータル用 Web フォームのメタデータを追加して構成するための手順。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 04201baf8406a6a9c9c66e1668406594334be754
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2020
ms.locfileid: "2978990"
---
# <a name="configure-web-form-metadata-for-portals"></a>ポータルの Web フォーム メタデータを構成します

Web フォーム メタデータには、ネイティブなエンティティ フォームの変更機能ではできない、フォーム フィールドの機能を拡張または上書きする追加の動作変更ロジックが含まれます。

## <a name="add-a-new-record"></a>新しいレコードを追加

1. 変更するフィールドを含む Web フォーム ステップ上で、**関連** > **メタデータ** へと移動します。 

2. **新しい Web フォーム メタデータ**を選択します。

## <a name="web-form-metadata-properties"></a>Web フォーム メタデータのプロパティ

次の属性は、フォームの要素に対する追加のスタイリングと機能を提供します。

| 件名          | 内容                                                                                                                                                                                                                                                                                                                                          |
|---------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Web フォーム ステップ | Web フォーム メタデータ レコードに関連付けられた Web フォーム ステップです。                                                                                                                                                                                                                                                                                      |
| 種類          | 使用できるオプションは次のとおりです。<ul><li>属性</li><li>セクション​​</li><li>タブ​​</li></ul>種類値として属性を選択すると、関連したステップに対して表示されている現在のフォームのフィールドを変更するための適切なオプションを表示します。 種類値としてセクションを選択すると、フォームのセクションを編集する場合に使用できるオプションを表示します。 種類値としてタブを選択すると、フォームのタブを編集する場合に使用できるオプションを表示します。  |

## <a name="web-form-metadata-type--attribute"></a>Web フォーム メタデータの種類 = Attribute

選択された種類が [属性] の場合、次のプロパティが表示されます。


|          名前          |                                                                                                                                                    内容                                                                                                                                                     |
|------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 属性の論理名 |                                                                                                                              変更する属性フィールドの論理名です。                                                                                                                               |
|         ラベル          | この入力に指定されたテキストで、エンティティの属性に割り当てられた既定のラベルを置き換えます。 Common Data Service 環境に対してインストールされ有効になっている各言語パックには、関連付けられた言語でフィールドにメッセージを入力できます。 |

### <a name="control-style"></a>スタイルの制御

以下のオプションは、属性のフィールドのスタイルおよび機能を変更します。


|                      名前                       |                                                                                                                                                                                                                                                                                                                                       内容                                                                                                                                                                                                                                                                                                                                       |
|-------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                      スタイル                      | 次のいずれか:<ul><li>垂直ラジオ ボタン リストに設定されたオプション</li><li>水平ラジオ ボタン リストに設定されたオプション</li><li>Geolocation Lookup 検証としての 1 行テキスト ([!INCLUDE[pn-bing](../../../includes/pn-bing.md)] マップ設定が必要 - 詳細はこちらです)</li><li>固定の合計としてのグループ整数 (グループ名が必要)</li><li>タイのないランク付けスケールとしてのグループ整数 (グループ名が必要)</li><li>タイが許可されたランク付けスケールとしてのグループ整数 (グループ名が必要)</li><li>複数選択マトリックス (グループ名が必要)</li><li>複数選択 (グループ名が必要)</li><li>スタック ランクとしてのグループ整数 (グループ名が必要)</li></u> |
|                   グループ名                    |                                                                                                                                                                                                                                                                                                             複合コントロールとしてコントロールをグループ化するための名前です。                                                                                                                                                                                                                                                                                                              |
| 複数選択の必要最小選択数 |                                                                                                                                                                                                                                                                      これは、複数選択の質問において選択する必要のある最小値です。 スタイルの制御に "複数選択" が選択されている場合にのみ必要です。                                                                                                                                                                                                                                                                       |
|       複数選択の最大選択数        |                                                                                                                                                                                                                                                          これは、複数選択の質問において選択可能な値の最大数です。 スタイルの制御に "複数選択" が選択されている場合にのみ必要です。                                                                                                                                                                                                                                                          |
|           固定の合計の最小合計            |                                                                                                                                                                                                                                                             これは、[固定の合計] 応答フィールドに適用される、必要な最小値です。 スタイルの制御に "固定の合計としてのグループ整数" が選択されている場合のみ必要です。                                                                                                                                                                                                                                                              |
|           固定の合計の最大合計            |                                                                                                                                                                                                                                                 これは、[固定の合計] 応答フィールドに適用することが許可されている値の最大数です。 スタイルの制御に "固定の合計としてのグループ整数" が選択されている場合のみ必要です。                                                                                                                                                                                                                                                 |
|           オプション セット値のランダム化           |                                                                                                                                                                                                                                                                     [はい] を指定すると、ランダムに並び替えられたオプション セット コントロールのオプションが表示されます。 [オプション セット] の種類の属性にのみ適用可能です。                                                                                                                                                                                                                                                                     |
|                    CSS クラス                    |                                                                                                                                                                                                                                                                                                                      コントロールにカスタム CSS クラス名を追加します。                                                                                                                                                                                                                                                                                                                       |

### <a name="prepopulate-field"></a>事前設定フィールド

次のオプションは、フォームのフィールドに既定値を提供します。


|         件名         |                                                                                                                                                                                                                                                                内容                                                                                                                                                                                                                                                                 |
|----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 既定値を無視 |                                                                              指定された属性フィールドの既定値は無視されます。 [はい] および [いいえ] のラジオ ボタンとして表示される [2 つのオプション] フィールドの属性に役立ちます。 はい/いいえの値は自動的に規定で割り当てられるため、このオプションにより事前定義された応答のない、はい/いいえで回答する質問を表示することができます。                                                                               |
|         種類​​         | 次のいずれか:<ul><li>値</li><li>今日の日付</li><li>現在のユーザーの取引先担当者</li></ul>値を選択するには、フォームが読み込まれるとフィールドに割り当てられる **値** フィールドで値が指定されている必要があります。 今日の日付を選択すると、属性フィールドに現在の日付と時間が割り当てられます。 現在のユーザーの取引先担当者を選択するには、現在のユーザーの取引先担当者のレコードから取得され、指定された属性フィールドに設定される取引先担当者エンティティの属性である**属性から**が必要です。 |
|        値         |                                                                                                                                                                                                                                        フォームが読み込まれるときにフィールドに割り当てられる値です。                                                                                                                                                                                                                                        |
|    属性から    |                                                                                                                                                                                             フォームが読み込まれるときに現在のポータルのユーザー レコードから取得され、フィールド割り当てられる取引先担当者エンティティの属性です。                                                                                                                                                                                             |

### <a name="set-value-on-save"></a>保存に値を設定

次のオプションは、フォームの保存時に設定する値を指定します。

| 名前              | 内容                                                                                                                                                                                                                                                                                                                                                                                                                                |
|-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 保存に値を設定 | [はい] は、**値** フィールドで指定される入力を使用する属性に値を割り当てる必要があることを意味します。 <br>**メモ**: 以下を除く、すべての属性の種類がサポートされています: 一意識別子。       |
| 種類​​              | 次のいずれか:<ul><li>値</li><li>  今日の日付</li><li>現在のユーザーの取引先担当者</li></ul>値を選択するには、フォームが読み込まれるとフィールドに割り当てられる **値** フィールドで値が指定されている必要があります。 今日の日付を選択すると、属性フィールドに現在の日付と時間が割り当てられます。 現在のユーザーの取引先担当者を選択するには、現在のユーザーの取引先担当者のレコードから取得され、指定された属性フィールドに設定される取引先担当者エンティティの属性である**属性から**が必要です。  |
| 値             | フォームが保存されるときに属性に割り当てられる値です。<br>2 つのオプション (ブール値) フィールドで true または false を使用します。<br>オプション セット フィールドではオプションに整数値を使用します。<br>検索 (エンティティ参照) フィールドには、GUID を使用します。<br>**メモ**: 属性がフォームにもある場合、ユーザーの値がこの値で上書きされます。|
| 属性から    | 保存中に現在のポータルのユーザー レコードから取得され、フィールド割り当てられる取引先担当者エンティティの属性です。 |

### <a name="validation"></a>検証

次のセクションには、さまざまな検証パラメーターおよびエラー メッセージを変更するプロパティが含まれます。

Common Data Service 環境に対してインストールされ有効になっている各言語パックには、関連付けられた言語でフィールドにメッセージを入力できます。

| 名前                                        | 内容                                                                                                                                                                                                                                                      |
|---------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 検証エラー メッセージ                    | フィールドの既定の検証エラー メッセージを上書きします。                                                                                                                                                                                                    |
| 正規表現                          | フィールドを検証するために追加する正規表現です。                                                                                                                                                                                                          |
| 正規表現の検証エラー メッセージ | 検証した正規表現が失敗した場合に表示される検証エラー メッセージです。                                                                                                                                                                               |
| フィールドは必須                           | 属性フィールドが値を含む必要があるようにするにはオンにします。                                                                                                                                                                                                   |
| 必須フィールドの検証エラー メッセージ     | フィールドに値がない場合、既定の必須フィールドの検証エラー メッセージが上書きされます。                                                                                                                                                                        |
| 範囲検証エラー メッセージ              | フィールドの値が、[整数]、[10 進数]、[浮動小数点数]、または [通貨] のエンティティ属性の種類で指定された適切な最小値と最大値の範囲外の場合、表示された範囲検証エラー メッセージが上書きされます。 |
| 物理的場所検証エラー メッセージ         | 属性が 1 行テキストで、スタイルの制御に物理的場所検索検証として 1 行テキストが指定されている場合に適用可能で、入力の検証が失敗した場合に表示される既定のエラー メッセージが上書きされます。 |
| 固定の合計検証エラー メッセージ       | 属性が整数の種類で、スタイルの制御に固定の合計としてグループ整数が指定されている場合に適用可能で、入力の検証が失敗した場合に表示される既定のエラー メッセージが上書きされます。                    |
| 複数選択の検証エラー メッセージ    | 属性が2 つのオプションの種類で、スタイルの制御に複数選択が指定されている場合に適用可能で、入力の検証が失敗した場合に表示される既定のエラー メッセージが上書きされます。                                         |
| タイのないランク付けの検証エラー メッセージ | 属性が整数の種類で、スタイルの制御にタイのないランク付けとしてグループ整数が指定されている場合に適用可能で、入力の検証が失敗した場合に表示される既定のエラー メッセージが上書きされます。              |

### <a name="description-and-instructions"></a>説明と指示

次のプロパティがカスタム説明または指示の場所と内容を指定します。


|                 名前                 |                                                                                                                                                           内容                                                                                                                                                           |
|--------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           説明の追加            |                                                                                                                        [はい] の場合、指定された場所のフォームにカスタム テキストが表示されます。                                                                                                                        |
|               ポジション               |                                                                                                             次のいずれか:<ul><li>フィールドの上側</li><li>フィールドの下側</li><li>ラベルの上側</li></ul>                                                                                                              |
| 属性の説明プロパティを使用 |                                                                                       属性メタデータに割り当てらた説明をエンティティに使用するには、[はい] を選択します。 カスタム説明を指定するには、[いいえ] を選択します。 既定は [いいえ] です。                                                                                       |
|             内容              | フォームに表示するカスタム テキストです。 [属性の説明プロパティを使用] が [いいえ] に設定されている場合、組み合わせて使用されます。 Common Data Service 環境に対してインストールされ有効になっている各言語パックには、関連付けられた言語でフィールドにメッセージを入力できます。 |

## <a name="web-form-metadata-type--section"></a>Web フォーム メタデータの種類 = Section

選択された種類が [セクション] と等しい場合、次のプロパティが表示されます。


|     名前     |                                                                                                                                                   説明                                                                                                                                                    |
|--------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| セクション名 |                                                                                           変更するエンティティ フォームのセクション名です。                                                                                            |
|    ラベル     | この入力に指定されたテキストで、エンティティのセクションに割り当てられた既定のラベルを置き換えます。 Common Data Service 環境に対してインストールされ有効になっている各言語パックには、関連付けられた言語でフィールドにメッセージを入力できます。 |

## <a name="web-form-metadata-type--tab"></a>Web フォーム メタデータの種類 = Tab

選択された種類が [タブ] と等しい場合、次のプロパティが表示されます。


|   名前   |                                                                                                                                                 説明                                                                                                                                                  |
|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| タブ名 |                                                                                           変更するエンティティ フォームのタブ名です。                                                                                            |
|  ラベル   | この入力に指定されたテキストで、エンティティのタブに割り当てられた既定のラベルを置き換えます。 Common Data Service 環境に対してインストールされ有効になっている各言語パックには、関連付けられた言語でフィールドにメッセージを入力できます。 |

### <a name="see-also"></a>関連項目

[ポータルの構成](configure-portal.md)  
[エンティティ フォームの定義](entity-forms.md)  
[ポータルの Web フォームのプロパティ](web-form-properties.md)  
[ポータルの Web フォームの手順](web-form-steps.md)  
[ポータルの Web フォームのサブグリッド構成](configure-web-form-subgrid.md)  
[ポータルの Web フォームのメモの構成](../configure-notes.md)  

