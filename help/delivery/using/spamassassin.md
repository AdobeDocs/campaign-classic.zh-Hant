---
product: campaign
title: SpamAssassin
description: 瞭解如何使用SpamAssassin設定電子郵件垃圾郵件檢測
feature: Email, Deliverability
exl-id: 8be6836d-f7dc-4199-b2b2-b6a9cac9d162
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 6%

---

# 垃圾郵件刺客{#spamassassin}

![](../../assets/common.svg)

Adobe Campaign可以配置為 [垃圾郵件刺客](https://spamassassin.apache.org)，用於電子郵件垃圾郵件過濾的第三方服務。 這允許您對電子郵件進行分級，以確定郵件是否存在被接收時使用的反垃圾郵件工具視為垃圾郵件的風險。

SpamAssassin利用多種垃圾郵件檢測技術，包括：

* 基於DNS和基於模糊校驗和的垃圾郵件檢測
* 貝葉斯過濾
* 外部程式
* 德尼列斯
* 聯機資料庫

>[!NOTE]
>
>必須在Adobe Campaign應用伺服器上安裝和配置SpamAssassin。 如需詳細資訊，請參閱[本章節](../../installation/using/configuring-spamassassin.md)。
>
>控制元素是否是垃圾郵件的規則通過SpamAssassin進行管理，管理員可以使用權限對其進行編輯。

## 在活動中使用SpamAssassin {#using-spamassassin}

在建立了電子郵件交付並定義了其內容後，請按照以下步驟評估風險。

有關建立和設計交貨的詳細資訊，請參閱 [此部分](about-email-channel.md)。

1. 移至 **[!UICONTROL Preview]** 索引標籤。
1. 選擇收件人以預覽交貨。

   ![](assets/s_tn_del_preview_spamassassin_recipient.png)

   >[!NOTE]
   >
   >如果未選擇收件人，則無法執行反垃圾郵件檢查。

1. 警告消息將給出test的結果。 如果檢測到高風險級別，將顯示以下警告消息：

   ![](assets/s_tn_del_preview_spamassassin_ko.png)

1. 按一下 **[!UICONTROL More...]** 連結。
1. 選取 **[!UICONTROL Anti-spam checking]** 索引標籤。
1. 轉到 **[!UICONTROL Points / Rule / Description]** 的子菜單。

   ![](assets/s_tn_del_msg_spamassassin_ko.png)

>[!NOTE]
>
>每次按一下 **[!UICONTROL Anti-spam checking]**&#x200B;對SpamAssassin服務進行調用，並對消息進行重新分析以進行反垃圾郵件檢測。 確保在再次運行反垃圾郵件分析之前更改了內容。
