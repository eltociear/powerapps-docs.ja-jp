---
title: 計画 - データに基づく決定 (ビジネスルール) | Microsoftドキュメント
description: Power Apps プロジェクトにおける計画フェーズの一環として、データに基づいてどのような意思決定をしているのか、どのようなビジネスルールに従う必要があるのかを判断します。
author: TGrounds
ms.service: powerapps
ms.topic: conceptual
ms.custom: guidance
ms.date: 06/16/2020
ms.author: thground
ms.reviewer: kathyos
ms.openlocfilehash: 27cf6d0f2c108d15b36222d8a9912b8ec4967a49
ms.sourcegitcommit: 213c46f7055eb71b9064b0645d8d17cf8eaad179
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/16/2020
ms.locfileid: "3461596"
---
# <a name="are-there-decisions-being-made-based-on-the-data-or-business-rules-to-follow"></a>データやビジネス ルールに基づいた決定がなされていますか？

## <a name="does-the-data-determine-the-outcome-of-any-decisions"></a>データが決定の結果を左右しますか？

- このプロセスにおける活動の最後に、何らかの決定がなされていますか？ データに基づいてソリューションが自動的に決定する方法はありますか？

- この決定は誰かに伝えられますか？ それはどのように伝えられますか？

- この決定により、プロセスの次のステップが実行されるかどうかが決まりますか？ それはどのように伝えられますか？

- 「if / then」 ロジックはありますか？
例えば、*もし* 食事代が \$ 75 以上 *の場合*、従業員は食事の領収書を添付する必要があります。かつ、*もし* 合計金額が \$ 500 以上 *の場合*、経費報告書には、さらなる承認段階が必要となります。

## <a name="does-the-decision-require-approvals"></a>この決定には承認が必要ですか？

- プロセスの次のステップが始まる前に承認は必要ですか？ これらの承認はどのように得られますか？ プロセスの次のステップを承認できる特定のユーザー、またはロールはありますか？ このユーザーはアプリにアクセスできますか？それとも別の方法を使用して承認しますか (承諾の依頼をメールで送信するなど)？

- このプロセスの次の段階のユーザーはこの応答についてどのような警告が通知されますか？これによって、プロセス内次のステップを進める (または進めない) ことができますか？ プロセスの次の段階のユーザーに警告する特定の方法はありますか？

- 割り当てられた時間枠で作業項目が処理されなかったために、作業項目がエスカレーションされる際に、ユーザーに通知する方法はありますか？

> [!TIP]
> これらのさまざまな側面を検討する際は、常に承認への応答対応の短縮に有用な最適な方法を探してください。

## <a name="are-escalations-required"></a>エスカレーションは必須ですか？

- このビジネス プロセスにはエスカレーションが必要ですか？

- 特定の条件下で、項目を自動的にエスカレーションする必要がありますか？ このソリューションを完成させなければならない時間枠はありますか？ ソリューションを使用する作業担当者が承認を逃した場合、アクティビティが別の作業担当者に移動するまでどのくらいの時間を要しますか？ または、別の通知を送信しますか？

- ユーザーは問題をエスカレーションする権限を有しますか？

- エスカレーションが必要な場合、どのように表示しますか？ 期限に遅延している作業項目を、上部に表示させますか？ 一部のアクティビティが予定より遅れていることを作業担当者に知らせるために、ソリューションの表示色を変えますか？

- アラートまたは通知を生成する必要がありますか？

## <a name="example-expense-report-approvals"></a>例 : 経費明細書の承認

経費報告のプロセスには承認が必要です。 すべての営業担当者は、マネージャーであるニックの承認を得た経費報告書を提出しなければなりません。 従業員が報告書を提出すると、ニックに通知が送られ、経費報告書を確認して承認する必要があります。

ニックは多忙なマネージャーであるため、彼の承認を5日以上待つ経費報告書についてはエスカレーションを検討すべきです。 この場合、いくつかのエスカレーション方法を考えることができます。

- ニックに別のアラートを送ることができます。&mdash;メールではなく、テキストメッセージの送信を検討します。

- ニックがまだ返事をしない場合は、ニックのマネージャーに報告書を送るか、&mdash;アベイ&mdash;にも報告書を送って確認、承認してもらいます。

> [!div class="nextstepaction"]
> [次のステップ : プロセス内で次のタスクに移る](next-task.md)

> [!div class="nextstepaction"]
> [すべてのタスクを文書化しました](visually-map-process.md)