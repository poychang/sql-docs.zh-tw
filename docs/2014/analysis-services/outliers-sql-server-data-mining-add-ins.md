---
title: 極端值 （SQL Server 資料採礦增益集） |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- exceptions [data mining]
- data preparation
- outliers [data mining]
- data cleaning
ms.assetid: e6fa7c62-4005-4792-9211-3b699377a517
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0771c953875e9871c53892bc14a3e2a537060833
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48224109"
---
# <a name="outliers-sql-server-data-mining-add-ins"></a>極端值 (SQL Server 資料採礦增益集)
  ![資料採礦功能區中的極端值精靈](media/dmc-outliers.gif "資料採礦功能區中的極端值精靈")  
  
 *極端值*表示資料值的任何一個，因為下列原因會造成問題：  
  
-   值在預期的範圍之外。  
  
-   資料可能未正確輸入。  
  
-   值遺失。  
  
-   資料是由空格或其他 null 字串組成。  
  
-   值是正確的，不過目前仍是在分佈範圍之外，可能大幅影響模型。  
  
 適用於 Excel 的資料採礦用戶端可協助您偵測此資料，然後升級這些值或隱藏這些值。 例如，您可以用算術平均值來取代極端值，或是可以刪除可能包含錯誤值的資料列。  
  
## <a name="handling-outliers"></a>處理極端值  
 **移除極端值**精靈為您提供數個工具來適當地處理極端值：  
  
-   首先，您可以瀏覽資料來進一步了解值的分佈以及極端值與其他資料的關係。  
  
     例如，您可以使用**瀏覽資料**工作，以檢閱並修正值。 **移除極端值**精靈也會顯示一條線或橫條圖，以協助您了解所有值的分佈的圖形。  
  
-   接下來，您可以使用**極端值**精靈來移除或變更極端值。 您使用的方法取決於值為離散或連續而定。  
  
     此精靈會將離散值顯示在橫條圖中，每一橫條都代表特定的值，而該橫條的高度則代表每個值的案例數。 藉由滑動圖形上的臨界值控制項，您可以切掉代表過於極端或可能有錯誤值之群組的橫條。  
  
-   此精靈會在橫條圖或折線圖上顯示連續的值。 在折線圖上，值是由 X 軸上的值表示，而計數值則是由 Y 軸上的值表示。  
  
     您可以控制是否要移除或保留在圖表的下限和上限結尾的值，藉由變更**最小**並**上限**值，或是滑動列。 當您變更最小和最大值設定時，將會隱藏的資料會以圖中的陰影來顯示。  
  
 在您選取要處理的極端值之後，您會告訴精靈要如何處理極端值。 您可以刪除包含極端值的資料列，或是可以指定取代值，如平均值、null 或另一個您所選擇的值。  
  
 最後，此精靈會提供您一些選項來顯示新的資料。 您可以用新的值取代原始資料、將新資料行加入包含新值的資料表，或是建立包含更新資料的新工作表。  
  
### <a name="using-the-outlier-wizard"></a>使用極端值精靈  
  
1.  在**資料採礦**功能區中，按一下**清理資料**，然後選取**極端值**。  
  
2.  在 **選取來源資料** 對話方塊中，選取 Excel 資料表或資料格範圍，然後按一下**下一步**。  
  
    > [!WARNING]  
    >  您無法使用**極端值**精靈的外部資料，除非您將它複製到 Excel 第一次。  
  
3.  在 [**選取資料行**] 對話方塊中，選取**單一**資料行。  
  
     按 [下一步] 。  
  
4.  在 **指定臨界值**對話方塊方塊中，檢閱資料的分佈。  
  
    -   如果資料行包含離散值，則精靈會顯示包含每個離散值計數的長條圖。  
  
         假設極端值會是很少見的值，您可以篩選出變更**最小值**值。  
  
    -   如果資料行包含數值資料，您可以按一下**以離散方式檢視** 按鈕或**以數值方式檢視**值中的橫條圖或折線圖的檢視之間切換 按鈕。  
  
5.  在 **指定臨界值**對話方塊方塊中，選擇您想要保留輸入最小和最大值或是拖曳滑動軸的資料範圍。 按 [下一步] 。  
  
6.  在 [**極端值處理**對話方塊，指定是否要刪除或取代的值，然後按一下**下一步]**。  
  
7.  在 **選取目的地**對話方塊方塊中，指定您想要儲存新的資料。  
  
### <a name="related-options"></a>相關的選項  
 精靈提供下列選項：  
  
|**選項。**|**註解**|  
|-----------------|-----------------|  
|**選取資料行**|您一次只能使用一個資料行。|  
|**指定臨界值處理方式**|設定臨界值，使用**最小值**來排除資料列少於臨界值中找到的值。<br /><br /> 一開始是中的值**最小**相等的值與最少的資料列，而且您不能做出最小值低於該值。|  
|**極端值處理**|如果您決定刪除極端值，可以變更目前工作表中的資料，或是在新工作表中建立資料複本。|  
  
## <a name="see-also"></a>另請參閱  
 [瀏覽資料&#40;SQL Server 資料採礦增益集&#41;](explore-data-sql-server-data-mining-add-ins.md)  
  
  
