---
title: 透過個人化擴充 OLAP |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- Analysis Services, extensibility
ms.assetid: 348e49fc-4390-43c1-9b6c-61b386ff4373
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 67e1af257dcdb9700fcdfa6643a50000f9dc845f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48092188"
---
# <a name="extending-olap-through-personalizations"></a>通過個人化擴充 OLAP
  Microsoft [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] 提供許多的內建函數，可搭配多維度運算式 (MDX) 和資料採礦延伸模組 (DMX) 語言使用。 這些函數是設計用來進行標準統計計算與階層中周遊成員間等工作。 不過，就如同其他複雜且功能強大的產品一樣，總是有進一步擴充產品功能的需求。  
  
 因此，Analysis Services 可讓您將組件和個人化的延伸模組加入到服務的執行個體，在標準功能不足時，完成您的商務需求。  
  
## <a name="assemblies"></a>組件  
 組件可以讓您延伸 MDX 和 DMX 的商務功能。 您可以將想要的功能建立成程式庫 (例如動態連結程式庫 (DLL))，然後將該程式庫當成組件加入 Analysis Services 執行個體或 Analysis Services 資料庫中。 程式庫中的公用方法便公開給 MDX 和 DMX 運算式、程序、計算、動作，以及用戶端應用程式，作為使用者自訂函數。  
  
## <a name="personalized-extensions"></a>個人化的延伸模組  
 SQL Server Analysis Services 個人化延伸模組是實作外掛程式架構之概念的基礎。 Analysis Services 個人化延伸模組是比現有 Managed 組件架構更簡單精緻的版本，會在整個 Analysis Services <xref:Microsoft.AnalysisServices.AdomdServer> 物件模型、多維度運算式 (MDX) 語法和結構描述資料列集中公開。  
  
## <a name="see-also"></a>另請參閱  
 [多維度模型組件管理](../multidimensional-model-assemblies-management.md)   
 [Analysis Services 個人化延伸模組](analysis-services-personalization-extensions.md)  
  
  
