---
title: 使用外部收件者表
seo-title: 使用外部收件者表
description: 使用外部收件者表
seo-description: null
page-status-flag: never-activated
uuid: a6147425-14f0-41e8-a47f-3e7072deafa7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: 92c32b2d-d8bf-41ab-9349-ef4a15f10521
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 使用外部收件者表{#using-an-external-recipient-table}

如果傳送表是外部表，則需要進行其他配置。 必 **[!UICONTROL nms:seedmember]** 須擴展模式。 系統會在種子地址中添加一個頁籤以定義適當的欄位，如下所示：

![](assets/s_ncs_user_seedlist_new_tab.png)

在這種情況下，要將種子地址添加到交貨中，請直接在匹配頁籤中輸入足夠的欄位，或導入地址模板：

![](assets/s_ncs_user_seedlist_add_new_tab.png)

此 **部分是nms:seedMember** 架構 [擴展](../../configuration/using/seed-addresses.md)。
