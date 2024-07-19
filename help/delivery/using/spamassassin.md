---
product: campaign
title: SpamAssassin
description: 瞭解如何使用SpamAssassin設定電子郵件垃圾郵件偵測
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Email, Deliverability
role: User
exl-id: 8be6836d-f7dc-4199-b2b2-b6a9cac9d162
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 4%

---

# SpamAssassin{#spamassassin}

Adobe Campaign可設定為搭配[SpamAssassin](https://spamassassin.apache.org) （用於電子郵件垃圾郵件篩選的協力廠商服務）使用。 這可讓您對電子郵件評分，以判斷郵件是否在收到時遭到的反垃圾郵件工具視為垃圾郵件的風險。

SpamAssassin運用各種垃圾郵件偵測技術，包括：

* DNS型和模糊總和型垃圾郵件偵測
* 貝葉斯篩選
* 外部計畫
* 封鎖清單
* 線上資料庫

>[!NOTE]
>
>必須在Adobe Campaign應用程式伺服器上安裝和設定SpamAssassin。 如需詳細資訊，請參閱[本章節](../../installation/using/configuring-spamassassin.md)。
>
>管控元素是否為垃圾郵件的規則，可透過SpamAssassin進行管理，並可由具有許可權的管理員編輯。

## 在Campaign中使用SpamAssassin {#using-spamassassin}

建立電子郵件傳遞並定義其內容後，請遵循下列步驟來評估風險。

如需建立和設計傳遞的詳細資訊，請參閱[本節](about-email-channel.md)。

1. 前往&#x200B;**[!UICONTROL Preview]**&#x200B;標籤。
1. 選取收件者以預覽您的傳遞。

   ![](assets/s_tn_del_preview_spamassassin_recipient.png)

   >[!NOTE]
   >
   >如果您未選取收件者，則無法執行反垃圾郵件檢查。

1. 警告訊息會提供測試的結果。 如果偵測到高風險等級，會顯示下列警告訊息：

   ![](assets/s_tn_del_preview_spamassassin_ko.png)

1. 按一下警告旁的&#x200B;**[!UICONTROL More...]**&#x200B;連結。
1. 選取 **[!UICONTROL Anti-spam checking]** 索引標籤。
1. 移至&#x200B;**[!UICONTROL Points / Rule / Description]**&#x200B;區段以檢視此風險的原因。

   ![](assets/s_tn_del_msg_spamassassin_ko.png)

>[!NOTE]
>
>每次您按一下&#x200B;**[!UICONTROL Anti-spam checking]**，就會呼叫SpamAssassin服務，並再次分析郵件以進行反垃圾郵件偵測。 再次執行反垃圾郵件分析前，請確定您已變更內容。
