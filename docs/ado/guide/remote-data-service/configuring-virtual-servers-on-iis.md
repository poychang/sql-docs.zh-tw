---
title: 在 IIS 上設定虛擬伺服器 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- virtual servers in RDS [ADO]
ms.assetid: 2b4786c6-40c4-4ce1-9ad4-03df436e0aff
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f11a031189cd184b2ad91430a059a0352c8fc18c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47684253"
---
# <a name="configuring-virtual-servers-on-iis"></a>在 IIS 上設定虛擬伺服器
在建立虛擬伺服器在網際網路資訊服務 4.0 時，若要設定虛擬伺服器，以使用 RDS 需要下列兩個額外的步驟：  
  
1.  當設定伺服器，請檢查 「 允許執行存取 」。  
  
2.  移至 msadcs.dll *vroot*\msadc，其中*vroot*是您的虛擬伺服器的主目錄。  
  
> [!IMPORTANT]
>  從 Windows 8 和 Windows Server 2012 開始，RDS 伺服器元件不會再包含在 Windows 作業系統中 (請參閱 Windows 8 和[Windows Server 2012 相容性操作手冊](https://www.microsoft.com/en-us/download/details.aspx?id=27416)如需詳細資訊)。 RDS 用戶端元件將會在 Windows 的未來版本中移除。 請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。 使用 RDS 的應用程式應該移轉至[WCF 資料服務](http://go.microsoft.com/fwlink/?LinkId=199565)。  
  
## <a name="see-also"></a>另請參閱  
 [RDS 基本概念](../../../ado/guide/remote-data-service/rds-fundamentals.md)


