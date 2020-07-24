---
title: キャンバス アプリ用のオンプレミス データ ゲートウェイを管理する | Microsoft Docs
description: オンプレミス データ ゲートウェイとその接続の管理
author: arthiriyer
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/14/2020
ms.author: arthii
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0956668fa3576dca58c728396d0c4c08473df73f
ms.sourcegitcommit: c0508e233a03ac4846c04d5caae79eccca3e2843
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/15/2020
ms.locfileid: "3309259"
---
# <a name="manage-an-on-premises-data-gateway-in-power-apps"></a>Power Apps でオンプレミス データ ゲートウェイを管理する

オンプレミス データ ゲートウェイをインストールして、Power Apps で構築されたキャンバス アプリと、オンプレミス SQL Server データベースやオンプレミス SharePoint サイトなど、クラウドではないデータ ソースの間でデータをすばやく安全に転送します。 管理者権限があるすべてのゲートウェイを表示し、それらのゲートウェイへのアクセス許可と接続を管理することができます。

ゲートウェイを使用すると、次の接続を介して、オンプレミス データに接続できます。

* SharePoint
* SQL Server
* Oracle
* Informix
* Filesystem
* DB2

## <a name="prerequisites"></a>前提条件

* Power Apps の[新規登録](../signup-for-powerapps.md)に使用したユーザー名とパスワード
* ゲートウェイの管理者権限。 (インストールしたゲートウェイごとにこれらのアクセス許可が既定で割り当てられます。また、他のゲートウェイの管理者から、そのゲートウェイへのアクセス許可を付与してもらうこともできます。)
* オンプレミス ゲートウェイを使用してオンプレミス データへのアクセスをサポートするライセンス。 詳細については、「[価格設定のページ](https://powerapps.microsoft.com/pricing/)」の「接続」セクションを参照してください。
* ゲートウェイおよびオンプレミス接続は、ユーザーの[既定の環境](working-with-environments.md)でのみ作成および使用できます。

## <a name="install-a-gateway"></a>ゲートウェイをインストールする

ゲートウェイをインストールするには、「[オンプレミス データ ゲートウェイをインストールする](/data-integration/gateway/service-gateway-install)」の手順に従います。 _オンプレミス データ ゲートウェイ (個人用モード)_ は Power BI にのみ使用できるため、ゲートウェイを標準モードでインストールします。

## <a name="view-and-manage-gateway-permissions"></a>ゲートウェイのアクセス許可を表示および管理する

1. [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) の左側のナビゲーション バーで、**ゲートウェイ**をクリックまたはタップし、ゲートウェイをクリックまたはタップします。

2. **ユーザー**をクリックまたはタップしてユーザーまたはグループを指定し、アクセス許可レベルを指定してゲートウェイにユーザーを追加します。

   * **使用可能**: ゲートウェイで接続を作成してアプリおよびフローを使用するできるが、ゲートウェイを共有することはできないユーザー。 アプリケーションを実行するが共有しないユーザーにこのアクセス許可を使用します。
   * **使用および共有可能**: ゲートウェイで接続を作成してアプリおよびフローを使用することができ、アプリを共有している時にゲートウェイを自動的に共有することができるユーザー。 他のユーザーまたは組織とアプリケーションを共有する必要があるユーザーには、このアクセス許可を使用します。
   * **管理者**: ユーザーの追加、アクセス許可の設定、使用可能なすべてのデータ ソースに対する接続の作成、ゲートウェイの削除を含む、ゲートウェイを完全にコントロールできる管理者。

**使用可能** および **使用および共有可能** アクセス許可レベルでは、ゲートウェイ経由で接続するデータ ソースを選択します。

> [!NOTE]
> **使用可能**および**使用および共有可能**は、のカスタム コネクタには適用できません。

## <a name="view-and-manage-gateway-connections"></a>ゲートウェイ接続を表示および管理する

1. [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) の左側のナビゲーション バーで、**ゲートウェイ**をクリックまたはタップし、ゲートウェイをクリックまたはタップします。

2. **接続**をクリックまたはタップし、詳細の表示、設定の編集、または削除を行う接続をクリックまたはタップします。

3. 接続を共有するには、**共有**をクリックまたはタップしてから、ユーザーを追加または削除します。

    > [!NOTE]
   > SQL Serverなど、一部の種類の接続のみを共有できます。 詳しくは、「[アプリ リソースの共有](share-app-resources.md)」を参照してください。

接続を管理する方法について詳しくは、「[接続を管理する](add-manage-connections.md)」を参照してください。

## <a name="troubleshooting-and-advanced-configuration"></a>トラブルシューティングと詳細な構成と

ゲートウェイの問題のトラブルシューティングの詳細については、「[オンプレミス データ ゲートウェイのトラブルシューティング](/data-integration/gateway/service-gateway-tshoot)」を参照してください。 構成の詳細については、「[オンプレミス データ ゲートウェイ アプリを使用する](/data-integration/gateway/service-gateway-app)」を参照してください。

## <a name="next-steps"></a>次の手順

* [オンプレミス データ ゲートウェイのインストール](/data-integration/gateway/service-gateway-install)。
* [SQL Server](connections/connection-azure-sqldatabase.md) や [SharePoint](connections/connection-sharepoint-online.md) などのオンプレミス データ ソースに接続するアプリを作成します。
* オンプレミス データ ソースに接続する[アプリを共有](share-app.md) します。
