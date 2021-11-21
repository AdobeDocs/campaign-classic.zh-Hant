---
product: campaign
title: 勾點
description: 勾點
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: e1d7d7c2-61e7-40d6-a8ce-69bc976f8c73
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 1%

---

# 勾點{#hooks}

![](../../assets/v7-only.svg)

互動中的鈎點可讓您修改 **標準引擎行為**.

此 **[!UICONTROL Target loading]** 和 **[!UICONTROL Proposition post-processing]** 在Adobe Campaign中，您可在選件空間中設定鈎點：

![](assets/interaction_hooks_1.png)

此 **[!UICONTROL Dynamic offer]** hook在Adobe Campaign中已設定選件權重：

![](assets/interaction_hooks_2.png)

## 目標載入 {#target-loading}

此連結可讓您以來自外部系統的其他資料，豐富連絡人的設定檔（由現成查詢載入）。

收集的資料必須插入呼叫資料節點（互動節點）中。 整合商必須預先擴展呼叫資料架構，以定義收集資料的結構。 使用者可以與標準呼叫資料（在適用性規則和個人化層級）相同的方式存取此資料。

**輸入參數：**

* xmlInteraction（xml類型）:交互節點
* aTargetId（表格類型）:目標識別碼
* sUuid230（字串類型）:uuid230永久cookie的值
* sNlid（字串類型）:nlid工作階段cookie的值

**傳回參數：**

* 擴充互動節點（此鈎的第一個參數）

>[!NOTE]
>
>此 **xmlInteraction** 參數包含呼叫資料和現成可用查詢載入之聯絡人的設定檔。

**範例:**

```
// Call an external system to get additional data for the target
  var additionalData  = getUrl("https://EXTERNAL_SYSTEM?target=" + encodeURIComponent(aTargetId.join("|")));
  // Enrich the context with this data
  interaction.@additionalData = additionalData;
```

## 主張後處理 {#proposition-post-processing-}

此掛接允許您檢查給定交互中合格命題的一致性和相容性。 它也可讓您定義新的分數或機率計算功能。

使用一致性規則的範例：

* 限制同一呼叫中連結到相同產品或相同類別的命題的數量。
* 僅在相同互動中顯示與產品相關的優惠方案。

後續處理會在類型規則應用程式和合格命題排序之後，以及優先順序步驟之前執行。

**輸入參數：**

* 主張：合格建議表。 以下是此表格中元素結構的範例

   ```
   { offer_id:1234,
     weight:2}
   ```

* dicOffer（xml類型）:符合資格優惠方案的所有屬性的字典（優惠方案代碼、類別id、類別完整名稱、開始日期、結束日期、標籤、內部名稱、優惠方案id、其他優惠方案欄位）。 例如

   ```
   { "1242": <offer category-id="61242" categoryFullName="/FULL/PATH/TO/CATEGORY/" code="CODE" endDate="" id="62473" label="LABEL" name="OFR38_OE4" product-id="43" startDate=""/>,
     "1243": ...}
   ```

* xmlTarget（xml類型）:設定檔資料節點
* xmlInteraction（xml類型）:呼叫資料節點
* iPropNumber（整數類型）:預期選件數

**傳回參數：**

* 修正命題清單（鈎的第一個參數）
* 修改的交互節點

**範例:**

```
var aReturnedProps = [];

if( aProposition.length > 0 )
{
  var iReturnedProps = 0;
  for( var iPropIdx = 0; iPropIdx < aProposition.length && iReturnedProps < iPropNumber; iPropIdx ++ )
  {
    // Check a consistency rule for instance
    if( true )
    {
      aReturnedProps.push(aProposition[iPropIdx]);
      iReturnedProps++;
    }
  }
}

return aReturnedProps;
```

## 動態選件 {#dynamic-offer}

此連結可讓您呼叫外部引擎，以選取連結至選件的產品清單。 這是在優惠方案中針對適用性規則和類型規則應用程式進行設定的。

預先，整合商應擴展建議 **主張Rcp** 搭配產品的其他資訊的結構。 若要指定此資料的儲存位置，請 **[!UICONTROL Proposition being processed]** 連結可在 **[!UICONTROL Storage]** 空格的標籤

![](assets/interaction_hooks_3.png)

**輸入參數：**

* xmlOffer（xml類型）:優惠方案（優惠方案代碼、類別id、類別完整名稱、開始日期、結束日期、標籤、內部名稱、優惠方案id、其他優惠方案欄位）
* dWeight:內容權重（雙重類型）
* xmlTarget（xml類型）:設定檔資料節點
* xmlInteraction（xml類型）:呼叫資料節點

**傳回參數：**

返回要生成的命題表。 此表的每個元素都由以下資訊組成：

* 優惠方案識別碼
* 其他產品資料（例如產品代碼）
* 權重

>[!NOTE]
>
>系統會檢查選件ID是否與輸入和傳回參數相同。

**範例:**

```
var product = getUrl("https://EXTERNAL_SYSTEM?offerCode=" + encodeURIComponent(xmlOffer.@code));
if( product )
  return [{offer_id: parseInt(String(xmlOffer.@id)), weight: dWeight, productId: product}];
```
