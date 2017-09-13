---
title: "M (geography 資料類型) |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- M (geography Data Type)
- M_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- M method
ms.assetid: cdba04f0-4e17-48f6-bafb-b1f918c5a501
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b9edb3d7c84fe1f92bb5888e97a782985d05ddd4
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="m-geography-data-type"></a>M (geography 資料類型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  **M** （測量） 值**geography**執行個體。 測量值的語意為使用者所定義，但是通常會描述沿著線段的距離。 例如，測量值可用來追蹤一條路上的里程碑。  
  
## <a name="syntax"></a>語法  
  
```  
  
.M  
```  
  
## <a name="return-types"></a>傳回類型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]類型： **float**  
  
 CLR 型別： **SqlDouble**  
  
## <a name="remarks"></a>備註  
 這個屬性的值為 null 如果**geography**執行個體不是**點**，以及對於任何**點**未設定它的執行個體。  
  
 此屬性是唯讀的。  
  
 M 值不會用於程式庫所做的任何計算，而且將不透過任何程式庫計算來夾帶。  
  
## <a name="examples"></a>範例  
 下列範例會建立具有 Z (高度) 和 M (測量) 值的 `Point` 例項，並使用 `M` 提取此例項的 `M` 值。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POINT(-122.34900 47.65100 10.3 12)', 4326);  
SELECT @g.M;  
```  
  
## <a name="see-also"></a>另請參閱  
 [Geography 執行個體上的擴充的方法](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [Z &#40; geography 資料類型 &#41;](../../t-sql/spatial-geography/z-geography-data-type.md)  
  
  