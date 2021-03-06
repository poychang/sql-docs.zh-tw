---
title: 導覽存取權 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- navigational access [Master Data Services]
- security [Master Data Services], navigational access
ms.assetid: 3403b7b0-44e2-48c3-a1b7-9c4612b874b8
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 20f3e8f8d51231f823fe43a8aeff4e606a10ffa2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48087198"
---
# <a name="navigational-access-master-data-services"></a>導覽存取權 (Master Data Services)
  導覽存取權會套用至模型物件安全性 (在 **[模型]** 索引標籤上指派)。  
  
 導覽存取權就是比您已指派安全性之層級還高的層級存取權。  
  
 在此範例中，權限會指派給實體，因此導覽存取權是在模型層級授與。  
  
 ![mds_conc_inheritance_model](../../2014/master-data-services/media/mds-conc-inheritance-model.gif "mds_conc_inheritance_model")  
  
 **實體**  
  
 當您指派權限給實體、其分葉成員或其合併成員時，導覽存取權就表示您可以讀取或更新所有成員的名稱和程式碼。 您也可以讀取模型名稱。  
  
 **屬性**  
  
 當您指派權限給屬性時，導覽存取權就表示您可以讀取或更新實體中所有成員的名稱和程式碼。 您也可以讀取模型名稱。  
  
 **集合**  
  
 當您指派權限給集合時，您可以讀取或更新名稱、程式碼、描述和擁有者識別碼。 您也可以讀取模型名稱。  
  
## <a name="see-also"></a>另請參閱  
 [如何決定權限&#40;Master Data Services&#41;](how-permissions-are-determined-master-data-services.md)  
  
  
