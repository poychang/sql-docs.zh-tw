---
title: "建立訊息類型 (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 04/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_MESSAGE_TSQL
- MESSAGE_TSQL
- MESSAGE
- CREATE MESSAGE
- CREATE_MESSAGE_TYPE_TSQL
- MESSAGE TYPE
- MESSAGE_TYPE_TSQL
- CREATE MESSAGE TYPE
dev_langs:
- TSQL
helpviewer_keywords:
- XML [Service Broker]
- validation [Service Broker]
- message types [Service Broker], creating
- empty messages [SQL Server]
- binary [SQL Server], message types
- CREATE MESSAGE TYPE statement
ms.assetid: 98fe0fff-1a2e-4ca2-b37f-83a06fdf098e
caps.latest.revision: 41
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f8869a53cf18a58ba58b02e6faf8a42231e971e5
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="create-message-type-transact-sql"></a>CREATE MESSAGE TYPE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  建立新的訊息類型。 訊息類型會定義訊息的名稱以及 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 針對該名稱的訊息所執行的驗證。 交談的兩端必須定義相同的訊息類型。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
CREATE MESSAGE TYPE message_type_name  
    [ AUTHORIZATION owner_name ]  
    [ VALIDATION = {  NONE  
                    | EMPTY   
                    | WELL_FORMED_XML  
                    | VALID_XML WITH SCHEMA COLLECTION schema_collection_name  
                   } ]  
[ ; ]  
```  
  
## <a name="arguments"></a>引數  
 *message_type_name*  
 這是要建立的訊息類型名稱。 新訊息類型會建立在目前的資料庫中，擁有者是 AUTHORIZATION 子句中所指定的主體。 您不可指定伺服器、資料庫和結構描述名稱。 *Message_type_name*可達 128 個字元。  
  
 授權*owner_name*  
 將訊息類型的擁有者設為指定的資料庫使用者或角色。 當目前的使用者是**dbo**或**sa**， *owner_name*可以是任何有效的使用者或角色的名稱。 否則， *owner_name*必須是目前使用者的名稱、 目前的使用者具有 IMPERSONATE 權限，使用者名稱或目前使用者所屬的角色的名稱。 當略過這個子句時，訊息類型會屬於目前的使用者。  
  
 VALIDATION  
 指定 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 如何驗證這種類型之訊息的訊息主體。 當沒有指定這個子句時，驗證的預設值便是 NONE。  
  
 無  
 指定不執行任何驗證。 訊息主體可包含資料，也可能是 NULL。  
  
 EMPTY  
 指定訊息主體必須是 NULL。  
  
 WELL_FORMED_XML  
 指定訊息主體必須包含格式正確的 XML。  
  
 VALID_XML WITH SCHEMA COLLECTION *schema_collection_name*  
 指定訊息本文必須包含符合指定的結構描述集合中的結構描述的 XML *schema_collection_name*必須是現有 XML 結構描述集合的名稱。  
  
## <a name="remarks"></a>備註  
 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 會驗證內送訊息。 當訊息包含不符合指定驗證類型的訊息主體時，[!INCLUDE[ssSB](../../includes/sssb-md.md)] 會捨棄無效的訊息，且會將錯誤訊息傳回給送出訊息的服務。  
  
 交談的兩端必須定義相同的訊息類型名稱。 為了有助於進行疑難排解，交談的兩端通常會針對此訊息類型指定相同的驗證，不過，[!INCLUDE[ssSB](../../includes/sssb-md.md)] 並不要求交談的兩端使用相同的驗證。  
  
 訊息類型不能是暫存物件。 訊息類型名稱開頭為 **#**  ，但它們是永久物件。  
  
## <a name="permissions"></a>Permissions  
 建立訊息類型的成員的預設值的權限**db_ddladmin**或**db_owner**固定資料庫角色和**sysadmin**固定的伺服器角色。  
  
 訊息類型的 REFERENCES 權限預設為訊息類型、 成員的擁有者**db_owner**固定資料庫角色的成員**sysadmin**固定的伺服器角色。  
  
 當 CREATE MESSAGE TYPE 陳述式指定了結構描述集合時，執行這個陳述式的使用者必須有所指定之結構描述集合的 REFERENCES 權限。  
  
## <a name="examples"></a>範例  
  
### <a name="a-creating-a-message-type-containing-well-formed-xml"></a>A. 建立包含格式正確之 XML 的訊息類型  
 下列範例會建立一個包含格式正確之 XML 的新訊息類型。  
  
```  
CREATE MESSAGE TYPE  
  [//Adventure-Works.com/Expenses/SubmitExpense]  
  VALIDATION = WELL_FORMED_XML ;     
```  
  
### <a name="b-creating-a-message-type-containing-typed-xml"></a>B. 建立包含 XML 類型的訊息類型  
 下列範例會建立用 XML 來編碼之費用報表的訊息類型。 這個範例會建立一個 XML 結構描述集合來存放簡單費用報表的結構描述。 之後，這個範例會建立一個比對結構描述來驗證訊息的新訊息類型。  
  
```  
CREATE XML SCHEMA COLLECTION ExpenseReportSchema AS  
N'<?xml version="1.0" encoding="UTF-16" ?>  
  <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
     targetNamespace="http://Adventure-Works.com/schemas/expenseReport"  
     xmlns:expense="http://Adventure-Works.com/schemas/expenseReport"  
     elementFormDefault="qualified"  
   >   
    <xsd:complexType name="expenseReportType">  
       <xsd:sequence>  
         <xsd:element name="EmployeeName" type="xsd:string"/>  
         <xsd:element name="EmployeeID" type="xsd:string"/>  
         <xsd:element name="ItemDetail"  
           type="expense:ItemDetailType" maxOccurs="unbounded"/>  
      </xsd:sequence>  
    </xsd:complexType>  
  
    <xsd:complexType name="ItemDetailType">  
      <xsd:sequence>  
        <xsd:element name="Date" type="xsd:date"/>  
        <xsd:element name="CostCenter" type="xsd:string"/>  
        <xsd:element name="Total" type="xsd:decimal"/>  
        <xsd:element name="Currency" type="xsd:string"/>  
        <xsd:element name="Description" type="xsd:string"/>  
      </xsd:sequence>  
    </xsd:complexType>  
  
    <xsd:element name="ExpenseReport" type="expense:expenseReportType"/>  
  
  </xsd:schema>' ;  
  
  CREATE MESSAGE TYPE  
    [//Adventure-Works.com/Expenses/SubmitExpense]  
    VALIDATION = VALID_XML WITH SCHEMA COLLECTION ExpenseReportSchema ;  
```  
  
### <a name="c-creating-a-message-type-for-an-empty-message"></a>C. 建立空訊息的訊息類型  
 下列範例會建立一個包含空白編碼的新訊息類型。  
  
```  
CREATE MESSAGE TYPE  
    [//Adventure-Works.com/Expenses/SubmitExpense]  
    VALIDATION = EMPTY ;  
```  
  
### <a name="d-creating-a-message-type-containing-binary-data"></a>D. 建立包含二進位資料的訊息類型  
 下列範例會建立用來存放二進位資料的新訊息類型。 由於訊息將包含不是 XML 的資料，因此，訊息類型會指定 `NONE` 驗證類型。 請注意，在這個情況下，接收這種類型之訊息的應用程式必須確認訊息包含資料，且資料的類型符合預期。  
  
```  
CREATE MESSAGE TYPE  
    [//Adventure-Works.com/Expenses/ReceiptImage]  
    VALIDATION = NONE ;  
```  
  
## <a name="see-also"></a>另請參閱  
 [變更訊息類型 &#40;TRANSACT-SQL &#41;](../../t-sql/statements/alter-message-type-transact-sql.md)   
 [卸除訊息類型 &#40;TRANSACT-SQL &#41;](../../t-sql/statements/drop-message-type-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
