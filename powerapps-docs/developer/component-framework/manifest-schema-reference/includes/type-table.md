---
title: 型 Table |Microsoft Docs
description: ''
keywords: ''
ms.author: nabuthuk
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
ms.assetid: 41ea27ac-65b6-45a4-ae03-5f8d02dfc67b
ms.openlocfilehash: 058580b8f39417ccc5e77e7ac96a51bfc95939a1
ms.sourcegitcommit: 63ea15e2f861d43333aacda19230cd8922d7bdfd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2019
ms.locfileid: "72338760"
---
|Value|Description|
|--|--|
|`Currency`|このフィールドには、-922337203685477 ~ 922337203685477 の通貨値を指定できます。 有効桁数を設定したり、特定の通貨または組織で使用される1つの標準有効桁数の有効桁数を基準にしたりすることができます。|
|`DateAndTime.DateAndTime`|日付と時刻を表示します。|
|`DateAndTime.DateOnly`|日付のみを表示します。|
|`Decimal`|-1000億 ~-1000億の値には、10個までの有効桁数を使用できます。このフィールドには、-を指定できます。 有効桁数および最大値と最小値を指定できます。|
|`Enum`|列挙データ型。|
|`FP`|このフィールドには、-1000億から-1000億までの値に対して最大5つの小数点以下桁数を使用できます。 有効桁数および最大値と最小値を指定できます。 |
|`Multiple`|このフィールドには、最大1048576文字まで含めることができます。 最大長は、この値より小さい値に設定できます。 フォームにこのフィールドを追加すると、フィールドのサイズを指定できます。|
|`OptionSet`|このフィールドには、一連のオプションが表示されます。 各オプションには、番号の値とラベルがあります。 フォームに追加されると、このフィールドにはユーザーが1つのオプションのみを選択するためのコントロールが表示されます。 |
|`SingleLine.Email`|テキストは、ユーザーの電子メールアプリケーションを開くための mailto リンクを提供します。|
|`SingleLine.Phone`|Web アプリケーションでは、いずれかのクライアントがコンピューターにインストールされている場合に、Skype または Lync を使用して呼び出しを開始するために、フィールドがクリック可能になります。 テレフォニープロバイダーの選択は、[システム設定] の [全般] タブの下部にあります。タブレットの Dynamics 365 では、使用可能な唯一のテレフォニープロバイダーです。|
|`SingleLine.Text`|このオプションは、単にテキストを表示します。|
|`SingleLine.TextArea`|この format オプションを使用すると、複数行のテキストを表示できます。 ただし、上限が4000文字である場合、テキストフィールドの複数行は、大量のテキストが必要な場合に適しています。|
|`SingleLine.Ticker`|ほとんどの言語では、テキストがリンクとして有効になり、MSN マネーの web サイトを開いて、ティッカーシンボルで表される株価の詳細を表示します。特定の東アジア言語の場合、ウィンドウは、ティッカーシンボルの Bing の検索結果を開きます。|
|`SingleLine.URL`|テキストは、指定されたページを開くためのハイパーリンクを提供します。 有効なプロトコルで開始されていないテキストは、先頭に "http://" が付加されます。このフィールドでは、HTTP、HTTPS、FTP、FTPS、ONENOTE、および TEL のプロトコルのみを使用できます。|
|`TwoOptions`|このフィールドには2つのオプションがあります。 各オプションには、false または true の値に対応する0または1の数値が含まれています。 また、各オプションにはラベルがあり、true または false の値を "Yes"、"No"、"Hot"、"コールド"、"On"、"Off"、または表示するラベルのペアとして表すことができます。|
|`Whole.None`|このオプションは、単に数値を表示します。|

## <a name="value-elements-that-are-not-supported"></a>サポートされていない値要素

次の `of-type` 属性値は現在サポートされていません。

|Value|Description|
|-----|------|
|`Whole.Duration`|この形式オプションを使用して、期間のオプションの一覧を表示できます。 ただし、データベースに格納されているデータは常に分単位です。 フィールドはドロップダウンリストのように表示され、最大3日間の1分、15分、30分のような推奨オプションを提供します。 これらのオプションを選択できます。 ただし、数分で入力するだけで、その期間に解決されることもあります。|
|`Whole.Timezone`|このオプションを選択すると、(GMT-12:00) 国際日付行の西部や (GMT-08:00) 太平洋標準時 (米国 & カナダ) などのタイムゾーンの選択リストが表示されます。 これらの各ゾーンは、数値として格納されます。 たとえば、タイムゾーン (GMT-08:00) の太平洋標準時 (米国 & カナダ) の場合、TimeZoneCode は4です。 詳細情報: [TimeZoneCode クラス (Sdk アセンブリ)](https://docs.microsoft.com/en-us/previous-versions/dynamics-crm4/developers-guide/bb959779(v=msdn.10))|
|`Whole.Language`|このオプションを選択すると、組織に対してプロビジョニングされた言語の一覧が表示されます。 値は言語名のドロップダウンリストとして表示されますが、データは LCID コードを使用して数値として格納されます。 言語コードは、4 桁または 5 桁のロケール ID です。 有効なロケール ID 値は[ロケール ID (LCID) チャート](https://docs.microsoft.com/en-us/previous-versions/windows/embedded/ms912047(v=winembedded.10)) に示されています。|
|`Lookup.Simple`|特定のエンティティへの単一の参照を許可します。 すべてのカスタム参照は、この型です。|
|`Lookup.Customer`|アカウントまたは連絡先レコードへの1つの参照を許可します。 これらの参照は、Opportunity、Case、Quote、Order、および Invoice の各エンティティで使用できます。 これらのエンティティには、顧客が常に1つの種類である場合に使用できる個別のアカウントと連絡先参照もあります。 または、顧客参照を使用する代わりに両方を含めることができます。|
|`Lookup.Owner`|チームまたはユーザーレコードへの1つの参照を許可します。 すべてのチームまたはユーザー所有のエンティティには、これらのうちの1つがあります。|
|`Lookup.PartyList`|複数のエンティティへの複数の参照を許可します。 これらの参照は、電子メール エンティティの **宛先** フィールドと **Cc** フィールドにあります。 これらは、Phone エンティティと予定エンティティでも使用されます。|
|`Lookup.Regarding`|複数のエンティティへの単一の参照を許可します。 これらの参照は、アクティビティで使用される関連フィールドにあります。|
|`MultiSelectOptionSet`|複数選択フィールドを追加することにより、フォーム (メイン、簡易作成、クイックビュー) および電子メールテンプレートをカスタマイズできます。 複数選択のオプションセットフィールドを追加するときに、ユーザーが選択できる複数の値を指定できます。 ユーザーがフォームに入力すると、ドロップダウンリストに表示される値を1つ、複数、またはすべて選択できます。|
