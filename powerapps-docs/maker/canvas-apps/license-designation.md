---
title: アプリのライセンス指定 | Microsoft Docs
description: 選択したアプリのライセンス指定を確認する方法について説明します
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/24/2020
ms.author: alaug
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 495325949776b066ed30d629fb031730e4463179
ms.sourcegitcommit: be9b8c0f5c7c7e9992e93fa0d03e961b4ac7e3ae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2020
ms.locfileid: "3308960"
---
# <a name="how-to-check-license-designation-for-an-app"></a>アプリのライセンス指定の確認方法

2019 年 10 月から、いくつかのコネクタがスタンダードからプレミアムに再分類されました。

[Power Apps ライセンスに関する質問](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#office-365)  再分類されたコネクタの概要を示します。 再分類の前に、これらのコネクタを使用するアプリは、プレミアム ライセンスを持たないユーザーを許可する延長期間が付与され、アプリにアクセスできます。

以下の表では、指定、およびエンドユーザーがアプリにアクセスするために必要なライセンスについて説明します。

| **指定** | **定義**
|-|-|
| 標準 | 標準コネクタのみを使用するアプリです。 エンド ユーザーは、アプリにアクセスするためにアプリ プランごと、またはユーザー プランごとに Office 365 プランの Power Apps が必要です。
| 拡張 | 2019 年 10 月 1 日にプレミアムに昇格し、コネクタの使用が許可されたアプリです。 エンドユーザーは、アプリ プランごとまたはユーザー プランごとに Office 365 プランの Power Apps が必要です。 [Power Apps ライセンスに関する質問](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#office-365)  では、2019 年 10 月 1 日にプレミアムに昇格したコネクタについて説明します。
| プレミアム | 少なくとも 1 つのプレミアム コネクタ、カスタム コネクタ、またはオンプレミス ゲートウェイを使用するアプリです。 エンド ユーザーは、アプリ プランごと、またはユーザー プランごとにアクセスする必要があります。

## <a name="check-app-license-designation-from-app-settings"></a>アプリの設定からアプリ ライセンスの指定を確認する

1. [Power Apps](https://make.powerapps.com) にサインインします。

1. 左側で**アプリ**を選択します。

1. アプリの一覧からアプリを選択します。 上から**設定**オプションを使うか、またはドロップダウン メニューから**その他のコマンド** (**...**) および**設定**を使用します:

    ![オプションの設定](media/license-designation/app-settings.png)

1. **設定**を選択し、ライセンス指定情報を確認します:

    ![設定からライセンスの指定](media/license-designation/settings-license-designation.png)

## <a name="check-app-license-designation-from-app-details"></a>アプリ詳細からアプリ ライセンスの指定を確認する

1. [Power Apps](https://make.powerapps.com) にサインインします。

1. 左側で**アプリ**を選択します。

1. アプリの一覧からアプリを選択します。 上から**詳細**オプションを使うか、またはドロップダウン メニューから**その他のコマンド** (**...**) および**詳細**を使用します:

    ![アプリの詳細](media/license-designation/app-details.png)

1. **詳細**を選択:

    ![アプリ指定の詳細](media/license-designation/app-details-page.png)

## <a name="pass-assignment"></a>パスの割り当て

パスの割り当てについては、[アプリ プランごとの Power Apps](https://docs.microsoft.com/power-platform/admin/about-powerapps-perapp#step-three-set-up-apps-to-use-per-app-plans) を参照してください。

## <a name="next-steps"></a>次の手順

- [Power Apps ライセンスに関する質問](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq)

### <a name="see-also"></a>関連項目

- [アプリの編集](edit-app.md)
- [アプリの削除](delete-app.md)
