---
title: Drop 元素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Drop Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Drop
- microsoft.xml.analysis.drop
- http://schemas.microsoft.com/analysisservices/2003/engine#Drop
helpviewer_keywords:
- Drop element
ms.assetid: a5d21db3-743a-4958-b16d-b6816a5ee787
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b723e6ae10ae045ce43c7138ce481ffdab3955bd
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48194938"
---
# <a name="drop-element-xmla"></a>Drop 元素 (XMLA)
  從維度中刪除屬性成員。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<Command>  
   <Drop>  
      <Object>...</Object>  
      <DeleteWithDescendants>...</DeleteWithDescendants>  
      <Where>...</Where>  
   </Drop>  
</Command>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|None|  
|預設值|None|  
|基數|0-n：出現一次以上的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[Command](../xml-elements-properties/command-element-xmla.md)|  
|子元素|[DeleteWithDescendants](../xml-elements-properties/deletewithdescendants-element-xmla.md)，[物件](../xml-elements-properties/object-element-dimension-xmla.md)，[位置](../xml-elements-properties/where-element-xmla.md)|  
  
## <a name="remarks"></a>備註  
 `Drop` 命令會從可寫入維度中刪除屬性成員。  
  
 如需有關刪除成員的詳細資訊，請參閱 <<c0> [ 插入、 更新和卸除成員&#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md)。</c0>  
  
## <a name="see-also"></a>另請參閱  
 [插入項目&#40;XMLA&#41;](insert-element-xmla.md)   
 [更新項目&#40;XMLA&#41;](update-element-xmla.md)   
 [命令&#40;XMLA&#41;](xml-elements-commands.md)  
  
  
