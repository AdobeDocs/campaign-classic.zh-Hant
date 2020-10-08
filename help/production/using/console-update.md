---
title: 主控台更新
seo-title: 主控台更新
description: 主控台更新
seo-description: null
page-status-flag: never-activated
uuid: d2193d4f-b98c-47b1-88f1-7e5ccf4c453c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 9281808b-1c2f-4095-9051-f181f089f205
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '57'
ht-degree: 14%

---


# 主控台更新{#console-update}

如果您選取了 **[!UICONTROL Do not request console update]** 選項，而且想要重新啟用更新請求，請套用下列程式：

1. 使用Windows菜單中的 **regedit** 命令開啟註冊表資料庫的編 **[!UICONTROL Start > Execute]** 輯器。

   ![](assets/ncs_console_update_1.png)

1. 在樹中，顯示節點的選 **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** 項。
1. 刪除條 **[!UICONTROL confAdvisedUpgrade]** 目並關閉註冊表編輯器。

   ![](assets/ncs_console_update_2.png)

