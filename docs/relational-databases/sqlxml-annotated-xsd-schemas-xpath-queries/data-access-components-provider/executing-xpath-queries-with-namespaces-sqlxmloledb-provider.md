---
title: 執行 XPath 查詢 （SQLXMLOLEDB 提供者） 的命名空間與 |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXMLOLEDB Provider, executing XPath queries
- namespaces property
- queries [SQLXML], SQLXMLOLEDB Provider
- XPath queries [SQLXML], namespaces
- XPath queries [SQLXML], SQLXMLOLEDB Provider
- namespaces [SQLXML], XPath queries
ms.assetid: 024a4b7d-435d-47ba-9e80-2c2f640108f5
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ef5008b688fe140aed4cc1d56a519db32769699b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47749182"
---
# <a name="executing-xpath-queries-with-namespaces-sqlxmloledb-provider"></a>執行含有命名空間的 XPath 查詢 (SQLXMLOLEDB 提供者)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  XPath 查詢可以包含命名空間。 如果結構描述元素會限定命名空間 (亦即，如果它們包含目標命名空間)，針對此結構描述進行的 XPath 查詢就必須指定此命名空間。  
  
 由於 SQLXML 4.0 不支援使用萬用字元 (*)，所以您必須使用命名空間前置詞來指定 XPath 查詢。 若要解析此前置詞，使用命名空間屬性來指定命名空間繫結。  
  
 在下列範例中，XPath 查詢，請指定使用萬用字元的命名空間 (\*) 和 local-name （) and namespace-uri （) XPath 函式。 此 XPath 查詢會傳回所有項目所在的區域名稱**連絡人**和命名空間 uri **urn: myschema:Contacts**。  
  
```  
/*[local-name() = 'Contact' and namespace-uri() = 'urn:myschema:Contacts']  
```  
  
 在 SQLXML 4.0 中，您必須使用命名空間前置詞來指定這個 XPath 查詢。 例如， **x: Contact**，其中**x**是命名空間前置詞。 請考慮下列 XSD 結構描述：  
  
```  
<schema xmlns="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema"  
            xmlns:con="urn:myschema:Contacts"  
            targetNamespace="urn:myschema:Contacts">  
<complexType name="ContactType">  
  <attribute name="CID" sql:field="ContactID" type="ID"/>  
  <attribute name="FName" sql:field="FirstName" type="string"/>  
  <attribute name="LName" sql:field="LastName"/>   
</complexType>  
<element name="Contact" type="con:ContactType" sql:relation="Person.Contact"/>  
</schema>  
```  
  
 由於這個結構描述會定義目標命名空間，所以針對此結構描述進行的 XPath 查詢 (例如 "Employee") 必須包含該命名空間。  
  
 這是針對上述 XSD 結構描述執行 XPath 查詢 (x:Employee) 的範例 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic 應用程式。 若要解析此前置詞，會使用命名空間屬性指定的命名空間繫結。  
  
> [!NOTE]  
>  在程式碼中，您必須於連接字串內提供 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的名稱。 此外，這個範例會指定針對資料提供者使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) (需要安裝其他網路用戶端軟體)。 如需詳細資訊，請參閱 < [SQL Server Native Client 的系統需求](../../../relational-databases/native-client/system-requirements-for-sql-server-native-client.md)。  
  
```  
Option Explicit  
Private Sub Form_Load()  
    Dim con As New ADODB.Connection  
    Dim cmd As New ADODB.Command  
    Dim stm As New ADODB.Stream  
    con.Open "provider=SQLXMLOLEDB.4.0;Data Provider=SQLNCLI11;Data Source=SqlServerName;Initial Catalog=AdventureWorks;Integrated Security=SSPI;"  
    Set cmd.ActiveConnection = con  
    stm.Open  
    cmd.Properties("Output Stream").Value = stm  
    cmd.Properties("Output Encoding") = "utf-8"  
    cmd.Properties("Mapping schema") = "C:\DirectoryPath\con-ex.xml"  
    cmd.Properties("namespaces") = "xmlns:x='urn:myschema:Contacts'"  
    '  Debug.Print "Set Command Dialect to DBGUID_XPATH"  
    cmd.Dialect = "{ec2a4293-e898-11d2-b1b7-00c04f680c56}"  
    cmd.CommandText = "x:Contact"  
    cmd.Execute , , adExecuteStream   
    stm.Position = 0  
    Debug.Print stm.ReadText(adReadAll)  
End Sub  
```  
  
### <a name="to-test-this-application"></a>測試這個應用程式  
  
1.  將範例 XSD 結構描述儲存在資料夾中。  
  
2.  建立 Visual Basic 可執行檔專案，然後將程式碼複製到其中。 依適當情況變更指定的目錄路徑。  
  
3.  加入下列專案參考：  
  
    ```  
    "Microsoft ActiveX Data Objects 2.8 Library"  
    ```  
  
4.  執行應用程式。  
  
 以下是部份結果：  
  
```  
<y0:Employee xmlns:y0="urn:myschema:Contacts"   
             LName="Achong" CID="1" FName="Gustavo"/>  
<y0:Employee xmlns:y0="urn:myschema:Employees"   
             LName="Abel" CID="2" FName="Catherine"/>  
```  
  
 雖然在 XML 文件中產生的前置詞是任意的，但是它們會對應至相同的命名空間。  
  
  
