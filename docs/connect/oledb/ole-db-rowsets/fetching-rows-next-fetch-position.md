---
title: 下一個提取位置 |Microsoft 文件
description: 提取資料列的下一個提取位置
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- next fetch position
- rowsets [OLE DB], fetching
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 58dc620996d8cba998ce8efbd5bcd3f3bbfa3e31
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2018
---
# <a name="fetching-rows---next-fetch-position"></a>提取資料列的下一個提取位置
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  OLE DB 驅動程式的 SQL Server 會持續追蹤的下一個提取位置因此的一連串的呼叫**GetNextRows**方法 (沒有略過，變更方向，或中介的呼叫**FindNextRow****搜尋**，或**的 restartposition 於**方法) 而略過或重複任何資料列不會讀取整個資料列集。 下一個提取位置的變更方式呼叫**irowset:: Getnextrows**， **irowset:: Restartposition**，或**irowsetindex:: Seek**，或藉由呼叫**FindNextRow**具有 null *Findnextrow*值。 呼叫**FindNextRow**包含非 null *Findnextrow*值不會影響下一個提取位置。  
  
## <a name="see-also"></a>另請參閱  
 [提取資料列](../../oledb/ole-db-rowsets/fetching-rows.md)  
  
  