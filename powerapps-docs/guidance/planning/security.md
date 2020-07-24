---
title: 設計 - アプリとデータのセキュリティ保護 | Microsoft Docs
description: この記事では、Power Apps プロジェクトに携わる人向けに、一般的なセキュリティの概念について説明し、セキュリティ レイヤーとその適用方法について説明します。
author: taiki-yoshida
ms.service: powerapps
ms.topic: conceptual
ms.custom: guidance
ms.date: 06/16/2020
ms.author: tayoshi
ms.reviewer: kathyos
ms.openlocfilehash: db76148aabe1b63789136ee48bc90d8dae241851
ms.sourcegitcommit: 213c46f7055eb71b9064b0645d8d17cf8eaad179
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/16/2020
ms.locfileid: "3461590"
---
# <a name="securing-the-app-and-data"></a>アプリとデータのセキュリティ保護

使用するデータ構造を決定したら、次のステップはデータを保護する方法を検討することです。 誰がどのデータにアクセスするかを検討し、計画フェーズでリストしたタスク、ビジネス プロセス、ペルソナを参照する必要があります。 この記事では、慣れていない人のために一般的なセキュリティの概念について説明します。 セキュリティの技術的側面の詳細については、[セキュリティ ロールおよび特権](https://docs.microsoft.com/power-platform/admin/security-roles-privileges) を参照してください。

## <a name="layers-of-security"></a>セキュリティ層

セキュリティを設定する場合、アプリで設定できる 4 つの異なるセキュリティ層があります。

### <a name="app-level-security"></a>アプリ レベルのセキュリティ

アプリ レベルのセキュリティにより、アプリへのアクセスが制限されます。

アプリ レベルのセキュリティでは、データの保存場所は保護されません。 データの保護方法は、データ ソースの機能によって異なります。 アプリを共有するときは、ユーザーが基になるデータにも適切にアクセスできることを確認してください。

### <a name="form-level-security"></a>フォーム レベルのセキュリティ

モデル駆動型アプリの場合、フォーム レベルのセキュリティにより、特定のセキュリティ グループのみに特定のフォームへのアクセスを許可できます。 これは、ユーザーが担当業務ごとにデータを入力または表示する方法を制限する場合に役立ちます。

たとえば、承認プロセス アプリには、従業員が承認申請を作成および送信するための 1 つのフォームと、承認者が送信された内容を確認するための別のフォームがある場合があります。 フォーム レベルのセキュリティは、このシナリオに適しています。
詳細: [モデル駆動型アプリへのアクセスを制御する。](../../maker/model-driven-apps/control-access-forms.md)

### <a name="record-level-security"></a>レコード レベルのセキュリティ

レコード レベルのセキュリティは、特定のレコードへのアクセスを割り当てることができるセキュリティの一種です。 現在、Excel ブックにシートがあるとします。 レコード レベルのセキュリティでは、個々の行ごとにセキュリティを設定できます。

CRUD (作成、読み取り、更新、削除) と呼ばれる 4 つの異なるタイプのアクセスがあり、レコード レベルのセキュリティを設定できます:

- **作成** ユーザーが新しいデータを作成できるようにします (Excel で新しい行を追加するなど)。

- **読み取り** ユーザーがデータを表示できるようにします。

- **更新** ユーザーが既存のデータを変更できるようにします。
    作成とは、*新規* データを追加することであるため、これは作成とは異なります。

- **削除** ユーザーがデータを削除できるようにします (Excel での行の削除など)。

Common Data Service には、追加、追加先、割り当て、共有という 4 つのタイプのアクセスがあります。 詳細: [セキュリティ ロールと特権](https://docs.microsoft.com/power-platform/admin/security-roles-privileges)

### <a name="field-level-security"></a>フィールド レベルのセキュリティ

フィールド レベルのセキュリティは、単一のレコード内のよりきめ細かいセキュリティです。 これは、Excel で単一の列にセキュリティを設定するようなものです。 これは通常、レコード レベルのセキュリティと同様のアクセス レベルがありますが、フィールド レベルです。

### <a name="how-different-levels-of-security-relate-to-each-other"></a>異なるレベルのセキュリティが互いにどのように関連しているか

上記のセキュリティ レベルは層のようなものです。 アプリの設計は、ニーズに合わせてこれらのセキュリティ レベルの 1 つ以上を考慮する必要があります。 次の表は、アプリの動作で各セキュリティ レベルが制御する内容を示しています。

|セキュリティ レベル  |例 |
|---------|---------|
|アプリ レベルのセキュリティ     |    "Sales アプリ" へのアクセス     |
|フォーム レベルのセキュリティ    |      "顧客カード" へのアクセス   |
|レコード レベルのセキュリティ     |     "Contoso Ltd." へのアクセス    |
|フィールド レベルのセキュリティ     |     "売上金額" へのアクセス    |

## <a name="the-five-steps-for-designing-security"></a>セキュリティを設計するための 5 つのステップ

異なるセキュリティ レベルは非常に複雑で圧倒的に見えるかもしれませんが、次の 5 つのステップに分類できます:

**ステップ 1**: 誰があるいはどのグループの人々 (部署、セクション、チームなど) がアプリ自体にアクセスできるかを特定します。 これは、計画フェーズで特定した人々と同じでなければなりません。

**ステップ 2**: ステップ 1 で特定したユーザーを、制限された種類の情報にアクセスする (またはアクセスしない) グループに分けます。

**ステップ 3**: レコードを表示できるユーザーの要件を特定します。

**ステップ 4**: Common Data Service&mdash;以外のデータ ソースまたは Office 365 あるいは Azure Active Directory認証&mdash;を持たないサービスを使用している場合は、これらのシステムへのアクセスを許可する方法を検討する必要があります。 これらのシステムを担当していない場合は、サービス管理者に相談してください。

**手順 5**: 上記のステップに基づいて、これらの異なるグループをどのように管理するかを検討する必要があります。 セキュリティ グループを使用することをお勧めします。

## <a name="example-expense-report-solution-security"></a>例: 経費精算書ソリューションのセキュリティ

経費承認シナリオでは、すべての従業員が経費精算書を提出できるので、すべての従業員が経費精算書作成アプリにアクセスできる必要があります。 さらに、承認者は承認アプリにアクセスする必要があります。

> 経費報告アプリとそれが使用するデータにアクセスできる全従業員のセキュリティ グループが必要です。
承認アプリにアクセスできる承認者のセキュリティ グループが必要です。

経理部門は、払い戻しのために従業員の銀行口座などのより機密性の高いデータにアクセスする必要がある場合があります。

> 従業員の銀行のルーティング情報にアクセスできる唯一のセキュリティ グループである経理チームのセキュリティ グループが必要です。

従業員がお互いの経費精算書を閲覧できないようにするために、従業員が自分のレコードのみにアクセスできるようにレコード レベルのセキュリティを設定する必要があります。 ただし、承認者が承認のために取得したレポートを表示できるようにする必要もあります。 また、監査チームがすべての経費精算書を確認できるようにする必要があります (ただし、変更はできません)。

> 監査担当者のセキュリティ グループが必要です。 これと承認者セキュリティ グループにすべてのレコードへのアクセス権を与え、全従業員グループに "作成したレコード" へのアクセス権のみを与える必要があります。

![経費精算書セキュリティ グループの図](media/expense-report-security.png "経費精算書セキュリティ グループの図")

詳細情報については次を参照してください: [ Common Data Serviceのセキュリティ](https://docs.microsoft.com/power-platform/admin/wp-security)

> [!div class="nextstepaction"]
> [次のステップ: アプリを作成する](making-phase.md)