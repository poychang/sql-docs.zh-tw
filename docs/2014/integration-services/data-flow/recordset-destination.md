---
title: 資料錄集目的地 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.recordsetdest.f1
helpviewer_keywords:
- Recordset destination
- ADO recordsets [Integration Services]
- destinations [Integration Services], Recordset
- in-memory ADO recordsets [Integration Services]
ms.assetid: be973cf1-c4ff-49f8-987e-314c08ef98e4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: dbfbf931bc28893b328ce4ac869278b012c6658c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48063890"
---
# <a name="recordset-destination"></a>資料錄集目的地
  資料錄集目的地可建立和擴展記憶體中的 ADO 資料錄集。 資料錄集的形狀，是由設計階段時對「資料錄集」目的地的輸入所定義。  
  
## <a name="configuration-of-the-recordset-destination"></a>資料錄集目的地的組態  
 藉由指定儲存 ADO 資料錄集的變數，您可以設定「資料錄集」目的地。  
  
 在執行階段，ADO 資料錄集會被寫入「資料錄集」目的地之 VariableName 屬性中指定的 [物件] 變數類型。 然後，該變數會使「資料錄集」在資料流程外部可用，指令碼及其他封裝元素會在此處使用該資料錄集。  
  
 此來源具有一個輸入。 它不支援錯誤輸出。  
  
 您可以透過「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」或以程式設計方式設定屬性。  
  
 **[進階編輯器]** 對話方塊會反映能以程式設計的方式設定之屬性。 如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按下列其中一個主題：  
  
-   [Common Properties](../common-properties.md)  
  
-   [資料錄集目的地自訂屬性](recordset-destination-custom-properties.md)  
  
 如需如何設定屬性的詳細資訊，請參閱 [設定資料流程元件的屬性](set-the-properties-of-a-data-flow-component.md)。  
  
## <a name="related-tasks"></a>相關工作  
 [使用資料錄集目的地](recordset-destination.md)  
  
  
