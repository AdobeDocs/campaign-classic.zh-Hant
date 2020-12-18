---
solution: Campaign Classic
product: campaign
title: 主控台更新
description: 主控台更新
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 10%

---


# 主控台更新{#console-update}

如果您選取了&#x200B;**[!UICONTROL Do not request console update]**&#x200B;選項，並且想要重新啟用更新請求，請套用下列程式：

1. 使用Windows **[!UICONTROL Start > Execute]**&#x200B;菜單中的&#x200B;**regedit**&#x200B;命令開啟註冊表資料庫的編輯器。

   ![](assets/ncs_console_update_1.png)

1. 在樹中，顯示&#x200B;**[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]**&#x200B;節點的選項。
1. 刪除&#x200B;**[!UICONTROL confAdvisedUpgrade]**&#x200B;條目並關閉註冊表編輯器。

   ![](assets/ncs_console_update_2.png)

