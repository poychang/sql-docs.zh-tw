---
title: "ERROR_STATE (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ERROR_STATE_TSQL
- ERROR_STATE
dev_langs:
- TSQL
helpviewer_keywords:
- messages [SQL Server], state
- ERROR_STATE function
- errors [SQL Server], state
- TRY...CATCH [SQL Server]
- CATCH block
- states [SQL Server], error numbers
ms.assetid: 6059af00-83fe-409f-ab7c-daad111bc671
caps.latest.revision: 39
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 98b5a1ecfbfd9efd84f8a5cc55454aaaec6f8423
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="errorstate-transact-sql"></a>ERROR_STATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  傳回造成執行 TRY…CATCH 建構之 CATCH 區塊之錯誤的狀態碼。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
-- Syntax for SQL Server, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
ERROR_STATE ( )  
```  
  
## <a name="return-types"></a>傳回類型  
 **int**  
  
## <a name="return-value"></a>傳回值  
 當它在 CATCH 區塊中被呼叫時，會傳回造成執行 CATCH 區塊之錯誤訊息的狀態碼。  
  
 如果是在 CATCH 區塊範圍之外呼叫，便傳回 NULL。  
  
## <a name="remarks"></a>備註  
 在程式碼的多個點，可以產生某些錯誤訊息[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]。 例如，在許多不同情況下，都有可能產生 "1105" 錯誤。 每個產生錯誤的特定狀況，都會指派唯一的狀態碼。  
  
 當檢視已知問題的資料庫時，例如 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 知識庫，您可以利用狀態碼來判斷所記錄的問題，與您遇到的錯誤是否相同。 例如，如果知識庫文件討論狀態為 2 的 1105 錯誤訊息，而您收到的 1105 錯誤訊息的狀態卻是 3，錯誤原因可能不是文章所報告的原因。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支援工程師也可以利用錯誤中的狀態碼，來找出原始程式碼發生錯誤的位置，這也許能提供如何診斷問題的其他想法。  
  
 可以在 CATCH 區塊範圍內的任何位置呼叫 ERROR_STATE。  
  
 ERROR_STATE 不論執行多少次，也不論是在 CATCH 區塊範圍內的任何位置執行，都會傳回錯誤狀態。 這是相較於函式，例如 @@ERROR，這只會傳回錯誤號碼在陳述式之後，立即會造成錯誤，或在 CATCH 區塊的第一個陳述式中。  
  
 在巢狀 CATCH 區塊中，ERROR_STATE 會傳回參考它的 CATCH 區塊範圍特定的錯誤狀態。 例如，外部 TRY...CATCH 建構的 CATCH 區塊可能會有巢狀的 TRY...CATCH 建構。 在巢狀 CATCH 區塊內，ERROR_STATE 會從呼叫巢狀 CATCH 區塊的錯誤傳回狀態。 如果 ERROR_STATE 是在外部 CATCH 區塊內執行，它會從呼叫 CATCH 區塊的錯誤傳回狀態。  
  
## <a name="examples"></a>範例  
  
### <a name="a-using-errorstate-in-a-catch-block"></a>A. 在 CATCH 區塊中使用 ERROR_STATE  
 下列範例顯示將會產生除以零之錯誤的 `SELECT` 陳述式。 它會傳回錯誤的狀態。  
  
```  
BEGIN TRY  
    -- Generate a divide by zero error  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_STATE() AS ErrorState;  
END CATCH;  
GO  
```  
  
### <a name="b-using-errorstate-in-a-catch-block-with-other-error-handling-tools"></a>B. 在含有其他錯誤處理工具的 CATCH 區塊中使用 ERROR_STATE  
 下列範例顯示將會產生除以零之錯誤的 `SELECT` 陳述式。 錯誤的相關訊息會隨同錯誤狀態一起傳回。  
  
```  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT  
        ERROR_NUMBER() AS ErrorNumber,  
        ERROR_SEVERITY() AS ErrorSeverity,  
        ERROR_STATE() AS ErrorState,  
        ERROR_PROCEDURE() AS ErrorProcedure,  
        ERROR_LINE() AS ErrorLine,  
        ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>範例：[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]和[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-errorstate-in-a-catch-block"></a>C. 在 CATCH 區塊中使用 ERROR_STATE  
 下列範例顯示將會產生除以零之錯誤的 `SELECT` 陳述式。 它會傳回錯誤的狀態。  
  
```  
BEGIN TRY  
    -- Generate a divide by zero error  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_STATE() AS ErrorState;  
END CATCH;  
GO  
```  
  
### <a name="d-using-errorstate-in-a-catch-block-with-other-error-handling-tools"></a>D. 在含有其他錯誤處理工具的 CATCH 區塊中使用 ERROR_STATE  
 下列範例顯示將會產生除以零之錯誤的 `SELECT` 陳述式。 錯誤的相關訊息會隨同錯誤狀態一起傳回。  
  
```  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT  
        ERROR_NUMBER() AS ErrorNumber,  
        ERROR_SEVERITY() AS ErrorSeverity,  
        ERROR_STATE() AS ErrorState,  
        ERROR_PROCEDURE() AS ErrorProcedure,  
        ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [sys.messages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)   
 [TRY...CATCH &#40;Transact-SQL&#41;](../../t-sql/language-elements/try-catch-transact-sql.md)   
 [ERROR_LINE &#40;Transact-SQL&#41;](../../t-sql/functions/error-line-transact-sql.md)   
 [ERROR_MESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/error-message-transact-sql.md)   
 [ERROR_NUMBER &#40;Transact-SQL&#41;](../../t-sql/functions/error-number-transact-sql.md)   
 [ERROR_PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/functions/error-procedure-transact-sql.md)   
 [ERROR_SEVERITY &#40;Transact-SQL&#41;](../../t-sql/functions/error-severity-transact-sql.md)   
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [@@ERROR &#40;Transact-SQL&#41;](../../t-sql/functions/error-transact-sql.md)  
  
  

