---
title: 商務物件上使用的用戶端向 DCOM |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- business objects in RDS [ADO]
ms.assetid: 75a21910-607f-463a-ae18-a17130dafb7e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4094d147e47bd39298b6dd94b4819eaa3d650eb6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47691006"
---
# <a name="registering-business-objects-on-the-client-for-use-with-dcom"></a>在用戶端上註冊商務物件以用於 DOM
自訂商務物件，就必須確保用戶端，可以將其程式名稱 (ProgId) 對應至可透過 DCOM 識別碼 (CLSID)。 基於這個理由，必須位於用戶端登錄 DCOM 物件的 ProgID，並將其對應至伺服器端商務物件的類別識別碼中。 其他支援之通訊協定 （HTTP、 HTTPS 和同處理序），這是不必要。  
  
> [!IMPORTANT]
>  從 Windows 8 和 Windows Server 2012 開始，RDS 伺服器元件不會再包含在 Windows 作業系統中 (請參閱 Windows 8 和[Windows Server 2012 相容性操作手冊](https://www.microsoft.com/en-us/download/details.aspx?id=27416)如需詳細資訊)。 RDS 用戶端元件將會在 Windows 的未來版本中移除。 請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。 使用 RDS 的應用程式應該移轉至[WCF 資料服務](http://go.microsoft.com/fwlink/?LinkId=199565)。  
  
 例如，如果呼叫 MyBObj 與特定的類別識別碼，例如，"{00112233-4455-6677-8899-00AABBCCDDEE}"的伺服器端商務物件公開 （expose） 請確定下列項目會新增至用戶端登錄：  
  
```  
[HKEY_CLASSES_ROOT]  
\MyBObj\Clsid\(Default) "{00112233-4455-6677-8899-00AABBCCDDEE}"  
```


