---
product: campaign
title: IMS 疑難排解
description: IMS 疑難排解
feature: Configuration
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 1ce89c3a-1fe6-4ed6-9547-2eb9713a0ec3
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 1%

---

# IMS 疑難排解{#ims-troubleshooting}


下列疑難排解提示可協助&#x200B;**內部部署**&#x200B;和&#x200B;**混合式**&#x200B;客戶解決使用IMS整合時最常發生的問題。 針對&#x200B;**託管**&#x200B;客戶，請連絡Adobe。

**外部帳戶**

應該只有&#x200B;**一個**&#x200B;外部帳戶具有下列設定：

* **內部名稱**： Adobe_Marketing_Cloud
* **型別**： Adobe Marketing Cloud

刪除具有相同設定的任何重複外部帳戶。

**產品內容**

如果外部帳戶有&#x200B;**產品內容**&#x200B;欄位，請檢查其值是否設為： **dma_campaign_classic**

請確定您的產品內容與Campaign和Experience Cloud相同。

例如，如果未出現&#x200B;**產品內容**，則促銷活動和Experience Cloud中的預設產品內容應該是&#x200B;**dma_campaign**。 如果出現「**產品內容**」欄位，促銷活動和Experience Cloud中的預設產品內容應該是&#x200B;**dma_campaign_classic**。

**[!UICONTROL IMS Server URL]**

在Campaign **Adobe Marketing Cloud**&#x200B;外部帳戶中，檢查&#x200B;**[!UICONTROL IMS Server URL]**&#x200B;是`adobeid-na1.services.adobe.com`或`ims-na1.adobelogin.com`。 確定中繼和生產執行個體都指向相同的IMS生產端點。

**關聯遮罩**

* 檢查嘗試登入的使用者是否為Enterprise Dashboard中操作員群組的一部分。
* 檢查&#x200B;**[!UICONTROL Association Mask]**&#x200B;是否為Enterprise Dashboard中使用者的運運算元群組名稱的前置詞。
* 請確定沒有空格和拼字錯誤。
* 檢查Campaign中運運算元群組的名稱是否未變更，並遵循下列語法：

```
<Association Mask> + <Operator Group Name in Campaign> = Complete name of the operator group in Enterprise Dashboard
```

**領域**

Campaign外部帳戶中定義的範圍必須是IMS提供之範圍的子集。

**回撥URL**

**回呼URL**&#x200B;應新增至允許清單，且以「https://」開頭。 檢查&#x200B;**回撥URL**&#x200B;是否已連結至對應的執行個體。 例如，生產執行個體應重新導向至生產URL。

**使用者端識別碼與密碼**

Campaign外部帳戶與IMS布建的帳戶之間的使用者端ID相符。

檢查輸入的使用者端密碼是否正確。

**重新啟動伺服器**

如果Campaign外部帳戶中的上述設定有任何變更，請重新啟動伺服器

**常見的錯誤型別和可能的解決方案**

* 系統會將使用者重新導向至adobe.com頁面：

  **[!UICONTROL Callback URL]**&#x200B;發生問題。 請參閱先前步驟以檢查&#x200B;**[!UICONTROL Callback URL]**&#x200B;設定。

* 訊息「登入沒有任何符合運算式的許可權」：

  請參閱先前步驟以檢查&#x200B;**[!UICONTROL Association Mask]**&#x200B;和運運算元群組組態。

* 使用者無法存取Adobe ID登入頁面：

  請參閱先前步驟以檢查範圍組態。
