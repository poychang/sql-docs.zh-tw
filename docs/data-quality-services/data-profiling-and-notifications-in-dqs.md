---
title: DQS 中的資料分析與通知 | Microsoft Docs
ms.custom: ''
ms.date: 10/01/2012
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology:
- data-quality-services
ms.topic: conceptual
ms.assetid: a778bb5b-8e35-4a7b-b04a-ae2b46dec21b
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8b54015726aa5e442326281c620db0399e709e8e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47764446"
---
# <a name="data-profiling-and-notifications-in-dqs"></a>DQS 中的資料分析與通知

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中的資料分析程序會分析現有資料來源中的資料，以及顯示有關 DQS 活動資料的統計資料。 此程序為您提供資料品質的自動化度量。 DQS 分析會整合到 DQS 知識管理與資料品質專案中。 它是動態的，而且可以調整。 分析有兩個主要目標：首先是在資料品質程序中引導您並支援您的決策，第二個目標是評估程序的效用。 DQS 分析程序的優點如下：  
  
-   分析會提供來源資料品質的洞察能力，並幫助您識別資料品質問題。  
  
-   分析會評估資料品質程序的效用，引導您進行知識探索、資料清理、比對原則和比對工作。  
  
-   分析為您呈現最相關之時間的最相關資訊。  
  
-   分析程序產生的通知會強調可能會保證動作的重要統計資料或事件。 在許多情況下，DQS 通知將會指示情況，並建議補救該狀況所可以採取的動作。  
  
 分析讓您不僅將 Data Quality Services 用於知識探索、清理和比對，也可以當做分析工具。 您可能會想要建立一個知識庫進行分析，並使用該知識庫執行知識探索，根據分析統計資料判斷此知識庫是否滿足您的探索、清理和比對需求。  
  
##  <a name="How"></a> 分析的運作方式  
 分析不會衡量知識庫的品質。 而會衡量來源資料的品質。 分析為您提供的統計資料會指示您在知識管理或是來源資料的資料品質專案中所執行之特定作業的效果。 分析一定會在您所執行之特定活動的內容中。 您可以按一下畫面上的分析索引標籤，以顯示分析資料，而不用離開您所執行之活動的階段。 執行此程序時會即時擴展分析資料表，好讓您在執行資料品質工作時加以評估。 您可以在清理或刪除重複作業之後判斷來源資料是否變得比較好以及變好的程度。  
  
 所有分析數字都會參考某個值出現的次數，在許多情況下也會參考總計的百分比，但是唯一性度量例外。 唯一性度量會參考值的絕對數目，不論這些值出現多少次。  
  
 分析是 DQS 知識驅動之方案的一部分。 它會根據資料來源欄位與知識庫定義域之間的對應，提供有關知識庫、比對或資料清理程序的資訊。 只有在完成對應之後才會執行分析；任何活動的對應階段期間都不會執行分析。 分析一定會附加至活動。 分析程序會針對對應至定義域的資料 (而不是定義域中的資料) 來執行。 分析會整合到以下的活動步驟中：  
  
-   知識探索活動的 **[探索]** 和 **[管理定義域值]** 步驟  
  
-   清理活動的 **[清理]** 和 **[管理和檢視結果]** 步驟  
  
-   比對原則活動的 **[比對原則]** 和 **[比對結果]** 步驟  
  
-   比對活動的 **[比對]** 和 **[匯出]** 步驟  
  
 DQS 不會提供 [定義域管理] 活動的分析統計資料。  
  
##  <a name="Activity"></a> 依據活動分析資料  
 DQS 分析會使用標準資料品質維度來表示資料的品質：完整性 (資料存在的程度) 和精確度 (可將資料用於預定用途的程度)，以及唯一性 (不同值代表不同實體的程度)。 根據預設，NULL 和空白值會被視為遺漏或低於完整性百分比；但是，您也可以將其他值定義為等於 NULL，此時這些值也會被視為遺漏。  
  
 分析為您提供評估程序所需的統計資料，但是您必須解譯這些統計資料。 請按資料行逐一查看這些統計資料，以理解分析要告訴您什麼事。  
  
 DQS 活動具有不同的分析統計資料集合，如下所示：  
  
-   只有清理活動才擁有精確度分析統計資料 (依定義域以百分比表示)。 精確度會受到有效性、一致性、語法錯誤和定義域規則的影響。  
  
-   只有清理活動才擁有來源中之正確、已更正和建議的分析統計資料，以及依定義域的更正和建議值 (兩個數字都是以百分比表示)。  
  
-   清理和知識探索活動具有有效性的分析統計資料 (依記錄的清理，以及依記錄和定義域的知識探索)。 比對原則和比對活動沒有有效性的統計資料。  
  
-   清理活動沒有唯一性的分析統計資料。 知識探索、比對原則和比對活動具有唯一性的分析統計資料 (針對來源以及依定義域以數字和百分比表示)。  
  
 如需有關與活動相關之特定分析統計資料的詳細資訊，請參閱以下主題中的分析章節：  
  
-   [執行知識探索](../data-quality-services/perform-knowledge-discovery.md)  
  
-   [使用 DQS &#40;內部&#41; 知識清理資料](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)  
  
-   [建立比對原則](../data-quality-services/create-a-matching-policy.md)  
  
-   [執行比對專案](../data-quality-services/run-a-matching-project.md)  
  
##  <a name="Monitoring"></a> 活動監控中的分析資料  
 知識探索、比對原則、比對和清理活動的分析資訊不但有在 Data Quality Client 活動頁面中提供，活動監控中也有提供。 活動監控為您提供目前和過去活動的概觀。 除了活動的屬性及相關的計算程序之外，您也可以檢視針對某個位置的每一個活動所產生的分析資訊。 您可在活動資料表中選取活動，於底下的資料表中顯示分析結果。 您也可以匯出分析結果。 如需詳細資訊，請參閱 [DQS Administration](../data-quality-services/dqs-administration.md)。  
  
##  <a name="Notifications"></a> 通知  
 除了透過分析來收集及顯示重要統計資料與度量以外，DQS 也會產生通知 (如果啟用的話)，以指示您何時可能會想要根據顯示的分析統計資料來採取動作。 DQS 會使用通知來強調有關資料來源的重要事實，並顯示目前活動相對於其執行目的的效用。 通知所提供的提示與建議會指示情況，並建議您如何改善知識探索、資料清理或資料比對活動。  
  
 DQS 通知是用來引發您可能會感興趣的問題，或是對付潛在問題。 您是否要對通知採取行動取決於該通知是否與您的目的相關。 例如，假設 DQS 在以下情況下發佈通知：資料清理未產生任何更正值或建議值，而完整性與精確度同時為 100%。 此通知指示，該活動可能不需要執行。 但是，不論您是否選擇執行活動，都是您自己的決定。  
  
 通知是由工具提示中， **[分析]** 索引標籤中的驚嘆號所指示。與通知有關的統計資料會以紅色顯示，以指示該通知的統計理由。  
  
 您可以在 Data Quality Client 首頁之 **[管理]** 區段的 **[一般設定]** 索引標籤中，啟用 (預設值) 或停用通知。 當停用通知時，工具提示並不會顯示，而且統計資料不會以紅色表示。 停用通知並不會顯著改善效能。 如果您停用通知，分析依然可運作。  
  
 如果是與活動之通知有關的特定情況，請參閱下列資源：  
  
-   [執行知識探索](../data-quality-services/perform-knowledge-discovery.md)  
  
-   [使用 DQS &#40;內部&#41; 知識清理資料](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)  
  
-   [建立比對原則](../data-quality-services/create-a-matching-policy.md)  
  
-   [執行比對專案](../data-quality-services/run-a-matching-project.md)  
  
## <a name="related-tasks"></a>相關工作  
  
|工作描述|主題|  
|----------------------|-----------|  
|描述如何啟用或停用 DQS 中的通知。|[啟用或停用 DQS 中的分析通知](../data-quality-services/enable-or-disable-profiling-notifications-in-dqs.md)|  
  
  
