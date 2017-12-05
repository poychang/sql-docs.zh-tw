---
title: "sys.sysconfigures (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sysconfigures
- sysconfigures
- sys.sysconfigures_TSQL
- sysconfigures_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sys.sysconfigures compatibility view
- sysconfigures system table
ms.assetid: 146bf10a-c898-4676-a2a1-673fb1cee7a2
caps.latest.revision: "39"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4e2151437e11f60107ddbe2cbfc64cc1b6f155df
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/27/2017
---
# <a name="syssysconfigures-transact-sql"></a>sys.sysconfigures (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  針對使用者所設定的每個組態選項，各包含一個資料列。 **sysconfigures**包含最近啟動之前所定義的組態選項[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，加上設定的任何動態組態選項。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**值**|**int**|使用者可以修改的變數值。 只有在執行 RECONFIGURE 時，[!INCLUDE[ssDE](../../includes/ssde-md.md)] 才會使用這個項目。|  
|**組態**|**int**|組態變數號碼。|  
|**註解**|**nvarchar(255)**|組態選項的說明。|  
|**status**|**smallint**|指示選項狀態的點陣圖。 可能的值如下：<br /><br /> 0 = 靜態。 設定在伺服器重新啟動時生效。<br /><br /> 1 = 動態。 變數在執行 RECONFIGURE 陳述式時生效。<br /><br /> 2 = 進階。 會顯示變數時，才**顯示進階選項**設定。 設定在伺服器重新啟動時生效。<br /><br /> 3 = 動態和進階。|  
  
## <a name="see-also"></a>請參閱  
 [將系統資料表對應至系統檢視 &#40;TRANSACT-SQL &#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [相容性檢視 &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  