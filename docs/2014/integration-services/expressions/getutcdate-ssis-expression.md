---
title: GETUTCDATE (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], GETUTCDATE
- current date
- UTC time
- GETUTCDATE function
ms.assetid: 2282339c-c24f-493e-8e66-181ea8af5ad0
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d266d5c329776279f21dfbfdaa51a823f460a407
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48087098"
---
# <a name="getutcdate-ssis-expression"></a>GETUTCDATE (SSIS 運算式)
  使用 DT_DBTIMESTAMP 格式，傳回 UTC 時間格式 (世界標準時間或格林威治標準時間) 的系統目前日期。 GETUTCDATE 函數不接受引數。  
  
## <a name="syntax"></a>語法  
  
```  
  
GETUTCDATE()  
```  
  
## <a name="arguments"></a>引數  
 None  
  
## <a name="result-types"></a>結果類型  
 DT_DBTIMESTAMP  
  
## <a name="expression-examples"></a>運算式範例  
 此範例會傳回 UTC 時間格式的目前日期之年份。  
  
```  
DATEPART("year",GETUTCDATE())  
```  
  
 此範例會傳回 **ModifiedDate** 資料行中的日期與目前 UTC 日期之間的天數。  
  
```  
DATEDIFF("dd",ModifiedDate,GETUTCDATE())  
```  
  
 此範例會將目前的 UTC 日期加上三個月。  
  
```  
DATEADD("Month",3,GETUTCDATE())  
```  
  
## <a name="see-also"></a>另請參閱  
 [GETDATE &#40;SSIS 運算式&#41;](getdate-ssis-expression.md)   
 [函式&#40;SSIS 運算式&#41;](functions-ssis-expression.md)  
  
  
