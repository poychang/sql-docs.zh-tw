---
title: SQLFreeConnect 對應 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLFreeConnect
- SQLFreeConnect function [ODBC], mapping
ms.assetid: 8a844538-93c0-4709-bab6-35c45e771d80
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ef90025a129bc624377bfe7891f122a838180a51
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47695656"
---
# <a name="sqlfreeconnect-mapping"></a>SQLFreeConnect 對應
當應用程式呼叫**SQLFreeConnect**透過 ODBC 3 *.x*驅動程式，會呼叫  
  
```  
SQLFreeConnect(hdbc)   
```  
  
 對應至  
  
```  
SQLFreeHandle(SQL_HANDLE_DBC,Handle)  
```  
  
 具有*處理*引數設定中的值為*hdbc*。
