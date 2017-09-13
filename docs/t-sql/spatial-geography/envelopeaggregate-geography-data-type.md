---
title: "EnvelopeAggregate (geography 資料類型) |Microsoft 文件"
ms.custom: 
ms.date: 07/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- EnvelopeAggregate_TSQL
- EnvelopeAggregate
dev_langs:
- TSQL
helpviewer_keywords:
- EnvelopeAggregate method (geography)
ms.assetid: 4947797f-edb8-490f-beca-37df9ec06954
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e9d50e15f644a5662af2eead65d29447af8493a9
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="envelopeaggregate-geography-data-type"></a>EnvelopeAggregate (geography 資料類型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

傳回一組指定的週框物件**geography**物件。 產生**geography**物件包含多個圓弧線段。
  
## <a name="syntax"></a>語法  
  
```  
  
EnvelopeAggregate ( geography_operand )  
```  
  
## <a name="arguments"></a>引數  
 *geography_operand*  
 是**geography**類型資料表資料行包含一組**geography**物件要執行封套彙總作業。  
  
## <a name="return-types"></a>傳回類型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]傳回型別：**地理位置**  
  
## <a name="remarks"></a>備註  
 A **FullGlobe**結果週框物件大於半球時，會傳回物件。 這個方法並不精確。  
  
 方法會傳回**null**如果輸入具有不同 Srid。 請參閱[空間參考識別碼 &#40;Srid &#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md).  
  
 方法會忽略**null**輸入。  
  
> [!NOTE]  
>  方法會傳回**null**如果所有輸入的值為**null**。  
  
## <a name="examples"></a>範例  
 下列範例會執行`EnvelopeAggregate`上一組**geography**縣 （市） 內的位置點。  
  
 `USE AdventureWorks2012`  
  
 `GO`  
  
 `SELECT City,`  
  
 `geography::EnvelopeAggregate(SpatialLocation) AS SpatialLocation`  
  
 `FROM Person.Address`  
  
 `WHERE PostalCode LIKE('981%')`  
  
 `GROUP BY City;`  
  
## <a name="see-also"></a>另請參閱  
 [擴充的靜態地理方法](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  
