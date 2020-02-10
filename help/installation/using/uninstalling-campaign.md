---
title: 解除安裝Campaign
seo-title: 解除安裝Campaign
description: 解除安裝Campaign
seo-description: null
page-status-flag: never-activated
uuid: 4e95a576-a2fe-41dd-a03d-e4a3120f8788
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: appendices
discoiquuid: 702253cc-3e1a-44ad-9340-b8588ee86bad
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 解除安裝Campaign{#uninstalling-campaign}

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

**Windows:**

Refer to this [page](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md#deleting-and-cleansing-adobe-campaign-previous-version). 別忘了移除Campaign安裝資料夾。
