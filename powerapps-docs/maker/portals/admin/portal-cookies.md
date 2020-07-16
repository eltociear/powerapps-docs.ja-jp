---
title: Power Apps ポータルの Cookie | MicrosoftDocs
description: Power Apps ポータルが使用する Cookie を把握します。
author: neerajnandwana-msft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 03/10/2020
ms.author: nenandw
ms.reviewer: tapanm
ms.openlocfilehash: 48868947721f9c5e1c732336df28a7679eb7dda1
ms.sourcegitcommit: 2fd873a1ea17f419f6194714efffa47a9bd00c2e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "3507272"
---
# <a name="cookies-in-power-apps-portals"></a>Power Apps ポータルの Cookie

Cookie は、ブラウザーによって Web サイトから訪問者のデバイスに送信される小さなファイルです。 1 つの Web セッションで複数の Cookie を使用できます。

Power Apps ポータルも、さまざまな目的で情報を保存するために Cookie を使用します。 次のセクションでは、Power Apps ポータルが使用する Cookie を示して説明します:

## <a name="names-and-descriptions-of-cookies-used-by-portals"></a>ポータルで使用される Cookie の名前と説明

#### <a name="arraffinity"></a>ARRAffinity

Azure Web サイトによって自動的に追加され、要求が異なるサイト間で負荷分散されるようにします。 ユーザー情報を保存しません。

####  <a name="aspnet-session-id"></a>ASP.Net Session Id

ログインしたユーザーのセッションを維持して、サインインが繰り返されないようにするために使用されます。 Cookie は永続的ではなく、セッションが閉じた後に削除されます。

#### <a name="dynamics-365-portal-analytics"></a>Dynamics 365 ポータル分析

サービスの使用状況を匿名で分析し、統計目的で集計する重要なサービス Cookie。

#### <a name="contextlanguagecode"></a>ContextLanguageCode

セッション内および Web ページ全体でポータルにアクセスするユーザーの既定言語を格納します。 セッションが終了すると、Cookie は削除されます。

#### <a name="aspnetapplicationcookie"></a>.AspNet.ApplicationCookie

ユーザー セッションを識別するために使用されます。 ユーザー セッションは、ユーザーが初めてポータルを閲覧したときに開始されます。 そして、セッションが閉じられると終了します。 [認証サイトの設定](https://docs.microsoft.com/powerapps/maker/portals/configure/set-authentication-identity) を使用して、セッションの有効期限を変更できます。

#### <a name="__requestverificationtoken"></a>__RequestVerificationToken 

[偽造防止](https://docs.microsoft.com/dotnet/api/system.web.helpers.antiforgeryconfig.cookiename) システムで使用されます。

#### <a name="adxpreviewunpublishedentities"></a>adxPreviewUnpublishedEntities

ポータル管理者用のクラシック CMS システムで使用されるプレビューの **オン/オフ** モードを保持します。

#### <a name="adx-notification"></a>adx-notification

エンティティ フォーム アクションで、リダイレクト時に表示される警告メッセージを格納するために使用されます。

#### <a name="timezonecode"></a>timezoneCode

現在のタイムゾーンの *CRM timezonedefinition* エンティティの *timezonecode* フィールド値を保持します。

#### <a name="timezoneoffset"></a>timezoneoffset

UTC とローカル ブラウザー時間の [タイムゾーンの差](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Date/getTimezoneOffset) を保持します。

#### <a name="isdstsupport"></a>isDSTSupport

指定された日時が夏時間の範囲内にあるかどうかを示します。

#### <a name="isdstobserved"></a>isDSTObserved

現在の時刻が夏時間かどうかを示す値を格納します。

### <a name="see-also"></a>関連項目

[Cookie 認証サイト設定](https://docs.microsoft.com/powerapps/maker/portals/configure/set-authentication-identity#cookie-authentication-site-settings)

