---
title: Power Apps ポータルのライフサイクルについて | MicrosoftDocs
description: Power Apps ポータルのライフサイクルと、試用版から運用版への変更に関する情報。
author: neerajnandwana-msft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 06/22/2020
ms.author: nenandw
ms.reviewer: tapanm
ms.openlocfilehash: 635222979ff99df941e447293f2cecdba22eca8d
ms.sourcegitcommit: 2fd873a1ea17f419f6194714efffa47a9bd00c2e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "3507092"
---
# <a name="about-the-portal-lifecycle"></a>ポータルのライフサイクルについて

ポータルは、試用版として常に作成されます。 30 日後に有効期限が切れる試用版は、無料でポータルの機能を試すために役立ちます。 有効期限が切れた後、ポータルは停止されシャットダウンされます。 停止から 7 日後に、試用版ポータルは削除されます。 ポータル ライフサイクル&mdash;間もなく停止、停止、削除、試用版から運用版への変更&mdash;の各段階で、トースト通知と電子メールで通知されます。

管理者の場合は、中断したポータルを運用ポータルへと変換できます。 ポータルを試用版からから運用版に変更する場合、環境が運用環境でもあること確認する必要があります。 試用版環境では、試用版ポータルを運用ポータルに変更することはできません。 試用ポータルを作成した環境を削除すると、ポータルも削除されます。

最初のポータルは、テナントの環境で作成するのは無料です。 1 つ以上のポータルを作成する必要がある場合、テナントに 1 GBの未使用の保存領域が必要です。

## <a name="stages-in-the-portal-lifecycle"></a>ポータル ライフサイクルのステージ

### <a name="trial-portal"></a>試用版ポータル

すべてのポータルは、30 日後に有効期限が切れる試用版ポータルとして開始されます。 必要なライセンスがある場合は、Power Apps ポータル管理センターから運用ポータルに変更できます。 詳細: [ポータルを試用版から運用版に変更する](#convert-a-portal-from-trial-to-production)

試用版ポータルを運用ポータルに変更するには、環境に外部ユーザー用のアドオンまたは内部ユーザー用のライセンスが必要です。 詳細: [Power Apps と Power Automate ライセンスに関する FAQ](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq) と [Power Apps ポータル ライセンス](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#can-you-share-more-details-regarding-the-new-power-apps-portals-licensing)

### <a name="suspended-portal"></a>中断状態のポータル

試用版ポータルの有効期限については、Power Apps ポータル管理センターで継続して通知が表示されます。 試用版ポータルは 30 日で有効期限が切れます。 試用期間内にポータルを運用に変更しないと、ポータルはシャットダウンされ、停止状態になります。

有効期限が切れた後は、ポータルにアクセスできません。 ただし、停止されたポータルは、停止から 7 日以内であれば運用に変更できます。

### <a name="deleted-portal"></a>削除されたポータル

ポータルを 7 日の中断期間内に運用に変換しない場合は、ポータルは削除されます。 ポータル データは環境から削除されませんが、環境でポータルが使用した領域は解放され、新しいポータルを作成できます。

## <a name="convert-a-portal-from-trial-to-production"></a>ポータルを試用版から運用版に変更する

試用版ポータルは、Power Apps ポータル管理センターに表示されている通知から運用ポータルへと変更できます。

> [!NOTE]
> ポータルを試用版から運用版に変更するには、次のロールの 1 つを割り当てる必要があります:
> - グローバル管理者
> - システム管理者

[Power Apps ポータル管理センター](admin-overview.md) を開き、**[ポータルの詳細](portal-details.md)** タブへ移動すると、**種類** フィールドの下に試用版の有効期限について通知が表示されます。

> [!div class=mx-imgBorder]
> ![[ポータルの詳細] タブの試用通知](../media/admin-center-convert-notif.png "[ポータルの詳細] タブの試用通知")

管理センターのその他のページには、ページの上部に通知が表示されます。

> [!div class=mx-imgBorder]
> ![他のページ上の試用通知](../media/admin-center-convert-notif-all.png "他のページ上の試用通知")

ポータルを試用版から運用版に変更するには:

1.  通知で、**変換**を選択します。

2.  **確認** を選択します。

    > [!div class=mx-imgBorder]
    > ![試用版から運用への確認](../media/trial-to-prod-confirm.png "試用版から運用への確認")

## <a name="convert-an-existing-portal-to-a-capacity-based-model"></a>既存のポータルを容量ベースのモデルに変換する

既存のポータル ライセンスを [容量ベースのライセンス モデル](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#can-you-share-more-details-regarding-the-new-power-apps-portals-licensing) に変換できます。 ポータル ライセンスを容量ベースのモデルに変更するには:

1. [ポータルの詳細](portal-details.md) に移動します。
1. **ライセンスの変更** を選択します。

    ![既存のポータルを容量ベースのモデルに変換する](media/portal-lifecycle/convert-to-capacity-based-licensing.gif "既存のポータルを容量ベースのモデルに変換する")

ポータル ライセンスを変更する前に、以下の点に注意してください:

- ライセンスの変更中にポータルが再起動し、数分間使用できなくなります。 ビジネス ユーザーのダウンタイム期間に、これをスケジュールする必要がある場合があります。
- 環境では、ライセンスを変更する前に適切な [ライセンス](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#portals) が利用可能で割り当てられている必要があります。
- ライセンスを変更するには、管理者権限が必要です。
- 既存ライセンスから容量ベース ライセンスに変更できるのは、運用環境のみです。 [試用版環境](https://docs.microsoft.com/power-platform/admin/trial-environments) がある場合は、まず運用環境に変更する必要があります。

## <a name="considerations-for-add-on-portals"></a>アドオン ポータルに関する考慮事項

次のセクションでは、[ポータル アドオン プランを使用してプロビジョニング](../provision-portal-add-on.md) したポータルに適用される条件について説明します。

### <a name="trial-add-on-portal"></a>試用版アドオン ポータル

試用版アドオン ポータルの有効期限は 30 日です。 期限切れのポータルは 7 日間停止されます。 ポータルは、停止期間が終了すると削除されます。 試用版アドオン ポータルは、環境に設定されているか停止されている間も、運用ポータルに変更できます。

### <a name="production-add-on-portal"></a>実稼働アドオン ポータル

運用アドオン ポータルは、購入したライセンス期間の終了時に期限切れになります。 運用アドオン ポータルの停止期間は、購入したライセンス プランによって異なります。 ポータルは、停止期間が終了すると削除されます。 ポータルが構成済みまたは停止状態のときに、運用アドオン ポータルのライセンスを延長できます。 停止している場合は、ライセンス期間の延長後にポータルを構成済みの状態に変更できます。

> [!IMPORTANT]
> ポータルの停止や削除による機能損失を避けるには、有効期限が切れる前に、適切なタイミングでライセンス期間を延長してください。

### <a name="reset-add-on-portal"></a>アドオン ポータルのリセット

[ポータルのリセット](reset-portal.md) の手順に従って、以前に購入したポータル アドオン プランを使用してプロビジョニングされたポータルをリセットします。

### <a name="see-also"></a>関連項目

[Power Apps ポータルに関する FAQ](../faq.md)
