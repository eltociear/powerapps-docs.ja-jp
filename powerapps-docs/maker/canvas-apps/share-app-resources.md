---
title: キャンバス アプリで使用されているリソースを共有する | Microsoft Docs
description: Power Apps でキャンバス アプリが使用するリソースを共有する方法を理解する
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 02/03/2020
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 77ccf02395c4d697a6d2054dd1a6dedda26d6e6e
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2020
ms.locfileid: "3308086"
---
# <a name="share-canvas-app-resources-in-power-apps"></a>Power Apps でキャンバス アプリのリソースを共有する

[キャンバス アプリを共有](share-app.md) する前に、依存するリソースの種類、たとえば以下のうちの 1 つまたは複数を考慮してください:

* Common Data Service のエンティティ

    このデータへのアクセス権をユーザーに付与する方法については、[エンティティのアクセス許可を管理する](share-app.md#manage-entity-permissions) を参照してください。
    
* データ ソースへの接続
* オンプレミス データ ゲートウェイ
* カスタム コネクタ
* Excel ワークブックまたはその他のサービス
* フロー

これらのリソースの中には、アプリを共有すると自動的に共有されるものがあります。 その他のリソースでは、ユーザーまたはアプリを共有している相手が、アプリが期待どおりに動作するように、追加の手順を実行する必要があります。

組織全体で接続、カスタム コネクタおよびオンプレミス データ ゲートウェイを共有することもできます。

## <a name="connections"></a>接続

一部の接続 (SQL または Windows 認証を備えた SQL Server など) は、アプリを他のユーザーと共有するとき、アプリと[暗黙的に共有](share-app-resources.md#implicit-sharing) を行います。 その他の接続では、ユーザーが独自の接続を作成し、セキュリティ特権を明示的に付与する必要があります (Common Data Service 向けのセキュリティ ロール、ビジネス向け OneDrive、Azure AD 認証による SQL Server など)。

アプリを他のユーザーと共有するとき、接続がアプリの一部として自動的に共有されるかどうかを決定できます; 共有権限を更新できます。 これを行うには、make.powerapps.com に移動して、左のナビゲーションから**データ** -> **接続**を選択します。 そして、必要な接続を選択します。 *その他のコマンド* (...) を選択するときに、**共有**ボタンが上部ナビゲーションに表示されるか、または**共有**オプションが表示される場合、選択した接続は他のユーザーと共有できます。

  ![ビジネス用 OneDrive の共有はない](./media/share-app-resources/shared-connections-odb.png)

  ![SQL Server への SQL 認証接続を共有する](./media/share-app-resources/shared-connections-sqlauth.png)

### <a name="implicit-sharing"></a>暗黙的な共有

共有可能な接続を使用するアプリを共有すると、アプリの接続は**暗黙的に共有**アプリと一緒に実行されます。 たとえば、make.powerapps.com に移動すると、次のメッセージが表示されるので、**アプリ**を選び、接続などを使用するアプリを選択し、*その他のコマンド* (...)、**共有**の順に選びます:

  ![暗黙の許可警告](./media/share-app-resources/share-app-implicit-permission.png)

**確認**を選び、選択したアプリを他のユーザーと共有すると、アプリの接続は暗黙的にアプリと一緒にそれらのユーザーと共有されます。

## <a name="on-premises-data-gateways"></a>オンプレミス データ ゲートウェイ
オンプレミス ソースからのデータを含むアプリを作成して共有する場合は、[オンプレミス データ ゲートウェイ](gateway-management.md) 自体、およびそのゲートウェイへの接続のうち一定の種類が自動的に共有されます。 自動的に共有されていない接続はすべて、(前のセクションに表示されているとおり) 手動で共有でき、またユーザーが独自の接続を作成するようアプリに求めさせることができます。 接続またはゲートウェイが構成されている接続を表示する方法は次の通りです。

1. [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) を開き、左側のナビゲーション バーの**管理**をクリックまたはタップし、**ゲートウェイ**をクリックまたはタップします。
2. ゲートウェイをクリックまたはタップして、**接続**タブをクリックまたはタップします。

> [!NOTE]
> 1 つ以上の接続を手動で共有する場合は、次の状況でもう一度共有する必要があるかもしれません。

* 既に共有しているアプリにオンプレミス データ ゲートウェイを追加します。
* オンプレミス データ ゲートウェイがあるアプリを、共有したグループのセットまたはグループを変更します。

## <a name="custom-connectors"></a>カスタム コネクタ
カスタム コネクタを使用するアプリを共有するときに、アプリは自動的に共有されますが、ユーザーは独自の接続を作成する必要があります。

[powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) で、カスタム コネクタのアクセス許可を表示または更新できます。 左側のナビゲーション バーで、**管理**をクリックまたはタップし、**接続**をクリックまたはタップして、右上隅の**新しい接続**をクリックまたはタップします。 **カスタム**をクリックまたはタップを行い、カスタム コネクタをクリックまたはタップして詳細を表示します。

## <a name="excel-workbooks"></a>Excel ワークブック
共有しているアプリが、(クラウド ストレージ アカウントの Excel ブックなど) すべてのユーザーにアクセスがないデータを使用している場合は、[データを共有](share-app-data.md) します。

## <a name="flows"></a>フロー
フローを含むアプリを共有する場合、アプリを実行しているユーザーは、フローが依存しているすべての接続を確認または更新するように求められます。 さらに、フローを作成したユーザーのみが、パラメーターをカスタマイズすることができます。 たとえば、指定したアドレスにメールを送信するフローを作成できますが、他のユーザーはそのアドレスの変更ができません。

