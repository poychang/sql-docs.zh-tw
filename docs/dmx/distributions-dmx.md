---
title: 散發 (DMX) |Microsoft 文件
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e4ffd21a2b507e03af6534296715528d83aac0f6
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "37992030"
---
# <a name="distributions-dmx"></a>散發 (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  在  [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]，您可以定義採礦結構，以影響您建立採礦模型時演算法如何處理這些資料行中的資料中的資料行的內容。 針對某些演算法，若已知資料行包含值的通用散發，則在處理模型前先定義任何連續資料行的散發很有用。 如果您未定義散發，則產生之採礦模型所做出的預測，可能不如定義了散發的預測那般精確，因為演算法能用來解譯資料的資訊比較少。  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] 資料採礦演算法支援下列散發類型：  
  
 **標準模式**  
 連續資料行的值形成一般高斯分佈的長條圖。  
  
 **Log Normal**  
 連續資料行的值形成長條圖，其中值的對數為一般分佈。  
  
 **統一**  
 連續資料行的值形成平坦曲線，其中所有值的機率都相當之。  
  
 如需詳細資訊[!INCLUDE[msCoName](../includes/msconame-md.md)]資料採礦演算法，請參閱[資料採礦演算法&#40;Analysis Services-Data Mining&#41;](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)。 協力廠商演算法提供者可能支援其他的散發類型。 若要判斷哪一個分佈類型演算法支援，請使用**SUPPORTED_DISTRIBUTION_FLAGS**結構描述資料列。  
  
 如需散發類型的詳細資訊，請參閱[資料行散發&#40;資料採礦&#41;](../analysis-services/data-mining/column-distributions-data-mining.md)。  
  
## <a name="see-also"></a>另請參閱  
 [內容類型&#40;資料採礦&#41;](../analysis-services/data-mining/content-types-data-mining.md)   
 [資料採礦延伸模組&#40;DMX&#41;參考](../dmx/data-mining-extensions-dmx-reference.md)   
 [資料採礦延伸模組&#40;DMX&#41;語法元素](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [資料採礦延伸模組&#40;DMX&#41;函式參考](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [資料採礦延伸模組&#40;DMX&#41;運算子參考](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [資料採礦延伸模組&#40;DMX&#41;陳述式參考](../dmx/data-mining-extensions-dmx-statements.md)   
 [資料採礦延伸模組&#40;DMX&#41;語法慣例](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [一般預測函數&#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [結構和使用方式的 DMX 預測查詢](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [了解 DMX Select 陳述式](../dmx/understanding-the-dmx-select-statement.md)  
  
  
