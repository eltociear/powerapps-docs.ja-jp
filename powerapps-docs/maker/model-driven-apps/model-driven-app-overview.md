---
title: Power Apps を使用したモデル駆動型アプリの構築の概要 | Microsoft Docs
description: Power Apps モデル駆動型アプリで使用するエンティティを作成および構成するための詳細な手順。
author: Mattp123
ms.service: powerapps
ms.topic: conceptual
ms.component: model
ms.date: 06/16/2020
ms.author: matp
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 79eb00aa79bb2c172dc3bc17cbf17d05713b701c
ms.sourcegitcommit: 213c46f7055eb71b9064b0645d8d17cf8eaad179
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/16/2020
ms.locfileid: "3456193"
---
# <a name="what-are-model-driven-apps-in-power-apps"></a>Power Apps におけるモデル駆動型アプリとは?

モデル駆動型アプリ設計は、アプリ開発においてコンポーネントに焦点を絞ったアプローチです。 モデル駆動型アプリの設計は、コードを必要とせず、作成するアプリはシンプルにもきわめて複雑にもすることができます。  デザイナーがアプリ レイアウトを完全に制御するキャンバス アプリ開発とは違い、モデル駆動型アプリではレイアウトの多くが自動的に決まり、アプリに追加するコンポーネントによって大部分が指定されます。

![サンプル モデル駆動型アプリ](media/model-driven-app-overview/model-app-sample.png)

モデル駆動型アプリの設計には、以下のメリットがあります。
- リッチ コンポーネントに焦点を当てたコードのない環境 
- デスクトップからモバイルまでさまざまなデバイスを介して、類似する UI を使用して複雑で応答性の高いアプリを作成する
- 豊富な設計機能 
- アプリはソリューションとして配布可能
 
## <a name="the-approach-to-model-driven-app-making"></a>モデル駆動型アプリの作成手法
基本レベルで、モデル駆動型アプリの作成は 3 つのフォーカス分野で構成されています。

- ビジネス データのモデル化 
- ビジネス プロセスの定義 
- アプリの作成

### <a name="modeling-business-data"></a>ビジネス データのモデル化
ビジネス データをモデル化するには、アプリが必要とするデータとそのデータが他のデータにどのように関連するかを決定します。 モデル駆動型設計では、メタデータ駆動のアーキテクチャを使用します。それにより、デザイナーはコードを記述せずアプリケーションをカスタマイズできます。 メタデータは "データについてのデータ" を意味しており、システムに格納されているデータの構造を定義します。 [チュートリアル: Power Apps でのコンポーネントがあるユーザー定義エンティティの作成](../common-data-service/create-custom-entity.md)

### <a name="defining-business-processes"></a>ビジネス プロセスの定義
一貫したビジネス プロセスを定義して適用することは、モデル駆動型アプリ設計の主要な側面です。 一貫性のあるプロセスにより、アプリ ユーザーが、一連の手動の手順を忘れずに実行することに集中するのではなく、自分たちの仕事に確実に集中することができます。 プロセスは単純または複雑な場合があり、徐々に変化することがよくあります。 プロセスを作成するには、PowerApps.com のモデル駆動型領域から ![設定](media/powerapps-gear.png) > **高度なカスタマイズ** > **ソリューション エクスプローラーを開く** を選択します。 次に、ソリューション エクスプローラーの左側のナビゲーション ウィンドウで、**プロセス**を選び、**新規** を選択します。 詳細情報: [業務プロセス フローの概要](/flow/business-process-flows-overview)および [Common Data Service を使用したビジネス ロジックの適用](../common-data-service/cds-processes.md)。 

### <a name="composing-the-model-driven-app"></a>モデル駆動型アプリの作成
データをモデル化し、プロセスを定義したら、アプリ デザイナーを使用して必要なコンポーネントを選択および構成することでアプリを構築します。

![アプリ デザイナー](media/model-driven-app-overview/app-designer.png)

Power Apps が初めてで、Power Apps を使用してアイデアを完全に機能するソリューションに変換する方法を学びたい場合は、[Power Apps プロジェクトの計画](/powerapps/guidance/planning/introduction) から始めてください。

## <a name="next-steps"></a>次の手順

[モデル駆動型アプリを作成する](build-first-model-driven-app.md)

[モデル駆動型アプリのコンポーネントについて](model-driven-app-components.md)

