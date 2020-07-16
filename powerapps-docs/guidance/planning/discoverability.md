---
title: Power Appsプロジェクトをデプロイする - 発見可能性 | Microsoft Docs
description: アプリを本番環境で使用できるようにすることで、ユーザーが利用できます。 続いて、アプリを見つけやすくするためのさまざまな方法を探ります。
author: taiki-yoshida
ms.service: powerapps
ms.topic: conceptual
ms.custom: guidance
ms.date: 06/16/2020
ms.author: tayoshi
ms.reviewer: kathyos
ms.openlocfilehash: e18f6b33304932e958041063358953995fb40fb6
ms.sourcegitcommit: 213c46f7055eb71b9064b0645d8d17cf8eaad179
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/16/2020
ms.locfileid: "3461586"
---
# <a name="making-apps-discoverable"></a>アプリを見つけやすくする

おめでとうございます! 最初のアプリを作成し、テストも完了し、リリースの準備が整いました

ただし、アプリの最初のバージョンを作成するだけでは、Power Apps に関する道のりはまだ終わっていません。
アプリを本番環境で使用できるようにすることで、ユーザーが利用できます。

アプリを起動したら、アプリが適切に機能し、目的を満たしていることを確認する必要があります。 多くの場合は、新機能や修正のリクエストを受けるか、変更されたビジネス プロセスに対応する必要があります。

このセクションでは、以下の方法について説明します。

- [アプリをデプロイする](#publishing-and-sharing-the-app)、そして[ユーザーが見つけやすくする](#featured-apps)。

- [フィードバックと使用法の情報](feedback-telemetry.md)にアクセスすることで、アプリの改良に役立ちます。

## <a name="publishing-and-sharing-the-app"></a>アプリの公開と共有

アプリを使用する準備ができたらすぐに、アプリを公開して共有する必要があります。

アプリの種類に合わせて指示に従ってください。

:::row:::
    :::column:::
        **モデル駆動型アプリ**

        -   [モデル駆動型アプリを公開する](../../maker/model-driven-apps/validate-app.md)

        -   [モデル駆動型アプリを共有する](../../maker/model-driven-apps/share-model-driven-app.md)


    :::column-end:::
    :::column:::
        **キャンバス アプリ**

        -   [キャンバス アプリを共有する](../../maker/canvas-apps/save-publish-app.md)

        -   [キャンバス アプリを共有する](../../maker/canvas-apps/share-app.md)

    :::column-end:::
:::row-end:::

アプリを公開して共有した後は、他のユーザーがアプリを使い始めることができるように、アプリを見つけられるようになっていることを確認することが重要です。 以下のセクションで説明するように、アプリを検出可能にする方法はいくつかあります。

## <a name="featured-apps"></a>おすすめアプリ

![注目のアプリ リスト](media/featured-apps.png "注目のアプリ リスト")

[注目のアプリ](https://powerapps.microsoft.com/blog/powerapps-discoverability-in-the-enterprise/)リストは、会社全体で使用することを目的としたアプリの紹介に適しています。&mdash;たとえば、従業員の検索や会社のニュースなどです。

Power Apps で PowerShell スクリプトを使用して注目のアプリを設定するには、[Power Apps で PowerShell を使用する](https://docs.microsoft.com/power-platform/admin/powerapps-powershell#power-apps-cmdlets-for-administrators-preview)を参照してください。

## <a name="qr-codes"></a>QR コード

QR コードは、モバイル デバイスにアプリをインストールする最速の方法です。 iOS デバイスでは、カメラを使用すると、QR コードを認識できます。 Android ユーザーは、カメラを使用して QR コードを認識する間、ホームボタンを押したままにしてください。

Bing には、URL に貼り付けできる QR コード ジェネレーターが実装されており、QR コードの画像がすぐに生成されます。 アプリを宣伝するには、QR コードの画像を右クリックしてコピーし、コミュニケーションに貼り付けます。

![Bing QR コード ジェネレーター](media/qr-codes.png "Bing QR コード ジェネレーター")

## <a name="deep-linking"></a>ディープ リンク

アプリ間でのアプリディープ リンクは、自分の仕事に関連するアプリをユーザーに知らせることができ、大変有用です。 ユーザーはアプリを起動して、関連するアプリに移動することができます。最初のアプリを終了してプレーヤーに戻って、別のアプリを検索する必要はありません。 ディープ リンクはより高速で、より没入型のエクスペリエンスを実現します。

ディープ リンクには、Power Apps の [起動およびパラメーター機能](../../maker/canvas-apps/functions/function-param.md)を使用できます。
詳細情報 :  [PowerAppsのディープ リンク](https://powerapps.microsoft.com/blog/powerapps-deep-linking/)

## <a name="microsoft-teams"></a>Microsoft Teams

Teams 内のタブの1つとしてアプリを埋め込むことができます。
Teams と既存のプロセスを行き来しなければならないシナリオでこのアプリを使用する場合に、ユーザーの満足度を高めることができます。

![Teams に埋め込まれたアプリのスクリーンショット](media/add-app-as-tab.png "Teams に埋め込まれたアプリのスクリーンショット")

詳細情報 : [Teams にアプリを埋め込む](../../maker/canvas-apps/embed-teams-app.md)

## <a name="tie-ins-to-existing-web-apps-and-portals"></a>既存の Web アプリおよびポータルへの関連付け

既存の Web サイトやポータルからアプリへのリンクを埋め込むことも、アプリを公開する良い方法です。

Param() 関数を使用して Web サイトやポータルからの情報を渡すことで、ユーザーがどの Web サイトやページから来たのか、データを入力する必要性を最小限に抑えることができます。 この関数を使用して、一部のデータを入力したり、そこから自動的にアクションを実行することができます。

## <a name="sharepoint-embedding"></a>SharePoint 埋め込み

アプリは、最新の  SharePoint  ページに直接埋め込むこともできます。 これはアプリの発見に役立つだけでなく、コンテンツとアプリを互いに独立した状態で簡単に変更することができます。

詳細情報 : [Power Apps Web パーツを使用する](https://support.microsoft.com/en-us/office/use-the-power-apps-web-part-6285f05e-e441-408a-99d7-aa688195cd1c)<!--note from editor: This link doesn't work if you remove "en-us" (which we usually do). Just FYI.-->

## <a name="microsoft-search-in-bing-integration"></a>Bing 統合における Microsoft Search

Bing の Microsoft Search を使用すると、企業のブックマークを作成し、検索結果に直接アプリを埋め込むことができます。

管理者は、Bing 検索エンジンを構成して、サイン インした際に特定のグループ、&mdash;あるいはロケールの従業員が特定のデバイスを使用して特定の用語を検索すると、&mdash;検索結果の上部のペインにアプリが表示されます。

> [!div class="nextstepaction"]
> [次の手順 : フィードバックとテレメトリを収集する](feedback-telemetry.md)
