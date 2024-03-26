---
product: campaign
title: SpamAssassin
description: 瞭解如何使用SpamAssassin設定電子郵件垃圾郵件偵測
badge-v7: label="v7" type="Informative" tooltip="套用至Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Email, Deliverability
role: User
exl-id: 8be6836d-f7dc-4199-b2b2-b6a9cac9d162
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 5%

---

# SpamAssassin{#spamassassin}

Adobe Campaign可設定為搭配 [SpamAssassin](https://spamassassin.apache.org)，用於電子郵件垃圾郵件篩選的第三方服務。 這可讓您對電子郵件評分，以判斷郵件是否在收到時遭到的反垃圾郵件工具視為垃圾郵件的風險。

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

有關建立及設計傳送的詳細資訊，請參閱 [本節](about-email-channel.md).

1. 前往 **[!UICONTROL Preview]** 標籤。
1. 選取收件者以預覽您的傳遞。

   ![](assets/s_tn_del_preview_spamassassin_recipient.png)

   >[!NOTE]
   >
   >如果您未選取收件者，則無法執行反垃圾郵件檢查。

1. 警告訊息會提供測試的結果。 如果偵測到高風險等級，會顯示下列警告訊息：

   ![](assets/s_tn_del_preview_spamassassin_ko.png)

1. 按一下 **[!UICONTROL More...]** 警告旁邊的連結。
1. 選取 **[!UICONTROL Anti-spam checking]** 索引標籤。
1. 前往 **[!UICONTROL Points / Rule / Description]** 區段來檢視此風險的原因。

   ![](assets/s_tn_del_msg_spamassassin_ko.png)

>[!NOTE]
>
>每次按一下 **[!UICONTROL Anti-spam checking]**，會呼叫SpamAssassin服務，並重新分析郵件以進行反垃圾郵件偵測。 再次執行反垃圾郵件分析前，請確定您已變更內容。
