---
title: "資料指標程式庫作業 |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC cursor library [ODBC], backward compatibility
- compatibility [ODBC], cursor library
- upgrading applications [ODBC], cursor library
- application upgrades [ODBC], cursor library
- backward compatibility [ODBC], cursor library
- cursor library [ODBC], backward compatibility
ms.assetid: 04d514b1-dc4d-4b84-bf35-60f4657ef1f6
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 00469dcf77ae81f5d02765026fe0c1f7194da5d1
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="cursor-library-operations"></a>資料指標程式庫作業
> [!IMPORTANT]  
>  將移除這項功能，在未來的版本的 Windows。 避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。 Microsoft 建議使用驅動程式的資料指標功能。  
  
 如果應用程式使用 ODBC 2*.x*驅動程式會呼叫 ODBC 3。*x*資料指標程式庫，應用程式可能無法使用 ODBC 3。*x* ODBC 2 不支援的功能*.x*驅動程式。 如何使用這些功能，不過應用程式寫入器應該要特別小心。 使用 ODBC 3。*x*資料指標程式庫並不會讓 ODBC 2*.x* ODBC 3 驅動程式。*x*驅動程式。