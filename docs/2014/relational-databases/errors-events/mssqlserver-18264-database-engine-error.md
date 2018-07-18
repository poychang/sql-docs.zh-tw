---
title: MSSQLSERVER_18264 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 18264 (Database Engine error)
ms.assetid: 3050fc56-2be5-43cf-916b-50a3ac5f89aa
caps.latest.revision: 12
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4067cde7352144c9ade23999b85b7cdaf45d5f97
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37420127"
---
# <a name="mssqlserver18264"></a>MSSQLSERVER_18264
    
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|Microsoft SQL Server|  
|事件識別碼|18264|  
|事件來源|MSSQLENGINE|  
|元件|SQLEngine|  
|符號名稱|STRMIO_DBDUMP|  
|訊息文字|已備份的資料庫。 資料庫: %s，建立日期(時間): %s(%s)，傾印的分頁: %d，第一個 LSN: %s，最後一個 LSN: %s，傾印裝置的數量: %d，裝置資訊: (%s)。 此為參考用訊息， 使用者不必採取任何動作。|  
  
## <a name="explanation"></a>說明  
 根據預設，每個成功的備份都會將這個參考用訊息加入至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔和系統事件記錄檔。 如果您經常備份交易記錄，這些訊息可能會快速累積，因而建立非常龐大的錯誤記錄檔，讓您難以尋找其他訊息。  
  
## <a name="user-action"></a>使用者動作  
 您可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 追蹤旗標 **3226** 來隱藏這些記錄項目。 如果您正執行經常記錄備份，而且沒有任何指令碼相依於這些項目，啟用此追蹤旗標就會很有用。  
  
 如需有關使用追蹤旗標的詳細資訊，請參閱《SQL Server 線上叢書》。  
  
## <a name="see-also"></a>另請參閱  
 [追蹤旗標 &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)  
  
  