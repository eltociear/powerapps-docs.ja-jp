---
title: Power Apps vs 従来のアプリ開発のアプローチ | Microsoftドキュメント
description: Power Apps 開発が従来のアプリ開発とどのように比較されているか、2つの重要な領域 (チームメンバーのコラボレーションと開発プロセス) における方法論について説明します
author: taiki-yoshida
ms.service: powerapps
ms.topic: conceptual
ms.custom: guidance
ms.date: 06/16/2020
ms.author: tayoshi
ms.reviewer: kathyos
ms.openlocfilehash: 1b4dc11381b2367b9f78bf22a285a172ca918802
ms.sourcegitcommit: 213c46f7055eb71b9064b0645d8d17cf8eaad179
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/16/2020
ms.locfileid: "3461579"
---
# <a name="differences-between-power-apps-and-traditional-app-development-approaches"></a>Power Apps と従来のアプリ開発におけるアプローチの違い

従来のアプリ開発と比較すると、Power Apps プロジェクトは以下の 2 つの重要な領域で異なります:

- 組織の様々なメンバーがどのように連携してソリューションを作り出すか

- 開発手法

## <a name="differences-in-who-develops-the-app"></a>アプリ開発者の違い

Power Apps は、 「プロ開発者」 と 「一般開発者」 の両方にメリットのあるプラットフォームです。

従来の開発環境では、実際にアプリを作ることができるのはプロの開発者だけでした。 Power Apps では、これまでプロの開発者しか利用できなかった高度な機能を利用して、必要なアプリを構築する権限を誰もが持っています。 Power Apps では、コードを記述しなくても機能が充実したカスタムのビジネス アプリを構築できるため、カスタムのビジネス アプリ構築を "民主化" できます。

![Microsoft Power Platform と Azure のエコシステム](media/ecosystem.png "Microsoft Power Platform と Azure のエコシステム")

## <a name="differences-in-development-methodology"></a>開発方法論の違い

プロセスが設計フェーズからリリースまで下下流に流れる「ウォーターフォール」モデルなどの従来のアプリ開発では、ユーザーが実際に動作するアプリを見るまでに長いリードタイムがあります。 その結果、ユーザーが当初の要件として求めていたものと、アプリ開発者が作成したものとの間にギャップが生じるリスクが高まります。

![ウォーターフォール開発 : 設計、開発、テスト、リリース](media/waterfall.png "ウォーターフォール開発 : 設計、開発、テスト、リリース")

アジャイル開発などのより最近の開発アプローチでも、最初の最小実行可能な製品 (MVP) がユーザーに提供されるまでにかなりの時間がかかる場合があります。

![アジャイル開発 : 設計、数回の試用、最初の MVP リリース](media/agile.png "アジャイル開発 : 設計、数回の試用、最初の MVP リリース")

Power Apps では、すぐに使えるバージョンのアプリを作ることができます。Power Apps は、WYSIWYG (あなたが見るものはあなたが得るものです) の開発エクスペリエンスを提供しています。 ユーザーは開発プロセスの非常に早い段階で実際に機能するアプリを体験し、新たな要件が発生した場合には、新しい機能を次のバージョンに追加できます。

![Power Apps開発 : コードの記述を最小限に抑えた WYSIWYG により、MVP をすぐに開発できます](media/power-apps-development.png "Power Apps 開発 : コードの記述を最小限に抑えた WYSIWYG により、MVP をすぐに開発できます")
