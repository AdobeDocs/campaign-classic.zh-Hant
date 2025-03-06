---
product: campaign
title: 傳入電子郵件
description: 深入瞭解傳入電子郵件工作流程活動
feature: Workflows, Channels Activity
hide: true
hidefromtoc: true
exl-id: b2a05e07-a7d7-436b-b2c6-90ab55d031cd
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 1%

---

# 傳入電子郵件{#inbound-emails}



**傳入電子郵件**&#x200B;活動可讓您從POP3郵件伺服器下載及處理電子郵件訊息。

![](assets/email_rec_edit_1.png)

**傳入電子郵件**&#x200B;活動的第一個索引標籤可讓您輸入POP3伺服器的引數，並輸入在收到每封郵件時要執行的指令碼。 第二個索引標籤可讓您將排程指派給活動，而第三個索引標籤會定義活動到期條件。

1. **[!UICONTROL Inbound Emails]**

   * **[!UICONTROL Use an external account]**

     啟用此選項時，您可以選取外部POP3帳戶，而不輸入連線引數。 **[!UICONTROL External account]**&#x200B;欄位指定要用來連線至電子郵件服務的外部POP3帳戶。 只有在啟用「使用外部帳戶」選項時，才會顯示此欄位。

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

   可從全域&#x200B;**[!UICONTROL mailMessage]**&#x200B;變數存取訊息的內容。

1. **[!UICONTROL Schedule]**

   若要定義活動的排程，請按一下&#x200B;**[!UICONTROL Scheduling]**&#x200B;索引標籤並核取&#x200B;**[!UICONTROL Plan execution]**。 按一下&#x200B;**[!UICONTROL Change]**&#x200B;按鈕以設定排程。

   排程設定與排程活動的設定相同。 請參閱[排程器](scheduler.md)。

1. **[!UICONTROL Expiration]**

   您可以透過&#x200B;**[!UICONTROL Expiration]**&#x200B;索引標籤定義到期延遲。

   ![](assets/email_rec_edit_3.png)

   設定與排程活動的設定相同。 請參閱[有效期](defining-approvals.md)。
