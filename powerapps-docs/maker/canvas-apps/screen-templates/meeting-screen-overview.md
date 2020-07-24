---
title: ミーティング - スクリーン テンプレート | Microsoft Docs
description: キャンバス アプリのミーティング スクリーン テンプレートの仕組みを理解し、独自の使用に合わせて画面を拡張する
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/30/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ac6b75d60f41cd68ee1723c913766ea701bc6ca8
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3307166"
---
# <a name="overview-of-the-meeting-screen-template-for-canvas-apps"></a>キャンバス アプリのミーティング スクリーン テンプレートの概要

キャンバス アプリで、ユーザーが Office 365 Outlook アカウントからミーティング要請を作成および送信できるミーティング画面を追加します。 ユーザーは組織内の出席者を検索し、外部の電子メール アドレスを追加することもできます。 テナントに Outlook へ組み込まれたミーティングの部屋がある場合、ユーザーは場所も選択できます。

[メール](email-screen-overview.md)、組織内の[ユーザー](people-screen-overview.md)、およびユーザーの[カレンダー](calendar-screen-overview.md) などの Office 365 とは異なるデータを表示する他のテンプレート ベースのスクリーンを追加することもできます。

この概要では、スクリーンの高レベル機能について説明します。

このスクリーンの既定機能についてさらに詳しく知りたい場合は、[ミーティング スクリーンを参照する](meeting-screen-reference.md) を参照してください。

## <a name="prerequisite"></a>前提条件

[Power Apps でアプリを作成する](../data-platform-create-app-scratch.md) ときに、画面およびその他のコントロールの追加および構成を行う方法に関する知識。

## <a name="default-functionality"></a>既定機能

テンプレートからミーティングのスクリーンを追加するには:

1. Power Apps に[サインインし](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)、アプリを作成するか、または Power Apps Studio で既存のアプリを開きます。

    このトピックでは電話アプリについて説明しますが、同じ概念がタブレット PC アプリにも適用されます。

1. リボンの**ホーム**タブで、**新しいスクリーン** > **ミーティング**を選択します。

  入力すると、ミーティング スクリーンの両方のタブは次のようになります:

  ![ミーティング スクリーン、両方のタブ](media/meeting-screen/meeting-screen-full-both.png)

いくつかの役に立つ注意事項があります。

* ミーティング スクリーンでは、アプリ ユーザーが Outlook でミーティングを作成できます。
  ユーザーは、出席者を検索して追加したり、オプションでミーティングの部屋をミーティングに追加したりできます。
* 組織内のユーザーを検索するには、「出席者」の下のテキスト入力ボックスにユーザーの名前を入力します。
* ユーザーを検索すると、上位 15 件の結果のみが返されます。
* 組織外の出席者の電子メール アドレスを追加するには、完全で有効な電子メール アドレスを入力し、メール アドレスの右側に表示される「+」アイコンを選択します。
* ミーティングを作成するには、少なくとも 1 人を出席者として追加し、件名を入力し、**スケジュール**タブのミーティング時間を選択します。
* ミーティング要請を送信すると、ミーティングのすべての情報が消去されます。
* 送信アイコンの (右上隅)**OnSelect** ステートメントには、次の式が含まれています:
    ```powerapps-dot
    Set( _myCalendarName, 
        LookUp( 'Office365'.CalendarGetTables().value, DisplayName = "Calendar" ).Name 
    );
    ```
* 「カレンダー」は、ほとんどの Office ユーザーのカレンダーの既定表示名ですが、組織によって異なる場合があります。 その場合は、「カレンダー」を組織に適した用語に変更できます。
* 過去のミーティングをスケジュールしようとしたり、20 人を超えるミーティングに追加しようとすると、エラーが発生します。

## <a name="next-steps"></a>次の手順

* [スクリーンの参照ドキュメントを表示します](./meeting-screen-reference.md)。
* [Office 365 Outlook コネクタについての詳細](../connections/connection-office365-outlook.md)。
* [Office 365 ユーザー コネクタについての詳細](../connections/connection-office365-users.md)。
