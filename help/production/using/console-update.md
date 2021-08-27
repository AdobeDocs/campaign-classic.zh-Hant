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

如果您選取了&#x200B;**[!UICONTROL Do not request console update]**&#x200B;選項，並且要重新激活更新請求，請應用以下過程：

1. 使用Windows **[!UICONTROL Start > Execute]**&#x200B;菜單中的&#x200B;**regedit**&#x200B;命令開啟註冊表資料庫的編輯器。

   ![](assets/ncs_console_update_1.png)

1. 在樹中，顯示&#x200B;**[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]**&#x200B;節點的選項。
1. 刪除&#x200B;**[!UICONTROL confAdvisedUpgrade]**&#x200B;條目並關閉註冊表編輯器。

   ![](assets/ncs_console_update_2.png)
