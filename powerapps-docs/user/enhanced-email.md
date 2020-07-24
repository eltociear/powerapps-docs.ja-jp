---
title: 'プレビュー: モデル駆動型アプリで強化された電子メール エクスペリエンスを使用して電子メールを送信する | MicrosoftDocs'
description: 強化された電子メール エクスペリエンスを使用して、作業中の内容を離れることなく電子メールを作成します。
ms.date: 04/09/2020
ms.service:
- dynamics-365-sales
ms.topic: article
author: shubhadaj
ms.author: shujoshi
manager: annbe
ms.openlocfilehash: bc4b7023e56ae75b34f797089a812ab4ea1f8d84
ms.sourcegitcommit: 2484ebce6563cfd1c849e1e2f66dd2d29fdb7b64
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2020
ms.locfileid: "3303624"
---
# <a name="send-email-using-the-enhanced-email-experience"></a>強化された電子メール エクスペリエンスを使用した電子メールの送信

モデル駆動型アプリの強化された電子メール エクスペリエンスにより、作業中のレコードを離れることなく電子メールを作成できます。 強化された電子メール エクスペリエンスにより、次のことが可能になりました。

- 電子メールの内容を失わずに、別のページに移動します。
- 作業中だったレコードに戻す電子メール ウィンドウを最小限にします。
- 電子メール エディターのポップアップ ウィンドウを展開し、さらに電子メール オプションを表示します。
- 同時に、3 つの電子メールの作成ポップアップ ウィンドウを開きます。
- あらかじめ定義されたテンプレートを検索し、作成中の電子メールに適用します。
- 電子メールに添付ファイルを追加します。


> [!IMPORTANT]
> - システム管理者は、使用する前に拡張電子メール エクスペリエンスを有効にする必要があります。
> - [!INCLUDE[cc_preview_features_definition](../includes/cc-preview-features-definition.md)]  
> - [!INCLUDE[cc_preview_features_expect_changes](../includes/cc-preview-features-expect-changes.md)]
> - [!INCLUDE[cc-preview-features-no-ms-support](../includes/cc-preview-features-no-ms-support.md)]

強化された電子メール エクスペリエンスを使用した電子メールの作成:

1. 取引先企業、取引先担当者レコードの **タイムライン** セクションで、**+** を選び、**活動** 配下の **電子メール**を選択します。

   新しいホップアップ ウィンドウが開きます。 

   > [!div class="mx-imgBorder"]
   > ![拡張された電子メールのポップアップ](media/enhanced-email-pop-up.png "拡張された電子メールのポップアップ")

   **から**および**に**フィールドは、元のレコードのユーザー、取引先企業および取引先担当者に基づいて、自動的に設定されます。

2. ゼロから電子メールを書き込む、または**テンプレートを挿入**を選択して、テンプレートを検索して適用します。 電子メール テンプレートの挿入に関する詳細については、[電子メールのテンプレートを挿入する](insert-email-template.md)を参照してください。

3. 添付ファイルを追加する場合は、**ファイルを添付**を選択します。

4. **署名の挿入**を選び、署名を検索して追加します。

5. 終了したら、**送信**を選択します。 

> [!IMPORTANT]
> - 強化された電子メール エクスペリエンスは、モデル駆動型アプリの **[タイムライン]** セクションから作成された電子メール アクティビティに対してのみ使用できます。 
> - 強化された電子メールのポップアップ ウィンドウは、画面サイズの高さと幅が 400 x 650 ピクセル以上の場合にのみ表示されます。 小さい場合は、拡張電子メール エクスペリエンスの代わりに、標準フォームに表示されます。 

### <a name="see-also"></a>関連項目

[拡張電子メールの設定](https://docs.microsoft.com/power-platform/admin/system-settings-dialog-box-email-tab)<br>
[電子メール テンプレートを挿入する](insert-email-template.md)
