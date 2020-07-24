---
title: Power Apps でタイムラインの制御 (セクション) を設定する | MicrosoftDocs
description: Power Apps で タイムラインの制御 (セクション) を設定する
ms.date: 03/10/2020
ms.service: powerapps
author: kabala123
ms.assetid: 7F495EE1-1208-49DA-9B02-17855CEB2FDF
ms.author: kabala
manager: shujoshi
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: b3dfc60d7c34ca91257d9aaa1b5979d894268866
ms.sourcegitcommit: 3c6c5594b73abd5ff438d50f3b579d56cef7241c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2020
ms.locfileid: "3285973"
---
# <a name="faqs-for-timeline-control"></a>タイム ライン 制御に関するよくある質問

## <a name="why-do-i-receive-the-message-records-could-not-be-loaded-because-of-unexpected-error"></a>「予期しないエラーが発生したため、レコードを読み込むことができませんでした」 とエラーが表示されましたが原因は何ですか？

**タイムライン** セクションは、フォーム カードに関するデータを取得して表示しています。 既定では、タイムラインは次の10個の標準活動エンティティのデータを取得します:

-    電子メール
-    タスク
-    インシデントの解決
-    FAX
-    営業案件のクローズ
-    レター
-    予定
-    電話

管理が次の手順を実行すると、実行時エラーが表示されます。

**手順**
-    ユーザー定義のアクティビティを追加作成する
-    モバイル の ユーザー定義の活動を有効化する
-    すべてのユーザー定義の活動で **カード フォーム** を選択する 

**エラー** 予期しないエラーが発生したため、レコードを読み込むことができませんでした。

   > [!div class="mx-imgBorder"] 
   > ![予期しないエラーが発生したため、レコードを読み込むことができませんでした。](media/timeline-error1.png "予期しないエラーが発生したため、レコードを読み込むことができませんでした。")

このエラーは、データを取得する活動エンティティの数が上限である10件を超えた場合に発生します。

   > [!div class="mx-imgBorder"] 
   > ![問い合わせの リンク エンティティ 数が制限値を超過しました](media/timeline-error2.png "問い合わせのリンク エンティティが最大値を超過しました")

### <a name="workaround"></a>回避策

この問題を回避するには、エンティティの数を10件以下に減らす必要があります。 それには、次の手順に従ってください。

1.  [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインします。

2.  モデル駆動形アプリを開き、コマンド バーの **設定** ![設定](../model-driven-apps/media/powerapps-gear.png) > **詳細設定**を選びます。

3.   **設定** > **カスタマイズ** > **システムのカスタマイズ**の順に移動します。 ソリューション の エクスプローラー ページが 新たなブラウザのウィンドウで 開きます。

4.   既定の ソリューション ウィンドウ の **コンポーネント** 配下の **エンティティ** を展開します。

5.   エンティティを選択し、 **フォーム** を選択します。 この例では、 **取引先企業** の エンティティ を選択します。

6.   **メイン** フォームタイプである、 **対話型エクスペリエンス の取引先企業** のレコードを選択します。 **対話型エクスペリエンスの取引先企業** のフォームが新規ブラウザ ウィンドウで開きます。

      > [!div class="mx-imgBorder"] 
      > ![名前に対話型エクスペリエンス が含まれる エンティティ フォーム を選択します](media/account-interactive-experience.png "名前に対話型エクスペリエンス が含まれる エンティティ フォーム を選択します")

      統一インターフェイスの場合は、 `<Entity> for Interactive experience` という形式のフォーム名称を使用する必要があります。

7.    **タイムライン** セクション の **会話タブ** をダブルクリックします 。 **活動 タブ の プロパティ** ダイアログが表示されます。

      > [!div class="mx-imgBorder"] 
      > ![ソーシャル ウィンドウ で空白の フィールド を ダブル クリック します](media/timeline-conversation-tabs-field.png "ソーシャル ウィンドウ で空白の フィールド を ダブル クリック します")  

8.    **フィルタ―** コンテナの **これらの活動を表示する** フィールドに対して、 **選択したものを表示する** オプションを選択します。

9.    ユーザーに表示する活動を選択します。

10.    **OK** を選び、 **保存** を選択します。

11.    カスタマイズを公開するには **公開** を選択します。


## <a name="why-i-cant-assign-or-delete-an-activity-from-the-timeline"></a>タイムライン から活動の割り当や削除ができないのはなぜですか？

リボンコマンドバーの定義にて、 **割り当て** や **削除** などの **HideCustomActions** のルールを使用している場合は、タイムライン制御にある当該ボタンは機能しません。 コマンドバーのボタンは、タイムライン制御のボタンと同等です。そのため、ユーザーが タイムライン制御で **割り当て** や **削除** のボタンを選択すると、エラーメッセージが表示されます。

**このアクションを実行する権限がありません。システム管理者に問い合わせてください。**

この問題を回避するには、コマンドバー 定義のボタンを 再表示してください。


## <a name="why-my-users-see-different-activities-and-records-in-their-my-activities-stream-in-the-dashboard"></a>ユーザーがダッシュボードの自分の活動ストリームに、さまざまなアクティビティとレコードを表示するのはなぜですか?

ダッシュボードの **自分の活動** ストリームには、特定のユーザーが所有するレコードとアクティビティが表示されます。 たとえば、ユーザー **A** は **A** が所有するレコードとアクティビティを参照し、ユーザー **B** は **B** が所有するレコードとアクティビティを参照します。


## <a name="why-my-agents-see-the-filter-pane-even-when-the-expand-filter-pane-by-default-check-box-is-cleared"></a>規定で [フィルターペインを展開する] チェックボックスがオフになっているのに、エージェントにフィルター ペインが表示されるのはなぜですか?

タイムラインが複数の列に表示される場合、フィルター ウィンドウはタイムライン レコードの横に列として表示されます。 タイムライン構成で **既定でフィルター ウィンドウを展開** チェック ボックスをオフにしても、フィルター ウィンドウは常にエージェントに表示されます。

## <a name="see-also"></a>関連項目

[タイムライン セクションの設定](set-up-timeline-control.md)

[顧客サービス ハブ アプリ の タイムライン セクション](https://docs.microsoft.com/dynamics365/customer-service/customer-service-hub-user-guide-basics#timeline)

[予定、メール、電話、メモ、またはタスク 活動をタイムラインに追加する](../../user/add-activities.md)
