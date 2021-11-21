---
product: campaign
title: 控制台更新
description: 控制台更新
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3a127bbe-9abb-4b5b-bd7e-e1ea550929ba
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 10%

---

# 控制台更新{#console-update}

![](../../assets/v7-only.svg)

如果您選取 **[!UICONTROL Do not request console update]** 選項，而您想要重新啟用更新請求，請套用下列程式：

1. 使用開啟註冊表資料庫的編輯器 **regedit** 命令 **[!UICONTROL Start > Execute]** 功能表。

   ![](assets/ncs_console_update_1.png)

1. 在樹中，顯示 **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** 節點。
1. 刪除 **[!UICONTROL confAdvisedUpgrade]** 登入並關閉註冊表編輯器。

   ![](assets/ncs_console_update_2.png)
