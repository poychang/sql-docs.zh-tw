---
title: ISNULL (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- null values [Integration Services]
- ISNULL function
ms.assetid: 88dbf49e-1307-4dda-b9db-ff1632053550
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6780ed81142343e0e08ff624ee80e8ef2cc532c8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48129818"
---
# <a name="isnull-ssis-expression"></a>ISNULL (SSIS 運算式)
  依據運算式是否為 Null 來傳回布林結果。  
  
## <a name="syntax"></a>語法  
  
```  
  
ISNULL(expression)  
```  
  
## <a name="arguments"></a>引數  
 *expression*  
 為任何資料類型的有效運算式。  
  
## <a name="result-types"></a>結果類型  
 DT_BOOL  
  
## <a name="expression-examples"></a>運算式範例  
 如果 **DiscontinuedDate** 資料行包含 Null 值，則此範例會傳回 TRUE。  
  
```  
ISNULL(DiscontinuedDate)  
```  
  
 如果 **LastName** 資料行中的值為 Null，則此範例會傳回「Unknown last name」，否則會傳回 **LastName**中的值。  
  
```  
ISNULL(LastName)? "Unknown last name":LastName  
```  
  
 如果 **DaysToManufacture** 資料行為 Null，無論 **AddDays**變數的值為何，此範例會固定傳回 TRUE。  
  
```  
ISNULL(DaysToManufacture + @AddDays)  
```  
  
## <a name="see-also"></a>另請參閱  
 [函式&#40;SSIS 運算式&#41;](functions-ssis-expression.md)   
 [COALESCE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/coalesce-transact-sql)  
  
  
