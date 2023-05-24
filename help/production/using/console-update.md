---
product: campaign
title: 控制台更新
description: 控制台更新
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3a127bbe-9abb-4b5b-bd7e-e1ea550929ba
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 10%

---

# 控制台更新{#console-update}



如果您已選取 **[!UICONTROL Do not request console update]** 選項後，如果您想要重新啟用更新請求，請套用以下程式：

1. 使用開啟登入資料庫的編輯器 **regedit** Windows中的命令 **[!UICONTROL Start > Execute]** 功能表。

   ![](assets/ncs_console_update_1.png)

1. 在樹狀結構中，顯示 **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** 節點。
1. 刪除 **[!UICONTROL confAdvisedUpgrade]** 輸入並關閉登入編輯程式。

   ![](assets/ncs_console_update_2.png)
