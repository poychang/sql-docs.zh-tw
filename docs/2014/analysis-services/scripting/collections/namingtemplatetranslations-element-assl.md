---
title: NamingTemplateTranslations 元素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- NamingTemplateTranslations Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- NamingTemplateTranslations
helpviewer_keywords:
- NamingTemplateTranslations element
ms.assetid: fde65778-1fa3-490a-9874-8bf2052ef25c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b1c7accfde72c3e64b3845f720c33fce5b55711e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48099399"
---
# <a name="namingtemplatetranslations-element-assl"></a>NamingTemplateTranslations 元素 (ASSL)
  提供當地語系化翻譯的集合[NamingTemplate](../properties/namingtemplate-element-assl.md)項目之父[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<Attribute xsi:type="DimensionAttribute">  
   ...  
   <NamingTemplateTranslations>  
            <NamingTemplateTranslation xsi:type="Translation">...</NamingTemplateTranslation>  
...</NamingTemplateTranslations>  
   ...  
</Attribute>  
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
|父元素|[屬性](../objects/attribute-element-assl.md)型別的[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|子元素|[NamingTemplateTranslation](../objects/translation-element-assl.md)型別的[轉譯](translations-element-assl.md)|  
  
## <a name="remarks"></a>備註  
 值`NamingTemplateTranslation`項目僅供父屬性 (亦即的值[使用量](../properties/usage-element-dimensionattribute-assl.md)項目之父代`DimensionAttribute`設定為*父*。)  
  
 在 「 分析管理物件 (AMO) 物件模型的對應元素是<xref:Microsoft.AnalysisServices.DimensionAttribute>。  
  
## <a name="see-also"></a>另請參閱  
 [集合&#40;ASSL&#41;](collections-assl.md)  
  
  
