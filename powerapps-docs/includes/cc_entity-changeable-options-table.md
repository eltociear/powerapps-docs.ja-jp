|オプション   |説明  |
|---------|---------|
|**アクセス チーム**|このエンティティのチーム テンプレートを作成します。 |
|**簡易作成を許可**|このエンティティの**簡易作成フォーム**を作成して公開すると、ナビゲーション ウィンドウの**作成**ボタンを使用して新しいレコードを作成するオプションを使用できます。 詳細情報: [フォームの作成と設計](../maker/model-driven-apps/create-design-forms.md)<br /><br /> これがユーザー定義活動エンティティに対して有効になると、ナビゲーション ウィンドウの**作成**ボタンを使用するときに、ユーザーが定義した活動が活動エンティティのグループに表示されます。 ただし、活動は簡易作成フォームをサポートしていないので、カスタム エンティティ アイコンをクリックしたときは、メイン フォームが使用されます。|
|**このエンティティが表示される領域**|Web アプリケーションでこのエンティティを表示するために利用可能なサイトマップ領域の 1 つを選択します。 これはモデル駆動型アプリには適用されません。|
|**監査**|監査が組織に対して有効になっている場合、エンティティ レコードの変化を時系列で取得することができます。 エンティティの監査を有効にすると、そのエンティティのすべてのフィールドの監査も有効になります。 監査を有効にするフィールドを選択またはクリアできます。|
|**変更履歴**|データが最初に抽出されてから、または最後に同期されてからどのデータが変更されたかを検出することによって、効率の良いデータ同期を可能にします。  |
|**色**|モデル駆動型アプリでエンティティに使用する色を設定します。|
|**説明**|エンティティの目的を示すわかりやすい説明を入力してください。|
|**ドキュメント管理**|組織のドキュメント管理を有効にするための他のタスクが完了した後、この機能を有効にすることによって、エンティティを SharePoint との統合に関与させることができます。 |
|**重複データ検出**|重複データ検出が組織に対して有効になっている場合、このオプションを有効にすることによって、このエンティティの重複データ検出ルールを作成できます。|
|**モバイルの有効化**|このエンティティを、Dynamics 365 for phones と Dynamics 365 for tablets のアプリで使用できるようにします。 また、このエンティティを**モバイルでは読み取り専用**にすることも選択できます。<br /><br /> エンティティのフォームで、Dynamics 365 for phones と Dynamics 365 for tablets のアプリでサポートされていない拡張機能が必要な場合は、この設定を使用して、これらのエンティティのデータをモバイル アプリ ユーザーが編集できないようにします。|
|**Phone Express の有効化**|このエンティティを、Dynamics 365 for phones アプリで使用できるようにします。|
|**差し込み印刷**|差し込み印刷でこのエンティティを使用できます。|
|**Dynamics 365 for Outlook のオフライン機能**|Dynamics 365 for Outlook アプリケーションがネットワークに接続していない間、このエンティティのデータが使用可能かどうか。|
|**プライマリ イメージ**|イメージをサポートするシステム エンティティには、**イメージ** フィールドがすでにあります。 このフィールドを **[なし]** または**既定のイメージ**に設定することによって、このフィールドのデータをレコードのイメージとして表示するかどうかを選択できます。<br /><br /> ユーザー定義エンティティについては、最初にイメージ フィールドを作成する必要があります。 各エンティティにはイメージ フィールドを 1 つのみ設定できます。 イメージ フィールドを 1 つ作成すると、この設定を変更してプライマリ イメージを設定できます。 詳細情報: [イメージ フィールド](../maker/common-data-service/types-of-fields.md#image-fields) |
|**Dynamics 365 for Outlook の閲覧ウィンドウ**|エンティティが Dynamics 365 for Outlook アプリ用の閲覧ウィンドウに表示されるかどうか。|
|**カスタム ヘルプを使用する**|有効にした場合、ヘルプ URL を設定して、ユーザーがアプリケーションのヘルプ ボタンをクリックしたときに表示されるページをコントロールします。 これは、エンティティの企業プロセスに特有のガイダンスを提供するために使用します。|