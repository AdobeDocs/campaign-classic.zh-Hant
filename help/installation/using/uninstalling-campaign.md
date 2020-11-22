---
solution: Campaign Classic
product: campaign
title: 解除安裝 Campaign
description: 瞭解如何解除安裝Campaign
audience: installation
content-type: reference
topic-tags: appendices
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 13%

---


# 解除安裝 Campaign{#uninstalling-campaign}

>[!CAUTION]
>
>這些程式將永久解除安裝Adobe Campaign。 所有資料都將遺失。

**RHEL:**

```
rpm -e nlserver6-v7
userdel -r neolane
groupdel neolane
rm -rf /user/local/neolane
```

**德比安：**

```
apt purge nlserver6-v7
userdel -r neolane
groupdel neolane
rm -rf /user/local/neolane
```

**Windows：**

Refer to this [page](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md#deleting-and-cleansing-adobe-campaign-previous-version). 別忘了移除Campaign安裝資料夾。
