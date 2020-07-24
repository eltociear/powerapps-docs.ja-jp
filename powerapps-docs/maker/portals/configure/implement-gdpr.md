---
title: Power Apps ポータルで一般データ保護規則を実装する | MicrosoftDocs
description: Power Apps ポータルで一般的なデータ保護規則を実装する方法を学習します。
author: sandhangitmsft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/18/2019
ms.author: sandhan
ms.reviewer: tapanm
ms.openlocfilehash: b1c88e5408079b47122085892b0c88b4fdf5163c
ms.sourcegitcommit: c12260f372ad2cc48d3146be570d2088c9ef1d86
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2020
ms.locfileid: "3494292"
---
# <a name="implementing-general-data-protection-regulations-in-your-power-apps-portals"></a>Power Apps ポータルで一般データ保護規則を実装する

一般的なデータ保護規則 (GDPR) は欧州連合 (EU) 内の法律行為で、EU 内のすべてのユーザーのデータを保護します。 GDPR を使用して、Common Data Service 内の個人データの使用をコントロールすることができます。

管理者は、GDPR 基準を満たすようにポータルを設定することができます。 たとえば、未成年者はポータルを使用するために親の同意が必要です。 また、ポータルを使用するユーザーのために利用条件を作成することができます。 ユーザーはポータルを使用するために利用条件に同意する必要があります。

GDPR を使用すると、個人データの使用に関するポータル ユーザーからの同意を取得し、未成年ユーザーを識別し、未成年者の親の同意を取得することができます。

## <a name="audit-logging"></a>監査ログ

ポータルの取引先担当者レコード内の**最後のサインイン成功**フィールドには、ポータル ユーザーが最後にログインした時間が表示されます。 この日付は取引先担当者レコードの監査から取得され、標準監査ストリームでその情報を利用可能にします。 これにより管理者は非アクティブなコミュニティ メンバーを表示してそのレコードを削除することができます。

> [!NOTE]
> ログイン追跡機能は廃止されました。 このような情報を取得するには、Azure Application Insights のような分析技術をご利用することを推奨します。 廃止された機能の一覧を表示するには、[ここ](https://blogs.msdn.microsoft.com/crm/2018/03/20/portal-capabilities-for-dynamics-365-deprecated-features/)をクリックします。

## <a name="identifying-minor-portal-users-and-obtaining-parental-consent"></a>未成年者ポータル ユーザーを識別して親の同意を取得する

未成年者を特定するための規則は国/地域によってそれぞれ異なります。 未成年者は親の同意があるポータルにのみアクセスすることができるため、ポータルの取引先担当者レコード内の以下のフィールドを使用して、未成年者を特定するようにポータルを構成することができます。
- **未成年であるかどうか**: 取引先担当者が管轄地域では未成年と見なされていることを示します。 既定では、**いいえ**が選択されます。
- **親の承諾がある未成年であるかどうか**: 取引先担当者が管轄地域では未成年と見なされ、保護者の同意があることを示します。 既定では、**いいえ**が選択されます。

    ![未成年ポータル ユーザーを識別して親の同意を取得する](../media/identify-minor-in-portal.png "未成年ポータル ユーザーを識別して親の同意を取得する")

以下のサイト設定は、未成年者および親の同意がない未成年者ごとにポータルの使用をコントロールします。

| Name  | 内容   |
|-----------------------|------------------------------------------|
| Authentication/Registration/DenyMinors  | 未成年者によるポータルの使用を拒否します。 既定では false に設定されています。                          |
| Authentication/Registration/DenyMinorsWithoutParentalConsent | 親の同意がない未成年者によるポータルの使用を拒否します。 既定では false に設定されています。 |
|||

ポータル ユーザーが未成年者であると判断され、そのポータルが未成年者をブロックするように構成されている場合、適切なメッセージが表示されて内容は表示されません。

![年齢要件のメッセージ](../media/gdpr-age-req.png "年齢要件のメッセージ")

ポータル ユーザーが親の同意がない未成年者であると判断され、そのポータルが親の同意がない未成年者をブロックするように構成されている場合、適切なメッセージが表示されて内容は表示されません。

![保護者の承諾のメッセージ](../media/gdpr-parental-consent.png "保護者の承諾のメッセージ")

次のコンテンツ スニペットは、未成年者および親の同意のない未成年者がポータルを使用するときに表示されるメッセージをコントロールします。 要件に応じてメッセージを変更することができます。

| Name                                                        | 種類​​ | Value                                                                    |
|-------------------------------------------------------------|------|--------------------------------------------------------------------------|
| Account/Signin/MinorNotAllowedHeading                       | テキスト | 年齢の要件                                                         |
| Account/Signin/MinorNotAllowedCopy                          | HTML | このポータルの使用は未成年者の使用に適しておらず許可されません。 |
| Account/Signin/MinorWithoutParentalConsentNotAllowedHeading | テキスト | 保護者の承諾                                                         |
| Account/Signin/MinorWithoutParentalConsentNotAllowedCopy    | HTML | 未成年によるこのポータルの使用には、保護者の承諾が必要です。              |
|||

だれかが外部プロバイダーを使用して登録し、未成年者および親の同意がない未成年者をブロックするようにポータルが構成されているとき、取引先担当者レコードは作成されずユーザーは認証されません。

## <a name="agreeing-to-terms-and-conditions"></a>利用条件の同意

GDPR に応じて、ポータル ユーザーはマーケティング、プロファイリング、または個人情報へのアクセスを許可するための利用条件に同意する必要があります。 管理者として、サイトに認証される前にポータル ユーザーの同意を取得する、独自の利用条件を公開することができます。

![ポータルの利用条件](../media/gdpr-terms-agreement.png "ポータルの利用条件")

以下のコンテンツ スニペットは画面上での利用条件の表示をコントロールします。 要件に応じてテキストを変更することができます。

| Name                                           | 種類​​ | Value                                 |
|------------------------------------------------|------|---------------------------------------|
| Account/Signin/TermsAndConditionsHeading       | テキスト | 使用条件                  |
| Account/Signin/TermsAndConditionsCopy          | HTML |                                       |
| Account/Signin/TermsAndConditionsAgreementText | テキスト | 利用条件に同意します |
| Account/Signin/TermsAndConditionsButtonText    | テキスト | 続行します                              |
|||

`Account/Signin/TermsAndConditionsCopy` コンテンツ スニペットは既定で空です。 ポータル管理者はこのコンテンツ スニペット内に利用条件を入力する必要があります。

以下のサイト設定は、条件公開日および条件をポータルに表示する必要があるかどうかをコントロールします。

| Name  | 内容 |
|------------|---------------|
| Authentication/Registration/TermsPublicationDate  | 現在公開済みの利用条件の有効日を示す GMT 形式の日付/時間の値です。 条件合意が有効にされる場合、条件を受け入れなかったポータル ユーザーは、この日付の後に次回のサインイン時に受け入れるよう尋ねられます。 日付が指定されず、条件合意が有効である場合は、ポータル ユーザーがサインインするときはいつでも条件が表示されます。 <br> **メモ**: ポータル ユーザーがサインインごとに利用条件に同意するようにする場合は、このサイト設定の値は入力しません。|
| Authentication/Registration/TermsAgreementEnabled | true または false の値。 true にセットする場合、ポータルにはサイトの利用条件が表示されます。 ユーザーは認証されてサイトを使用することができると判断される前に、利用条件に同意する必要があります。 既定では false に設定されています。        |
|||

ポータル ユーザーが利用条件に同意した日付を格納する、以下のフィールドがポータルの取引先担当者レコードに追加されます。
- **ポータル使用条件合意の日付**: ユーザーがポータルの使用条件に同意した日時を示します。

    ![ポータルの使用条件合意の日付](../media/portal-terms-agreement.png "ポータル使用条件合意の日付")

### <a name="see-also"></a>関連項目

[アイデンティティ プロバイダを Azure AD B2Cへ移行する](migrate-identity-providers.md)
