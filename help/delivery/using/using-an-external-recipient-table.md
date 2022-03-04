---
product: campaign
title: 使用外部收件者表格
description: 使用外部收件者表格
feature: Audiences
exl-id: b6aabc68-707d-4c6c-b008-277609166c6c
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 18%

---

# 使用外部收件者表格{#using-an-external-recipient-table}

![](../../assets/common.svg)

如果交貨表是外部表，則需要進行其他配置。 的 **[!UICONTROL nms:seedmember]** 必須擴展架構。 在種子地址中添加一個頁籤以定義適當的欄位，如下所示：

![](assets/s_ncs_user_seedlist_new_tab.png)

在這種情況下，要將種子地址添加到交貨中，請直接在匹配標籤中輸入足夠的欄位，或導入地址模板：

![](assets/s_ncs_user_seedlist_add_new_tab.png)

的 **nms:seedMember** 架構擴展是 [此部分](../../configuration/using/seed-addresses.md)。
