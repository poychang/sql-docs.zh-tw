---
title: SQLGetTypeInfo | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetTypeInfo function
ms.assetid: 13b982c3-ae03-4155-bc0d-e225050703ce
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cc2287678e7fd3e481c3eaf1d33af64e9ea7dad8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48186078"
---
# <a name="sqlgettypeinfo"></a>SQLGetTypeInfo
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式報告一組結果中的其他資料行 USERTYPE `SQLGetTypeInfo`。 USERTYPE 會報告 DB-Library 資料類型定義，而且對於將現有 DB-Library 應用程式移植至 ODBC 的開發人員很有用。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會將識別視為屬性，而 ODBC 則會將它視為資料類型。 若要解決此不相符，`SQLGetTypeInfo`傳回的資料類型： **intidentity**， **smallintidentity**， **tinyintidentity**， **decimalidentity**，並**numericidentity**。 `SQLGetTypeInfo`結果集資料行 auto_unique_value 會回報這些資料類型的值為 TRUE。  
  
 針對**varchar**， **nvarchar**並**varbinary**，則[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client ODBC 驅動程式會繼續針對 COLUMN_SIZE 分別報告 8000、 4000 和 8000值，即使實際上沒有限制。 這為了確保回溯相容性。  
  
 針對**xml**資料類型， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式針對 COLUMN_SIZE 報告 SQL_SS_LENGTH_UNLIMITED 指出大小沒有限制。  
  
## <a name="sqlgettypeinfo-and-table-valued-parameters"></a>SQLGetTypeInfo 和資料表值參數  
 資料表值參數的資料表類型實際上就是中繼類型，亦即，用來定義其他類型的類型。 因此，它沒有透過 SQLGetTypeInfo 公開。 應用程式必須使用 SQLTables，而不是 SQLGetTypeInfo，來擷取資料表值參數搭配使用的資料表類型的中繼資料。  
  
 如需詳細資訊，關於擷取之中繼資料的資料表值參數，請參閱[陳述式屬性該 Affect Table-Valued 參數](../native-client-odbc-table-valued-parameters/statement-attributes-that-affect-table-valued-parameters.md)。  
  
 如需有關資料表值參數的詳細資訊，請參閱 < [Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)。  
  
## <a name="sqlgettypeinfo-support-for-enhanced-date-and-time-features"></a>增強型日期和時間功能的 SQLGetTypeInfo 支援  
 針對日期/時間類型傳回值，請參閱[Catalog Metadata](../native-client-odbc-date-time/metadata-catalog.md)。  
  
 如需詳細資訊，請參閱 <<c0> [ 日期和時間改善&#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)。</c0>  
  
## <a name="sqlgettypeinfo-support-for-large-clr-udts"></a>大型 CLR UDT 的 SQLGetTypeInfo 支援  
 `SQLGetTypeInfo` 支援大型 CLR 使用者定義型別 (UDT)。 如需詳細資訊，請參閱 < [Large CLR User-Defined 類型&#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md)。  
  
## <a name="see-also"></a>另請參閱  
 [SQLGetTypeInfo 函數](http://go.microsoft.com/fwlink/?LinkId=59356)   
 [ODBC API 實作詳細資料](odbc-api-implementation-details.md)  
  
  
