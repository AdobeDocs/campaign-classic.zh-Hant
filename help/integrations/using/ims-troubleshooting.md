---
product: campaign
title: IMS 疑難排解
description: IMS 疑難排解
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 1ce89c3a-1fe6-4ed6-9547-2eb9713a0ec3
source-git-commit: f4513834cf721f6d962c7c02c6c64b2171059352
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 2%

---

# IMS 疑難排解{#ims-troubleshooting}

![](../../assets/common.svg)

下列疑難排解提示將有所幫助 **內部部署** 客戶可解決使用IMS整合時最常發生的問題。 針對 **托管** 客戶，請聯絡Adobe。

**外部帳戶**

應該只有 **one** 具有下列設定的外部帳戶：

* **內部名稱**:Adobe_Marketing_Cloud
* **類型**:Adobe Marketing Cloud

刪除具有相同設定的任何重複外部帳戶。

**產品內容**

如果外部帳戶具有 **產品內容** 欄位中，檢查其值設為： **dma_campaign_classic**

請確定您的產品內容與Campaign和Experience Cloud相同。

例如，若 **產品內容** 未顯示，預設產品內容應為 **dma_campaign** 在Campaign和Experience Cloud中。 若 **產品內容** 欄位，預設產品內容應為 **dma_campaign_classic** 在Campaign和Experience Cloud中。

**[!UICONTROL IMS Server URL]**

在促銷活動中 **Adobe Marketing Cloud** 外部帳戶，檢查 **[!UICONTROL IMS Server URL]** 為 `adobeid-na1.services.adobe.com` 或 `ims-na1.adobelogin.com`. 請確定預備和生產執行個體都指向相同的IMS生產端點。

**關聯掩碼**

* 檢查嘗試登入的使用者是否屬於Enterprise Dashboard中的運算子群組。
* 檢查 **[!UICONTROL Association Mask]** 是Enterprise Dashboard中使用者運算子群組名稱的前置詞。
* 請確定沒有空格和拼字錯誤。
* 檢查Campaign中運算子群組的名稱是否未變更，並遵循下列語法：

```
<Association Mask> + <Operator Group Name in Campaign> = Complete name of the operator group in Enterprise Dashboard
```

**範圍**

Campaign外部帳戶中定義的範圍必須是IMS布建的範圍的子集。

**回呼URL**

此 **回呼URL** 應新增至允許清單，並以「https://」開頭。 檢查 **回呼URL** 連結至對應的例項。 例如，生產執行個體應重新導向至生產URL。

**用戶端ID與密碼**

用戶端ID在Campaign外部帳戶與IMS布建的帳戶之間相符。

檢查輸入的客戶端密碼是否正確。

**重新啟動伺服器**

如果在Campaign外部帳戶中對上述設定進行任何變更，請重新啟動伺服器

**常見的錯誤類型和可能的解決方案**

* 系統會將使用者重新導向至adobe.com頁面：

   有問題 **[!UICONTROL Callback URL]**. 請參閱先前的步驟以檢查 **[!UICONTROL Callback URL]** 設定。

* 訊息「登入沒有任何符合運算式的權利」：

   請參閱先前的步驟以檢查 **[!UICONTROL Association Mask]** 和運算子群組設定。

* 使用者無法存取Adobe ID登入頁面：

   請參閱前面的步驟以檢查範圍配置。
