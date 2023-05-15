---
product: campaign
title: 在 ISP 中斷後更新跳出資格
description: 了解如何在ISP中斷後更新退信資格
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

如果ISP中斷，透過Campaign傳送的電子郵件無法成功傳送給其收件者：這些電子郵件會錯誤標示為退信。

例如，Apple或Gmail的全域問題可能會導致傳送至有效Apple或Gmail電子郵件地址的部分電子郵件訊息，由於ISP伺服器的無效電子郵件地址，而錯誤地硬退信，且會出現下列回應：

* 「550 5.1.1 &#39;電子郵件地址&#39;:用戶查找成功，但未找到用戶記錄。」

* &quot;550 &#39;電子郵件地址&#39;收件人已拒絕&quot;

請注意，如果延遲彈回訊息「452要求動作已中止：會觀察到「稍後重試」 — 會自動重試，且不需要任何動作。 當ISP恢復滿容量時，應會改善。

>[!NOTE]
>
>您可以在 [本頁](https://www.apple.com/support/systemstatus/){_blank}。
>
>您可以在「Google工作區狀態控制面板」上查看 [本頁](https://www.google.com/appsstatus#hl=en&amp;v=status){_blank}。

## 影響{#update-bounce-impact}

如果ISP中斷，透過Campaign傳送的電子郵件無法成功傳送給其收件者：這些電子郵件會錯誤標示為退信。

根據標準退信處理邏輯，Adobe Campaign會使用 **[!UICONTROL Status]** 設定 **[!UICONTROL Quarantine]**. 若要修正此問題，您需要尋找和移除這些收件者，或變更其，以更新Campaign中的隔離表格 **[!UICONTROL Status]** to **[!UICONTROL Valid]** 以便夜間清理工作流程將其移除。

若要尋找受此問題影響的收件者，請參閱下列指示。

## 更新流程{#update-bounce-update}

您需要對隔離表格執行查詢，以篩除所有受中斷影響的收件者(例如Apple)，這些地址包括@icloud.com、@me.com、@mac.com，以便從隔離清單中移除，並包含在未來的Campaign電子郵件傳送中。

根據事件的時間範圍和ISP，以下是此查詢的建議准則。

* 若為具有 **[!UICONTROL Error text]** 隔離清單欄位：

   * **錯誤文本（隔離文本）** 包含&quot;Momen_Code10_InvalidRecipient&quot;
   * **電子郵件網域(@domain)** 等於domain1.com或 **電子郵件網域(@domain)** 等於domain2.com或 **電子郵件網域(@domain)** 等於domain3.com
   * **更新狀態(@lastModified)** MM/DD/YYYY HH時或之後:MM:SS AM
   * **更新狀態(@lastModified)** 在MM/DD/YYYY HH之前或之前:MM:SS PM

* 若是在中具有SMTP退信回應資訊的促銷活動環境， **[!UICONTROL Error text]** 隔離清單欄位：

   * **錯誤文本（隔離文本）** 包含「550-5.1.1」和 **錯誤文本（隔離文本）** 包含&quot;support.ISP.com&quot;

      其中「support.ISP.com」可以是：&quot;support.apple.com&quot;或&quot;support.google.com&quot;，例如

   * **更新狀態(@lastModified)** MM/DD/YYYY HH時或之後:MM:SS AM
   * **更新狀態(@lastModified)** 在MM/DD/YYYY HH之前或之前:MM:SS PM


取得受影響收件者的清單後，您就可以將其設為 **[!UICONTROL Valid]** 以便將其從隔離清單中由 **[!UICONTROL Database cleanup]** 工作流程，或只是從表格中刪除。

**相關主題：**
* [了解傳送失敗](understanding-delivery-failures.md)
* [退回郵件資格](understanding-delivery-failures.md#bounce-mail-qualification)
