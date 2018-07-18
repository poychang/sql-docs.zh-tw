---
title: 檢視外部索引鍵屬性 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- foreign keys [SQL Server], attributes
- displaying foreign keys attributes
- viewing foreign keys attributes
ms.assetid: b0e57cb7-9b26-4b96-b76a-1f59f5f498c5
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a5266731ce16988dd9ed8dbc82d2f6c002c846ba
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37331358"
---
# <a name="view-foreign-key-properties"></a>檢視外部索引鍵屬性
  您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中檢視關聯性的外部索引鍵屬性。  
  
 **本主題內容**  
  
-   **開始之前：**  
  
     [Security](#Security)  
  
-   **使用下列方法，檢視特定資料表的外部索引鍵屬性：**  
  
     [Transact-SQL](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> 權限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 如需相關資訊，請參閱 [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md)。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-view-the-foreign-key-attributes-of-a-relationship-in-a-specific-table"></a>檢視特定資料表中之關聯性的外部索引鍵屬性  
  
1.  針對包含您要檢視外部索引鍵的資料表開啟 [資料表設計工具]，以滑鼠右鍵按一下 [資料表設計工具]，然後從快速鍵功能表選擇 [關聯性]。  
  
2.  從 [ **外部索引鍵關聯性** ] 對話方塊中，選取具備您想要檢視之屬性的關聯性。  
  
 如果外部索引鍵資料行與主索引鍵相關聯，主索引鍵資料行會在 **[資料表設計工具]** 內由資料列選取器中的主索引鍵符號識別。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
  
#### <a name="to-view-the-foreign-key-attributes-of-a-relationship-in-a-specific-table"></a>檢視特定資料表中之關聯性的外部索引鍵屬性  
  
1.  在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。  
  
2.  在標準列上，按一下 **[新增查詢]**。  
  
3.  複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]**。 此範例會針對範例資料庫中的 `HumanResources.Employee` 資料表傳回所有外部索引鍵及其屬性。  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT   
        f.name AS foreign_key_name  
       ,OBJECT_NAME(f.parent_object_id) AS table_name  
       ,COL_NAME(fc.parent_object_id, fc.parent_column_id) AS constraint_column_name  
       ,OBJECT_NAME (f.referenced_object_id) AS referenced_object  
       ,COL_NAME(fc.referenced_object_id, fc.referenced_column_id) AS referenced_column_name  
       ,is_disabled  
       ,delete_referential_action_desc  
       ,update_referential_action_desc  
    FROM sys.foreign_keys AS f  
    INNER JOIN sys.foreign_key_columns AS fc   
       ON f.object_id = fc.constraint_object_id   
    WHERE f.parent_object_id = OBJECT_ID('HumanResources.Employee');  
    ```  
  
 如需詳細資訊，請參閱 [sys.foreign_keys &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-foreign-keys-transact-sql) 和 [sys.foreign_key_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-foreign-key-columns-transact-sql)。  
  
###  <a name="TsqlExample"></a>  