---
title: 建立明確階層 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating explicit hierarchies [Master Data Services]
- explicit hierarchies, creating
ms.assetid: ba768393-6990-4eda-8cb0-d58cb3cfc2e2
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 71c695a31aacf146bf2e97dd0ad4a38044d6b8b5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48083578"
---
# <a name="create-an-explicit-hierarchy-master-data-services"></a>建立明確階層 (Master Data Services)
  當您需要成員可存在於任何層級的不完全階層時，可以在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中建立明確階層。 明確階層包含來自單一實體的成員。  
  
 建立明確階層之後，您可以在總管 功能區域的這個階層中加入成員。  
  
## <a name="prerequisites"></a>先決條件  
 若要執行此程序：  
  
-   您必須擁有存取 **[系統管理]** 功能區域的權限。  
  
-   您必須是模型管理員。 如需詳細資訊，請參閱 [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md) (管理員 (Master Data Services))。  
  
-   您必須啟用明確階層和集合的實體。 如需詳細資訊，請參閱 <<c0> [ 啟用明確階層和集合的實體&#40;Master Data Services&#41;](../../2014/master-data-services/enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)。</c0>  
  
### <a name="to-create-an-explicit-hierarchy"></a>若要建立明確階層  
  
1.  在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[系統管理]**。  
  
2.  在 **[模型檢視]** 頁面上，從功能表列指向 **[管理]** ，然後按一下 **[實體]**。  
  
3.  在 **[實體維護]** 頁面上，選取 **[模型]** 清單中的模型。  
  
4.  針對要建立明確階層的實體選取資料列。  
  
5.  按一下 **[編輯選取的實體]**。  
  
6.  在 **編輯實體**頁面上，於**明確階層**窗格中，按一下 **加入明確階層**。  
  
7.  在 **加入明確階層**頁面上，於**明確階層名稱**方塊中，輸入階層的名稱。  
  
8.  (選擇性) 清除 [強制階層] 核取方塊，將階層建立為非強制階層。 如需階層類型的詳細資訊，請參閱[明確階層 &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)。  
  
9. 按一下 **儲存階層**。  
  
10. 在 **編輯實體**頁面上，按一下**儲存實體**。  
  
## <a name="next-steps"></a>後續步驟  
  
-   [建立合併的成員&#40;Master Data Services&#41;](../../2014/master-data-services/create-a-consolidated-member-master-data-services.md)  
  
-   [在階層中移動成員&#40;Master Data Services&#41;](../../2014/master-data-services/move-members-within-a-hierarchy-master-data-services.md)  
  
## <a name="see-also"></a>另請參閱  
 [明確階層&#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)   
 [具有明確頂層的衍生階層 &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)   
 [變更明確階層名稱&#40;Master Data Services&#41;](../../2014/master-data-services/change-an-explicit-hierarchy-name-master-data-services.md)  
  
  
