---
title: 工作階段 |Microsoft 文件
description: SQL Server 的 OLE DB 驅動程式中的工作階段
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-data-source-objects
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- sessions [OLE DB]
- OLE DB Driver for SQL Server, sessions
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c3c0d94c31c298fa9840067c15c169cfb4e56b92
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2018
---
# <a name="sessions"></a>工作階段
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  OLE DB 驅動程式的 SQL Server 工作階段代表單一執行個體的連接[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]。  
  
 SQL Server OLE DB 驅動程式需要工作階段分隔資料來源的交易空間。 所有從特定工作階段物件建立而來的命令物件，都會參與工作階段物件的本機或分散式交易。  
  
 在初始化資料來源上建立的第一個工作階段物件會接收在初始化時所建立的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 連接。 當工作階段物件介面上的所有參考被釋放時，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的連接就可供資料來源上建立的另一個工作階段物件使用。  
  
 在資料來源上建立的其他工作階段物件會依照資料來源的指示，對 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體建立本身的連接。 當應用程式釋放對該工作階段所建立物件的所有參考時，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的連接就會卸除。  
  
 下列範例示範如何使用 SQL Server OLE DB 驅動程式連接到[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]資料庫：  
  
```  
int main()  
{  
    // Interfaces used in the example.  
    IDBInitialize*      pIDBInitialize      = NULL;  
    IDBCreateSession*   pIDBCreateSession   = NULL;  
    IDBCreateCommand*   pICreateCmd1        = NULL;  
    IDBCreateCommand*   pICreateCmd2        = NULL;  
    IDBCreateCommand*   pICreateCmd3        = NULL;  
  
    // Initialize COM.  
    if (FAILED(CoInitialize(NULL)))  
    {  
        // Display error from CoInitialize.  
        return (-1);  
    }  
  
    // Get the memory allocator for this task.  
    if (FAILED(CoGetMalloc(MEMCTX_TASK, &g_pIMalloc)))  
    {  
        // Display error from CoGetMalloc.  
        goto EXIT;  
    }  
  
    // Create an instance of the data source object.  
    if (FAILED(CoCreateInstance(CLSID_MSOLEDBSQL, NULL,  
        CLSCTX_INPROC_SERVER, IID_IDBInitialize, (void**)  
        &pIDBInitialize)))  
    {  
        // Display error from CoCreateInstance.  
        goto EXIT;  
    }  
  
    // The InitFromPersistedDS function   
    // performs IDBInitialize->Initialize() establishing  
    // the first application connection to the instance of SQL Server.  
    if (FAILED(InitFromPersistedDS(pIDBInitialize, L"MyDataSource",  
        NULL, NULL)))  
    {  
        goto EXIT;  
    }  
  
    // The IDBCreateSession interface is implemented on the data source  
    // object. Maintaining the reference received maintains the   
    // connection of the data source to the instance of SQL Server.  
    if (FAILED(pIDBInitialize->QueryInterface(IID_IDBCreateSession,  
        (void**) &pIDBCreateSession)))  
    {  
        // Display error from pIDBInitialize.  
        goto EXIT;  
    }  
  
    // Releasing this has no effect on the SQL Server connection  
    // of the data source object because of the reference maintained by  
    // pIDBCreateSession.  
    pIDBInitialize->Release();  
    pIDBInitialize = NULL;  
  
    // The session created next receives the SQL Server connection of  
    // the data source object. No new connection is established.  
    if (FAILED(pIDBCreateSession->CreateSession(NULL,  
        IID_IDBCreateCommand, (IUnknown**) &pICreateCmd1)))  
    {  
        // Display error from pIDBCreateSession.  
        goto EXIT;  
    }  
  
    // A new connection to the instance of SQL Server is established to support the  
    // next session object created. On successful completion, the  
    // application has two active connections on the SQL Server.  
    if (FAILED(pIDBCreateSession->CreateSession(NULL,  
        IID_IDBCreateCommand, (IUnknown**) &pICreateCmd2)))  
    {  
        // Display error from pIDBCreateSession.  
        goto EXIT;  
    }  
  
    // pICreateCmd1 has the data source connection. Because the  
    // reference on the IDBCreateSession interface of the data source  
    // has not been released, releasing the reference on the session  
    // object does not terminate a connection to the instance of SQL Server.  
    // However, the connection of the data source object is now   
    // available to another session object. After a successful call to   
    // Release, the application still has two active connections to the   
    // instance of SQL Server.  
    pICreateCmd1->Release();  
    pICreateCmd1 = NULL;  
  
    // The next session created gets the SQL Server connection  
    // of the data source object. The application has two active  
    // connections to the instance of SQL Server.  
    if (FAILED(pIDBCreateSession->CreateSession(NULL,  
        IID_IDBCreateCommand, (IUnknown**) &pICreateCmd3)))  
    {  
        // Display error from pIDBCreateSession.  
        goto EXIT;  
    }  
  
EXIT:  
    // Even on error, this does not terminate a SQL Server connection   
    // because pICreateCmd1 has the connection of the data source   
    // object.  
    if (pICreateCmd1 != NULL)  
        pICreateCmd1->Release();  
  
    // Releasing the reference on pICreateCmd2 terminates the SQL  
    // Server connection supporting the session object. The application  
    // now has only a single active connection on the instance of SQL Server.  
    if (pICreateCmd2 != NULL)  
        pICreateCmd2->Release();  
  
    // Even on error, this does not terminate a SQL Server connection   
    // because pICreateCmd3 has the connection of the   
    // data source object.  
    if (pICreateCmd3 != NULL)  
        pICreateCmd3->Release();  
  
    // On release of the last reference on a data source interface, the  
    // connection of the data source object to the instance of SQL Server is broken.  
    // The example application now has no SQL Server connections active.  
    if (pIDBCreateSession != NULL)  
        pIDBCreateSession->Release();  
  
    // Called only if an error occurred while attempting to get a   
    // reference on the IDBCreateSession interface of the data source.  
    // If so, the call to IDBInitialize::Uninitialize terminates the   
    // connection of the data source object to the instance of SQL Server.  
    if (pIDBInitialize != NULL)  
    {  
        if (FAILED(pIDBInitialize->Uninitialize()))  
        {  
            // Uninitialize is not required, but it fails if an  
            // interface has not been released. Use it for  
            // debugging.  
        }  
        pIDBInitialize->Release();  
    }  
  
    if (g_pIMalloc != NULL)  
        g_pIMalloc->Release();  
  
    CoUninitialize();  
  
    return (0);  
}  
```  
  
 SQL Server 執行個體的工作階段物件連接 OLE DB 驅動程式[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]可以產生持續建立和釋放工作階段物件的應用程式的重大額外負荷。 可以是額外負荷也藉由有效率地管理 SQL Server 工作階段物件的 OLE DB 驅動程式。 OLE DB 驅動程式的 SQL Server 應用程式可以保持[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]連線的工作階段物件，由維持至少一個物件的介面上的參考。  
  
 例如，維持命令建立物件參考的集區，可以將集區中這些工作階段物件的連接保持為使用中。 需要工作階段物件時，集區維護程式碼會傳遞有效**IDBCreateCommand**需要該工作階段的應用程式方法的介面指標。 當應用程式方法不再需要工作階段時，該方法會將介面指標傳回給集區維護程式碼，而不是釋放應用程式對命令建立物件的參考。  
  
> [!NOTE]  
>  在上述範例中， **IDBCreateCommand**介面用因為**ICommand**介面會實作**GetDBSession**方法，讓物件判斷其建立所在的工作階段的命令或資料列集的範圍內的唯一方法。 因此，只有命令物件才可以讓應用程式擷取資料來源物件指標，而其他的工作階段可從該指標建立。  
  
## <a name="see-also"></a>另請參閱  
 [資料來源物件 &#40; OLE DB &#41;](../../oledb/ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  