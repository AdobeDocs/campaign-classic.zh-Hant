---
product: campaign
title: 在 ISP 中斷後更新跳出資格
description: 瞭解如何在ISP中斷後更新跳出資格
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Deliverability
hide: true
hidefromtoc: true
exl-id: 7a9afe0a-0219-40f1-9fe2-6374db8d555c
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 4%

---

# 在 ISP 中斷後更新不正確的硬退件 {#update-bounces}



## 內容{#update-bounce-context}

如果ISP發生中斷，透過Campaign傳送的電子郵件無法成功傳遞給其收件者：這些電子郵件將錯誤標籤為跳出。

例如，Apple或Gmail的全域問題可能會導致傳送至有效Apple或Gmail電子郵件地址的某些電子郵件錯誤地硬退回，由ISP伺服器當作無效的電子郵件地址，並出現以下回應：

* 「550 5.1.1 &#39;電子郵件地址&#39;：使用者查詢成功，但找不到使用者記錄。」

* 「550 &#39;email address&#39;收件者已拒絕」

請注意，如果觀察到延遲跳出並出現訊息「452請求的動作已中止：請稍後再試」，則會自動重試這些動作，而不需要任何動作。 隨著ISP恢復全部容量，這些功能應該會有所改善。

>[!NOTE]
>
>您可以檢視Apple系統狀態儀表板，於 [此頁面](https://www.apple.com/support/systemstatus/){_blank}。
>
>您可以檢視Google Workspace狀態控制面板，於 [此頁面](https://www.google.com/appsstatus#hl=en&amp;v=status){_blank}。

## 影響{#update-bounce-impact}

如果ISP發生中斷，透過Campaign傳送的電子郵件無法成功傳遞給其收件者：這些電子郵件將錯誤標籤為跳出。

根據標準退信處理邏輯，Adobe Campaign會使用自動將這些收件者新增至隔離清單 **[!UICONTROL Status]** 設定 **[!UICONTROL Quarantine]**. 若要修正此問題，您需要尋找並移除這些收件者，或變更其收件者，以更新Campaign中的隔離表格 **[!UICONTROL Status]** 至 **[!UICONTROL Valid]** 以便「夜間清理」工作流程會將其移除。

若要尋找受此問題影響的收件者，請參閱下列指示。

## 更新流程{#update-bounce-update}

您必須在隔離表格上執行查詢，以篩選出所有受影響的收件者(例如Apple)，其位址包括、@icloud.com、@me.com、@mac.com — 這些位址可能受到中斷影響，因此可將這些位址從隔離清單中移除，並納入未來的Campaign電子郵件傳送中。

根據事件的時間範圍和ISP，以下是此查詢的建議准則。

* 適用於具有傳入電子郵件規則資訊的行銷活動環境。 **[!UICONTROL Error text]** 隔離清單的欄位：

   * **錯誤文字（隔離文字）** 包含「Momen_Code10_InvalidRecipient」
   * **電子郵件網域(@domain)** 等於domain1.com或 **電子郵件網域(@domain)** 等於domain2.com或 **電子郵件網域(@domain)** 等於domain3.com
   * **更新狀態(@lastModified)** YYYY/MM/DD HH當天或之後:MM:SS AM
   * **更新狀態(@lastModified)** YYYY/MM/DD HH當天或之前:MM:SS PM

* 對於含有SMTP退回回應資訊的Campaign環境 **[!UICONTROL Error text]** 隔離清單的欄位：

   * **錯誤文字（隔離文字）** 包含「550-5.1.1」和 **錯誤文字（隔離文字）** 包含&quot;support.ISP.com&quot;

      其中「support.ISP.com」可以是：例如「support.apple.com」或「support.google.com」

   * **更新狀態(@lastModified)** YYYY/MM/DD HH當天或之後:MM:SS AM
   * **更新狀態(@lastModified)** YYYY/MM/DD HH當天或之前:MM:SS PM


取得受影響的收件者清單後，您就可以將收件者設定為 **[!UICONTROL Valid]** 因此，會將他們從隔離清單中移除， **[!UICONTROL Database cleanup]** 工作流程，或從表格中刪除工作流程。

**相關主題：**
* [瞭解傳遞失敗](understanding-delivery-failures.md)
* [退回郵件資格](understanding-delivery-failures.md#bounce-mail-qualification)
