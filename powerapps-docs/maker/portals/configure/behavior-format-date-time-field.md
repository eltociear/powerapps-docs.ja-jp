---
title: Common Data Service における日時フィールドの動作と形式 | MicrosoftDocs
description: ポータルで使用される日時フィールドの動作と形式。
author: sandhangitmsft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: sandhan
ms.reviewer: tapanm
ms.openlocfilehash: 6f67900066f3d0fd36823de095f4f1b6bb3270db
ms.sourcegitcommit: c12260f372ad2cc48d3146be570d2088c9ef1d86
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2020
ms.locfileid: "3494607"
---
# <a name="behavior-and-format-of-the-date-and-time-field"></a>日時フィールドの動作と形式

Common Data Service では、日付と時刻のデータ型はシステム エンティティの多くのフィールドで使用されます。 たとえば、マーケティング キャンペーンでアカウントが最後に使用された日時を表示したり、ケースがエスカレートされた日時を表示したりすることができます。 また、日付および時間フィールドを含むユーザー定義エンティティを作成することもできます。 フィールドを表す内容に応じて、ポータル フォームおよびグリッドに対する次のいずれかのフィールドの動作を選択できます。 
- **ユーザーのローカル**: フィールドの値はユーザーのローカル時間で表示され、現在のポータル言語/ロケールに基づいて書式設定されます。 値は、Common Data Service の UTC タイム ゾーン形式で保存されます。 異なるタイム ゾーンにいる Common Data Service のユーザー (または別のポータル ユーザー) がその値を表示した場合、それらは表示したユーザー自身のタイム ゾーンに変換されます。
- **日付のみ**: フィールド値には日付のみが含まれ、タイムゾーン変換なしで表示されます。 値の時間部分は常に午前 12 時です。 1 人のユーザーが入力した値は、異なるタイムゾーン (たとえば、生年月日) の他のユーザーによって同じになります。
  
  > [!Note]
  > このフィールドの動作は、保存後に変更することはできません。
  
- **タイム ゾーン非依存**: フィールドの値は日時を含み、タイム ゾーン変換なしで表示されます。 1 人のユーザーにより入力された値は、異なるタイム ゾーンの他のユーザーにも同じように表示されます。
  
  > [!Note]
  > このフィールドの動作は、保存後に変更することはできません。

次のサイト設定の作成により、ポータルに使用する既定の日付/時刻の形式を上書きすることもできます。
- DateTime/DateFormat: ポータルで使用する日付の形式。 
- DateTime/TimeFormat: ポータルで使用する時刻の形式。 
- DateTime/DateTimeFormat: ポータルで使用するすべての日付と時間の形式。

既定では、ポータルは Web サイト言語設定で指定されている標準の日付/時刻の形式を使用します。
承諾された日付/時刻の形式は [こちら](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings)で指定されます。
