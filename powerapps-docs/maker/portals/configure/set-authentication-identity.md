---
title: ポータル用の認証 ID の設定 | MicrosoftDocs
description: ポータル用の認証 ID を設定する手順。
author: sandhangitmsft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 04/30/2020
ms.author: sandhan
ms.reviewer: tapanm
ms.openlocfilehash: db974229255eb37fe90fc4961d132013c3cced0a
ms.sourcegitcommit: c12260f372ad2cc48d3146be570d2088c9ef1d86
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2020
ms.locfileid: "3491767"
---
# <a name="set-authentication-identity-for-a-portal"></a>ポータル用の認証 ID の設定

ポータルは、[ASP.NET アイデンティティ](https://www.asp.net/identity)　API上に構築された認証機能を提供します。 それに対して、ASP.NET ID は、[OWIN](https://www.asp.net/aspnet/overview/owin-and-katana) フレームワーク上に構築され、これは認証システムの重要なコンポーネントでもあります。 提供されるサービスには、次のものが含まれます。

- ローカル ユーザーのサインイン (ユーザー名とパスワード)
- 外部 (社会プロバイダー) ユーザーはサード パーティ ID プロバイダー経由でサインイン
- 電子メールでの二段階認証
- 電子メール アドレスの確認
- パスワード回復
- 事前生成された連絡先レコードを登録するために招待コードを登録する

> [!NOTE]
> 取引先担当者エンティティのポータル連絡先フォーム上の **確認済み携帯電話** フィールドは、現在は何の役にも立ちません。 このフィールドは、Adxstudio Portals からアプグレードされた時のみに使用される必要があります。

## <a name="requirements"></a>要件

ポータルに必要なもの：

- 基本ポータル
- [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] ID
- [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] ID ワークフロー ソリューション パッケージ

## <a name="authentication-overview"></a>認証の概要

返却されたポータル ビジターでは、ローカル ユーザー資格情報または外部 ID プロバイダー アカウントのどちらかを使用して認証できます。 新規ビジターは、ユーザー名およびパスワードを提示するか、外部プロバイダー経由で登録することにより、新しいユーザー アカウントを登録できます。 ポータル管理者から招待コードを受け取ったビジターは、新しいユーザー アカウントにサインアップするときにコードを交換することができます。

**関連サイトの設定:**

- `Authentication/Registration/Enabled`
- `Authentication/Registration/LocalLoginEnabled`
- `Authentication/Registration/ExternalLoginEnabled`
- `Authentication/Registration/OpenRegistrationEnabled`
- `Authentication/Registration/InvitationEnabled`
- `Authentication/Registration/RememberMeEnabled`
- `Authentication/Registration/ResetPasswordEnabled`

### <a name="sign-in-by-using-a-local-identity-or-external-identity"></a>ローカル ID または外部 ID でサインイン

![ローカル アカウントでサインイン](../media/sign-in-local-account.png "ローカル アカウントでサインイン")  

### <a name="sign-up-by-using-a-local-identity-or-external-identity"></a>ローカル ID または外部 ID で登録

![新しいローカル アカウントを登録する](../media/register-new-local-account.png "新しいローカル アカウントを登録する")  

### <a name="redeem-an-invitation-code-manually"></a>招待コードを手動で入力します

![招待コードを使用して登録](../media/sign-up-invitation-code.png "招待コードを使用して登録")  

## <a name="forgot-password-or-password-reset"></a>パスワードを忘れた/パスワードのリセット 

パスワードを再設定する必要のある再訪問者 (自分のユーザー プロファイルで電子メール アドレスとパスワードを設定したことのあるユーザー) は、パスワードを再設定するためのトークンを自分の電子メール アカウントに送信するようにリクエストできます。 再設定用のトークンの所有者は、新しいパスワードを自分で決めて設定することができます。 トークンを破棄して、ユーザーの元のパスワードを変更せずに残すこともできます。

**関連サイトの設定:**

- `Authentication/Registration/ResetPasswordEnabled`
- `Authentication/Registration/ResetPasswordRequiresConfirmedEmail`

**関連するプロセス:** 取引先担当者をリセットするパスワードの送信

1.  必要に応じてワークフローの電子メールをカスタマイズします。
2.  処理を実行するには、電子メールを送信します。
3.  訪問者に電子メールを確認するように促します。
4.  訪問者には、パスワードをリセットするための電子メールが、説明と共に届きます。
5.  訪問者が再設定フォームに戻ります。
6.  パスワードのリセットが完了しました。

## <a name="redeem-an-invitation"></a>招待状の引き換え

招待コードを入力すると、登録しようとしている訪問者を、その訪問者用に事前に準備した既存の取引先担当者レコードに関連付けることができます。 通常、招待コードは電子メールで送信されますが、一般的なコードの送信フォームを使用して、他のチャネル経由でコードを送信できます。 有効な招待コードが送信されたら、通常ユーザー登録 (サインアップ) プロセスでは新しいユーザー アカウントの設定が実施されます。

**関連サイトの設定:**

`Authentication/Registration/InvitationEnabled`

**関連するプロセス**招待状の送信

このワークフローによって送信される電子メールは、ポータル上の招待ページを利用するために URL を使用することでカスタマイズされる必要があります: https://portal.contoso.com/register/?returnurl=%2f&invitation={Invitation Code(Invitation)}

1. 新しい連絡先に対する招待状を作成します。

    ![新しい連絡先に対する招待状を作成します。](../media/create-invitation.png "新しい連絡先に対する招待状を作成します。")  

2. 新しい招待状をカスタマイズし、保存します。

    ![新しい招待状のカスタマイズ](../media/customize-new-invitation.png "新しい招待状のカスタマイズ")  

3. プロセス: 招待状の送信
4. 招待メールをカスタマイズします。
5. 招待メールで償還ページを開きます。
6. ユーザーは招待コードを送信して登録します。

    ![招待コードでサインアップする](../media/sign-up-invitation-code.png "招待コードを使用して登録")  

## <a name="manage-user-accounts-through-profile-pages"></a>プロフィール ページでユーザー アカウントを管理する

認証されたユーザーは、プロファイル ページの**セキュリティ**ナビゲーション バーを介して自分のユーザー アカウントを管理します。 ユーザーのユーザー登録時に選択するアカウントは 1 つのローカル アカウントまたは 1 つの外部アカウントに限定されていません。 外部アカウントを持つユーザーは、ユーザー名とパスワードを適用することによってローカル アカウントを作成するか選択できます。 ローカル アカウントから開始したユーザーは、自分のアカウントに複数の外部の ID を関連付けることができます。 プロフィールのページは、確認用の電子メールを自分の電子メール アカウントに送るようにリクエストをして電子メール アドレスを確認するようにユーザーに注意喚起する場所でもあります。

**関連サイトの設定:**

- `Authentication/Registration/LocalLoginEnabled`
- `Authentication/Registration/ExternalLoginEnabled`
- `Authentication/Registration/TwoFactorEnabled`

## <a name="set-or-change-a-password"></a>パスワードを設定または変更する

既存のローカル アカウントを持つユーザーは、元のパスワードを入力することによって新しいパスワードを適用することができます。 ローカル アカウントを持たないユーザーは、ユーザー名とパスワードを選択して新しいローカル アカウントを設定することができます。 ユーザー名は、設定後に変更することはできません。

**関連サイトの設定:**

`Authentication/Registration/LocalLoginEnabled`

**関連するプロセス:**
- ユーザー名およびパスワードを作成します。
- 既存のパスワードを変更します。

## <a name="confirm-an-email-address"></a>電子メール アドレスの確認

電子メールを変更すると (または最初に作成すると)、電子メールが未確認の状態になります。 ユーザーは、新しい電子メール アドレスに確認メールを要求することができます。その電子メールには、電子メール確認プロセスを完了するためにユーザーへの指示が含まれています。

**関連するプロセス:** 確認をする電子メールを連絡先に送信する

1. 必要に応じてワークフローの電子メールをカスタマイズします。 
2. ユーザーは、未確認状態の新規電子メールを送信します。
3. ユーザーは、確認のために電子メールを確認します。
4. プロセス: 連絡先の確認をする電子メールの送信
5. 確認メールをカスタマイズします。
6. ユーザーは確認リンクをクリックして確認プロセスを完了します。

> [!NOTE]
> 確認電子メールは、取引先担当者の既定電子メール (emailaddress1) にのみ送信されるため、既定電子メールが取引先担当者に対して指定されていることを確認します。 確認電子メールは、取引先担当者レコードの電子メール アドレス 2 (emailaddress2) や連絡用電子メール アドレス (emailaddress3) には送信されません。

## <a name="enable-two-factor-authentication"></a>2 要素認証を有効化する

二段階認証機能は、標準のローカルまたは外部アカウント サインインに加えて確認電子メールの所有権の証拠を要求することによってユーザー アカウント セキュリティを強化します。 二段階認証有効のアカウントにサインインするユーザーには、アカウントに関連付けられている確認電子メールにセキュリティ コードが送られます。 セキュリティ コードは、サインイン処理を完了するために必ず送信する必要があります。 ユーザーは検証が完了したブラウザーを記憶するかどうか選ぶことができるので、セキュリティ コードは同じブラウザーから次にサインインする場合は要求されません。 各ユーザー アカウントでこの機能が個別に有効となり、確認電子メールを要求することができます。

> [!WARNING]
> **Authentication/Registration/MobilePhoneEnabled** サイト設定を従来機能を有効化するように作成および有効化する場合は、エラーが発生します。 このサイトの設定はボックスからは提供されず、ポータルではサポートされていません。

**関連サイトの設定:**

- `Authentication/Registration/TwoFactorEnabled`
- `Authentication/Registration/RememberBrowserEnabled`

**関連するプロセス:** ツーファクタ コードを連絡先に電子メールの送信

1. 二段階認証を有効にします。
2. 電子メールでセキュリティ コードを受信することを選択します。
3. セキュリティのコードを含む電子メールをお待ちください。
4. プロセス: ツーファクタ コードを連絡先に電子メールを送信します。
5. 二段階認証は無効にすることができます。

## <a name="manage-external-accounts"></a>外部アカウントの管理

認証されたユーザーは、複数の外部 ID を、各構成済みの ID プロバイダーから、自分のアカウントに接続 (登録) できます。 ID が接続されると、ユーザーは接続された任意の ID を使用し、サインインすることを選択できます。 既存の ID は、少なくとも 1 つの外部 ID またはローカル ID を残して、接続解除することができます。

**関連するサイト設定:**

- `Authentication/Registration/ExternalLoginEnabled`

**外部 ID プロバイダー サイトの設定**

1.  ユーザー アカウントに接続するプロバイダーを選択します。

    ![外部アカウントの管理](../media/manage-external-accounts.png "外部アカウントの管理")  

2.  接続するプロバイダーを使用してサインインします。

プロバイダーが接続されました。 プロバイダーを接続解除することもできます。

## <a name="enable-aspnet-identity-authentication"></a>ASP.NET ID 認証の有効化

以下は各種の認証方式や挙動を有効および無効にするための設定を説明しています。


|                        サイト設定の名前                        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  内容                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|-----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|          Authentication/Registration/LocalLoginEnabled          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     ユーザー名 (または電子メール) とパスワードによるローカル アカウントのサインインを有効化または無効化します。 既定値: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|          Authentication/Registration/LocalLoginByEmail          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               ユーザー名フィールドのかわりに電子メール アドレス フィールドを使用するローカル アカウントのサインインを有効化または無効化します。 既定: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|        Authentication/Registration/ExternalLoginEnabled         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  外部アカウントのサインインと登録を有効化または無効化します。 既定値: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|          Authentication/Registration/RememberMeEnabled          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          このアカウントを記憶するチェック ボックスをローカルのサインインで選択またはクリアすると、Web ブラウザーを閉じたあとも認証セッションを継続します。 既定値: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|          Authentication/Registration/TwoFactorEnabled           |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        2 要素認証をユーザーが有効化できるオプションを有効または無効にします。 確認電子メール アドレスでユーザーは追加した二段階認証のセキュリティを選択できます。 既定: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|       Authentication/Registration/RememberBrowserEnabled        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                現在のブラウザーの二次因数検証を保持する二次因数検証 (電子メールコード) のブラウザを記憶するチェック ボックスを選択またはクリアします。 ユーザーは、同一のブラウザーを使用する場合に、次のサインインで 2 要素認証を行う必要がなくなります。 既定値: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|        Authentication/Registration/ResetPasswordEnabled         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         パスワード再設定機能を有効または無効にします。 既定値: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Authentication/Registration/ResetPasswordRequiresConfirmedEmail |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               確認済みの電子メール アドレスについてのみ、パスワード再設定を有効または無効にします。 有効の場合、未確認の電子メール アドレスにはパスワード再設定の手順を送信できません。 既定: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|   Authentication/Registration/TriggerLockoutOnFailedPassword    |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          パスワードの認証失敗の記録を有効または無効にします。 無効の場合、ユーザー アカウントがロックされることはありません。既定値: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|             Authentication/Registration/IsDemoMode              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                          開発環境やデモ環境でのみ使用されるデモ モード フラグを有効または無効にします。 運用環境でこの設定を有効にしないでください。 デモ モードでは、Web アプリケーション サーバーに対して Web ブラウザーがローカルで実行している必要があります。 デモ モードを有効にしている場合、パスワード再設定のコードおよび 2 要素認証のコードは、すばやくアクセスするためにユーザーに対して表示されます。 既定: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|    Authentication/Registration/LoginButtonAuthenticationType    | これにより、ポータルが単一の外部 ID プロバイダーのみを要求する場合 (すべての認証を処理するため)、ヘッダーのナビゲーション バーの**サインイン**ボタンからその外部 ID プロバイダーのサインイン ページに直接リンクすることができます (中間的なローカルのサインイン フォームや ID プロバイダーの選択ページにリンクする代わりとして)。 この動作のためには、単一の ID プロバイダーのみが選択されている必要があります。 プロバイダーの [AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx) の値を指定します。<br>Azure Active Directory B2C を使用するような  OpenIdConnect を使用した単一サインオン構成については、ユーザーは認証を提供しなければなりません。<br>プロバイダーに基づく OAuth2 の適用値は: `Facebook, Google, Yahoo, [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)], LinkedIn, Yammer,` または `Twitter`<br>WS-Federation ベースのプロバイダーでは、`Authentication/WsFederation/ADFS/AuthenticationType` および `Authentication/WsFederation/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]/\[provider\]/AuthenticationType` のサイト設定で指定した値を使用します。 例: https://adfs.contoso.com/adfs/services/trust、Facebook-0123456789、Google、Yahoo!、URL:[!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)]LiveID。 |
|                                                                 |                                                                                                                                                                                                                                                                                                  |

## <a name="enable-or-disable-user-registration"></a>ユーザー登録の有効化または無効化

以下ではユーザー登録 (サインアップ) のオプションを有効および無効にする設定について説明します:

| サイト設定の名前                                   | 内容                                                                                                                                                                             |
|-----------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/Registration/Enabled                 | ユーザー登録のすべてのフォームを有効または無効にします。 このセクションのほかの設定を使用できるようにするには、登録を有効化する必要があります。 既定値: true                                   |
| Authentication/Registration/OpenRegistrationEnabled | 新しいローカル ユーザーを作成するためのサインアップ登録フォームを有効または無効にします。 サインアップのフォームでは、ポータルへの未登録の訪問者が、新しいユーザー アカウントを作成することができます。 既定値: true |
| Authentication/Registration/InvitationEnabled       | 招待コードがあるユーザーを登録する招待コード入力フォームを有効化または無効化します。 既定値: true                                                               |
|Authentication/Registration/CaptchaEnabled|ユーザー登録ページで画像文字を有効化または無効化します。 既定: false<br>**注意**: このサイト設定は既定では使用できない場合があります。 画像文字を有効にするには、サイト設定を作成して、その値を true に設定する必要があります。 |
||

> [!NOTE]
> 登録はユーザーの既定電子メール (emailaddress1) を使用して実行されるため、既定電子メールがユーザーに対して指定されていることを確認します。 ユーザーは、取引先担当者レコードの電子メール アドレス 2 (emailaddress2) や連絡用電子メール アドレス (emailaddress3) を使用して登録できません。

## <a name="user-credential-validation"></a>ユーザーの資格情報の検証

以下ではユーザー名およびパスワードの検証パラメーターを調整するための設定について説明します。 検証は、新しいローカル アカウントのサイン アップ時、またはパスワードの変更時に実行されます。

| サイト設定の名前                                                       | 内容                                                                                                                                                                                         |
|-------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/UserManager/PasswordValidator/EnforcePasswordPolicy      | パスワードに、次のカテゴリの 3 つからの文字を含めるかどうかを示します:<br><ul><li>ヨーロッパ言語の大文字 (A ~ Z、区別的発音符号を含む、ギリシャ文字、およびキリル文字)</li><li>ヨーロッパ言語の小文字 (a ~ z、シャープ s、区別的発音符号を含む、ギリシャ文字、およびキリル文字)</li><li>基本 10 桁 (0 ~ 9)</li><li>非英数字 (特殊文字) (!、$、\#、% など)</li></ul>既定値: true。 詳細については、[パスワード ポリシー](https://technet.microsoft.com/library/hh994562(v=ws.10).aspx) を参照してください。                                                                                                           |  
| Authentication/UserManager/UserValidator/AllowOnlyAlphanumericUserNames | ユーザー名に英数字のみ許可するかどうか。 既定: false。 詳細情報: [UserValidator<TUser, TKey>.AllowOnlyAlphanumericUserNames](https://msdn.microsoft.com/library/dn613211.aspx)。                                                          |  
| Authentication/UserManager/UserValidator/RequireUniqueEmail             | ユーザーの検証に一意の電子メールを必要とするかどうか。 既定値: true。 詳細情報: [UserValidator<TUser, TKey>.RequireUniqueEmail](https://msdn.microsoft.com/library/dn613213.aspx)。                                                                   |  
| Authentication/UserManager/PasswordValidator/RequiredLength             | 最低限必要なパスワードの文字数。 既定: 8 詳細情報: [PasswordValidator.RequiredLength](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requiredlength.aspx)。                                       |  
| Authentication/UserManager/PasswordValidator/RequireNonLetterOrDigit    | パスワードに英字以外の文字または数字を許可するかどうか。 既定: false。 詳細情報: [PasswordValidator.RequireNonLetterOrDigit](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requirenonletterordigit.aspx)。 |  
| Authentication/UserManager/PasswordValidator/RequireDigit               | パスワードに数字 (0 ～ 9) が必要であるかどうか。 既定: false。 詳細情報: [PasswordValidator.RequireDigit](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requiredigit.aspx)。                |  
| Authentication/UserManager/PasswordValidator/RequireLowercase           | パスワードに小文字 (a ～ z) が必要かどうか。 既定: false。 詳細情報: [PasswordValidator.RequireLowercase](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requirelowercase.aspx)。        |  
| Authentication/UserManager/PasswordValidator/RequireUppercase           | パスワードに大文字 (A ～ Z) が必要かどうか。 既定: false。 詳細情報: [PasswordValidator.RequireUppercase](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requireuppercase.aspx)。       | 
|| 

## <a name="user-account-lockout-settings"></a>ユーザー アカウントのロックアウトの設定

以下ではアカウントを認証できないようにロックする場合の方法とタイミングの設定を説明します。 短期間に指定回数のパスワード失敗の操作が行われたのを検出すると、しばらくの間ユーザー アカウントをロックします。 そのユーザーは、その期間の経過後にもう一度実行できます。

| サイト設定の名前                                               | 内容                                                                                                                                                                                                                                     |
|-----------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/UserManager/UserLockoutEnabledByDefault          | ユーザーの作成時にユーザーのロックアウトを有効にするかどうかを示します。 既定値: true。 詳細情報: [UserManager<TUser, TKey>.UserLockoutEnabledByDefault](https://msdn.microsoft.com/library/dn613214.aspx)。                                                                                                  |  
| Authentication/UserManager/DefaultAccountLockoutTimeSpan        | Authentication/UserManager/MaxFailedAccessAttemptsBeforeLockout に達するまでの、ユーザーがロックアウトされるまでの既定の経過時間。 既定値: 24:00:00 (1 日)。 詳細情報: [UserManager<TUser, TKey>.DefaultAccountLockoutTimeSpan](https://msdn.microsoft.com/library/dn613201.aspx)。                 |  
| Authentication/UserManager/MaxFailedAccessAttemptsBeforeLockout | ロックアウトされるまでにユーザーがアクセス試行できる最大回数 (ロックアウトが有効な場合)。 既定: 5 詳細情報: [UserManager<TUser, TKey>.MaxFailedAccessAttemptsBeforeLockout](https://msdn.microsoft.com/library/dn613202.aspx)。                                                                        |  
| Authentication/ApplicationCookie/ExpireTimeSpan                 | クッキー認証セッションの既定の時間は有効になります。 既定値: 24:00:00 (1 日)。 詳細情報: [CookieAuthenticationOptions.ExpireTimeSpan](https://msdn.microsoft.com/library/microsoft.owin.security.cookies.cookieauthenticationoptions.expiretimespan(v=vs.113).aspx)。 |
||  

## <a name="cookie-authentication-site-settings"></a>Cookie 認証サイト設定

既定の認証 Cookie の動作を変更するための設定です。 [CookieAuthenticationOptions](https://msdn.microsoft.com/library/microsoft.owin.security.cookies.cookieauthenticationoptions.aspx) クラスで定義されます。

| サイト設定の名前   | 説明       |
|----------------------|------------------------------------------------|
| Authentication/ApplicationCookie/AuthenticationType                      | アプリケーション認証 cookie の種類です。 既定: ApplicationCookie。 詳細: [AuthenticationOptions::AuthenticationType](https://msdn.microsoft.com/library/dn300391.aspx).  |
| Authentication/ApplicationCookie/CookieName                              | ID を保持するために使用する cookie 名を決定します。 既定: .AspNet.Cookies。 詳細: [CookieAuthenticationOptions::CookieName](https://msdn.microsoft.com/library/dn385537.aspx).  |
| Authentication/ApplicationCookie/CookieDomain                            | Cookie の作成に使用するドメインを決定します。 詳細: [CookieAuthenticationOptions::CookieDomain](https://msdn.microsoft.com/library/dn385536.aspx).  |
| Authentication/ApplicationCookie/CookiePath                              | cookie の作成に使用するパスを決定します。 既定: /。 詳細: [CookieAuthenticationOptions::CookiePath](https://msdn.microsoft.com/library/dn385539.aspx). |
| Authentication/ApplicationCookie/CookieHttpOnly                          | クライアント側 JavaScript から Cookie へのアクセスをブラウザーが許可するかどうか決定します。 既定値: true。 詳細: [CookieAuthenticationOptions::CookieHttpOnly](https://msdn.microsoft.com/library/dn385540.aspx).                     |
| Authentication/ApplicationCookie/CookieSecure                            | cookie が HTTPS 要求でのみ送信されるかを決定します。 既定: SameAsRequest。 詳細: [CookieAuthenticationOptions::CookieSecure](https://msdn.microsoft.com/library/dn385538.aspx).  |
| Authentication/ApplicationCookie/ExpireTimeSpan                          | アプリケーション Cookie が作成された時点から有効状態にとどまる時間をコントロールします。 既定: 14 日です。 詳細: [CookieAuthenticationOptions::ExpireTimeSpan](https://msdn.microsoft.com/library/microsoft.owin.security.cookies.cookieauthenticationoptions.expiretimespan(v=vs.113).aspx).  |
| Authentication/ApplicationCookie/SlidingExpiration                       | SlidingExpiration は true に設定されて、有効期限ウィンドウの半分を過ぎた要求を処理するときはいつでも、ミドルウェアに新しい有効期限の新しい Cookie を再発行するよう指示します。 既定値: true。 詳細: [CookieAuthenticationOptions::SlidingExpiration](https://msdn.microsoft.com/library/dn385548.aspx). |
| Authentication/ApplicationCookie/LoginPath                               | LoginPath プロパティはミドルウェアに対し、送信 401 未承認ステータス コードを指定ログイン パス上の 302 リダイレクトに変更する必要があることを通知します。 既定: ~/signin。 詳細: [CookieAuthenticationOptions::LoginPath](https://msdn.microsoft.com/library/dn385541.aspx).                                            |
| Authentication/ApplicationCookie/LogoutPath                              | LogoutPath がミドルウェアにより提供される場合、ReturnUrlParameter に基づきそのパスに対する要求がリダイレクトされます。 詳細: [CookieAuthenticationOptions::LogoutPath](https://msdn.microsoft.com/library/dn385545.aspx).               |
| Authentication/ApplicationCookie/ReturnUrlParameter                      | ReturnUrlParameter は、401 未承認ステータス コードがログイン パス上に 302 リダイレクトに変更されるときの、ミドルウェアにより追加されるクエリ文字列パラメーターの名前を決定します。 詳細: [CookieAuthenticationOptions::ReturnUrlParameter](https://msdn.microsoft.com/library/dn385546.aspx).                           |
| Authentication/ApplicationCookie/SecurityStampValidator/ValidateInterval | セキュリティ スタンプ検証間の期間。 既定: 30 分。 詳細: [SecurityStampValidator::OnValidateIdentity](https://msdn.microsoft.com/library/microsoft.aspnet.identity.owin.securitystampvalidator.onvalidateidentity.aspx).                    |
| Authentication/TwoFactorCookie/AuthenticationType                        | 2 要素認証 cookie の種類です。 既定: TwoFactorCookie。 詳細: [AuthenticationOptions::AuthenticationType](https://msdn.microsoft.com/library/dn300391.aspx).            |
| Authentication/TwoFactorCookie/ExpireTimeSpan                            | 2 要素 Cookie が作成された時点から有効状態にとどまる時間をコントロールします。 既定: 5 分。 詳細: [CookieAuthenticationOptions::ExpireTimeSpan](https://msdn.microsoft.com/library/dn385543.aspx).     |
|||

### <a name="see-also"></a>関連項目

[ポータル認証の構成](configure-portal-authentication.md)  
[ポータル用 OAuth2 プロバイダーの設定](configure-oauth2-settings.md)  
[ポータルの Open ID 接続プロバイダーの設定](configure-openid-settings.md)  
[ポータル用 WS-Federation プロバイダーの設定](configure-ws-federation-settings.md)  
[ポータルの SAML 2.0 プロバイダーの設定](configure-saml2-settings.md)  
