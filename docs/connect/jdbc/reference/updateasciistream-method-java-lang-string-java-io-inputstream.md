---
title: updateAsciiStream 方法 (java.io.InputStream) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 747b0308-1ce6-4eba-bdfc-af29c21c18cf
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b5e6c7507319d712f54dcef90f3358b13066a346
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47810096"
---
# <a name="updateasciistream-method-javalangstring-javaioinputstream"></a>updateAsciiStream 方法 (java.lang.String, java.io.InputStream)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  使用 ASCII 資料流值，更新指定的資料行。  
  
## <a name="syntax"></a>語法  
  
```  
  
public void updateAsciiStream(java.lang.String columnLabel,  
                              java.io.InputStream x)  
```  
  
#### <a name="parameters"></a>參數  
 *columnLabel*  
  
 **String**，包含資料行標籤。  
  
 *x*  
  
 InputStream 物件。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 這個 updateAsciiStream 方法是由 java.sql.ResultSet 介面中的 updateAsciiStream 方法指定。  
  
 這個方法會從 InputStream 物件，將 ASCII 字元 (位元組) 傳遞到可轉換的字元資料行，這些是 Unicode 的 ASCII 範圍 [0x00 – 0x7F]，以及 874、932、936、949、950 和 1250 到 1258 的字碼頁。 這個方法會執行轉換，直到目的地定序頁面。 嘗試更新無法轉換的目的地資料行，將擲回例外狀況。 若是處理二進位資料行，則會傳遞未經處理位元組。  
  
 使用這個方法來**映像**，**文字**，並**ntext** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]資料型別可能會影響效能。  
  
## <a name="see-also"></a>另請參閱  
 [updateAsciiStream 方法 &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md)   
 [SQLServerResultSet 成員](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 類別](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
