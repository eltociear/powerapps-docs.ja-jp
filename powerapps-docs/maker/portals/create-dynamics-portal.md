---
title: Dynamics 365のモデル駆動型アプリケーションを含む環境でポータルを作成する | Microsoft Docs
description: Dynamics 365のモデル駆動型アプリケーションを含む環境でポータルを作成する方法を説明します。
author: neerajnandwana-msft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: nenandw
ms.reviewer: tapanm
ms.openlocfilehash: 586dc8b2335b0f1d3913bfecadbebbdad7aaefe4
ms.sourcegitcommit: 2fd873a1ea17f419f6194714efffa47a9bd00c2e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "3506594"
---
# <a name="create-a-portal-in-an-environment-containing-model-driven-apps-in-dynamics-365"></a>Dynamics 365のモデル駆動型アプリケーションを含む環境でポータルを作成する

Dynamics 365 (Dynamics 365 Sales や Dynamics 365 Customer Service など) にモデル駆動型アプリを含む環境を選択した場合、 [ポータルテンプレート](portal-templates.md)に記載されているポータルを作成できます。

1.  [Power Apps](https://make.powerapps.com) にサインインします。

2.  左側のウィンドウの **作成する** を選択し、 **テンプレートを検索する** フィールドに **ポータル** と入力し、すべての Dynamics 365 ポータルのテンプレートを表示します。

    > [!div class=mx-imgBorder]
    > ![Dynamics 365 ポータル テンプレート](media/dynamics-portals.png "Dynamics 365 ポータル テンプレート")  

3.  必要となるポータルのテンプレートを選択します。

4.  ポータルの作成ウィンドウで、ポータルの名称とWebサイトのアドレスを入力し、ドロップダウンリストから言語を選択します。 完了したら、 **作成** を選択します。 作成の手順は [Common Data Service スターター ポータルを作成する](create-portal.md) セクションに記載されている内容と同じです。

> [!NOTE]
> - 古いポータルアドオンを購入し、そのアドオンを使用してポータルをプロビジョニングする場合は、**Dynamics 365管理センター**ページに移動する必要があります。 詳細については次を参照してください: [古いポータル アドオンを使用してポータルをプロビジョニングする](provision-portal-add-on.md)
> - 古いポータル アドオンを使用したポータルをプロビジョニングする場合は、 [make.powerapps.com](https://make.powerapps.com) にてカスタマイズ、管理することができます。
> - [make.powerapps.com](https://make.powerapps.com) からのポータルをプロビジョニングすると、古いポータル アドオンを使用しません。 また、これらのポータルは、 **Dynamics 365管理センター** ページの **アプリケーション** タブ配下には表示されません。
> - Common Data Service スターター ポータルは、 **Dynamics 365管理センター** ページから作成することはできません
> - テナントにおけるポータルの作成を無効にするには、 [テナントでのポータルの作成を無効にする](create-portal.md#disable-portal-creation-in-a-tenant) を参照してください。
> - ポータルを作成すると、いくつかの ソリューション が インストール され、サンプルデータ が インポート されます。

