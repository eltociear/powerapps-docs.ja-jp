---
title: IP アドレスを使用したポータルへのアクセスに対する制限 | MicrosoftDocs
description: IP アドレスによるポータル アクセスを制限するための手順。
author: neerajnandwana-msft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: nenandw
ms.reviewer: tapanm
ms.openlocfilehash: 1d97ac775cd9777b7c4258832a5f0db33c089140
ms.sourcegitcommit: 2fd873a1ea17f419f6194714efffa47a9bd00c2e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "3507947"
---
# <a name="restrict-portal-access-by-ip-address"></a>IP アドレスによるポータル アクセスの制限

このポータルは、プロビジョニングされどのコンピュータからでも誰でもアクセスが可能な場合に、公開されます。 IP アドレスの一覧から、ポータルへのアクセスを制限できます。 たとえば、政府機関ではコンテンツを組織内ネットワークのみに表示する必要がある場合があります。 商用組織の場合、データのリークを避けるため、開発中ポータルではなく公開済みポータルのみを表示する場合があります。

ポータルへの要求がユーザーから発生した場合、IP アドレスは許可リストに対して評価されます。 IP アドレスが一覧にない場合、ポータルには HTTP 403 状態コードの Web ページが表示されます。

IP アドレスを追加、または削除するには、次のロールのいずれかを割り当てる必要があります。
- Office 365 グローバル管理者 
-  サービス管理者。 詳細: [サービス管理者ロールを使用してテナントを管理する](https://technet.microsoft.com/library/mt793847.aspx)  
- ポータル用に選択された Common Data Service 環境のシステム管理者

## <a name="add-an-ip-address"></a>IP アドレスを追加

IP アドレスからポータルにアクセスまたは一連のIPアドレスを使用するには、IP アドレスを一覧に追加します。 これにより、追加された IP アドレスの一覧からのみポータルにアクセスできるようになります。 IP アドレスを追加しない場合は、すべての IP アドレスからポータルにアクセスできます。

IP アドレスを制限リストに追加すると、指定した IP アドレスにのみがポータルにアクセス可能になります。 他の IP アドレスからポータルにアクセスしようとすると、アクセスは拒否され、HTTP 403 ステータス コードを含む Web ページが表示されます。 この Web ページのコンテンツは静的で、変更することはできません。

> [!div class=mx-imgBorder]
> ![HTML 403 エラー](../media/ip-address-page-error.png "HTML 403 エラー")  

> [!NOTE]
> ポータルからアクセスできるパブリック IP アドレスを指定する必要があります。 プライベート IP アドレスは、ポータルからはアクセスできません。

1.  [Power Apps ポータル管理センター](admin-overview.md) を開きます。

2.  **IP アドレス制限の設定**に移動します。 IP アドレスおよびその種類の一覧が表示されます。

    > [!div class=mx-imgBorder]
    > ![IP アドレス制限の設定](../media/set-up-ip-address-restrict.png "IP アドレス制限の設定")

3.  セットアップ IP アドレスの制限のページで、**新規追加**を選択します。

4.  IP アドレスを追加するウィンドウで、次の値を入力します。

    - **IP アドレスの種類を選択**: IP アドレスは IPv4 または IPv6 を選択します。

    - **CIDR 表記で IP アドレスを指定します**: CIDR 表記で IP アドレスを指定します。 詳細: [クラスレス ドメイン間ルーティング](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing)

      > [!div class=mx-imgBorder]
      > ![IP アドレスを追加](../media/add-ip-address.png "IP アドレスを追加")    

5.  **構成**を選択します。

## <a name="remove-an-ip-address"></a>IP アドレスを削除

以前に許可した IP アドレスからポータルへのアクセス権を削除するには、リストの IP アドレスを削除します。 どの IP アドレスも削除しない場合、ポータルはすべての IP アドレスからアクセスできます。

1.  [Power Apps ポータル管理センター](admin-overview.md) を開きます。

2.  **IP アドレス制限の設定**に移動します。 IP アドレスおよびその種類の一覧が表示されます。

    > [!div class=mx-imgBorder]
    > ![IP アドレス制限の設定](../media/set-up-ip-address-restrict.png "IP アドレス制限の設定")

3.  削除するには、IP アドレスの横の **IP アドレスを削除(x)** を選択します。

4.  確認メッセージの**削除**を選択します。

