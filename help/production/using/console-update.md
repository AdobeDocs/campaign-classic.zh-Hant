---
product: campaign
title: 控制台更新
description: 控制台更新
feature: Monitoring, Upgrade
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3a127bbe-9abb-4b5b-bd7e-e1ea550929ba
TQID: https://experienceleague.adobe.com/oNVXa9DaMu-b-GpfxT-Z0jFbWEd-MnsSzu8Jdb0S0Fw
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
feature_v2: []
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 55
ht-degree: 10%

---

# 控制台更新{#console-update}



如果您已選取&#x200B;**[!UICONTROL Do not request console update]**&#x200B;選項，且您想要重新啟用更新要求，請套用下列程式：

1. 使用Windows **[!UICONTROL Start > Execute]**&#x200B;功能表中的&#x200B;**regedit**&#x200B;命令開啟登入資料庫編輯器。

   ![](assets/ncs_console_update_1.png)

1. 在樹狀結構中，顯示&#x200B;**[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]**&#x200B;節點的選項。
1. 刪除&#x200B;**[!UICONTROL confAdvisedUpgrade]**&#x200B;專案並關閉登入編輯程式。

   ![](assets/ncs_console_update_2.png)
