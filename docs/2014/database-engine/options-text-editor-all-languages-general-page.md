---
title: 選項 （文字編輯器-所有語言-一般頁面） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.All_Languages.General
ms.assetid: bf18907c-94e2-4c09-9b2b-0925ac04c627
caps.latest.revision: 28
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 39394ea71a428d634bcee27adc2b76a3fca4af02
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37189075"
---
# <a name="options-text-editor---all-languages---general-page"></a>選項 (文字編輯器 - 所有語言 - 一般頁面)
  使用這個對話方塊可設定 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中，全部五個編輯器的一般編輯選項。 若要顯示這些選項，請按一下 [工具] 功能表上的 [選項]。 選取 [文字編輯器] 資料夾，展開 [所有語言] 資料夾，然後按一下 [一般]。  
  
## <a name="option-settings-by-editor"></a>依編輯器的選項設定  
 您必須使用 [所有語言] 對話方塊設定 DMX、MDX 和 SQL Server Compact 編輯器的選項。 在此處設定的選項也會套用至純文字、Transact-SQL 和 XML 編輯器，不過，藉由展開這些語言的子資料夾，然後選取其選項頁面，您就可以個別為這些編輯器設定選項。  
  
> [!CAUTION]  
>  如果您使用這個對話方塊設定選項，但是想要為純文字、Transact-SQL 或 XML 編輯器進行不同的設定，則必須先在 [所有語言] 對話方塊中套用您的選取範圍，再設定這些編輯器的選項。  
  
 某些編輯器可能不支援此頁面中列出的全部選項。 有些程式語言在 [選項] 對話方塊的 [一般] 頁面上，已經選取的選項會顯示灰色核取記號，但有些程式語言則不會。  
  
## <a name="statement-completion"></a>陳述式完成  
 **自動列出成員**  
 顯示您在編輯器中輸入的可用成員、屬性或值的快顯清單。 從快顯清單中選擇任何項目，以將項目插入程式碼。 選取此核取方塊會啟用 [隱藏進階成員] 選項。  
  
 **隱藏進階成員**  
 透過只顯示那些最常使用的項目來縮短快顯陳述式完成清單。 從清單中篩選其他項目。 如果沒有成員標示為進階成員，就不能使用此選項。  
  
 **參數資訊**  
 將目前宣告或程序的完整語法及其所有可用的參數顯示在編輯器插入點的左邊。 您可以指派的下一個參數會以粗體顯示。  
  
## <a name="settings"></a>[設定]  
 **啟用虛擬空間**  
 將註解放在程式碼旁邊的一致位置上。 選取這個核取方塊時，您可將游標放在資料列的最後一個字元後面。 輸入時，會自動在插入點加入 Tab 鍵或空格，以完成資料列。  
  
 **自動換行**  
 在下一行顯示横向超出可檢視編輯器區域之行的任何部分。 選取這個核取方塊將啟用 **[顯示自動換行的視覺化圖像]** 選項。  
  
 **顯示自動換行的視覺化圖像**  
 顯示換行箭頭指標，其中過長的行就會自動換行到第二行。  
  
> [!NOTE]  
>  這些提醒箭頭不會加入您的程式碼中，且不會列印。 它們僅供參考。 不是所有類型的編輯器都有此功能。  
  
 **沒有選取項目時，套用剪下/複製命令至空白行**  
 設定當您將插入點放置在空白行上、不選取任何內容，然後按一下 **[複製]** 或 **[剪下]** 時的編輯器行為。  
  
 如果選取此核取方塊，就會複製或剪下空白行。 接著，如果您按一下 **[貼上]**，就會插入一個新的空白行。  
  
 如果清除此核取方塊，就不會複製或剪下任何內容。 接著，您按一下 **[貼上]**，就會貼上最近複製的內容。 如果沒有進行複製，就不會有貼上動作。  
  
 當行不是空白時，此設定對 [複製] 或 [剪下] 命令沒有作用。 如果沒有選取內容，就會複製或剪下整個行。 接著，如果您按一下 **[貼上]**，就會貼上整行的文字與其結束字元。  
  
## <a name="display"></a>顯示器  
 **行號**  
 在每一行程式碼旁邊顯示行號。  
  
> [!NOTE]  
>  這些行號不會加入您的程式碼中，且不會列印。 它們僅供參考。  
  
 **啟用按一下方式的 URL 導覽**  
 當游標在編輯器的 URL 上方時，會變成手指符號。 按一下 URL 即可在 Web 瀏覽器中顯示該頁面。  
  
 **導覽列**  
 在程式碼編輯器頂端顯示導覽列。 使用其 [物件] 與 [程序] 下拉式清單來選擇程式碼中的特定物件，從它的程序中選取，然後插入選取之程序的執行個體。 並非所有的程式碼類型都可以使用導覽列。  
  
  