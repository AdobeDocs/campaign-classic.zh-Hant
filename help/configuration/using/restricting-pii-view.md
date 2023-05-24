---
product: campaign
title: 限制 PI 檢視
description: 瞭解如何限制PI檢視
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: PI
exl-id: 0f32d62d-a10a-4feb-99fe-4679b98957d4
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 2%

---

# 限制 PI 檢視{#restricting-pii-view}

## 概覽 {#overview}

某些客戶需要行銷使用者能夠存取資料記錄，但不希望他們看到個人識別資訊(PII)，例如名字、姓氏或電子郵件地址。 Adobe Campaign建議保護隱私權並防止資料被一般行銷活動運運算元不當使用的方法。

## 實作 {#implementation}

結構描述中已新增可套用至任何元素或屬性的新屬性，它補充了現有屬性 **[!UICONTROL visibleIf]** . 此屬性是： **[!UICONTROL accessibleIf]** . 當包含與目前使用者內容相關的XTK運算式時，它可以利用 **[!UICONTROL HasNamedRight]** 或 **[!UICONTROL $(login)]** ，例如。

收件者方案擴充功能的範例顯示以下用法：

```
<srcSchema desc="Recipient table (profiles" entitySchema="xtk:srcSchema" extendedSchema="nms:recipient"
           img="nms:recipient.png" label="Recipients" labelSingular="Recipient"
           name="recipient" namespace="sec" xtkschema="xtk:srcSchema">
  <element desc="Recipient table (profiles" img="nms:recipient.png" label="Recipients"
           labelSingular="Recipient" name="recipient">
    <attribute name="firstName" accessibleIf="$(login)=='admin'"/>
    <attribute name="lastName" visibleIf="$(login)=='admin'"/>
    <attribute name="email" accessibleIf="$(login)=='admin'"/>
  </element>
</srcSchema>
```

主要屬性包括：

* **[!UICONTROL visibleIf]** ：隱藏中繼資料中的欄位，因此無法在結構描述檢視、欄選擇或運算式產生器中存取這些欄位。 但這不會隱藏任何資料，如果手動在運算式中輸入欄位名稱，則會顯示值。
* **[!UICONTROL accessibleIf]** ：隱藏產生的查詢中的資料（以空白值取代）。 如果visibleIf空白，則會取得與相同的運算式 **[!UICONTROL accessibleIf]** .

在Campaign中使用此屬性的後果如下：

* 資料將不會在主控台中使用一般查詢編輯器顯示。
* 資料不會顯示在概述清單和記錄清單（主控台）中。
* 詳細檢視中的資料將變成唯讀。
* 資料只能在篩選器中使用（這表示使用某些二分法策略，您仍然可以猜測值）。
* 使用限制欄位建立的任何運算式也會受到限制： lower(@email)會變得與@email一樣可存取。
* 在工作流程中，您可以將受限制的欄新增至目標母體，作為轉變的額外欄，但Adobe Campaign使用者仍無法存取。
* 將目標母體儲存在群組（清單）中時，所儲存欄位的特性與資料來源相同。
* 依預設，JS程式碼無法存取資料。

## 建議 {#recommendations}

每次傳送時，電子郵件地址都會複製到 **[!UICONTROL broadLog]** 和 **[!UICONTROL forecastLog]** 表格：因此，這些欄位也需要受到保護。

以下為實作此專案的記錄表擴充功能範例：

```
<srcSchema entitySchema="xtk:srcSchema" extendedSchema="nms:broadLogRcp" img="nms:broadLog.png"
           label="Recipient delivery logs" labelSingular="Recipient delivery log"
           name="broadLogRcp" namespace="sec" xtkschema="xtk:srcSchema">
  <element img="nms:broadLog.png" label="Recipient delivery logs" labelSingular="Recipient delivery log"
           name="broadLogRcp">
    <attribute accessibleIf="$(login)=='admin'" name="address"/>
  </element>
</srcSchema>
<srcSchema desc="Delivery messages being prepared." entitySchema="xtk:srcSchema"
           extendedSchema="nms:tmpBroadcast" img="" label="Messages being prepared"
           labelSingular="Message" name="tmpBroadcast" namespace="sec" xtkschema="xtk:srcSchema">
  <element desc="Delivery messages being prepared." label="Messages being prepared"
           labelSingular="Message" name="tmpBroadcast">
    <attribute accessibleIf="$(login)=='admin'" name="address"/>
  </element>
</srcSchema>
<srcSchema entitySchema="xtk:srcSchema" extendedSchema="nms:excludeLogRcp" img="nms:excludeLog.png"
           label="Recipient exclusion logs" labelSingular="Recipient exclusion log"
           name="excludeLogRcp" namespace="sec" xtkschema="xtk:srcSchema">
  <element img="nms:excludeLog.png" label="Recipient exclusion logs" labelSingular="Recipient exclusion log"
           name="excludeLogRcp">
    <attribute accessibleIf="$(login)=='admin'" name="address"/>
  </element>
</srcSchema>
```

>[!NOTE]
>
>此限制適用於非技術使用者：具有相關許可權的技術使用者將能夠擷取資料。 因此，此方法並非100%安全。
