---
title: IMS疑難排解
seo-title: IMS疑難排解
description: IMS疑難排解
seo-description: null
page-status-flag: never-activated
uuid: 5db95afc-8cbf-4ec3-b58f-504486fe4a40
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
discoiquuid: e31db11a-ad8e-4fd0-bab7-0df1079231c9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# IMS疑難排解{#ims-troubleshooting}

下列疑難排解秘訣可 **協助內部部署** ，客戶解決使用IMS整合時最常發生的問題。 若為 **代管** ，請聯絡Adobe。

**外部帳戶**

只有一個外 **部帳戶** ，其設定如下：

* **內部名稱**:Adobe_Marketing_Cloud
* **類型**:Adobe Marketing Cloud

刪除具有相同設定的任何重複外部帳戶。

**產品內容**

如果外部帳戶有「產 **品內容** 」欄位，請檢查其值是否設為： **dma_campaign_classic**

請確定您的產品內容與Campaign和Experience cloud相同。

例如，如果未顯 **示「產品內容** 」，則預設產品內容應為 **dma_campaign** （在Campaign和Experience cloud中）。 如果出 **現「產品內容** 」欄位，則預設產品內容應為 **dma_campaign_classic** （在Campaign和Experience cloud中）。

**[!UICONTROL IMS Server URL]**

在Campaign **Adobe Marketing cloud外部帳戶中，檢查** 是 **[!UICONTROL IMS Server URL]** adobeid-na1.services.adobe.com或 [ims-na1.adobelogin.com](https://adobeid-na1.services.adobe.com/)[](http://ims-na1.adobelogin.com/)。 請確定舞台和生產執行個體都指向相同的IMS生產端點。

**關聯遮色片**

* 檢查嘗試登入的使用者是否屬於Enterprise Dashboard中的運算元群組。
* 在Enterprise Dashboard **[!UICONTROL Association Mask]** 中，檢查使用者的運算子群組名稱前置詞。
* 請確定沒有空格和拼字錯誤。
* 檢查「促銷活動」中運算元群組的名稱是否未變更，並遵循下列語法：

```
<Association Mask> + <Operator Group Name in Campaign> = Complete name of the operator group in Enterprise Dashboard
```

**範圍**

促銷活動外部帳戶中定義的範圍必須是IMS所布建的範圍子集。

**回呼URL**

回 **呼URL** 應列入白名單，並以&quot;https://&quot;開頭。 檢查回 **呼URL** 是否連結至對應的例項。 例如，生產例項應重新導向至生產URL。

**用戶端ID與密碼**

用戶端ID與促銷活動外部帳戶和IMS布建的帳戶相符。

檢查輸入的客戶機密碼是否正確。

**重新啟動伺服器**

如果對「促銷活動」外部帳戶中的上述設定進行任何變更，請重新啟動伺服器

**常見的錯誤類型和可能的解決方案**

* 使用者已重新導向至adobe.com頁面：

   這個問題出了問題 **[!UICONTROL Callback URL]**。 請參閱上述步驟以檢查設 **[!UICONTROL Callback URL]** 定。

* 訊息「登入沒有任何與運算式相符的權限」:

   請參閱上述步驟，以檢查 **[!UICONTROL Association Mask]** 和運算元群組設定。

* 使用者無法存取Adobe ID登入頁面：

   請參閱上述步驟，檢查範圍配置。

