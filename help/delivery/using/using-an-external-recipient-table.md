---
solution: Campaign Classic
product: campaign
title: 使用外部收件者資料表
description: 使用外部收件者資料表
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 18%

---


# 使用外部收件者資料表{#using-an-external-recipient-table}

如果傳送表是外部表，則需要進行其他配置。 **[!UICONTROL nms:seedmember]**&#x200B;架構必須擴展。 系統會在種子地址中添加一個頁籤以定義適當的欄位，如下所示：

![](assets/s_ncs_user_seedlist_new_tab.png)

在這種情況下，要將種子地址添加到交貨中，請直接在匹配頁籤中輸入足夠的欄位，或導入地址模板：

![](assets/s_ncs_user_seedlist_add_new_tab.png)

**nms:seedMember**&#x200B;模式擴展是[本節](../../configuration/using/seed-addresses.md)。
