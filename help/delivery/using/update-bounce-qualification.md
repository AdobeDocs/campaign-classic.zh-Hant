---
solution: Campaign Classic
product: campaign
title: 在 ISP 中斷後更新跳出資格
description: 瞭解如何在ISP中斷後更新反彈資格。
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
hidefromtoc: true
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
translation-type: tm+mt
source-git-commit: 7c161862a4ce2e86e7968fd61af6b8ca28d6623f
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 3%

---

# 在Apple中斷{#update-bounce-qualification.md}後更新不正確的硬彈回數

## 內容

2021年4月26日，Apple發生全域問題，導致傳送至有效Apple電子郵件地址的部分電子郵件訊息，由於Apple伺服器無效的電子郵件地址遭到錯誤硬性反彈，並出現反彈後回應： &quot;550 5.1.1 <email address>:使用者查閱成功，但找不到使用者記錄。」

此問題發生在東部時間4/26，持續時間為上午7點至下午1點。

如果ISP中斷，透過Campaign傳送的電子郵件無法成功傳送給其收件者：這些電子郵件會被錯誤地標示為彈回。

>[!NOTE]
>
>您可以在[此頁面](https://www.apple.com/support/systemstatus/)上檢查Apple System Status Dashboard。

根據標準彈回數處理邏輯，Adobe Campaign會自動將這些收件者加入隔離清單，並設定&#x200B;**[!UICONTROL Quarantine]**。 **[!UICONTROL Status]**&#x200B;若要修正此問題，您必須尋找並移除這些收件者，或將其&#x200B;**[!UICONTROL Status]**&#x200B;變更為&#x200B;**[!UICONTROL Valid]**，以便每日清除工作流程移除這些收件者，以更新Campaign中的隔離表格。

若要尋找受此問題影響的收件者，或是在其他ISP再次發生此問題時，請參閱以下說明。

## 更新程式

您必須在隔離表格上執行查詢，以篩選所有可能受中斷影響的Apple收件者（包括@iccloud.com、@me.com、@mac.com），以便從隔離清單中移除，並納入未來的Campaign電子郵件傳送。

根據事件的時間範圍，以下是此查詢的建議准則。

>[!IMPORTANT]
>
>這些日期／時間以東部標準時區(EST)為基礎。 請根據您實例的時區進行調整。

* 對於隔離清單&#x200B;**[!UICONTROL Error text]**&#x200B;欄位中具有SMTP彈迴響應資訊的促銷活動實例：

   * **錯誤文字（隔離文字）** 包含「使用者查閱成功但找不到使用者記錄」，而 **錯誤文字（隔離文字）** 包含「support.apple.com」
   * **更新狀態(@lastModified)** 於4/26/2021 07:00:00 AM或之後
   * **更新狀態(@lastModified)** 於4/26/2021 01:00:00 PM或之前

* 對於隔離清單&#x200B;**[!UICONTROL Error text]**&#x200B;欄位中包含入站電子郵件規則資訊的促銷活動實例：

   * **錯誤文字（隔離文字）** 包含&quot;Momen_Code10_InvalidRecipient&quot;
   * **電子郵件網域(@domain)** 等於icloud.com&quot; OR Email domain(@domain)等於me.com&quot; OR Email domain(@domain)等於mac.com&quot;
   * **更新狀態(@lastModified)** 於4/26/2021 07:00:00 AM或之後
   * **更新狀態(@lastModified)** 於4/26/2021 01:00:00 PM或之前

在您擁有受影響接收者的清單後，可以將其設定為&#x200B;**[!UICONTROL Valid]**&#x200B;狀態，以便通過&#x200B;**[!UICONTROL Database cleanup]**&#x200B;工作流將其從隔離清單中刪除，或者只從表中刪除它們。

**相關主題：**
* [瞭解傳送失敗](../../delivery/using/understanding-delivery-failures.md)
* [退回郵件資格](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)
