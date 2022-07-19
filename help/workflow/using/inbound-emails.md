---
product: campaign
title: 傳入電子郵件
description: 瞭解有關入站電子郵件工作流活動的詳細資訊
feature: Workflows, Channels Activity
exl-id: b2a05e07-a7d7-436b-b2c6-90ab55d031cd
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 1%

---

# 傳入電子郵件{#inbound-emails}

![](../../assets/v7-only.svg)

的 **入站電子郵件** 活動，您可以從POP3郵件伺服器下載和處理電子郵件。

![](assets/email_rec_edit_1.png)

第一個頁籤 **入站電子郵件** 活動，您可以輸入POP3伺服器的參數，並輸入在收到每條消息時要執行的指令碼。 第二個頁籤允許您為活動分配計畫，第三個頁籤定義活動到期條件。

1. **[!UICONTROL Inbound Emails]**

   * **[!UICONTROL Use an external account]**

      激活此選項後，您可以選擇外部POP3帳戶，而不是輸入連接參數。 的 **[!UICONTROL External account]** 欄位指定用於連接到電子郵件服務的外部POP3帳戶。 僅當啟用「使用外部帳戶」選項時，此欄位才可見。

      如果未選擇此選項，則必須指定以下參數：

      ![](assets/email_rec_edit_1b.png)

      * **[!UICONTROL POP3 server]**

         POP3伺服器的名稱。

      * **[!UICONTROL POP3 account]**

         用戶的名稱。

      * **[!UICONTROL Password]**

         用戶帳戶密碼。

      * **[!UICONTROL Port]**

         POP3連接埠號。 預設埠為110。
   * **[!UICONTROL Stop as soon as email is processed]**

      此選項允許您逐個處理電子郵件。 該活動僅激活其轉換一次，然後完成處理，將未處理的消息留在伺服器上。


1. **[!UICONTROL Script]**

   該指令碼允許您處理消息並執行取決於消息內容的各種操作。 該指令碼針對每條消息執行，並且可以確定要對消息（離開或刪除該消息）和激活出站轉換執行的操作。

   返回代碼必須是以下值之一：

   * 1 — 從伺服器刪除消息並激活出站轉換。
   * 2 — 將消息留在伺服器上並激活出站轉換。
   * 3 — 從伺服器刪除消息。
   * 4 — 將消息留在伺服器上。

   可從全局訪問消息的內容 **[!UICONTROL mailMessage]** 變數。

1. **[!UICONTROL Schedule]**

   要定義活動的計畫，請按一下 **[!UICONTROL Scheduling]** 頁籤 **[!UICONTROL Plan execution]**。 按一下 **[!UICONTROL Change]** 按鈕來配置計畫。

   計畫配置與計畫活動的配置相同。 請參閱 [調度程式](scheduler.md)。

1. **[!UICONTROL Expiration]**

   您可以通過 **[!UICONTROL Expiration]** 頁籤。

   ![](assets/email_rec_edit_3.png)

   配置與計畫活動的配置相同。 請參閱 [過期](defining-approvals.md)。
