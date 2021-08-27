---
product: campaign
title: 限制 PII 檢視
description: 限制 PII 檢視
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 0f32d62d-a10a-4feb-99fe-4679b98957d4
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 2%

---

# 限制 PI 檢視{#restricting-pii-view}

![](../../assets/v7-only.svg)

## 概覽 {#overview}

有些客戶需要行銷使用者才能存取資料記錄，但不希望他們看到個人識別資訊(PII)，例如名字、姓氏或電子郵件地址。 Adobe Campaign提出了保護隱私和防止常規競選運營商濫用資料的方法。

## 實作 {#implementation}

可套用至任何元素或屬性的新屬性已新增至結構，可補充現有屬性&#x200B;**[!UICONTROL visibleIf]** 。 此屬性為：**[!UICONTROL accessibleIf]** 。 當包含與目前使用者內容相關的XTK運算式時，例如，它可以運用&#x200B;**[!UICONTROL HasNamedRight]**&#x200B;或&#x200B;**[!UICONTROL $(login)]**。

您可以找到收件者結構擴充功能的範例，其中顯示以下用法：

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

主要屬性為：

* **[!UICONTROL visibleIf]** :會隱藏中繼資料中的欄位，因此無法在結構檢視、欄選取項目或運算式產生器中存取這些欄位。但這不會隱藏任何資料，如果在運算式中手動輸入欄位名稱，則會顯示值。
* **[!UICONTROL accessibleIf]** :會隱藏資料（以空值取代），使其不會產生查詢。如果visibleIf為空，則會獲得與&#x200B;**[!UICONTROL accessibleIf]**&#x200B;相同的運算式。

以下是在Campaign中使用此屬性的後果：

* 控制台中不會使用一般查詢編輯器來顯示資料，
* 概覽清單和記錄清單（主控台）中不會顯示資料。
* 在詳細檢視中，資料將變成唯讀。
* 資料只能在篩選器中使用（這表示使用某些二分法策略，您仍可以猜測值）。
* 使用限制欄位建立的任何運算式也會受到限制：lower(@email)將變成可存取@email。
* 在工作流程中，您可以將限制欄新增至目標母體，作為轉變的額外欄，但Adobe Campaign使用者仍無法存取該欄。
* 將目標母體儲存在組（清單）中時，所儲存欄位的特徵與資料源相同。
* JS程式碼預設無法存取資料。

## 建議 {#recommendations}

在每次傳送中，電子郵件地址都會複製到&#x200B;**[!UICONTROL broadLog]**&#x200B;和&#x200B;**[!UICONTROL forecastLog]**&#x200B;表格中：因此，這些欄位也需要得到保護。

以下是實作此項目的記錄表擴充功能範例：

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
>此限制適用於非技術使用者：具有相關權限的技術使用者將能擷取資料。 因此，此方法並非100%安全。
