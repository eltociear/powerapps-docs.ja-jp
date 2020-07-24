---
title: 簡素化された認証と ID プロバイダー構成を使用する (プレビュー) | MicrosoftDocs
description: 迅速で簡単な、簡素化されたポータル構成を認証に使用する方法を説明します。
author: sandhangitmsft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 05/05/2020
ms.author: sandhan
ms.reviewer: tapanm
ms.openlocfilehash: cd4ddd631443cbd51693582045f13ada587efda2
ms.sourcegitcommit: c12260f372ad2cc48d3146be570d2088c9ef1d86
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2020
ms.locfileid: "3491407"
---
# <a name="simplified-authentication-and-identity-provider-configuration-preview"></a>簡素化された認証と ID プロバイダー構成 (プレビュー)

[このトピックはプレリリース ドキュメントであり、変更されることがあります。]

認証の設定は、すべてのポータルでコア カスタマイズです。 Power Apps ポータルでの簡素化された ID プロバイダー構成は、ID プロバイダーの設定のためのアプリ内ガイダンスを提供し、設定の複雑さを抽象化します。 メーカーと管理者は、サポートされている ID プロバイダーのポータルを簡単に構成できます。

> [!NOTE]
> 簡素化された認証と ID プロバイダー構成機能はプレビュー段階です。 このプレビュー機能にアクセスするには、[Power Apps プレビュー ](https://make.preview.powerapps.com) を使用する必要があります。 このプレビュー機能が一般提供されると、[Power Apps](https://make.powerapps.com) からアクセスできるようになります。 ポータルでこのプレビュー機能をオンまたはオフにすることはできません。 プレビュー機能の詳細については、[実験とプレビュー機能についてPower Apps](https://docs.microsoft.com/powerapps/maker/canvas-apps/working-with-experimental-preview) を参照してください。 

## <a name="overview"></a>概要

簡素化されたポータル認証の構成を使用して、[Power Apps プレビュー](https://make.preview.powerapps.com) からポータル ID プロバイダーを有効化、無効化、および構成できます。 ID プロバイダーを選択した後、[認証を手動で設定する](set-authentication-identity.md) 代わりに、プロンプトに従ってプロバイダーの設定を簡単に入力できます。

### <a name="authentication-settings"></a>認証設定

ポータルの ID プロバイダーの構成を開始するには :

1. [Power Apps プレビュー](https://make.preview.powerapps.com) に移動します。

1. 左側のナビゲーション ウィンドウから、**アプリ**を選択します。

    ![アプリを選択する](media/use-simplified-authentication-configuration/select-apps.png "アプリを選択する")

1. 使用可能なアプリの一覧からポータルを選択します。

1. 上部メニューから、**設定**を選択します。 **その他のコマンド** (**...**) を選択してから**設定**を選択することもできます。

    ![設定を選択する](media/use-simplified-authentication-configuration/select-settings.png "設定を選択する")

1. ワークスペースの右側の設定から、**認証設定**を選択します。

    ![認証設定](media/use-simplified-authentication-configuration/portal-settings-right-pane.png "認証設定")

構成可能な ID プロバイダーの一覧が表示されます。

![ID プロバイダー](media/use-simplified-authentication-configuration/portal-authentication-settings.png "ID プロバイダー")

> [!NOTE]
> Power Apps ポータルは、いくつかの ID プロバイダーをサポートしています。 ただし、簡素化された認証および ID プロバイダー構成の機能は現在、上記の ID プロバイダーのみをサポートしています。

#### <a name="authentication-settings-from-the-portal-details-page"></a>ポータルの詳細ページからの認証設定

ポータルの詳細ページから ID プロバイダーを表示することもできます。

1. 使用可能なアプリの一覧からポータルを選択します。

1. 上部メニューから**詳細**を選択します。 **その他のコマンド** (**...**) を選択してから**詳細**を選択することもできます。

    ![詳細を選択する](media/use-simplified-authentication-configuration/select-details.png "詳細を選択する")

詳細ページに **ID プロバイダー** セクションが表示されます。

![ポータルの詳細](media/use-simplified-authentication-configuration/portal-details.png "ポータルの詳細")

> [!NOTE]
> ポータルの詳細ページから**すべて表示**を選択すると、ID プロバイダーの完全なリストに移動します。

## <a name="general-authentication-settings"></a>全般的な認証設定

**ID プロバイダー** ページで**認証設定**を選択すると、次の全般的な認証設定を構成できます。

![全般的な認証設定](media/use-simplified-authentication-configuration/general-authentication-settings.png "全般的な認証設定")

- **外部ログイン** - **オフ**に設定すると、外部アカウントの登録とサインインを無効化および非表示にします。
<br>外部認証は、ASP.NET ID API によって提供されます。 この場合、アカウント資格情報とパスワード管理は、Facebook、LinkedIn、Google、Twitter、Microsoft などのサード パーティの ID プロバイダーによって処理されます。 ユーザーは、ポータルに登録するための外部 ID を選択して、ポータルへのアクセスにサインアップします。 登録した後、外部 ID でローカル アカウントと同じ機能にアクセスできます。 関連するサイト設定については、[外部アカウントを管理する](set-authentication-identity.md#manage-external-accounts) を参照してください。

- **[オープン登録](configure-portal-authentication.md#open-registration)** - **オフ**に設定すると、外部アカウントの登録を無効化および非表示にします。

**ID プロバイダー** セクションの右上隅にある**設定**を選択して、ポータルの詳細ページから全般的な認証設定に移動することもできます。

![詳細ページからの全般的な認証設定](media/use-simplified-authentication-configuration/general-settings-from-details.png "詳細ページからの全般的な認証設定")

### <a name="default-identity-provider"></a>既定の ID プロバイダー

任意の ID プロバイダーを既定として設定できます。 ID プロバイダーを既定として設定している場合、ポータルにサインインするユーザーはポータルのサインイン ページにリダイレクトされません。代わりに、サインイン処理では常に、選択したプロバイダーを使用してサインインするように既定で設定されます。

![既定の ID プロバイダー](media/use-simplified-authentication-configuration/set-default.png "既定の ID プロバイダー")

> [!IMPORTANT]
> ID プロバイダーを既定として設定すると、ユーザーは他の ID プロバイダーを選択することができなくなります。

ID プロバイダーを既定として設定した後、既定として削除するには**既定として削除**を選択します。 ID プロバイダーを既定から削除すると、ユーザーはポータルのサインイン ページにリダイレクトされ、有効にした ID プロバイダーの中から選択できます。

> [!NOTE]
> 構成された ID プロバイダーのみを既定として設定できます。 **既定として設定**オプションは、ID プロバイダーを構成した後に使用可能になります。

## <a name="add-configure-or-delete-an-identity-provider"></a>ID プロバイダーを追加、構成、または削除する

構成可能ないくつかの ID プロバイダーが既定で追加されます。 追加の Azure Active Directory (Azure AD) B2C プロバイダーを追加するか、または LinkedIn や Microsoft などの利用可能な OAuth 2.0 プロバイダーを構成できます。

> [!NOTE]
> - このインターフェイスを使用する場合、[ローカル サインイン](configure-portal-authentication.md) および Azure Active Directory プロバイダーの構成を変更することはできません。
> - **Facebook**, **LinkedIn**, **Google**, **Twitter**, and **Microsoft** など、OAuth 2.0 の各 ID プロバイダーのインスタンスは 1 つだけ持つことができます。
> - ID プロバイダー構成の更新がポータルに反映されるまでに数分かかる場合があります。 変更をすぐに適用するには、[ポータルを再起動](../admin/admin-overview.md#open-power-apps-portals-admin-center) します。

### <a name="add-or-configure-a-provider"></a>プロバイダーの追加または構成

ID プロバイダーを追加するには、**認証設定**から**プロバイダーの追加**を選択します。

![設定からプロバイダーを追加する](media/use-simplified-authentication-configuration/add-provider-from-settings.png "設定からプロバイダーを追加する")

ポータルの詳細ページから**プロバイダーの追加**を選択することもできます。

![詳細ページからプロバイダーを追加する](media/use-simplified-authentication-configuration/add-provider-from-details.png "詳細ページからプロバイダーを追加する")

利用可能なプロバイダーの一覧から選択し、名前を入力してから、**次**を選択してプロバイダー設定を構成します。

![新しいプロバイダーを追加する](media/use-simplified-authentication-configuration/add-provider.png "新しいプロバイダーを追加する")

> [!NOTE]
> ここで入力した**プロバイダー名**は、ユーザーがこのプロバイダーを選択するときに使用するボタンのテキストとして、ユーザーのサインイン ページに表示されます。

プロバイダーを構成するには、**クリックして構成**を選択 (または**その他のコマンド** (**...**) を選択してから**構成**を選択) します。

![プロバイダーの構成](media/use-simplified-authentication-configuration/configure-provider.png "プロバイダーの構成")

> [!NOTE]
> **プロバイダーの追加**または**構成**を使用して、プロバイダーを初めて追加または構成します。 プロバイダーを構成した後、編集できます。 プロバイダー名のハイパーリンクを選択して、構成オプションをすばやく開くこともできます。

**次**を選択した後の構成の手順は、選択する ID プロバイダーの種類によって異なります。 たとえば、Azure Active Directory B2C の構成は、LinkedIn の設定方法とは異なります。 選択したプロバイダーを構成する方法については、この記事の後半のプロバイダー固有のセクションを参照してください。

### <a name="edit-a-provider"></a>プロバイダーの編集

プロバイダーを追加して構成すると、ポータル設定または詳細ページで**有効**状態のプロバイダーを確認できます。

構成したプロバイダーを編集するには、プロバイダーを選択し、**その他のコマンド** (**...**) を選択してから、**構成を編集**を選択します。

![プロバイダーの編集](media/use-simplified-authentication-configuration/edit-provider.png "プロバイダーの編集")

選択したプロバイダーの種類の設定を編集するには、この記事の後半にあるプロバイダー固有のセクションを参照してください。

### <a name="delete-a-provider"></a>プロバイダーの削除

ID プロバイダーを削除するには、**その他のコマンド** (**...**) を選択してから、**削除**を選択します。

![プロバイダーの削除](media/use-simplified-authentication-configuration/delete-provider.png "プロバイダーの削除")

プロバイダーを削除すると、選択したプロバイダーの種類のプロバイダー構成が削除され、プロバイダーの構成が再び可能になります。

> [!NOTE]
> プロバイダーを削除すると、プロバイダーのポータル構成のみが削除されます。 たとえば、LinkedIn プロバイダーを削除した場合、LinkedIn アプリとアプリ構成はそのまま残ります。 同様に、Azure Active Directory B2C プロバイダーを削除した場合、ポータル構成のみが削除されます。このプロバイダーの Azure テナント構成は変更されません。

## <a name="configure-the-azure-active-directory-b2c-provider"></a>Azure Active Directory B2C プロバイダーの構成

### <a name="step-1---configure-the-azure-active-directory-b2c-application"></a>ステップ 1 - Azure Active Directory B2C アプリケーションの構成

![Azure AD B2C アプリの構成](media/use-simplified-authentication-configuration/configure-ad-b2c-step1.png "Azure AD B2C アプリの構成")

ID プロバイダーとして Azure AD B2C を使用する方法 :

1. [Azure AD B2C テナントを作成して構成](https://docs.microsoft.com/azure/active-directory-b2c/tutorial-create-tenant) します。

1. テナントに [アプリケーションを登録](https://docs.microsoft.com/azure/active-directory-b2c/tutorial-register-applications?tabs=applications#register-a-web-application) します。 アプリケーションの構成中にウィザードで提供される**返信 URL** を使用します。

    > [!NOTE]
    >  **暗黙的なフローの許可** フィールドで **はい** を選択し、 **返信 URL**  フィールドでポータルの URL を入力する必要があります。

1. [ユーザー フローを作成](https://docs.microsoft.com/azure/active-directory-b2c/tutorial-create-user-flows#create-a-sign-up-and-sign-in-user-flow) します。 必要に応じて、[パスワード リセット ユーザー フローを作成](https://docs.microsoft.com/azure/active-directory-b2c/tutorial-create-user-flows#create-a-password-reset-user-flow) します。

1. **tfp** を含む**発行者 (iss) 要求** URL との[トークンの互換性を構成](https://docs.microsoft.com/azure/active-directory-b2c/configure-tokens#configure-token-compatibility) します。 詳細: [トークンの互換性](https://docs.microsoft.com/azure/active-directory-b2c/tokens-overview#compatibility)

### <a name="step-2---configure-site-settings"></a>ステップ 2 - サイトの設定を構成する

Azure AD B2C プロバイダーの以下のサイト設定とパスワード リセット ポリシーを構成します。

![サイトの設定を構成する](media/use-simplified-authentication-configuration/configure-ad-b2c-step2.png "サイトの設定を構成する")

- **オーソリティ** - サインアップおよびサインイン ポリシーのユーザー フローのメタデータで定義された発行者 URL。
<br> 発行者 URL を取得する方法 :

   1. [ステップ 1](#step-1---configure-the-azure-active-directory-b2c-application) で作成したサインアップおよびサインイン ユーザー フローを開きます。 このステップでは、[Azure ポータル](https://portal.azure.com) で Azure AD B2C テナントに移動する必要があります。
   1. **ユーザー フローを実行する**を選択し、**開く**ダイアログ ボックスで、上部にある URL を選択して構成ドキュメントを開きます。 <br> URL は、*OpenID の既知の構成エンドポイント*としても知られる *OpenID 接続 IDプロバイダーの構成文書*を参照しています。
   1. 新しいブラウザーで開く構成ドキュメントから**発行者** URL をコピーします。  

- **クライアント ID** - [ステップ 1](#step-1---configure-the-azure-active-directory-b2c-application) で作成した Azure AD B2C アプリケーションの**アプリケーション ID** を入力します。

- **リダイレクト URI** - ポータルの URL を入力します。 <br> リダイレクト URI を変更する必要があるのは、カスタム ドメイン名を使用する場合だけです。

#### <a name="password-reset-settings"></a>パスワードのリセット設定

- **既定のポリシー ID** - [ステップ 1](#step-1---configure-the-azure-active-directory-b2c-application) で作成したサインアップおよびサインイン ユーザー フローの名前を入力します。 名前の先頭に *B2C_1* が付きます。

- **パスワード リセット ポリシーの ID** - [ステップ 1](#step-1---configure-the-azure-active-directory-b2c-application) で作成したパスワード リセット ユーザー フローの名前を入力します。 名前の先頭に *B2C_1* が付きます。

- **有効な発行者** - [ステップ 1](#step-1---configure-the-azure-active-directory-b2c-application) で作成したサインアップおよびサインイン ユーザー フローとパスワード リセット ユーザー フローの発行者 URL のカンマ区切りの一覧。 
<br> サインアップおよびサインイン ユーザー フローとパスワード リセットユーザー フローの発行者の URL を取得するには、各フローを開き、このセクションの前半の**オーソリティ**の手順に従います。

サイト設定の詳細については、[関連サイトの設定](azure-ad-b2c.md#related-site-settings) を参照してください。

### <a name="step-3---configure-additional-settings"></a>ステップ 3 - 追加設定を構成する

Azure AD B2C ID プロバイダーの追加設定を構成することができます。

![追加設定を構成する](media/use-simplified-authentication-configuration/configure-ad-b2c-step3.png "追加設定を構成する")

- **登録クレーム マッピング** - サインアップ中に作成された Azure AD B2C から返されたクレーム値を取引先担当者レコードの属性にマップするために使用する論理名 / クレーム ペアのリスト。 <br> たとえば、**役職 (jobTitle)** および**郵便番号 (postalCode)** をユーザー フローで**ユーザー属性**として有効にして、対応する連絡先エンティティ フィールド**役職 (jobtitle)** および**住所 1: 郵便番号 (address1_postalcode)** を更新する場合、クレーム マッピングには ```jobtitle=jobTitle,address1_postalcode=postalCode``` と入力します。
- **ログイン クレーム マッピング** - サインイン後に Azure AD B2C から返されたクレーム値を取引先担当者レコードの属性にマップするために使用する論理名 / クレーム ペアのリスト。 <br> たとえば、**役職 (jobTitle)** および**郵便番号 (postalCode)** をユーザー フローで**アプリケーション クレーム**として有効にして、対応する連絡先エンティティ フィールド**役職 (jobtitle)** および**住所 1: 郵便番号 (address1_postalcode)** を更新する場合、クレーム マッピングには ```jobtitle=jobTitle,address1_postalcode=postalCode``` と入力します。
- **外部ログアウト** - フェデレーションによるサインアウトを有効または無効にします。**オン**に設定すると、ユーザーはポータルからサインアウトしたときにフェデレーション サインアウト ユーザー エクスペリエンスにリダイレクトされます。 **オフ**に設定すると、ユーザーはポータルからのみサインアウトします。
- **メールによる取引先担当者マッピング** - 取引先担当者が対応するメールにマップされるかどうかを指定します。 この設定を**オン**に設定すると、一意の取引先担当者レコードが一致するメール アドレスに関連付けられ、ユーザーが正常にサインインした後に自動的に外部 ID プロバイダーがその取引先担当者に割り当てられます。
- **登録が有効** - ポータルの[オープン登録](configure-portal-authentication.md#open-registration) をオンまたはオフにします。 このトグルを**オフ**にすると、外部アカウント登録を無効化および非表示にします。

**確認**を選択して構成の概要を表示し、ID 構成を完了します。

クレーム マッピングの詳細については、[Azure AD B2C クレーム マッピングのシナリオ](azure-ad-b2c.md#claims-mapping) を参照してください。

Azure AD B2C ID プロバイダーを構成する方法の詳細については、[ポータルの Azure AD B2C プロバイダー設定](azure-ad-b2c.md#customize-the--ad-b2c-user-interface) を参照してください。

## <a name="configure-the-facebook-provider"></a>Facebook プロバイダーの構成

![Facebook アプリの構成](media/use-simplified-authentication-configuration/configure-facebook.png "Facebook アプリの構成")

ID プロバイダーとして **Facebook** を使用するには 、リダイレクト URL を使用して [Facebook でアプリを作成](https://developers.facebook.com) する必要があります。

リダイレクト URL は、認証が成功した後にユーザーをポータルにリダイレクトするために Facebook アプリによって使用されます。 ポータルでカスタム ドメイン名を使用している場合は、ここで提供されているものとは異なる URL を使用している可能性があります。

Facebook の**ポータル サイト設定** :

- **クライアント ID** - アプリ用に Facebook によって生成された一意のアプリ ID。
- **クライアント シークレット** - Facebook アプリのアプリ シークレット。

Facebook の追加設定を構成するには、[OAuth 2 プロバイダーの追加設定を構成する](#configure-additional-settings-for-oauth-2-providers) を参照してください。

OAuth 2 プロバイダーを構成する方法の詳細については、[ポータルの OAuth 2 プロバイダー設定](configure-oauth2-settings.md) を参照してください。

## <a name="configure-the-linkedin-provider"></a>LinkedIn プロバイダーの構成

![LinkedIn アプリの構成](media/use-simplified-authentication-configuration/configure-linkedin.png "LinkedIn アプリの構成")

ID プロバイダーとして **LinkedIn** を使用するには 、リダイレクト URL を使用して [LinkedIn でアプリを作成](https://www.linkedin.com/developers/apps) する必要があります。

リダイレクト URL は、認証が成功した後にユーザーをポータルにリダイレクトするために LinkedIn アプリによって使用されます。 ポータルでカスタム ドメイン名を使用している場合は、ここで提供されているものとは異なる URL を使用している可能性があります。

LinkedIn の**ポータル サイト設定** :

- **クライアント ID** - アプリ用に LinkedIn によって生成された一意のアプリ ID。
- **クライアント シークレット** - LinkedIn アプリのアプリ シークレット。

LinkedIn の追加設定を構成するには、[OAuth 2 プロバイダーの追加設定を構成する](#configure-additional-settings-for-oauth-2-providers) を参照してください。

OAuth 2 プロバイダーを構成する方法の詳細については、[ポータルの OAuth 2 プロバイダー設定](configure-oauth2-settings.md) を参照してください。

## <a name="configure-the-google-provider"></a>Google プロバイダーの構成

![Google アプリの構成](media/use-simplified-authentication-configuration/configure-google.png "Google アプリの構成")

ID プロバイダーとして **Google** を使用するには 、リダイレクト URL を使用して [Google でアプリを作成](https://console.developers.google.com/) する必要があります。

リダイレクト URL は、認証が成功した後にユーザーをポータルにリダイレクトするために Google アプリによって使用されます。 ポータルでカスタム ドメイン名を使用している場合は、ここで提供されているものとは異なる URL を使用している可能性があります。

Google の**ポータル サイト設定** :

- **クライアント ID** - アプリ用に Google によって生成された一意のアプリ ID。
- **クライアント シークレット** - アプリ用に Google によって生成されたクライアント シークレット。

Google の追加設定を構成するには、[OAuth 2 プロバイダーの追加設定を構成する](#configure-additional-settings-for-oauth-2-providers) を参照してください。

OAuth 2 プロバイダーを構成する方法の詳細については、[ポータルの OAuth 2 プロバイダー設定](configure-oauth2-settings.md) を参照してください。

## <a name="configure-the-twitter-provider"></a>Twitter プロバイダーの構成

![Twitter アプリの構成](media/use-simplified-authentication-configuration/configure-twitter.png "Twitter アプリの構成")

ID プロバイダーとして **Twitter** を使用するには 、リダイレクト URL を使用して [Twitter でアプリを作成](https://developer.twitter.com/apps) する必要があります。

リダイレクト URL は、認証が成功した後にユーザーをポータルにリダイレクトするために Twitter アプリによって使用されます。 ポータルでカスタム ドメイン名を使用している場合は、ここで提供されているものとは異なる URL を使用している可能性があります。

Twitter の**ポータル サイト設定** :

- **クライアント ID** - アプリ用に Twitter によって生成された一意のアプリ ID。
- **クライアント シークレット** - アプリ用に Twitter によって生成されたクライアント シークレット。

Twitter の**追加設定**を構成するには、[OAuth 2 プロバイダーの追加設定を構成する](#configure-additional-settings-for-oauth-2-providers) を参照してください。

OAuth 2 プロバイダーを構成する方法の詳細については、[ポータルの OAuth 2 プロバイダー設定](configure-oauth2-settings.md) を参照してください。

## <a name="configure-the-microsoft-provider"></a>Microsoft プロバイダーの構成

![Microsoft アプリの構成](media/use-simplified-authentication-configuration/configure-microsoft.png "Microsoft アプリの構成")

ID プロバイダーとして **Microsoft** を使用するには 、リダイレクト URL を使用して [Azure portal でアプリを作成](https://aka.ms/AppRegistrations) する必要があります。

リダイレクト URL は、認証が成功した後にユーザーをポータルにリダイレクトするために Microsoft アプリによって使用されます。 ポータルでカスタム ドメイン名を使用している場合は、ここで提供されているものとは異なる URL を使用している可能性があります。

Microsoft の**ポータル サイト設定** :

- **クライアント ID** - アプリ用に Microsoft によって生成された一意のアプリ ID。
- **クライアント シークレット** - アプリ用に Microsoft によって生成されたクライアント シークレット。

Microsoft の**追加設定**を構成するには、[OAuth 2 プロバイダーの追加設定を構成する](#configure-additional-settings-for-oauth-2-providers) を参照してください。

OAuth 2 プロバイダーを構成する方法の詳細については、[ポータルの OAuth 2 プロバイダー設定](configure-oauth2-settings.md) を参照してください。

## <a name="configure-additional-settings-for-oauth-2-providers"></a>OAuth 2 プロバイダーの追加設定を構成する

このセクションの追加の認証設定は、**Facebook**、**Twitter**、**Microsoft**、**LinkedIn**、および**Google** プロバイダーに適用されます。

![追加設定を構成する](media/use-simplified-authentication-configuration/additional-oauth-settings.png "追加設定を構成する")

- **認証の種類** - OWIN 認証のミドルウェアの種類 : [AuthenticationOptions.AuthenticationType](https://docs.microsoft.com/previous-versions/aspnet/mt152183(v=vs.113)?redirectedfrom=MSDN)。 たとえば、https://sts.windows.net/contoso.onmicrosoft.com/ などとします。
- **認証のモード** - OWIN 認証のミドルウェアのモード : [AuthenticationOptions.AuthenticationMode](https://docs.microsoft.com/previous-versions/aspnet/mt152179(v=vs.113)?redirectedfrom=MSDN)。
- **バックチャネルのタイムアウト** - バックチャネル通信のタイムアウト値 (ミリ秒) : [MicrosoftAccountAuthenticationOptions.BackchannelTimeout](https://docs.microsoft.com/previous-versions/aspnet/mt174421(v=vs.113)?redirectedfrom=MSDN)。
- **コールバック パス** - ユーザー エージェントが返される、アプリケーションの基本パス内におけるリクエスト パス : [MicrosoftAccountAuthenticationOptions.CallbackPath](https://docs.microsoft.com/previous-versions/aspnet/mt174433(v=vs.113)?redirectedfrom=MSDN)。
- **認証の種類としてサインイン** - 実際にユーザーのクレーム ID の発行を担当する別の認証ミドルウェアの名前 : [MicrosoftAccountAuthenticationOptions.SignInAsAuthenticationType](https://docs.microsoft.com/previous-versions/aspnet/mt174430(v=vs.113)?redirectedfrom=MSDN)。
- **スコープ** - 要求に対するアクセス許可のコンマ区切りの一覧 : [MicrosoftAccountAuthenticationOptions.Scope](https://docs.microsoft.com/previous-versions/aspnet/mt174435(v=vs.113)?redirectedfrom=MSDN)。
- **登録が有効** - 既存の ID プロバイダーの登録要件を有効または無効にする。 無効にすると、ユーザーの取引先担当者レコードが存在しない場合、エラーによってユーザーは登録を拒否されます。 有効にすると、サイト設定 **Authentication/Registration/Enabled** が true に設定されている場合にのみ、新規ユーザーのユーザー登録が許可されます。

詳細については、以下の [OAuth2 のサイト設定](configure-oauth2-settings.md#create-site-settings-by-using-oauth2) を参照してください。

### <a name="see-also"></a>関連項目

- [ポータル用の認証 ID の設定](set-authentication-identity.md)
- [Azure AD B2C プロバイダー設定を構成する](azure-ad-b2c.md)
- [OAuth2 プロバイダーの設定の構成](configure-oauth2-settings.md)
