---
product: campaign
title: IMS 疑難排解
description: IMS 疑難排解
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 1ce89c3a-1fe6-4ed6-9547-2eb9713a0ec3
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 2%

---

# IMS 疑難排解{#ims-troubleshooting}



下列疑難排解提示將有所幫助 **內部部署** 客戶可解決使用IMS整合時最常見的問題。 對象 **託管** 客戶，請聯絡Adobe。

**外部帳戶**

應該只有 **一** 外部帳戶，具有以下設定：

* **內部名稱**：Adobe_Marketing_Cloud
* **型別**：Adobe Marketing Cloud

刪除具有相同設定的任何重複外部帳戶。

**產品內容**

如果外部帳戶具有 **產品內容** 欄位，檢查其值是否設為： **dma_campaign_classic**

請確定您的產品內容與Campaign和Experience Cloud相同。

例如，如果 **產品內容** 不會出現，預設產品內容應為 **dma_campaign** 行銷活動和Experience Cloud中設定。 如果 **產品內容** 欄位，預設產品內容應為 **dma_campaign_classic** 行銷活動和Experience Cloud中設定。

**[!UICONTROL IMS Server URL]**

在行銷活動中 **Adobe Marketing Cloud** 外部帳戶，檢查 **[!UICONTROL IMS Server URL]** 為 `adobeid-na1.services.adobe.com` 或 `ims-na1.adobelogin.com`. 確定中繼和生產執行個體都指向相同的IMS生產端點。

**關聯遮罩**

* 檢查嘗試登入的使用者是否為Enterprise Dashboard中運運算元群組的一部分。
* 檢查 **[!UICONTROL Association Mask]** 是Enterprise Dashboard中使用者的操作員群組名稱的前置詞。
* 請確定沒有空格和拼字錯誤。
* 檢查Campaign中運運算元群組的名稱是否未變更，並遵循下列語法：

```
<Association Mask> + <Operator Group Name in Campaign> = Complete name of the operator group in Enterprise Dashboard
```

**範圍**

Campaign外部帳戶中定義的範圍必須是IMS布建的範圍的子集。

**回撥URL**

此 **回撥URL** 應新增至允許清單，並以「https://」開頭。 檢查 **回撥URL** 會連結至對應的例項。 例如，生產執行個體應重新導向至生產URL。

**使用者端ID和密碼**

Campaign外部帳戶和IMS布建的帳戶之間的使用者端ID相符。

檢查輸入的使用者端密碼是否正確。

**重新啟動伺服器**

如果Campaign外部帳戶中的上述設定有任何變更，請重新啟動伺服器

**常見錯誤型別和可能的解決方案**

* 系統會將使用者重新導向至adobe.com頁面：

   發生問題 **[!UICONTROL Callback URL]**. 請參閱先前步驟以檢查 **[!UICONTROL Callback URL]** 設定。

* 訊息「登入沒有任何符合運算式的許可權」：

   請參閱先前步驟以檢查 **[!UICONTROL Association Mask]** 和運運算元群組設定。

* 使用者無法存取Adobe ID登入頁面：

   請參閱先前步驟以檢查範圍組態。
