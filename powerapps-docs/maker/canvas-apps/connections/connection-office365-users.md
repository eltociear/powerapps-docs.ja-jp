---
title: Dynamics Office 365 ユーザーの接続の概要 | Microsoft Docs
description: いくつかの例を通して Office 365 ユーザーへの接続方法の段階的説明とすべての機能の紹介について参照する
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/07/2016
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: aacb19180fc41cc52a9d292fd9d3282f19cc649f
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3306338"
---
# <a name="connect-to-office-365-users-connection-from-power-apps"></a>Power Apps から Office 365 ユーザー接続に接続する
![Office 365 Users](./media/connection-office365-users/office365icon.png)

Office 365 ユーザーを使用すると、自分の Office 365 アカウントを使用して組織内のユーザー プロファイルにアクセスできます。 プロファイル、ユーザーのプロファイル、ユーザーの上司または直属の部下を取得するなど、さまざまなアクションを実行できます。

この情報を、アプリのラベルに表示できます。 1 つの機能、複数の機能、または異なる機能の組みわせを表示できます。 たとえば、ユーザー名と電話番号を組み合わせる式を作成してから、この情報をアプリに表示できます。

このトピックでは、Office 365 ユーザーを接続として追加する方法、アプリに Office 365 ユーザーをデータ ソースとして追加する方法、およびギャラリー コントロールでテーブル データを使用する方法について説明します。

[!INCLUDE [connection-requirements](../../../includes/connection-requirements.md)]

## <a name="add-a-connection"></a>接続の追加
1. [データ接続を追加](../add-data-connection.md) して、**Office 365 ユーザー**を選択します:  

    ![Office 365 への接続](./media/connection-office365-users/add-office.png)
2. **接続**を選択します。サインインが求められた場合は、職場のアカウントを入力します。

Office 365 ユーザー接続が作成され、アプリに追加されました。 これにより、接続を使用できるようになりました。

## <a name="use-the-connection-in-your-app"></a>アプリで接続を使用する
### <a name="show-information-about-the-current-user"></a>現在のユーザーに関する情報を表示する
1. **挿入**メニューで、**ラベル**を選択します
2. 関数バーで、**[テキスト](../controls/properties-core.md)** プロパティに次のいずれかの式を設定します:

   `Office365Users.MyProfile().City`  
   `Office365Users.MyProfile().CompanyName`  
   `Office365Users.MyProfile().Country`  
   `Office365Users.MyProfile().Department`  
   `Office365Users.MyProfile().DisplayName`  
   `Office365Users.MyProfile().GivenName`  
   `Office365Users.MyProfile().Id`  
   `Office365Users.MyProfile().JobTitle`  
   `Office365Users.MyProfile().Mail`  
   `Office365Users.MyProfile().MailNickname`  
   `Office365Users.MyProfile().mobilePhone`  
   `Office365Users.MyProfile().OfficeLocation`  
   `Office365Users.MyProfile().PostalCode`  
   `Office365Users.MyProfile().Surname`  
   `Office365Users.MyProfile().TelephoneNumber`  
   `Office365Users.MyProfile().UserPrincipalName`  
   `Office365Users.MyProfile().AccountEnabled`  
   `Office365Users.MyProfile().BusinessPhones`

ラベルには、現在のユーザーに関する入力した情報が表示されます。

### <a name="show-information-about-another-user"></a>別のユーザーに関する情報を表示する
1. **挿入**メニューで、**テキスト**を選択してから、**テキスト入力**を選択します。 名前を **InfoAbout** に変更します:  

    ![コントロール名の変更](./media/connection-office365-users/renameinfoabout.png)
2. **InfoAbout** に、組織内のユーザーの電子メール アドレスを入力するか貼り付けます。 たとえば、*yourName*@*yourCompany.com* を入力します。
3. **ラベル** (**挿入**メニュー) を追加し、**[テキスト](../controls/properties-core.md)** プロパティに次のいずれかの式を設定します:

   * 別のユーザーに関する情報を表示する場合:  

     `Office365Users.UserProfile(InfoAbout.Text).City`  
     `Office365Users.UserProfile(InfoAbout.Text).CompanyName`  
     `Office365Users.UserProfile(InfoAbout.Text).Country`  
     `Office365Users.UserProfile(InfoAbout.Text).Department`  
     `Office365Users.UserProfile(InfoAbout.Text).DisplayName`  
     `Office365Users.UserProfile(InfoAbout.Text).GivenName`  
     `Office365Users.UserProfile(InfoAbout.Text).Id`  
     `Office365Users.UserProfile(InfoAbout.Text).JobTitle`  
     `Office365Users.UserProfile(InfoAbout.Text).Mail`  
     `Office365Users.UserProfile(InfoAbout.Text).MailNickname`  
     `Office365Users.UserProfile(InfoAbout.Text).mobilePhone`  
     `Office365Users.UserProfile(InfoAbout.Text).OfficeLocation`  
     `Office365Users.UserProfile(InfoAbout.Text).PostalCode`  
     `Office365Users.UserProfile(InfoAbout.Text).Surname`  
     `Office365Users.UserProfile(InfoAbout.Text).TelephoneNumber`  
     `Office365Users.UserProfile(InfoAbout.Text).UserPrincipalName`  
     `Office365Users.UserProfile(InfoAbout.Text).AccountEnabled`  
     `Office365Users.UserProfile(InfoAbout.Text).BusinessPhones`

   * 別のユーザーの上司に関する情報を表示する場合:  

     `Office365Users.Manager(InfoAbout.Text).City`  
     `Office365Users.Manager(InfoAbout.Text).CompanyName`  
     `Office365Users.Manager(InfoAbout.Text).Country`  
     `Office365Users.Manager(InfoAbout.Text).Department`  
     `Office365Users.Manager(InfoAbout.Text).DisplayName`  
     `Office365Users.Manager(InfoAbout.Text).GivenName`  
     `Office365Users.Manager(InfoAbout.Text).Id`  
     `Office365Users.Manager(InfoAbout.Text).JobTitle`  
     `Office365Users.Manager(InfoAbout.Text).Mail`  
     `Office365Users.Manager(InfoAbout.Text).MailNickname`  
     `Office365Users.Manager(InfoAbout.Text).mobilePhone`  
     `Office365Users.Manager(InfoAbout.Text).OfficeLocation`  
     `Office365Users.Manager(InfoAbout.Text).PostalCode`  
     `Office365Users.Manager(InfoAbout.Text).Surname`  
     `Office365Users.Manager(InfoAbout.Text).TelephoneNumber`  
     `Office365Users.Manager(InfoAbout.Text).UserPrincipalName`  
     `Office365Users.Manager(InfoAbout.Text).AccountEnabled`  
     `Office365Users.Manager(InfoAbout.Text).BusinessPhones`

ラベルに、指定したユーザーまたはそのユーザーの上司に関する入力した情報が表示されます。

> [!NOTE]
> Common Data Service のエンティティに基づくアプリを開発する場合は、電子メール アドレスではなく ID でユーザーを指定できます。

たとえば、[アプリを自動で作成](../data-platform-create-app.md) し、**ラベル** コントロールが含まれる画面を追加し、コントロールの**テキスト** プロパティを次の式に設定できます:
<br>**Office365Users.UserProfile(BrowseGallery1.Selected.CreatedByUser).DisplayName**

連絡先を作成して、アプリの閲覧画面でその連絡先を選択すると、**ラベル** コントロールに表示名が表示されます。

### <a name="show-the-direct-reports-of-another-user"></a>別のユーザーの直属の部下を表示する
1. **テキスト入力**コントロール (**挿入**メニュー > **テキスト**) を追加し、名前を **InfoAbout** に変更します。
2. **InfoAbout** に、組織内のユーザーの電子メール アドレスを入力します。 たとえば、*yourManagersName*@*yourCompany.com* を入力します
3. **テキスト付き** ギャラリー (**挿入**メニュー > **ギャラリー**) を追加し、**[項目](../controls/properties-core.md)** プロパティに次の式を設定します:

    `Office365Users.DirectReports(InfoAbout.Text)`

    ギャラリーに、入力したユーザーの直属の部下に関する情報が表示されます。

    ギャラリーを選択すると、右側のウィンドウにそのギャラリーのオプションが表示されます。
4. 2 番目のリストで、**JobTitle** を選択します。 3 番目のリストで、**DisplayName**  を選択します。 ギャラリーが更新され、これらの値が表示されます。  

> [!NOTE]
> 1 番目のボックスは、実際にはイメージ コントロールです。 画像がない場合、画像コントロールを削除し、その場所にラベルを追加できます。 [コントロールの追加および構成](../add-configure-controls.md) は優れたリソースです。

### <a name="search-for-users"></a>ユーザーを検索する
1. **テキスト入力**コントロール (**挿入**メニュー > **テキスト**) を追加し、名前を **SearchTerm** に変更します。 検索対象の名前を入力します。 たとえば、名を入力します。
2. **テキスト付き** ギャラリー (**挿入**メニュー > **ギャラリー**) を追加し、**[項目](../controls/properties-core.md)** プロパティに次の式を設定します:

    `Office365Users.SearchUser({searchTerm: SearchTerm.Text})`

    ギャラリーでは、入力した検索テキストを含む名前のユーザーが表示されます。

    ギャラリーを選択すると、右側のウィンドウにそのギャラリーのオプションが表示されます。
3. 2 番目のリストで、**電子メール**を選択します。 3 番目のリストで、**DisplayName**  を選択します。

    ギャラリーの 2 番目と 3 番目のラベルが更新されます。

## <a name="view-the-available-functions"></a>使用可能な関数を表示する
この接続には、次の関数が含まれています:

| 関数名 | 内容 |
| --- | --- |
| [DirectReports](connection-office365-users.md#directreports) |指定したユーザーの直属の部下を返します。 |
| [管理者](connection-office365-users.md#manager) |指定したユーザーの上司のユーザー プロファイルを取得します。 |
| [MyProfile](connection-office365-users.md#myprofile) |現在のユーザーのプロファイルを取得します。 |
| [SearchUser](connection-office365-users.md#searchuser) |ユーザー プロファイルの検索結果を取得します。 |
| [UserProfile](connection-office365-users.md#userprofile) |特定のユーザー プロファイルを取得します。 |

### <a name="myprofile"></a>MyProfile
プロファイルの取得: 現在のユーザーのプロファイルを取得します。

#### <a name="input-properties"></a>入力プロパティ
ありません。

#### <a name="output-properties"></a>出力プロパティ

| プロパティ名 | 種類​​ | 内容 |
| --- | --- | --- |
| 市区町村 | string |ユーザーの市区町村。 |
| CompanyName | string |ユーザーの会社。 |
| 国 | string |ユーザーの国/地域。 |
| 課 |string |ユーザーの部署。 |
| DisplayName |string |ユーザーの表示名。 |
| GivenName |string |ユーザーの名前。 |
| ID |string |ユーザー ID。 |
| JobTitle |string |ユーザーの役職。 |
| Mail |string |ユーザーの電子メール ID。 |
| MailNickname |string |ユーザーのニックネーム。 |
| mobilePhone | string |ユーザーの携帯電話。 |
| OfficeLocation | string |ユーザーの勤務先所在地。|
| PostalCode | string |ユーザーの郵便番号。|
| 姓 |string |ユーザーの姓。 |
| TelephoneNumber |string |ユーザーの電話番号。 |
| UserPrincipalName |string |ユーザー プリンシパル名。 |
| AccountEnabled |boolean |アカウントの有効化されたフラグ。 |
| BusinessPhones | string |ユーザーの会社の電話番号。|

### <a name="userprofile"></a>UserProfile
ユーザー プロファイルの取得: 特定のユーザー プロファイルを取得します。

#### <a name="input-properties"></a>入力プロパティ

| 件名 | データの種類 | 必要な領域 | 内容 |
| --- | --- | --- | --- |
| ID |string |はい |ユーザー プリンシパル名または電子メール ID。 |

#### <a name="output-properties"></a>出力プロパティ

| プロパティ名 | 種類​​ | 内容 |
| --- | --- | --- |
| 市区町村 | string |ユーザーの市区町村。 |
| CompanyName | string |ユーザーの会社。 |
| 国 | string |ユーザーの国/地域。 |
| 課 |string |ユーザーの部署。 |
| DisplayName |string |ユーザーの表示名。 |
| GivenName |string |ユーザーの名前。 |
| ID |string |ユーザー ID。 |
| JobTitle |string |ユーザーの役職。 |
| Mail |string |ユーザーの電子メール ID。 |
| MailNickname |string |ユーザーのニックネーム。 |
| 姓 |string |ユーザーの姓。 |
| TelephoneNumber |string |ユーザーの電話番号。 |
| UserPrincipalName |string |ユーザー プリンシパル名。 |
| AccountEnabled |boolean |アカウントの有効化されたフラグ。 |
| BusinessPhones | string |ユーザーの会社の電話番号。|

### <a name="manager"></a>マネージャー
上司の取得: 指定したユーザーの上司のユーザー プロファイルを取得します。

#### <a name="input-properties"></a>入力プロパティ

| 件名 | データの種類 | 必要な領域 | 内容 |
| --- | --- | --- | --- |
| ID |string |はい |ユーザー プリンシパル名または電子メール ID。 |

#### <a name="output-properties"></a>出力プロパティ

| プロパティ名 | 種類​​ | 内容 |
| --- | --- | --- |
| 市区町村 | string |ユーザーの市区町村。 |
| CompanyName | string |ユーザーの会社。 |
| 国 | string |ユーザーの国/地域。 |
| 課 |string |ユーザーの部署。 |
| DisplayName |string |ユーザーの表示名。 |
| GivenName |string |ユーザーの名前。 |
| ID |string |ユーザー ID。 |
| JobTitle |string |ユーザーの役職。 |
| Mail |string |ユーザーの電子メール ID。 |
| MailNickname |string |ユーザーのニックネーム。 |
| mobilePhone | string |ユーザーの携帯電話。 |
| OfficeLocation | string |ユーザーの勤務先所在地。|
| PostalCode | string |ユーザーの郵便番号。|
| 姓 |string |ユーザーの姓。 |
| TelephoneNumber |string |ユーザーの電話番号。 |
| UserPrincipalName |string |ユーザー プリンシパル名。 |
| AccountEnabled |boolean |アカウントの有効化されたフラグ。 |
| BusinessPhones | string |ユーザーの会社の電話番号。|

### <a name="directreports"></a>DirectReports
直属の部下の取得: 直属の部下を取得します。

#### <a name="input-properties"></a>入力プロパティ

| 件名 | データの種類 | 必要な領域 | 内容 |
| --- | --- | --- | --- |
| ID |string |はい |ユーザー プリンシパル名または電子メール ID。 |

#### <a name="output-properties"></a>出力プロパティ

| プロパティ名 | 種類​​ | 内容 |
| --- | --- | --- |
| 市区町村 | string |ユーザーの市区町村。 |
| CompanyName | string |ユーザーの会社。 |
| 国 | string |ユーザーの国/地域。 |
| 課 |string |ユーザーの部署。 |
| DisplayName |string |ユーザーの表示名。 |
| GivenName |string |ユーザーの名前。 |
| ID |string |ユーザー ID。 |
| JobTitle |string |ユーザーの役職。 |
| Mail |string |ユーザーの電子メール ID。 |
| MailNickname |string |ユーザーのニックネーム。 |
| mobilePhone | string |ユーザーの携帯電話。 |
| OfficeLocation | string |ユーザーの勤務先所在地。|
| PostalCode | string |ユーザーの郵便番号。|
| 姓 |string |ユーザーの姓。 |
| TelephoneNumber |string |ユーザーの電話番号。 |
| UserPrincipalName |string |ユーザー プリンシパル名。 |
| AccountEnabled |boolean |アカウントの有効化されたフラグ。 |
| BusinessPhones | string |ユーザーの会社の電話番号。|

### <a name="searchuser"></a>SearchUser
ユーザーの検索: ユーザー プロファイルの検索結果を取得します。

#### <a name="input-properties"></a>入力プロパティ

| 件名 | データの種類 | 必要な領域 | 内容 |
| --- | --- | --- | --- |
| searchTerm |string |いいえ |検索文字列。 適用対象: 表示名、名、姓、電子メール、メールのニックネーム、およびユーザー プリンシパル名。 |

#### <a name="output-properties"></a>出力プロパティ

| プロパティ名 | 種類​​ | 内容 |
| --- | --- | --- |
| 市区町村 | string |ユーザーの市区町村。 |
| CompanyName | string |ユーザーの会社。 |
| 国 | string |ユーザーの国/地域。 |
| 課 |string |ユーザーの部署。 |
| DisplayName |string |ユーザーの表示名。 |
| GivenName |string |ユーザーの名前。 |
| ID |string |ユーザー ID。 |
| JobTitle |string |ユーザーの役職。 |
| Mail |string |ユーザーの電子メール ID。 |
| MailNickname |string |ユーザーのニックネーム。 |
| mobilePhone | string |ユーザーの携帯電話。 |
| OfficeLocation | string |ユーザーの勤務先所在地。|
| PostalCode | string |ユーザーの郵便番号。|
| 姓 |string |ユーザーの姓。 |
| TelephoneNumber |string |ユーザーの電話番号。 |
| UserPrincipalName |string |ユーザー プリンシパル名。 |
| AccountEnabled |boolean |アカウントの有効化されたフラグ。 |
| BusinessPhones | string |ユーザーの会社の電話番号。|

## <a name="helpful-links"></a>便利なリンク
* [使用可能な接続](../connections-list.md) をすべて参照してください。
* アプリに [接続を追加する](../add-manage-connections.md) 方法についてご確認ください。

