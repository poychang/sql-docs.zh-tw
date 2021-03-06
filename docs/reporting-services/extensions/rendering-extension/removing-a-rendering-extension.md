---
title: 移除轉譯延伸模組 | Microsoft Docs
ms.date: 03/18/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- deleting rendering extensions
- removing rendering extensions
- rendering extensions [Reporting Services], removing
ms.assetid: 2abfebfb-065f-45cc-a904-c914394cf900
author: markingmyname
ms.author: maghan
ms.openlocfilehash: bd360d5a4929ab41c7b77e60b59b394f127f6f13
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47723876"
---
# <a name="removing-a-rendering-extension"></a>移除轉譯延伸模組
  若要移除 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 轉譯延伸模組，只要從 rsreportserver.config 檔案 (位於 **%ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<執行個體名稱>\Reporting Services\ReportServer** 資料夾) 中移除轉譯延伸模組的 **Extension** 項目即可。 如果您已經為報表設計師以及報表伺服器建立項目，請同時從 [RSReportDesigner 設定檔](../../../reporting-services/report-server/rsreportdesigner-configuration-file.md)中移除 **Extension** 項目。 在移除組態資訊之後，轉譯延伸模組將無法再供元件使用。  
  
## <a name="see-also"></a>另請參閱  
 [Reporting Services 組態檔](../../../reporting-services/report-server/reporting-services-configuration-files.md)   
 [實作轉譯延伸模組](../../../reporting-services/extensions/rendering-extension/implementing-a-rendering-extension.md)   
 [轉譯延伸模組概觀](../../../reporting-services/extensions/rendering-extension/rendering-extensions-overview.md)   
 [實作 IRenderingExtension 介面](../../../reporting-services/extensions/rendering-extension/implementing-the-irenderingextension-interface.md)   
 [延伸模組的安全性考量](../../../reporting-services/extensions/security-considerations-for-extensions.md)   
 [部署轉譯延伸模組](../../../reporting-services/extensions/rendering-extension/deploying-a-rendering-extension.md)  
  
  
