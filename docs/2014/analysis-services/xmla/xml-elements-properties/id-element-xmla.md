---
title: ID 元素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#ID
- urn:schemas-microsoft-com:xml-analysis#ID
- microsoft.xml.analysis.id
helpviewer_keywords:
- ID element
ms.assetid: f7d67599-6a70-4455-bfdb-1d127e5eff4e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 86a24d14a0c9e198c879e4dce092f430a4755871
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48110128"
---
# <a name="id-element-xmla"></a>ID 元素 (XMLA)
  識別要在上面執行父代[鎖定](../xml-elements-commands/lock-element-xmla.md)或是[Unlock](../xml-elements-commands/unlock-element-xmla.md)項目。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<Lock> <!-- or Unlock>  
   ...  
   <ID>...</ID>  
   ...  
</Lock>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|String|  
|預設值|None|  
|基數|1-1：只出現一次的必要元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[鎖定](../xml-elements-commands/lock-element-xmla.md)，[解除鎖定](../xml-elements-commands/unlock-element-xmla.md)|  
|子元素|None|  
  
## <a name="remarks"></a>備註  
 `ID` 元素包含用來識別鎖定的全域唯一識別碼 (GUID)。  
  
## <a name="see-also"></a>另請參閱  
 [物件項目&#40;XMLA&#41;](object-element-xmla.md)   
 [Mode 元素&#40;XMLA&#41;](mode-element-xmla.md)   
 [屬性&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
