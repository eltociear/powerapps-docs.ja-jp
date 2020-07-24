---
title: AppSource チェッカーの概要 | Microsoft Docs
description: AppSource チェッカーの使用方法に関する説明
services: ''
suite: powerapps
documentationcenter: na
author: nkrb
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.reviewer: pehecke
ms.workload: na
ms.date: 04/07/2020
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 9fac6873de58e3090e62e24e7f43f79caad30a63
ms.sourcegitcommit: a94b56525667015d4439a082873c2262a61b25a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/16/2020
ms.locfileid: "3455956"
---
# <a name="appsource-checker"></a>AppSource チェッカー

[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

AppSource チェッカーを使用して、[AppSource](https://appsource.microsoft.com/) に送信する前にアプリが認定基準に一致しているか検証することができます。 チェッカーによりソリューション ファイルに修正が必要なエラーがあるかどうか知ることができ、AppSource 認定基準に一致しているか検証できます。 

ISV Studio で、完全な [パッケージ](/power-platform/alm/package-deployer-tool) またはソリューションをアップロードできます。 修復される必要がある問題があるか通知されます。

**AppSource チェッカーの実行**

1. ISV Studio で、左端のウィンドウの **AppSource チェッカー**を選択し、**アプリを検証する**を選択します。

    > [!div class="mx-imgBorder"]
    > ![AppSource チェッカー](media/appsource-checker.png "AppSource チェッカー")

2. **参照**を選択し、ローカル コンピュータからソリューション ファイルをアップロードしてから、**チェックを実行**を選択します。
   
   > [!div class="mx-imgBorder"]
   > ![コマンド チェックの実行](media/appsource-browse-solution-files.png "コマンド チェックの実行")
 
   > [!NOTE]
   > 以前に検証用のソリューションをアップロードしたことがある場合、上のスクリーンショットの代わりに提出の履歴が表示されます。

3. 検証チェックが完了した後、見つかった問題の数 (ある場合) と共に結果の概要が表示されます。 ダブルクリックしてソリューション ファイルを選択し、問題の詳細を表示します。

   > [!div class="mx-imgBorder"]
   > ![AppSource チェッカーの結果の概要](media/appsource-results-page.png "AppSource チェッカーの結果の概要")

4. 送信エラーがない場合、次のメッセージが表示されます。
 
   > [!div class="mx-imgBorder"]
   > ![AppSource チェッカー成功メッセージ](media/appsource-no-error-page.png "AppSource チェッカー成功メッセージ")
   
アプリの検証レポートをダウンロードして、AppSource 送信に含めることができるようになりました。 

### <a name="see-also"></a>関連項目

[ホーム ページ](isv-app-management-homepage.md)<br/>
[アプリ ページ](isv-app-management-apppage.md)<br/>
[テナント ページ](isv-app-management-tenantpage.md)<br/>
[コネクタ認定](isv-app-management-certification.md)

