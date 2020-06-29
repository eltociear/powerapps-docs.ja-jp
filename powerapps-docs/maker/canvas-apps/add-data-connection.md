---
title: キャンバス アプリへのデータ接続の追加 | Microsoft Docs
description: 既存のキャンバス アプリや空のアプリにデータ接続を追加する
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/06/2018
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d1397f9fd2859611a3cd54023210a27cd5977834
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/13/2020
ms.locfileid: "3308592"
---
# <a name="add-a-data-connection-to-a-canvas-app-in-power-apps"></a>Power Apps でキャンバス アプリにデータ接続を追加する

Power Apps で、既存のキャンバス アプリまたは一から作成するアプリにデータ接続を追加します。 アプリは、SharePoint、Common Data Service、Salesforce、OneDrive、または[その他の多くのデータ ソース](connections-list.md) に接続できます。

この記事の後に来る[次のステップ](#next-steps) は、以下に示す例のように、接続したデータ ソースのデータをアプリで表示および管理することです。

* OneDrive に接続し、アプリの Excel ワークブックのデータを管理する。
* Twilio に接続し、アプリから SMS メッセージを送信する。
* Common Data Service に接続して、アプリからエンティティを更新する。
* SQL Server に接続し、アプリからテーブルを更新する。

## <a name="prerequisites"></a>前提条件

Power Apps に[サインアップ](../signup-for-powerapps.md) し、登録に使用した同じ資格情報を使用して[サインイン](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) します。

## <a name="open-a-blank-app"></a>空のアプリを開く

1. **ホーム** タブで、**キャンバス アプリを一から作成**を選択します。

1. アプリに名前を指定してから、**作成**を選択します。

1. **Power Apps Studio へようこそ**のダイアログ ボックスが表示されたら、**スキップ**を選択します。

## <a name="add-data-source"></a>データ ソースの追加

1. 中央のウィンドウで **データに接続** を選択して**データ** ウィンドウを開きます。

    これが既存のアプリであり、スクリーンにすでにコントロールが含まれている場合は、**表示** > **データ ソース**を選択して、同じウィンドウを開きます。

1. **データソースの追加**を選択します。

1. 使用する接続が接続の一覧に含まれている場合は、その接続を選択してアプリに追加します。 それ以外の場合、次のステップに進んでください。

    ![既存の接続を選択する](./media/add-data-connection/choose-existing-connection.png)

1. **新しい接続**を選択して、接続の一覧を表示します。

    ![接続の追加](./media/add-data-connection/add-connection.png)

1. 検索バーに目的の接続の最初の数文字を入力するか貼り付け、表示されたら接続を選択します。

    ![接続の検索](./media/add-data-connection/search-connections.png)

1. **作成**を選択して、接続の作成とアプリへの追加の両方を行います。

    **Office 365 Outlook** などのコネクタでは、追加の手順を実行しなくても、すぐにデータを表示できます。 他のコネクタでは、資格情報の入力、特定のデータ セットの指定、またはその他の手順が要求されます。 たとえば、[SharePoint](connections/connection-sharepoint-online.md) および [SQL Server](connections/connection-azure-sqldatabase.md) では、使用する前に追加情報の入力を求められます。 [Common Data Service](connections/connection-common-data-service.md) を使用すると、エンティティを選択する前に環境を変更できます。

## <a name="identify-or-change-a-data-source"></a>データ ソースの特定または変更
アプリを更新する際、ギャラリー、フォーム、または別のコントロールに表示されるデータ ソースを特定または変更する必要がある場合があります。 たとえば、他のユーザーが作成したアプリや、以前作成したアプリを更新するときなどに、データ ソースを特定する必要があります。

1. データ ソースを特定または変更するコントロール (ギャラリーなど) を選択します。

    右側のウィンドウの**プロパティ** タブにデータ ソース名が表示されます。

    ![接続の特定](./media/add-data-connection/identify-connection.png)

1. データ ソースの詳細情報を表示したり、データ ソースを変更したりするには、名前の横にある下矢印を選択します。

    現在のデータ ソースに関する詳細情報が表示され、別のソースを選択または作成できます。

    ![接続の変更](./media/add-data-connection/change-connection.png)

## <a name="next-steps"></a>次の手順

* Excel、SharePoint、Common Data Service、SQL Server などのソースにあるデータを表示および更新するには、[ギャラリーを追加](add-gallery.md) して、[フォームを追加](add-form.md) します。
* [Office 365 Outlook](connections/connection-office365-outlook.md)、[Twitter](connections/connection-twitter.md)、[Microsoft Translator](connections/connection-microsoft-translator.md) などのソースの場合は、各コネクタに用意された機能を使用して表示や更新を行います。
