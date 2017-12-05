---
title: "sp_releaseapplock (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_releaseapplock_TSQL
- sp_releaseapplock
dev_langs: TSQL
helpviewer_keywords: sp_releaseapplock
ms.assetid: 51b03c2f-0d54-40f5-9172-e747942d4a46
caps.latest.revision: "20"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5eb17b39125209ca15214356e84f832e2f8cbc73
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/27/2017
---
# <a name="spreleaseapplock-transact-sql"></a>sp_releaseapplock (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  釋放應用程式資源的鎖定。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_releaseapplock [ @Resource = ] 'resource_name'   
     [ , [ @LockOwner = ] 'lock_owner' ]  
     [ , [ @DbPrincipal = ] 'database_principal' ]  
[ ; ]  
```  
  
## <a name="arguments"></a>引數  
 [ @Resource=] '*resource_name*'  
 這是用戶端應用程式所指定的鎖定資源名稱。 應用程式必須確定資源是唯一的。 指定的名稱會在內部雜湊成可儲存在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 鎖定管理員中的值。 *resource_name*是**nvarchar （255)**沒有預設值。 *resource_name*是二進位來比較，因此會區分大小寫，不論目前資料庫的定序設定為何。  
  
 [ @LockOwner=] '*lock_owner*'  
 已鎖定，這是擁有者*lock_owner*要求鎖定時的值。 *lock_owner*是**nvarchar （32)**。 這個值可以是**交易**（預設值） 或**工作階段**。 當*lock_owner*值是**交易**，依預設或明確地指定 sp_getapplock 必須從交易內執行。  
  
 [ @DbPrincipal=] '*database_principal*'  
 這是擁有資料庫中物件權限的使用者、角色或應用程式角色。 函式的呼叫端必須是成員*database_principal*、 dbo 或 db_owner 固定資料庫角色，才能成功呼叫函數。 預設值是 public。  
  
## <a name="return-code-values"></a>傳回碼值  
 \>= 0 （成功） 或 < 0 （失敗）  
  
|值|結果|  
|-----------|------------|  
|0|鎖定釋放成功。|  
|-999|表示參數驗證或其他呼叫錯誤。|  
  
## <a name="remarks"></a>備註  
 當應用程式針對相同鎖定資源來重複呼叫 sp_getapplock 時，也必須呼叫 sp_releaseapplock 相同次數，以便釋出鎖定。  
  
 當因故關閉伺服器時，會釋放鎖定。  
  
## <a name="permissions"></a>Permissions  
 需要 public 角色中的成員資格。  
  
## <a name="examples"></a>範例  
 下列範例會釋放 `Form1` 資料庫中 `AdventureWorks2012` 資源目前交易的相關聯鎖定。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_getapplock @DbPrincipal = 'dbo', @Resource = 'Form1',   
     @LockMode = 'Shared';  
EXEC sp_releaseapplock @DbPrincipal = 'dbo', @Resource = 'Form1';  
GO  
```  
  
## <a name="see-also"></a>請參閱  
 [APPLOCK_MODE &#40;TRANSACT-SQL &#41;](../../t-sql/functions/applock-mode-transact-sql.md)   
 [APPLOCK_TEST &#40;TRANSACT-SQL &#41;](../../t-sql/functions/applock-test-transact-sql.md)   
 [sp_getapplock &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/sp-getapplock-transact-sql.md)  
  
  