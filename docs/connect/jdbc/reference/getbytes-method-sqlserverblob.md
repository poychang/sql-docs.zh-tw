---
title: getBytes 方法 (SQLServerBlob) |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerBlob.getBytes
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: bea1b810-b5c1-466d-bdc4-561468214632
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7a872d042c0a96123cccffac5c5a6f8e2b686c4d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32830869"
---
# <a name="getbytes-method-sqlserverblob"></a>getBytes 方法 (SQLServerBlob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  取得 BLOB 資料來當做位元組陣列。  
  
## <a name="syntax"></a>語法  
  
```  
  
public byte[] getBytes(long pos,  
                       int length)  
```  
  
#### <a name="parameters"></a>參數  
 *pos*  
  
 開始位置，從 1 (而不是 0) 開始。  
  
 *長度*  
  
 要取得的資料長度。  
  
## <a name="return-value"></a>傳回值  
 A**位元組**陣列，其中包含所要求的資料。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 這個 getBytes 方法是由 java.sql.Blob 介面中 getBytes 方法指定。  
  
 如果您擁有為 null 或零長度的 BLOB，並嘗試在位置 1，空取得剛好零個位元組**位元組**則會傳回陣列 （長度為 0 的位元組陣列）。  
  
 如果您擁有長度為 null 或零的 BLOB，而且嘗試在位置 1 以外的位置取得任何位元組長度，則會擲回位置例外狀況。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerBlob 方法](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [SQLServerBlob 成員](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [SQLServerBlob 類別](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
