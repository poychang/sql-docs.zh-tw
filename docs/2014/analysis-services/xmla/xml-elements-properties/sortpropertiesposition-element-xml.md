---
title: SortPropertiesPosition 元素 (XML) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 68b040a7-ab16-46f5-8610-21db07df9181
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0838a11aab6fa73060365b38c0f834749726a18d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48101258"
---
# <a name="sortpropertiesposition-element-xml"></a>SortPropertiesPosition 元素 (XML)
  包含有關元素在元素集合中的位置資訊。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<RelationshipEndVisualizationProperties>  
   ...  
   <SortPropertiesPosition>...</SortPropertiesPosition>  
   ...  
</RelationshipEndVisualizationProperties>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|Integer|  
|預設值|-1|  
|基數|0-1：只出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[RelationshipEndVisualizationProperties](../../scripting/data-type/relationshipendvisualizationproperties-data-type-assl.md)|  
|子元素|None|  
  
## <a name="remarks"></a>備註  
 對於 `RelationshipEndVisualizationProperties` 元素，`SortPropertiesPosition` 元素包含排序屬性元素在詳細資料集合中的位置。 預設值表示沒有要使用的排序屬性。  
  
  
