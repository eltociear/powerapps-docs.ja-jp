---
title: Power Apps プロジェクトの計画例 | Microsoft Docs
description: この経費報告の例では、組織内での典型的な紙ベースの経費承認が、複数の部署や従業員にとっていかに非効率であるかを表わしています。
author: TGrounds
ms.service: powerapps
ms.topic: conceptual
ms.custom: guidance
ms.date: 06/16/2020
ms.author: thground
ms.reviewer: kathyos
ms.openlocfilehash: 2f983623bd670fe7c2d519ed9fd0de16bb9552f3
ms.sourcegitcommit: 213c46f7055eb71b9064b0645d8d17cf8eaad179
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/16/2020
ms.locfileid: "3461584"
---
# <a name="example-expense-reporting"></a>例: 経費報告

以下の例では、組織内での典型的な紙ベースの経費承認が、複数の部署や従業員にとっていかに非効率であるかを表わしています。

![さまざまなチーム メンバーが、現在の紙ベースのプロセスの欠点を説明します](media/process-problem.png "さまざまなチーム メンバーが、現在の紙ベースのプロセスの欠点を説明します")

この例からわかるように、すべての人にそれぞれの問題がありますが、ここでの共通の問題は、経費承認プロセスが紙で行われていることです。これは、Lee、Shawna、Rebecca がレポートを作成するときに面倒で大変だということです。 Nick は自分のチームで提出される書類に圧倒されます。 Abhay はその後、財務システムへの投稿に加えて、週次の予算報告書に向けてすべてをエクセルに書き写して入力する必要があります。 Lee、Shawna、Rebecca が費やした金額を Charlotte が知るまでには時間を要します。

紙の帳票を Power Apps の画面で再現でき、承認は Power Automate で設定でき、データ分析は Power BI でできるため、 Microsoft Power Platform にとっては理想的な問題です。 この一連の記事を通して、この例に立ち返ることにします。

チームが解決するビジネス上の問題は以下です。

> 経費報告 : 従業員と経理部門にとって効率的なプロセスを作成し、より迅速な予算追跡を可能にし、監査への露出を減らします。

デジタル化する価値があることは明白です。 簡単な計算として、監査チームは週に約150件の経費報告書を処理し、標準的な従業員コストとして、 \$ 90/時間を適用していことが分かりました。 各レポートのライフ サイクル全体で1時間を節約できれば、少なくとも無駄な時間を省くだけで \$ 500,000 の節約になります。 ライセンス費用やアプリの開発時間と相殺する必要がありますが、CFO は予算の可視性とレポートのコンプライアンスの改善は投資する価値があると言及しています。

計画のプロセス全体を通して Power Apps プロジェクトでは、この例を再び参照します。

> [!div class="nextstepaction"]
> [次の手順 : 現在のビジネス プロセスを理解する](understanding-current-business-process.md)
