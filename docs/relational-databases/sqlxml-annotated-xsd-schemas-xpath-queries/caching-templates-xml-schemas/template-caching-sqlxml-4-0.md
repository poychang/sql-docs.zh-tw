---
title: 範本快取 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- templates [SQLXML], caching
ms.assetid: 73e151c6-b24e-4422-a116-51e0846bc6f5
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: cade212f2f669190ce8c771c912a8d8147f7e161
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47704576"
---
# <a name="template-caching-sqlxml-40"></a>範本快取 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  範本快取會大幅改善效能。 如果設定範本快取，範本在第一次執行後仍會保留在記憶體中。 這樣可以增進後續執行範本的效能。  
  
 您可以在登錄中加入下列機碼來設定範本快取大小：  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\TemplateCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 範本大小應該根據可用的記憶體以及您要使用的範本數目來設定。 預設值是**TemplateCacheSize**大小為 31。 如果範本存取速度似乎緩慢，您可以增加快取大小，或者如果記憶體不足，則減少快取大小。  
  
 為了達到最佳效能，建議您設定**TemplateCacheSize**比您通常使用的範本數目高。 如果**TemlateCacheSize**小於您擁有的範本數目，效能會隨著範本增加數目。 **TemplateCacheSize**可以設為上限 128。  
  
 每次使用快取的範本時，就會檢查範本檔的修改時間以查看該範本檔是否需要重新整理。 這是因為磁碟副本比快取副本新的緣故。  
  
> [!NOTE]  
>  系統不會快取範本參數和命令屬性。  
  
## <a name="see-also"></a>另請參閱  
 [結構描述快取&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/schema-caching-sqlxml-4-0.md)   
 [XSL 快取&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/xsl-caching-sqlxml-4-0.md)  
  
  
