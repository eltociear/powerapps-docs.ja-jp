---
title: User 関数 | Microsoft Docs
description: Power Apps での User 関数の構文を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/07/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 75b7b4e1f4c66745bdbddebb30c0e4ca45dfeb2b
ms.sourcegitcommit: 56c8c7cc64695ccb00e0d021c9f98cf70b69b4a2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2020
ms.locfileid: "3308132"
---
# <a name="user-function-in-power-apps"></a>Power Apps の User 関数
現在のユーザーに関する情報を返します。

## <a name="description"></a>内容
**User** 関数は現在のユーザーに関する情報の[レコード](../working-with-tables.md#records) を返します。

| プロパティ | 内容 |
| --- | --- |
| **User().Email** |現在のユーザーのメール アドレス。 |
| **User().FullName** |姓名を含む、現在のユーザーのフル ネーム。 |
| **User().Image** |現在のユーザーの画像。 これは、フォーム "blob:*identifier*" の画像の URL になります。 **[Image](../controls/control-image.md)** コントロールの **[Image](../controls/properties-visual.md)** プロパティをこの値に設定し、アプリで画像を表示します。 |

> [!NOTE]
> 返される情報は、現在の Power Apps ユーザーについての情報です。  これは、Power Apps プレーヤーおよびスタジオに表示される "アカウント" 情報と一致します。これらの情報は、作成したアプリの外にある可能性があります。  これは、Office 365 または他のサービスの現在のユーザー情報と一致しない場合があります。

> [!NOTE]
> 2020 年 3 月より前に User 関数を使用してアプリケーションを公開した場合は、断続的に、写真が取得されないことがあります。 この問題は、2020 年 3 月末のリリースで修正されました。  更新された実装を利用するには、アプリケーションを再度開き、保存して、再公開します。  

## <a name="syntax"></a>構文
**User**()

## <a name="examples"></a>例
現在の Power Apps ユーザーには、次の情報があります。

* フル ネーム: **"John Doe"**
* メール アドレス: **"john.doe@contoso.com"**
* 画像: ![](media/function-user/john-doe-picture.png) 

|       計算式       |                                                                    内容                                                                    |                                                 結果                                                  |
|---------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|
|     **User()**      |                                             現在の Power Apps ユーザーについてのすべての情報のレコード。                                             |    { FullName:&nbsp;"John Doe", Email:&nbsp;"john.doe@contoso.com", Image:&nbsp;"blob:1234...5678" }    |
|  **User().Email**   |                                                 現在の Power Apps ユーザーのメール アドレス。                                                  |                                         "john.doe@contoso.com"                                          |
| **User().FullName** |                                                   現在の Power Apps ユーザーのフル ネームを返します。                                                    |                                               "John Doe"                                                |
|  **User().Image**   | 現在の Power Apps ユーザーの画像の URL。  **Image** コントロールの **Image** プロパティをこの値に設定し、アプリで画像を表示します。 | "blob:1234...5678"<br><br>**ImageControl.Image** を使用:<br>![](media/function-user/john-doe-picture.png) |

