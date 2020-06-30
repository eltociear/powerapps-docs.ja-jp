---
title: Web ページの作成 | Microsoft Docs
description: ポータルの Web ページを構成するための手順
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 05/11/2020
ms.author: nenandw
ms.reviewer: tapanm
ms.openlocfilehash: 2181d8211c6bfbdacb70c43433e0c03e7f0f66d0
ms.sourcegitcommit: ef921bbf0908283a3621c2ca1069e6b58a2b14e7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2020
ms.locfileid: "3373709"
---
# <a name="compose-a-page"></a>ページの作成

必要な Web ページを追加して、サイトマップ内の階層を管理すると、さまざまなコンポーネントを追加できます。 WYSIWYG エディターを使用すると、キャンバス上の必須コンポーネントを簡単に追加および編集できます。 キャンバスに、次のコンポーネントを追加および編集できます。

- セクション
    - 1 列のセクション
    - 2 列のセクション
    - 3 列のセクション
- ポータル コンポーネント
    - Text
    - イメージ
    - [IFrame]
    - [フォーム]
    - 一覧取得
    - 階層リンク

> [!NOTE]
> Power Apps ポータル スタジオを使用してポータルをカスタマイズすると、Web サイトのユーザーはパフォーマンスに影響を与えることに気付くはずです。 ライブ ポータルのピーク以外の時間帯に変更を行うことをお勧めします。 

## <a name="use-the-wysiwyg-editor"></a>WYSIWYG エディターの使用

1.  [ポータルを編集](manage-existing-portals.md#edit) して、ポータルを Power Apps ポータル Studioで開きます。  

2.  どのページに対してコンポーネントを追加するかを選択します。

3.  キャンバスで編集可能な要素を選択します。

    > [!NOTE]
    > 編集可能な要素は境界で区切られます。

4.  画面左側から、 **コンポーネント** ![コンポーネント アイコン](media/components-icon.png "コンポーネント アイコン")を選択します。  

5.  追加するコンポーネントを選択します。

    > [!div class=mx-imgBorder]
    > ![コンポーネント ウィンドウ](media/components-pane.png "コンポーネント ウィンドウ")  

    選択したコンポーネントが、編集可能な要素内のキャンバスに追加されます。

6.  コンポーネントを削除するには、キャンバスでコンポーネントを選択し、ページ上部のコマンド バーで**削除**を選択します。

    > [!div class=mx-imgBorder]
    > ![コンポーネントの削除](media/delete-component.png "コンポーネントの削除")  

## <a name="add-sections"></a>セクションの追加

セクションを使用すると、ページの構造を定義し、ポータルのコンポーネントを配置できます。

ページにセクションを追加したら、要件に応じてセクション内にポータル コンポーネントを追加できます。

1.    [ポータルを編集](manage-existing-portals.md#edit) して、ポータルを Power Apps ポータル Studioで開きます。

2.    セクションを追加するページを選択します。

3.    キャンバスで編集可能な要素を選択します。

4.    画面左側から、 **コンポーネント** ![コンポーネント アイコン](media/components-icon.png "コンポーネント アイコン")を選択します。

5.    **セクション レイアウト**で、挿入するセクションの種類を選択します。

6.    画面右側のプロパティ ウィンドウで、次の情報を入力または選択します。

    - **最小の高さ**: セクションの最小の高さを入力します。 指定した高さよりも多くのスペースを占めるコンポーネントを追加すると、セクションがコンポーネントに合わせて拡大します。 既定では、最小の高さは 100 px です。 高さをポイント (pt) とパーセンテージ (%) で入力することもできます。

        > [!div class=mx-imgBorder]
        > ![セクション内の配置](media/section-props-height.png "セクション内の配置")  

    - **配置**: セクション内のコンポーネントを左揃え、中央揃え、または右揃えにする必要があるかどうかを選択します。

        > [!div class=mx-imgBorder]
        > ![セクション内の配置](media/section-props-align.png "セクション内の配置")  

    - **バックグラウンド** : セクションのバックグラウンドに、色または画像を使用するかどうかを選択します。

        - **塗りつぶし**: バックグラウンドの色を選択します。

            > [!div class=mx-imgBorder]
            > ![セクション内の色を塗りつぶす](media/section-props-fill.png "セクション内の色を塗りつぶす")  

        - **画像**: 一覧から画像を選択します。 新しい画像をアップロードする場合は、**画像のアップロード**を選択します。

            > [!div class=mx-imgBorder]
            > ![セクション内に画像を追加する](media/section-props-image.png "セクション内に画像を追加する")  

7.    セクション内に必須ポータル コンポーネントを追加します。


## <a name="add-portal-components"></a>ポータル コンポーネントの追加

Web ページで次のコンポーネントを追加できます。

- [テキスト](#add-text-box)
- [イメージ](#add-image)
- [IFrame](#add-iframe)
- [フォーム](#add-form)
- [リスト](#add-list)
- [階層リンク](#add-breadcrumb)
- [Power BI](#add-power-bi)


### <a name="add-text-box"></a>テキスト ボックスの追加

1.  [ポータルを編集](manage-existing-portals.md#edit) して、ポータルを Power Apps ポータル Studioで開きます。  

2.  どのページに対してコンポーネントを追加するかを選択します。

3.  キャンバスで編集可能な要素を選択します。

4.  画面左側から、 **コンポーネント** ![コンポーネント アイコン](media/components-icon.png "コンポーネント アイコン")を選択します。  

5.    **ポータル コンポーネント**で、**テキスト**を選択します。

6.  テキスト ボックスに必要なテキストを入力します。

7.  テキストの書式を設定するには、書式設定のオプションを表示するためのテキストを選択します。 フォント サイズを変更し、必要に応じてスタイルを作成します。

    > [!div class=mx-imgBorder]
    > ![テキスト コンポーネント](media/text-component.png "テキスト コンポーネント")  

8. 画面右側のプロパティ ウィンドウで、次の情報を選択します。

    - **配置**: テキストを左揃え、中央揃え、または右揃えにする必要があるかどうかを選択します。

    - **フォントの色**: テキストの色を選択します。

        > [!div class=mx-imgBorder]
        > ![テキストの配置と色の選択](media/text-props.png "テキストの配置と色の選択")  
 

### <a name="add-image"></a>画像の追加

1.  [ポータルを編集](manage-existing-portals.md#edit) して、ポータルを Power Apps ポータル Studioで開きます。  

2.  どのページに対してコンポーネントを追加するかを選択します。

3.  キャンバスで編集可能な要素を選択します。

4.  画面左側から、 **コンポーネント** ![コンポーネント アイコン](media/components-icon.png "コンポーネント アイコン")を選択します。  

5.  **ポータル コンポーネント**で、**画像**を選択します。 画像プレースホルダーがキャンバスに追加されます。

6.  画面右側のプロパティ ウィンドウで、次の情報を入力します。

    - **画像**: 既存の画像を選択するか、または新しい画像をアップロードする場合は、このオプションを選択します。 以前にアップロードされた画像を選択する場合は、**画像の選択**のリストから選択します。 新しい画像をアップロードする場合は、**画像のアップロード**を選択します。 アップロードされたすべての画像は画像ライブラリに含まれており、**画像の選択**のリストから再び選択できます。

        > [!div class=mx-imgBorder]
        > ![画像のプロパティ](media/image-props.png "画像のプロパティ")  

        > [!NOTE]
        > - 最大 5 MB の png、svg、jpg、jpeg 形式の画像のみをアップロードできます。
        > - 同じ名前の画像はアップロードできません。 画像の名前を変更して再度アップロードする必要があります。

    - **外部 URL**: 外部 URL からの画像をアップロードする場合は、このオプションを選択します。 **外部 URL** フィールドに URL を入力します。 セキュリティで保護されたリンクのみを入力できます。従って、必ず https:// で始まります。 コンテンツ配信ネットワークに画像が保存されている場合、このフィールドにリンクを提供できます。

        > [!div class=mx-imgBorder]
        > ![外部 URL の画像](media/image-ext-url.png "外部 URL の画像")  

    -   **書式設定オプション**

        - **幅**: 画像の幅を入力します。

        - **高さ**: 画像の高さを入力します。

    > [!NOTE]
    > キャンバスの画像を選択し、ハンドルをドラッグしてサイズを変更できます。

### <a name="add-iframe"></a>IFrame の追加

1.  [ポータルを編集](manage-existing-portals.md#edit) して、ポータルを Power Apps ポータル Studioで開きます。  

2.  どのページに対してコンポーネントを追加するかを選択します。

3.  キャンバスで編集可能な要素を選択します。

4.  画面左側から、 **コンポーネント** ![コンポーネント アイコン](media/components-icon.png "コンポーネント アイコン")を選択します。  

5.  **ポータル コンポーネント**で、**IFrame** を選択します。 IFrame プレースホルダーがキャンバスに追加されます。

6.  画面右側のプロパティ ウィンドウで、次の情報を入力します。

    - **幅**: IFrame の幅を入力します。

    - **高さ**: IFrame の高さを入力します。

        > [!NOTE]
        > キャンバスの IFrame を選択し、ハンドルをドラッグしてサイズを変更できます。

    - **リンク**: IFrame で表示する Web サイトの URL を入力します。 セキュリティで保護されたリンクのみを入力できます。従って、必ず https:// で始まります。 既定では、<https://www.bing.com> が値として利用可能です。
    
        > [!div class=mx-imgBorder]
        > ![IFRAME のプロパティ](media/iframe-props.png "IFrame のプロパティ")  

> [!NOTE]
> また、 [ウェブサイトのボットを追加する](https://docs.microsoft.com/power-virtual-agents/publication-connect-bot-to-web-channels#custom-website) に記載されている手順と同様の方法で [Power Virtual Agent](https://docs.microsoft.com/power-virtual-agents/fundamentals-what-is-power-virtual-agents) ボットを IFrame に追加することもできます。

### <a name="add-form"></a>フォームの追加

フォームとは、開発者がポータル内でフォームを露見させることなく、ポータル内でデータを収集するデータ駆動型の構成です。 

フォームは [Common Data Service で作成されます](https://docs.microsoft.com/powerapps/maker/model-driven-apps/form-designer-overview)。 ポータル内の Web ページやリストと組み合わせて使用することで、完全な Web アプリケーションを構築することができます。  

1.  [ポータルを編集](manage-existing-portals.md#edit) して、ポータルを Power Apps ポータル Studioで開きます。  

2.  どのページに対してコンポーネントを追加するかを選択します。

3.  キャンバスで編集可能な要素を選択します。

4.  画面左側から、 **コンポーネント** ![コンポーネント アイコン](media/components-icon.png "コンポーネント アイコン")を選択します。  

5.  **ポータル コンポーネント**で、**フォーム**を選択します。

6.  画面右側のプロパティ ウィンドウで、次のオプションから 1 つ選択します。

    - **新規作成**: 新しいフォームを作成します。
    - **既存を使用**: 既存のフォームを使用します。

7. 情報を入力、または選択してください :

    - **名前**: フォームの名前です。

    - **エンティティ** : フォームの読み込み元のエンティティの名前。

    - **フォーム レイアウト**: レンダリングされる Common Data Service のターゲット エンティティにあるフォームの名前。

    - **モード**: 次のいずれかのオプションを選択してください。

        - **挿入**: 送信時に、フォームが新しいレコードを挿入する必要があることを示します。

        - **編集**: フォームが既存のレコードを編集する必要があることを示します。

        - **読み取り専用** : 既存のレコードの編集不可能なフォームを表示することを示します。

        > [!NOTE]
        > **編集**モードおよび**読み取り専用**モードの既定のオプションは、 URL で ID として渡されるクエリ文字列パラメーター名として設定されます。 これらの値を変更するには、ポータル管理アプリを開き、フォームのプロパティを更新する必要があります。

    - **成功時**: 次のいずれかのオプションを選択します。

        - **成功メッセージの表示**: フォームの送信に成功すると、ユーザーにメッセージを表示する必要があります。 また、**成功時にフォームを非表示にする**を選択して、送信の成功時にフォームを非表示にすることもできます。

        - **Web ページにリダイレクト**: ポータルの選択した Web ページにユーザーをリダイレクトします。 これは必須フィールドです。

        - **URL にリダイレクト**: 指定した URL にユーザーをリダイレクトします。 これは必須フィールドです。

    - **匿名ユーザーに画像文字を表示**: 匿名ユーザーに画像文字を表示します。

    - **認証されたユーザーに画像文字を表示**: 認証されたユーザーに画像文字を表示します。

    - **エンティティのアクセス許可を有効にする**:エンティティのアクセス許可がフォームで考慮されます。 既定では選択されません。 選択された場合、フォームにアクセスする必要のあるユーザーには、明示的なアクセス許可が必要です。 詳細: [エンティティのアクセス許可](configure/assign-entity-permissions.md)

        > [!div class=mx-imgBorder]
        > ![フォームのプロパティ](media/form-props.png "フォームのプロパティ")

### <a name="add-list"></a>リストの追加

リストは、ポータル内のグリッドを開発者が露見させることなく、レコードのリストをレンダリングするデータ駆動型の構成です。

リストは、[Common Data Service ビュー](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-and-edit-views)を使用して、ポータルのレコードを表示します。  

1.  [ポータルを編集](manage-existing-portals.md#edit) して、ポータルを Power Apps ポータル Studioで開きます。  

2.  どのページに対してコンポーネントを追加するかを選択します。

3.  キャンバスで編集可能な要素を選択します。

4.  画面左側から、 **コンポーネント** ![コンポーネント アイコン](media/components-icon.png "コンポーネント アイコン")を選択します。  

5.  **ポータル コンポーネント**で、**リスト**を選択します。

6.  画面右側のプロパティ ウィンドウで、次のオプションから 1 つ選択します。

    - **新規作成**: 新しいリストを作成します。
    - **既存を使用**: 既存のリストを使用します。

7.  情報を入力、または選択してください :

    - **名前**: リストの名前です。

    - **エンティティ** : ビューの読み込み元のエンティティの名前。

    - **ビュー**: 表示されるターゲット エンティティのビューのリスト。 複数のビューを選択して、リストにレコードを表示できます。 最初に選択されたビューが既定のビューとなります。

    - **新しいレコードの作成**: ユーザーは新しいレコードを作成できます。 フォームを含む Web ページを選択して、新しいレコードを作成します。

    - **詳細の表示**: ユーザーが詳細を表示できるようにします。 フォームを含む Web ページを選択して、詳細を表示します。

    - **レコードの編集**: ユーザーはレコードを編集できます。 フォームを含む Web ページを選択して、レコードを編集します。

    - **レコードの削除**: ユーザーはレコードを削除できます。

    - **空のリストのメッセージ**: 表示するレコードがないときに表示されるメッセージです。

    - **ページあたりのレコード数** : ページに表示するレコード数を入力します。

    - **エンティティ リストでの検索を有効にする**: ユーザーが一覧でレコードを検索できるようになります。

    - **エンティティのアクセス許可を有効にする**:エンティティのアクセス許可がリストで考慮されます。 既定では選択されません。 選択された場合、フォームにアクセスする必要のあるユーザーには、明示的なアクセス許可が必要です。 詳細: [エンティティのアクセス許可](configure/assign-entity-permissions.md)  

    > [!div class=mx-imgBorder]
    > ![リストのプロパティ](media/list-props.png "リストのプロパティ")

### <a name="add-breadcrumb"></a>階層リンクの追加

1.  [ポータルを編集](manage-existing-portals.md#edit) して、ポータルを Power Apps ポータル Studioで開きます。  

2.  どのページに対してコンポーネントを追加するかを選択します。

3.  キャンバスで編集可能な要素を選択します。

4.  画面左側から、 **コンポーネント** ![コンポーネント アイコン](media/components-icon.png "コンポーネント アイコン")を選択します。  

5.  **ポータル コンポーネント**で、**階層リンク** を選択します。

## <a name="add-a-custom-menu"></a>カスタム メニューの追加

既定では、Web サイトのメニューは Web ページの階層に基づいて自動的に作成されます。 これは **既定**のメニューと呼ばれます。 カスタム メニューを作成するには、ポータル管理アプリで Web リンク セットを作成する必要があります。 詳細: [Web リンクの管理](configure/manage-web-links.md)

Web リンク セットの作成後は、次を行います。

1.    [ポータルを編集](manage-existing-portals.md#edit) して、ポータルを Power Apps ポータル Studioで開きます。

2.    ヘッダー コンポーネントを選択します。 

3.    画面の右側のプロパティで、**ナビゲーション メニュー**のリストから Web リンク セットの名前を選択します。

    > [!div class=mx-imgBorder]
    > ![ナビゲーション メニュー](media/navigation-menu.png "ナビゲーション メニュー")

## <a name="use-code-editor"></a>コード エディターの使用

キャンバスのコンポーネントのソースを表示するには、コンポーネントを選択し、フッターのソース コード エディターのアイコン**&lt;/&gt;** を選択します。

> [!div class=mx-imgBorder]
> ![コード エディター アイコン](media/code-editor-icon.png "コード エディター アイコン")  

ソース コードは画面の一番下の**コード エディター** ウィンドウに表示されます。 先に加えた変更によりソース コードが更新されます。 変更を加えるには、ソース コードを更新し、**保存**を選択します。 キャンバスに変更が反映されます。

> [!div class=mx-imgBorder]
> ![コード エディター](media/code-editor.png "コード エディター") 

> [!NOTE]
> また、ソース コード エディターに Liquid タグを追加して、高度な構成を行うこともできます。 詳細: [Liquid テンプレートに関する作業](liquid/liquid-overview.md)

## <a name="add-power-bi"></a>Power BIの追加

ページに Power BI のコンポーネントを追加して、ポータル上に Power BI のダッシュボードやレポートを表示させることができます。

> [!NOTE]
> 開始する前に、[Power BI のアクセス タイプに関する考慮事項](#power-bi-access-type-considerations) および [Power BI の一般的な考慮事項](#general-power-bi-considerations)を参照しておくと、 Power Apps ポータルの重要な Power BI 用語や注意点を知ることができます。

Web ページに Power BI コンポーネントを追加するには :

1. [ポータルを編集する](../portals/manage-existing-portals.md#edit)。

1. コンポーネントを追加するページを選択します。

1. キャンバスで編集可能な要素を選択します。

1. 画面の左側から **コンポーネント** を選択します。

1. ポータルコンポーネント セクションから、 **Power BI**を選択します。 Power BI プレースホルダーがキャンバスに追加されます :

    ![コンポーネント](media/components-powerbi.png)

1. 画面右側のプロパティ ウィンドウで、次の情報を入力します。

    1. **アクセス タイプ** : 要件に応じて、ドロップダウンから適切なオプションを選択します。

        ![Power BI のアクセスの種類](media/powerbi-access-type.png "Power BI アクセスの種類")

        1. **顧客向けの埋め込み** - Power BI のライセンスや Azure Active Directory 認証の設定をしなくても、安全に Power BI ダッシュボードやレポートを外部ユーザーに共有することができます。 このオプションでは、Power BI Embedded サービスを利用して、Power BI のダッシュボードやレポートをポータルに統合することができます。
            > [!NOTE]
            > [Power BI Embedded サービスが有効化](../portals/admin/set-up-power-bi-integration.md#enable-power-bi-embedded-service)されていることと、それぞれの Power BI ワークスペースが選択されていることを確認し、メーカーまたはログインユーザーと共有してください。

        1. **組織向けの埋め込み** - Power BI ダッシュボードまたはレポートを Azure Active Directory 認証されたユーザに安全に共有することができます。

            > [!NOTE]
            > Power BI ワークスペースをメーカーや対象とするポータルのユーザーと共有していることを確認してください。

        3. **Web に公開する** - インターネット上の誰とでも Power BI レポートやダッシュボードを共有することができます。

        アクセス タイプの詳細については、[アクセス タイプ](#power-bi-access-type-considerations)に移動します。

    1. **ワークスペース** : リストから Power BI ワークスペースを選択します。

    1. **タイプの選択** : リストからタイプに*ダッシュボード* または *レポート*を選択します。

        ![種類の選択](media/type-powerbi.png "種類の選択")

        - **ダッシュボード** - **ダッシュボード**を選択し、選択したダッシュボードから **タイル** を選択して Web ページに表示することができます。
        - **レポート** - **レポート**を選択し、レポートから **ページ** を選択して Web ページに表示することができます。

    1. **ロールの適用** : Power BI でロールを定義してレポートに割り当てている場合は、この欄に適切なロールを入力する必要があります。

        ![ ロールの適用](media/apply-roles-powerbi.png "ロールの適用")
    
        - カンマで区切って複数のロールを入力することができます (入力例 :  ```role_1,role_2```)。 Power BIにおける役割の定義に関する詳細情報については、 [ Power BI の行レベルセキュリティ (RLS)](https://docs.microsoft.com/power-bi/service-admin-rls) を参照してください。 <br>
        - アクセス タイプ **組織向けの埋め込み** でのみ使用可能です。

    1. **フィルターを適用** : あらかじめフィルター処理された値でレポートを読み込むことができます。 ユーザーはフィールドでフィルターの条件を指定できます。 
        
        ![フィルターの適用](media/apply-filter-powerbi.png "フィルターの適用")

        - フィルターのパラメーターには、```?filter=``` 接頭辞を含めてはいけません。 たとえば、```Table/Field eq 'value'``` などとします。
        <br> 詳細については、[フィルター パラメーターの詳細](https://docs.microsoft.com/power-bi/service-url-filters)に移動してください。
        - アクセス タイプの **顧客向けの埋め込み** と **組織向けの埋め込み** を持つ **レポート**でのみ利用可能です。

    1. **埋め込みコード URL** : 埋め込みコードの URL を入力します。
    
        ![埋め込みコードの URL](media/embed-code-url.png "埋め込みコードの URL")

        - 埋め込みコードの URL を取得する方法については、[Power BI からウェブに公開する](https://docs.microsoft.com/power-bi/service-publish-to-web) にアクセスしてください。
        - アクセス タイプ **ウェブに公開する** でのみ使用可能です。

### <a name="power-bi-access-type-considerations"></a>Power BIアクセス タイプに関する考慮事項

次のリストでは、Power BI のアクセス タイプの概要について解説します。 また、Power Apps ポータルにおけるアクセス タイプに関する考慮事項をリストします。 Power BI のアクセスタイプに関する詳細については、[Power BIサービスと Power BI embedded の違い](https://docs.microsoft.com/power-bi/developer/embedded/embedded-faq#how-is-power-bi-embedded-different-from-power-bi-the-service)にアクセスしてください。

- **顧客向けの埋め込み** :
    - 現在[Power BI Embedded サービス](../portals/admin/set-up-power-bi-integration.md#enable-power-bi-embedded-service)にログインしているユーザーと、共有されているワークスペースの一覧が表示されます。
    - Power BI Embedded サービスを使用する。
    - 以前に Power Apps ポータルで Power BI Embedded サービスを利用したことがある場合は、**顧客向けの埋め込み**を選択すると以下のようなエラーが表示されます :

        ![Power BI の顧客向けの埋め込み - 再度視覚化を有効にする](media/embed-power-bi-visualization-enable-again.png)
    
        これが発生した場合は、[無効化](../portals/admin/set-up-power-bi-integration.md#disable-power-bi-visualization)した後で、Power BI の資格化を再度[有効化](../portals/admin/set-up-power-bi-integration.md#enable-power-bi-visualization)してください。
    - **匿名**で利用できる Power Apps ポータル ページに、**顧客向けの埋め込み**で Power BI を追加すると、誰でもダッシュボードを見ることができます。 このような Web ページを保護するには、[Power Appsポータルにおける Web ページのアクセス制御](../portals/configure/webpage-access-control.md)を参照してください。

- **組織向けの埋め込み** :

    - ログインしているユーザーと共有されているワークスペースのリストを表示します。
    - Azure Active Directory 認証を使用します。

- **Web に公開する** : 公開したレポートをインターネット上のすべてのユーザーが見ることができます。 これには認証は不要で、レポートの集計結果の詳細レベルのデータを表示することも含まれています。 レポートを公開する前に、データや視覚エフェクトを公開しても問題がないかを確認してください。 機密情報は公開しないでください。 公開前に、組織のポリシーを確認してください。

### <a name="general-power-bi-considerations"></a>Power BI の一般的なな配慮

- [ポータル スタジオ](../portals/portal-designer-anatomy.md) Power BI ワークスペースで作業しているときにパフォーマンスが低下する場合は、以下の Power BI ワークスペースの構成に起因していることが考えられます :
    - ログインしているメーカー ユーザーと共有しているワークスペース数が多い。
    - Power BI ワークスペースが多くのユーザーと共有されている。
- Power BI コンポーネントでの作業時には、[液体変数の取得](../portals/liquid/portals-entity-tags.md#powerbi)は、ポータル スタジオではご利用頂けません。
- [ポータルをリセット](../portals/admin/reset-portal.md)して新規ポータルをプロビジョニングする場合は、新規ポータルのポータル アプリケーション ID を**ポータル Power BI Embedded サービス**の Azure AD セキュリティ グループに追加する必要があります。 詳細については、[Power BI の統合を行う設定](../portals/admin/set-up-power-bi-integration.md#create-security-group-and-add-to-power-bi-account)にアクセスしてください。
- Power Apps ポータル管理センターで変更を行った場合、ポータル スタジオが既に開いている場合は、ポータル スタジオを再読込する必要があります。
- Power BI ダッシュボードとレポートへのユーザーの追加をポータル スタジオに反映するには、時間がかかる場合があります。

### <a name="power-bi-performance-and-optimization-considerations"></a>Power BI パフォーマンスと最適化に関する注意事項

複数の Power BI ワークスペースの埋め込み処理には、別途注意が必要となります。 Power BI の埋め込みシナリオに関するトラブル シューティング、最適化、ベスト プラクティスについては、以下のリソースを参照してください :

- [Power BI Embedded アプリケーションのコンテンツ レンダリングに関するトラブルシューティング](https://docs.microsoft.com/power-bi/developer/embedded/embedded-troubleshoot#content-rendering)。
- [Power BI Embedded パフォーマンスのベスト プラクティス](https://docs.microsoft.com/power-bi/developer/embedded/embedded-performance-best-practices)。
- [Power BI の最適化ガイド](https://docs.microsoft.com/power-bi/guidance/power-bi-optimization)。


## <a name="next-steps"></a>次の手順

[テンプレートの操作](work-with-templates.md)