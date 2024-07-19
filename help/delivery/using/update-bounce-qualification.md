---
product: campaign
title: 在Apple 2021年中斷後更新退回資格
description: 瞭解如何在Apple 2021年中斷後更新跳出資格
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Deliverability
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# 在Apple中斷{#update-bounce-qualification.md}後更新不正確的硬退信

## 內容

2021年4月26日，Apple發生全域問題，導致傳送至有效Apple電子郵件地址的某些電子郵件訊息被Apple伺服器錯誤地硬退為無效的電子郵件地址，並出現以下回應：「550 5.1.1 &#39;電子郵件地址&#39;：使用者查詢成功但找不到使用者記錄。」

此問題發生於2026年4月26日，並持續到東部時間上午7點至下午1點。

>[!NOTE]
>
>您可以在[此頁面](https://www.apple.com/support/systemstatus/)上檢視Apple系統狀態儀表板。

如果ISP發生中斷，透過Campaign傳送的電子郵件無法成功傳送給其收件者：這些電子郵件將錯誤標示為跳出。

根據標準退信處理邏輯，Adobe Campaign會自動將這些收件者新增至隔離清單，**[!UICONTROL Status]**&#x200B;設定為&#x200B;**[!UICONTROL Quarantine]**。 若要修正此問題，您需要透過尋找並移除這些收件者，或將其&#x200B;**[!UICONTROL Status]**&#x200B;變更為&#x200B;**[!UICONTROL Valid]**，以在Campaign中更新隔離表格，讓夜間清理工作流程將移除這些收件者。

若要尋找受此問題影響的收件者，或當此問題在任何其他ISP中再次發生時，請參閱下列指示。

## 更新流程

您將需要在隔離表格上執行查詢，以篩選出所有可能受到中斷影響的Apple收件者(包括、@icloud.com、@me.com、@mac.com)，以便將其從隔離清單中移除，並包含在將來的Campaign電子郵件傳送中。

根據事件的時間範圍，以下是此查詢的建議准則。

>[!IMPORTANT]
>
>這些日期/時間以東部標準時區(EST)為基礎。 請根據您執行個體的時區進行調整。

* 對於在隔離清單的&#x200B;**[!UICONTROL Error text]**&#x200B;欄位中有SMTP退回回應資訊的Campaign執行個體：

   * **錯誤文字（隔離文字）**&#x200B;包含「使用者查詢成功但找不到使用者記錄」以及&#x200B;**錯誤文字（隔離文字）**&#x200B;包含「support.apple.com」
   * 上午4/26/2021 07:00:00或之後的&#x200B;**更新狀態(@lastModified)**
   * 下午4/26/2021 01:00:00或之前的&#x200B;**更新狀態(@lastModified)**

* 對於在隔離清單的&#x200B;**[!UICONTROL Error text]**&#x200B;欄位中有傳入電子郵件規則資訊的Campaign執行個體：

   * **錯誤文字（隔離文字）**&#x200B;包含「Momen_Code10_InvalidRecipient」
   * **電子郵件網域(@domain)**&#x200B;等於icloud.com或&#x200B;**電子郵件網域(@domain)**&#x200B;等於me.com或&#x200B;**電子郵件網域(@domain)**&#x200B;等於mac.com
   * 上午4/26/2021 07:00:00或之後的&#x200B;**更新狀態(@lastModified)**
   * 下午4/26/2021 01:00:00或之前的&#x200B;**更新狀態(@lastModified)**

一旦您擁有受影響的收件者清單，您就可以將他們的狀態設定為&#x200B;**[!UICONTROL Valid]**，以便透過&#x200B;**[!UICONTROL Database cleanup]**&#x200B;工作流程將其從隔離清單中移除，或者只是從表格中刪除他們。

**相關主題：**
* [瞭解傳遞失敗](understanding-delivery-failures.md)
* [退回郵件資格](understanding-delivery-failures.md#bounce-mail-qualification)
