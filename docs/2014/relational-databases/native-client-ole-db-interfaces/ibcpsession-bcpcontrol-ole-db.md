---
title: 'Ibcpsession:: Bcpcontrol (OLE DB) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- IBCPSession::BCPControl (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPControl method
ms.assetid: d58f3fe1-45e3-4e46-8e9c-000971829d99
caps.latest.revision: 49
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f1e1d13ff0d31dee51eacaaffe71e5b4a53e1b24
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37408437"
---
# <a name="ibcpsessionbcpcontrol-ole-db"></a>IBCPSession::BCPControl (OLE DB)
  設定大量複製作業的選項。  
  
## <a name="syntax"></a>語法  
  
```  
  
HRESULT BCPControl(   
inteOption,  
void *iValue);  
```  
  
## <a name="remarks"></a>備註  
 **BCPControl**方法會設定各種大量複製作業，包括取消大量複製，若要從資料檔和批次大小複製的第一個和最後一個資料列的數字之前所允許的錯誤號碼的控制參數。  
  
 當從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 大量複製資料時，這個方法也可用於指定要使用的 SELECT 陳述式。 您可以設定`eOption`引數為 BCP_OPTION_HINTS 和`iValue`具有指向寬字元字串，包含 SELECT 陳述式的引數。  
  
 可能值為*eOption*是：  
  
|選項|描述|  
|------------|-----------------|  
|BCP_OPTION_ABORT|停止已經進行的大量複製作業。 您可以呼叫**BCPControl**方法*eOption*用 bcp_option_abort 的引數，從另一個執行緒停止執行的大量複製作業。 *IValue*引數會被忽略。|  
|BCP_OPTION_BATCH|每一批次中的資料列數目。 預設值為 0，表示資料擷取時，會指出資料表中的所有資料列，或資料複製到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時，會指出使用者資料檔案中的所有資料列。 小於 1 的值會將 BCP_OPTION_BATCH 重設為預設值。|  
|BCP_OPTION_DELAYREADFMT|布林值，如果設定為 true，會導致[ibcpsession:: Bcpreadfmt](ibcpsession-bcpreadfmt-ole-db.md)若要在執行時讀取。 如果為 false （預設值），ibcpsession:: Bcpreadfmt 會立即讀取格式檔案。 如果會發生順序錯誤`BCP_OPTION_DELAYREADFMT`是 true，並且呼叫 ibcpsession:: Bcpcolumns 或 ibcpsession:: Bcpcolfmt。<br /><br /> 如果您呼叫，也會發生順序錯誤`IBCPSession::BCPControl(BCPDELAYREADFMT, (void *)FALSE))`之後呼叫`IBCPSession::BCPControl(BCPDELAYREADFMT, (void *)TRUE)`和 ibcpsession:: Bcpwritefmt。<br /><br /> 如需詳細資訊，請參閱 <<c0> [ 中繼資料探索](../native-client/features/metadata-discovery.md)。|  
|BCP_OPTION_FILECP|*IValue*引數中包含的資料檔案的字碼頁數目。 您可以指定程式碼頁面的數目，例如 1252 或 850，或以下任一個值：<br /><br /> -BCP_FILECP_ACP： 檔案中的資料是在用戶端的 Microsoft Windows® 字碼頁。<br />-BCP_FILECP_OEMCP： 檔案中的資料是在用戶端 （預設值） 的 OEM 字碼頁。<br />-BCP_FILECP_RAW： 檔案中的資料位於的字碼頁[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。|  
|BCP_OPTION_FILEFMT|資料檔案格式的版本號碼。 這個號碼可以是 80 ([!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)])、90 ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)])、100 ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 或 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)])、110 ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) 或 120 ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)])。 120 是預設值。 這個值在使用舊版伺服器支援的格式匯出和匯入資料時非常實用。  比方說，若要匯入資料取自中的文字資料行[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]伺服器**varchar （max)** 中的資料行[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]或更新版本的伺服器，您應該指定 80。 同樣地，如果您匯出資料時指定 80 **varchar （max)** 資料行，它會儲存就像文字資料行就會存入[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]格式，且可以匯入的文字資料行[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]伺服器。|  
|BCP_OPTION_FIRST|要複製的檔案或資料表的資料列。 預設值為 1，小於 1 的值會將這個選項重設為預設。|  
|BCP_OPTION_FIRSTEX|如果是 BCP Out 作業，則指定將資料庫資料表第一個資料列複製到資料檔案中。<br /><br /> 如果是 BCP In 作業，則指定將資料檔案的第一個資料列複製到資料庫資料表中。<br /><br /> *IValue*參數必須是帶正負號的 64 位元整數，其中包含值的位址。 可傳遞至 BCPFIRSTEX 的最大值為 2^63-1。|  
|BCP_OPTION_FMTXML|用於指定所產生的格式檔案應該是 XML 格式。 根據預設，這個選項是關閉的，而且格式檔案會儲存為文字檔案。 XML 格式檔案提供更大的彈性，但是有一些條件約束。 例如，您不可以同時指定欄位的前置詞和結束字元，即使在更早版本中是可以這麼做的。 **注意：** 僅限 XML 格式檔案時，支援[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]連同安裝工具[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]原生用戶端。|  
|BCP_OPTION_HINTS|*IValue*引數包含寬字元字串指標。 定址的字串會指定處理提示的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 大量複製或傳回結果集的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。 如果 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式指定為傳回一個以上的結果集，則第一個結果集之後的所有結果集都會被忽略。|  
|BCP_OPTION_KEEPIDENTITY|當*iValue*引數設定為 TRUE，此選項可讓您指定大量複製方法插入的資料值提供給[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]身分識別條件約束所定義的資料行。 輸入檔案必須提供識別資料行的值。 如果沒有設定，就會為插入的資料列產生新的識別值。 檔案中屬於識別欄位的所有資料都會被忽略。|  
|BCP_OPTION_KEEPNULLS|指定檔案中的空資料值在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表中是否會轉換為 NULL 值。 當*iValue*引數設定為 TRUE，會將空的值轉換為中的 NULL[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料表。 預設是將空的值轉換為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表中資料行的預設值 (如果有預設值的話)。|  
|BCP_OPTION_LAST|要複製的最後一個資料列。 預設為複製所有資料列。 小於 1 的值會將這個選項重設為預設。|  
|BCP_OPTION_LASTEX|如果是 BCP Out 作業，則指定將資料庫資料表最後一個資料列複製到資料檔案中。<br /><br /> 如果是 BCP In 作業，則指定將資料檔案的最後一個資料列複製到資料庫資料表中。<br /><br /> *IValue*參數必須是帶正負號的 64 位元整數，其中包含值的位址。 可傳遞至 BCPLASTEX 的最大值是 2^63-1。|  
|BCP_OPTION_MAXERRS|在大量複製作業失敗之前，允許發生錯誤的數目。 預設值是 10。 小於 1 的值會將這個選項重設為預設。 大量複製會限制 65,535 個錯誤的上限。 如果嘗試將這個選項設為大於 65,535 的值，則該選項會設定為 65,535。|  
|BCP_OPTION_ROWCOUNT|傳回受到目前 (或最近) BCP 作業影響的資料列數目。|  
|BCP_OPTION_TEXTFILE|資料檔案不是二進位檔案，而是文字檔案 BCP 會藉由檢查資料檔案中前 2 個位元組中的 Unicode 位元組標記，偵測文字檔案是否為 Unicode 檔案格式。|  
|BCP_OPTION_UNICODEFILE|當設定為 TRUE 時，這個選項會指定輸入檔案為 Unicode 檔案格式。|  
  
## <a name="arguments"></a>引數  
 *eOption*[in]  
 設定為上面＜備註＞一節所列的其中一個選項。  
  
 *iValue*[in]  
 指定的值*eOption*。 *IValue*引數是整數值轉換成 void 指標以便日後擴充為 64 位元值。  
  
## <a name="return-code-values"></a>傳回碼值  
 S_OK  
 此方法已成功。  
  
 E_FAIL  
 發生提供者特定錯誤如需詳細資訊，請使用[ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)介面。  
  
 E_UNEXPECTED  
 此方法的呼叫是非預期的。 例如， [ibcpsession:: Bcpinit](ibcpsession-bcpinit-ole-db.md)方法不會呼叫此函式之前呼叫。  
  
 E_OUTOFMEMORY  
 記憶體不足錯誤  
  
## <a name="see-also"></a>另請參閱  
 [IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md)   
 [執行大量複製作業](../native-client/features/performing-bulk-copy-operations.md)  
  
  