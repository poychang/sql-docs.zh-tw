---
title: NonEmptyBehavior 元素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- NonEmptyBehavior Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- NonEmptyBehavior
helpviewer_keywords:
- NonEmptyBehavior element
ms.assetid: b4c78af4-b049-4189-a35b-206e3938d1db
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 911b797b3f1d6ff2a8cd9fac1dfc88384d2cac7f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48227978"
---
# <a name="nonemptybehavior-element-assl"></a>NonEmptyBehavior 元素 (ASSL)
  決定父代相關聯的非空白行為[CalculationProperty](../objects/calculationproperty-element-assl.md)項目。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<CalculationProperty>  
  
   <NonEmptyBehavior>...</NonEmptyBehavior>  
  
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
|父元素|[CalculationProperty](../objects/calculationproperty-element-assl.md)|  
|子元素|None|  
  
## <a name="remarks"></a>備註  
 `NonEmptyBehavior`屬性會套用至`CalculationProperty`項目[CalculationType](calculationtype-element-assl.md)設定為*成員*。  
  
 對應至父系的元素`NonEmptyBehavior`在 「 分析管理物件 (AMO) 物件模型是<xref:Microsoft.AnalysisServices.CalculationProperty>。  
  
## <a name="see-also"></a>另請參閱  
 [CalculationProperties 元素&#40;ASSL&#41;](../collections/calculationproperties-element-assl.md)   
 [MdxScript 元素&#40;ASSL&#41;](../objects/mdxscript-element-assl.md)   
 [MdxScripts 元素&#40;ASSL&#41;](../collections/mdxscripts-element-assl.md)   
 [屬性&#40;ASSL&#41;](properties-assl.md)  
  
  
