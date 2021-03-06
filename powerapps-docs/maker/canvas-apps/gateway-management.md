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
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/15/2020
ms.locfileid: "81385214"
---
# <a name="manage-an-on-premises-data-gateway-in-power-apps"></a>Power Apps でのオンプレミスデータゲートウェイの管理

オンプレミスのデータゲートウェイをインストールすると、パワーアプリに組み込まれているキャンバスアプリと、オンプレミスの SQL Server データベースやオンプレミスの SharePoint サイトなど、クラウドにないデータソースとの間でデータをすばやく安全に転送できます。 管理者権限があるすべてのゲートウェイを表示し、それらの権限と接続を管理することができます。

ゲートウェイでは、次の接続を通じてオンプレミスのデータに接続することができます。

* SharePoint
* SQL Server
* Oracle
* Informix
* ファイル システム
* DB2

## <a name="prerequisites"></a>前提条件

* Power Apps の[サインアップ](../signup-for-powerapps.md)に使用したユーザー名とパスワード。
* ゲートウェイでの管理アクセス許可。 これらのアクセス許可は、インストールするゲートウェイごとに既定で付与されます。また、他のゲートウェイの管理者から、そのゲートウェイに対するこのアクセス許可が付与される場合もあります。
* オンプレミス ゲートウェイを使用したオンプレミス データへのアクセスをサポートするライセンス。 詳細については、[料金に関するページ](https://powerapps.microsoft.com/pricing/)の「Connectivity (接続)」セクションを参照してください。
* ゲートウェイとオンプレミス接続は、ユーザーの[既定の環境](working-with-environments.md)でのみ作成および使用できます。

## <a name="install-a-gateway"></a>ゲートウェイのインストール

ゲートウェイをインストールするには、「[オンプレミス データ ゲートウェイをインストールする](/data-integration/gateway/service-gateway-install)」に記載の手順に従います。 _オンプレミス データ ゲートウェイ (個人用モード)_ は Power BI にのみ使用できるため、ゲートウェイを標準モードでインストールします。

## <a name="view-and-manage-gateway-permissions"></a>ゲートウェイ アクセス許可の表示と管理

1. [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) の左側のナビゲーション バーで、 **[ゲートウェイ]** をクリックまたはタップし、ゲートウェイをクリックまたはタップします。

2. **[ユーザー]** をクリックまたはタップしてユーザーまたはグループを指定し、権限レベルを指定してゲートウェイにユーザーを追加します。

   * **使用可能**: アプリとフローに使用する接続をゲートウェイに対して作成できるが、ゲートウェイを共有できないユーザーです。 このアクセス許可は、アプリを実行するが共有しないユーザーに対して使用します。
   * **使用と共有が可能**: ゲートウェイに対してアプリとフローに使用する接続を作成し、アプリを共有するときに自動的にゲートウェイを共有できるユーザーです。 このアクセス許可は、他のユーザーまたは組織とアプリを共有する必要があるユーザーに対して使用します。
   * **管理者**: ユーザーの追加、アクセス許可の設定、使用可能なすべてのユーザー ソースに対する接続の作成、ゲートウェイの削除を含む、ゲートウェイのフル コントロール権限を持つ管理者です。

**[使用可能]** と **[使用と共有が可能]** のアクセス許可レベルについては、ユーザーがゲートウェイを経由して接続できるデータ ソースを選択します。

> [!NOTE]
> を**使用でき**ます。また、**使用できる + 共有**はカスタムコネクタには適用されません。

## <a name="view-and-manage-gateway-connections"></a>ゲートウェイ接続の表示と管理

1. [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) の左側のナビゲーション バーで、 **[ゲートウェイ]** をクリックまたはタップし、ゲートウェイをクリックまたはタップします。

2. **[接続]** をクリックまたはタップし、詳細の表示、設定の編集、または接続の削除を行います。

3. 接続を共有するには、 **[共有]** をクリックまたはタップしてユーザーを追加または削除します。

    > [!NOTE]
   > 共有できる接続の種類は一部 (SQL Server など) に限定されています。 詳しくは、「[Share app resources (アプリ リソースの共有)](share-app-resources.md)」をご覧ください。

接続を管理する方法について詳しくは、「[PowerApps で接続を管理する](add-manage-connections.md)」を参照してください。

## <a name="troubleshooting-and-advanced-configuration"></a>トラブルシューティングと高度な構成

ゲートウェイに関する問題のトラブルシューティングの詳細については、「[オンプレミスデータゲートウェイのトラブルシューティング](/data-integration/gateway/service-gateway-tshoot)」を参照してください。 構成の詳細については、「[オンプレミスデータゲートウェイアプリを使用する](/data-integration/gateway/service-gateway-app)」を参照してください。

## <a name="next-steps"></a>次のステップ:

* [オンプレミスデータゲートウェイをインストール](/data-integration/gateway/service-gateway-install)します。
* [SQL Server](connections/connection-azure-sqldatabase.md) や [SharePoint](connections/connection-sharepoint-online.md) などのオンプレミス データ ソースに接続するアプリを作成する
* オンプレミス データ ソースに接続する[アプリを共有する](share-app.md)。
