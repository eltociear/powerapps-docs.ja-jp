---
title: PowerApps アプリ デザイナーでのモデル駆動型アプリ プロパティの管理 | MicrosoftDocs
description: アプリのプロパティの管理方法を説明します。
keywords: ''
ms.date: 02/05/2019
ms.service: powerapps
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: e773e60f-0211-4c4b-a1af-663be4997629
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: 14
topic-status: Drafting
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: a4f28dd878ca2e862a99982564066eefacfb7892
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "2701888"
---
# <a name="manage-model-driven-app-properties-in-the-app-designer"></a>アプリ デザイナーでのモデル駆動型アプリ プロパティの管理

アプリ プロパティは、タイトルまたは URL などのアプリケーションに関する重要な詳細を定義します。 アプリを作成するとき、そのアプリ プロパティを定義します。 それらのプロパティを後で変更する場合は、アプリ デザイナーで行うことができます。  
  
1.  アプリ デザイナーの右側で、**プロパティ**タブを選択します。  

    > [!div class="mx-imgBorder"] 
    > ![アプリ デザイナーの [プロパティ] ウィンドウ](media/app-designer-properties-tab.png "アプリ デザイナーの [プロパティ] ウィンドウ")  
  
2.  必要に応じて、情報を変更:  

    |プロパティ|内容|  
    |--------------|-----------------|
    |**名前**|アプリケーションに一意および内容を示す名前を入力します。|  
    |**説明**|どのアプリであるかに関する短い説明を入力します。|  
    |**アイコン**|既定では、**既定のアプリの使用**チェック ボックスはオンになっています。 アプリケーションのアイコンとして、異なる Web リソースを選択するには、チェック ボックスをオフにし、次に、ドロップダウン リストからアイコンを選択します。 このアイコンはアプリのプレビュー タイルに表示されます。|
    |**一意の名前**| 一意の名前は変更できません。 一意の名前を使用してテーブルをクエリし、データベースからデータを取得できます。|
    |**アプリの URL の接頭辞<sup>1</sup>**| アプリの作成中に選択した URL は、既定でここに表示されます。 **アプリの管理**ダイアログ ボックスでアプリの URL を変更できます。 この時点では、ソリューションによってアプリ URL サフィックスをエクスポート、またはインポートすることはできない点に注目してください。|
    |**アプリの [ようこそ] ページを選択**|このオプションを使用すると、環境で利用できる Web リソースの中から選択することができます。 作成した [ようこそ] ページには、ビデオへのリンク、アップグレードの手順、開始方法に関する情報など、有用な情報を含めることができます。 [ようこそ] ページとして使用できる HTML ファイルなどの Web リソースの作成方法の詳細については、「[Web リソースを作成および編集して Web アプリケーションを拡張](create-edit-web-resources.md)」を参照してください。|
    |**Mobile Offline の有効化**|このオプションにより、**Mobile Offline プロファイル**ドロップ ダウン リストを使用して選択されたプロファイルを、モバイル上のアプリがオフラインで使用できます。|

    <sup>1</sup>新しいアプリケーションを作成するとき、**アプリケーション URL の接尾辞** プロパティおよび **クライアント** プロパティは使用できなくなります。
3.  アプリを保存します。  
  
## <a name="next-steps"></a>次のステップ  
 [アプリの作成または編集](create-edit-app.md)
