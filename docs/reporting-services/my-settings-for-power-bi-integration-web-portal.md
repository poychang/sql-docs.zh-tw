---
title: Power BI 整合的我的設定 (入口網站) | Microsoft Docs
ms.date: 08/17/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
f1_keywords:
- pbi
- power bi
- power bi integration
ms.assetid: 85c2fac7-80bf-45b7-8654-764b5f5231f5
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 766b33607487a8dcc247402b16edd67ab86071ab
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47818966"
---
# <a name="my-settings-for-power-bi-integration-web-portal"></a>Power BI 整合的我的設定 (入口網站)

[!INCLUDE[ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../includes/ssrs-appliesto-pbirs.md)]

個別使用者可以使用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] 中的 [我的設定] 頁面來管理其 [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] 登入。 當您在進行固定報表項目的步驟時，系統會自動提示您登入。  不過，如果您需要手動登入或需要登出，可以使用 [我的設定] 頁面。如果您看不到 [我的設定] 功能表選項，表示報表伺服器尚未與 [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] 整合。  如需詳細資訊，請參閱 [Power BI 報表伺服器整合 &#40;組態管理員&#41;](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md)。  
  
![ssRS_WebPortal_MySettings](../reporting-services/media/ssrs-webportal-mysettings.png)  
  
## <a name="why-sign-in"></a>為什麼要登入

 當您登入時，會建立 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 使用者帳戶與 [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] 帳戶之間的關聯性。  登入會建立有效期間達 90 天的安全性權杖。 如果權杖到期，而您有項目釘選到 Power BI，則您會看到通知。  
   
 ![ssRS_WebPortal_PowerBI_Notification](../reporting-services/media/ssrs-webportal-powerbi-notification.png)    
   
[!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] 儀表板內的磚在您透過登入 **MySettings**重新登入之前都不會重新整理。  
  
![ssRS_WebPortal_PowerBI_SignIn_Again](../reporting-services/media/ssrs-webportal-powerbi-signin-again.png)  
  
一旦您登入，就會建立新的安全性權杖。  儀表板磚會開始依照先前設定的排程進行更新。  

## <a name="next-steps"></a>後續步驟

[Power BI 報表伺服器整合](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md)   
[Power BI 儀表板的固定 Reporting Services 項目](../reporting-services/pin-reporting-services-items-to-power-bi-dashboards.md)   
[Power BI 的儀表板](https://powerbi.microsoft.com/documentation/powerbi-service-dashboards/)  
[入口網站](../reporting-services/web-portal-ssrs-native-mode.md)  

更多問題嗎？ [請嘗試詢問 Reporting Services 論壇](http://go.microsoft.com/fwlink/?LinkId=620231)
