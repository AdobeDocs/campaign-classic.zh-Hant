---
solution: Campaign Classic
product: campaign
title: IMS 疑難排解
description: IMS 疑難排解
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 1%

---


# IMS 疑難排解{#ims-troubleshooting}

下列疑難排解提示將協助&#x200B;**on-premise**&#x200B;客戶解決使用IMS整合時最常見的問題。 若是&#x200B;**代管**&#x200B;的客戶，請聯絡Adobe。

**外部帳戶**

只有&#x200B;**一個**&#x200B;外部帳戶具有以下設定：

* **內部名稱**:Adobe_Marketing_Cloud
* **類型**:Adobe Marketing Cloud

刪除具有相同設定的任何重複外部帳戶。

**產品內容**

如果外部帳戶有&#x200B;**產品上下文**&#x200B;欄位，請檢查其值是否設定為：**dma_campaign_classic**

請確定您的產品內容與Campaign和Experience Cloud相同。

例如，如果未顯示&#x200B;**產品內容**，則Campaign和Experience Cloud中的預設產品內容應為&#x200B;**dma_campaign**。 如果出現「**產品內容**」欄位，則Campaign和Experience Cloud中的預設產品內容應為&#x200B;**dma_campaign_classic**。

**[!UICONTROL IMS Server URL]**

在Campaign **Adobe Marketing Cloud**&#x200B;外部帳戶中，檢查&#x200B;**[!UICONTROL IMS Server URL]**&#x200B;是[adobeid-na1.services.adobe.com](https://adobeid-na1.services.adobe.com/)還是[ims-na1.adobelogin.com](http://ims-na1.adobelogin.com/)。 請確定舞台和生產執行個體都指向相同的IMS生產端點。

**關聯遮色片**

* 檢查嘗試登入的使用者是否屬於Enterprise Dashboard中的運算元群組。
* 檢查&#x200B;**[!UICONTROL Association Mask]**&#x200B;是Enterprise Dashboard中使用者運算子群組名稱的首碼。
* 請確定沒有空格和拼字錯誤。
* 檢查「促銷活動」中運算元群組的名稱是否未變更，並遵循下列語法：

```
<Association Mask> + <Operator Group Name in Campaign> = Complete name of the operator group in Enterprise Dashboard
```

**範圍**

促銷活動外部帳戶中定義的範圍必須是IMS所布建的範圍子集。

**回呼URL**

**回呼URL**&#x200B;應新增至allowlist，並以&quot;https://&quot;開頭。 檢查&#x200B;**回呼URL**&#x200B;是否連結至對應的例項。 例如，生產例項應重新導向至生產URL。

**用戶端ID與密碼**

用戶端ID與促銷活動外部帳戶和IMS布建的帳戶相符。

檢查輸入的客戶機密碼是否正確。

**重新啟動伺服器**

如果對「促銷活動」外部帳戶中的上述設定進行任何變更，請重新啟動伺服器

**常見的錯誤類型和可能的解決方案**

* 使用者已重新導向至adobe.com頁面：

   **[!UICONTROL Callback URL]**&#x200B;有問題。 請參閱上述步驟以檢查&#x200B;**[!UICONTROL Callback URL]**&#x200B;配置。

* 訊息「登入沒有任何與運算式相符的權限」:

   請參閱上述步驟，檢查&#x200B;**[!UICONTROL Association Mask]**&#x200B;和運算子群組組態。

* 使用者無法存取Adobe ID登入頁面：

   請參閱上述步驟，檢查範圍配置。

