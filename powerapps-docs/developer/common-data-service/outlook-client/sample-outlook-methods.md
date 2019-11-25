---
title: 'サンプル:  Dynamics 365 for Outlook メソッド (Common Data Service)  の使用| Microsoft Docs'
description: このサンプルは、`Microsoft.Crm.Outlook.Sdk.dll` アセンブリ内で使用できるメソッドの使用方法を示しています。
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: sriharibs
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 49ea89b034c617c03e23b11a115eada4735b83ab
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749246"
---
# <a name="sample-use-dynamics-365-for-outlook-methods"></a>サンプル: Dynamics 365 for Outlook メソッドの使用

このサンプル コードは、Common Data Service 向けです。 サンプルをダウンロードするには、[サンプル:  Dynamics 365 for Outlook メソッドの使用](https://msdn.microsoft.com/library/gg309513.aspx) を参照してください。

## <a name="prerequisites"></a>前提条件

サンプルプロジェクトをダウンロードし、サンプルプロジェクトで使用する NuGet パッケージを復元するにはインターネット接続が必要です。
  
## <a name="demonstrates"></a>説明  
 このサンプルは、`Microsoft.Crm.Outlook.Sdk.dll` アセンブリ内で使用できるメソッドの使用方法を示しています。  
  
## <a name="example"></a>例  

```csharp
// Set up the CRM Service.  
CrmOutlookService outlookService = new CrmOutlookService();

// Determine if the Outlook client is running
if (outlookService.IsCrmClientLoaded)
{
    if (outlookService.IsCrmDesktopClient)
    {
        // The desktop client cannot go offline
        Console.WriteLine("CRM Client Desktop URL: " +
            outlookService.ServerUri.AbsoluteUri);
        Console.WriteLine("CRM Client state: " +
            outlookService.State.ToString());
    }
    else
    {
        // See if laptop client is offline
        if (outlookService.IsCrmClientOffline)
        {
            Console.WriteLine("CRM Client Offline URL: " +
                outlookService.ServerUri.AbsoluteUri);
            Console.WriteLine("CRM Client state: " +
                outlookService.State.ToString());

            // Take client online
            // NOTE: GoOnline() will automatically Sync up with CRM
            // database, no need to call Sync() manually
            Console.WriteLine("Going Online...");
            outlookService.GoOnline();

            Console.WriteLine("CRM Client state: " +
                outlookService.State.ToString());
        }
        else
        {
            Console.WriteLine("CRM Client Online URL: " +
                outlookService.ServerUri.AbsoluteUri);
            Console.WriteLine("CRM Client state: " +
                outlookService.State.ToString());

            // Take client offline 
            // NOTE: GoOffline triggers a synchronization of the
            // offline database with the online server.
            // If a sync is not required, you can use SetOffline().
            Console.WriteLine("Going Offline...");
            outlookService.GoOffline();

            Console.WriteLine("CRM Client state: " +
                outlookService.State.ToString());
        }
    }
}
```
  
### <a name="see-also"></a>関連項目  

[Dynamics 365 for Outlook の拡張](extend-dynamics-365-outlook.md)<br />
<xref:Microsoft.Crm.Outlook.Sdk.CrmOutlookService><br />
<xref:Microsoft.Crm.Outlook.Sdk.CrmOutlookService.GoOnline><br />
<xref:Microsoft.Crm.Outlook.Sdk.CrmOutlookService.GoOffline>