---
title: 屬性元素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Attributes Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Attributes
helpviewer_keywords:
- Attributes element
ms.assetid: d6b545e6-1521-496f-a731-f2c2c44118e4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d726fe60be6aa2e79e8f1032f4f49606472baf3f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48131208"
---
# <a name="attributes-element-assl"></a>Attributes 元素 (ASSL)
  包含相關聯維度之屬性的集合。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<AggregationDesignDimension> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Attributes>  
      <Attribute>...</Attribute>  
  </Attributes>  
   ...  
</AggregationDesignDimension>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|None|  
|預設值|None|  
|基數|0-1：只能出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[AggregationDesignDimension](../data-type/dimension-data-type-assl.md)， [AggregationDimension](../data-type/aggregationdimension-data-type-assl.md)， [AggregationInstanceCubeDimension](../data-type/cubedimension-data-type-assl.md)， [CubeDimension](../data-type/cubedimension-data-type-assl.md)，[維度](../objects/dimension-element-assl.md)， [PerspectiveDimension](../data-type/perspectivedimension-data-type-assl.md)， [RegularMeasureGroupDimension](../data-type/measuregroupdimension-data-type-assl.md)， [RelationshipEnd](../data-type/relationshipend-data-type-assl.md)|  
|子元素|[Attribute](../objects/attribute-element-assl.md)|  
  
## <a name="remarks"></a>備註  
 在「分析管理物件」(AMO) 物件模型中對應的元素是 <xref:Microsoft.AnalysisServices.AggregationAttributeCollection>、<xref:Microsoft.AnalysisServices.AggregationDesignAttributeCollection>、<xref:Microsoft.AnalysisServices.AggregationInstanceAttributeCollection>、<xref:Microsoft.AnalysisServices.CubeAttributeCollection>、<xref:Microsoft.AnalysisServices.DimensionAttributeCollection>、<xref:Microsoft.AnalysisServices.MeasureGroupAttributeCollection> 和 <xref:Microsoft.AnalysisServices.PerspectiveAttributeCollection>。  
  
## <a name="see-also"></a>另請參閱  
 [集合&#40;ASSL&#41;](collections-assl.md)  
  
  
