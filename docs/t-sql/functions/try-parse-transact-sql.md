---
title: "TRY_PARSE (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TRY_PARSE_TSQL
- TRY_PARSE
dev_langs:
- TSQL
helpviewer_keywords:
- TRY_PARSE function
ms.assetid: 292bac1d-edd8-468c-8ff1-8c7de625bc55
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 735d1e38b81a08da50cba340b0e5663d6e6d5755
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="tryparse-transact-sql"></a>TRY_PARSE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  將會傳回運算式的結果，並轉譯為所要求的資料類型。若在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中轉換失敗，則傳回 Null。 TRY_PARSE 僅適用於從字串轉換到日期/時間及數字類型。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
TRY_PARSE ( string_value AS data_type [ USING culture ] )  
```  
  
## <a name="arguments"></a>引數  
 *string_value*  
 **nvarchar （4000)**值，代表要剖析為指定的資料類型的格式化的值。  
  
 *string_value*必須是有效表示法要求的資料類型，否則 TRY_PARSE 會傳回 null。  
  
 *data_type*  
 以文字表示結果所要求的資料類型。  
  
 *文化特性*  
 識別在其中的文化特性的選擇性字串*string_value*格式化。  
  
 如果*文化特性*未提供引數，會使用目前的工作階段的語言。 此語言是以 SET LANGUAGE 陳述式隱含或明確加以設定。 *文化特性*任何.NET Framework; 所支援的文化特性並不限於使用明確支援的語言[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 如果*文化特性*引數無效，PARSE 會引發錯誤。  
  
## <a name="return-types"></a>傳回類型  
 將傳回運算式結果，並轉譯為所要求的資料類型；若轉換失敗，則傳回 Null。  
  
## <a name="remarks"></a>備註  
 TRY_PARSE 僅適用於從字串轉換到日期/時間及數字類型。 一般類型轉換仍可繼續使用 CAST 或 CONVERT。 請注意，剖析字串值將對效能造成一定程度的負擔。  
  
 TRY_PARSE 仰賴既存的 .NET Framework Common Language Runtime (CLR)。  
  
 因為必須要有 CLR 才可執行此函數，所以無法從遠端進行。 從遠端處理需要 CLR 的函數，會導致遠端伺服器發生錯誤。  
  
 **Data_type 參數的詳細資訊**  
  
 值*data_type*參數會限制為下表，與樣式中所顯示的類型。 此處所提供的樣式資訊可以協助您決定所要允許的模式類型。 如需有關樣式的詳細資訊，請參閱.NET Framework 文件**System.Globalization.NumberStyles**和**DateTimeStyles**列舉型別。  
  
|類別目錄|類型|.NET 類型|使用的樣式|  
|--------------|----------|---------------|-----------------|  
|數值|bigint|Int64|NumberStyles.Number|  
|數值|int|Int32|NumberStyles.Number|  
|數值|smallint|Int16|NumberStyles.Number|  
|數值|tinyint|Byte|NumberStyles.Number|  
|數值|decimal|Decimal|NumberStyles.Number|  
|數值|numeric|Decimal|NumberStyles.Number|  
|數值|float|Double|NumberStyles.Float|  
|數值|real|Single|NumberStyles.Float|  
|數值|smallmoney|Decimal|NumberStyles.Currency|  
|數值|money|Decimal|NumberStyles.Currency|  
|日期及時間|date|DateTime|DateTimeStyles.AllowWhiteSpaces &#124;DateTimeStyles.AssumeUniversal|  
|日期及時間|time|TimeSpan|DateTimeStyles.AllowWhiteSpaces &#124;DateTimeStyles.AssumeUniversal|  
|日期及時間|datetime|DateTime|DateTimeStyles.AllowWhiteSpaces &#124;DateTimeStyles.AssumeUniversal|  
|日期及時間|smalldatetime|DateTime|DateTimeStyles.AllowWhiteSpaces &#124;DateTimeStyles.AssumeUniversal|  
|日期及時間|datetime2|DateTime|DateTimeStyles.AllowWhiteSpaces &#124;DateTimeStyles.AssumeUniversal|  
|日期及時間|datetimeoffset|DateTimeOffset|DateTimeStyles.AllowWhiteSpaces &#124;DateTimeStyles.AssumeUniversal|  
  
 **文化特性參數的詳細資訊**  
  
 下表顯示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 語言所對應的 .NET Framework 文化特性。  
  
|全名|別名|LCID|專屬文化特性|  
|---------------|-----------|----------|----------------------|  
|us_english|英文|1033|zh-TW|  
|Deutsch|德文|1031|de-DE|  
|Français|法文|1036|fr-FR|  
|日本語|日文|1041|ja-JP|  
|Dansk|丹麥文|1030|da-DK|  
|Español|西班牙文|3082|es-ES|  
|Italiano|義大利文|1040|it-IT|  
|Nederlands|荷蘭文|1043|nl-NL|  
|Norsk|挪威文|2068|nn-NO|  
|Português|葡萄牙文|2070|pt-PT|  
|Suomi|芬蘭文|1035|fi|  
|Svenska|瑞典文|1053|sv-SE|  
|čeština|捷克文|1029|Cs-CZ|  
|magyar|匈牙利文|1038|Hu-HU|  
|polski|波蘭文|1045|Pl-PL|  
|română|羅馬尼亞文|1048|Ro-RO|  
|hrvatski|克羅埃西亞文|1050|hr-HR|  
|slovenčina|斯洛伐克文|1051|Sk-SK|  
|slovenski|斯洛維尼亞文|1060|Sl-SI|  
|ελληνικά\|希臘文|1032|El-GR|  
|български|保加利亞文|1026|bg-BG|  
|русский|俄文|1049|Ru-RU|  
|Türkçe|土耳其文|1055|Tr-TR|  
|British|英式英文|2057|en-GB|  
|eesti|愛沙尼亞文|1061|Et-EE|  
|latviešu|拉脫維亞文|1062|lv-LV|  
|lietuvių|立陶宛文|1063|lt-LT|  
|Português (Brasil)|巴西文|1046|pt-BR|  
|繁體中文|繁體中文|1028|zh-TW|  
|한국어|韓文|1042|Ko-KR|  
|简体中文|簡體中文|2052|zh-CN|  
|阿拉伯文|阿拉伯文|1025|ar-SA|  
|ไทย|泰文|1054|Th-TH|  
  
## <a name="examples"></a>範例  
  
### <a name="a-simple-example-of-tryparse"></a>A. TRY_PARSE 的簡單範例  
  
```  
SELECT TRY_PARSE('Jabberwokkie' AS datetime2 USING 'en-US') AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
---------------  
NULL  
  
(1 row(s) affected)  
```  
  
### <a name="b-detecting-nulls-with-tryparse"></a>B. 使用 TRY_PARSE 偵測 Null  
  
```  
SELECT  
    CASE WHEN TRY_PARSE('Aragorn' AS decimal USING 'sr-Latn-CS') IS NULL  
        THEN 'True'  
        ELSE 'False'  
END  
AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
---------------  
True  
  
(1 row(s) affected)  
```  
  
### <a name="c-using-iif-with-tryparse-and-implicit-culture-setting"></a>C. 一併使用 IIF 與 TRY_PARSE 及隱含文化特性設定  
  
```  
SET LANGUAGE English;  
SELECT IIF(TRY_PARSE('01/01/2011' AS datetime2) IS NULL, 'True', 'False') AS Result;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
---------------  
False  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>另請參閱  
 [剖析 &#40;TRANSACT-SQL &#41;](../../t-sql/functions/parse-transact-sql.md)   
 [轉換函式 &#40;TRANSACT-SQL &#41;](../../t-sql/functions/conversion-functions-transact-sql.md)   
 [TRY_CONVERT &#40;TRANSACT-SQL &#41;](../../t-sql/functions/try-convert-transact-sql.md)   
 [CAST 和 CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  