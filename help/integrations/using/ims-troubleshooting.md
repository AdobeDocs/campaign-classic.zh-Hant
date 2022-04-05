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
ht-degree: 1%

---

# IMS 疑難排解{#ims-troubleshooting}

![](../../assets/common.svg)

以下故障排除提示將幫助 **現場** 客戶在使用IMS整合時解決了最常見的問題。 對於 **托管** 客戶，請聯繫Adobe。

**外部帳戶**

應該只有 **一個** 具有以下設定的外部帳戶：

* **內部名稱**:Adobe_營銷_雲
* **類型**:Adobe Marketing Cloud

刪除具有相同設定的所有重複外部帳戶。

**產品上下文**

如果外部帳戶具有 **產品上下文** 欄位，檢查其值設定為： **dma_campigment_classic**

確保您的產品上下文與市場活動和Experience Cloud相同。

例如，如果 **產品上下文** 不顯示，預設產品上下文應 **dma_campigment** 競選和Experience Cloud。 如果 **產品上下文** 欄位，預設產品上下文應為 **dma_campigment_classic** 競選和Experience Cloud。

**[!UICONTROL IMS Server URL]**

在活動中 **Adobe Marketing Cloud** 外部帳戶，檢查 **[!UICONTROL IMS Server URL]** 或 `adobeid-na1.services.adobe.com` 或 `ims-na1.adobelogin.com`。 確保階段實例和生產實例都指向相同的IMS生產端點。

**關聯掩碼**

* 檢查嘗試登錄的用戶是否是企業儀表板中操作員組的一部分。
* 檢查 **[!UICONTROL Association Mask]** 是企業儀表板中用戶的運算子組名稱的前置詞。
* 確保沒有空白和拼寫錯誤。
* 檢查「市場活動」中運算子組的名稱是否未更改，並遵循以下語法：

```
<Association Mask> + <Operator Group Name in Campaign> = Complete name of the operator group in Enterprise Dashboard
```

**範圍**

市場活動外部帳戶中定義的範圍必須是IMS提供的範圍的子集。

**回調URL**

的 **回調URL** 應添加到allowlist中，並以「https://」開頭。 檢查 **回調URL** 連結到相應實例。 例如，生產實例應重定向到生產URL。

**客戶端ID和密碼**

客戶端ID與市場活動外部帳戶和IMS設定的客戶端ID匹配。

檢查輸入的客戶端密碼是否正確。

**重新啟動伺服器**

如果對市場活動外部帳戶中的上述設定進行了任何更改，請重新啟動伺服器

**常見錯誤類型和可能的解決方案**

* 用戶被重定向到adobe.com頁面：

   有個問題 **[!UICONTROL Callback URL]**。 請參閱上面的步驟以檢查 **[!UICONTROL Callback URL]** 配置。

* 消息「登錄名沒有與表達式匹配的任何權限」：

   請參閱上面的步驟以檢查 **[!UICONTROL Association Mask]** 和運算子組配置。

* 用戶無法訪問Adobe ID登錄頁：

   請參閱前面的步驟以檢查範圍配置。
