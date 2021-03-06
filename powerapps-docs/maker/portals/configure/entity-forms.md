---
title: エンティティ フォームの定義 | MicrosoftDocs
description: ポータルのエンティティ フォームを作成するための手順。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 04/09/2020
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 4ddc8daba01d281a483d51b1ce7a42205d0c6e93
ms.sourcegitcommit: 2484ebce6563cfd1c849e1e2f66dd2d29fdb7b64
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2020
ms.locfileid: "3256684"
---
# <a name="about-entity-forms"></a>エンティティ フォームについて

開発者がポータルでフォームを表示する必要なく、エンドユーザーがポータルのデータを収集するためのフォームを追加できるようにするデータ駆動型の構成では、エンティティ フォームは Common Data service で作成され、ポータルの Web ページに配置するか、サブグリッドとエンティティリストと組み合わせて使用して、完全な Web アプリケーションを構築します。 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [エンティティ リストについて](entity-lists.md) 

![お問い合わせフォーム](../media/contact-us-form.png "お問い合わせフォーム")  

## <a name="add-a-form-to-your-portal"></a>自分のポータルにフォームを追加する

エンティティ フォームには、Web ページとの関連付け、およびポータル内のフォームの初期化を制御する追加プロパティが含まれています。 Web ページへの関連付けにより、Web サイト 内の特定のページ ノードのフォーム定義を動的に取得できます。 

既存のエンティティ フォームの表示、または新しいエンティティ フォームの作成を行うには、 [ポータル管理アプリ](configure-portal.md) を開き、 **ポータル** &gt; **エンティティ フォーム** の順に移動します。

新しいエンティティ フォームを作成する場合は、最初の手順として、**モード: 挿入、編集、または読み取り専用**とともに表示する**エンティティ**および**フォーム名**を決めます。 選択したモードは、ポータルから新しいレコードを作成するか、既存のレコードを編集するか、ポータルのレコードに関する情報を表示するだけかを決定します。

> [!Note]
> - サイトでフォームを表示できるようにするには、 **エンティティ フォーム** を特定の Web サイト の Web ページに関連付ける必要があります。
> - つながり (Connection) エンティティのサブグリッドは、エンティティ フォームではサポートされません。 フォーム デザイナーを使用してフォームにつながり (Connection) エンティティのサブグリッドを追加した場合、ポータルにフォームを表示させ、つながりエンティティを使用すると、エラー メッセージが表示されます。
> - 重複したフィールド、複数が選択されたオプション セット、カスタム コントロール、パーティー リスト フィールド、業務ルールはエンティティ フォームに対応していません。
> - ビジネス ルールおよびクライアントAPIでは、読取り専用フォームのロックされたフィールドを有効化することができます。
> - 挿入モードでエンティティ フォームを作成する場合は、ボタンの展開の変更、またはエンティティ フォーム上部にアクション ボタンを配置することはできません。
> - 検索コントロールをフォーム上のドロップダウン リストとして表示する場合は、関連するレコード フィルターは動作しません。

エンティティ フォームに関連付けられる Web ページは、左端のメニューにある**関連**ナビゲーション リンクに一覧表示されている **Web ページ**リンクを選択することにより表示できます。

Web ページを作成または編集する場合には、Web ページ フォームに表示されている lookup フィールドで**エンティティ フォーム**を指定できます。

ポータルで使用されるさまざまなマスター ページには、 **EntityForm** サーバー コントロールの宣言が含まれています。 ページ (~/Pages/Page.aspx) のページ テンプレートまたはフル ページ (~/Pages/FullPage.aspx) のページ テンプレートのどちらかを含む Web ページを表示する場合、コントロールがエンティティ フォームの検索に値が含まれるかどうかを確認し、この場合、フォームが表示されます。

## <a name="secure-your-forms"></a>フォームのセキュリティ保護

フォームをセキュリティで保護するには、Web ロールに従ってレコードのアクセスおよび所有者を決定するエンティティ アクセス許可を作成する必要があります。 ユーザーがアクセス許可のない [エンティティ フォーム] を訪問した場合、エラー メッセージが表示されます。 エンティティに対するアクセス許可を有効にするには、**エンティティのアクセス許可を有効にする**を true に設定します。 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [ポータルの Web ロールの作成](create-web-roles.md)。  

## <a name="entity-form-attributes-and-relationships"></a>エンティティ フォームの属性と関連付け

|Name|説明|
|-----|----------|
|Name|レコードの内容を示す名前です。 これは必須フィールドです。|
|エンティティ名|フォームの読み込み元のエンティティの名前。 これは必須フィールドです。|
|フォーム名|    レンダリング対象のエンティティにある [フォーム] の名前。 これは必須フィールドです。|
|タブ名|    レンダリング対象として指定されたエンティティにある [フォーム] の [タブ] のオプションの名前。|
|モード|次のいずれかの値です。<ul><li>Ins</li><li>編集​​</li><li>ReadOnly</li></ul>_挿入_を選択すると、送信時に、フォームが新しいレコードを挿入する必要があることを示します。 _編集_を指定すると、フォームが既存のレコードを編集する必要があることを示します。 _読み取り専用_を選択すると、フォームが既存のレコードの編集不可のフォームを表示することを示します。 _編集_および_読み取り専用_は、ソース レコードが存在し、ポータルにフォームが読み込まれるときに [レコード ソースの種類] および [レコード ID クエリ文字列パラメーター名] フィールドで適切なレコードを選択する必要があります。|
|レコード ソースの種類|次のいずれかの値です。<ul><li>クエリ文字列</li><li>現在のポータル ユーザー</li><li>関連付けを現在のポータル ユーザーにレコード</li></ul>_クエリ文字列_を選択すると、フォームへの URL のクエリ文字で指定されるパラメーター名が必要です。 これは、[レコード ID クエリ文字列パラメーター名] フィールドで指定できます。<br>_現在のポータル ユーザー_を選択すると、現在認証しているユーザーのポータル ユーザー レコードを取得します。<br>_現在のポータル ユーザーに関連付けられたレコード_ を選択すると、現在の認証済みユーザーのポータル ユーザー レコードを取得して、次に '関連付けの名前' フィールドで指定された特定の関係のレコードを取得します。|
|レコード ID のクエリ文字列パラメーター名|    この [エンティティ フォーム] を含む Web ページへの URL のクエリ文字列で指定されたパラメーターの名前。|
|関連付け名|    [レコード ソースの種類] が [現在のポータル ユーザーに関連付けられたレコード] の場合は、必須です。 現在のポータル ユーザー レコードとターゲット レコードとの間の関連を示す論理名。 [エンティティ名] フィールドで指定されているものと同じエンティティの種類を返す必要があります。|
|Null の場合に作成を許可|    [レコード ソースの種類] が [現在のポータル ユーザーに関連付けられたレコード] のときに使用可能な任意のブール値。 関連レコードが存在しない場合は、ユーザーがそれを最初に作成できることを示します。それ以外の場合、フォームはデータ バインドを行う対象レコードを必要とするため、レコードがすでに存在しない場合は例外がスローされます。|
|エンティティのアクセス許可の有効化|    フォームがエンティティのアクセス許可に従うようにします。 既定は false で、下位互換性を目的としています。 true に設定した場合、フォームにアクセスする必要のあるユーザーには、明示的なアクセス許可が必要です。|
|||

### <a name="form-options"></a>フォームのオプション

|Name|説明|
|----|---------|
|画像文字の追加|    captcha を表示します。|
|認証されたユーザーに Captcha を表示する|    認証されたユーザーに captcha を表示します。|
|検証グループ|    名前付きグループの入力値が有効かどうか評価するために入力コントロールに割り当てるグループ名。|
|ステップ フォーム タブの自動作成|    エンティティ フォームに複数のタブが表示され、各タブが、最初のタブからすべてのタブをナビゲーションするまでの連続した手順として表示され、最終の送信時にレコードが挿入されることを示します。 既定では選択されません。 既定値は現在のステップに対してひとつのタブやフォームのみが表示されることを示します。 タブ名が指定されない場合、最初のタブが表示されます。|
|Web リソースをインラインで表示|    エンティティ フォームで Web リソースを含む iframe を削除します。|
|ToolTip が有効|    ターゲット エンティティの属性の説明を使用して、ヒントを設定します。|
|サポートされないフィールドを表示|    すべてのフィールドが現在サポートされています。 これは、Common Data Service がフィールドの種類に対して行う潜在的な変更のために予約されます。|
|必要に応じて推奨フィールドを設定|     [推奨項目] に設定されているフィールド入力要件レベルを持つ、必要なすべての属性を作成します。|
|すべてのフィールドを必須にする|     フィールドの入力要求レベルに関係なく、必要なすべてのフィールドが作成されます。|
|検証概要の CSS クラス|    検証の概要に割り当てられた CSS クラス名。 既定値: 'validation-summary alert alert-error alert-block'|
|検証の概要のリンクを有効化|    検証の概要で、エラーを含むフィールドにスクロールするようにアンカー リンクを表示するかどうかを示す、true または false のブール値です。 既定値は true です。|
|検証の概要のリンク テキスト|    確認の概要のリンクに割り当てられるラベルです。 既定では、'click here' (ここをクリックしてください) です。|
|検証概要のヘッダー テキスト|    確認の概要のヘッダーに割り当てられるラベルです。|
|手順|    フォームで作業する手順|
|レコードが見つからない場合のメッセージ|    レコードが見つからないときに表示されるメッセージ。|
|||

### <a name="on-success-settings"></a>成功時の設定

|Name|説明|
|----|----------|
|成功時|    次のいずれかの値です。<ul><li>成功メッセージの表示 (既定)</li><li>リダイレクト</li></ul>|
|成功時にフォームを非表示にする|    成功時の要求を、成功メッセージを表示に設定します。 選択すると、フォームの送信に成功するとフォームは非表示になります。|
|成功メッセージ|    成功時の要求を、成功メッセージを表示に設定します。 送信の成功時にユーザーに表示されるメッセージ。 指定されていない場合は、既定のメッセージ (送信が正常に完了しました) が表示されます。 組織に対してインストールされ有効になっている各言語パックには、関連付けられた言語でフィールドにメッセージを入力できます。|
|外部 URL|リダイレクトに、成功時のセットが必要です。 Web の外部リソースの URL を指定します。
|または Web ページ|リダイレクトに、成功時のセットが必要です。 現在の Web サイトから Web ページを選択します。|
|既存のクエリ文字列を追加|    リダイレクトに、成功時のセットが必要です。 選択された場合、既存のクエリ文字列パラメーターがリダイレクト前にターゲット URL に追加されます。|
|クエリ文字列にレコード ID を追加|     リダイレクトに、成功時のセットが必要です。 選択された場合、リダイレクトされる URL のクエリ文字列に、作成されたレコードが追加されます。|
|レコード ID のクエリ文字列パラメーター名|     リダイレクトに、成功時のセットが必要です。 リダイレクトされる URL のクエリ文字列パラメーターの ID 名です。|
|ユーザー定義のクエリ文字列を追加|    リダイレクトに、成功時のセットが必要です。 リダイレクト URL の既存のクエリ文字列に追加できるユーザー定義の文字列です。|
|属性値をクエリ文字列 - パラメーター名に追加|    リダイレクトに、成功時のセットが必要です。 リダイレクト URL のクエリ文字列に追加されるターゲット エンティティの属性値に関連付ける、パラメーターに付与する名前です。|
|属性値をクエリ文字列 - 属性論理名に追加|リダイレクトに、成功時のセットが必要です。 リダイレクト URL のクエリ文字列に値を追加するためのターゲット エンティティの属性の論理名です。|
|||

### <a name="additional-settings"></a>[追加設定]

|Name|説明|
|----|----------|
|現在のポータル ユーザーを関連付け|    現在ログインしているユーザーのレコードを、対象のエンティティ レコードに関連付ける必要があることを示します。|
|対象エンティティ用のポータル ユーザーの検索属性|    ポータル ユーザーを格納する対象エンティティの属性の論理名。|
|活動関係者である|    対象エンティティ用のポータル ユーザーの検索属性が活動関係者の種類であるかどうかを指定するブール値。|
|ファイルの添付 |  選択すると、フォームの下部にファイル アップロードのコントロールを追加し、レコードにファイルを添付できるようにします。 <br> **注意**: [バージョン 9.2.2.x 以降](https://support.microsoft.com/help/4541765/power-apps-portals-version-9-2-2-x-release) のポータルは、ファイルを添付するためにエンティティ フォームで **エンティティのアクセス許可を有効にする** を有効にする必要はありません。 ただし、選択した場合は、親エンティティと注釈エンティティに適切な特権が付与され、コメント エンティティがフォーム上に **ファイルを添付する** ボタンが表示されていることを確認します。 コメント エンティティには少なくとも **作成** 特権と **追加** 特権があり、親エンティティには対応する **追加先** 特権があることが必要です。 作成フォームと更新フォームのどちらを使用しているかに応じて、フォームのシナリオを完了させるための **作成**、 **読む** 、 **書く** の各特権も必要になります。 |
|添付ファイルの保存場所|    オプション: メモの添付ファイル、Azure Blob Storage。 組織が Azure Storage を使用するように構成されている場合、このエンティティ フォームにアップロードされたファイルをそこに保存することを選択できます。 それ以外の場合、ファイルはメモ添付ファイルとして保存されます。|
|複数ファイルの許可|ユーザーに複数のファイルをアップロードを許可するかを示すブール値。|
|引き受け|    許可の属性は、ファイルのアップロード時にサーバーが許可するファイルの MIME タイプを指定します。 複数の値を指定するには、値をコンマで区切ります (例: audio/*,video/*,image/*)。|
|ラベル|    ファイル アップロード コントロールの隣に表示するテキスト。 組織に対してインストールされ有効になっている各言語パックには、関連付けられた言語でフィールドにメッセージを入力できます。|
|ファイルの添付が必要| 続行するには必要なファイルの添付を作成します。|
|必須の場合のエラー メッセージ|[必須] が true のときユーザーがファイルを添付しない場合に、フォームの検証時に表示されるメッセージ。 組織に対してインストールされ有効になっている各言語パックには、関連付けられた言語でフィールドにメッセージを入力できます。|
|ファイルを承認済みの種類に制限|    承認フィールドで検証を強制します。 選択されない場合、承認属性はファイルのアップロード ダイアログの候補としてのみ使用されます。|
|ファイルの種類のエラー メッセージ|承認された種類のファイルに制限が true で、ユーザーが無効なファイルの種類をアップロードしようとした場合に、フォームの検証中に表示されるメッセージ。 組織に対してインストールされ有効になっている各言語パックには、関連付けられた言語でフィールドにメッセージを入力できます。|
|最大ファイル サイズ (KB 単位)|    アップロードされたファイルの最大許容サイズについて検証を強制します。|
|ファイル サイズのエラー メッセージ|    最大ファイル サイズ (KB 単位) が true で、ユーザーが大きすぎるファイルをアップロードしようとした場合に、フォームの検証中に表示されるメッセージ。 組織に対してインストールされ有効になっている各言語パックには、関連付けられた言語でフィールドにメッセージを入力できます。|
|カスタム JavaScript|    ページの下部のフォームの閉じタグ要素の直前に追加される、JavaScript のカスタム ブロック。 エンティティ フィールドの HTML の入力 ID は、属性の論理名に設定されます。 これにより、フィールドの選択、値の設定、または他のクライアント側の処理が jQuery で容易になります。<br>`$(document).ready(function() {   $("#address1_stateorprovince").val("Saskatchewan");});`|
|||

### <a name="entity-reference"></a>エンティティの参照

次のパラメーターは、フォーム保存時のエンティティ参照の設定に関連します。

これにより、フォームで作成または更新される現在のレコードを対象レコードに関連付ける方法が提供されます。 これは、複数のエンティティの種類に対して複数の手順があり、実行結果のレコードを関連付けたい場合、または関連付けたいレコードの ID がクエリ文字列で渡されるページの場合に便利です。 たとえば、求人情報のリストのある人材募集ページがあり、それぞれに求人情報から応募フォームへの ID を含む応募リンクが付いているとします。それにより応募の作成時に求人情報がそのレコードに関連付けられます。 

|名前|内容|
|-----|---------|
|保存時にエンティティ参照を設定|[はい] または [いいえ] です。 [はい] の値は、フォームの保存時にエンティティ参照を割り当てることを示します。それ以外の場合、何も設定されません。|
|関連付け名|2 つのエンティティの種類の間の、特定の関連付けの [関連付けの定義名]。|
|エンティティの論理名|参照エンティティの論理名。|
|ターゲット検索属性の論理名|作成または更新する対象エンティティ内の検索属性の論理名。|
|検索フィールドの入力|    参照エンティティに関する検索をフォームで行う場合、この値をオンにすると、次の設定を使用して取得した値をフォームのフィールドに入力します。|
|参照エンティティのソースの種類|    次のいずれかの値です。<ul><li>クエリ文字列</li><li>現在のポータル ユーザー</li><li>前の手順からの結果</li></ul> _クエリ文字列_を選択すると、フォームへの URL のクエリ文字で指定されるパラメーター名が必要です。 これは、**クエリ文字列名**フィールドで指定できます。 このパラメーターが主キーの場合、**クエリ文字列では主キーです**で [はい] を選択します。それ以外の場合は [いいえ] を選択し、**クエリ属性の論理名**フィールドで指定された、クエリを行う対象エンティティの属性の論理名を指定します。  現在のポータル ユーザーを選択すると、現在認証しているユーザーの担当者レコードを取得します。 前の手順からの結果を選択すると、現在より前の手順の結果またはエンティティ ソースの手順に関連付けられた手順に基づいた特定の手順以降の結果として作成されたレコードを取得します。|
|参照エンティティ手順|    その手順で作成または編集されたエンティティを取得し、現在の手順のレコードに関連付けるための、前の手順の Web フォームの手順レコード。|
|クエリ文字列名|    [Web フォーム] を含む [Web ページ] への URL の [クエリ文字列] で指定されたパラメーターの名前。|
|クエリ文字列は主キー|    [はい] は、[クエリ文字列] の値が [主キー] の値であることを示します。 [いいえ] は、[クエリ文字列] の値が、[主キー] 以外の属性の種類であることを示しています。|
|クエリ属性の論理名|    レコードを検索するための属性の論理名です。|
|ReadOnly の詳細を表示|    参照レコードに関する読み取り専用の情報を表示するフォームをページの最上部に表示することを示します。 [フォーム名] が必要です。|
|フォーム名|    読み取り専用の詳細を表示するのに使用する参照エンティティのフォームの名前。|
|||


## <a name="entity-form-action-configuration"></a>エンティティ フォームのアクション構成

既定でエンティティ フォームは既存のレコードの読み取りとアップロード、もしくは新規レコードの挿入を許可します。  ただし、エンティティ フォームのレコードに対して、追加のアクションを簡単に有効にして構成することもできます (削除、有効化、無効化など)。 既定のラベル、サイズ、アクションが有効にな場合に表示されるその他の属性を上書きすることもできます。

これらの設定はエンティティ フォームの **追加設定** セクションにあります。 既定では、**基本設定**だけが表示されます。 追加設定を表示するには、 **詳細設定** を選択します。

個々のレコードに適用可能な操作の操作ボタンを追加することができ、適切な特権が [エンティティのアクセス許可](assign-entity-permissions.md) によって許可されているグリッドの各行に表示されます。 次の操作を使用できます。

- 削除
- ワークフロー
- 関連レコードの作成
- アクティブ化
- 非アクティブ化

これらのオプション の 1 つをクリックすると、その操作の構成領域が表示されます。 また、特定のエンティティには、エンティティごとに利用できる特殊な操作があります。

- 営業案件の値の計算 (opportunity)
- サポート案件の取り消しアクション (incident)
- サポート案件のクローズ (resolve) アクション (incident)
- 見積もりから受注への変換 (quote)
- 受注から請求書への変換 (salesorder)
- 営業案件から見積もりを生成 (opportunity)
- 営業案件の失注アクション (opportunity)
- 営業案件の受注アクション (opportunity)
- サポート案件の再オープンアクション (incident)
- 営業案件を保留にする (opportunity)

> [!NOTE]
> 業務プロセスに必要な特定の **状態** と **状態コード** 値が定義されているすぐに使用可能なエンティティに **有効化** や **無効化** ボタンを追加するのではなく、ワークフローを作成することをお勧めします。 たとえば、インシデント ([状態オプション](https://docs.microsoft.com/dynamics365/customerengagement/on-premises/developer/entities/incident#statuscode-options)), Opportunity([status options](https://docs.microsoft.com/dynamics365/customerengagement/on-premises/developer/entities/opportunity#statuscode-options))、権利 ([状態オプション](https://docs.microsoft.com/dynamics365/customerengagement/on-premises/developer/entities/entitlement#statuscode-options))。 


## <a name="geolocation-configuration-for-entity-forms"></a>エンティティ フォーム用の物理的場所の構成

地図コントロールを表示するよう管理されたフォームを構成し、地図上のピンとして既存の位置を表示するか、ユーザーが位置を指定する機能を提供できます。 [物理的場所を追加する](add-geolocation.md) を参照してください。

位置フィールドに値を割り当てたりそこから値を取得したりするには、様々な位置フィールドの ID をフォームのマップ コントロールに伝えるための追加の構成が必要です。 エンティティ フォーム レコードには、指定する必要のある、これらのフィールド マッピングを定義する構成セクションがあります。 フィールド名は、作成したスキーマによってそれぞれ異なります。

![エンティティ フォームの位置情報データ](../media/geolocation-managed-form.png "エンティティ フォームの位置情報データ") 

> [!Note]
> - 読み取り専用のエンティティ フォームのアドレス フィールドは、物理的場所が有効になっている場合、マップで置き換えられます。
> - 物理的場所セクションは、ドイツの主権クラウド環境では表示されません。 ユーザーが別のフォームを使用して物理的場所を有効にしている場合、ポータルでレンダリング中には表示されません。

## <a name="request-validation"></a>要求の検証

[リクエストの検証](https://docs.microsoft.com/aspnet/whitepapers/request-validation)、バージョン1.1以降の ASP.NET の機能により、サーバーはエンコードされていないHTMLを含むコンテンツを受け入れなくなりました。 この機能は、クライアント スクリプト コードまたは HTML が気付かないうちにサーバに送信、保存され、他のユーザに提示されてしまう可能性のあるスクリプト インジェクション攻撃を防ぐために設計されています。 すべての入力データを検証し、必要に応じて HTML エンコードすることを推奨します。

デフォルトでは、要求の検証はポータル上で有効になっており、エンティティ フォーム フィールド内で HTML エンコーディングなしでスクリプト ードを入力すると、次の一般的なエラーが発生します。

![要求検証エラー](../media/request-validation-error.png)

検証の要求を無効化するには、次の手順に従ってください。

1. [ポータルの構成](https://docs.microsoft.com/powerapps/maker/portals/manage-existing-portals#settings) に移動し、 **サイトの設定** を選択します。

1. **新規**を選択します。

1. 名前に **DisableValidationWebTemplate** を入力してください。

1. 適切な Web サイトのレコードを選択します。

1. 値には**真**を入力します。 既定では、設定は**偽**となっており、検証の要求が有効化されています。

1. 適切な説明を入力します。

1. **保存して閉じる**を選択します。

> [!CAUTION]
> 検証の要求が無効になっている場合は、コンテンツをページに送信できます。 コンテンツが適切にエンコード、または処理されていることを確認してください。

### <a name="see-also"></a>関連項目

[ポータルの構成](configure-portal.md)  
[ポータルの Web フォームのプロパティ](web-form-properties.md)  
[ポータルの Web フォームの手順](web-form-steps.md)  
[ポータルの Web フォームのメタデータ](configure-web-form-metadata.md)  
[ポータルの Web フォームのサブグリッド構成](configure-web-form-subgrid.md)  
[ポータルのエンティティ フォームおよび Web フォームのメモの構成](../configure-notes.md)
