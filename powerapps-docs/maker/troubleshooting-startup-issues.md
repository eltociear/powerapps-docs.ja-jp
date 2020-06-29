---
title: Power Apps の起動時の問題のトラブルシューティング | Microsoft Docs
description: このトラブルシューティング ガイドは、Power Apps の起動を妨げる一般的な構成の問題を修正するのに役立ちます。
author: matthewbolanos
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 10/28/2019
ms.author: mabolan
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9da1202dc157d7f763dd4bfd2e4c2040a053b704
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3307235"
---
# <a name="troubleshooting-startup-issues-for-power-apps"></a>Power Apps の起動時の問題のトラブルシューティング

このトラブルシューティング トピックは、Power Apps の起動を妨げる次の 2 つの一般的な構成の問題を修正するのに役立ちます。

- 表示される場合 “お待ちください… サインインできませんでした” というエラー メッセージおよび次の画像のような識別子:

    ![お待ちください… サインインできませんでした。以下の情報が役立つ場合があります](./media/troubleshooting-startup-issues/error.png "お待ちください… サインインできませんでした。以下の情報が役立つ場合があります")

- SharePoint リストからアプリを作成しようすると、次の "異常終了" エラー メッセージが表示される
    ```
    WebAuthoring abnormal termination.

    Client date/time: <Client Time>Thh:mm:ss.sssZ
    Version: 2.0.602
    Session ID: xxxx-xxxxx-xxxxxxx--xxxxxxxx
    description: {"error":{"detail":{"exception":{}},"colno":0,"filename":"https://paaeuscdn.azureedge.net/v2.0.602.0/studio/openSource/modified/winjs/js/base.js?v=39de0f2edf1...",
    "lineno":0,"message":"Script error","initErrorEvent":"[function]","bubbles":false,"cancelBubble":false,"cancelable":false,"currentTarget":"[window]","defaultPrevented":true,
    "eventPhase":2,"isTrusted":true,"srcElement":"[window]","target":"[window]","timeStamp":1490711965955,"type":"error","initEvent":"[function]","preventDefault":"[function]",
    "stopImmediatePropagation":"[function]","stopPropagation":"[function]","AT_TARGET":2,"BUBBLING_PHASE":3,"CAPTURING_PHASE":1},"errorLine":0,"errorCharacter":0,
    "errorUrl":"https://paaeuscdn.azureedge.net/v2.0.602.0/studio/openSource/modified/winjs/js/base.js?v=39de0f2edf1... error","setPromise":"[function]","exception":{}}
    stack: null
    errorNumber: 0
    errorMessage: Script error
    ```

このセクションで説明されている問題のいずれかが発生した場合は、後の一般的なエラー マトリックスを確認し、後のリストされている解決策の 1 つを試して問題を解決してください。

## <a name="common-error-matrix"></a>一般的なエラー マトリックス

| エラー識別子                                                              | Microsoft Internet Explorer 11          | Microsoft Edge                          | Google Chrome                        |
|-------------------------------------------------------------------------------|-------------------------------|-------------------------------|-------------------------------|
| UserInterventionNeeded_CookiesBlocked UserInterventionNeeded_StorageBlocked   | ローカル データのストレージを有効にする  | ローカル データのストレージを有効にする  | ローカル データのストレージを有効にする  |
| UserInterventionNeeded_NavigateToAadTimeout                                   | 考えられるネットワークの問題      | セキュリティ ゾーンを構成する         | 考えられるネットワークの問題      |
| UserInterventionNeeded_NavigateToAadDenied UserInterventionNeeded_StorageLost | セキュリティ ゾーンを構成する         | セキュリティ ゾーンを構成する         | 適用なし                |
| AadError                                                                      | Azure Active Directory エラー | Azure Active Directory エラー | Azure Active Directory エラー |

## <a name="resolution-1-enable-storage-of-local-data-in-your-browser"></a>解決方法 1: ブラウザーでローカル データのストレージを有効にする
Power Apps は、ユーザー ID および基本設定を含む一部のデータをブラウザーにローカルに格納します。 Power Apps では、ブラウザーがこれを許可しないように構成されている場合は機能しません。

### <a name="instructions-for-internet-explorer-11"></a>Internet Explorer 11 の説明

- **オプション 1: すべてのサイトのローカル データを有効にする**

    1. Internet Explorer および Edge windows すべてを閉じます。
    2. **OK** を選択して、**インターネット オプション** ダイアログ ボックスを閉じます。
    3. **OK** を選択します。
    4. **powerapps.com** のエントリを削除します。
    5. **設定**セクションで、**サイト**を選択します。
    6. **OK** を選択します。
    7. サード パーティの Cookie について、**同意**を選択します。
    8. ファースト パーティの Cookie について、**同意**を選択します。
    9. **設定**セクションで、**詳細**を選択します。
    10. **プライバシー** タブを選択します。
    11. **インターネット オプション**を選択します。
    12. ブラウザーのツールバーで、歯車のアイコンを選択します。
    13. Internet Explorer を開きます。

- **オプション 2: 例外を作成し、Power Apps および関連サービスのローカル データを有効にする**
    1. Internet Explorer を開きます。
    2. ブラウザーのツールバーで、歯車のアイコンを選択します。
    3. **インターネット オプション**を選択します。
    4. **プライバシー** タブを選択します。
    5. **設定**セクションで、**サイト**を選択します。
    6. “同意” **powerapps.com** にエントリを追加します。
    7. **OK** を選択します。
    8. インターネット オプション ダイアログ ボックスを閉じるには **OK** を選択します。
    9. Internet Explorer および Edge windows すべてを閉じます。

### <a name="instructions-for-edge"></a>Edge の説明
1. Edge を開きます。
2. Edge ツールバーで、**その他** > **設定**を選択します。
3. パネルの下部近くで、**詳細設定を表示**を選択します。
4. パネルの下部近くで、**Cookies** ドロップダウン オプション リストを検索します。
5. **Cookie をブロックしない**を選択します。
6. Internet Explorer および Edge windows すべてを閉じます。

### <a name="instructions-for-chrome"></a>Chrome の説明
    
- **オプション 1: すべてのサイトのローカル データを有効にする**
    1. ブラウザーのツールバーで、**その他**を選択します。
    2. **設定**を選択します。
    3. ページの下部近くで、**詳細設定を表示**を選択します。
    4. "プライバシー" セクションで、**コンテンツ設定**を選択します。
    5. **ローカル データの設定を許可する (推奨)** を選択します。
    6. **サード パーティの Cookie およびサイト データをブロックする**が選択されていないことを確認します。
    7. 例外の管理を選択し、**https://create.powerapps.com**、**https://\*.create.powerapps.com**、**https://make.\*.powerapps.com**、**https://make.powerapps.com**、および**https://login.microsoftonline.com** に例外がないことを確認します。 そのような例外がある場合は、対応する行の x 記号をクリックして削除します。
    8. **完了**を選択します。
    
- **オプション 2: 例外を作成し、Power Apps および関連サービスのローカル データを許可する**
      
    1. ブラウザーのツールバーで、**その他**を選択します。
    2. **設定**を選択します。
    3. ページの下部近くで、**詳細設定を表示**を選択します。
    4. プライバシー セクションで、**コンテンツ設定**を選択します。
    5. **例外の管理**を選択し、**https://create.powerapps.com**、**https://\*.create.powerapps.com**、**https://make.\*.powerapps.com**、**https://make.powerapps.com**、および**https://login.microsoftonline.com** のデータ ストレージを “許可する” 例外を作成します。
    6. **完了**を選択します。


## <a name="resolution-2-configure-trust-zones-for-internet-explorer-and-edge"></a>解決方法 2: Internet Explorer および Edge のセキュリティ ゾーンを構成する

Internet Explorer および Edge は *セキュリティ ゾーン*を使用します。 Power Apps が依存するサービスが、ブラウザー設定の異なるセキュリティ ゾーンにある場合、問題が起こる可能性があります。 これらの設定は Internet Explorer および Edge の両方に適用されるとしても、アクセスする最も簡単な方法は Internet Explorer からです。 (これらの設定の一部を変更するには、IT 管理者の支援が必要になる場合があります。)

- **オプション 1: 必要な Power Apps ドメインを信頼済みサイトゾーンへ追加する**
    1. ブラウザーのツールバーで、歯車のアイコンを選択します。
    2. **インターネット オプション**を選択します。
    3. **セキュリティ** タブを選択します。
    4. **信頼済みサイト**を選択します。
    5. **サイト**を選択します。
    6. アドレスを入力しそれぞれに**追加**を選択して、次のサイトを追加します。
        - **https://login.microsoftonline.com**
        - **https://create.powerapps.com**
        - **https://*.create.powerapps.com** (アスタリスクはアドレスの一部です、置き換えないでください)
        - **https://make.powerapps.com**
        - **https://make.*.powerapps.com** (アスタリスクはアドレスの一部です、置き換えないでください)
        - **https://*.powerapps.com** (アスタリスクはアドレスの一部です、置き換えないでください)
    7. **閉じる**を選択します。
    8. **OK** を選択します。
    9. Internet Explorer および Edge windows すべてを閉じます。
 

- **オプション 2: すべての Power Apps ドメインを信頼済みサイトゾーンから削除する**
    1. ブラウザーのツールバーで、歯車のアイコンを選択します。
    2. **インターネット オプション**を選択します。
    3. **セキュリティ** タブを選択します。
    4. **信頼済みサイト**を選択します。
    5. **サイト**を選択します。
    6. 次のサイトの既存のエントリをすべて削除します。
        - **https://login.microsoftonline.com**
        - **https://create.powerapps.com**
        - **https://*.create.powerapps.com**
        - **https://make.powerapps.com**
        - **https://make.*.powerapps.com** 
        - **powerapps.com** または **create.powerapps.com** で終わるその他のアドレス。
  7. **閉じる**を選択します。

## <a name="resolution-3-azure-active-directory-errors"></a>解決方法 3: Azure Active Directory エラー

Azure Active Directory (Azure AD) は、Power Apps エコシステムがユーザーの認証および承認に依存する技術です。

表示されるエラーページには、問題の診断と修正に役立つことのできる追加情報が含まれている場合があります。

Azure AD エラーを解決するには、IT 部署からの支援が必要になることがあります。
