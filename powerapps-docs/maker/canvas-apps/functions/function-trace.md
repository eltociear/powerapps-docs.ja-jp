---
title: Trace 関数 | Microsoft Docs
description: Power Apps テスト スタジオの Trace 関数の構文を含む参照情報
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/19/2018
ms.author: aheneay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 927b8dae59a4dc6fc55d74c1998b0d434eb8356c
ms.sourcegitcommit: d500f44e77747a3244b6691ad9b3528e131dbfa5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "3308247"
---
# <a name="trace-function"></a>Trace 関数 

Trace は、テスト スタジオで使用する場合、**OnTestCaseComplete** イベントからのテスト結果に追加情報を提供するために使用できる省略可能な式です。 トレース イベント メッセージおよびアサーションの成功と失敗に対するメッセージが、TestCaseResult レコードの Traces テーブルに含まれます。 Traces テーブルには、Message と Timestamp の 2 つのプロパティがあります。 

アプリでトレース メッセージを定義することもできます。 これらは、他のアクティビティと一緒に Power Apps モニターツールで表示でき、アプリのリアルタイム診断情報で問題をデバッグまたは特定するのに役立ちます。 アプリで Azure Application Insights にテレメトリ データを送信できるようにした場合、Trace 関数を使用して、Application Insights リソースにイベントまたは診断のカスタム情報を送信することもできます。  Application Insights でこのデータを調べて、問題を診断したり、アプリと機能の使用状況を把握したりすることができます。 Tests で使用されるトレース情報も、Application Insights に記録されます。 Canvas Studio からモニターを再生するとき、モニターがアプリに接続されるので、テスト トレース情報はモニター ツールでは使用できません。 

## <a name="syntax"></a>構文

*Trace(message, trace_severity, custom_record )*

- *Message* – 必須。 トレースされる情報。 テストでは、これにより TestCaseResult レコードの Traces テーブルにレコードが作成されます。 
- *Trace_severity* - 省略可能。 Application Insights に記録されたトレースの重大度レベル。 オプションは TraceSeverity.Information、TraceSeverity.Warning または TraceSeverity.Error です。 
- *custom_record* - 省略可能。 Application Insights に記録されるカスタム データを含むレコード。 
  

### <a name="see-also"></a>関連項目

[Test Studio の概要](../test-studio.md) <br>
[Test Studio の操作](../working-with-test-studio.md)
