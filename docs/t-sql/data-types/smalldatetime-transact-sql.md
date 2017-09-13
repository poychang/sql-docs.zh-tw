---
title: "smalldatetime (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 07/22/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- smalldatetime_TSQL
- smalldatetime
dev_langs:
- TSQL
helpviewer_keywords:
- time [SQL Server], data types
- smalldatetime data type [SQL Server]
- dates [SQL Server], data types
- date and time [SQL Server], smalldatetime
- data types [SQL Server], date and time
ms.assetid: 68b74610-d54c-4c8e-b4b2-7e3747546ee0
caps.latest.revision: 50
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 07012d85a54292fa763a7b291d1b7318b6969ca4
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="smalldatetime-transact-sql"></a>smalldatetime (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

定義與當日時間結合的日期。 這個時間是以 24 小時制為基礎，而秒鐘一律為零 (:00) 而且不含小數秒數。
  
> [!NOTE]  
>  使用**時間**，**日期**， **datetime2**和**datetimeoffset**新工作的資料型別。 這些類型符合 SQL 標準。 它們具有方便移植的特性。 **時間**， **datetime2**和**datetimeoffset**提供更多秒數有效位數。 **datetimeoffset**全域部署的應用程式提供時區支援。  
  
## <a name="smalldatetime-description"></a>smalldatetime 描述
  
|||  
|-|-|  
|語法|**smalldatetime**|  
|使用方式|宣告@MySmalldatetime **smalldatetime**<br /><br /> 建立資料表 Table1 (Column1 **smalldatetime** )|  
|預設的字串常值格式<br /><br /> (用於下層用戶端)|不適用|  
|日期範圍|1900-01-01 到 2079-06-06<br /><br /> 1900 年 1 月 1 日到 2079 年 6 月 6 日|  
|時間範圍|00:00:00 到 23:59:59<br /><br /> 2007-05-09 23:59:59 會四捨五入為<br /><br /> 2007-05-10 00:00:00|  
|元素範圍|YYYY 是代表年份的四位數，範圍介於 1900 至 2079 之間。<br /><br /> MM 是代表指定年份中某個月份的兩位數，範圍介於 01 至 12 之間。<br /><br /> DD 是代表指定月份中某個日期的兩位數，範圍介於 01 至 31 之間 (視月份而定)。<br /><br /> hh 是代表小時的兩位數，範圍介於 00 至 23 之間。<br /><br /> mm 是代表分鐘的兩位數，範圍介於 00 至 59 之間。<br /><br /> ss 是代表秒鐘的兩位數，範圍介於 00 至 59 之間。 29.998 秒或以下的值會向下捨入到最接近的分鐘，而 29.999 秒或以上的值會向上捨入到最接近的分鐘。|  
|字元長度|19 個位置上限|  
|儲存體大小|4 個位元組 (固定)。|  
|精確度|一分鐘|  
|預設值|1900-01-01 00:00:00|  
|日曆|西曆<br /><br /> (不含年份的完整範圍)。|  
|使用者自訂的小數秒數有效位數|否|  
|時區位移感知和保留|否|  
|日光節約感知|否|  
  
## <a name="ansi-and-iso-8601-compliance"></a>ANSI 和 ISO 8601 標準  
**smalldatetime**不符合 ANSI 或 ISO 8601 相容。
  
## <a name="converting-date-and-time-data"></a>將日期和時間資料轉換
當您轉換成日期與時間資料類型時，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會拒絕所有無法辨識為日期或時間的值。 使用 CAST 和 CONVERT 函數與日期和時間資料的相關資訊，請參閱[CAST 和 CONVERT &#40;TRANSACT-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md).
  
### <a name="converting-smalldatetime-to-other-date-and-time-types"></a>將 smalldatetime 轉換成其他日期和時間類型
本章節描述發生的狀況時**smalldatetime**資料類型已轉換成其他日期和時間資料類型。
  
在轉換成**日期**，年、 月和日都會複製。 下列程式碼顯示將 `smalldatetime` 值轉換成 `date` 值的結果。
  
```sql
DECLARE @smalldatetime smalldatetime = '1955-12-13 12:43:10';  
DECLARE @date date = @smalldatetime  
  
SELECT @smalldatetime AS '@smalldatetime', @date AS 'date';  
  
--Result  
--@smalldatetime          date  
------------------------- ----------  
--1955-12-13 12:43:00     1955-12-13  
--  
--(1 row(s) affected)  
```  
  
當轉換為**time （n)**，會複製時、 分、 秒數。 小數秒數會設定為 0。 下列程式碼顯示將 `smalldatetime` 值轉換成 `time(4)` 值的結果。
  
```sql
DECLARE @smalldatetime smalldatetime = '1955-12-13 12:43:10';  
DECLARE @time time(4) = @smalldatetime;  
  
SELECT @smalldatetime AS '@smalldatetime', @time AS 'time';  
  
--Result  
--@smalldatetime          time  
------------------------- -------------  
--1955-12-13 12:43:00     12:43:00.0000  
--  
--(1 row(s) affected)  
```  
  
當轉換為**datetime**、 **smalldatetime**值複製到**datetime**值。 小數秒數會設定為 0。 下列程式碼顯示將 `smalldatetime` 值轉換成 `datetime` 值的結果。
  
```sql
DECLARE @smalldatetime smalldatetime = '1955-12-13 12:43:10';  
DECLARE @datetime datetime = @smalldatetime;  
  
SELECT @smalldatetime AS '@smalldatetime', @datetime AS 'datetime';  
  
--Result  
--@smalldatetime          datetime  
------------------------- -----------------------  
--1955-12-13 12:43:00     1955-12-13 12:43:00.000  
--  
--(1 row(s) affected)  
```  
  
在轉換成**datetimeoffset （n)**、 **smalldatetime**值複製到**datetimeoffset （n)**值。 小數秒數會設定為 0，而時區時差會設定為 +00:0。 下列程式碼顯示將 `smalldatetime` 值轉換成 `datetimeoffset(4)` 值的結果。
  
```sql
DECLARE @smalldatetime smalldatetime = '1955-12-13 12:43:10';  
DECLARE @datetimeoffset datetimeoffset(4) = @smalldatetime;  
  
SELECT @smalldatetime AS '@smalldatetime', @datetimeoffset AS 'datetimeoffset(4)';  
  
--Result  
--@smalldatetime          datetimeoffset(4)  
------------------------- ------------------------------  
--1955-12-13 12:43:00     1955-12-13 12:43:00.0000 +00:0  
--  
--(1 row(s) affected)  
```  
  
要轉換**datetime2**、 **smalldatetime**值複製到**datetime2**值。 小數秒數會設定為 0。 下列程式碼顯示將 `smalldatetime` 值轉換成 `datetime2(4)` 值的結果。
  
```sql
DECLARE @smalldatetime smalldatetime = '1955-12-13 12:43:10';  
DECLARE @datetime2 datetime2(4) = @smalldatetime;  
  
SELECT @smalldatetime AS '@smalldatetime', @datetime2 AS ' datetime2(4)';  
  
--Result  
--@smalldatetime           datetime2(4)  
------------------------- ------------------------  
--1955-12-13 12:43:00     1955-12-13 12:43:00.0000  
--  
--(1 row(s) affected)  
```  
  
## <a name="examples"></a>範例  
  
### <a name="a-casting-string-literals-with-seconds-to-smalldatetime"></a>A. 將包含秒數的字串常值轉換成 smalldatetime  
下列範例會比較將字串常值中的秒數轉換成 `smalldatetime` 的結果。
  
```sql
SELECT   
     CAST('2007-05-08 12:35:29'     AS smalldatetime)  
    ,CAST('2007-05-08 12:35:30'     AS smalldatetime)  
    ,CAST('2007-05-08 12:59:59.998' AS smalldatetime);  
```  
  
|輸入|輸出|  
|---|---|
|2007-05-08 12:35:29|2007-05-08 12:35:00|  
|2007-05-08 12:35:30|2007-05-08 12:36:00|  
|2007-05-08 12:59:59.998|2007-05-08 13:00:00|  
  
### <a name="b-comparing-date-and-time-data-types"></a>B. 比較 date 和 time 資料類型  
下列範例會比較將字串轉換成各種 date 與 time 資料類型的結果。
  
```sql
SELECT   
     CAST('2007-05-08 12:35:29. 1234567 +12:15' AS time(7)) AS 'time'   
    ,CAST('2007-05-08 12:35:29. 1234567 +12:15' AS date) AS 'date'   
    ,CAST('2007-05-08 12:35:29.123' AS smalldatetime) AS   
        'smalldatetime'   
    ,CAST('2007-05-08 12:35:29.123' AS datetime) AS 'datetime'   
    ,CAST('2007-05-08 12:35:29. 1234567 +12:15' AS datetime2(7)) AS   
        'datetime2'  
    ,CAST('2007-05-08 12:35:29.1234567 +12:15' AS datetimeoffset(7)) AS   
        'datetimeoffset';  
```  
  
|資料類型|輸出|  
|---|---|
|**time**|12:35:29. 1234567|  
|**date**|2007-05-08|  
|**smalldatetime**|2007-05-08 12:35:00|  
|**datetime**|2007-05-08 12:35:29.123|  
|**datetime2**|2007-05-08 12:35:29. 1234567|  
|**datetimeoffset**|2007-05-08 12:35:29.1234567 +12:15|  
  
## <a name="see-also"></a>另請參閱
[CAST 和 CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  
