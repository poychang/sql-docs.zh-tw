---
title: ManufacturingExtraMonthQuarter 元素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ManufacturingExtraMonthQuarter Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ManufacturingExtraMonthQuarter
helpviewer_keywords:
- ManufacturingExtraMonthQuarter element
ms.assetid: 6e97d92c-dd1e-48f6-a379-c1036c975f9f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f1090e5057208a1472cd58dfeddfd83111abd509
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48048109"
---
# <a name="manufacturingextramonthquarter-element-assl"></a>ManufacturingExtraMonthQuarter 元素 (ASSL)
  定義要指派延長月份之製造週期的月份[TimeBinding](../data-type/binding-data-type-assl.md)項目。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<TimeBinding>  
   ...  
   <ManufacturingExtraMonthQuarter>...</ManufacturingExtraMonthQuarter>  
   ...  
</TimeBinding>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|整數 (1 至 4)|  
|預設值|`4`|  
|基數|0-1：只能出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[TimeBinding](../data-type/binding-data-type-assl.md)|  
|子元素|None|  
  
## <a name="remarks"></a>備註  
 對應至父系的元素`ManufacturingExtraMonthQuarter`在 「 分析管理物件 (AMO) 物件模型是<xref:Microsoft.AnalysisServices.TimeBinding>。  
  
## <a name="see-also"></a>另請參閱  
 [屬性&#40;ASSL&#41;](properties-assl.md)  
  
  
