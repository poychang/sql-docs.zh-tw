---
title: Alter 元素 (XMLA) |Microsoft 文件
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5ff62bcde0aa40e9bb052691d4d3dee1317c1217
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34574600"
---
# <a name="alter-element-xmla"></a>Alter 元素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  包含所使用的 Analysis Services 指令碼語言 (ASSL) 元素[Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)方法來修改 Analysis Services 執行個體上的物件。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<Command>  
   <Alter Scope="enum" AllowCreate="boolean" ObjectExpansion="enum">  
      <Object>...</Object>  
      <ObjectDefinition>...</ObjectDefinition>  
   </Alter>  
</Command>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|無|  
|預設值|無|  
|基數|0-n：出現一次以上的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|子元素|[物件](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)， [ObjectDefinition](../../../analysis-services/xmla/xml-elements-properties/objectdefinition-element-xmla.md)|  
  
## <a name="attributes"></a>屬性  
  
|attribute|描述|  
|---------------|-----------------|  
|AllowCreate|(選擇性**布林**屬性) 指出物件是否定義在**Alter**應建立命令，如果它們尚不存在。<br /><br /> 如果設定為 true 中, 定義的物件**ObjectDefinition**上所建立的項目[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]執行個體如果已經存在。 換句話說， **Alter**命令會被視為**建立**命令如果物件不存在的執行個體上。<br /><br /> 如果這個屬性被省略或設定為**false**，如果物件不存在，就會發生錯誤。|  
|ObjectExpansion|(選擇性**列舉**屬性) 定義的所要執行的更改範圍**Execute**方法。<br /><br /> 如果設定為*ObjectProperties*、 **ObjectDefinition**項目應該包含要改變的主要物件的完整定義包括從屬次要物件。 要更改之物件的從屬主要物件會維持不變。<br /><br /> 附註： 當使用*ObjectProperties*設定[ClrAssembly](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)資料型別，[資料](../../../analysis-services/scripting/objects/data-element-assl.md)相關聯的項目[ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md)不需要指定資料類型。 如果未指定， **ClrAssembly**會使用現有的檔案。<br /><br /> 如果設定為*ExpandFull*、 **ObjectDefinition**項目應該包含不只是要變更、 物件的定義，但是也就是物件的下階的所有主要物件的定義若要改變。<br /><br /> 注意： *ExpandFull*設定無法搭配[伺服器](../../../analysis-services/scripting/objects/server-element-assl.md)項目。|  
|範圍。|(選擇性**列舉**屬性) 定義中定義之物件的持續時間**ObjectDefinition**項目。<br /><br /> 如果設定為*工作階段*中, 定義的物件**ObjectDefinition**元素只存在於 XMLA 工作階段的持續時間。<br /><br /> 注意： 當使用*工作階段*設定， **ObjectDefinition**元素只能包含[維度](../../../analysis-services/scripting/objects/dimension-element-assl.md)， [Cube](../../../analysis-services/scripting/objects/cube-element-assl.md)，或[MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md) ASSL 元素。<br /><br /> 如果省略此屬性，則中定義的物件**ObjectDefinition**項目會保存[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]執行個體。|  
  
## <a name="remarks"></a>備註  
 每個**Alter**命令會變更所指定的父物件底下某個主要物件的定義[ParentObject](../../../analysis-services/xmla/xml-elements-properties/parentobject-element-xmla.md)項目。  
  
## <a name="see-also"></a>另請參閱
 [命令&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
