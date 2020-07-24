---
title: ルールの作成 | Microsoft Docs
description: ルールを作成してアプリ ロジックを構築するための詳しい手順
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/23/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 52deddf87a1c3ee4604591110cfb08eb2d2680b8
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2019
ms.locfileid: "3303969"
---
# <a name="create-a-rule-in-canvas-apps"></a>キャンバス アプリでルールを作成する
指定する条件に基づいてアプリを自動的に変更するためのルールを作成します。 たとえば、状態に基づいて品目を赤、黄、または緑で表示したり、特定のユーザー (管理者など) に対してのみ承認ボタンを表示したりします。 ルールは、さまざまなコントロールに追加できます。 このトピックでは、**Slider** コントロールの値が 70 を超えている場合に、**Label** コントロールのテキストの色を変更するルールを追加します。

> [!IMPORTANT]
> 2019 年 10 月 14 日をもって、キャンバス アプリのルール機能は廃止されました。 詳細: [ブログ: キャンバス ルール機能の廃止](https://powerapps.microsoft.com/blog/canvas-rules-feature-deprecation/)。

## <a name="add-a-rule"></a>ルールを追加する
1. コントロールを選択します (またはコントロールを追加し、選択されたままにします)。

    このトピックでは、[ラベルとスライダーを追加](add-configure-controls.md)して、ラベルの **Text** プロパティを **Slider1.Value** に設定してから、スライダーを選択します。

1. 右側のパネルで、**ルール**をクリックまたはタップしてから、**新しいルール**をクリックまたはタップします。

    ![新規ルールの作成](./media/working-with-rules/new-rule.png)

    1 つまたは複数のルールが既に定義されているコントロールを選択すると、それをクリックまたはタップしていずれも編集することができます。  

## <a name="add-a-condition"></a>条件を追加する
条件とは、値が 70 を超えているかどうかなどを、true または false で評価する式です。 テンプレートに基づいて、または最初から式を記述して、UI (IntelliSense) のガイダンスに基づいて式をカスタマイズできます。

1. **条件の追加**をクリックまたはタップしてから、テンプレートまたは**ユーザー定義条件**をクリックします。

    このトピックでは、**以上**をクリックまたはタップします。

    ![条件の追加](./media/working-with-rules/rule-conditions.png)

1. ルールを適用する条件を定義する式を更新します。

    このトピックでは、0 を 70 に変更してこの式を取得します。 <br>**Slider1.Value > 70**

## <a name="add-an-action"></a>アクションを追加する
アクションは、ルールが適用されるときの動作を定義します。 Power Apps では、コントロールに加えた変更に基づいて、自動的にアクションを作成できます。

1. **アクションの定義**をクリックまたはタップします。

    ![アクションの定義](./media/working-with-rules/rule-define-actions.png)

1. 確認ダイアログ ボックスで**始めましょう**をクリックまたはタップして、Power Apps で次の変更を 1 つまたは複数のアクションとしてキャプチャできるようにします。

1. 条件が true のときに期待どおりに動作するよう、1 つまたは複数のコントロールを構成します。

    このトピックでは、ラベルの色を変更します。

    ![プロパティのキャプチャ](./media/working-with-rules/rule-capture-properties.png)

1. (オプション) **アクションの表示**をクリックまたはタップして、変更を確認します。

    ![アクションの確認](./media/working-with-rules/rule-review-actions.png)

1. アクションの追加が完了したら、**完了**をクリックまたはタップします。

1. ルールの条件とアクションを確認します。

    ![ルールの確認](./media/working-with-rules/rule-review.png)

## <a name="rename-the-rule"></a>ルール名を変更する

1. **Rule1** にマウス ポインターを移動し、編集ボタンをクリックまたはタップします。

    ![ルール名にマウス ポインターを移動](./media/working-with-rules/hover-over-rules_name.png)

1. ルールの新しい名前を入力します。

    ![ルール名の変更](./media/working-with-rules/rename-rule.png)

1. **完了**をクリックまたはタップしてエディターを閉じます。

## <a name="test-the-rule"></a>ルールをテストする
1. F5 キーを押して (または右上隅の再生ボタンをクリックして) アプリをプレビューします。

    ![プレビューを開く](./media/working-with-rules/open-preview.png)

1. true に指定した条件を作成してから、アクションが期待通りに動作することを確認します。

    このトピックでは、スライダーを 70 よりも大きい値に設定して、ラベルのテキストの色が変わることを確認します。

## <a name="see-all-rules"></a>すべてのルールを表示する
既定では、**ルール** タブでは、選択したコントロールと、ルールの条件またはアクションで使用されるすべての子コントロールのルールのみが表示されます。 アプリですべてのルールを表示するには、**このコントロールのルールのみを表示する**チェック ボックスをオフにします。

![フィルターの解除](./media/working-with-rules/rules-filter.png)

## <a name="known-limitations"></a>既知の制限
現時点で:

* 条件の一部として、フォームまたはギャラリーの **ThisItem** プロパティを指定することはできません。
