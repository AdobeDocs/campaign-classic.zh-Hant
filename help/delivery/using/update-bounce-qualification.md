---
product: campaign
title: 在 ISP 中斷後更新跳出資格
description: 了解如何在ISP中斷後更新退信資格。
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
source-git-commit: cee019432c64eaaefac86a27b731355242fd1555
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 3%

---

# 在Apple中斷後更新不正確的硬退信 {#update-bounce-qualification.md}

![](../../assets/common.svg)

## 內容

2021年4月26日，Apple發生全域問題，導致傳送至有效Apple電子郵件地址的部分電子郵件訊息錯誤地硬退信，因為Apple伺服器所寄送的無效電子郵件地址，並有下列回應：「550 5.1.1 &#39;電子郵件地址&#39;:用戶查找成功，但未找到用戶記錄。」

此問題發生在4/26，持續時間為東部標準時間早7點至晚1點。

>[!NOTE]
>
>您可以在 [本頁](https://www.apple.com/support/systemstatus/).

如果ISP中斷，透過Campaign傳送的電子郵件無法成功傳送給其收件者：這些電子郵件會錯誤標示為退信。

根據標準退信處理邏輯，Adobe Campaign會使用 **[!UICONTROL Status]** 設定 **[!UICONTROL Quarantine]**. 若要修正此問題，您需要尋找和移除這些收件者，或變更其，以更新Campaign中的隔離表格 **[!UICONTROL Status]** to **[!UICONTROL Valid]** 以便夜間清理工作流程將其移除。

若要尋找受此問題影響的收件者，或若此情況再次發生於其他ISP，請參閱下列指示。

## 更新流程

您需要對隔離表格執行查詢，以篩除所有可能受中斷影響的Apple收件者(包括@icloud.com、@me.com、@mac.com)，以便從隔離清單中移除，並納入未來的Campaign電子郵件傳送。

根據事件的時間範圍，以下是此查詢的建議准則。

>[!IMPORTANT]
>
>這些日期/時間以東部標準時區(EST)為基礎。 請根據您執行個體的時區進行調整。

* 若是具有SMTP退信回應資訊的促銷活動例項，請參閱 **[!UICONTROL Error text]** 隔離清單欄位：

   * **錯誤文本（隔離文本）** 包含「使用者查詢成功，但找不到使用者記錄」和 **錯誤文本（隔離文本）** 包含&quot;support.apple.com&quot;
   * **更新狀態(@lastModified)** 4/26/2021 07後:00:00 AM
   * **更新狀態(@lastModified)** 4/26/2021 01之前:00:00 PM

* 若為包含 **[!UICONTROL Error text]** 隔離清單欄位：

   * **錯誤文本（隔離文本）** 包含&quot;Momen_Code10_InvalidRecipient&quot;
   * **電子郵件網域(@domain)** 等於icloud.com或 **電子郵件網域(@domain)** 等於me.com或 **電子郵件網域(@domain)** 等於mac.com
   * **更新狀態(@lastModified)** 4/26/2021 07後:00:00 AM
   * **更新狀態(@lastModified)** 4/26/2021 01之前:00:00 PM

取得受影響收件者的清單後，您就可以將其設為 **[!UICONTROL Valid]** 以便將其從隔離清單中由 **[!UICONTROL Database cleanup]** 工作流程，或只是從表格中刪除。

**相關主題：**
* [了解傳送失敗](understanding-delivery-failures.md)
* [退回郵件資格](understanding-delivery-failures.md#bounce-mail-qualification)
