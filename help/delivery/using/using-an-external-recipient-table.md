---
product: campaign
title: 使用外部收件者表格
description: 使用外部收件者表格
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Audiences
exl-id: b6aabc68-707d-4c6c-b008-277609166c6c
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 18%

---

# 使用外部收件者表格{#using-an-external-recipient-table}



如果傳遞表格是外部表格，您將需要執行其他設定。 此 **[!UICONTROL nms:seedmember]** 結構描述必須擴充。 種子地址會新增索引標籤，以定義適當的欄位，如下所示：

![](assets/s_ncs_user_seedlist_new_tab.png)

在這種情況下，若要將種子地址新增至傳遞，請直接在比對索引標籤中輸入適當的欄位，或匯入地址範本：

![](assets/s_ncs_user_seedlist_add_new_tab.png)

此 **nms：seedMember** 結構描述擴充功能為 [本節](../../configuration/using/seed-addresses.md).
