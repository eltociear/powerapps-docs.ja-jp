---
title: よくあるご質問 | Microsoft Docs
description: PowerApps ポータルに関してよくあるご質問。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 810829b58d666b66bd2cac7235d013a4bfdcd806
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "2759869"
---
# <a name="powerapps-portals-faq"></a>PowerApps ポータルに関するよくあるご質問

必要な情報がすぐに手に入るように、よく寄せられる質問とその簡潔な回答を一覧にまとめました。

## <a name="im-getting-an-error-that-only-one-portal-can-be-created"></a>作成できるポータルは一つのみです、というエラーが表示されます。

現在、一言語あたり、一環境につき各種類で一つのポータルのみ作成できます。 1 つ以上のポータルを作成した場合は、次のエラー メッセージが表示されます:

> [!div class=mx-imgBorder]
> ![ポータル作成の上限に達したエラー](media/portal-max-error.png "ポータル作成の上限に達したエラー")

より多くのポータルを作成するには、エラー メッセージ内の**新しい環境を作成する**リンクを使用して新しい環境を作成する必要があります。 ポータルの作成に関する詳細情報は、[ポータルの作成](create-portal.md)を参照してください。

## <a name="im-getting-an-error-that-i-cant-delete-my-portal"></a>ポータルを削除できないというエラーメッセージが表示されます。

ポータルを削除するために十分な特権がない場合、次のエラーが表示されます:

> [!div class=mx-imgBorder]
> ![ポータルの削除エラー](media/portal-delete-error.png "ポータルの削除エラー")

ポータルの削除と必要な特権の詳細については、[ポータルの削除](manage-existing-portals.md#delete)を参照してください。

## <a name="im-getting-an-error-that-i-cant-create-a-portal"></a>ポータルを作成できないというエラーメッセージが表示されます。

その環境でポータルを作成するための適切な特権を持っていない場合は、次のエラーが表示されます:

> [!div class=mx-imgBorder]
> ![ポータルの作成エラー](media/portal-create-error.png "ポータルの作成エラー")

ポータルの削除と必要な特権の詳細については、[ポータルの削除](create-portal.md)を参照してください。

## <a name="im-getting-the-message-your-data-isnt-quite-ready"></a>「あなたのデーターの準備ができていません」というメッセージが表示されます。

時々、データベース作成に時間がかかることがあり、適切な状態がホーム ページに反映されていない場合もあります。 この場合、次のメッセージが表示されます。

> [!div class=mx-imgBorder]
> ![データが準備できていません](media/data-not-ready.png "データが準備できていません")

データベースの作成プロンプトやデータの準備ができていませんプロンプトが何度も表示される場合は、 **空のポータル** タイルを選択する前に、 PowerApps ホームページを更新してみてください。

## <a name="im-getting-an-error-that-i-dont-have-required-permissions-to-create-azure-active-directory-applications"></a>Azure Active Directory アプリケーションの作成に必要なアクセス許可がありません、というメッセージが表示されます。

ポータルを作成する際、新しいアプリケーションとしてのポータルは、そのテナントに関連付けられた Azure Active Directory に登録されています。 自分の Azure Active Directory テナントでアプリケーションに登録するために適切なアクセス許可を持っていない場合は、次のエラーメッセージが表示されます。

> [!div class=mx-imgBorder]
> ![Azure Active Directory エラー](media/azure-ad-error.png "Azure Active Directory エラー")

Azure Active Directory でアプリケーションの作成および登録するには、**アプリ登録**設定をあなたのテナント用に有効化してもらうように自分のテナント管理者に問い合わせてください。 詳細については、[必要なアクセス許可](https://docs.microsoft.com/azure/active-directory/develop/howto-create-service-principal-portal#required-permissions)をご覧ください。

## <a name="im-getting-an-error-that-portal-creation-is-blocked-in-this-tenant-by-global-administrator"></a>グローバル管理者によって、このテナントでのポータル作成がブロックされている、というエラーが表示されています。

グローバル管理者によってテナントでポータル作成がブロックされている場合は、次のエラーが表示されます。

> [!div class=mx-imgBorder]
> ![ポータル作成ブロックエラー](media/portal-create-blocked-error.png "ポータル作成ブロックエラー")

グローバル管理者に連絡をして、非管理者によるポータル作成を有効化してもらう必要があります。

あなた自身がグローバル管理者の場合は、PowerShell を通じて `disablePortalsCreationByNonAdminUsers` テナントレベルの設定を無効にする必要があります。 PowerShell ウィンドウで次のコマンドを実行します (PowerShellを管理者として実行)。

```
Set-TenantSettings -RequestBody @{ "disablePortalsCreationByNonAdminUsers" = $false }
```

詳細: [テナントでポータル作成を無効化する](create-portal.md#disable-portal-creation-in-a-tenant)

## <a name="im-getting-an-error-that-i-dont-have-appropriate-license-to-access-this-website"></a>この Web サイトにアクセスするための適切なライセンスがありませんというエラーが表示されます。

ポータルを使用して認証済みページにアクセスする組織内ユーザーは、ポータルが接続されている環境にライセンスを割り当てる必要があります。 内部ユーザーのポータルのユーザー権限について詳しくは、 [こちら](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#can-you-clarify-the-use-rights-to-portals-for-internal-users) をご覧ください。 環境にライセンスが割り当てられていない場合、内部ユーザーに次のようなエラーが表示されます:

> [!div class=mx-imgBorder]
> ![ポータル ログイン エラー](media/portal-login-error.png "ポータル ログイン エラー")

