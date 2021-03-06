---
title: setResponseBuffering 方法 (SQLServerStatement) |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerStatement.setResponseBuffering(String responseBufferingValue)
apilocation:
- SQLServerStatement.setResponseBuffering(String responseBufferingValue)
apitype: Assembly
ms.assetid: 9f489835-6cda-4c8c-b139-079639a169cf
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 114bba1ad782a3cc14585267407386d30f4ac0b6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32845793"
---
# <a name="setresponsebuffering-method-sqlserverstatement"></a>setResponseBuffering 方法 (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  設定的回應緩衝模式，這個[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)物件以不區分大小寫**完整字串**或**適應性**。  
  
## <a name="syntax"></a>語法  
  
```  
  
public final void setResponseBuffering(java.lang.String value)  
```  
  
#### <a name="parameters"></a>參數  
 *value*  
  
 A**字串**包含回應緩衝模式。 有效的模式可以是下列的不區分大小寫字串的其中之一：**完整**或**適應性**。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 **自動調整**指定最小可能的資料在必要時緩衝處理。  
  
 **完整**指定在執行階段從伺服器讀取整個結果。  
  
 adaptive 是 JDBC Driver 2.0 和 3.0 版中的預設值。 full 是 JDBC Driver 2.0 版之前的預設值。  
  
 [SetResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)方法可讓您覆寫**responseBuffering**連接**字串**屬性目前[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)物件。 如需使用回應緩衝模式的詳細資訊，請參閱[使用適應性緩衝](../../../connect/jdbc/using-adaptive-buffering.md)。  
  
 如果應用程式指定了無效的參數值來[setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)方法， [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)就會擲回。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerStatement 成員](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement 類別](../../../connect/jdbc/reference/sqlserverstatement-class.md)   
 [使用適應性緩衝](../../../connect/jdbc/using-adaptive-buffering.md)  
  
  
