---
title: Tuple 元素 (XMLA) |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0192a126b3be4338cedd47c1cd5b175ba1debc41
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38062665"
---
# <a name="tuple-element-xmla"></a>Tuple 元素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  包含 [Tuples](../../../analysis-services/xmla/xml-elements-properties/tuples-element-xmla.md) 父元素所包含之 [Member](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md) 元素的集合。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<Tuples>  
   <Tuple>  
      <Member>...</Member>  
   </Tuple>  
   ...  
</Tuples>  
```  
  
## <a name="element-characteristics"></a>項目特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|無|  
|預設值|無|  
|基數|0-n：出現一次以上的選擇性元素。|  
  
## <a name="element-relationships"></a>項目關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[Tuple](../../../analysis-services/xmla/xml-elements-properties/tuples-element-xmla.md)|  
|子元素|[成員](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md)|  
  
## <a name="remarks"></a>備註  
 當用戶端應用程式將 **AxisFormat** 屬性設為 *TupleFormat* 時，軸就會表示成 Tuple 集合。 每個 **Axis** 元素都包含代表該軸上 Tuple 集合的 **Tuples** 元素。 每個 Tuple 都會使用包含該軸上每個階層之 **Member** 元素的 **Tuple** 元素來表示。  
  
## <a name="example"></a>範例  
 下列範例將說明當用戶端指定 *TupleFormat* 或 *CustomFormat* 給 **AxisFormat** XMLA 屬性時，**Tuple** 元素的結構 (假設軸具有下列成員的話)：  
  
|||||  
|-|-|-|-|  
|**時間**階層|1999|1999|2000|  
|**類別目錄**階層|實際|預算|預算|  
  
```  
<Axes>  
   <Axis name="Axis0">  
      <Tuples>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[1999]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Actual]</UName>  
               ...  
            </Member>  
         </Tuple>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[1999]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Tuple>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[2000]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Tuple>  
      </Tuples>  
   </Axis>  
   ...  
</Axes>  
```  
  
## <a name="see-also"></a>另請參閱
 [屬性&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
