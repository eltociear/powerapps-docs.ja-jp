---
title: Power Platform 管理センターの Power Apps ポータルの設定 | MicrosoftDocs
description: Power Platform 管理センターの Power Apps ポータル設定についての情報。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 05/29/2020
ms.author: nenandw
ms.reviewer: tapanm
ms.openlocfilehash: 8f6d5ac03736612e1b328d087885fa085ebb421b
ms.sourcegitcommit: e2c92335fe6162c4576f0b86238ccbe4a7f74732
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2020
ms.locfileid: "3417833"
---
# <a name="manage-portals-from-the-power-platform-admin-center"></a>Power Platform 管理センターからポータルを管理する

Power Platform 管理センターでポータルを管理できるようになりました。 Power Platform 管理センターは、容量ベースのポータルとアドオン ポータルの両方を管理するのに役立ちます。 また、トライアル ポータルの有効期限が切れるまでの残り日数などの情報も確認できます。 ポータル ライセンスに関する詳細情報は、[ライセンスに関するよくある質問](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#portals) と [ポータルの違い](https://docs.microsoft.com/powerapps/maker/portals/faq#what-is-the-difference-between-power-apps-portals-dynamics-365-portals-and-add-on-portals) を参照してください。

Power Platform 管理センターでポータルを次の 2 つの方法で管理できます: 現在のテナントのすべてのポータルは、**リソース** > **ポータル** から管理でき、**環境** から特定の環境のポータルを管理できます。

## <a name="manage-all-portals-for-a-tenant"></a>テナントのすべてのポータルを管理する

1.  [Power Platform 管理センター](https://admin.powerplatform.microsoft.com/) にサインインします。

1. 左側のペインで、 **リソース**、次に **ポータル** を選択します。

    ![のポータルオプションPower Platform管理センター](media/power-platform-admin-center/manage-portals-all-environments.png "Power Platform 管理センターのポータル オプション")

1. ポータルを選択します。

1. ポータルを管理するには、**その他のポータル アクション** (**...**)、次に **管理する** を選択します。 または、ポータルを選択してから、ページの上部で **管理する** を選択します。

    ![Power Platform 管理センターからポータルを管理する](media/power-platform-admin-center/portals-manage-ppac.png "Power Platform 管理センターからポータルを管理する")

ポータルの詳細を構成するには、[ポータルの詳細](https://docs.microsoft.com/powerapps/maker/portals/admin/portal-details) を参照してください。

## <a name="manage-all-portals-for-an-environment"></a>環境のすべてのポータルを管理する

1.  [Power Platform 管理センター](https://admin.powerplatform.microsoft.com/) にサインインします。

1. 左ペインで、 **環境** を選択します。

    ![環境の一覧](media/power-platform-admin-center/environments-list.png "環境の一覧")

1. ハイパーリンクされた環境名にカーソルを合わせて選択し、環境の詳細を開きます。

    ![環境を選択する](media/power-platform-admin-center/select-environment.png "環境を選択する")

1. 画面右側の **資源** で、**ポータル** を選択します。

    ![環境の詳細](media/power-platform-admin-center/environment-details.png "環境の詳細")

   選択された環境内で自分がインストールしたポータルのリストが表示されます。

    ![環境に固有のポータル](media/power-platform-admin-center/environments-portals.png "環境に固有のポータル")

1. ポータルを管理するには、**その他のポータル アクション** (**...**)、次に **管理する** を選択します。 または、ポータルを選択してから、ページの上部から **管理する** を選択します。

    ![環境に固有のポータルを管理する](media/power-platform-admin-center/manage-environments-portal.png "環境に固有のポータルを管理する")

ポータルの詳細を構成するには、[ポータルの詳細](portal-details.md) を参照してください。

## <a name="manage-the-portal-add-on"></a>ポータル アドオンを管理する

Power Platform 管理センターを使用して、この記事で説明するように、ポータルを管理することは、次の図に示す以前の機能を置き換えます。

![ポータル アドオンを管理するための古い機能](media/power-platform-admin-center/old-admin-center.png "ポータル アドオンを管理するための古い機能")

### <a name="portal-types"></a>ポータルの種類

次の表は、Power Platform管理センターにリストされているさまざまなタイプのポータルについて説明します。

| 種類​​                |内容                                                           |
|---------------------|----------------------------------------------------------------------|
| 実稼働          | 容量ベースのライセンスに基づいた運用ポータル。               |
| 試用版 (*n* 日)    | 容量ベースのライセンスに基づくトライアルポータル。_ん_停止までの残り日数。 |
| 実稼働 (アドオン) | アドオン ライセンスに基づく運用ポータル。     |
| 試用版 (アドオン)      | アドオン ライセンスに基づく試用版ポータル。          |

### <a name="portal-status"></a>ポータルの状態

ポータルには次のステータスがあります: *構成済み*、*一時停止*、または *未構成*。 次の表で各場外を説明します。

| ステータス         |  内容    |
|----------------|-----------------|
| 構成済み     | このポータルは環境に対して既に構成されています。     |
| 中止      | 試用期間が終了したため、このポータルは停止されました。 運用ポータルに変換しない限り、7 日後に削除されます。 |
| 未構成 | このポータルは環境に対して構成の準備が完了しています。   |

> [!NOTE]
> ポータルのアドオンの状態が *未構成* の場合、[新規ポータルの作成](https://docs.microsoft.com/powerapps/maker/portals/provision-portal-add-on) ができます。 ポータルがプロビジョニングされた後、状態が *構成済み* に変わります。

## <a name="update-the-power-apps-portal-solution"></a>Power Apps ポータル ソリューションの更新

Power Platform 管理センターを使用して、Power Apps ポータル ソリューションを更新できます。

1. **管理** を選択して、この記事の前半で説明した方法のいずれかを使用してポータルを管理します。

1. 左ペインで、**Dynamics 365 インスタンスを管理する** を選択します。

1. **Dynamics 365 インスタンスの更新** を選択します。

    ![Dynamics 365 インスタンスの更新](media/power-platform-admin-center/update-dynamics365-instance.png "Dynamics 365 インスタンスの更新")

1. 既存のインスタンスとポータルを選択します。

    ![Dynamics 365 インスタンスの選択](media/power-platform-admin-center/select-dynamics365-instance.png "Dynamics 365 インスタンスの選択")

1. **OK** を選択します。

1. 確認するには **送信** を選択します。

    ![Dynamics 365 ソリューションの更新を送信する](media/power-platform-admin-center/submit-selection.png "Dynamics 365 ソリューションの更新を送信する")

    更新リクエストが進行中であることの確認が表示されます。

    ![更新の要求が送信されました...](media/power-platform-admin-center/update-request-submitted.png "更新の要求が送信されました")

**送信** を選択した後、更新にはしばらく時間がかかる場合があります。 詳細: [ポータルのアップグレード](upgrade-portal.md)

## <a name="next-steps"></a>次の手順

[ポータルの詳細の構成](portal-details.md)

### <a name="see-also"></a>関連項目

[Dynamics 365 アプリの管理](https://docs.microsoft.com/power-platform/admin/manage-apps)  
[ポータルのアップグレード](upgrade-portal.md)
