---
title: 模型權限 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], permissions
- permissions [Master Data Services], models
ms.assetid: 210f440b-2cc1-4c49-94b1-3a97e2af7bc3
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 29269184b63f32c02d2386d0e75757b748c5bd2f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48112718"
---
# <a name="model-permissions-master-data-services"></a>模型權限 (Master Data Services)
  模型權限適用於所有實體、衍生階層、明確階層及存在於模型內的集合。 可以針對任何個別的物件來覆寫指派給模型的權限。  
  
> [!NOTE]  
>  如果使用者是模型管理員，則使用者介面的所有功能區域中都會顯示此模型。 否則，此模型只會顯示在 [總管] 功能區域中。 如需詳細資訊，請參閱 [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md) (管理員 (Master Data Services))。  
  
|權限|描述|  
|----------------|-----------------|  
|**唯讀**|在 **總管**，會顯示此模型，但使用者無法加入或移除成員，也無法更新屬性值、 階層成員資格或集合成員資格。|  
|**Update**|在 **總管**模型會顯示，而且使用者可以新增和移除成員，可以更新屬性值、 階層成員資格和集合成員資格。|  
|**拒絕**|不顯示模型。|  
  
 當您將權限指派給模型時，使用者會取得模型之所有版本的存取權。 您無法將權限指派給個別的版本。  
  
## <a name="see-also"></a>另請參閱  
 [指派模型物件權限&#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)   
 [模型物件權限&#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [實體權限 &#40;Master Data Services&#41;](../../2014/master-data-services/entity-permissions-master-data-services.md)   
 [集合權限 &#40;Master Data Services&#41;](../../2014/master-data-services/collection-permissions-master-data-services.md)  
  
  
