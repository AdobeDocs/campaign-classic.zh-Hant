---
product: campaign
title: 控制台更新
description: 控制台更新
feature: Monitoring, Upgrade
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3a127bbe-9abb-4b5b-bd7e-e1ea550929ba
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '62'
ht-degree: 20%

---

# 控制台更新{#console-update}



如果您已選取 **[!UICONTROL Do not request console update]** 選項，而且您想要重新啟用更新請求，請套用下列程式：

1. 使用開啟登入資料庫的編輯器 **regedit** Windows中的命令 **[!UICONTROL Start > Execute]** 功能表。

   ![](assets/ncs_console_update_1.png)

1. 在樹狀結構中，顯示 **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** 節點。
1. 刪除 **[!UICONTROL confAdvisedUpgrade]** 輸入並關閉登入編輯程式。

   ![](assets/ncs_console_update_2.png)
