---
title: "&lt;= （小於或等於） (MDX) |Microsoft 文件"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- <=
dev_langs:
- kbMDX
helpviewer_keywords:
- <= (less than or equal to operator)
- less than or equal to operator (<=)
ms.assetid: 6c805c68-cf9d-48ca-a00b-2ef9ade89b0a
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: d7c4f714a78223afb9bdd1309eea9835b3e2bfc3
ms.contentlocale: zh-tw
ms.lasthandoff: 08/02/2017

---
# <a name="lt-less-than-or-equal-to-mdx"></a>&lt;= （小於或等於） (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  執行比對作業，判定某個多維度運算式 (MDX) 運算式的值是否小於或等於另一個 MDX 運算式的值。  
  
## <a name="syntax"></a>語法  
  
```  
  
MDX_Expression <= MDX_Expression  
```  
  
#### <a name="parameters"></a>參數  
 *MDX_Expression*  
 有效的 MDX 運算式。  
  
## <a name="return-value"></a>傳回值  
 布林值根據以下條件而定：  
  
-   t**rue**如果這兩個參數都為非 null，而且第一個參數可能的值小於或等於第二個參數的值。  
  
-   f**alse**如果這兩個參數都為非 null，而且第一個參數的值可大於第二個參數的值。  
  
-   Null，如果有一個參數或兩個參數都評估為 Null 值。  
  
## <a name="examples"></a>範例  
 以下範例示範此運算子的用法。  
  
```  
-- This query returns the gross profit margin (GPM)  
-- for Australia where the GPM is less than or equal to 30%.  
With Member [Measures].[LowGPM] as  
  IIF(  
      [Measures].[Gross Profit Margin] <= .5,  
      [Measures].[Gross Profit Margin],  
      null)  
SELECT   
NON EMPTY [Sales Territory].[Sales Territory Country].[Australia] ON 0,  
    NON EMPTY [Product].[Category].Members ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[LowGPM])  
```  
  
## <a name="see-also"></a>另請參閱  
 [MDX 運算子參考 &#40;MDX &#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
