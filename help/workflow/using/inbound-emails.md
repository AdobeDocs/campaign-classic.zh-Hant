---
product: campaign
title: 傳入電子郵件
description: 深入瞭解傳入電子郵件工作流程活動
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
feature: Workflows, Channels Activity
exl-id: b2a05e07-a7d7-436b-b2c6-90ab55d031cd
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 3%

---

# 傳入電子郵件{#inbound-emails}



此 **傳入電子郵件** 活動可讓您從POP3郵件伺服器下載及處理電子郵件訊息。

![](assets/email_rec_edit_1.png)

的第一個標籤 **傳入電子郵件** 活動可讓您輸入POP3伺服器的引數，並輸入在收到每則訊息時要執行的指令碼。 第二個索引標籤可讓您將排程指派給活動，而第三個索引標籤會定義活動到期條件。

1. **[!UICONTROL Inbound Emails]**

   * **[!UICONTROL Use an external account]**

     啟用此選項時，您可以選取外部POP3帳戶，而不輸入連線引數。 此 **[!UICONTROL External account]** 欄位會指定用來連線至電子郵件服務的外部POP3帳戶。 只有在啟用「使用外部帳戶」選項時，才會顯示此欄位。

     如果未選取此選項，您必須指定下列引數：

     ![](assets/email_rec_edit_1b.png)

      * **[!UICONTROL POP3 server]**

        POP3伺服器的名稱。

      * **[!UICONTROL POP3 account]**

        使用者的名稱。

      * **[!UICONTROL Password]**

        使用者帳戶密碼。

      * **[!UICONTROL Port]**

        POP3連線埠號碼。 預設連線埠為110。

   * **[!UICONTROL Stop as soon as email is processed]**

     此選項可讓您逐一處理電子郵件。 活動只會啟動其轉變一次，然後完成處理，將未處理的訊息留在伺服器上。

1. **[!UICONTROL Script]**

   指令碼可讓您處理訊息，並根據訊息內容執行各種操作。 指令碼會針對每個訊息執行，並可決定要對訊息執行的操作（離開或刪除訊息）以及啟動出站轉變。

   傳回碼必須是下列其中一個值：

   * 1 — 從伺服器刪除訊息，並啟動出站轉變。
   * 2 — 在伺服器上保留訊息並啟動出站轉變。
   * 3 — 從伺服器刪除訊息。
   * 4 — 在伺服器上保留訊息。

   可從全域存取訊息的內容 **[!UICONTROL mailMessage]** 變數中。

1. **[!UICONTROL Schedule]**

   若要定義活動的排程，請按一下 **[!UICONTROL Scheduling]** 標籤並核取 **[!UICONTROL Plan execution]**. 按一下 **[!UICONTROL Change]** 按鈕以設定排程。

   排程設定與排程活動的設定相同。 請參閱 [排程器](scheduler.md).

1. **[!UICONTROL Expiration]**

   您可以透過定義到期延遲 **[!UICONTROL Expiration]** 標籤。

   ![](assets/email_rec_edit_3.png)

   設定與排程活動的設定相同。 請參閱 [有效期](defining-approvals.md).
