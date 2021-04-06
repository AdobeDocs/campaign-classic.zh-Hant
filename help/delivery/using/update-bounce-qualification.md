---
solution: Campaign Classic
product: campaign
title: 在ISP中斷後更新反彈資格
description: 瞭解如何在ISP中斷後更新反彈資格。
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
hidefromtoc: true
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
translation-type: tm+mt
source-git-commit: 3b5a6e6f03d9cb26ed372c3df069cbada36756a2
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 1%

---

# 在ISP中斷{#update-bounce-qualification.md}後更新彈回資格

## 內容

如果ISP中斷，透過Campaign傳送的電子郵件無法成功傳送給其收件者：這些電子郵件會被錯誤地標示為彈回。

2020年12月，Gmail的全球性問題導致一些電子郵件被發送到有效Gmail電子郵件地址，但由於Gmail伺服器的電子郵件地址無效，並出現以下反彈：*&quot;550-5.1.1您嘗試觸及的電子郵件帳戶不存在。&quot;*

谷歌表示，造成此問題的Gmail服務中斷和中斷始於12月14日早上6:55，於12月15日東部時間下午6:09結束。 我們的資料分析還顯示，Gmail彈回數在美國東部時間12月16日凌晨2點06分出現非常短的尖峰，其中大部分發生在美國東部時間12月15日東部時間下午2點至下午6點30分。

>[!NOTE]
>
>您可以在[此頁面](https://www.google.com/appsstatus#hl=en&amp;v=status)上檢查Google Workspace狀態控制面板。


根據標準彈回數處理邏輯，Adobe Campaign會自動將這些收件者加入隔離清單，並設定&#x200B;**[!UICONTROL Quarantine]**。 **[!UICONTROL Status]**&#x200B;若要修正此問題，您必須尋找並移除這些收件者，或將其&#x200B;**[!UICONTROL Status]**&#x200B;變更為&#x200B;**[!UICONTROL Valid]**，以便每日清除工作流程移除這些收件者，以更新Campaign中的隔離表格。

若要尋找受此Gmail問題影響的收件者，或在其他ISP再次發生此情況時，請參閱以下說明。

## 更新程式

您必須在隔離表格上執行查詢，以篩選所有可能受到中斷影響的Gmail（或其他ISP）收件者，以便從隔離清單中移除這些收件者，並納入未來的Campaign電子郵件傳送。

根據事件的時間範圍，以下是此查詢的建議准則。

>[!IMPORTANT]
>
>這些日期／時間以東部標準時區(EST)為基礎。 請根據您實例的時區進行調整。

* 對於隔離清單&#x200B;**[!UICONTROL Error text]**&#x200B;欄位中具有SMTP彈迴響應資訊的促銷活動實例：

   * **錯誤文字（隔離文字）** 包含「550-5.1.1您嘗試存取的電子郵件帳戶不存在」，而「 **Error」文字（隔離文字）** 包含「support.google.com」 **
   * **12/14/2020 6:55:00 AM** 或之後的更新狀態(@lastModified)
   * **12/16/2020 6:00:00 AM** 或之前更新狀態(@lastModified)

* 對於隔離清單&#x200B;**[!UICONTROL Error text]**&#x200B;欄位中包含入站電子郵件規則資訊的促銷活動實例：

   * **錯誤文字（隔離文字）** 包含&quot;Momen_Code10_InvalidRecipient&quot;
   * **電子郵件網域(@domain)** 等於&quot;gmail.com&quot;，或電子郵件網域(@domain)等於&quot;googlemail.com&quot;
   * **12/14/2020 6:55:00 AM** 或之後的更新狀態(@lastModified)
   * **12/16/2020 6:00:00 AM** 或之前更新狀態(@lastModified)

在您擁有受影響接收者的清單後，可以將其設定為&#x200B;**[!UICONTROL Valid]**&#x200B;狀態，以便通過&#x200B;**[!UICONTROL Database cleanup]**&#x200B;工作流將其從隔離清單中刪除，或者只從表中刪除它們。

**相關主題：**
* [瞭解傳送失敗](../../delivery/using/understanding-delivery-failures.md)
* [退回郵件資格](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)
