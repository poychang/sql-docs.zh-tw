---
title: AggregationInstanceCubeDimension 資料類型 (ASSL) |Microsoft 文件
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b15df19973cc4b398772880eeee04dc4a4f6e5c9
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
ms.locfileid: "34029929"
---
# <a name="aggregationinstancecubedimension-data-type-assl"></a>AggregationInstanceCubeDimension 資料類型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  定義代表彙總執行個體所使用之 Cube 維度相關資訊的基本資料類型。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<AggregationInstanceCubeDimension>  
   <CubeDimensionID>...</CubeDimensionID>  
   <KeyColumns>...</KeyColumns>  
   <Attributes>...</Attributes>  
</AggregationInstanceCubeDimension>  
```  
  
## <a name="data-type-characteristics"></a>資料類型特性  
  
|特性|說明|  
|--------------------|-----------------|  
|基底資料類型|無|  
|衍生資料類型|無|  
  
## <a name="data-type-relationships"></a>資料類型關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|無|  
|子元素|[屬性](../../../analysis-services/scripting/collections/attributes-element-assl.md)， [CubeDimensionID](../../../analysis-services/scripting/properties/cubedimensionid-element-assl.md)， [KeyColumns](../../../analysis-services/scripting/collections/keycolumns-element-assl.md)|  
|衍生的元素|[維度](../../../analysis-services/scripting/objects/dimension-element-assl.md)|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [Analysis Services 指令碼語言 XML 資料類型 & #40;ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
