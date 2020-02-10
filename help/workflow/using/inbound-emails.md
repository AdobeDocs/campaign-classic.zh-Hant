---
title: 傳入電子郵件
seo-title: 傳入電子郵件
description: 傳入電子郵件
seo-description: null
page-status-flag: never-activated
uuid: 6bcc7952-f051-4e50-8833-95d49c7ed781
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: event-activities
discoiquuid: 4c0530b1-0292-45bc-8730-668bc5b8550b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 傳入電子郵件{#inbound-emails}

「傳 **入電子郵件** 」活動可讓您從POP3郵件伺服器下載並處理電子郵件訊息。

![](assets/email_rec_edit_1.png)

「入站電子郵 **件** 」活動的第一個頁籤允許您輸入POP3伺服器的參數，並輸入在收到每條消息時要執行的指令碼。 第二個標籤可讓您指派排程給活動，而第三個標籤則定義活動到期條件。

1. **[!UICONTROL Inbound Emails]**

   * **[!UICONTROL Use an external account]**

      啟用此選項時，您可以選擇外部POP3帳戶，而不是輸入連接參數。 該 **[!UICONTROL External account]** 欄位指定用於連接到電子郵件服務的外部POP3帳戶。 只有啟用「使用外部帳戶」選項時，才會顯示此欄位。

      如果未選取此選項，您必須指定下列參數：

      ![](assets/email_rec_edit_1b.png)

      * **[!UICONTROL POP3 server]**

         POP3伺服器的名稱。

      * **[!UICONTROL POP3 account]**

         用戶名。

      * **[!UICONTROL Password]**

         使用者帳戶密碼。

      * **[!UICONTROL Port]**

         POP3連接埠號。 預設埠為110。
   * **[!UICONTROL Stop as soon as email is processed]**

      此選項可讓您逐一處理電子郵件。 活動只啟動其轉換一次，然後完成處理，在伺服器上留下未處理的訊息。


1. **[!UICONTROL Script]**

   此指令碼可讓您處理訊息，並執行取決於訊息內容的各種作業。 該指令碼對每條消息執行，並可確定要對消息執行的操作（離開或刪除消息）和激活出站轉換。

   傳回代碼必須是下列值之一：

   * 1 —— 從伺服器刪除消息並激活出站轉換。
   * 2 —— 將消息保留在伺服器上並激活出站過渡。
   * 3 —— 從伺服器刪除消息。
   * 4 —— 將消息保留在伺服器上。
   可從全域變數存取訊息的 **[!UICONTROL mailMessage]** 內容。

1. **[!UICONTROL Schedule]**

   要定義活動的計畫，請按一下該標 **[!UICONTROL Scheduling]** 簽並選中 **[!UICONTROL Plan execution]**。 按一下 **[!UICONTROL Change]** 按鈕以設定排程。

   計畫配置與計畫活動的配置相同。 請參閱 [Scheduler](../../workflow/using/scheduler.md)。

1. **[!UICONTROL Expiration]**

   您可以透過標籤來定義到期延 **[!UICONTROL Expiration]** 遲。

   ![](assets/email_rec_edit_3.png)

   設定與排程活動的設定相同。 請參閱 [到期](../../workflow/using/executing-a-workflow.md#expirations)。

