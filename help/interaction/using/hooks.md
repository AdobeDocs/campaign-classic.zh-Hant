---
title: 鈎子
seo-title: 鈎子
description: 鈎子
seo-description: null
page-status-flag: never-activated
uuid: 4394717e-8625-4e2f-9492-3fd9b444a732
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: advanced-parameters
discoiquuid: 2b799ad7-b729-4b3e-9adc-1df13259f2a9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 鈎子{#hooks}

「互動」中的勾點可讓您修改標 **準引擎行為**。

在Adobe **[!UICONTROL Target loading]** Campaign中 **[!UICONTROL Proposition post-processing]** ，會在選件空間中設定和勾選：

![](assets/interaction_hooks_1.png)

此掛 **[!UICONTROL Dynamic offer]** 接是以Adobe Campaign中的選件權重設定：

![](assets/interaction_hooks_2.png)

## 目標載入 {#target-loading}

此掛接可讓您使用外部系統的額外資料，豐富連絡人的描述檔（由現成可用的查詢載入）。

收集的資料必須插入到呼叫資料節點（交互節點）中。 整合器必須事先擴充呼叫資料架構，以定義所收集資料的結構。 使用者可以與標準呼叫資料（在資格規則和個人化層級）相同的方式存取此資料。

**輸入參數：**

* xmlInteraction（xml類型）:交互節點
* aTargetId（表格類型）:目標標識符
* sUuid230（字串類型）:uuid230永久Cookie的值
* sNid（字串類型）:內部作業Cookie的值

**返回參數：**

* 豐富的交互節點（此掛接的第一個參數）

>[!NOTE]
>
>xmlInteraction **** 參數同時包含呼叫資料和由現成可用查詢載入之連絡人的描述檔。

**例如：**

```
// Call an external system to get additional data for the target
  var additionalData  = getUrl("https://EXTERNAL_SYSTEM?target=" + encodeURIComponent(aTargetId.join("|")));
  // Enrich the context with this data
  interaction.@additionalData = additionalData;
```

## 提案後處理 {#proposition-post-processing-}

此掛接可讓您檢查特定互動中合格命題的一致性和相容性。 它還可讓您定義新的計分或概率計算功能。

使用一致性規則的示例：

* 限制同一呼叫、連結至相同產品或相同類別的主張數。
* 僅在相同的互動中呈現與產品相關的選件。

後處理在排版規則應用程式和合格命題排序之後以及優先順序步驟之前執行。

**輸入參數：**

* 建議：合格主張表。 下面是此表中元素結構的示例

   ```
   { offer_id:1234,
     weight:2}
   ```

* dicOffer（xml類型）:合格選件的所有屬性的字典（選件程式碼、類別ID、類別完整名稱、開始日期、結束日期、標籤、內部名稱、選件ID、其他選件欄位）。 例如

   ```
   { "1242": <offer category-id="61242" categoryFullName="/FULL/PATH/TO/CATEGORY/" code="CODE" endDate="" id="62473" label="LABEL" name="OFR38_OE4" product-id="43" startDate=""/>,
     "1243": ...}
   ```

* xmlTarget（xml類型）:配置檔案資料節點
* xmlInteraction（xml類型）:呼叫資料節點
* iPropNumber（整數類型）:預期選件數

**返回參數：**

* 修正命題清單（掛接的第一個參數）
* 修改的交互節點

**例如：**

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

此掛接可讓您呼叫外部引擎，以選取連結至選件的產品清單。 它是在選件中設定的符合資格規則，以及在分類規則應用程式之前。

在此之前，整合商應使用產品上的附 **加資訊來擴展命題CompositionRcp** schema。 若要指定此資料的儲存位置， **[!UICONTROL Proposition being processed]** 空間標籤中會 **[!UICONTROL Storage]** 有連結

![](assets/interaction_hooks_3.png)

**輸入參數：**

* xmlOffer（xml類型）:選件（選件代碼、類別ID、類別完整名稱、開始日期、結束日期、標籤、內部名稱、選件ID、其他選件欄位）
* 重量：上下文權重（雙重類型）
* xmlTarget（xml類型）:配置檔案資料節點
* xmlInteraction（xml類型）:呼叫資料節點

**返回參數：**

返回要生成的命題表。 此表的每個元素都由以下資訊組成：

* 選件識別碼
* 其他產品資料（例如產品代碼）
* 權重

>[!NOTE]
>
>系統會檢查選件ID是否與輸入和傳回參數相同。

**例如：**

```
var product = getUrl("https://EXTERNAL_SYSTEM?offerCode=" + encodeURIComponent(xmlOffer.@code));
if( product )
  return [{offer_id: parseInt(String(xmlOffer.@id)), weight: dWeight, productId: product}];
```

