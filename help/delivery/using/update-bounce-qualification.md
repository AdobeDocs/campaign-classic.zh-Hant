---
product: campaign
title: 在 ISP 中斷後更新跳出資格
description: 了解如何在ISP中斷後更新退信資格。
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
hidefromtoc: true
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 3%

---

# 在Apple中斷{#update-bounce-qualification.md}後更新不正確的硬退信

![](../../assets/common.svg)

## 內容

2021年4月26日，Apple發生全域問題，導致傳送至有效Apple電子郵件地址的部分電子郵件訊息錯誤地硬退回，因為Apple伺服器的無效電子郵件地址，並有下列回應： 「550 5.1.1 &#39;電子郵件地址&#39;:用戶查找成功，但未找到用戶記錄。」

此問題發生在4/26，持續時間為東部標準時間早7點至晚1點。

>[!NOTE]
>
>您可以在[此頁面](https://www.apple.com/support/systemstatus/)上查看Apple系統狀態控制面板。

如果ISP中斷，透過Campaign傳送的電子郵件無法成功傳送給其收件者：這些電子郵件會錯誤標示為退信。

根據標準退信處理邏輯，Adobe Campaign會以&#x200B;**[!UICONTROL Quarantine]**&#x200B;設定，自動將這些收件者新增至隔離清單。 **[!UICONTROL Status]**&#x200B;若要修正此問題，您需要在Campaign中尋找並移除這些收件者，或將其&#x200B;**[!UICONTROL Status]**&#x200B;變更為&#x200B;**[!UICONTROL Valid]**，以便夜間清理工作流程將其移除，以更新隔離表格。

若要尋找受此問題影響的收件者，或若此情況再次發生於其他ISP，請參閱下列指示。

## 更新流程

您需要對隔離表格執行查詢，以篩除所有可能受中斷影響的Apple收件者(包括@icloud.com、@me.com、@mac.com)，以便從隔離清單中移除這些收件者，並納入未來的Campaign電子郵件傳送。

根據事件的時間範圍，以下是此查詢的建議准則。

>[!IMPORTANT]
>
>這些日期/時間以東部標準時區(EST)為基礎。 請根據您執行個體的時區進行調整。

* 對於隔離清單的&#x200B;**[!UICONTROL Error text]**&#x200B;欄位中，含有SMTP退信回應資訊的Campaign執行個體：

   * **錯誤文字（隔離文字）** 包含「使用者查詢成功，但找不到使用者記錄」，而「錯誤 **文字（隔離文字）」** 包含「support.apple.com」
   * **4/26/2021 07 00 AM或之後** 更新狀態(@lastModified):00:
   * **更新狀態(@lastModified)** (在4/26/2021 01 00 PM之前:00:)

* 若是隔離清單的&#x200B;**[!UICONTROL Error text]**&#x200B;欄位中有入站電子郵件規則資訊的促銷活動例項：

   * **錯誤文字（隔離文字）** 包含「Momen_Code10_InvalidRecipient」
   * **電子郵件網域(@domain)** 等於icloud.com或電子 **郵件網域(@domain)** 等於me.com或電子郵 **件網域(@domain)** 等於mac.com
   * **4/26/2021 07 00 AM或之後** 更新狀態(@lastModified):00:
   * **更新狀態(@lastModified)** (在4/26/2021 01 00 PM之前:00:)

在您獲得受影響的收件者清單後，您可以將其設定為&#x200B;**[!UICONTROL Valid]**&#x200B;狀態，以便讓其透過&#x200B;**[!UICONTROL Database cleanup]**&#x200B;工作流程從隔離清單中移除，或直接從表格中刪除。

**相關主題：**
* [了解傳送失敗](understanding-delivery-failures.md)
* [退回郵件資格](understanding-delivery-failures.md#bounce-mail-qualification)
