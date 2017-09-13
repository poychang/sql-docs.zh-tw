---
title: "SET ANSI_NULL_DFLT_OFF (TRANSACT-SQL) |Microsoft 文件"
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
- ANSI_NULL_DFLT_OFF_TSQL
- ANSI_NULL_DFLT_OFF
- SET ANSI_NULL_DFLT_OFF
- SET_ANSI_NULL_DFLT_OFF_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- default nullability
- ANSI_NULL_DFLT_OFF option
- null values [SQL Server], overriding
- overriding default nullability
- SET ANSI_NULL_DFLT_OFF statement
ms.assetid: 8ed5c512-f5de-4741-a18a-de85a3041295
caps.latest.revision: 27
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1eeb95a4fdeb8e0db5ed08f3f5728a38f512bc2f
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="set-ansinulldfltoff-transact-sql"></a>SET ANSI_NULL_DFLT_OFF (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  改變資料庫的 ANSI null default 選項時，覆寫新資料行的預設 null 屬性的工作階段的行為**true**。 如需有關設定 ANSI null 預設值的詳細資訊，請參閱[ALTER DATABASE &#40;TRANSACT-SQL &#41;](../../t-sql/statements/alter-database-transact-sql.md).  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
SET ANSI_NULL_DFLT_OFF { ON | OFF }  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
SET ANSI_NULL_DFLT_OFF OFF  
```  
  
## <a name="remarks"></a>備註  
 這項設定只在 CREATE TABLE 和 ALTER TABLE 陳述式未指定新資料行的 Null 屬性時，才會影響新資料行的 Null 屬性設定。 依預設，當 SET ANSI_NULL_DFLT_OFF 是 ON 時，如果未明確指定資料行的 Null 屬性狀態，ALTER TABLE 和 CREATE TABLE 陳述式所建立的新資料行是 NOT NULL。 SET ANSI_NULL_DFLT_OFF 不會影響利用明確的 NULL 或 NOT NULL 來建立的資料行。  
  
 SET ANSI_NULL_DFLT_OFF 和 SET ANSI_NULL_DFLT_ON 不能同時設為 ON。 如果一個選項設為 ON，另一個選項便設為 OFF。 因此，您可以將 ANSI_NULL_DFLT_OFF 或 SET ANSI_NULL_DFLT_ON 設為 ON，也可以同時將它們設為 OFF。 如果任何一個選項是 ON，這項設定 (SET ANSI_NULL_DFLT_OFF 或 SET ANSI_NULL_DFLT_ON) 就會生效。 如果這兩個選項都設為 OFF，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用中的 is_ansi_null_default_on 資料行的值[sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)目錄檢視。  
  
 如果希望在資料庫中搭配不同 Null 屬性設定來使用的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼作業比較可靠，最好是一律在 CREATE TABLE 和 ALTER TABLE 陳述式中指定 NULL 或 NOT NULL。  
  
 SET ANSI_NULL_DFLT_OFF 的設定是在執行階段進行設定，而不是在剖析階段進行設定。  
  
 若要檢視此設定的目前設定，請執行下列查詢。  
  
```  
DECLARE @ANSI_NULL_DFLT_OFF VARCHAR(3) = 'OFF';  
IF ( (2048 & @@OPTIONS) = 2048 ) SET @ANSI_NULL_DFLT_OFF = 'ON';  
SELECT @ANSI_NULL_DFLT_OFF AS ANSI_NULL_DFLT_OFF;  
  
```  
  
## <a name="permissions"></a>Permissions  
 需要 public 角色中的成員資格。  
  
## <a name="examples"></a>範例  
 下列範例會顯示含有兩種 ANSI null default 資料庫選項設定之 `SET ANSI_NULL_DFLT_OFF` 的效果。  
  
```  
USE AdventureWorks2012;  
GO  
  
-- Set the 'ANSI null default' database option to true by executing   
-- ALTER DATABASE.  
GO  
ALTER DATABASE AdventureWorks2012 SET ANSI_NULL_DEFAULT ON;  
GO  
-- Create table t1.  
CREATE TABLE t1 (a TINYINT);  
GO  
-- NULL INSERT should succeed.  
INSERT INTO t1 (a) VALUES (NULL);  
GO  
  
-- SET ANSI_NULL_DFLT_OFF to ON and create table t2.  
SET ANSI_NULL_DFLT_OFF ON;  
GO  
CREATE TABLE t2 (a TINYINT);  
GO   
-- NULL INSERT should fail.  
INSERT INTO t2 (a) VALUES (NULL);  
GO  
  
-- SET ANSI_NULL_DFLT_OFF to OFF and create table t3.  
SET ANSI_NULL_DFLT_OFF OFF;  
GO  
CREATE TABLE t3 (a TINYINT) ;  
GO   
-- NULL INSERT should succeed.  
INSERT INTO t3 (a) VALUES (NULL);  
GO  
  
-- This illustrates the effect of having both the database  
-- option and SET option disabled.  
-- Set the 'ANSI null default' database option to false.  
ALTER DATABASE AdventureWorks2012 SET ANSI_NULL_DEFAULT OFF;  
GO  
-- Create table t4.  
CREATE TABLE t4 (a tinyint) ;  
GO   
-- NULL INSERT should fail.  
INSERT INTO t4 (a) VALUES (null);  
GO  
  
-- SET ANSI_NULL_DFLT_OFF to ON and create table t5.  
SET ANSI_NULL_DFLT_OFF ON;  
GO  
CREATE TABLE t5 (a tinyint);  
GO   
-- NULL insert should fail.  
INSERT INTO t5 (a) VALUES (null);  
GO  
  
-- SET ANSI_NULL_DFLT_OFF to OFF and create table t6.  
SET ANSI_NULL_DFLT_OFF OFF;  
GO  
CREATE TABLE t6 (a tinyint);   
GO   
-- NULL insert should fail.  
INSERT INTO t6 (a) VALUES (null);  
GO  
  
-- Drop tables t1 through t6.  
DROP TABLE t1, t2, t3, t4, t5, t6;  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [SET 陳述式 &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET ANSI_NULL_DFLT_ON &#40;TRANSACT-SQL &#41;](../../t-sql/statements/set-ansi-null-dflt-on-transact-sql.md)  
  
  