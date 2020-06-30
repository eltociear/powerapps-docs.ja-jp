---
title: Power Apps を使ったコンポーネントを持つユーザー定義エンティティの作成 | Microsoft Docs
description: Power Apps アプリで使用するエンティティを作成および構成するための詳細な手順を説明します。
author: Mattp123
manager: kvivek
ms.service: powerapps
ms.component: cds
ms.topic: tutorial
ms.date: 01/23/2019
ms.author: matp
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5f9a7fbc708ad67a31217f87e6ae189c5b5283d8
ms.sourcegitcommit: 04893378fd8914edcc9c9d1cfaf244a29f020649
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "3385411"
---
# <a name="create-a-custom-entity-that-has-components-in-power-apps"></a>Power Appsにコンポーネントが存在するユーザー定義エンティティの作成

Power Apps を使えば、組織が属する業種、専門用語、固有のビジネス プロセスに合わせてアプリをカスタマイズすることができます。 Power Apps アプリ開発には、標準の "簡単に使える" エンティティを追加したり、ユーザー定義エンティティの作成が含まれています。 エンティティは、レコードの形式で追跡する情報を定義します。通常は会社名、場所、製品、電子メール、電話などのプロパティが含まれます。 

このトピックでは、エンティティを作成し、フィールド、関係、ビュー、フォームなどの主要コンポーネントを追加またはカスタマイズします。 以下の方法を説明します。

- ユーザー定義エンティティの作成
- エンティティにユーザー定義フィールドを追加する
- エンティティ関係の追加
- ビューのカスタマイズ 
- フォームのカスタマイズ

トピックは、犬と猫をグルーミングするペット グルーミング企業である Contoso に従います。 Contoso には、さまざまなデバイスで従業員が使用できるクライアントおよびペット追跡用のアプリが必要です。

## <a name="prerequisites"></a>前提条件

[Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインします。 まだ Power Apps アカウントを持っていない場合、 [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) の **無料で使用開始する** リンクを選択します。

## <a name="create-a-custom-entity"></a>ユーザー定義エンティティの作成

1. 左側のナビゲーション ウィンドウで、**データ**を展開して**エンティティ**を選び、**新しいエンティティ**を選択します。

    > [!div class="mx-imgBorder"] 
    > ![エンティティの新規作成](media/create-custom-entity/create-new-entity.png)

2. 右側のウィンドウで、次の値を入力し、**作成**を選択します。

    - **表示名**: *[Pet] ペット* 
    - **説明**: *ペット サービスを追跡するユーザー定義エンティティ*

## <a name="add-and-customize-fields"></a>フィールドを追加してカスタマイズ
 
1. エンティティの一覧で、前のセクションで作成された**Pet ペット** エンティティを選択します。

2. **フィールド** タブで、**Pet ペット** フィールドを選択します。

3. 右側のウィンドウで、**表示名**フィールドに対して次の変更を加えます。 

    - **表示名**を**Pet ペット**から*ペット名*に変更する
    -   **検索可能**を選びます。  
  
      > [!div class="mx-imgBorder"] 
      > ![プライマリ フィールドの変更](media/create-custom-entity/primary-field.png)

4. **完了**を選択します。

5. エンティティ デザイナー ツール バーの**フィールド** タブで、**フィールドの追加**を選択します。 **フィールドのプロパティ** ウィンドウで、次の値とオプションを入力または選択します。
    - **表示名**。 *[Species] 種類*
    - **データの種類**。 *オプション セット*
    - **オプション セット**。 *新しいオプション セット*
  
6. **さらに表示**を選択して、次に**ローカル オプション セット**を選択します。

7. オプション セットの作成

      a. **新しいオプション**を*犬*に置き換えます。 
      
      b. **新しい項目の追加**を選択します。 
        
      c.  **新しいオプション**を*猫*に置き換えます。 
        
      d. **保存**を選択します。 

    > [!div class="mx-imgBorder"] 
    > ![新しいオプション セット](media/create-custom-entity/optionset-add-items.png)

6. **検索可能**を選択し、**完了**を選択します。

7. エンティティ デザイナー ツール バーで、**フィールドの追加**を選択します。 **フィールドのプロパティ** ウィンドウで、次の値を入力または選択し、**完了**を選択します。
    - **表示名**。 *[Breed] ブリーディング*
    - **データの種類**。 *テキスト*

8. **検索可能**を選択し、**完了**を選択します。

8. エンティティ デザイナー ツール バーで、**フィールドの追加**を選択します。 

9. **フィールドのプロパティ** ウィンドウで、次の値を入力または選択し、**完了**を選択します。 
    -   **表示名**。 *[Appointment date] 予定の日付*
    - **データの種類**。 *日付と時刻*

10. **完了** を選択します。

## <a name="add-a-relationship"></a>関係の追加

1. **リレーションシップ**タブを選択し、エンティティ デザイナー ツール バーで**リレーションシップの追加**を選択し、**多対一** を選択します。

2. 右側のウィンドウの**関連**の一覧で、**取引先企業**を選択します。

3. **完了**を選択します。

4. **エンティティの保存**を選択します。

  多対一の関係を追加すると、データの種類が**検索**の**取引先企業**フィールドが**フィールド** タブのフィールドの一覧に自動的に追加されることに注意してください。
  > [!div class="mx-imgBorder"]
  > ![取引先企業検索フィールド](media/create-custom-entity/account-lookup-field.png)

## <a name="customize-a-view"></a>ビューのカスタマイズ

1. **ビュー** タブを選択し、**アクティブなペット** ビューを選択します。 **アクティブ ペット**ビューが表示されない場合、コマンド バーのフィルターを**デフォルト**から**すべて**に変更します。

2. ビュー デザイナーで**列の追加**を選択し、次の列を選択して **OK** を選択します。

    - 取引先企業
    - [Appointment date] 予定の日付 
    - 品種 
    - 種

3. **作成日**列を選択し、**削除**を選択します。

4. 列を並べ替えるには、移動させる列を選択し、**左に移動**と**左に移動**を使用してビューを変更します。
    > [!div class="mx-imgBorder"] 
    > ![アクティブなペット ビュー](media/create-custom-entity/active-pets-view.png)

5. ビュー デザイナーのツールバーで、**保存**を選択します。  

## <a name="model-driven-apps-only-customize-the-main-form"></a>モデル駆動型アプリ: メイン フォームをカスタマイズする

キャンバスの アプリでペット エンティティを使用する場合は、この手順は省略します。 

1. 左側のナビゲーション ウィンドウで、**データ**を展開して**エンティティ**を選び、**Pet ペット**を選択します。

2. **フォーム**タブを選択し、**メイン**フォームの隣の**情報**を選択して、フォーム デザイナーを開きます。

    > [!div class="mx-imgBorder"] 
    > ![メイン フォームの編集](media/create-custom-entity/main-form-edit.png)

3. フォーム エディターで、フィールド エクスプローラー ウィンドウにある**Species 種類**、**Breed ブリーティング**、**Appointment date 予定の日付**、**Account 取引先企業**フィールドを、フォームが次のようになるまでフォーム キャンバスの全般セクションにドラッグ アンド ドロップします。

    > [!div class="mx-imgBorder"] 
    > ![メイン フォームにフィールドを選択](media/create-custom-entity/main-form-edit2.png) 

4. **保存**を選択します。

5. **発行**を選択します。

6. Power Apps ホーム ページに戻ります。

## <a name="add-the-custom-entity-to-an-app"></a>アプリにユーザー定義エンティティを追加する

これで、キャンバスまたはモデル駆動型アプリをビルドするために、エンティティを使用する準備が整いました。 

## <a name="next-steps"></a>次のステップ

このトピックでは、役に立つアプリの作成に使用できるエンティティの作成方法について学びました。 
- モデル駆動型のアプリの作成方法については、「[最初のモデル駆動型アプリの作成](../model-driven-apps/build-first-model-driven-app.md)」を参照してください。
- キャンバス アプリを作成する方法について詳しくは、「[アプリを最初から作成する](../canvas-apps/get-started-create-from-blank.md)」を参照してください。
