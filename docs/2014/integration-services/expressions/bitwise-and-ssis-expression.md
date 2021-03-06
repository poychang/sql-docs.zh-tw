---
title: '&amp; (位元 AND) (SSIS 運算式) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- AND, bitwise AND
- '& (bitwise AND)'
- bitwise AND (&)
ms.assetid: 06d2958e-66a5-44d8-8bc4-56209ebe1ff2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a89f5c0a9c4044c56d14015fe1fe9282b6a5dfb7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48118738"
---
# <a name="amp-bitwise-and-ssis-expression"></a>&amp; (位元 AND) (SSIS 運算式)
  執行兩個整數值的位元 AND 運算。 它會比較其第一個運算元的每個位元和其第二個運算元的對應位元。 如果這兩個位元都是 1，則對應的結果位元會設為 1。 否則，對應的結果位元會設為 0。  
  
 兩種條件必須都是帶正負號的整數類型，或者兩種條件必須都是不帶正負號的整數類型。  
  
## <a name="syntax"></a>語法  
  
```  
  
integer_expression1 & integer_expression2  
  
```  
  
## <a name="arguments"></a>引數  
 *integer_expression1, integer_expression2*  
 已簽署或未簽署整數資料類型的任何有效運算式。 如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。  
  
## <a name="result-types"></a>結果類型  
 由兩個引數的資料類型決定。 如需相關資訊，請參閱 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)。  
  
## <a name="remarks"></a>備註  
 如果任一個條件為 Null，則運算式結果為 Null。  
  
## <a name="expression-examples"></a>運算式範例  
 此範例會執行 **NumberA** 和 **NumberB**資料行之間的位元 AND 運算。 **NumberA** 資料行包含 3 (0000011)，且 **NumberB** 資料行包含 7 (00000111)。  
  
```  
NumberA & NumberB  
```  
  
 運算式評估結果為 3 (00000011)。  
  
 00000011  
  
 00000111  
  
 ----------\-  
  
 00000011  
  
 此範例會執行 **ReorderPoint** 和 **SafetyStockLevel** 資料行之間的位元 AND 運算。  
  
```  
ReorderPoint & SafetyStockLevel  
```  
  
 如果 **ReorderPoint** 為 10，且 **SafetyStockLevel** 為 8，則運算式評估結果為 8 (00001000)。  
  
 00001010  
  
 00001000  
  
 ----------\-  
  
 00001000  
  
 此範例執行兩個整數之間的位元 AND 運算。  
  
```  
3 & 5   
```  
  
 運算式評估結果為 1 (00000001)。  
  
 00000011  
  
 00000101  
  
 ----------\-  
  
 00000001  
  
## <a name="see-also"></a>另請參閱  
 [（& s) （& s)&#40;邏輯 AND&#41; &#40;SSIS 運算式&#41;](logical-and-ssis-expression.md)   
 [運算子優先順序和關聯性](operator-precedence-and-associativity.md)   
 [運算子&#40;SSIS 運算式&#41;](operators-ssis-expression.md)  
  
  
