---
product: campaign
title: IMS 疑難排解
description: IMS 疑難排解
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 1ce89c3a-1fe6-4ed6-9547-2eb9713a0ec3
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 1%

---

# IMS 疑難排解{#ims-troubleshooting}

下列疑難排解秘訣可協助&#x200B;**內部部署**&#x200B;客戶解決使用IMS整合時最常見的問題。 對於托管的&#x200B;****&#x200B;客戶，請聯繫Adobe。

**外部帳戶**

只有&#x200B;**一個**&#x200B;外部帳戶應具有下列設定：

* **內部名稱**:Adobe_Marketing_Cloud
* **類型**:Adobe Marketing Cloud

刪除具有相同設定的任何重複外部帳戶。

**產品內容**

如果外部帳戶有&#x200B;**產品內容**&#x200B;欄位，請檢查其值是否設為：**dma_campaign_classic**

請確定您的產品內容與Campaign和Experience Cloud相同。

例如，如果未顯示&#x200B;**產品內容**，則在促銷活動和Experience Cloud中，預設產品內容應為&#x200B;**dma_campaign**。 如果顯示「**產品內容**」欄位，則「促銷活動」和「Experience Cloud」中的預設產品內容應為&#x200B;**dma_campaign_classic**。

**[!UICONTROL IMS Server URL]**

在Campaign **Adobe Marketing Cloud**&#x200B;外部帳戶中，檢查&#x200B;**[!UICONTROL IMS Server URL]**&#x200B;是否為[adobeid-na1.services.adobe.com](https://adobeid-na1.services.adobe.com/)或[ims-na1.adobelogin.com](http://ims-na1.adobelogin.com/)。 請確定預備和生產執行個體都指向相同的IMS生產端點。

**關聯掩碼**

* 檢查嘗試登入的使用者是否屬於Enterprise Dashboard中的運算子群組。
* 檢查&#x200B;**[!UICONTROL Association Mask]**&#x200B;是否為Enterprise Dashboard中用戶運算子組名稱的前置詞。
* 請確定沒有空格和拼字錯誤。
* 檢查Campaign中運算子群組的名稱是否未變更，並遵循下列語法：

```
<Association Mask> + <Operator Group Name in Campaign> = Complete name of the operator group in Enterprise Dashboard
```

**範圍**

Campaign外部帳戶中定義的範圍必須是IMS布建的範圍的子集。

**回呼URL**

應將&#x200B;**回呼URL**&#x200B;新增至允許清單，並以「https://」開頭。 檢查&#x200B;**回呼URL**&#x200B;是否已連結至對應的例項。 例如，生產執行個體應重新導向至生產URL。

**用戶端ID與密碼**

用戶端ID在Campaign外部帳戶與IMS布建的帳戶之間相符。

檢查輸入的客戶端密碼是否正確。

**重新啟動伺服器**

如果在Campaign外部帳戶中對上述設定進行任何變更，請重新啟動伺服器

**常見的錯誤類型和可能的解決方案**

* 系統會將使用者重新導向至adobe.com頁面：

   **[!UICONTROL Callback URL]**&#x200B;有問題。 請參閱前面的步驟以檢查&#x200B;**[!UICONTROL Callback URL]**&#x200B;配置。

* 訊息「登入沒有任何符合運算式的權利」：

   請參閱上述步驟，檢查&#x200B;**[!UICONTROL Association Mask]**&#x200B;和運算子群組組態。

* 使用者無法存取Adobe ID登入頁面：

   請參閱前面的步驟以檢查範圍配置。
