---
product: campaign
title: 在Apple 2021年中斷後更新彈回資格
description: 瞭解如何在Apple 2021年中斷後更新跳出資格
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Deliverability
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 1%

---

# 在Apple中斷後更新不正確的硬退信 {#update-bounce-qualification.md}



## 內容

在2021年4月26日，Apple發生全球性問題，導致傳送至有效Apple電子郵件地址的某些電子郵件訊息被Apple伺服器錯誤地硬退為無效的電子郵件地址，並出現以下回應：「550 5.1.1 &#39;電子郵件地址&#39;：使用者查詢成功但找不到使用者記錄。」

此問題發生於2026年4月26日，並持續至東部時間上午7點至下午1點。

>[!NOTE]
>
>您可以檢視Apple系統狀態儀表板，於 [此頁面](https://www.apple.com/support/systemstatus/).

如果ISP發生中斷，透過Campaign傳送的電子郵件無法成功傳遞給其收件者：這些電子郵件將錯誤標籤為跳出。

根據標準退信處理邏輯，Adobe Campaign會使用自動將這些收件者新增至隔離清單 **[!UICONTROL Status]** 設定 **[!UICONTROL Quarantine]**. 若要修正此問題，您需要尋找並移除這些收件者，或變更其收件者，以更新Campaign中的隔離表格 **[!UICONTROL Status]** 至 **[!UICONTROL Valid]** 以便「夜間清理」工作流程會將其移除。

若要尋找受此問題影響的收件者，或當此問題再次發生在任何其他ISP上時，請參閱下列指示。

## 更新流程

您必須在隔離表格上執行查詢，以篩選出所有可能受到中斷影響的Apple收件者(包括、@icloud.com、@me.com、@mac.com)，以便將其從隔離清單中移除，並包含在將來的Campaign電子郵件傳送中。

根據事件的時間範圍，以下是此查詢的建議准則。

>[!IMPORTANT]
>
>這些日期/時間以東部標準時區(EST)為基礎。 請根據您的執行個體時區進行調整。

* 對於具有SMTP退回回應資訊的Campaign執行個體， **[!UICONTROL Error text]** 隔離清單的欄位：

   * **錯誤文字（隔離文字）** 包含「使用者查詢成功但找不到使用者記錄」和 **錯誤文字（隔離文字）** 包含&quot;support.apple.com&quot;
   * **更新狀態(@lastModified)** 2021年4月26日或之後07:00:上午00
   * **更新狀態(@lastModified)** 2021 01年4月26日或之前:00:下午00

* 對於含有傳入電子郵件規則資訊的Campaign執行個體， **[!UICONTROL Error text]** 隔離清單的欄位：

   * **錯誤文字（隔離文字）** 包含「Momen_Code10_InvalidRecipient」
   * **電子郵件網域(@domain)** 等於icloud.com或 **電子郵件網域(@domain)** 等於me.com或 **電子郵件網域(@domain)** 等於mac.com
   * **更新狀態(@lastModified)** 2021年4月26日或之後07:00:上午00
   * **更新狀態(@lastModified)** 2021 01年4月26日或之前:00:下午00

取得受影響的收件者清單後，您就可以將收件者設定為 **[!UICONTROL Valid]** 因此，會將他們從隔離清單中移除， **[!UICONTROL Database cleanup]** 工作流程，或從表格中刪除工作流程。

**相關主題：**
* [瞭解傳遞失敗](understanding-delivery-failures.md)
* [退回郵件資格](understanding-delivery-failures.md#bounce-mail-qualification)
