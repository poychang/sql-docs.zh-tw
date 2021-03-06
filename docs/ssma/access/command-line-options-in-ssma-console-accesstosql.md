---
title: SSMA 主控台 (AccessToSQL) 中的命令列選項 |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 08/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: c1f3b3f0-0f3e-4e07-b745-2fbdde85c67e
author: Shamikg
ms.author: Shamikg
manager: murato
ms.openlocfilehash: 6c1e8480308f0ffb8b4966bf61b395072ae2390b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47807436"
---
# <a name="command-line-options-in-the-ssma-console-accesstosql"></a>SSMA 主控台 (AccessToSQL) 中的命令列選項
Microsoft 為您提供一組強大的命令列選項來執行，並控制 SSMA 活動。 後續的章節會提供其他詳細資料。  
  
## <a name="command-line-options-in-the-ssma-console"></a>SSMA 主控台中的命令列選項  
此處所述是主控台命令的選項。  
  
本節中，為了 「 選項 」 一詞也稱為 'switch'。  
  
選項不區分大小寫和可能的開頭是 '**-**'**/**' 字元。  
  
如果指定了選項，它是必要，您會指定對應的選項參數。  
  
選項參數必須以泛空白字元分隔從選項中的字元。  
  
**語法範例：**  
  
`C:\> SSMAforAccessConsole.EXE -s scriptfile`  
  
`C:\> SSMAforAccessConsole.EXE -s “C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\AssessmentReportGenerationSample.xml” –v “C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\VariableValueFileSample.xml” –c “C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ServersConnectionFileSample.xml”`  
  
包含空格的資料夾或檔案名稱應指定雙引號括住。  
  
命令列的項目和錯誤訊息的輸出會儲存在 STDOUT 或指定的檔案。  
  
### <a name="script-file-option-sscript"></a>指令碼檔案的選項:-s/指令碼  
必要的參數，指令碼檔案的路徑/名稱指定要由 SSMA 執行的命令順序的指令碼。  
  
**語法範例：**  
  
`C:\>SSMAforAccessConsole.EXE –s “C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml”`  
  
### <a name="variable-value-file-option-vvariable"></a>變數值檔案選項: – v/變數  
變數值檔案包含在指令碼檔案中使用的變數。 參數是選擇性的。 如果變數不是變數的檔案中宣告，並使用指令碼檔案中，應用程式就會產生錯誤，並結束主控台執行。  
  
**語法範例：**  
  
-   定義多個變數值檔案，可能是一個預設值，另一個執行個體特定值時適用的變數。 最後一個命令列引數中指定的變數檔案會接受喜好設定，以防萬一發生重複的變數：  
  
    `C:\>SSMAforAccessConsole.EXE -s`  
  
    `“C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml” –v c:\migration`  
  
    `projects\global_variablevaluefile.xml –v “c:\migrationprojects\instance_variablevaluefile.xml”`  
  
### <a name="server-connection-file-option-cserverconnection"></a>伺服器連線檔案選項: – c/serverconnection  
此檔案包含每一部伺服器的伺服器連接資訊。 每個伺服器定義會識別唯一的伺服器識別碼。 伺服器識別碼會參考連接相關的命令的指令碼檔案中。  
  
伺服器定義可以是伺服器連線檔案和/或指令碼檔案的一部分。 指令碼檔案中的伺服器識別碼的優先順序高於伺服器連線檔案中，如果有重複的伺服器識別碼。  
  
**語法範例：**  
  
-   伺服器識別碼會用於指令碼檔案。 它們是不同的伺服器連線檔案中定義。 這個檔案會使用變數值檔案中所定義的變數：  
  
    `C:\>SSMAforAccessConsole.EXE –s “C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –v`  
  
    `c:\SsmaProjects\myvaluefile1.xml –c`  
  
    `c:\SsmaProjects\myserverconnectionsfile1.xml`  
  
-   伺服器定義內嵌在指令碼檔案中：  
  
    `C:\>SSMAforAccessConsole.EXE –s “C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml”`  
  
### <a name="xml-output-option--xxmloutput-xmloutputfile"></a>XML 輸出的選項:-x / xmloutput [xmloutputfile]  
此命令用來輸出至主控台或至 xml 檔案的 xml 格式的命令輸出訊息。  
  
有兩個選項可供 xmloutput，也就是：  
  
-   如果檔案路徑會提供 xmloutput 切換之後，輸出會重新導向至檔案。  
  
    **語法範例：**  
  
    `C:\>SSMAforAccessConsole.EXE –s`  
  
    `“C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –x d:\xmloutput\project1output.xml`  
  
-   如果沒有檔案路徑提供 xmloutput 切換之後，則會顯示 xmlout 本身在主控台上。  
  
    **語法範例：**  
  
    `C:\>SSMAforAccessConsole.EXE –s “C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –xmloutput`  
  
### <a name="log-file-option-llog"></a>記錄檔選項:-l/記錄檔  
在主控台應用程式中的所有 SSMA 作業會都記錄在記錄檔，並是選擇性參數。 如果在命令列指定記錄檔和其路徑，取得產生記錄檔，在指定的位置。 否則，它會產生在其預設位置。  
  
**語法範例：**  
  
`C:\>SSMAforAccessConsole.EXE`  
  
`“C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –l c:\SsmaProjects\migration1.log`  
  
### <a name="project-environment-folder-option-eprojectenvironment"></a>專案環境資料夾選項:-e/projectenvironment  
此選用參數代表目前的 SSMA 專案的專案環境設定 資料夾。  
  
**語法範例：**  
  
`C:\>SSMAforAccessConsole.EXE –s`  
  
`“C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –e c:\SsmaProjects\CommonEnvironment`  
  
||  
|-|  
||  
  
### <a name="secure-password-option-psecurepassword"></a>安全的密碼選項:-p/securepassword  
這個選項表示伺服器連接的加密的密碼。 與所有其他選項，但不會執行任何指令碼或協助任何移轉相關的活動，協助管理移轉專案中使用的伺服器連接的密碼加密。  
  
您無法輸入任何其他選項和密碼，做為命令列參數。 否則，它會導致錯誤。 如需詳細資訊，請參閱 <<c0> [ 管理密碼](managing-passwords-accesstosql.md)一節。  
  
支援下列子`–p/securepassword`:  
  
-   若要新增密碼，或更新現有的密碼，以指定的伺服器識別碼，或在伺服器連線檔案中定義的所有伺服器 id 受保護的儲存體：  
  
    `-p|-securepassword -a|add    {"<server_id>[, .n]"|all}``-c|-serverconnection <server-connection-file> [-v|variable <variable-value-file>]``[-o|overwrite]`  
  
    `-p|-securepassword -a|add    {"<server_id>[, .n]"|all}``-s|-script <server-connection-file> [-v|variable <variable-value-file>] [-o|overwrite]`  
  
-   若要從受保護的儲存體指定的伺服器識別碼或所有的伺服器識別碼移除加密的密碼：  
  
    `–p/securepassword –r/remove {<server_id> [, …n] | all}`  
  
-   若要顯示的加密密碼的伺服器識別碼的清單：  
  
    `–p/securepassword –l/list`  
  
-   若要匯出受保護的儲存體加密的檔案中儲存的密碼。 這個檔案是以使用者指定的複雜密碼加密。  
  
    `–p/securepassword –e/export {<server-id> [, …n] | all} <encrypted-password -file>`  
  
-   加密-稍早匯出檔案匯入本機受保護的儲存體，使用使用者指定的複雜密碼。 一旦解密檔案，它會儲存在新的檔案，接著，在本機電腦上加密。  
  
    `–p/securepassword –i/import {<server-id> [, …n] | all} <encrypted-password -file>`  
  
    可以使用逗號分隔符號來指定多個伺服器識別碼。  
  
### <a name="help-option-help"></a>Help 選項:-？ / 協助  
顯示 SSMA 主控台選項的語法的摘要：  
  
`C:\>SSMAforAccessConsole.EXE -?`  
  
SSMA 主控台命令列選項以表格形式顯示，請參閱[附錄-1 &#40;AccessToSQL&#41;](../../ssma/access/appendix-1-accesstosql.md)。  
  
### <a name="securepassword-help-option-securepassword--help"></a>SecurePassword 說明選項:-securepassword-？ / 協助  
顯示 SSMA 主控台選項的語法的摘要：  
  
`C:\>SSMAforAccessConsole.EXE -securepassword -?`  
  
SSMA 主控台命令列選項以表格形式顯示，請參閱[附錄-1 &#40;AccessToSQL&#41;](../../ssma/access/appendix-1-accesstosql.md)  
  
### <a name="next-steps"></a>後續步驟  
下一個步驟取決於您的專案需求：  
  
1.  指定的密碼或匯出 / 匯入的密碼，請參閱 <<c0> [ 管理的密碼&#40;AccessToSQL&#41;](../../ssma/access/managing-passwords-accesstosql.md)。</c0>  
  
2.  要產生報表，請參閱[產生的報表&#40;AccessToSQL&#41;](../../ssma/access/generating-reports-accesstosql.md)。  
  
3.  如需疑難排解主控台中的問題，請參閱[疑難排解&#40;AccessToSQL&#41;](../../ssma/access/troubleshooting-accesstosql.md)。  
  
