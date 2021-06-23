---
product: campaign
title: SpamAssassin
description: 了解如何使用SpamAssassin設定電子郵件垃圾郵件偵測
audience: delivery
content-type: reference
topic-tags: deliverability-management
exl-id: 8be6836d-f7dc-4199-b2b2-b6a9cac9d162
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 6%

---

# SpamAssassin{#spamassassin}

## 關於SpamAssassin {#about-spamassassin}

Adobe Campaign可以設定為與[SpamAssassin](https://spamassassin.apache.org)搭配使用，此為用於電子郵件垃圾訊息篩選的協力廠商服務。 這可讓您對電子郵件進行分數，以判斷郵件是否存在被接收時使用的反垃圾郵件工具視為垃圾郵件的風險。

SpamAssassin利用各種垃圾郵件檢測技術，包括：

* 基於DNS和基於模糊校驗和的垃圾郵件檢測
* 貝葉斯濾波
* 外部方案
* 封鎖清單
* 線上資料庫

>[!NOTE]
>
>必須在Adobe Campaign應用程式伺服器上安裝及設定SpamAssassin。 如需詳細資訊，請參閱[本章節](../../installation/using/configuring-spamassassin.md)。
>
>控管元素是否為垃圾訊息的規則會透過SpamAssassin進行管理，並可由具有權限的管理員編輯。

## 使用SpamAssassin {#using-spamassassin}

建立電子郵件傳送並定義其內容後，請依照下列步驟評估風險。

如需建立和設計傳送的詳細資訊，請參閱[此區段](about-email-channel.md)。

1. 移至 **[!UICONTROL Preview]** 索引標籤。
1. 選取收件者以預覽您的傳送。

   ![](assets/s_tn_del_preview_spamassassin_recipient.png)

   >[!NOTE]
   >
   >如果您未選擇收件人，則無法執行反垃圾郵件檢查。

1. 警告訊息會提供測試結果。 如果檢測到高風險，則顯示以下警告消息：

   ![](assets/s_tn_del_preview_spamassassin_ko.png)

1. 按一下警告旁的&#x200B;**[!UICONTROL More...]**&#x200B;連結。
1. 選取 **[!UICONTROL Anti-spam checking]** 索引標籤。
1. 前往&#x200B;**[!UICONTROL Points / Rule / Description]**&#x200B;區段，查看此風險的原因。

   ![](assets/s_tn_del_msg_spamassassin_ko.png)

>[!NOTE]
>
>每次按一下&#x200B;**[!UICONTROL Anti-spam checking]**&#x200B;時，都會呼叫SpamAssassin服務，並再次分析郵件以偵測反垃圾訊息。 在再次運行反垃圾郵件分析之前，請確保已更改您的內容。
