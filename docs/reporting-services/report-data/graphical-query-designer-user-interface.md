---
title: 圖形化查詢設計工具使用者介面 | Microsoft Docs
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-data
ms.topic: conceptual
f1_keywords:
- "10012"
- sql13.rtp.rptdesigner.dataview.vdtquerydesigner.f1
helpviewer_keywords:
- graphical query designer [Reporting Services]
- data sources [Reporting Services], creating
- text-based query designer [Reporting Services]
- query designers [Reporting Services]
- Reporting Services, query designers
ms.assetid: 5022ae33-03a3-48de-8ac1-82742f48cebe
author: markingmyname
ms.author: maghan
ms.openlocfilehash: eaa7c799c6897403b085eb55acf7de3e4247aa77
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47844644"
---
# <a name="graphical-query-designer-user-interface"></a>圖形化查詢設計工具使用者介面
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 同時提供了圖形化查詢設計工具以及以文字為基礎的查詢設計工具來建立查詢，以便從關聯式資料庫中擷取資料作為報表設計師中的報表資料集。 使用圖形化查詢設計工具，可透過互動方式建立查詢及檢視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、Oracle、OLE DB 和 ODBC 資料來源類型的結果。 使用以文字為基礎的查詢設計工具，可指定多個 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式、複雜查詢或命令語法以及以運算式為基礎的查詢。 如需詳細資訊，請參閱 [以文字為基礎的查詢設計工具使用者介面](http://msdn.microsoft.com/library/44b7c664-03aa-494e-a484-052b318e810c)。 如需使用特定資料來源類型的詳細資訊，請參閱 [報表資料集 &#40;SSRS&#41;](../../reporting-services/report-data/report-datasets-ssrs.md)。  
  
 執行個體時提供 SQL Server 登入。  
  
## <a name="graphical-query-designer"></a>圖形化查詢設計工具  
 此圖形化查詢設計工具支援三種查詢命令：**Text**、**StoredProcedure** 或 **TableDirect**。 在您為資料集建立查詢之前，您必須先在 [ [資料集屬性](http://msdn.microsoft.com/library/1fa34a4b-7de0-4e92-99fa-bc28a206773f) ] 對話方塊的 [查詢] 頁面上選取命令類型選項。  
  
 下列選項可用於查詢類型：  
  
-   **Text** ：可支援關聯式資料庫資料來源的標準 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢文字，包括 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 Oracle 的資料處理延伸模組。  
  
-   **TableDirect** ：從指定的資料表中選取所有資料行。 例如，如果是名為 Customers 的資料表，這就等於 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式 `SELECT * FROM Customers`。  
  
-   **StoredProcedure** ：可支援資料來源上預存程序的呼叫。 若要使用這個選項，您必須已經獲得資料來源的資料庫管理員授與對預存程序的 Execute 權限。  
  
 預設的命令類型為 **Text**。  
  
> [!NOTE]  
>  並不是所有資料處理延伸模組都支援所有的類型。 基礎資料提供者必須支援某種命令類型，才能使用此選項。  
  
### <a name="command-type-text"></a>Text 命令類型  
 在 **Text** 類型中，圖形化查詢設計工具提供了四個區域，或稱窗格。 您可以指定 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢的資料行、別名、排序值和篩選值。 您也可以檢視依據選取項目所產生的查詢文字、執行查詢，以及檢視結果集。 下圖顯示了這四個窗格。  
  
 ![SQL 查詢適用的圖形化查詢設計工具](../../reporting-services/report-data/media/rsqd-dsaw-sql.gif "SQL 查詢適用的圖形化查詢設計工具")  
  
 下表會描述各個窗格的功能。  
  
|窗格|函數|  
|----------|--------------|  
|圖表|顯示查詢中之資料表的圖形表示。 使用此窗格，即可選取欄位並定義資料表之間的關聯性。|  
|方格|顯示查詢傳回的欄位清單。 使用此窗格，即可定義別名、排序次序、篩選、群組和參數。|  
|SQL|顯示以 [圖表] 和 [方格] 窗格表示的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢。 使用此窗格，即可利用 [!INCLUDE[tsql](../../includes/tsql-md.md)]來撰寫或更新查詢。|  
|結果|顯示查詢的結果。 若要執行查詢，請以滑鼠右鍵按一下任何窗格，然後按一下 [執行]，或是按一下工具列上的 [執行] 按鈕。|  
  
 當您在前三個窗格中的任何一個窗格內變更資訊時，那些變更將會出現在其他窗格中。 例如，如果您在 [圖表] 窗格中加入資料表，則也會將該資料表自動加入至 [SQL] 窗格中的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢。 如果將欄位加入至 [SQL] 窗格中的查詢，則也會將該欄位自動加入至 [方格] 窗格中的清單，以及更新 [圖表] 窗格中的資料表。  
  
 如需詳細資訊，請參閱[查詢和檢視表設計工具 &#40;Visual Database Tools&#41;](http://msdn.microsoft.com/library/12e4b5a5-b793-4b6c-a0e5-c450c49bf26f)。  
  
#### <a name="toolbar-for-the-graphical-query-designer"></a>圖形化查詢設計工具工具列  
 圖形化查詢設計工具工具列會提供按鈕，協助您使用圖形化介面設計 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢。  
  
|按鈕|Description|  
|------------|-----------------|  
|**當成文字編輯**|在以文字為基礎的查詢設計工具和圖形化查詢設計工具之間切換。|  
|**匯入**|從檔案或報表匯入現有的查詢。 只支援 .sql 和 .rdl 檔案類型。 如需詳細資訊，請參閱 [報表內嵌資料集和共用資料集 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)。|  
|![顯示/隱藏圖表窗格切換按鈕](../../reporting-services/report-data/media/rsqdicon-showhidediagram.gif "顯示/隱藏圖表窗格切換按鈕")|顯示或隱藏 [圖表] 窗格。|  
|![顯示或隱藏方格窗格切換](../../reporting-services/report-data/media/rsqdicon-showhidegrid.gif "顯示或隱藏方格窗格切換")|顯示或隱藏 [方格] 窗格。|  
|![顯示或隱藏 SQL 窗格切換](../../reporting-services/report-data/media/rsqdicon-showhidesql.gif "顯示或隱藏 SQL 窗格切換")|顯示或隱藏 [SQL] 窗格。|  
|![顯示或隱藏結果窗格切換](../../reporting-services/report-data/media/rsqdicon-showhideresult.gif "顯示或隱藏結果窗格切換")|顯示或隱藏 [結果] 窗格。|  
|![執行查詢](../../reporting-services/report-data/media/rsqdicon-run.gif "執行查詢")|執行查詢。|  
|![在 SQL 窗格中驗證 SQL 的按鈕](../../reporting-services/report-data/media/rsqdicon-verifysql.gif "在 SQL 窗格中驗證 SQL 的按鈕")|檢查查詢文字的語法是否正確。|  
|![在選取的欄位設定遞增排序](../../reporting-services/report-data/media/rsqdicon-sortascending.gif "在選取的欄位設定遞增排序")|將 [圖表] 窗格中選取之資料行的排序次序，設定為 [遞增排序]。|  
|![在選取的欄位設定遞減排序](../../reporting-services/report-data/media/rsqdicon-sortdescending.gif "在選取的欄位設定遞減排序")|將 [圖表] 窗格中選取之資料行的排序次序，設定為 [遞減排序]。|  
|![移除所選欄位的篩選](../../reporting-services/report-data/media/rsqdicon-removefilter.gif "移除所選欄位的篩選")|在標記為有篩選 (![所選篩選資料行旁邊的篩選圖形](../../reporting-services/report-data/media/rsqdicon-filter.gif "所選篩選資料行旁邊的篩選圖形")) 的 [圖表] 窗格中，移除所選資料行的篩選。|  
|![對所選欄位使用 [分組依據]](../../reporting-services/report-data/media/rsqdicon-usegroupby.gif "對所選欄位使用 [分組依據]")|顯示或隱藏 [方格] 窗格中的 [群組依據] 資料行。 當 [分組依據] 切換為開啟時，[方格] 窗格中會出現一個名稱為 [分組依據] 的額外資料行，而且查詢中所選資料行的每一個值都會預設為 [分組依據]，這樣就會將選取的資料行包含在 SQL 文字的 Group By 子句中。 使用 [群組依據] 按鈕即可自動加入 GROUP BY 子句，該子句會包含 SELECT 子句中的所有資料行。 如果 SELECT 子句中包含的是彙總函式呼叫 (例如 SUM(ColumnName))，但是您希望非彙總資料行也出現在結果集中，則請將其包含在 GROUP BY 子句中。<br /><br /> 查詢中的每個資料行都必須定義彙總函式，用以計算要顯示在 [結果] 窗格中的值，或者必須在 SQL 查詢的 GROUP BY 子句中指定查詢的資料行，這樣資料行才會出現在 [結果] 窗格中。|  
|![將新資料表新增到圖表窗格](../../reporting-services/report-data/media/rsqdicon-addtable.gif "將新資料表新增到圖表窗格")|將資料來源中的新資料表加入至 [圖表] 窗格中。<br /><br /> **注意** ：當您加入新資料表時，查詢設計工具會嘗試比對資料來源中的外部索引鍵關聯性。 因此，在加入資料表之後，請確認以資料表之間的連結所表示的外部索引鍵關聯性是否正確。|  
  
#### <a name="example"></a>範例  
 下列查詢會從 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫的 **Person** 資料表傳回姓氏清單：  
  
```  
SELECT LastName FROM Person.Person;  
```  
  
 您也可以從 [SQL] 窗格中執行預存程序。 下列查詢會在 **資料庫中執行** uspGetEmployeeManagers [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 預存程序：  
  
```  
EXEC uspGetEmployeeManagers '1';  
```  
  
### <a name="command-type-tabledirect"></a>TableDirect 命令類型  
 在 **TableDirect** 類型中，圖形化查詢設計工具會顯示資料來源中可用的資料表下拉式清單和 [結果] 窗格。 如果選取資料表並按一下 [執行] 按鈕，便會傳回該資料表的所有資料行。  
  
> [!NOTE]  
>  只有 **OLE DB** 和 **ODBC** 資料來源類型才支援 TableDirect 功能。  
  
 下表會描述各個窗格的功能。  
  
|窗格|函數|  
|----------|--------------|  
|資料表下拉式清單|列出資料來源中所有可使用的資料表。 從清單中選取一項，即可使其變成使用中狀態。|  
|結果|顯示選取之資料表中的所有資料行。 若要執行資料表查詢，請按一下工具列上的 [執行] 按鈕。|  
  
#### <a name="toolbar-buttons-for-the-command-type-tabledirect"></a>TableDirect 命令類型的工具列按鈕  
 圖形化查詢設計工具工具列會提供資料來源中的資料表下拉式清單。 下表列出每一個按鈕以及該按鈕的功能。  
  
|按鈕|Description|  
|------------|-----------------|  
|**當成文字編輯**|在以文字為基礎的查詢設計工具和圖形化查詢設計工具之間切換。|  
|**匯入**|從檔案或報表匯入現有的查詢。 只支援 .sql 和 .rdl 檔案類型。 如需詳細資訊，請參閱 [報表內嵌資料集和共用資料集 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)。|  
|![一般查詢設計工具按鈕的圖示](../../reporting-services/report-data/media/icongenericquerydesigner.gif "一般查詢設計工具按鈕的圖示")|在一般查詢設計工具與圖形化查詢設計工具之間切換，並保留查詢文字或預存程序檢視。|  
|![執行查詢](../../reporting-services/report-data/media/rsqdicon-run.gif "執行查詢")|從選取的資料表中選取所有的資料行。|  
  
### <a name="command-type-storedprocedure"></a>StoredProcedure 命令類型  
 在 **StoredProcedure** 類型中，圖形化查詢設計工具會顯示資料來源中可用的預存程序下拉式清單和 [結果] 窗格。 下表會描述各個窗格的功能。  
  
|窗格|函數|  
|----------|--------------|  
|預存程序下拉式清單|列出資料來源中所有可使用的預存程序。 從清單中選取一項，即可使其變成使用中狀態。|  
|結果|顯示執行預存程序的結果。 若要執行選取的預存程序，請按一下工具列上的 [執行] 按鈕。|  
  
#### <a name="toolbar-buttons-for-command-type-storedprocedure"></a>StoredProcedure 命令類型的工具列按鈕  
 圖形化查詢設計工具工具列會提供資料來源中的預存程序下拉式清單。 下表列出每一個按鈕以及該按鈕的功能。  
  
|按鈕|Description|  
|------------|-----------------|  
|**當成文字編輯**|在以文字為基礎的查詢設計工具和圖形化查詢設計工具之間切換。|  
|**匯入**|從檔案或報表匯入現有的查詢。 只支援 .sql 和 .rdl 檔案類型。 如需詳細資訊，請參閱 [報表內嵌資料集和共用資料集 &#40;報表產生器和 SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)(Dependent Dataset)。|  
|![執行查詢](../../reporting-services/report-data/media/rsqdicon-run.gif "執行查詢")|執行選取的預存程序。|  
|預存程序下拉式清單|按一下向下箭頭，即可顯示資料來源中可使用的預存程序清單。 按一下清單中的任何一個預存程序，以選取它。|  
  
#### <a name="example"></a>範例  
 下列預存程序會從 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫中呼叫員工經理的命令鏈結清單。 這個預存程序會接受 *BusinessEntityID* 作為參數。 您可以輸入任何較小的整數。  
  
 `uspGetEmployeeManagers '1';`  
  
## <a name="see-also"></a>另請參閱  
 [查詢設計工具 &#40;SSRS&#41;](../../reporting-services/report-data/query-design-tools-ssrs.md)   
 [報表資料集 &#40;SSRS&#41;](../../reporting-services/report-data/report-datasets-ssrs.md)   
 [SQL Server 連接類型 &#40;SSRS&#41;](../../reporting-services/report-data/sql-server-connection-type-ssrs.md)   
 [OLE DB 連線類型 &#40;SSRS&#41;](../../reporting-services/report-data/ole-db-connection-type-ssrs.md)   
 [報表資料集 &#40;SSRS&#41;](../../reporting-services/report-data/report-datasets-ssrs.md)   
 [Oracle 連線類型 &#40;SSRS&#41;](../../reporting-services/report-data/oracle-connection-type-ssrs.md)   
 [RSReportDesigner 組態檔](../../reporting-services/report-server/rsreportdesigner-configuration-file.md)   
 [設計查詢和檢視使用說明主題 &#40;Visual Database Tools&#41;](http://msdn.microsoft.com/library/200903f4-1208-4563-9dca-26aabaacfa20)  
  
  
