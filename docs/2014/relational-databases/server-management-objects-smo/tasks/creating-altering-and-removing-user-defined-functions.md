---
title: 建立、 改變和移除使用者定義函數 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- user-defined functions [SMO]
ms.assetid: 0ebebd3b-0775-41c2-989d-aa4cf81af12a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ced5a796739ea508440fea9ddbb645443fdda786
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48054498"
---
# <a name="creating-altering-and-removing-user-defined-functions"></a>建立、改變和移除使用者定義函數
  <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction>物件提供功能，可讓使用者以程式設計方式管理中的使用者定義函數[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]。 使用者定義函數支援輸入和輸出參數，也支援資料表資料行的直接參考。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 需要資料庫才能內註冊組件可以使用預存程序、 使用者定義函數、 觸發程序和使用者定義資料類型。 SMO 以 <xref:Microsoft.SqlServer.Management.Smo.SqlAssembly> 物件支援此功能。  
  
 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction>物件參考.NET 組件<xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.AssemblyName%2A>， <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.ClassName%2A>，和<xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.MethodName%2A>屬性。  
  
 當<xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction>物件參考.NET 組件時，您必須藉由建立註冊組件<xref:Microsoft.SqlServer.Management.Smo.SqlAssembly>物件，並將它加入至<xref:Microsoft.SqlServer.Management.Smo.SqlAssemblyCollection>物件，它屬於<xref:Microsoft.SqlServer.Management.Smo.Database>物件。  
  
## <a name="example"></a>範例  
 如果要使用所提供的任何程式碼範例，您必須選擇建立應用程式用的程式設計環境、程式設計範本，及程式設計語言。 如需詳細資訊，請參閱[Visual Studio.NET 中建立 Visual Basic SMO Project](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)或是[建立 Visual C&#35; Visual Studio.NET 中的 SMO 專案](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。  
  
## <a name="creating-a-scalar-user-defined-function-in-visual-basic"></a>在 Visual Basic 中建立純量使用者定義函數  
 此程式碼範例示範如何建立和移除的純量使用者定義函式具有輸入<xref:System.DateTime>物件參數和整數傳回類型[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]。 使用者定義函式上建立[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)]資料庫。 此範例會建立使用者定義函數 ISOweek，該函數取用日期引數並計算 ISO 週數。 為了讓這個函數能夠正確計算，必須先將資料庫 DATEFIRST 選項設定為 1，才能呼叫該函數。  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBUserDefFuncs1](SMO How to#SMO_VBUserDefFuncs1)]  -->  
  
## <a name="creating-a-scalar-user-defined-function-in-visual-c"></a>在 Visual C# 中建立純量使用者定義函數  
 此程式碼範例示範如何建立和移除的純量使用者定義函式具有輸入<xref:System.DateTime>物件參數和整數傳回類型[!INCLUDE[csprcs](../../../includes/csprcs-md.md)]。 使用者定義函式上建立[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)]資料庫。 本範例會建立使用者定義函數。 `ISOweek`. 這個函數採用日期引數並計算 ISO 週數。 為了讓這個函數能夠正確計算，必須先將資料庫 `DATEFIRST` 選項設定為 `1` ，才能呼叫該函數。  
  
```  
{  
            //Connect to the local, default instance of SQL Server.   
           Server srv = new Server();  
            //Reference the AdventureWorks2012 database.   
           Database db = srv.Databases["AdventureWorks2012"];  
  
            //Define a UserDefinedFunction object variable by supplying the parent database and the name arguments in the constructor.   
            UserDefinedFunction udf = new UserDefinedFunction(db, "IsOWeek");  
  
            //Set the TextMode property to false and then set the other properties.   
            udf.TextMode = false;  
            udf.DataType = DataType.Int;  
            udf.ExecutionContext = ExecutionContext.Caller;  
            udf.FunctionType = UserDefinedFunctionType.Scalar;  
            udf.ImplementationType = ImplementationType.TransactSql;  
  
            //Add a parameter.   
  
     UserDefinedFunctionParameter par = new UserDefinedFunctionParameter(udf, "@DATE", DataType.DateTime);  
            udf.Parameters.Add(par);  
  
            //Set the TextBody property to define the user-defined function.   
            udf.TextBody = "BEGIN DECLARE @ISOweek int SET @ISOweek= DATEPART(wk,@DATE)+1 -DATEPART(wk,CAST(DATEPART(yy,@DATE) as CHAR(4))+'0104') IF (@ISOweek=0) SET @ISOweek=dbo.ISOweek(CAST(DATEPART(yy,@DATE)-1 AS CHAR(4))+'12'+ CAST(24+DATEPART(DAY,@DATE) AS CHAR(2)))+1 IF ((DATEPART(mm,@DATE)=12) AND ((DATEPART(dd,@DATE)-DATEPART(dw,@DATE))>= 28)) SET @ISOweek=1 RETURN(@ISOweek) END;";  
  
            //Create the user-defined function on the instance of SQL Server.   
            udf.Create();  
  
            //Remove the user-defined function.   
            udf.Drop();  
        }  
```  
  
## <a name="creating-a-scalar-user-defined-function-in-powershell"></a>在 PowerShell 中建立純量使用者定義函數  
 此程式碼範例示範如何建立和移除的純量使用者定義函式具有輸入<xref:System.DateTime>物件參數和整數傳回類型[!INCLUDE[csprcs](../../../includes/csprcs-md.md)]。 使用者定義函式上建立[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)]資料庫。 本範例會建立使用者定義函數。 `ISOweek`. 這個函數採用日期引數並計算 ISO 週數。 為了讓這個函數能夠正確計算，必須先將資料庫 `DATEFIRST` 選項設定為 `1` ，才能呼叫該函數。  
  
```  
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = get-item Adventureworks2012  
  
# Define a user defined function object variable by supplying the parent database and name arguments in the constructor.   
$udf  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.UserDefinedFunction `  
-argumentlist $db, "IsOWeek"  
  
# Set the TextMode property to false and then set the other properties.   
$udf.TextMode = $false  
$udf.DataType = [Microsoft.SqlServer.Management.SMO.DataType]::Int   
$udf.ExecutionContext = [Microsoft.SqlServer.Management.SMO.ExecutionContext]::Caller  
$udf.FunctionType = [Microsoft.SqlServer.Management.SMO.UserDefinedFunctionType]::Scalar  
$udf.ImplementationType = [Microsoft.SqlServer.Management.SMO.ImplementationType]::TransactSql  
  
# Define a Parameter object variable by supplying the parent function, name and type arguments in the constructor.  
$type = [Microsoft.SqlServer.Management.SMO.DataType]::DateTime  
$par  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.UserDefinedFunctionParameter `  
-argumentlist $udf, "@DATE",$type  
  
# Add the parameter to the function  
$udf.Parameters.Add($par)  
  
#Set the TextBody property to define the user-defined function.   
$udf.TextBody = "BEGIN DECLARE @ISOweek int SET @ISOweek= DATEPART(wk,@DATE)+1 -DATEPART(wk,CAST(DATEPART(yy,@DATE) as CHAR(4))+'0104') IF (@ISOweek=0) SET @ISOweek=dbo.ISOweek(CAST(DATEPART(yy,@DATE)-1 AS CHAR(4))+'12'+ CAST(24+DATEPART(DAY,@DATE) AS CHAR(2)))+1 IF ((DATEPART(mm,@DATE)=12) AND ((DATEPART(dd,@DATE)-DATEPART(dw,@DATE))>= 28)) SET @ISOweek=1 RETURN(@ISOweek) END;"  
  
# Create the user-defined function on the instance of SQL Server.   
$udf.Create()  
  
# Remove the user-defined function.   
$udf.Drop()  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction>  
  
  
