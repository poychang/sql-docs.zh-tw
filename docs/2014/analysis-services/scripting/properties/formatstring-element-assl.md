---
title: FormatString 元素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- FormatString Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- FormatString
helpviewer_keywords:
- FormatString element
ms.assetid: 7b996221-936e-4f36-a3a8-676eb9869c55
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cbcc34f0bdc167f61beebb2e97171027759d6c3b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48089858"
---
# <a name="formatstring-element-assl"></a>FormatString 元素 (ASSL)
  說明的顯示格式[CalculationProperty](../objects/calculationproperty-element-assl.md)項目或有[量值](../objects/measure-element-assl.md)項目。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<CalculationProperty> <!-- or Measure -->  
   ...  
   <FormatString>...</FormatString>  
   ...  
</CalculationProperty>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|String|  
|預設值|None|  
|基數|0-1：只能出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[CalculationProperty](../objects/calculationproperty-element-assl.md)，[量值](../objects/measure-element-assl.md)|  
|子元素|None|  
  
## <a name="remarks"></a>備註  
 `FormatString` 屬性會包含多維度運算式 (MDX) 運算式。 若是`CalculationProperty`項目，它適用於具有項目[CalculationType](calculationtype-element-assl.md)的*成員*或*儲存格*。  
  
 對應至父系的元素`FormatString`在 「 分析管理物件 (AMO) 物件模型所<xref:Microsoft.AnalysisServices.CalculationProperty>和<xref:Microsoft.AnalysisServices.Measure>。  
  
## <a name="see-also"></a>另請參閱  
 [CalculationProperties 元素&#40;ASSL&#41;](../collections/calculationproperties-element-assl.md)   
 [MdxScript 元素&#40;ASSL&#41;](../objects/mdxscript-element-assl.md)   
 [MdxScripts 元素&#40;ASSL&#41;](../collections/mdxscripts-element-assl.md)   
 [屬性&#40;ASSL&#41;](properties-assl.md)  
  
  
