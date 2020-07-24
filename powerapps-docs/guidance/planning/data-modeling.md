---
title: データ構造を設計する | Microsoft Docs
description: アプリでデータを保存、または表示する場合は、設計で重要となる部分はデータ構造です。 データ モデリングの重要な考慮事項について説明します。
author: taiki-yoshida
ms.service: powerapps
ms.topic: conceptual
ms.custom: guidance
ms.date: 06/16/2020
ms.author: tayoshi
ms.reviewer: kathyos
ms.openlocfilehash: fbf2a7fd209ecfc64fad85fe9fb3bd0d328533be
ms.sourcegitcommit: 213c46f7055eb71b9064b0645d8d17cf8eaad179
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/16/2020
ms.locfileid: "3461589"
---
# <a name="data-modeling-designing-your-data-structure"></a>データ モデリング : データ構造を設計する

アプリでデータを保存、または表示する場合は、設計で重要となる部分はデータ構造です。 特定のアプリや画面でデータがどのように使われるかだけでなく、他のユーザーがどのようにデータを使うかを考慮してください。 ペルソナ、タスク、ビジネス プロセス、目標を参考とすることで、格納するデータとその構造の定義付けに役立ちます。

> [!TIP]
> [データベース設計の基本](https://support.office.com/article/Database-design-basics-EB2159CF-1E30-401A-8084-BD4F9C9CA1F5) : これは Access データベース向けに作成されたものではありますが、データ設計の基本に関するこの記事には、データ モデリングの原則についての汎用的な説明がされています。

以下の経費報告書を例に考えてみましょう。

![経費明細書の例](media/expense-report.png "経費明細書の例")

従業員名と部門の詳細を含む経費レポートの主要な部分が表示されます。 主要な部分の下部に、購入した各アイテムの説明が複数行にわたって表示されます。 これらを明細項目と呼びます。 明細項目は、経費報告書の主要部分とは異なる構造を持っています。 すべての経費報告書には、いくつかの明細項目が存在します。

このようなデータをデータベースに格納するには、データベース設計でデータ構造をモデル化する必要があります。

## <a name="one-to-many-1n-data-structure"></a>1対多 (1 : N) のデータ構造

これは、前述の例で説明したデータ構造のタイプです。 経費報告書の主要な部分は、いくつかの明細項目にリンクされています。 (明細項目の観点から関係を確認することもできます : 多くの明細項目から1つの経費報告書へ (N : 1))

## <a name="many-to-many-nn-data-structure"></a>多対多 (N : N) のデータ構造

多対多のデータ構造は特別なタイプです。 これは、複数のレコードをその他レコードの複数のセットに関連付けることができる場合を指します。 分かりやすい例としては、ビジネス パートナーのネットワークがあります。 たとえば、あなたと共同作業を行っている複数のビジネス パートナー (顧客とベンダー) がいると仮定します。このビジネス パートナーもあなたの複数の同僚たちと共同作業をしています。

![回線で接続された複数の人](media/many-to-many.png "回線で接続された複数の人")

## <a name="data-modeling-examples"></a>データ モデリングの例

システムで発生する可能性のあるモデリングにはいくつかのタイプが存在します。 いくつかの例を以下に挙げます。

### <a name="example-1-time-off-approval-request"></a>例 1 : 休暇の承認申請

![休暇の承認申請におけるデータ構造例](media/time-off.png "休暇の承認申請におけるデータ構造の例")

この簡単な例では、2つのデータセットを示されています。 1 つは従業員、もう 1 つは休暇申請です。 各従業員は複数の要求を送信するため、ここでの関係は1対多となります。ここでは、「1」は従業員であり、「多」は申請です。 従業員データと休暇申請データは、従業員番号を共通フィールドとすることで、互いに関連づけられています (別名*キー*)。

### <a name="example-2-purchase-approval"></a>例 2 : 購入の承認

![購入の承認申請におけるデータ構造の例](media/purchase-approval.png "購入の承認申請におけるデータ構造の例")

ここでは、データ構造が非常に洗練されているように見えますが、この記事の冒頭で説明した経費報告書の例と非常によく似ています。 各ベンダーまたはサプライヤーは、複数の注文書に関連付けられています。 各従業員は、複数の発注書を担当しています。 したがって、これらの両方のデータセットは、1 対多のデータ構造を持っています。

従業員が常に同じベンダーやサプライヤーを利用するとは限らないため、ベンダーは複数の従業員が利用しており、各従業員は複数のベンダーと取引をしています。
したがって、従業員とベンダーの関係は多対多となります。

### <a name="example-3-expense-reporting"></a>例3 : 経費明細書

![経費報告のデータ構造の例](media/expense-report-data.png "経費報告のデータ構造の例")

> [!div class="nextstepaction"]
> [次の手順 : 作成するアプリのタイプを決定する](app-type.md)