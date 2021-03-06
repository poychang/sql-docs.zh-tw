---
title: 設定量值屬性 |Microsoft 文件
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e579d8090300e205e99807f8016be066f557b6fb
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
ms.locfileid: "34022225"
---
# <a name="configure-measure-properties"></a>設定量值屬性
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  量值有一些屬性可讓您定義量值的運作方式以及控制量值讓使用者看到的樣子。  
  
 您可以在建立或編輯 Cube 或量值時，在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中設定屬性。 您也可以使用 MDX 或 AMO，透過程式設計方式來設定這些屬性。 如需詳細資訊，請參閱[在多維度模型中建立量值和量值群組](../../analysis-services/multidimensional-models/create-measures-and-measure-groups-in-multidimensional-models.md)、[CREATE MEMBER 陳述式 &#40;MDX&#41;](../../mdx/mdx-data-definition-create-member.md) 或[設計 AMO OLAP 基本物件的程式](../../analysis-services/multidimensional-models/analysis-management-objects/programming-amo-olap-basic-objects.md)。  
  
## <a name="measure-properties"></a>量值屬性  
 量值會從其隸屬為成員的量值群組中繼承特定屬性，除非這些屬性在量值層級受到覆寫。 量值屬性決定如何彙總量值、量值的資料類型、向使用者顯示的名稱、量值所在的顯示資料夾、量值的格式字串、任何量值運算式、基礎來源資料行，以及對使用者的可見性。  
  
|屬性|定義|  
|--------------|----------------|  
|**AggregateFunction**|必要。 決定如何彙總量值。 **Sum** 為預設彙總。 如需詳細資訊，請參閱 [使用彙總函式](../../analysis-services/multidimensional-models/use-aggregate-functions.md) 中每個函數的描述。|  
|**DataType**|必要。 指定量值所繫結之基礎事實資料表資料行的資料類型。 這個值預設從來源資料行繼承而來。|  
|**說明**|提供量值的描述，可以在用戶端應用程式中公開。|  
|**DisplayFolder**|指定使用者連接到 Cube 時，可在其中看到量值的資料夾。 Cube 具有許多量值時，您可使用顯示資料夾來分類量值，並改進使用者瀏覽經驗。|  
|**FormatString**|您可使用屬性的 **FormatString** 屬性，來選取用於對使用者顯示量值的格式。<br /><br /> 雖然 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]會提供顯示格式的清單，但您仍可指定清單中未提供的其他格式。 您可以指定在 Microsoft Visual Basic 中有效的任何具名格式或使用者自訂格式。|  
|**識別碼**|必要。 顯示量值的唯一識別碼 (ID)。 此屬性是唯讀的。|  
|**MeasureExpression**|指定受條件約束的 MDX 運算式來定義量值的值。 運算式會在彙總之前，先在分葉層級求取值，以便於對值進行加權。 例如，在匯率轉換時，銷售金額會以匯率加權。|  
|**名稱**|必要。 指定量值的名稱。|  
|**Source**|必要。 指定量值所繫結之資料來源檢視中的資料行。 請參閱[資料來源和繫結 &#40;SSAS 多維度&#41;](../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)。|  
|**Visible**|指定量值是否要在用戶端應用程式中顯示。|  
  
## <a name="see-also"></a>另請參閱  
 [設定量值群組屬性](../../analysis-services/multidimensional-models/configure-measure-group-properties.md)   
 [修改量值](../../analysis-services/lesson-3-1-modifying-measures.md)  
  
  
