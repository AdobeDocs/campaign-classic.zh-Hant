---
solution: Campaign Classic
product: campaign
title: 限制 PII 檢視
description: 限制 PII 檢視
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 693e38477b318ee44e0373a04d8524ddf128fe36
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 2%

---


# 限制PI視圖{#restricting-pii-view}

## 概觀 {#overview}

有些客戶需要行銷使用者能夠存取資料記錄，但不希望他們看到個人識別資訊(PII)，例如名字、姓氏或電子郵件地址。 Adobe Campaign提出了保護隱私和防止資料被常規宣傳活動運營商濫用的方法。

## 實施{#implementation}

新屬性（可套用至任何元素或屬性）已新增至結構描述，它補充了現有屬性&#x200B;**[!UICONTROL visibleIf]**。 此屬性為：**[!UICONTROL accessibleIf]**。 例如，當包含與當前用戶上下文相關的XTK表達式時，它可以利用&#x200B;**[!UICONTROL HasNamedRight]**&#x200B;或&#x200B;**[!UICONTROL $(login)]**。

您可以找到以下顯示此用法的收件者結構擴展示例：

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

主要屬性有：

* **[!UICONTROL visibleIf]** :隱藏中繼資料中的欄位，因此無法在架構檢視、欄選取或運算式產生器中存取欄位。但這不會隱藏任何資料，如果欄位名稱是手動輸入在運算式中，值就會顯示。
* **[!UICONTROL accessibleIf]** :隱藏資料（以空值取代資料），以免產生查詢。如果visibleIf為空，則其獲得與&#x200B;**[!UICONTROL accessibleIf]**&#x200B;相同的表達式。

以下是在促銷活動中使用此屬性的後果：

* 控制台中不會使用一般查詢編輯器顯示資料，
* 概述清單和記錄清單（主控台）中不會顯示資料。
* 資料將在詳細檢視中變成唯讀。
* 資料只能在篩選器中使用（這表示使用某些二分法策略，您仍可以猜測值）。
* 使用限制欄位建立的任何運算式也會受到限制：lower(@email)變得和@email一樣可存取。
* 在工作流程中，您可以將受限制的欄新增至目標人口，作為轉場的額外欄，但Adobe Campaign使用者仍無法存取。
* 將目標人口儲存在群組（清單）中時，儲存欄位的特性與資料來源相同。
* 依預設，JS程式碼無法存取資料。

## 建議 {#recommendations}

在每次傳送中，電子郵件地址都會複製到&#x200B;**[!UICONTROL broadLog]**&#x200B;和&#x200B;**[!UICONTROL forecastLog]**&#x200B;表格中：因此，這些欄位也需要受到保護。

以下是實施此功能的日誌表擴展示例：

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
>此限制適用於非技術使用者：具有相關權限的技術使用者將能夠擷取資料。 因此，此方法不是百分之百安全。

