---
title: FILESTREAM DDL、函式、預存程序和檢視 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
ms.assetid: 9ecb49ee-f64e-4d30-a803-e4064a21950a
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7ec7d554c8dedd2fb48d1af8a44dbee550e376ef
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48189848"
---
# <a name="filestream-ddl-functions-stored-procedures-and-views"></a>FILESTREAM DDL、函數、預存程序和檢視表
  列出支援 FILESTREAM 的 Transact-SQL 陳述式和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫物件。  
  
 如需支援 FileTable 功能的資料庫物件清單，請參閱＜ [FileTable DDL, Functions, Stored Procedures, and Views](../views/views.md)＞。  
  
##  <a name="ddl"></a> Transact-SQL 資料定義語言 (DDL) 陳述式  
  
-   [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
-   [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)  
  
-   [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql)  
  
-   [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)  
  
-   [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)  
  
-   [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)DROP INDEX  
  
##  <a name="func"></a> 系統函數  
  
-   [GET_FILESTREAM_TRANSACTION_CONTEXT &#40;Transact-SQL&#41;](/sql/t-sql/functions/get-filestream-transaction-context-transact-sql)  
  
-   [PathName &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/pathname-transact-sql)  
  
##  <a name="proc"></a> 系統預存程序  
  
-   [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
-   [sp_filestream_force_garbage_collection &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/filestream-and-filetable-sp-filestream-force-garbage-collection)  
  
##  <a name="cat"></a> 系統檢視表 - 目錄檢視  
  
-   [sys.database_filestream_options &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql)  
  
##  <a name="dmv"></a> 系統檢視表 - 動態管理檢視  
  
-   [sys.dm_filestream_file_io_handles &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-filestream-file-io-handles-transact-sql)  
  
-   [sys.dm_filestream_file_io_requests &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-filestream-file-io-requests-transact-sql)  
  
##  <a name="api"></a> 程式設計 API  
  
-   [使用 OpenSqlFilestream 存取 FILESTREAM 資料](access-filestream-data-with-opensqlfilestream.md)  
  
-   [Managed API - SqlFileStream 類別](http://go.microsoft.com/fwlink/?LinkId=220875)  
  
  
