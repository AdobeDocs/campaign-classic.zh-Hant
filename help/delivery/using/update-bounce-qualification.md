---
product: campaign
title: 在 ISP 中斷後更新跳出資格
description: 瞭解如何在ISP停機後更新彈出資格
feature: Deliverability
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 3%

---

# 在Apple停機後更新不正確的硬邊界 {#update-bounce-qualification.md}

![](../../assets/common.svg)

## 內容

2021年4月26日，Apple的一個全球性問題導致一些發送到有效Apple電子郵件地址的電子郵件被錯誤地硬彈回，因為Apple伺服器的電子郵件地址無效，並回復如下：&quot;550 5.1.1 &#39;電子郵件地址&#39;:用戶查找成功，但未找到用戶記錄。」

此問題發生在東部時間4/26 ，持續時間為早7點至晚1點。

>[!NOTE]
>
>您可以檢查Apple系統狀態控制板 [此頁](https://www.apple.com/support/systemstatus/)。

在ISP中斷時，無法將通過Campaign發送的電子郵件成功發送給其收件人：這些電子郵件會被錯誤地標籤為回報。

根據標準彈出處理邏輯，Adobe Campaign自動將這些收件人添加到隔離清單中， **[!UICONTROL Status]** 設定 **[!UICONTROL Quarantine]**。 要更正此問題，您需要通過查找和刪除這些收件人或更改其來更新市場活動中的隔離表 **[!UICONTROL Status]** 至 **[!UICONTROL Valid]** 這樣夜間清理工作流就會刪除它們。

要查找受此問題影響的收件人，或在其他ISP再次出現此問題時，請參閱以下說明。

## 要更新的進程

您需要在隔離表上運行查詢，以篩選所有可能受中斷影響的Apple收件人(包括@icloud.com、@me.com、@mac.com)，以便他們可以從隔離清單中刪除，並包括在將來的市場活動電子郵件遞送中。

根據事件的時間範圍，以下是此查詢的建議准則。

>[!IMPORTANT]
>
>這些日期/時間基於東部標準時區(EST)。 請根據實例的時區進行調整。

* 對於具有SMTP彈出響應資訊的市場活動實例 **[!UICONTROL Error text]** 隔離清單的欄位：

   * **錯誤文本（隔離文本）** 包含「用戶查找成功但未找到用戶記錄」和 **錯誤文本（隔離文本）** 包含&quot;support.apple.com&quot;
   * **更新狀態(@lastModified)** 4/26/2021 07後:00:上午00點
   * **更新狀態(@lastModified)** 4/26/2021 01之前:00:00 PM

* 對於具有入站電子郵件規則資訊的市場活動實例，請 **[!UICONTROL Error text]** 隔離清單的欄位：

   * **錯誤文本（隔離文本）** 包含&quot;Momen_Code10_InvalidRecipient&quot;
   * **電子郵件域(@domain)** 等於icloud.com或 **電子郵件域(@domain)** 等於me.com或 **電子郵件域(@domain)** 等於mac.com
   * **更新狀態(@lastModified)** 4/26/2021 07後:00:上午00點
   * **更新狀態(@lastModified)** 4/26/2021 01之前:00:00 PM

一旦您擁有受影響的收件人清單，您就可以將其設定為 **[!UICONTROL Valid]** 這樣它們就會被 **[!UICONTROL Database cleanup]** 工作流，或者只是從表中刪除它們。

**相關主題：**
* [瞭解交付失敗](understanding-delivery-failures.md)
* [退回郵件資格](understanding-delivery-failures.md#bounce-mail-qualification)
