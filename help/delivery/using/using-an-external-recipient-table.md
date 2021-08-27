---
product: campaign
title: 使用外部收件者資料表
description: 使用外部收件者資料表
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
exl-id: b6aabc68-707d-4c6c-b008-277609166c6c
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 18%

---

# 使用外部收件者資料表{#using-an-external-recipient-table}

![](../../assets/common.svg)

如果傳送表格是外部表格，則您需要進行其他設定。 必須擴展&#x200B;**[!UICONTROL nms:seedmember]**&#x200B;架構。 種子地址中會新增一個索引標籤，以定義足夠的欄位，如下所示：

![](assets/s_ncs_user_seedlist_new_tab.png)

在這種情況下，若要將種子地址添加到傳送中，請直接在匹配頁簽中輸入足夠的欄位，或導入地址模板：

![](assets/s_ncs_user_seedlist_add_new_tab.png)

**nms:seedMember**&#x200B;方案擴展為[此部分](../../configuration/using/seed-addresses.md)。
